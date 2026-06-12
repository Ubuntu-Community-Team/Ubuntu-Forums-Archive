---
title: "NTFS Hard Drive Problem - Missing 20gb"
date: 2006-11-26
forum: General Help
---

### Post by hxx4 on 2006-11-26
Ubuntu says I've used 163 out of 166GB of my mounted internal hard drive (not the same hd that ubuntu is installed on). Gnome Partitioner says I've used 183 out of 186GB on this hard drive. So I'm missing 20GB.
For this hard drive:
Size: 191GB
Used: 164GB
Unused: 7GB
I think this problem was caused when I tried converting the partition on the hard drive to FAT32. But it failed and is currently still NTFS. There is only one partition on this hard drive. I'm wondering if anyone knows of a way to get my 20gbs back. I tried Partition Magic with no luck. I want to avoid reformatting the drive of course. Is that my only option?

---

### Post by taurus on 2006-11-26
What does this command say, from a terminal?

```
sudo fdisk -l
```

---

### Post by hxx4 on 2006-11-26
Disk /dev/hdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       24321   195358401    7  HPFS/NTFS

This hard drive is advertised as a ATA133 200GB Seagate.
I also checked Filesystems under System Monitor and it only recognizes 167GB.

---

### Post by taurus on 2006-11-26
What does XP say about the capacity of your harddrive?  Wait.  How old is your machine?  Some older machines can't see more than ~160GB!!!  If that's the case, you need to upgrade your BIOS...

---

### Post by hxx4 on 2006-11-26
I ditched XP for Ubuntu recently. I built my machine a year ago and I do not believe that there are any hardware problems causing Ubuntu not to recognize the 20gb. XP recognized the space fine but when I switched to Ubuntu I decided to try converting to FAT32. But once I configured ntfs-3g I no longer needed fat32. ntfs-3g is not the problem because I have tried using the kernel read-only ntfs driver to mount the hard drive and I am still missing 20gb

---

### Post by taurus on 2006-11-26
If you don't have Windows on that partition anymore, then why still use ntfs!!!  Format it to ext3 and see if you get the full capacity.

---

### Post by hxx4 on 2006-11-26
Well in the future I was thinking about installing Vista and I wouldn't be able to read/write ext3 easily with that. But unless there are any other immediate fixes, I think I will just backup all my data and erase that hard drive and remake the partition. Thanks a lot for your help taurus.

---

### Post by taurus on 2006-11-26
Well, good luck.

---

