---
title: "remove other linux installation"
date: 2007-08-17
forum: General Help
---

### Post by ubiwankanubi on 2007-08-17
I'm dual booting pclinux and ubuntu, and i want to remove pclinux from the computer.
pclinux is taking up /dev/hda1 and showing up on ubuntu as /media/disk  which also makes it automounted and has an icon on my desktop.

how can i either prevent the icon on my desktop from showing up (stop ubuntu from automounting the partition at boot) or uninstall pclinux. 

when I installed the linuxes, i first installed pclinux then ubuntu. if i do mkfs.ext3 /dev/hda1 to erase pclinux, will that destroy grub?

---

### Post by bodhi.zazen on 2007-08-17
yea, you  can format over the top of PCLinuxOS

hard to say 'bout grub, depends on were it is installed (ie are you using /boot on RXLinuxOS or Ubuntu)??? 

If you need you can re-install grub very easily :

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Otherwise, edit /boot/grub/menu.lst and remove the entries for PCLinuxOS

---

