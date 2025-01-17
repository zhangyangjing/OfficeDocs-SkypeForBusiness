---
ms.date: 06/11/2018
title: "Partner qualification for Lync - IP PBXs"
ms.author: serdars
author: msdmaguire
manager: serdars
ms.reviewer: dougand
ms.topic: article
ms.tgt.pltfrm: lync
ms.service: skype-for-business-online
ms.collection: Lync
audience: Admin
appliesto:
- Lync
- Skype for Business
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.custom:
- Lync Certification
- dn788945
description: "Partner qualification requirements for Lync IP PBXs."
---

# Supported IP PBXs

The following IP PBXs are supported by Microsoft. But, they haven't gone through the formal UCOIP qualification process, nor did the vendor request testing.

Microsoft does sufficient internal testing to identity specific, supported configurations (where applicable with known limitations). These configurations use the commercially available production SIP trunk interface of the IP-PBX vendor, but might not be supported by the vendor. Also, the vendor might not provide complete documentation for installation, set-up, release notes, or support processes. Wherever possible, Microsoft tries to provide documentation for installation and set-up.

## Supported for Lync 2013
***Table 1 - Supported for Lync 2013***

<table border="1" cellpadding="5" cellspacing="" class="grid" width="100%">
    <colgroup>
        <col width="74" />
        <col width="364" />
        <col width="254" />
        <col />
    </colgroup>
    <thead>
        <tr bgcolor="#DEDEDE">
            <td align="center" valign="top"><strong>IP-PBX Vendor</strong></td>
            <td align="center" valign="top"><strong>Tested Product</strong></td>
            <td align="center" valign="top"><strong>Supported Configuration</strong></td>
            <td align="center" valign="top"><strong>Software Version Tested</strong></td>
        </tr>
    </thead>
    <tbody>
        <tr align="left" valign="top">
            <td rowspan="6">Avaya</td>
            <td>Aura Session Manager 6.1</td>
            <td>Direct SIP</td>
            <td>6.1.2.0.612004 (Service Pack 2)</td>
        </tr>
        <tr>
            <td colspan="3" > </td>
        </tr>
        <tr align="left" valign="top">
            <td colspan="3">
                <p>Documentation: <a href="https://www.microsoft.com/download/details.aspx?id=41152">Lync 2013 and Avaya Aura 6.1 Integration Guide v1.3</a></p>
                <p>Configuration Notes:</p>
                <ol>
                    <li>REFER can be set to enabled and RTCP set to Disabled.</li>
                    <li>TLS and SRTP weren't tested.</li>
                    <li>Disable "ForwardCallHistory" on the trunk Call forwarding on Lync client fails at PRI when History-Info is turned on.</li>
                </ol>
                <p>Known Limitations:</p>
                <ol>
                    <li>Because of the issue documented in <a href="https://support.microsoft.com/kb/2904439">KB 2904439</a>, call hold fails with media bypass enabled.</li>
                    <li>Comfort noise generation isn't supported. As a result, comfort noise isn't played on Lync.</li>
                </ol>
            </td>
        </tr>
        <tr align="left" valign="top">
            <td>Aura Session Manager 6.3</td>
            <td>Direct SIP</td>
            <td>6.3.2.0.632023</td>
        </tr>
        <tr>
            <td colspan="3"> </td>
        </tr>
        <tr align="left" valign="top">
            <td colspan="3">
                <p>Configuration Notes<em>:</p>
                <ol>
                    <li>Media Bypass, RTCP, REFER, Centralized Media Processing and ForwardCallHistory were set to Disabled.</li>
                    <li>Session Timer were set to Enabled.<br /></em>Information was received from Avaya.</li>
                </ol>
                <p>Known Limitations:</p>
                <ol>
                    <li>When Media bypass is enabled in Lync, and there's an incoming call to a Lync client with simultaneous ring to a number with early media enabled, the caller hears ring back instead of early media.</li>
                    <li>Avaya Aura communication manager doesn't send disconnect to PSTN via ISDN trunk while receiving SIP 603 response from Mediation server for incoming call to Lync client. Caller will hear overflow tone and call won't disconnect until caller drops the call.</li>
                </ol>
            </td>
        </tr>
        <tr align="left" valign="top">
            <td rowspan="6">Cisco</td>
            <td>Cisco Unified Communications Manager</td>
            <td>Direct SIP</td>
            <td>UCM 8.6.2.20000-2</td>
        </tr>
        <tr>
            <td colspan="3"> </td>
        </tr>
        <tr align="left" valign="top">
            <td colspan="3">
                <p>Configuration Notes:</p>
                <ol>
                    <li>On the Cisco IP-PBX, configure MTP to enabled and PRACK to disabled (the default for PRACK).</li>
                    <li>In order to manage call hold appropriately in bypass scenarios, the following update is needed for the Lync client: <a href="https://support.microsoft.com/kb/3020377">https://support.microsoft.com/kb/3020377</a></li>
                    <li>On Lync Mediation Server, Media Bypass, REFER, and Session Timer are set to enabled. RTCP is set to disabled.</li>
                </ol>
                <p>Known Limitations:</p>
                <ol>
                    <li>Comfort noise generation isn't supported. As a result, comfort noise isn't played on Microsoft Lync.</li>
                    <li>When a Lync user configures call forward or simul-ring to a PSTN IVR number, the calling party won't hear early media played from the IVR.</li>
                    <li>Cisco UCM doesn't originate or pass through 'History-Info' and 'Referred-by' nor convert it to 'Diversion' header. As a result, calls forwarded or transferred to a PSTN user or calls that simultaneously ring a PSTN user might fail with Service Providers that expect history information (transferring party info). Service Providers not looking for the transferring party details in history or diversion headers might pass the call through. However, this behavior might cause billing challenges for these kinds of calls.</li>
                </ol>
            </td>
        </tr>
        <tr align="left" valign="top">
            <td>Cisco Unified Communications Manager</td>
            <td>Direct SIP</td>
            <td>UCM 7.0.1.11000-2</td>
        </tr>
        <tr>
            <td colspan="3"> </td>
        </tr>
        <tr align="left" valign="top">
            <td colspan="3">
                <p>Configuration Notes:</p>
                <ol>
                    <li>On the Cisco IP-PBX, configure MTP to enabled and PRACK to disabled (the default for PRACK).</li>
                    <li>On Lync Mediation Server, Media Bypass is set to enabled. RTCP and REFER are set to disabled, as Cisco doesn't send RTCP messages and REFER isn't supported by this IP-PBX without a Referred-By header.</li>
                </ol>
                <p>Known Limitations:</p>
                <ol>
                    <li>When a Lync user transfers a PBX call to another PBX user, the local PBX phone will still show connected to the first Lync user.</li>
                    <li>Comfort noise generation isn't supported. As a result, comfort noise isn't played on Microsoft Lync.</li>
                    <li>When a Lync user configures call forward or simul-ring to a PSTN IVR number, the calling party won't hear early media played from the IVR.</li>
                    <li>CUCM won't send OPTIONS, impacting failover scenarios as the IP-PBX can't determine Lync's state until a call is offered.</li>
                </ol>
            </td>
        </tr>
        <tr align="left" valign="top">
            <td>Siemens</td>
            <td>OpenScape Voice</td>
            <td> </td>
            <td>v6.00.01</td>
        </tr>
    </tbody>
