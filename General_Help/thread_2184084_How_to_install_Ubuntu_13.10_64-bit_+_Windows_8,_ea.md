---
title: "How to install Ubuntu 13.10 64-bit + Windows 8, each on entirely separate SSD's"
date: 2013-10-27
forum: General Help
---

### Post by apower2 on 2013-10-27
Hello, 

I'm a college student whose trying to install Ubuntu 13.10 on an entirely separate SSD than the Windows 8.1 SSD that's already installed and working. For absolute clarification, I have two SSD's: one (1) 240GB SSD with windows 8.1 installed and one (1) 120GB SSD that's a completely empty volume. Both are recognized by my UEFI Bios. Since I'm installing Ubuntu on an entirely separate disk, does this change my installation procedure? I'm following this article as a reference: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Thank you for the support, I really appreciate it. I'm a computer engineer but have literally no experience with Ubuntu or Linux. 
Alex

---

### Post by oldfred on 2013-10-27
Only a bit different. 
You may end up with grub2's efi boot loader in the Window's drive efi partition, but I suggest an efi partition on the Ubuntu drive so it could boot on its own. 
You can insure that is the case if you disconnect the Windows SSD.
You still have to make sure you partition Ubuntu SSD with gpt, and boot installer in UEFI mode.

I only have BIOS, but configured my SSD for future use with UEFI with both an efi partition and the bios_grub for my current BIOS booting. 

You will still need to turn off fast boot in Windows as it causes all sorts of issues with dual booting. You may want to shrink Windows and make a separate NTFS data partition or add one on the Ubuntu drive. My SSD is 62GB, but I added two / (root) partitions since I have all data on my rotating hard drive.

You also will need to run Boot-Repair. Some links to other users with dual drive installs in the link in my signature.

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
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

