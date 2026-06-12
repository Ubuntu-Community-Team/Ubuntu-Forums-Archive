---
title: "xp/ubuntu dual boot setup - cannot see NTFS partitions"
date: 2008-04-22
forum: General Help
---

### Post by lattmau on 2008-04-22
Hi all, I gave up on Ubuntu a couple months ago but I was re-inspired recently and decided to try setting up my system to dual boot XP and Ubuntu, but I ran into a problem.. 

So I have 2 physical drives.  
-With Drive 1, I made 2 partitions
-Installed Windows XP (NTFS format)on first partition of Drive 1
-Then inserted Ubuntu 7.10 and manually partitioned free space of Drive 1.  I made a swap partition and made the rest for Ubuntu, mounting it to /
-Grub was installed to MBR of (hd0)
-Drive 2 is backup drive formatted to NTFS

Install was good I think.  When computer rebooted, it showed Grub and I was able to boot into XP or Ubuntu.  

The problem is when I boot into Ubuntu and I go to My Computer, I cannot see either the Windows partition or Drive2.  Then I try mounting them manually in terminal.  Both attempts, I get 

"Mount is denied because NTFS is marked to be in use".

Ideas?  Solutions?  Much appreciated.

---

### Post by logos34 on 2008-04-22
sudo apt-get install ntfs-config

[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)

---

### Post by lattmau on 2008-04-22
I thought the ntfs driver was default for 7.10 and should automatically mount? ...if thats the case, is ntfs-config even necessary?

---

### Post by logos34 on 2008-04-22
> **lattmau said:**
> I thought the ntfs driver was default for 7.10 and should automatically mount? ...if thats the case, is ntfs-config even necessary?

yes, they *should* automount, and ntfs-3g is now installed by default, but not the ntfs-config gui frontend, which is what you need to configure the drive mountpoints, etc.  Unless you want to edit fstab by hand, in which case post your fstab and fdisk output

sudo fdisk -l

cat /etc/fstab

---

