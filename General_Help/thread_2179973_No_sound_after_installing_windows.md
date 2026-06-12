---
title: "No sound after installing windows"
date: 2013-10-10
forum: General Help
---

### Post by JaySeeJC on 2013-10-10
So i've had this laptop for about a year now, and decided to install windows 8 on the side to see what all the fuss was about. Unfortunately, it seems as though my speakers have been wiped off the face of the earth as far as ubuntu is concerned. All other audio devices work, HDMI, headphones and mic, just the speakers are gone. The situation is the same with live USBs as well, and not just ubuntu based ones. 


```
$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 630M] (rev ff)
07:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10)
08:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
09:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)

$ dmesg
...
[   28.411216] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   28.411465] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   28.662418] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   28.662482] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   28.662535] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   28.712636] Linux video capture interface: v2.00
...


```

alsamixer:
[IMG]http://i.imgur.com/kJ9dyHS.png[/IMG]

alsainfo.sh
[http://www.alsa-project.org/db/?f=2ef3939242d99e358ebea948a13f4b83e68ca80e](http://www.alsa-project.org/db/?f=2ef3939242d99e358ebea948a13f4b83e68ca80e)

sound settings (cinnamon):
[IMG]http://i.imgur.com/icaP2UL.png[/IMG]
^ neither output works

---

### Post by JaySeeJC on 2013-10-10
So i've found a workaround. It seems uninstalling the drivers windows side works, leaving me with tinny sounding speakers. It works good enough for now, but a better solution is more than welcome.

---

