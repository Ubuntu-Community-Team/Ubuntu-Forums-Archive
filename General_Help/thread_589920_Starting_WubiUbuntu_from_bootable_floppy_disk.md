---
title: "Starting Wubi/Ubuntu from bootable floppy disk"
date: 2007-10-24
forum: General Help
---

### Post by doomer80 on 2007-10-24
Hi to all, I have just installed Wubi 7.04.04 on my Windows XP Professional PC.
I have downloaded Ubuntu 7.4 Alternate in ISO format and copied it into the same folder of Wubi setup. Than I installed Wubi (8 Gb installation, Italian language) in my C: NTFS partition under C:\WUBI. The installation was succesfully. Note that my Windows XP account has standard privileges (it's not an administrative account).
Due to my account limitations (I think so) the installation program didn't changed my boot.ini file settings. This in not a real problem because my intention is to start Ubuntu on Wubi using a custom Windows XP boot floppy with the correct boot.ini settings.
I have created this disk copying on it NTLDR and NTDETECT.COM, and I created a new boot.ini on the floppy.
I have added to it the entry for starting Ubuntu using Wubi loader (C:\WBLDR="Ubuntu").
Next I booted the PC from that floppy choosing "Ubuntu" in the o.s list. Suddenly I have received an "Error loading hal.dll" (or similar) message and Ubuntu didn't started at all. 

Have I inserted a wrong entry in my boot.ini file? In this case which is the correct string to enter?

Thanks!

Bye.

Sergio

---

### Post by ago on 2007-10-24
c:\wubildr.mbr

---

### Post by doomer80 on 2007-10-25
I have tried the "c:\wubildr.mbr" entry but it doesn't work. 
After choosing "Ubuntu" in the boot menu I see a black screen with an error message sayng "Unable to find hal.dll - file corrupted or missing - Unable to start Windows" (this isn't the exact message but the meaning is this). It seems that wubildr.mbr doesn't work and the system is trying to boot Windows! 
What I should try? Wubi is my only solution because I can't modify my PC's partitions (it's my work PC!). 
I think that Linux/Ubuntu is a wonderful operating system and using it for my work needs (I manage Web applications and Unix-based servers via ssh) it's a very good way to learn and master Linux!

I'm italian, sorry for my english if it isn't perfect!

Thanks.

Sergio

---

### Post by ago on 2007-10-25
try 7.10

---

### Post by tinybit on 2007-10-27
hal.dll ........ thingy

That might mean a "BOOT.INI" entry problem.

You need to copy wubildr.mbr onto the floppy, thou.

Remember to not change the C: drive letter in the BOOT.INI line. That is to say, the following is wrong:

A:\wubildr.mbr=......

it should be:

C:\wubildr.mbr=......

here C:\wubildr.mbr actually refer to A:\wubildr.mbr, but you have to write it in A:\BOOT.INI with a line of C:\wubildr.mbr=...  instead of A:\wubildr.mbr=....

Sound quite weird? But MS likes the way, and we are not able to change it.

---

