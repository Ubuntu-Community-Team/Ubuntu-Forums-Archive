---
title: "HDD Partition has lost file system ID"
date: 2007-06-17
forum: General Help
---

### Post by Catfish81 on 2007-06-17
Hi,

I posted this in beginner but got no help. Maybe users here know something.

Recently I lost the file system ID on one of my partitions. Trying to mount the partition now outputs:
> catfish@delta:~$ sudo mount /dev/hdd5
Password:
mount: wrong fs type, bad option, bad superblock on /dev/hdd5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


gparted displays a partition of "unknown" but fdisk output a partition of type 83 (Linux):

> catfish@delta:~$ sudo fdisk -l /dev/hdd

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        1976    15872188+   7  HPFS/NTFS
/dev/hdd2            1977       24321   179486212+   5  Extended
/dev/hdd5            1977       24321   179486181   83  Linux


hdd1 contains an install of WinXP. Before the partition failure, I booted from that partition by disabling /dev/hda in the BIOS.

Is there anything that may have happened to prevent hdd5 from mounting since booting from hdd1? Usually hdd5 is an ext3 partition. Is there anyway I can restore it as this is my data partition and I've lost a lot of stuff!!!

---

### Post by confused57 on 2007-06-17
See this guide for mounting an ext3 partition:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by Catfish81 on 2007-06-17
When I try blkid it does not output the hdd5 partition:

> catfish@delta:~$ blkid
/dev/hda1: UUID="cfbaa130-5385-45fd-aecf-667c57a52435" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: UUID="27410967-30af-452a-a3bd-0a2a7b3439fb" TYPE="swap" 
catfish@delta:~$ sudo blkid
Password:
/dev/hda1: UUID="cfbaa130-5385-45fd-aecf-667c57a52435" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: UUID="27410967-30af-452a-a3bd-0a2a7b3439fb" TYPE="swap" 
/dev/hdd1: TYPE="ntfs" 
catfish@delta:~$ 


Is there a way to restore the hdd5 ext3 partition without formatting it? What causes the partition to suddenly disappear as though it is unformatted?
I am getting gparted live cd to check the partitions.

---

### Post by confused57 on 2007-06-17
> **Catfish81 said:**
> When I try blkid it does not output the hdd5 partition:



Is there a way to restore the hdd5 ext3 partition without formatting it? What causes the partition to suddenly disappear as though it is unformatted?
I am getting gparted live cd to check the partitions.
That's a great idea, just right click the partition & select "check"...hopefully, the check will correct the problems.
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)
scroll up a little on this page for instructions.

---

### Post by Catfish81 on 2007-06-17
The gparted live cd doesn't recognize the partition as ext3 and thinks it is unformatted. The only software that recognizes ext3 is fdisk. Because of this, gparted can't check the partition for me.

I would guess that if I told gparted to "format to" ext3 then it would do exactly that and format the partition and lose all my data. So I guess there's not much hope for all my data?


While I'm here, what would everyone reccommend to use for a stable data filesystem? I don't care much about access from Win32, though that might be nice. Am I better off using ext2 or ext3? What are the bad things about using vfat with Linux to outweigh it's good points? (Like that it can be accessed from Win as well) The thing I dislike most about vfat are the file size limitations.

---

