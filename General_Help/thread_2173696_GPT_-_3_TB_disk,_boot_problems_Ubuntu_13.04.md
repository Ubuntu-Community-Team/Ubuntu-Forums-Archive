---
title: "GPT - 3 TB disk, boot problems Ubuntu 13.04"
date: 2013-09-10
forum: General Help
---

### Post by jerome1232 on 2013-09-10
So I'm having some problems getting Ubuntu to boot on this computer, I had it working previously with Windows 7 and Ubuntu 13.04 both on a mbr disk, I have since reinstalled Windows to the mbr disk and Ubuntu to the gpt disk. Windows 7 boots fine, but since installing Ubuntu grub fails to boot, dumping me at a grub rescue prompt.

I ran boot-repair, and there was no improvement, here is it's dump.

[http://paste.ubuntu.com/6090575/](http://paste.ubuntu.com/6090575/)

---

### Post by oldfred on 2013-09-11
There was a bug supposedly fixed that grub would not work with / (root) partitions over 500GB. I normally suggest 10 to 25GB / partitions anyway and use rest of drive as /home or as data partition(s). 
Smaller / is more efficient as all the boot files are closer and drive does not have to jump all over 3TB just to boot or load drivers or applications. Data then can be all over drive as it is not loaded as often.

The issue seems also be related to some BIOS and BIOS settings. Do you have BIOS set to AHCI. If not you also may need to update driver for AHCI in Windows before changing. 

Also if system is UEFI or you move move drive to an UEFI system, I would create an efi partition at beginning of drive even if booting with BIOS now. It is difficult to add the efi at beginning of drive later when you have lots of data on drive. And since Windows is BIOS you need Ubuntu installed in BIOS mode for now.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu - Post #6 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by jerome1232 on 2013-09-11
I believe that bug bit me, I did just try with a much smaller /boot partition and she is up and running.

I will rethink the partitioning scheme, I will be eventually adding win8 (if it works with bios systems) onto the mbr disk, so part of the 3tb gpt disk will go to ntfs for data sharing.

Thanks, the tip about the bug got her going!

---

