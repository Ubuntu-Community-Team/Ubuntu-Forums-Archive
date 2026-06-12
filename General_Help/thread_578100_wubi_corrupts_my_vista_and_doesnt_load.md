---
title: "wubi corrupts my vista and doesnt load"
date: 2007-10-16
forum: General Help
---

### Post by pokekid on 2007-10-16
i instaled it properly and when i boot ubuntu after start up it loads the first screen and then my screen proceeds to fade to black in segments like a wave. i let it sit there for about 30 minutes and when i cancel out and reboot to vista...it says boot up dlls werent located and i have to put the vista cd into my computer and have to repair my vista partition. any help....

---

### Post by ago on 2007-10-17
If you hardreboot you need to run chkdsk /r from windows CD or other recovery CD
The issues are due to missing driver for your videocard
Search this forum for "vesa"

---

### Post by stinger30au on 2007-10-17
rather then use wubi i suggest debian.exe

it can be found here

[http://goodbye-microsoft.com/](http://goodbye-microsoft.com/)

---

### Post by ago on 2007-10-17
debian.exe installs Debian to a dedicated partition, that has advanatages (more robust filesystem, isolation between linux and windows filesystems, hibernation/suspend, slightly faster) and disadvantages (bootloader is replaced, cannot be uninstalled easily, requires you to modify the partition table). If you are ready to do that you can use debian.exe, the Ubuntu Live CD or UNetBootin [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) (for Ubuntu, Fedora and More)

---

