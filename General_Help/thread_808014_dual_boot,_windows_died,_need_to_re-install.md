---
title: "dual boot, windows died, need to re-install"
date: 2008-05-26
forum: General Help
---

### Post by scimitar123 on 2008-05-26
Hi

I have ubuntu and windows on a dual boot.Some stuff went wrong with windows (naturally) and i need to reinstall it. I wanted to check here, seeing as this is a dual boot system if there is a special way in which i need to do it? Windows was originally installed first so i dont know if installing it again once ubuntu changed all the partitions is ok?

Is it just a case of booting from the install disk and continuing as usual?


Any help much appreciated.

Alan

---

### Post by jhorto1 on 2008-05-26
I'm pretty much a n00b to linux myself, so please correct me if I'm wrong.

I'd say you re-install windows to it's original partition. This will probably wipe your grub boot loader though.

Afterwards I think you'll need to use the supergrubdisk [http://www.supergrubdisk.org/index.php](http://www.supergrubdisk.org/index.php)

To restore grub using your existing menu.lst file.

---

### Post by Nameless Neko on 2008-05-26
How exactly do you have it set up?  Two separate partitions on one hard drive, or one OS on one drive and the other on a separate drive?

If they're on two separate drives, it's pretty easy to fix.  Just physically unplug the drive with Ubuntu on it before reinstalling Windows so that Windows can't mess with the partitions on the Ubuntu drive, and then plug it back in and make sure you're set to boot from the Ubuntu drive when you get it back up and running.

If it's on one drive, it's a bit trickier.  I think the best bet then would be to install Windows and then boot from the Ubuntu live-cd when it's installed.  Install GRUB in the MBR via the terminal, and you should be set.

This is all, of course, assuming you're using GRUB as your bootloader.  I'm not sure how you'd go about doing this if you're using the XP bootloader, but why would you want to mess with that thing anyway?

---

