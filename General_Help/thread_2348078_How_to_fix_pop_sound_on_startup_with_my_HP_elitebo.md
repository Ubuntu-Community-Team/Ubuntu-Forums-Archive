---
title: "How to fix pop sound on startup with my HP elitebook 840?"
date: 2016-12-31
forum: General Help
---

### Post by ascripting on 2016-12-31
Hi

When I boot my HP elitebook 840 laptop, I hear loud pop sound from speakers/headset that is externally connected, however, laptop's built-in speaker doesnt do that.

I have already tried:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/373452](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/373452)
```
[LEFT][COLOR=#333333][FONT=monospace]options snd-hda-intel power_save=10[/FONT][/COLOR][/LEFT]
```
Did not fix stuff for me. Not sure if I should adjust this command to my computer or not.

I have also tried this:
[http://askubuntu.com/questions/160882/popping-noise-from-laptop-speakers?rq=1](http://askubuntu.com/questions/160882/popping-noise-from-laptop-speakers?rq=1)
But it did not help either.

Here is output of lspci command:
```
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection (3) I218-LM (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.1 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #2 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1d.0 USB controller: Intel Corporation Wildcat Point-LP USB EHCI Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader (rev 01)
03:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)

```

and here is output of sudo lshw | grep snd:
```
             configuration: driver=snd_hda_intel latency=0
             configuration: driver=snd_hda_intel latency=64


```

Does anyone know how to fix it?

---

