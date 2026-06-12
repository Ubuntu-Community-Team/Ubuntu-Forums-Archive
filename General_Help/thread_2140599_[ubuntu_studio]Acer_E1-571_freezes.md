---
title: "[ubuntu_studio]Acer E1-571 freezes"
date: 2013-04-30
forum: General Help
---

### Post by Dr.tilik on 2013-04-30
I have a brand new acer e1-571(i7-3612QM 2.1GHZ, 6GB RAM), i have installed ubuntu studio 12.04 on it and it seems to work fluid and cool, but quite often it just freezes completely, and there's nothing i can do apart from reboot using the switch. Any help will be appreciated! 
Thanks in advance!

---

### Post by Dr.tilik on 2013-05-02
it may be an ubuntu studio issue, anyone has the same laptop and can say something about it?

---

### Post by Dr.tilik on 2013-05-06
At least a clue to monitor my system or something similar? 
thanks!

---

### Post by sulobanks on 2013-05-06
Note the time that it freezes, then look through /var/log/ for clues.  The files syslog, kern.log and dmesg are good places to start.  Look for events logged around the time your computer froze.

---

### Post by Dr.tilik on 2013-05-08
I found this in kernel.log...
There seems to be a capital ERROR 
] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 16000000, was 12060000
but I don't know if it's that... 

any help appreciated, if more information needed I can collect, no problem. 

Thank you, 

here's a brief of the last logs before getting freezed... 


May  9 00:43:54 Doctor kernel: [   12.795019] init: failsafe main process (857) killed by TERM signal
May  9 00:43:54 Doctor kernel: [   12.995141] ppdev: user-space parallel port driver
May  9 00:43:54 Doctor kernel: [   13.045094] type=1400 audit(1368053034.985:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=936 comm="apparmor_parser"
May  9 00:43:54 Doctor kernel: [   13.045449] type=1400 audit(1368053034.985:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=936 comm="apparmor_parser"
May  9 00:43:55 Doctor kernel: [   13.158466] type=1400 audit(1368053035.098:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=969 comm="apparmor_parser"
May  9 00:43:55 Doctor kernel: [   13.158739] type=1400 audit(1368053035.099:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=964 comm="apparmor_parser"
May  9 00:43:55 Doctor kernel: [   13.190312] Bluetooth: Core ver 2.16
May  9 00:43:55 Doctor kernel: [   13.190335] NET: Registered protocol family 31
May  9 00:43:55 Doctor kernel: [   13.190337] Bluetooth: HCI device and connection manager initialized
May  9 00:43:55 Doctor kernel: [   13.190339] Bluetooth: HCI socket layer initialized
May  9 00:43:55 Doctor kernel: [   13.190341] Bluetooth: L2CAP socket layer initialized
May  9 00:43:55 Doctor kernel: [   13.190347] Bluetooth: SCO socket layer initialized
May  9 00:43:55 Doctor kernel: [   13.226039] Bluetooth: RFCOMM TTY layer initialized
May  9 00:43:55 Doctor kernel: [   13.226042] Bluetooth: RFCOMM socket layer initialized
May  9 00:43:55 Doctor kernel: [   13.226044] Bluetooth: RFCOMM ver 1.11
May  9 00:43:55 Doctor kernel: [   13.268537] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May  9 00:43:55 Doctor kernel: [   13.268539] Bluetooth: BNEP filters: protocol multicast
May  9 00:43:55 Doctor kernel: [   13.310298] hda_codec: ALC269: SKU not ready 0x598301f0
May  9 00:43:55 Doctor kernel: [   13.474640] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
May  9 00:43:55 Doctor kernel: [   13.474707] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
May  9 00:43:55 Doctor kernel: [   13.474781] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
May  9 00:43:55 Doctor kernel: [   13.474842] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
May  9 00:43:55 Doctor kernel: [   13.668566] init: anacron main process (1035) killed by TERM signal
May  9 00:43:55 Doctor kernel: [   13.717012] tg3 0000:02:00.0: irq 44 for MSI/MSI-X
May  9 00:43:55 Doctor kernel: [   13.717016] tg3 0000:02:00.0: irq 45 for MSI/MSI-X
May  9 00:43:55 Doctor kernel: [   13.717020] tg3 0000:02:00.0: irq 46 for MSI/MSI-X
May  9 00:43:55 Doctor kernel: [   13.717023] tg3 0000:02:00.0: irq 47 for MSI/MSI-X
May  9 00:43:55 Doctor kernel: [   13.717026] tg3 0000:02:00.0: irq 48 for MSI/MSI-X
May  9 00:43:56 Doctor kernel: [   14.289617] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  9 00:43:56 Doctor kernel: [   14.290418] ADDRCONF(NETDEV_UP): eth0: link is not ready
**May  9 00:43:56 Doctor kernel: [   14.369338] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 16000000, was 12060000**
May  9 00:43:56 Doctor kernel: [   14.597105] init: plymouth-stop pre-start process (1350) terminated with status 1
May  9 00:44:09 Doctor kernel: [   27.317571] eth1: no IPv6 routers present
May  9 00:44:34 Doctor kernel: [   52.285020] [Firmware Bug]: battery: (dis)charge rate invalid.
May  9 00:49:12 Doctor kernel: imklog 5.8.6, log source = /proc/kmsg started.

---

### Post by Dr.tilik on 2013-05-13
After searching I think I discovered the source of my error, the kernel. 
Anyone could tell me how to update my lowatency kernel in a reliable way if it is possible? 

Thanks in advance!

---

