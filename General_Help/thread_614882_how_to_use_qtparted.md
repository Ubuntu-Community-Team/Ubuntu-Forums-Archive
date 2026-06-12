---
title: "how to use qtparted"
date: 2007-11-16
forum: General Help
---

### Post by dafunkmon on 2007-11-16
i want to completely format my hard drive, get rid of kubuntu and install windows(and no the partitioning tool for windows did not work so im using this), help i really need to remove kubuntu and install windows xp pro! how do i use qt parted?

---

### Post by minus198 on 2007-11-16
Put in the Windows XP CD. Restart the computer. Install Windblows. You are done.

You don't have to format the drive before installing windows.

---

### Post by dafunkmon on 2007-11-16
so i put windows cd in, restart and boot ubuntu, install windblows on ubuntu ?

---

### Post by minus198 on 2007-11-16
Well... Do you want to completely remove Kubuntu?

Then you should pop in the windows CD and reboot, and the installation CD will hopefully start automatically.

If you want to remove kubuntu att the same time, just install windblows over kubuntu. It will automatically remove it when the windows installer formats the drive.

---

### Post by dafunkmon on 2007-11-16
but thats the thing, i put the cd in and then when it says ready to install windows it will say;
windows has detected an error
then i get a blue screen telling talking about my hard drive

how do i use qtparted, so i can wipe my hard drive, install windows and go on with my day becausei have been trying to format my harddrive for weeks now...;)

---

### Post by minus198 on 2007-11-16
You cant format the drive you have Kubuntu installed on, if you are using Kubuntu.

Post the exact error of the bluescreen.

---

### Post by dafunkmon on 2007-11-16
a problem has been detected and windows has been shut down to prevent damage to your computer.

if this is the first time youve seen this stop error screen, restart your computer. if this screen appears again, follow these steps:

check for viruses on your computer. remove any newly installed hard drives or hard drive controllers. check your hard drvie to make sure it is properly configured and terminated. run chkdsk /F to check for hard drive corruption, and then restart your computer.

technical information:

***stop: 0x00000007B (ocf78d2524, 0xc00000034, 0x00000000,0x00000000)

this is the screen i get word for word

---

### Post by froy02 on 2007-11-17
I use Maxtor, Seagate and Western Digital hard drives. Each one of them comes with a utility for preparing your hard drive for windows installation.  If not you can download their utilities to repair the mbr. 
Linux always writes grub, lilo or something in the mbr so windows thinks the hard drive may be bad.  Restore or fix the mbr (master boot record) using the utility for your hard drive. 

Froy

---

