---
title: "Dual Boot with Windows 8[Solved]"
date: 2013-04-07
forum: General Help
---

### Post by Spiritof76 on 2013-04-07
My Old Ubuntu system died, and I bought a brand new Dell complete with Windows 8. This system has a 2 Terrabyte and a 1 terrabyte hard drive. The 1 terrabyte hard drive is empty.  The System has this UEFI boot security thing. 

I am not sure whether I should wait for the 20 days to install the newest version 13.04 or whether to install 12.10.  What concerns me is the support time for 13.04 is only 9 months.  I would like to avoid a massive update until the next LTS version comes out.  I have read that with 13.04 there will be these roling updates though. Does this mean that 13.04  will automatically update to 13.10.  

My other question relates to partitioning and grub.  Can I safely install Ubuntu on my primary disk and use the 1 terabyte as a /usr partition? or would I be better off just installing Ubuntu on my secondary drive.  I really never see my self using any where near 1 terrabyte on either Windows or Ubuntu systems.. But my Ubuntu system will be my most used OS.

Thanks  ...

---

### Post by oldfred on 2013-04-07
If never installing Windows on other drive and one drive is already UEFI, make sure you partition with gpt and leave an efi partition at beginning of drive.
You cannot easily dual boot an UEFI install and a BIOS install. Ubuntu will also boot from gpt drives in BIOS mode, where Windows has to have gpt partitioning to boot in UEFI mode.

I would install both 12.04, and 13.04. I have 12.04 & 12.10 on my SSD and testing 13.04 on my hard drive. My SSD is gpt but I only have BIOS. But since I was hoping to build new system I also left space for an efi partition on my SSD.
I normally install Ubuntu in 25GB / (root) partition including /home, but with all data in data partitions. My new large drive of 640GB three years ago was allocated two 100GB data partitions, and a couple of 25GB partitions for / installs, and the rest unallocated. I now just about have filled drive, most are 25GB partitions so I can test or experiment with an install and I have not been housecleaning like I should only because I had the room.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

      
 Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)


 GPT Advantages (older but still valid)  srs5694 post #@:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

I really like an operating system on every drive and keeping Windows separate from Ubuntu if you have more than one drive. I use Ubuntu, but like this blog's logic.
       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by Spiritof76 on 2013-04-07
How do I Partition the drive with GPT ? Will the Ubuntu insta ll DVD detect or prompt me to do this?

---

### Post by oldfred on 2013-04-07
Ubuntu only auto creates gpt partitioning if you boot in UEFI mode or drive is empty (no Windows in with MBR) and drive is somewhere over 1TB.

I always create partitions in advance.

        I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

IF drive is for UEFI or might be sometime in future leave space at front of drive for a 200 to 300MB efi partition. If booting with BIOS, you then need a 1MB unformatted partition with the bios_grub flag set from gparted.

Arch also recommends gpt for SSDs.
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

---

