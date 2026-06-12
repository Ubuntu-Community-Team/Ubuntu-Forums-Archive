---
title: "Booting to command line, not gui Kubuntu 12.04"
date: 2013-05-22
forum: General Help
---

### Post by Waddle on 2013-05-22
Strange behavior..about half the time the computer boots directly into the the desktop, the other half of the time it boots to the command line just befor it checks the battery state. I've tried different kernels and different Nvidia drivers (Nvidia GTX 460) but the results are the same. I'm running KDE 4.1.3 from Kubuntu backports. The system runs stabe and I can even access the Nvidia system settings showing the proper drivers. But if you look at the printout below you will see it is saying there is an error and that no driver is activated.  When it boots to the command line I can log-in and startx and it boots fine. 

> wallace@wallace-P35C-DS3R:~$ hwinfo --gfxcard --monitor
> hal.1: read hal dataprocess 2790: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
27: PCI 100.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.318]
  Unique ID: VCu0.Kyva9gIytI3
  Parent ID: vSkL.aGagsEhnrb7
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "nVidia VGA compatible controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0e22 
  Revision: 0xa1
  Driver: "nvidia"
  Driver Modules: "nvidia"
  Memory Range: 0xf4000000-0xf5ffffff (rw,non-prefetchable)
  Memory Range: 0xe0000000-0xe7ffffff (ro,non-prefetchable)
  Memory Range: 0xe8000000-0xebffffff (ro,non-prefetchable)
  I/O Ports: 0xb000-0xbfff (rw)
  Memory Range: 0xec000000-0xec07ffff (ro,non-prefetchable,disabled)
  IRQ: 16 (136091 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v000010DEd00000E22sv00000000sd00000000bc03sc00i00"
  Driver Info #0:
    Driver Status: nvidiafb is not active
    Driver Activation Cmd: "modprobe nvidiafb"
  Driver Info #1:
    Driver Status: nouveau is not active
    Driver Activation Cmd: "modprobe nouveau"
  Driver Info #2:
    Driver Status: nvidia_experimental_310 is not active
    Driver Activation Cmd: "modprobe nvidia_experimental_310"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #9 (PCI bridge)
wallace@wallace-P35C-DS3R:~$ 


---

### Post by dino99 on 2013-05-22
have you set a too short time delay to boot inside grub ?
if you have not recently clean your system, then do it: clean/autoclean/autoremove/bleachbit

---

