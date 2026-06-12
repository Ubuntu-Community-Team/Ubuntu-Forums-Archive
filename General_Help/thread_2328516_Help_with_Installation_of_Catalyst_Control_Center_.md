---
title: "Help with Installation of Catalyst Control Center Radeon 2400 PRO"
date: 2016-06-21
forum: General Help
---

### Post by ken55 on 2016-06-21
```
  PCI 200.0: 0300 VGA compatible controller (VGA)
  [Created at pci.366]
  Unique ID: B35A.4Thn76XFb02
  Parent ID: WL76.lW0IfrjOTIA
  SysFS ID: /devices/pci0000:00/0000:00:09.0/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: graphics card
  Model: "ATI RV610 [Radeon HD 2400 PRO]"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x94c3 "RV610 [Radeon HD 2400 PRO]"
  SubVendor: pci 0x1545 "VISIONTEK"
  SubDevice: pci 0x3210 
  Driver: "radeon"
  Driver Modules: "drm"
  Memory Range: 0xe0000000-0xefffffff (ro,non-prefetchable)
  Memory Range: 0xfdde0000-0xfddeffff (rw,non-prefetchable)
  I/O Ports: 0xbc00-0xbcff (rw)
  Memory Range: 0xfdd00000-0xfdd1ffff (ro,non-prefetchable,disabled)
  IRQ: 27 (82056 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001002d000094C3sv00001545sd00003210bc03sc00i00"
  Driver Info #0:
    Driver Status: radeon is active
    Driver Activation Cmd: "modprobe radeon"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #21 (PCI bridge)
```

Having issues with overscan when connected to the tv via HDMI, I have been searching for a way to install CCC on this pc, but having zero luck. If anyone can point me in the right direction, I would greatly appreciate it. I am pretty new to linux, so please speak to me as such. ;)

Thanks in advance,
Ken

---

### Post by QIII on 2016-06-21
Unfortunately, AMD dropped Linux support for that GPU eight or ten years ago.

The only thing you can do is continue to use the open source Radeon driver that is installed by default.

---

### Post by ken55 on 2016-06-21
> **QIII said:**
> Unfortunately, AMD dropped Linux support for that GPU eight or ten years ago.

The only thing you can do is continue to use the open source Radeon driver that is installed by default.

How would I go about getting rid of overscan on the TV though? The television has no options to do so.

---

### Post by X-RED_Tech on 2016-06-22
> **ken55 said:**
> The television has no options to do so.

Only very old (flat) TVs miss that option. If you post the brand/model I can try to find out. If it really has no such setting then perhaps xrandr can do it but I'm not sure, never had to use any software to do that, always adjusted it in the TV itself.

---

### Post by ken55 on 2016-06-22
> **X-RED_Tech said:**
> Only very old (flat) TVs miss that option. If you post the brand/model I can try to find out. If it really has no such setting then perhaps xrandr can do it but I'm not sure, never had to use any software to do that, always adjusted it in the TV itself.

It is quite old, around 10 years or so. It's a Symphonic WF32L6. 720P LCD HDTV. 
[h=1][/h]Thanks Alot,
Ken

---

### Post by X-RED_Tech on 2016-06-22
Here's your manual: [https://mega.nz/#!IFshSLSR!4u76H0dZwN5_X0mn5Q1bI5lxyEck7Ui05ECDcxRM11Q](https://mega.nz/#!IFshSLSR!4u76H0dZwN5_X0mn5Q1bI5lxyEck7Ui05ECDcxRM11Q)
Check page 21. One of the modes should be just right. "Full" is usually the one in other brands but you need to test yours.

---

### Post by ken55 on 2016-06-22
> **X-RED_Tech said:**
> Here's your manual: [https://mega.nz/#!IFshSLSR!4u76H0dZwN5_X0mn5Q1bI5lxyEck7Ui05ECDcxRM11Q](https://mega.nz/#!IFshSLSR!4u76H0dZwN5_X0mn5Q1bI5lxyEck7Ui05ECDcxRM11Q)
Check page 21. One of the modes should be just right. "Full" is usually the one in other brands but you need to test yours.

Thank you for that. The problem is I don't have the remote to the TV, and I haven't seen a way to access those settings using the buttons on the actual TV. I can get into the setup menu, but that is about it.

---

### Post by X-RED_Tech on 2016-06-22
Well, you know, flatscreen TVs including 4K, are cheaper than ever. I wouldn't bother with a "HD Ready" (not full HD) device today, without even the remote that would be necessary to set things right for a PC video source (the default is underscan because of the cable service providers' boxes).

Someone experienced with xrandr or something similar might be able to help you with that.

---

