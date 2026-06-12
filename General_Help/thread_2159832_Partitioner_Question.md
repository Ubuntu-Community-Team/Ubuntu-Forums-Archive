---
title: "Partitioner Question"
date: 2013-07-04
forum: General Help
---

### Post by Changturkey on 2013-07-04
Hi, just wondering, when I am installing Ubuntu alongside Windows 8, the installer asks me to provide a certain amount of storage space to each OS. My question is, is the left block Windows 8, or is it Ubuntu? The installer does not show this, so I don't want to end up with a very small Ubuntu partition (which I intend to use as my main os). Thanks.

---

### Post by Mark Phelps on 2013-07-04
IF you use the installer to shrink Win8, you will very likely end up corrupting Win8 and rendering it unbootable.  Instead, you should be going into Disk Management in Win8 and using the partitioning tool to shrink the Win8 OS partition.

Also, you are going to have problems with secure-boot and EFI BIOS -- which are new to Win8 preinstalled PCs.

---

### Post by Changturkey on 2013-07-04
> **Mark Phelps said:**
> IF you use the installer to shrink Win8, you will very likely end up corrupting Win8 and rendering it unbootable.  Instead, you should be going into Disk Management in Win8 and using the partitioning tool to shrink the Win8 OS partition.

Also, you are going to have problems with secure-boot and EFI BIOS -- which are new to Win8 preinstalled PCs.

I've already disable Fastboot and Secure boot in my BIOS, so I shouldn't have a problem right?

---

### Post by arpanaut on 2013-07-04
Good info for uefi installations:
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by fantab on 2013-07-05
> **Changturkey said:**
> I've already disable Fastboot and Secure boot in my BIOS, so I shouldn't have a problem right?

UEFI booting is a relatively new feature. And dual-booting with Windows8 is known to create problems if not careful. This UEFI depends on OEM to OEM. What worked with one OEM may not work with other OEM machine. For instance, on some OEM machines Windows8 will not boot with 'Secure Boot' turned off, but on others it does. So UEFI is still an unchartered territory to many of us here and in general. So expect problems.

Having said that its is quite easy to Dual-Boot Windows 8 and Ubuntu.

But before you proceed do thorough **BACK UP of your Windows**. Read the link that follows to learn how to BACK UP: [http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
Here is an [excellent Thread on UEFI Installing Tips]("http://ubuntuforums.org/showthread.php?t=2147295") by oldfred. Do go through it before you commit to UEFI dual-boot.

Also, it is best and recommended that you use only Windows tools to manage Windows Partitions, like when you have to 'Shrink' Windows Partition to make space for Ubuntu.

Good Luck...

---

