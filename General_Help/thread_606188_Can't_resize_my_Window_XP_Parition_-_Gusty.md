---
title: "Can't resize my Window XP Parition - Gusty"
date: 2007-11-07
forum: General Help
---

### Post by thenetduck on 2007-11-07
Hello my most excellent Ubuntu buddies

I am trying to install Ubuntu 7.10 32bit on my laptop which as Windows XP on it. The live boot up is fine and i installed my wireless drivers with ease (muy bueno!) but when it comes to install the OS it have run into a couple of problems. 

This is what I tried: 

 : Regular install, got to resize partition and install so left it on default and when it tries to partition the drive it gives me some error and says it doesn't work. 
 
 : GParted resize, I resized the NTFS partition with gparted but runs into problems. If you would like I can post whatever it saved if that will help you figure this one out. 


Anyway I though you were suppose to be able to install Ubuntu on machines that have windows xp installed? Am I mistaken? 

Thanks for the wonderful support!

The Net Duck

---

### Post by geirha on 2007-11-07
My guess is that the ntfs partition has too much fragmentation. Try defragmenting it in windows.

---

### Post by Maestro23 on 2007-11-07
What I always tell people who want to dual-boot. Get all the housekeeping done in Windows 1st.

1. Defrag the Windows partition first while you are in Windows.

2. After the defrag, create the free space with a program in Windows (Partitoin magic, etc...)

3. Boot up the Ubuntu Live CD and install Ubuntu to the free space.

*Just one way of preparing your system for a dual-boot.:)

---

