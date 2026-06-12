---
title: "Install XP onto my Ubuntu laptop"
date: 2007-08-16
forum: General Help
---

### Post by leepy123 on 2007-08-16
Long story (cut short)......

Bought new laptop with XP installed
added Ubuntu 7.04 as dual boot (everything working fine)
tried to resize my Ubuntu partition (make it bigger) and managed to delete my XP partition in the process
had some recovery discs I'd made to try and recover the PC back to just XP (discs didn't work)
reinsatlled Ubuntu
now just a full Ubuntu 7.04 120Gb laptop

What's the problem you may ask? Well I actually need XP on my laptop for work / university etc so I'm a bit stuck without it.

My question is this (sorry for the long post):
How do I resize, create a new partition to then be able to install XP onto my hard disk?

Cheers,

Lee

---

### Post by merlinus on 2007-08-16
If your xp disks do not work, then how do you plan to install it?

-merlin

---

### Post by ZipoTe on 2007-08-16
you can use gparted to resize your partitions :)

---

### Post by leepy123 on 2007-08-16
Thanks for the quick replies.

merlinus
The recovery discs aren't just XP. My laptop is a Lenovo produst and has/had a recovery program built in. I had no recovery media delivered with the laptop so the 1st thing I did was make some recovery CD's just in case things went wrong! These are the discs that don't work and I'm currently argueing with Lenovo support to get a recovery CD for free (yes they want me to pay for one!).
I have an XP install disc that I can use anyway but I think I should be entitled to a free one from Lenovo.

ZipoTe
I only have 1 partition though and Ubuntu is installed on it! Is there any way I can create a new partition ready to install XP into?

Cheers,

Lee

---

### Post by anaconda on 2007-08-16
One good solution is to have XP (or win2000) image in vmware in ubuntu.

With an vmware virtual machine you can do practically anything where you need windows for in work/university.

But if your rescue disk is broken then it might be difficult. 

There are programs, which can rescue data drom faulty CD:s and make a new working copy of it..

---

### Post by merlinus on 2007-08-16
Since windows runs best when it is on the first partition, I suggest starting over.

Install xp, and then install ubuntu.  The partitioner will allow you to shrink xp to make room.

If you have already done a fair bit of customization and installation of applications in ubuntu, then use gparted live cd to shrink the ubuntu parttion from left to right and make space at the beginning of your hdd for xp.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by ugm6hr on 2007-08-16
> **leepy123 said:**
> I only have 1 partition though and Ubuntu is installed on it! Is there any way I can create a new partition ready to install XP into?


Just shrink the Ubuntu partition (and it should be 2 partitions - inc swap) in GParted (**running from LiveCD** - I recommend the actual GParted LiveCD, but Ubuntu LiveCD will work just as well), and add a new PRIMARY partition (as NTFS or fat32) for XP in the newly created space.

Then boot from your XP install CD (or Lenovo recovery if you prefer), point it towards the newly created partition.  Tell it to format the partition during the install, then wait for 4 hours while XP reinstalls.

You will then have to restore GRUB in order to access Ubuntu again - have a search for it in these forums - the question's been asked loads of times.

EDIT: merlinus option would actually be a lot easier....

---

### Post by ZipoTe on 2007-08-16
As someone said, gparted live CD is what you should use to resize your partition. It should work and it's quite easy to do.

---

### Post by Steve1961 on 2007-08-16
Your Lenovo recovery discs don't work because when you installed Ubuntu and used Grub for dual booting you wrote over the customised mbr that Lenovo provides.  You have a number of options:

1. restore the thinkpad mbr - [http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-62978](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-62978)

then just hit f11 when booting to restore windows from the hidden partition

2. restore the thinkpad mbr and then hit the access ibm button and restore from your diskc

3. Just use your existing disk to install using the COD on the back of the machine to a partition of your choice

1 and 2 will overwrite the entire disk and wipe out Ubuntu, but you have more flexibility with 3.

As an aside, if you want to retain teh customised thinkpad mbr when dual booting use the nt bootloader to boot Ubuntu

---

### Post by leepy123 on 2007-08-16
Thanks for all the help guys.

Just got off the phone with Lenovo support and they immedietly agreed to send me out some recovery CD's to recover the laptop to it's factory default state.
I think my best option is to use these CD's to recover to factory default (i.e. XP only) then set up a dual boot again only this time give Ubuntu more HDD space.

Lee

---

