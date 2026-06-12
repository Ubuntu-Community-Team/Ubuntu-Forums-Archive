---
title: "Gaming Mouse Installation Help"
date: 2013-03-28
forum: General Help
---

### Post by SgtHubcap on 2013-03-28
I just got the [COLOR=#000000][FONT=Arial]Perixx MX-2000 gaming mouse. I installed it on windows fine. didnt need any extra drivers or downloads. works with the HID built it drivers. Is there anyway i can get help installing this on to ubuntu. Ive tried with ndiswrapper with not much success. I dont know what to do, any help or advice would help.Thanks
[/FONT][/COLOR]
```
USB 00.1: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: 8e8U.gKgsKAf4_iE
  Parent ID: pBe4.Uu0aCsrHYoB
  SysFS ID: /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2:1.1
  SysFS BusID: 2-2:1.1
  Hardware Class: unknown
  Model: "Holtek USB Gaming Mouse"
  Hotplug: USB
  Vendor: usb 0x04d9 "Holtek Semiconductor, Inc."
  Device: usb 0xa067 "USB Gaming Mouse"
  Revision: "1.16"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Speed: 12 Mbps
  Module Alias: "usb:v04D9pA067d0116dc00dsc00dp00ic03isc00ip02"
  Driver Info #0:
    Driver Status: usbhid is active
    Driver Activation Cmd: "modprobe usbhid"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #62 (Hub)




```

---

### Post by SgtHubcap on 2013-03-29
bump*

---

### Post by Mark Phelps on 2013-03-29
First of all, ndiswrapper is only for wireless networking -- it has nothing to do with pointing devices.

Second, according to what you posted the module for HID is already installed and running (usbhid).

So, if you're having problems, you need to describe them.

---

### Post by SgtHubcap on 2013-03-29
Mouse has power but, doesnt move courser. Ive started with that mouse plugged in alone and still doesnt work. I have to resort to my older leaser mouse. I also installed stock mouse software, for programming. Its doesnt change colour of mouse so i believe its not connect correctly. Any Questions will happily answer. Thanks again

---

### Post by SgtHubcap on 2013-04-04
Found a fix!! follow instructions compile takes about 1hr or so. Thanks to [Florian Diesch]("http://askubuntu.com/users/2369/florian-diesch") & [njallam]("http://askubuntu.com/users/72212/njallam") for the fix 

[http://askubuntu.com/questions/232564/sharkoon-drakonia-gaming-mouse-doesnt-work-at-all](http://askubuntu.com/questions/232564/sharkoon-drakonia-gaming-mouse-doesnt-work-at-all)

---

### Post by Canezila on 2013-05-27
** bump

---

