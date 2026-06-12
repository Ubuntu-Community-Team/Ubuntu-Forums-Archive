---
title: "Grub stage 1.5"
date: 2007-12-02
forum: General Help
---

### Post by froy02 on 2007-12-02
Can anyone explain what is grub stage 1.5?.  Where does it install, in the MBR of the first drive, the second drive, or on another partition?  What exactly does it do?   I am guessing that stage 1 is in the MBR of the first drive and stage 2 is the menu list in one of the drives.

So what the heck is stage 1.5?

Thanks

---

### Post by Cresho on 2007-12-02
grub is your bootloader.  Im actually looking into some mannuals on how to add windows xp because i use that for gaming with world in conflict and unreal tournament 3.  So far, information is available and I was able to find really good commands and easy to use tutorial.

When I first installed ubuntu, the default installation is on 3 partitions.  1st has /, the second has swap, the third has home.....i think...In any case, i have 4 partisions.

/boot
/
swap
/home

grub basically is your bootloader and has all information on bootable partitions.

In the default ubuntu install, /boot folder is in your / or main root partition.  What I don't understand is that why is this if it is highly recommended that you have a separate boot partition available.  Wierd huh!

Here is a recent link I am reading up on  [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by meierfra on 2007-12-02
The Stage 1.5 files  are located on sectors 2 to about 16  of the hardrive  (the first partition starts at sector 63, the MBR is the first sector)

The Stage1.5 files  contain information about the  type of file  system  used. So somebody with an ext3 file system, will have different stage 1.5 files than  someone with  reiser file system.

I don't know what the Stage 1.5 actually do.

The Stage 1.5 files are optional. If Grub is installed to the boot section  of a partition, they are not used. With  a little extra work Grub  can also be installed to the boot section of hard drive without using the Stage 1.5.  Just for fun I tried that once  and it did not cause me any problems.

---

### Post by meierfra on 2007-12-02
>  if it is highly recommended that you have a separate boot partition available.

As far as I know, a normal PC user does not need a separate boot partition.

---

### Post by froy02 on 2007-12-10
Thanks for the info.  That answered my question. 
I am now a Ubuntu convert. Vista is worse than XP.  I installed Ubuntu and used 3.7 gig of hard drive while my installation for vista is now 49 gigs with about the same functionality.

I could  probably install ubuntu in 1 of my old 25gb WD hard drive and it would just be as good.  I never use the operating system drive for my data. It is always a separate drive for data.  My OS crashes, data is safe.  With the nwe SATA and USB drives, unmount them and data is safe from prying eyes.

The reason I had to know how grub works was to dual boot Ubuntu and XP in one 150gb hard drive instead of my old setup of separate drives for each OS.  Now my 200gb HD is just for data.

Again thanks.

---

### Post by erfahren on 2007-12-10
this page at hermanzone's site explains it well (there's also a page on GRUB)
[http://users.bigpond.net.au/hermanzone/p6.htm](http://users.bigpond.net.au/hermanzone/p6.htm)

---

