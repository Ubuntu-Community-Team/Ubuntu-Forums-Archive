---
title: "linux-firmware-updater in boot menu"
date: 2022-06-09
forum: General Help
---

### Post by cam17 on 2022-06-09
I received a update few weeks ago and noticed that not only my workstation but another has "Linux-firmware-updater in the boot selection menu. When I select the menu nothing occurs and the option remains in the boot menu of my Lenovo.

How is this update executed? i assume once the update is installed that the boot option should disappears?

---

### Post by oldfred on 2022-06-10
My older motherboard based systems do not support fwupdate, so I totally uninstall it.
See device list to see if yours is supported.

[https://fwupd.org/](https://fwupd.org/)
[https://github.com/fwupd/fwupd](https://github.com/fwupd/fwupd)
[https://github.com/fwupd/fwupd/releases/tag/1.6.0](https://github.com/fwupd/fwupd/releases/tag/1.6.0)
Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

I do not have this anymore, as it would be bland in my case anyway.
sudo fwupdmgr get-devices

If UEFI firmware update not supported (yet), you can totally remove it.
sudo apt-get purge fwupd

---

### Post by cam17 on 2022-06-10
My device is supported but the linux update remains in my boot selection list. That should only be for optional boot selections. the inofmration you provided seems to suggest the update is run form the O.S.

---

### Post by #&amp;thj^% on 2022-06-10
It is ran from the OS IE:
```
 fwupdmgr refresh
``` 
command to check for available firmware updates for your devices.

---

