---
title: "Ubuntu XP Dual Boot-Grub Error 17"
date: 2008-04-25
forum: General Help
---

### Post by notesetter on 2008-04-25
Hello.

System:
Compaq Presario Laptop (US 2170)
Intel Celeron 2.0 gHz
80 GB HDD
256 MB RAM

Problem:

I like Ubuntu Studio but I need XP to run some work-related applications. So, after (foolishly) messing up my system by trying to upgrade to Hardy without enough memory, I decided that it would be the perfect opportunity to go ahead and re-load XP and set up the dual-boot with Ubuntu Studio 7.10 (and wait to upgrade until after I install new RAM)

After attempting to load XP on the system, when I now try to boot into Windows I get the following message:

Grub 1.5 starting
please wait...
Error 17

How can I remove Grub so that I may do a fresh install of XP, so that I may then install Ubuntu Studio 7.10 on a partition?

Thanks,

Dave

---

### Post by fearful on 2008-04-25
You need to go into the BIOS and set the CD to be the first device to boot, put the hard drive second.
Do you have Windows installed already? If so, boot from the CD, enter the recovery console (press R when it asks you whether you want to install windows etc.) When you're at the console, type:

fixmbr

and that will remove GRUB from your system.

If you don't have Windows installed, GRUB will be overwritten as part of the installation.

Rgds 
Ben

---

### Post by Perpetual on 2008-04-25
> **notesetter said:**
> Hello.

System:
Compaq Presario Laptop (US 2170)
Intel Celeron 2.0 gHz
80 GB HDD
256 MB RAM

Problem:

I like Ubuntu Studio but I need XP to run some work-related applications. So, after (foolishly) messing up my system by trying to upgrade to Hardy without enough memory, I decided that it would be the perfect opportunity to go ahead and re-load XP and set up the dual-boot with Ubuntu Studio 7.10 (and wait to upgrade until after I install new RAM)

After attempting to load XP on the system, when I now try to boot into Windows I get the following message:

Grub 1.5 starting
please wait...
Error 17

How can I remove Grub so that I may do a fresh install of XP, so that I may then install Ubuntu Studio 7.10 on a partition?

Thanks,

Dave

Grab a Windows boot disk and run [fixmbr]("http://support.microsoft.com/kb/314058") (fix windows master boot record) to get rid of grub.

Edit: I am too slow :)

---

### Post by Naatan on 2008-04-25
Just to clarify; you don't have to reinstall either OS in order to restore their boot managers, for windows you can do what fearful suggested, as for Ubuntu; that's a bit more complicated.. boot the livecd, enter a console and enter;

$ grub
$ root (hd0,1)
$ setup (hd0)
$ quit

Note that hd0 refers to which HD the OS'es are on, most of the time hd0 is correct.
hd0,1 stands for the first partition on hd0, so this depends on your partition layout, if you installed windows on your "first" partition and ubuntu on the "second" then use hd0,2. You can find out which ones are on what partition by running the installation and going into the manual partitioning screen, write down the values and cancel the installation.

You can add Windows to the grub menu by editing the "/boot/grub/menu.lst" file

goodluck!

---

### Post by notesetter on 2008-04-27
Thanks all. I've now removed GRUB and am on my way to setting up my dual-boot system.

Dave

---