</table>
<br />

## Supported in Lync 2010

<strong><em>Table 2 - IP PBXs supported in Lync 2010</em></strong>
<table border="1" cellpadding="5" cellspacing="" class="grid" width="100%">
    <thead>
        <tr bgcolor="#DEDEDE">
            <td align="center" valign="top"><strong>IP-PBX Vendor</strong></td>
            <td align="center" valign="top"><strong>Tested Product</strong></td>
            <td align="center" valign="top"><strong>Supported Configuration</strong></td>
            <td align="center" valign="top"><strong>Software Version Tested</strong></td>
        </tr>
    </thead>
    <tbody>
        <tr align="left" valign="top">
            <td rowspan="3">Alcatel-Lucent</td>
            <td>OmniPCX Enterprise OXE</td>
            <td>Direct SIP</td>
            <td>R9.1</td>
        </tr>
        <tr>
            <td colspan="3"> </td>
        </tr>
        <tr align="left" valign="top">
            <td colspan="3">
                <p>Configuration Notes:</p>
                <ol>
                    <li>On Lync Mediation Server, Media Bypass, RTCP, and REFER are set to disabled. Testing found Media Bypass doesn't work for inbound calls, REFER isn't supported and Alcatel doesn't send RTCP messages.</li>
                </ol>
                <p>Known Limitations:</p>
                <ol>
                    <li>When a Lync user initiates a call to a PBX or PSTN endpoint and then places the call on hold, they receive the error, "call could not be put on hold" with the Lync client muted. Afterwards, the Lync client can't be unmuted.</li>
                    <li>When a Lync user performs a Blind transfer of a PBX or PSTN call to another PBX, PSTN, or Lync number and the transfer target doesn't answer, the call can't be recovered to the original call. If the transfer completes, the local PBX phone will still show connection to the first Lync user</li>
                    <li>When a call is ringing to a Lync user, the caller (either on an Alcatel station or a PSTN line routed through the PBX) won't get a ring-back tone.</li>
                    <li>Comfort noise generation isn't supported. As a result, comfort noise isn't played on Microsoft Lync.</li>
                    <li>When a Lync user declines a PSTN call routed from some PSTN trunk configurations, the PSTN caller doesn't get disconnected, and instead hears ring-back.</li>
                    <li>Because Alcatel sends a 502 message for a T1 line out of service or disconnected instead of a 503, failover to an alternate route doesn't function.</li>
                </ol>
            </td>
        </tr>
        <tr align="left" valign="top">
            <td rowspan="6">Avaya</td>
            <td>Aura Session Manager</td>
            <td>Direct SIP</td>
            <td>6.0.1</td>
        </tr>
        <tr>
            <td colspan="3"> </td>
        </tr>
        <tr align="left" valign="top">
            <td colspan="3">
                <p>Configuration Notes:</p>
                    <ol>
                        <li>On Lync Mediation Server, Media Bypass and REFER are set to disabled. Testing found Media Bypass doesn't work for inbound calls and REFER isn't supported.</li>
                        <li>TLS and SRTP aren't supported by Avaya and as a result need to be set to be disabled on Mediation Server.</li>
                    </ol>
                </div>
                <p>Known Limitations:</p>
                <ol>
                    <li>Avaya doesn't support using an FQDN in the connection field.</li>
                    <li>Comfort noise generation isn't supported. As a result, comfort noise isn't played on Lync.</li>
                    <li>Testing found when calls routed to Avaya Audix voice mail might hear partial audio followed by disconnection.</li>
                </ol>
            </td>
        </tr>
        <tr align="left" valign="top">
            <td>Communications Manager SIP Enablement Services</td>
            <td>Direct SIP</td>
            <td>4.0<br />5.1<br />5.2.1</td>
        </tr>
        <tr>
            <td colspan="3"> </td>
        </tr>
        <tr align="left" valign="top">
            <td colspan="3">
                <p>Documentation: <a href="https://www.microsoft.com/download/details.aspx?displaylang=en&amp;id=2187">Integrating Microsoft Lync Server 2010 and Avaya Communications Manager S8300</a></p>
                <p>Configuration Notes:</p>
                <ol>
                    <li>On the Avaya IP-PBX, the configuration requires setting "Alternate Route Timer(sec)" value from default of 10 sec to 30 sec. The configuration should show "Alternate Route Timer(sec): 30" in the corresponding SIP signaling group.</li>
                    <li>On Lync Mediation Server, Media Bypass and REFER are set to disabled. Testing found Media Bypass doesn't work for inbound calls and REFER isn't supported.</li>
                </ol>
                <p>Known Limitations:</p>
                <ol>
                    <li>When a Lync user transfers a PBX call to another PBX user, the local PBX phone still shows connected to the first Lync user.</li>
                    <li>When a call is ringing to a Lync user, the caller (either on an Avaya station or a PSTN line routed through the PBX) doesn't get a ring-back tone. Avaya resolves this issue with the 5.2.1 SP1 software release.</li>
                    <li>Monitoring reports doesn't contain information regarding jitter and packet loss.</li>
                    <li>Comfort noise generation isn't supported. As a result, comfort noise isn't played on Lync.</li>
                    <li>ISDN Failover isn't supported from a Lync perspective. If the Avaya PBX is being used for PSTN connectivity and multiple T1s are being utilized, a Lync client doesn't retry a call based on a T1 being unavailable. It might be possible to configure the PBX to not assign outbound calls from Lync to an unavailable T1, but this configuration isn't tested.</li>
                </ol>
            </td>
        </tr>
        <tr align="left" valign="top">
            <td rowspan="10">Cisco</td>
            <td colspan="3">Documentation: <a href="https://www.microsoft.com/download/details.aspx?id=26800">Integrating Microsoft Lync Server 2010 and Cisco Unified Communications Manager</a></td>
        </tr>
        <tr align="left" valign="top">
            <td>Cisco Unified Communications Manager<br />Cisco Unified Session Manager<em></td>
            <td>Direct SIP</td>
            <td>UCM 8.5.1.12900-7</td>
        </tr>
        <tr>
            <td colspan="3"> </td>
        </tr>
        <tr align="left" valign="top">
            <td colspan="3">
                <p>Configuration Notes:</p>
                <ol>
                    <li>On the Cisco IP-PBX, configure MTP to enabled and PRACK to enabled.</li>
                    <li>On Lync Mediation Server, Media Bypass is set to enabled. RTCP is set to disabled, as Cisco doesn't send RTCP messages. You should set REFER to be enabled, because IP-PBX supports REFER.</li>
                </ol>
                <p>Known Limitations:</p>
                <ol>
                    <li>Comfort noise generation isn't supported. As a result, comfort noise isn't played on Microsoft Lync. When a Lync user configures call forward or simul-ring to a PSTN IVR number, the calling party doesn't hear early media played from the IVR.</li>
                </ol>
                <p></em> <b>Note:</b> Cisco states that Unified Session Manager is based on the same SIP capability as Unified Communications Manager. As such, it supports the same capabilities as the qualified version of Unified Communications Manager.</p>
            </td>
        </tr>
        <tr align="left" valign="top">
            <td>Cisco Unified Communications Manager</td>
            <td>Direct SIP</td>
            <td>UCM 8.0.3.21900-8</td>
        </tr>
        <tr>
            <td colspan="3"> </td>
        </tr>
        <tr align="left" valign="top">
            <td colspan="3">
                <p>Configuration Notes:</p>
                <ol>
                    <li>On the Cisco IP-PBX, configure MTP to enabled and PRACK to disabled (the default for PRACK). The PRACK message sent by CUCM 4 is malformed by missing the MAXFORWARDS header.</li>
                    <li>On Lync Mediation Server, Media Bypass is set to enabled. RTCP and REFER are set to disabled, as Cisco doesn't send RTCP messages and REFER isn't supported by this IP-PBX.</li>
                </ol>
                <p>Known Limitations:</p>
                <ol>
                    <li>Comfort noise generation isn't supported. As a result, comfort noise isn't played on Microsoft Lync.</li>
                    <li>When a Lync user configures call forward or simul-ring to a PSTN IVR number, the calling party doesn't hear early media played from the IVR.</li>
                </ol>
            </td>
        </tr>
        <tr align="left" valign="top">
            <td>Cisco Unified Communications Manager</td>
            <td>Direct SIP</td>
            <td>UCM 4.2 2000-4-4a<br />UCM 6.1.3.2000-1<br />UCM 7.1.3.10000-11</td>
        </tr>
        <tr>
            <td colspan="3"> </td>
        </tr>
        <tr align="left" valign="top">
            <td colspan="3">
                <p>Configuration Notes:</p>
                <ol>
                    <li>On the Cisco IP-PBX, configure MTP to enabled and PRACK to disabled (the default for PRACK). The PRACK message sent by CUCM 4 is malformed by missing the MAXFORWARDS header.</li>
                    <li>On Lync Mediation Server, Media Bypass is set to enabled. RTCP and REFER are set to disabled, as Cisco doesn't send RTCP messages and IP-PBX doesn't support REFER.</li>
                </ol>
                <p>Known Limitations:</p>
                <ol>
                    <li>When a Lync user transfers a PBX call to another PBX user, the local PBX phone still shows connected to the first Lync user.</li>
                    <li>Comfort noise generation isn't supported. As a result, comfort noise isn't played on Microsoft Lync.</li>
                    <li>When a Lync user configures call forward or simul-ring to a PSTN IVR number, the calling party doesn't hear early media played from the IVR.</li>
                </ol>
            </td>
        </tr>
    </tbody>
</table>

For more information on Direct SIP Configurations with Lync Server, see: [PSTN Connectivity Components](../../SfbServer/plan-your-deployment/enterprise-voice-solution/pstn-connectivity.md).

