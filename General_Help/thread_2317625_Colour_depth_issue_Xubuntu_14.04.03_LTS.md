---
title: "Colour depth issue Xubuntu 14.04.03 LTS"
date: 2016-03-18
forum: General Help
---

### Post by Ben_Gillam on 2016-03-18
Hi All,

Experiencing an odd issue with one of my xubuntu machines. I have set it up on some unused ex windows 7/8 grade hardware (Aspire XC-603) for the purposes of a slideshow pc in our waiting area running FEH. After getting all my relevant stuff locked down and the slideshow working i put the pc in place. I then swapped the monitor for a bigger one and had to unplug it whilst the machine was on but when I powered back on and restarted the colour depth appeared to have got stuck in what looks like 256 colour rather than the normal 16bit or 24bit I assume it started with after the installer finished.

Ive been googling colour depth and xubuntu/ubuntu/linux in general and all suggest a variation of creating an xorg.conf file if one doesnt exist. Mine didnt have one and have created one using some suggestions on a forum of 

```

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    16
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" 
    EndSubSection
EndSection


```

but this doesnt seem to make any difference.

Any ideas how to fix this? Am i going to have to reload my system? Or is there a way or resetting and redetecting my hardware?

Any advice would be great and any more info I can provide please let me know, seen a few people mention lspci so here that is too 

```
00:00.0 Host bridge: Intel Corporation ValleyView SSA-CUnit (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation ValleyView Gen7 (rev 0c)
00:13.0 IDE interface: Intel Corporation ValleyView 4-Port SATA Storage Controller (rev 0c)
00:14.0 USB controller: Intel Corporation ValleyView USB xHCI Host Controller (rev 0c)
00:1a.0 Encryption controller: Intel Corporation ValleyView SEC (rev 0c)
00:1b.0 Audio device: Intel Corporation ValleyView High Definition Audio Controller (rev 0c)
00:1c.0 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0c)
00:1c.2 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0c)
00:1f.0 ISA bridge: Intel Corporation ValleyView Power Control Unit (rev 0c)
00:1f.3 SMBus: Intel Corporation ValleyView SMBus Controller (rev 0c)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
```


Thanks

---

