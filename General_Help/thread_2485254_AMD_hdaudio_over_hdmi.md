---
title: "AMD hdaudio over hdmi"
date: 2023-03-24
forum: General Help
---

### Post by ranger671 on 2023-03-24
version Ubuntu 22.10

during normal patching Ubuntu pushed from kernel 5.19.0-31 to 5.19.0-35. After this push, I lost audio from my AMD RX570 hdmi. I booted back to -31 waiting for the next kernel push in the hopes the problem would be caught and addressed. It wasn't and still persists in -38. The card info is below.

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] (rev ef)
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590]

root@xxxxx:~# hwinfo --sound
35: PCI 100.1: 0403 Audio device                                
  [Created at pci.386]
  Unique ID: NXNs.TsyFmhFLPLA
  Parent ID: mnDB.fA+tdbAkMSD
  SysFS ID: /devices/pci0000:00/0000:00:01.1/0000:01:00.1
  SysFS BusID: 0000:01:00.1
  Hardware Class: sound
  Model: "ATI Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590]"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0xaaf0 "Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590]"
  SubVendor: pci 0x1458 "Gigabyte Technology Co., Ltd"
  SubDevice: pci 0xaaf0 
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfcf60000-0xfcf63fff (rw,non-prefetchable)
  IRQ: 86 (5 events)
  Module Alias: "pci:v00001002d0000AAF0sv00001458sd0000AAF0bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #31 (PCI bridge)



The errors I am getting during intialization are:

[    4.895282] hdaudio hdaudioC0D0: no AFG or MFG node found
[    4.895306] snd_hda_intel 0000:01:00.1: no codecs initialized


and if I try to validate the card

root@xxxxx:~# aplay -l
aplay: device_list:274: no soundcards found...

I have tried passing numerous arguments to the module but to no avail. Booting back to -31 brings the card right back to functioning. I believe there has been an update to snd_hda_intel which is causing this issue and is most likely a regression situation. Can anyone assist? I have searched for a model to be passed specific to AMD cards, but can't find one. Any suggestions would be greatly appreciated. Additionally, I'm wondering if this should be directed to Ubuntu, or should it go to kernel.org the HD-Audio group? Again, thanks for your thoughts.

options snd_hda_intel dmic_detect=0
options snd_hda_intel model=generic
options snd_hda_intel model=auto

options snd_hda_intel probe_mask=1
options snd-intel-dspcfg dsp_driver=1

---

### Post by Claus7 on 2023-03-24
Hello and welcome to the forums,

just a minor idea: if this was related to ubuntu you could try to boot from a usb iso of another linux distribution using the same kernels just to check if it is working. I would try also the latest ubuntu (lunar) with kernel 6.2 to check out if the issue is fixed. Unless you are not intending to stay with 22.10, which soon will be EOL, trying lunar would be the best option to my opinion.

Regards!

---

### Post by DuckHook on 2023-03-24
Please see earlier thread:

[https://ubuntuforums.org/showthread.php?t=2484563](https://ubuntuforums.org/showthread.php?t=2484563)

Kernel 5.19.0-35 has a regression that breaks the HDMI sink on AMD graphics cards. Until the devs issue a fix in a new kernel, you must work around the issue by loading the older kernel at boot.

As mentioned in linked thread, you may wish to pin (apt-mark hold) the older kernel just in case.

---

