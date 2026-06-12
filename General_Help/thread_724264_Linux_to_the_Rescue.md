---
title: "Linux to the Rescue ?"
date: 2008-03-14
forum: General Help
---

### Post by PlipO on 2008-03-14
I have a hard drive that is failing, when XP loads; it ask me if I want to format the drive when I try access any partitions on that drive.
I have use Winternals, ReactOS, Ubuntu and Slax, I am not able access the partitions using any of these Operating Systems.
Are the any Linux distributions that will be able to mount the faulty partitions and allow me to copy my files from the partitions? 
Are there any NTFS boot disks that will allow me have a graphical interface and copy files ?

---

### Post by SPr on 2008-03-14
[SystemRescueCD](/www.sysresccd.org/) has a program that can recover files from unmounted hard drives so this may be your best bet if the HDD is unmountable. The program's name is photorec but it finds more than just pictures. You'll need to save the recovered files on a different HDD, of course.

When the CD has booted type "photorec" without the quotes, follow the prompts and search the entire HDD.

---

