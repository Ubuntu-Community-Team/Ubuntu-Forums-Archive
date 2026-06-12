---
title: "Dual Boot"
date: 2007-11-06
forum: General Help
---

### Post by ploik on 2007-11-06
Hi, this is a quick, and may be an easy answer. All i want to know is how to be able to dual boot win XP home with ubuntu 7.10 gutsy. I previously did not have a dual ribbon, but now i do, and it only boots from one harddrive at a time. I do not wish to re-install ubuntu, as i already have many files on it. I previously heard that you can create a floppy with both boot sectors from each system, and be able to boot like that, only i do not have a floppy drive sadly. My question is if i can do the same thing as the floppy, but with a cd-r. Please tell me if it is possible, and where i may find the boot sectors in each windows and ubuntu so i may copy them to the cd. Also, if anyone has a different method of how to dual boot, please post it here. Thank you in advance for all your help,
Ploik

---

### Post by p_quarles on 2007-11-06
Booting from a removable disk sounds like a lot of trouble for something this simple (though, yes, you could do this from a CD if you really wanted to). 

Really, all you need to do is (re)install GRUB on one of the hard disks, and then set the BIOS to boot from that disk. Unless things go horribly wrong, this will automatically detect all bootable operating systems available, and set up a boot menu that pops up following the BIOS screen. If things *do* go horribly wrong, btw, this is something that's pretty easy to fix manually. 

You can reinstall GRUB using the normal Ubuntu installation disk. A slightly more foolproof tool can be found [here]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html"). That won't be necessary in most cases, though. 

In any case, do make sure that you have backups of all important files. This goes whether you actually modify your computer or not: hard drive failures do not come at expected or convenient times.

---

### Post by ploik on 2007-11-06
nice, thanks for the answer, just one quick question, when you say to r-install grub on one of the hard disks, what do you actually mean? sorry, but im kinda new to linux. I previously used to WHOLE disk to install linux, so do i first re-size, and then is there an option to install grub only, or is grub the WHOLE system? thank you again... and sorry for bein a noob, lol

---

### Post by 00l0 on 2007-11-06
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

;D

---

### Post by p_quarles on 2007-11-06
I started out as a noob myself. No need to apologize. :)

Anyway, GRUB is the bootloader that is installed by Ubuntu by default. When you installed it using the entire disk, it became invisible because it didn't need to give you any boot options (you only had one OS). If you install it on a system that has multiple operating systems, it will automatically configure itself to give you a boot menu at startup time. 

And, no, GRUB is not the entire system: it's the program that the BIOS finds on the bootable disk, which then gives the computer instructions about how to proceed. There's a more detailed explanation [here]("https://help.ubuntu.com/community/GrubHowto").

Like I said, you can use the regular Ubuntu live disk to reinstall it ([instructions]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")). You can also use the Super GRUB Disk, in the link in my first post.

---

### Post by ploik on 2007-11-06
ok, thanks a bunch, you helped alot! just one last EASY and QUICK question... i installed my XP and Ubuntu on different HDs, both using the whole thing, so does it matter which one i install the GRUB on, or does it have to be the master? ^^
Ploik

---

### Post by p_quarles on 2007-11-06
To make things easiest, I would install GRUB onto whatever hard disk you're currently booting from. I'm not 100% sure of this, but I believe that's what your system considers the master disk.

---

