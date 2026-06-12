---
title: "Tri-boot ubuntu suse and XP"
date: 2007-09-02
forum: General Help
---

### Post by Eriksmits596 on 2007-09-02
Hi everybody!
I want to have Tri-boot with Ubuntu 7,04, windows XP and OpenSuse 10.2. Currently I have Dualboot with XP and ubuntu. Is there anyway to fix it without reinstall the whole system?

---

### Post by eionmac on 2007-09-02
I have been tri-booting WinXP, Ubunto and SuSE for some two years. Order of booting is very important in order to recover from any mistakes.
Download Super Grub live CD and burn   ISO ("Burn ISO , do not COPY!
Download QTparted live CD and burn  ISO

UseQTParted to  partition with windows closed if you want. 
SuperGrub sorts out problems if MBR or GRUB  faults later.

1. Boot Win Xp as normal system on C: drive. or h use existing win Xp if loaded.
2. Defrag this Win Xp drive directory at least twice, this is important!
3. Load a commercial (or free magazine) partition program inside windows. I use Partition Manager 8.5 free on magazine discs.
4. Load partition manager and  resize Win XP C  to a smaller size say  40% of hard drive.
(This is why defrag is important so not to lose data)
5. Choice: make at least one more active partition  Fat 32  formatted and one extended partition.
size depends on hard disc size but Ubunto and SuSE need about 10GB and you need another10GB for /home so say 32 GB for extended partition which will contain 4 subpartitions:
-
 -  Swap linux partition
 - SuSE
 - Ubunto
  /home
6 Format a linux swap partition inside your extended partition of about twice your RAM  size.
 7 format the linux partitions in Ext3
leave program
shut down Windows
reboot windows  - to make sure it starts!

 
8 Load SuSE ,  save boot loader to floppy disc ( if you have one, this is a safety measure)

SET Windows as default  system and then if any problems it  loads back into Windows
This is important, if you have not used  GRUB before or do not know how to alter GRUB
Set time to choose as 20 seconds from default    of 8 seconds, allows one to think and choose.

9 Load SuSE

10 Reboot, if problems reload from SuSE disc and resave boot  loader to SuSE partition.
If real problems use SuperGrub Live Linux- it willl    finds and allow both SuSE to be loaded or WIndows.

11 You should have a GRUB screen allowing choice of Windows or SuSE with Windows as default 

12 check both Windows and SuSE work

13 Load Ubunto
Ensure it does not wipe hard disc! or overwrite windows 

It will set Ubunto as first operating default system.

This can be changed by altering Ubunto menu.1st grub   to   set copy o f the Windows loaded at top of menu or by use of SuperGrub.

NOTE: This will need to be done every time Ubunto alters the Kernel! 
Also when SuSe alters the Kernel during upgrades, I use supergrub to adjust menu of loading in Grub..

I keep two copies of Grub oin system , one on windows (Ubunto GRUB) and One onsuSE inSuSE boot file.
This ensures I can boot machine from:
- floppy 
_ from Hard disc 1 partition
from hard dissc 2 partition
from supereGrub
_from windows  discs

Good luck
eion Macdonald

---

### Post by eionmac on 2007-09-02
Also as insurance keep a Live Knoppix disc available. Use itto sort out any problems in Ubuntu or SuSE or recover windows documents.
Save mutual documents to the FAT32 partition, they can be read and used by all systems.

My work  horse  is Knopix as my " sorter out  Live disc".
regards
eion macDonald

---

