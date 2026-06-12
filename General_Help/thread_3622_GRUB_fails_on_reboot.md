---
title: "GRUB fails on reboot"
date: 2004-11-07
forum: General Help
---

### Post by Ozitraveller on 2004-11-07
Hi

I downloaded the iso and created the cd ok. It boots and starts the install. Everything seemed fine until the second phase of the install, remove the cd and let the os boot up. I get the following messages:

GRUB loading stage1.5

GRUB loading please wait.
ERROR18

At this point it hangs!


hda is 20GB automatically partitioned 
hdb is 30GB /home



I've had an earlier version installed and running ok.

Any help appreciated.

---

### Post by wallijonn on 2004-11-07
Go into your BIOS and set the boot priority to boot from HD first.

---

### Post by Ozitraveller on 2004-11-07
I'll give it a try. 

Thanks.

---

### Post by Monika on 2004-11-12
I just tried installing Ubuntu onto my mum's computer and I can't boot into any system now because when GRUB is supposed to load (I also didn't even complete the whole installation), it says
GRUB Hard Disk Error

I've reinstalled SuSE onto her computer for now because the SuSE GRUB seems to work no problem and thank God - she can use her Windows normally now, but I would like to install Ubuntu for her (since she doesn't use SuSE anyway, we've both found SuSE quite unfriendly).

What is the problem? And why does the GRUB from the SuSE installation work, but the GRUB from the Ubuntu installation doesn't?

---

### Post by FLeiXiuS on 2004-11-12
**Hard Disk Error**
The stage2 or stage1.5 is being read from a hard disk, and the attempt to determine the size and geometry of the hard disk failed. 

Sounds to me like an old drive, or bad partitions.

---

### Post by Monika on 2004-11-12
What can I do about it? And also how is it that the problem with GRUB does not occur after a SuSE linux installation? If it was a bad hard disk then it should cause problems for all linuxes, no?

I don't know much about partitioning but what could be wrong with the partitions? I didn't do the original windows/linux setup, my mum's computer needed to have windows and everything possible reinstalled anyway, so we asked for it to be partitionedso that about half the drive is for windows and half for linux and all this was done at a professional computer service place (they did my computer too and mine's running Ubuntu fine). I know SuSE's default installation which just decides where it will install itself on it's own is not the best and it made some strange decisions (like only using 2 out of 3 or more linux partitions on the computer), but that's exactly why when I was installing Ubuntu, I totally changed the partition set-up for Ubuntu. I deleted the partitions that were set for linux previously, except for the swap partition and made two new ones, one for the system and the other for /home. Surely Ubuntu should work fine on partitions made by its own installer? Or should I delete the swap partition as well and make a new one? Would that help? Somehow I doubt it cause I don't see the logic of that... but, I've no idea what I should do to get it running...

---

### Post by wallijonn on 2004-11-13
[QUOTE=Monika]I totally changed the partition set-up for Ubuntu. I deleted the partitions that were set for linux previously, except for the swap partition and made two new ones, one for the system and the other for /home. Surely Ubuntu should work fine on partitions made by its own installer? Or should I delete the swap partition as well and make a new one? [/QUOTE]

If you think SUSE is not user friendly, I wonder what you think of Ubuntu as there is more manual configuring to be done. You may want to call it tuning or tweaking but the fact remains that the latest SUSE is superior to Ubuntu in many ways, most notably mounting of floppies, the automatic installation of xmms, etc. My problem with SUSE is that it is KDE based and I just do not like KDE and its applications - so I end up stripping SUSE after an install. And like most distros you're tempted to install everything because you do not know what anything is. Ubuntu's streamlined distro is it's biggest asset. That and I love the apps it does come with - Evolution, FireFox, GIMP and OpenOffice. I do not have to uninstall Mozilla, Galeon, Epiphany, KDEOffice, etc., then install FIreFox and Evolution and OpenOffice... 

I fail to see how creating a /home partition will work as you will may have to hack the OS to link to the partition correctly as /home is created usually under / (root). 

The problem may have been that there was a prior GRUB which pointed to different OS and disk geometry. I find that Ubuntu's GRUB cannot clear out an old table unless a new one is completely defined (the table is not written out). All the Linux partitions should be deleted, even the swap space, otherwise fstab may not see and 'mount' the old swap space. I suggest you use the default Ext3fs instead of Reiser. 

I do wish that there were a GRUB install / repair utility, though. I installed Slackware and even though I mounted it on its own / and told it not to write LILO it still completely messed up GRUB. Basically my days of messing around with other distros is over - I have settled upon a distro I love, Ubuntu.

I deleted all the old Linux partitions, and told Ubuntu to use all the free space. It created a EXT3 and swap.

---

### Post by Monika on 2004-11-13
> **wallijonn]If you think SUSE is not user friendly, I wonder what you think of Ubuntu as there is more manual configuring to be done.[/quote]


Well, SuSE might be friendly for some users, but not for me and my mum  said:**
> You may want to call it tuning or tweaking but the fact remains that the latest SUSE is superior to Ubuntu in many ways, most notably mounting of floppies, the automatic installation of xmms, etc.

I only ever used 9.1. I didn't try 9.2

> I fail to see how creating a /home partition will work as you will may have to hack the OS to link to the partition correctly as /home is created usually under / (root). 

Actually when you manually edit partitions in the Ubuntu installer it's quite easy :) I've no idea how I'd go about doing it in the SuSE installer, but all you have to do in Ubuntu is choose the mount point. In fact if you make more than one non-swap linux partition, the Ubuntu installer automatically assumes you'll be mounting it as /home. And it sounds like a very good idea to me since then if I need to reinstall I can only reinstall the base system (choose "keep existing data" for the /home partition and tell the installer where to mount it).

> The problem may have been that there was a prior GRUB which pointed to different OS and disk geometry. I find that Ubuntu's GRUB cannot clear out an old table unless a new one is completely defined (the table is not written out).

I did a very similar thing on my own computer and it worked, although I did delete the swap partition and made a new one...

> All the Linux partitions should be deleted, even the swap space, otherwise fstab may not see and 'mount' the old swap space. I suggest you use the default Ext3fs instead of Reiser. 

I let it do the defaults as far as file systems are concerned and Ext3 is the default I think :) But thanks, maybe I'll try making a new swap then :)

---

### Post by wallijonn on 2004-11-14
Monika, 

Thanks for responding. I'm delighted to hear that you prefer Ubuntu over SUSE. It's a great testimonial.

My concern is that there will be two /home directories - I never got a similarily named directory to work under Red Hat 9; ie, it used the the system named directory  and not the one which I created on a separate partition. If in fact it does work it will be another plus for Ubuntu.

---

