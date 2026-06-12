---
title: "how find partition for ubuntu in dual boot with windows 7 &amp; uninstallation guidance"
date: 2014-10-14
forum: General Help
---

### Post by ramadavid on 2014-10-14
Dear Friends,
         I have dual boot laptop with wndows 7  and Ubuntu 14.04 LTS. My system is 64 bit 
and Unfortunatly I installed 32 bit ubuntu instead of 64 bit ubuntu. I really not know where is 
the ubutu partition.
   So my question is, how to find ubuntu partition and uninstalled it. 

   I will be a very thankful to your help.
I am not really a expert in computer. I am average user of laptop.

---

### Post by oldfred on 2014-10-14
Important to only use Something Else to reinstall. May not be an issue with BIOS/MBR but many users with Windows 8 have used one of the auto reinstall options and it says it is overwriting Ubuntu. But it overwrites entire drive.

       Reinstall says overwrite Ubuntu but it also erases existing Windows. 
Sept 2014 Fix being released for one drive installs, but mulitple drive installs must use Something Else. And fix is not in current versions.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Post this from Ubuntu or live installer:
sudo parted -l

The Linux formatted partition usually ext4 will the main install. If you have more than one ext4 then did you create a separate /home data partition? All NTFS partitions will be Windows, unless you also created a shared NTFS data partition for both systems to share data.

---

### Post by Bashing-om on 2014-10-14
ramadavid; Hello;

To see the partitioning on the hard disk(s), execute terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
where 'fdisk' is for the legacy MBR partitioning scheme, 'parted' will see both the MBR and EFI schemes.
ext4 is a ubuntu partition
ntfs is a Windows partition.

As to the advisability of installing the 64 bit version of ubuntu .. 
Do you have 4 Gigs or more ram installed ?
If not you will get better overall performance with the 32 bit version - due to the addressing overhead of 64 bits verses 32 bits.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

