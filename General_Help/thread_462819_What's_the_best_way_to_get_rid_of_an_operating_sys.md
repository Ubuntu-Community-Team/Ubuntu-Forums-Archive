---
title: "What's the best way to get rid of an operating system?"
date: 2007-06-03
forum: General Help
---

### Post by the lemming on 2007-06-03
No, I don't mean ubuntu either now that I have successfully got it onto my PC.

I have been messing around with several different distros while dual booting on my laptop but somehow I can't help think that I am doing something wrong or inefficiently when swapping around.

At first I tried to re-format the partitions but that messed up the boot process and eventually I had to settle for inserting the Recovery disc, putting XP back on and then choosing my next distro after I had downloaded all the updates for XP.  Surely that is not a good use of my time.

May I ask how other people get around this?

Cheers

---

### Post by jd65pl on 2007-06-03
Format the partition then [repair grub]("http://www.sorgonet.com/linux/grubrestore/") afterward. That should eliminate any problems you were having.

---

### Post by kellemes on 2007-06-03
Just formating your partition shouldn't have any influance on the bootloader (MBR).

To be on the safe side you can skip the formating and start with configuring Grub.  Simply clean your partitions after you've done that from the OS you want to stick with.

Anyway, if things went wrong, any Tux-LiveCD will do to fix your system.

---

### Post by coffeecat on 2007-06-03
If you reformat the partition that part of grub (the bootloader) is on then that will indeed 'mess up the boot process'. A word of explanation. Stage 1 of grub resides in the mbr (master boot loader), which is the first few hundred bytes on the hard drive. It replaces the Windows mbr code. That calls stage 1.5 which is written to a normally-unused portion of the hard-drive that comes immediately after that first sector. Stage 1.5 calls stage 2 which you will find in the /boot/grub directory of your working Linux installation. Stage 2 used a file called menu.lst which is also in /boot/grub. Reformat the partition and you've lost /boot and you probably got a Grub error - possibly error 22.

I'm not 100% sure what it is you want to do but if it's going from dual-boot Windows/DistroA to dual-boot Windows/DistroB, then you certainly don't have to go through that rigmarole.

If that's what you want to do then simply insert distro B's disk and at some point in the installation process - at the partitioning stage - it will give you a choice something along the lines of using the current Linux partitions. The wording varies from distro to distro and if you choose this it will reformat the partition with distro A, install distro B and install either grub or lilo as the boot loader and set you up with a menu to dual-boot Distro B and Windows.

At least that's the theory. All the popular mainstream distros, as far as I am aware, will do this. Just avoid the enthusiast distros like Gentoo, Arch and Slackware which require technical knowledge of setting up the bootloader and you should be fine.

If the dual-boot scenario that I've describes is not what you want, just post back.

---

### Post by the lemming on 2007-06-03
> **coffeecat said:**
> 
If the dual-boot scenario that I've describes is not what you want, just post back.

That dual boot scenario is exactly what I'm after.  Seeing as I know bugger all about Grub, will it amend itself and delete the details of the distro about to be removed?

My next question is about the Home folder.  If and when I swap distros will I be able to continue using the same home folder, which is on a seperate disc drive, without losing information or will I have to re-format that as well?

Cheers

---

### Post by coffeecat on 2007-06-03
> **the lemming said:**
> Seeing as I know bugger all about Grub,

Don't worry. I've been there myself. :D It'll give you a headache, but it's worth adding the [Grub manual]("http://www.gnu.org/software/grub/manual/") to your bookmarks.

> **the lemming said:**
> will it amend itself and delete the details of the distro about to be removed?

Mmmm - not quite. Grub is an operating system agnostic boot-loading utility that was developed quite independently of Linux, but is now the most popular bootloader for Linux. What happens is that the new distro will overwrite your old distro's root partititon and completely reinstall Grub for you.

> **the lemming said:**
> My next question is about the Home folder. If and when I swap distros will I be able to continue using the same home folder, which is on a seperate disc drive, without losing information or will I have to re-format that as well?

Yes but you'll have to select 'custom partitioning' or whatever it will be called at the partitioning stage of the installer. Again the details will vary from distro to distro but you should be able to tell it to reformat the old / (root) partition and use it for the new distro's root, but to not format the /home partition and to set up a mount point for /home. 

The advantage of this is that all your old settings will be preserved but there is one big potential problem - that of permissions. Most distros (in my experience) set the UID for the first created user to 1000, but some - including Fedora, PCLinuxOS and Mandriva - use 500. There are a number of ways of getting round this but it is something to be aware of.

---

