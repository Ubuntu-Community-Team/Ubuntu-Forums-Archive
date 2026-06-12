---
title: "Ubuntu 19.04 / sound card not in alsa but in lspci"
date: 2019-10-19
forum: General Help
---

### Post by nestorcayce on 2019-10-19
Dear All, 

I've installed Ubuntu 19.04 for my kids on old barebone Shuttle SD37P2 (Vendor doc says that Audio is ALC882)
(just added an SDD so it's more comfortable). 

Already wasted few hours to troubleshoot my no sound issue...
**Could an external USB card be an option ? (any cheap model to recommend ?) **

Thanks for your support / info below:

The only audio card that seems to be properly installed is the HDMi one (but I've no speakers on my monitor)
/proc/asound/card0 => folder is empty
/proc/asound/card1 => contains info related to HDMI


Alsa report: [Report Alsa]("http://alsa-project.org/db/?f=9042b0637e2f2e896f451aa2e0391f61ef72b40a")  (visible at the bottom=> **snd_hda_intel 0000:00:1b.0: no codecs found!**)

From hardware info (integrated chip on the motherboard is well detected, as well as the HDMi): 

```

hwinfo --sound
14: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.386]
  Unique ID: u1Nb.dvotA5wWJK1
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel NM10/ICH7 Family High Definition Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27d8 "NM10/ICH7 Family High Definition Audio Controller"
  Revision: 0x01
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfdff8000-0xfdffbfff (rw,non-prefetchable)
  IRQ: 24 (no events)
  Module Alias: "pci:v00008086d000027D8sv00000000sd00000000bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

21: PCI 200.1: 0403 Audio device
  [Created at pci.386]
  Unique ID: 2Oa+.j18tSRZEo21
  Parent ID: 3hqH.JVqAOgaj8O4
  SysFS ID: /devices/pci0000:00/0000:00:03.0/0000:02:00.1
  SysFS BusID: 0000:02:00.1
  Hardware Class: sound
  Model: "ATI Juniper HDMI Audio [Radeon HD 5700 Series]"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0xaa58 "Juniper HDMI Audio [Radeon HD 5700 Series]"
  SubVendor: pci 0x1458 "Gigabyte Technology Co., Ltd"
  SubDevice: pci 0xaa58 
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfd8fc000-0xfd8fffff (rw,non-prefetchable)
  IRQ: 25 (231 events)
  Module Alias: "pci:v00001002d0000AA58sv00001458sd0000AA58bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #19 (PCI bridge)

```

lspci gives: 
```

lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Juniper HDMI Audio [Radeon HD 5700 Series]

```

Alsamixer fails with *no files or folder.*.. (sorry it's in french, I don't know the exact message in english)

Already tried with no luck: 
*```
sudo apt install ubuntu-restricted-extras 
```*

---

### Post by mörgæs on 2019-10-20
Hi, welcome to the fora.
Questions like this have a better change of being answered in the multimedia forum. If you click Report you can ask a moderator to move it.

---

