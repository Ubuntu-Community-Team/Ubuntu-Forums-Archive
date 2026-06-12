---
title: "How to get iTunes in Windows Vista/Virtualbox/Ubuntu 8.04 to read iPhone 5"
date: 2012-10-17
forum: General Help
---

### Post by Fidelio1st on 2012-10-17
Anyone have any ideas how to get iTunes 10.7.0.21 (most recent) running in Windows Vista in Virtualbox in Ubuntu 8.04 to read the new iPhone 5?

When I go to devices/USB devices, it shows my iPhone 5. However, iTunes is not showing my iPhone on the left bar and I can't figure out how to access the iPhone through iTunes in Vitualbox/Vista. I've shut down and restarted iTunes several times, and then I shut down and restarted Vista, but still the same.

I ran a device connectivity test through iTunes and everything checks out under ports, except "no iPod, iPhone, or iPad found". Below is the entire diagnostic (I replaced some #'s with [NA] as I wasn't sure if I should post on a public form).


DIAGNOSTIC


Microsoft Windows Vista Home Premium Edition (Build 6000)
innotek GmbH VirtualBox
iTunes 10.7.0.21
QuickTime not available
FairPlay 2.2.19
Apple Application Support 2.2.2
iPod Updater Library 10.0d2
CD Driver 2.2.3.0
CD Driver DLL 2.1.3.1
Apple Mobile Device 6.0.0.59
Apple Mobile Device Driver 1.62.0.0
Bonjour 3.0.0.10 (333.10)
Gracenote SDK 1.9.6.502
Gracenote MusicID 1.9.6.115
Gracenote Submit 1.9.6.143
Gracenote DSP 1.9.6.45

iTunes Serial Number [NA]

Current user is not an administrator.
The current local date and time is 2012-10-14 15:40:15.
iTunes is not running in safe mode.
WebKit accelerated compositing is disabled.
HDCP is not supported.
Core Media is not supported. (16002)

Video Display Information

Oracle Corporation, VirtualBox Graphics Adapter


**** External Plug-ins Information ****

No external plug-ins installed.

**** Network Connectivity Tests ****

Network Adapter Information

Adapter Name: { [NA]}
Description: Intel(R) PRO/1000 MT Desktop Adapter
IP Address: [NA]
Subnet Mask: [NA]
Default Gateway: [NA]
DHCP Enabled: Yes
DHCP Server: [NA]
Lease Obtained: Sun Oct 14 15:02:01 2012

Lease Expires: Mon Oct 15 15:02:01 2012

DNS Servers: [NA]
[NA]

Active Connection: LAN Connection
Connected: Yes
Online: Yes
Using Modem: No
Using LAN: Yes
Using Proxy: No

Firewall Information

Windows Firewall is on.
iTunes is NOT enabled in Windows Firewall.

Connection attempt to Apple web site was successful.
Connection attempt to browsing iTunes Store was successful.
Connection attempt to purchasing from iTunes Store was successful.
Connection attempt to iPhone activation server was successful.
Connection attempt to firmware update server was successful.
Connection attempt to Gracenote server was successful.
Last successful iTunes Store access was 2012-10-14 15:32:21.


**** Device Connectivity Tests ****

iPodService 10.7.0.21 is currently running.
iTunesHelper 10.7.0.21 is currently running.
Apple Mobile Device service 3.3.0.0 is currently running.

Universal Serial Bus Controllers:

Standard OpenHCD USB Host Controller. Device is working properly.

No FireWire (IEEE 1394) Host Controller found.

**** Device Sync Tests ****

No iPod, iPhone, or iPad found.

---

### Post by lmm5247 on 2012-10-17
> **Fidelio1st said:**
> Anyone have any ideas how to get iTunes 10.7.0.21 (most recent) running in Windows Vista in Virtualbox in Ubuntu 8.04 to read the new iPhone 5?

When I go to devices/USB devices, it shows my iPhone 5. However, iTunes is not showing my iPhone on the left bar and I can't figure out how to access the iPhone through iTunes in Vitualbox/Vista. I've shut down and restarted iTunes several times, and then I shut down and restarted Vista, but still the same.

I ran a device connectivity test through iTunes and everything checks out under ports, except "no iPod, iPhone, or iPad found". Below is the entire diagnostic (I replaced some #'s with [NA] as I wasn't sure if I should post on a public form).


DIAGNOSTIC


Microsoft Windows Vista Home Premium Edition (Build 6000)
innotek GmbH VirtualBox
iTunes 10.7.0.21
QuickTime not available
FairPlay 2.2.19
Apple Application Support 2.2.2
iPod Updater Library 10.0d2
CD Driver 2.2.3.0
CD Driver DLL 2.1.3.1
Apple Mobile Device 6.0.0.59
Apple Mobile Device Driver 1.62.0.0
Bonjour 3.0.0.10 (333.10)
Gracenote SDK 1.9.6.502
Gracenote MusicID 1.9.6.115
Gracenote Submit 1.9.6.143
Gracenote DSP 1.9.6.45

iTunes Serial Number [NA]

Current user is not an administrator.
The current local date and time is 2012-10-14 15:40:15.
iTunes is not running in safe mode.
WebKit accelerated compositing is disabled.
HDCP is not supported.
Core Media is not supported. (16002)

Video Display Information

Oracle Corporation, VirtualBox Graphics Adapter


**** External Plug-ins Information ****

No external plug-ins installed.

**** Network Connectivity Tests ****

Network Adapter Information

Adapter Name: { [NA]}
Description: Intel(R) PRO/1000 MT Desktop Adapter
IP Address: [NA]
Subnet Mask: [NA]
Default Gateway: [NA]
DHCP Enabled: Yes
DHCP Server: [NA]
Lease Obtained: Sun Oct 14 15:02:01 2012

Lease Expires: Mon Oct 15 15:02:01 2012

DNS Servers: [NA]
[NA]

Active Connection: LAN Connection
Connected: Yes
Online: Yes
Using Modem: No
Using LAN: Yes
Using Proxy: No

Firewall Information

Windows Firewall is on.
iTunes is NOT enabled in Windows Firewall.

Connection attempt to Apple web site was successful.
Connection attempt to browsing iTunes Store was successful.
Connection attempt to purchasing from iTunes Store was successful.
Connection attempt to iPhone activation server was successful.
Connection attempt to firmware update server was successful.
Connection attempt to Gracenote server was successful.
Last successful iTunes Store access was 2012-10-14 15:32:21.


**** Device Connectivity Tests ****

iPodService 10.7.0.21 is currently running.
iTunesHelper 10.7.0.21 is currently running.
Apple Mobile Device service 3.3.0.0 is currently running.

Universal Serial Bus Controllers:

Standard OpenHCD USB Host Controller. Device is working properly.

No FireWire (IEEE 1394) Host Controller found.

**** Device Sync Tests ****

No iPod, iPhone, or iPad found.
so in Vista, you can go to Computer and see your iPhone under devices? or can you not even get that far? I had to make sure my iPod was selected inside the VirtualBox Manager (attachment) so it could be seen inside my VM...

---

