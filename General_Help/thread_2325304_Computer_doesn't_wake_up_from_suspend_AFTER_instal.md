---
title: "Computer doesn't wake up from suspend AFTER installing bcmwl"
date: 2016-05-21
forum: General Help
---

### Post by Itai_Peri on 2016-05-21
Hi all,
I've recently updated from 14.04 to 16.04.
I've got a Dell e7450, with a broadcom BCM4352 (pcid: 14e4:43b1) chip, and like always, there are problems communicating with this chip.
On 14.04 what I did to fix this was to install the dkms and bcmwl from the pool directory in the install USB drive.
I tried to do the same on 16.04, but after the WIfi problem gets fixed, everytime I suspend my computer, when it wakes up from the suspend the screen is black and doesn't show up at all. Tried to do Alt+Ctrl+F1 and then Alt+F7 but it didn't help.

Some info:
```

$ sudo lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Broadwell-U Host Bridge -OPI [8086:1604] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Broadwell-U Integrated Graphics [8086:1616] (rev 09)
00:03.0 Audio device [0403]: Intel Corporation Broadwell-U Audio Controller [8086:160c] (rev 09)
00:04.0 Signal processing controller [1180]: Intel Corporation Broadwell-U Camarillo Device [8086:1603] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation Wildcat Point-LP USB xHCI Controller [8086:9cb1] (rev 03)
00:16.0 Communication controller [0780]: Intel Corporation Wildcat Point-LP MEI Controller #1 [8086:9cba] (rev 03)
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (3) I218-LM [8086:15a2] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation Wildcat Point-LP High Definition Audio Controller [8086:9ca0] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 [8086:9c90] (rev e3)
00:1c.3 PCI bridge [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 [8086:9c96] (rev e3)
00:1c.4 PCI bridge [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 [8086:9c98] (rev e3)
00:1d.0 USB controller [0c03]: Intel Corporation Wildcat Point-LP USB EHCI Controller [8086:9ca6] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation Wildcat Point-LP LPC Controller [8086:9cc3] (rev 03)
00:1f.2 RAID bus controller [0104]: Intel Corporation 82801 Mobile SATA Controller [RAID mode] [8086:282a] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation Wildcat Point-LP SMBus Controller [8086:9ca2] (rev 03)
01:00.0 SD Host controller [0805]: O2 Micro, Inc. SD/MMC Card Reader Controller [1217:8520] (rev 01)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
03:00.0 3D controller [0302]: NVIDIA Corporation GM108M [GeForce 840M] [10de:1341] (rev a2)
$ uname -r
4.4.0-21-generic

```

Thanks for the help!

---

### Post by chili555 on 2016-05-23
I'm not sure you have a wireless problem at all. It sounds like a video problem to me. Before suspend, may I assume the wireless works as expected?> Tried to do Alt+Ctrl+F1 and then Alt+F7 but it didn't help.When you do Ctrl+Alt+F1, do you get a login prompt? Can you log in and see any clues in the logs?```
dmesg 
cat /var/log/syslog | tail -n20
```I don't know much else to ask as I am not allowed in the video department for everyone's protection!

---

