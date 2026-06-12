---
title: "Unistalling Ubuntu on a Dual Boot Laptop, With No CD Drive"
date: 2014-09-24
forum: General Help
---

### Post by jamesva3 on 2014-09-24
I have windows 7 pre-installed on a w110ER laptop. I installed Ubuntu shortly after i got my pc and haven't touched it in the 2 years I have had my laptop. Now I am migrating everything from my old hard drive to a new SSD, and I am cutting out the excess data, and Ubuntu needs to go. I have done some google searches, but none show how to uninstall ubuntu without a cd drive. I want to do this safely and do not want to brick my pc so I would really appreciate advice and help.

---

### Post by amoun on 2014-09-24
Ubuntu should be on a separate partition which you can delete.

---

### Post by jamesva3 on 2014-09-24
Don't I need to do something with the bootloader?

---

### Post by amoun on 2014-09-24
Yes you can manually change the bootloader, I'm sure you can find help on that but "and I am cutting out the excess data, and Ubuntu needs to go" you will get rid of 99.99999% of the excess data anyway

I thought win 7 has a backup partition which you can use in lieu of a CD

[http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)

have you been to

[http://www.tomshardware.co.uk/forum/67104-63-uninstall-ubuntu-windows](http://www.tomshardware.co.uk/forum/67104-63-uninstall-ubuntu-windows)

---

### Post by ajgreeny on 2014-09-24
**DON'T DELETE UBUNTU WITHOUT GETTING THE WINDOWS BOOTLOADER** [B]RESTORED FIRST !.
[/B]
Sorry to shout, but if you don't restore the windows bootloader before removing the Ubuntu partition you will find yourself at a grub prompt with nowhere else to go, so whilst amoun is basically correct, doing what was suggested could have dropped you right in the middle of a mess with no computer to use to search for information on a solution.

Regrettably I can not help with details of restoring windows bootloader for Win 7.  For XP you could use a Ubuntu live system, install lilo to that, and with a simple couple of commands put a basic but effective Windows bootloader back on disk.  It may still work for Win 7, and I think it does, but I do not know for sure, so I suggest you search that out in more detail.

EDIT:
A quick search shows that it is still possible to use a live system and lilo installation, or also by using the **Boot-repair** available from the link in my signature.

PS:
Was this a full partitioned installation of Ubuntu or did you install with wubi, ie, within a running Windows system.  If you used wubi you can simply uninstall ubuntu using the windows **add/remove software** option in **control-centre**.

---

### Post by coffeecat on 2014-09-24
Restoring Windows 7 bootloader either with a Windows 7 install/repair disc or with a live Ubuntu USB:

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Without a CD drive, you'd probably want to go the live Ubuntu USB route, but another possibility is to run either the lilo or dd command from your installed Ubuntu to restore the Windows bootloader, and then delete the Ubuntu partition from within Windows.

One caveat. Make sure you don't have a wubi installation. If so, you simply uninstall it from within Windows as you would any Windows application.

---

