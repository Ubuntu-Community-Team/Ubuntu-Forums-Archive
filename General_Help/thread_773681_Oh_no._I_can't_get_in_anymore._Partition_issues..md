---
title: "Oh no. I can't get in anymore. Partition issues."
date: 2008-04-29
forum: General Help
---

### Post by SZF2001 on 2008-04-29
Alright, I messed up my system.

You can see in my attatchments that disk-1 is the Hardy Xubuntu partition and the unallocated space was my old Mint partition. I thought I would just delete it, figure out how to merge all that space later, set Xubuntu as the booting partition, and be done.

Nope. Grub gives me "Error 17" when it tries to find anything. This is being typed with a Live session, and the rt* drivers for the WMP54G card = crap, meaning that if I try and download a bunch of programs my session freezes with no warning. What now? Everything seems intact when I look around in disk-1... And these drivers keep killing my sessions. :(

---

### Post by Koroviev on 2008-04-29
It looks like you need to reinstall GRUB. You can find instructions here [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) or here [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

