---
title: "Dual-boot Ubuntu &amp; XP trouble.."
date: 2008-03-21
forum: General Help
---

### Post by Kristin on 2008-03-21
Here's the issue -- I successfully installed Ubuntu onto my laptop, used GParted to resize my main primary partition in order to dual-boot with Windows XP, but when I pop in the XP disk to install it into the unallocated space I get an error saying that the setup wizard is unable to detect any hard disk drives!  I don't understand what the problem could be.  I did notice, though, that when I installed Ubuntu for some reason the partition manager recognized my HDD as an SCSI device because it installed Ubuntu under the directory /dev/sda1. As far as I know, HDD IDE's are traditionally installed under the directory /dev/hda.. could that have something to do with it possibly?

Any help is really appreciated!

Kristin

---

### Post by Herman on 2008-03-21
Most people have Windows installed first and then install Ubuntu.
You *should* be able to do it the other way around, but Windows can be a bit finicky and temperamental about sharing the hard drive with another operating system. It depends on what kind of a Windows CD you have. Some are okay, others won't install and some wipe the entire hard drive and claim it all for Windows XP.

If you haven't put very much work into your Ubuntu installation yet, consider deleting it and installing Windows first, then Ubuntu.
Or better yet just use Ubuntu and don't bother with Windows XP.

Regards, Herman :)

---

### Post by Kristin on 2008-03-21
Here is another strange detail to the problem -- When I first realized this was going to be an issue I actually wiped out Ubuntu, in order to install Windows first in hopes that the problem was due to the fact that there was already an operating system in place and that Windows was just being stubborn.
When I went back to re-install Windows, the I got the same error!  No hard disks able to be detected.., there was no other OS installed at that point.  I am wondering what could cause the MS install disk to not recognize my HDD?

---

### Post by sandysandy on 2008-03-21
have u formatted the hard disk to NTFS with gparted ?

regards

---

### Post by Kristin on 2008-03-22
Yes, I did make sure to format the space to NTFS before attempting to install Windows XP on it.

---

### Post by sandysandy on 2008-03-22
>  I actually wiped out Ubuntu, in order to install Windows first

after booting with live CD

please post output of [COLOR="Blue"]sudo fdisk -lu[/COLOR] (in terminal)

regards

---

