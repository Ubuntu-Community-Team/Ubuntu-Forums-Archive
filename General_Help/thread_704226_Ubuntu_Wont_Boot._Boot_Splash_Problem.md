---
title: "Ubuntu Wont Boot. Boot Splash Problem"
date: 2008-02-22
forum: General Help
---

### Post by Dojan5 on 2008-02-22
Well, I installed a Boot Splash from GNOME-Look.org and. Well.
The system crashed during the installation.
Now, How should i fix this?

This is my var\logs\messages
```
Feb 21 18:51:40 Kissedesigns-2c -- MARK --
Feb 21 19:11:42 Kissedesigns-2c -- MARK --
Feb 21 19:31:49 Kissedesigns-2c -- MARK --
Feb 21 19:51:51 Kissedesigns-2c -- MARK --
Feb 21 20:12:03 Kissedesigns-2c -- MARK --
Feb 21 20:32:04 Kissedesigns-2c -- MARK --
Feb 21 20:52:04 Kissedesigns-2c -- MARK --
Feb 21 21:12:05 Kissedesigns-2c -- MARK --
Feb 21 21:32:06 Kissedesigns-2c -- MARK --
Feb 21 21:52:06 Kissedesigns-2c -- MARK --
Feb 21 22:12:06 Kissedesigns-2c -- MARK --
Feb 21 22:32:15 Kissedesigns-2c -- MARK --
Feb 21 22:52:21 Kissedesigns-2c -- MARK --
Feb 21 23:12:21 Kissedesigns-2c -- MARK --
Feb 21 23:32:24 Kissedesigns-2c -- MARK --
Feb 21 23:52:29 Kissedesigns-2c -- MARK --
Feb 22 00:12:31 Kissedesigns-2c -- MARK --
Feb 22 00:32:35 Kissedesigns-2c -- MARK --
Feb 22 00:52:37 Kissedesigns-2c -- MARK --
Feb 22 01:12:38 Kissedesigns-2c -- MARK --
Feb 22 01:32:45 Kissedesigns-2c -- MARK --
Feb 22 01:52:47 Kissedesigns-2c -- MARK --
Feb 22 02:11:11 Kissedesigns-2c exiting on signal 15
```

The boot-splash was a screen with a circle thingy instead of the loading progress bar, Like in MAC.

Please help. id rather not reinstall Ubuntu.
Anyhow, I cant use the computer at all since it sorta freezes on a black sxreen.
Im stuck with a Live session. Is it possible to correct it wihoout reinstalling ubuntu.
Thanks
/
Joel

---

### Post by kesman on 2008-02-22
From the livesession, edit your /boot/grub/menu.lst -file's boot section in bottom of the file NOT to contain the words "splash" and "quiet" and then save the file and try rebooting your computer.
Be sure that you don't edit the file for LiveCD, but your actual linux installation.

---

### Post by Dojan5 on 2008-02-22
> **kesman said:**
> From the livesession, edit your /boot/grub/menu.lst -file's boot section in bottom of the file NOT to contain the words "splash" and "quiet" and then save the file and try rebooting your computer.
Be sure that you don't edit the file for LiveCD, but your actual linux installation.

Thanks for yer tip. I saw that in another topc and tried it. It didnt work.
I reinstalled Ubuntu and now everything works fine.
Thanks anyway.

---

