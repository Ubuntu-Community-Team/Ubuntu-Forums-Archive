---
title: "HDD Sizing Problem"
date: 2007-08-18
forum: General Help
---

### Post by sgtbob on 2007-08-18
I have Ununtu and Win XP on a dual boot system.  Due to some crash problems recently, I had to reformat both HDD 's I have installed on this Dell 8250.  I have Win XP on one 120 GB HDD and Ubuntu on the 2nd 40 GB HDD - if things keep on with Ubuntu, I may switch these..  

I didn't notice until after everything was up and running that my 120 GB HDD now shows only as a 31.5 GB HDD.  It hasn't affected performance ---yet, but is there anyway to restore this drive to its full potential of 120 GB?

Bob ](*,)

---

### Post by scrooge_74 on 2007-08-18
Repartiton the drive again, use a Live Cd and go to Gparted. You should not have any problem doing it, you probably left part of the drive un used, you can take the oportunity and  make a separate /home partition if you don't have one at the moment (that will help in case of an emergency restore) and then you can even point XP to read from it.

---

### Post by sgtbob on 2007-08-18
Please show the exact steps.  I put the Ubuntu disc in the drive after I booted into it, went to the 'terminal' and typed 'Gparted' - it says invalid command.  Can you elaborate please.
:redface:

---

### Post by confused57 on 2007-08-18
> **sgtbob said:**
> Please show the exact steps.  I put the Ubuntu disc in the drive after I booted into it, went to the 'terminal' and typed 'Gparted' - it says invalid command.  Can you elaborate please.
:redface:

Post the output of:
```
sudo fdisk -l
```
-l is a small "L"

Also, I believe you can access Gnome Partition Editor from the Ubuntu live cd...try System---Administration---Gnome Partition Editor...this should show your current partitions.

You might want to enter your bios setup and make sure LBA is enabled for your hard drives.

Added:  You can see how Windows sees your partitions by right-clicking on "My Computer", then select "Manage", select "Disk Management".

---

### Post by scrooge_74 on 2007-08-18
You have to reboot and start the PC with the live CD

---

