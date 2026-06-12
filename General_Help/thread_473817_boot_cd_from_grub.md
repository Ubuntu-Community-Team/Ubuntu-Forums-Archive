---
title: "boot cd from grub"
date: 2007-06-14
forum: General Help
---

### Post by Greykrrr on 2007-06-14
Hi

I have been struggling for some time to make me laptop boot from cd without success. One way around this would be to make an menu entry in grub that would boot a cd. Is there a way to do this?

---

### Post by confused57 on 2007-06-14
> **Greykrrr said:**
> Hi

I have been struggling for some time to make me laptop boot from cd without success. One way around this would be to make an menu entry in grub that would boot a cd. Is there a way to do this?
Found this in the Gentoo Wiki:
[http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB](http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB)

If you have a floppy drive, you can just make a SBM boot floppy:
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)
[http://ubuntuforums.org/showthread.php?t=246486](http://ubuntuforums.org/showthread.php?t=246486)

---

### Post by RocketRanger on 2007-06-14
Thanks. However the buildstep fails for me and I can't download the premade imagefiles as the links asks for username and password. So that kind of stops there. And as a final problem, the guide wants me to create a floppy which I can't as I don't have a floppy drive in my laptop.

Alternatively. Is it possible to make grub boot an iso file?

Any other ideas?

---

### Post by confused57 on 2007-06-14
Maybe this will work:
[http://doc.gwos.org/index.php/Install_Edgy_6.10_from_an_.iso_file](http://doc.gwos.org/index.php/Install_Edgy_6.10_from_an_.iso_file)

---

### Post by RocketRanger on 2007-06-14
it's actually not a bad plan and I've bookmarked this for when I need to upgrade my dapper installation. But right now I'm trying to boot a windows disc.

Is there a way to mount the iso as a loopback device in linux and then use grub to boot it afterwards?

---

### Post by logos34 on 2007-06-14
> **RocketRanger said:**
> it's actually not a bad plan and I've bookmarked this for when I need to upgrade my dapper installation. But right now I'm trying to boot a windows disc.

Here's another link similar to confused57's:
[https://help.ubuntu.com/community/Installation/FromLinux?highlight=%28installation%29](https://help.ubuntu.com/community/Installation/FromLinux?highlight=%28installation%29)

I used it successfully for a Xubuntu 7.04 install (alternate install version) straight from hard disk.  

> Is there a way to mount the iso as a loopback device in linux and then use grub to boot it afterwards?

Good question.  Been wondering about it myself.  Like a special 700MB+ holding partition which grub could boot from in a repeatable fashion using some generic entry in menu.lst, without the need to edit it for each iso, copy kernel and initrd files over, etc.

edit: If your bios allows you to boot from usb, then a usb floppy drive would at least allow you to use the SBM method.

---

