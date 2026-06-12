---
title: "Uninstalled Grub2 and need repository to reinstall through terminal"
date: 2019-01-07
forum: General Help
---

### Post by vineyridge on 2019-01-07
I am using Boot-Repair-Disk which uses lubuntu 14.04.  When I ask it to reinstall Grub it gives me this message:> Please enable a repository containing the [grub2] packages in the software sources of Ubuntu 18.04.1 LTS (sdb6). Then try again.

I've been searching and trying things I found on AskUbuntu for about two days, and nothing has worked.  I'm afraid to post there because I'm not Linux literate, and the folks there can be very snarky and unhelpful.

One post said that I had to enter this source list somehow, but I don't know where to begin.
```
0-09 07:59:53 startup packages configure
2018-10-10 04:34:09 startup archives unpack
2018-10-10 04:34:20 upgrade initramfs-tools:all 0.122ubuntu8.12 0.122ubuntu8.13
2018-10-10 04:34:20 status half-configured initramfs-tools:all 0.122ubuntu8.12
2018-10-10 04:34:20 status unpacked initramfs-tools:all 0.122ubuntu8.12
2018-10-10 04:34:20 status half-installed initramfs-tools:all 0.122ubuntu8.12
2018-10-10 04:34:20 status triggers-pending man-db:amd64 2.7.5-1
2018-10-10 04:34:20 status half-installed initramfs-tools:all 0.122ubuntu8.12
2018-10-10 04:34:20 status unpacked initramfs-tools:all 0.122ubuntu8.13
2018-10-10 04:34:20 status unpacked initramfs-tools:all 0.122ubuntu8.13
2018-10-10 04:34:21 upgrade initramfs-tools-core:all 0.122ubuntu8.12 0.122ubuntu8.13
2018-10-10 04:34:21 status half-configured initramfs-tools-core:all 0.122ubuntu8.12
2018-10-10 04:34:21 status unpacked initramfs-tools-core:all 0.122ubuntu8.12
2018-10-10 04:34:21 status half-installed initramfs-tools-core:all 0.122ubuntu8.12
2018-10-10 04:34:21 status triggers-pending doc-base:all 0.10.7
2018-10-10 04:34:22 status half-installed initramfs-tools-core:all 0.122ubuntu8.12
2018-10-10 04:34:22 status unpacked initramfs-tools-core:all 0.122ubuntu8.13
2018-10-10 04:34:22 status unpacked initramfs-tools-core:all 0.122ubuntu8.13
2018-10-10 04:34:22 upgrade initramfs-tools-bin:amd64 0.122ubuntu8.12 0.122ubuntu8.13
2018-10-10 04:34:22 status half-configured initramfs-tools-bin:amd64 0.122ubuntu8.12
2018-10-10 04:34:22 status unpacked initramfs-tools-bin:amd64 0.122ubuntu8.12
2018-10-10 04:34:22 status half-installed initramfs-tools-bin:amd64 0.122ubuntu8.12
2018-10-10 04:34:23 status half-installed initramfs-tools-bin:amd64 0.122ubuntu8.12
2018-10-10 04:34:23 status unpacked initramfs-tools-bin:amd64 0.122ubuntu8.13
2018-10-10 04:34:23 status unpacked initramfs-tools-bin:amd64 0.122ubuntu8.13
2018-10-10 04:34:23 upgrade flashplugin-installer:amd64 31.0.0.108ubuntu0.16.04.1 31.0.0.122ubuntu0.16.04.1
2018-10-10 04:34:23 status half-configured flashplugin-installer:amd64 31.0.0.108ubuntu0.16.04.1
2018-10-10 04:34:24 status unpacked flashplugin-installer:amd64 31.0.0.108ubuntu0.16.04.1
2018-10-10 04:34:24 status half-installed flashplugin-installer:amd64 31.0.0.108ubuntu0.16.04.1
2018-10-10 04:34:24 status triggers-pending update-notifier-common:all 3.168.9
2018-10-10 04:34:24 status half-installed flashplugin-installer:amd64 31.0.0.108ubuntu0.16.04.1
2018-10-10 04:34:24 status half-installed flashplugin-installer:amd64 31.0.0.108ubuntu0.16.04.1
2018-10-10 04:34:24 status unpacked flashplugin-installer:amd64 31.0.0.122ubuntu0.16.04.1
2018-10-10 04:34:24 status unpacked flashplugin-installer:amd64 31.0.0.122ubuntu0.16.04.1
2018-10-10 04:34:24 trigproc man-db:amd64 2.7.5-1 <none>
2018-10-10 04:34:24 status half-configured man-db:amd64 2.7.5-1
2018-10-10 04:34:26 status installed man-db:amd64 2.7.5deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) main
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) main

```

I uninstalled Grub2 by mistake while using the Boot-Repair-Command, one of which failed, and I stupidly aborted the session.

Can someone help me?  The disk in question is failing, and I need to be able to save certain files on it before I replace the disk and install Ubuntu on the new disk.

---

### Post by Bashing-om on 2019-01-07
vineyridge; Hello -

As your stated goal is to copy off certain files .. well - that can easily be done from a liveDVD/USB .

Post back - Between code tags - the output of terminal command:
```

sudo fdisk -lu

```
and we see what we can do about mounting the file system where your files are located. You will need an external medium to copy the files onto.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]ain't nothing but a thing
[/INDENT]

---

### Post by vineyridge on 2019-01-07
First of all, I cannot boot from a ubuntu disk in any flavor.  I've tried a Kubuntu disk, a Ubuntu 16.04 LTS disk.  This has been constant since the Grub problem started.  I can boot into Boot-Repair-Disk.  I've checked my boot order, and it is set to boot from the CD Drive 1st.  I downloaded and burned a new Ubuntu 18.04 LTS disk just now, put it in the CD drive, and attempted to boot from it.  Instead, I booted into Windows 7, which is my "dual boot" other OS.  

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1156cf4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2   *      206848   414310399   207051776    7  HPFS/NTFS/exFAT
/dev/sda3       414326784   934582271   260127744   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf934346b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   584591359   292294656   83  Linux
/dev/sdb3       584593406   976771071   196088833    5  Extended
/dev/sdb5       968386560   976771071     4192256   82  Linux swap / Solaris
/dev/sdb6   *   584593408   968386559   191896576   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x844aee8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   976771119   488384536    7  HPFS/NTFS/exFAT




```

---

### Post by vineyridge on 2019-01-07
I save all my data to an external HD when I think about it.  But there are two programs in the old Ubuntu that have their own databases.  One is Password Gorilla;  the other is Gjots.  Those two database files are really the only ones that I will need to rescue so they can be installed in the new Ubuntu on the new HDD.

I have no idea why I am booting to the drive that I am booting to.  It is not the drive that I would have chosen for my boot drive.  It is on the same disk as Windows 7, and I'd rather have it on the new Ubuntu disk.

I'd also like to boot with a Ubuntu Live Disk, because I cannot see how I can install it otherwise.

---

### Post by oldfred on 2019-01-07
Your fdisk output says you have gpt info on sda.
But sda is a BIOS boot Windows that only boots from MBR drives.
If drive originally was gpt or you started conversion, it may have some gpt info. And that will cause issues of grub installing.

BIOS/UEFI controls which drive you boot from. And if newer system in last 5 years, it is UEFI hardware and you have both UEFI & BIOS boot modes, depending on how you install the operating systems.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the summary report ( not post full report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by vineyridge on 2019-01-08
At this time, my computer will not boot from a CD with any flavor of Ubuntu on it.  See above post.  It is 9 years old, so is certainly a bios computer.  I have checked the boot order, and it is set to boot first from the CD drive, but when I use a Ubuntu disk, even one that I just created yesterday, it boots immediately to Windows.

I THINK that the GPT data on sda is leftover from Grub2.  I believe that Grub2 was installed on that disk.  There is a command in Boot_Repair-Disk that defaults to putting Grub on all disks, and I didn't notice that the last time I had to use Boot-Repair-Disk.  

I do have an empty flash drive and could live boot from that, but I have no idea how to create a bootable flash drive with Ubuntu on it that will boot if a CD won't.

---

### Post by oldfred on 2019-01-08
The relationship between gpt & grub2 is only that if you have gpt partitioning, you must have a bios_grub partition.
Normal MBR partitioning uses grub2 and it puts its core.img in the sectors just after the MBR, so no bios_grub required.
But installing grub would not change partitioning.

I converted a long time ago or when my system would boot from flash drive to flash drives. I had previously burned a lot of coasters (bad burns). I actually used one as a coaster for years.

Some find one installer works better than others, some find one brand of flash drive works better and some have to enable boot from USB as separate setting in BIOS to allow USB boot.
       Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[URL="https://help.ubuntu.com/community/Installation"]https://help.ubuntu.com/community/Installation
      [/URL]
 Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) or 
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 
    [URL="https://help.ubuntu.com/community/Installation"]
[/URL]

---

### Post by vineyridge on 2019-01-09
My major problem is that I cannot get to Ubuntu.  Anything I do will have to be done through Windows.  mkusb seems to be a built-in Ubuntu element;  without a Linux boot disk I cannot use it.  My computer WILL NOT boot to anything Linux/Ubuntu with a terminal except Boot-Repair-Disk.  Why my computer refuses to boot to a Ubuntu Live Disk is a mystery to me.  

Ubuntu has been backing up my system regularly, but I can't access the backups.

I can't even find GParted as a Windows file to install in Windows;  it only comes as a Live CD these days.  If I had it, I would just erase both HDDs and do a clean install, but I would like to be able to find those two Linux files and save them to my external HD before I start all over from scratch.

---

### Post by yancek on 2019-01-09
Are you actually using a DVD rather than a CD?  It has been several years since most Ubuntu derivatives would fit on an actual CD.  How are you burning the various Ubuntu's to the DVD, which software do you use on windows?  Do you have another computer available to test to see if the DVD boots on  it?  If you can boot one CD from the CD drive, you should be able to boot others unless they were improperly written.

[QUOTEI am using Boot-Repair-Disk which uses lubuntu 14.04.  When I ask it to reinstall Grub it gives me this message:][/QUOTE]

I don't understand that comment, you seem to have it backwards as if you have an install DVD/flash drive of Ubuntu/Lubuntu,etc. you should be able to put the boot repair software on it rather than the reverse.

If you have some files on your Linux system, you may be able to download software which can read a Linux filesystem from windows 7.  Definitely cannot do that with a default installation of windows so you might try an online search for that type of sofware.

---

### Post by vineyridge on 2019-01-09
1) My ubuntu install disks are all DVDs.  Boot-Repair-Disk is also on a DVD.  That DVD will boot.   My Clonezilla DVD will also boot. None of the "pure" Ubuntu install disks will boot.  I made the Clonezilla disk the same day that I made the Ubuntu disk of 18.04 LTS.
2) I am burning to disk with CDBurnerXP latest edition which has always worked before.
3) I installed Linux Reader yesterday.  I just looked at sdb6 with it, and it shows a 4k "bin" file in /mnt/boot-sav/sdb6 that is empty. 

If Boot-Repair-Disk can reinstall Grub if I install a repository for it, can I use the command ```
sudo apt-get install repository 
``` to install a repository that contains Grub2 software?  If so, what would be the correct command for a repository that includes Grub2 install files?  Maybe "main"?

---

### Post by yancek on 2019-01-09
Have you read through the Ubuntu documentation on installing/re-installing Grub at the link below?

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

It seems a little strange that you can boot the boot repair iso from a DVD and not the Ubuntu DVD.  Did you verify the download of the Ubuntu iso before burning it to a DVD?  Are you able to test it on another computer?

I've never used CDBurnerXP so have no advice on that.  My understanding is that the boot repair on the iso is less up to data than boot repair from the :ppa.  I doubt very much that you would be able to add a repository to the Boor Repair CD.  The suggestions you referred to in your initial post were apparently to add archived repositories because I'm sure support for Lubuntu 14.04 has ended.  In any case, you would need to add repositories in the /etc/apt/sources list file and then update and upgrade.

---

### Post by vineyridge on 2019-01-09
I do not have access to another computer, but, if necessary, will try to find one.

> The suggestions you referred to in your initial post were apparently  to add archived repositories because I'm sure support for Lubuntu 14.04  has ended.  In any case, you would need to add repositories in the  /etc/apt/sources list file and then update and upgrade.

This is exactly what I want to do before trying anything else, I am desperate to do it,  but I don't know how to do it.  
1) What repository will include Grub2?
2) What code would I need to input in the Boot-Repair-Terminal to add that repository to /etc/sources list file?
3) What code would I need to input to update?
4) What code would I need to input to upgrade?

I have found the code for updating and upgrading before, and I can certainly search to find it again, but the repository and the code for installing that particular one would be unique to that repository.

I should mention that I have tried many, many proposed fixes from AskUbuntu in the terminal, and none have worked.

---

### Post by yancek on 2019-01-09
Any Ubuntu or derivative will have the necessary Grub2 boot files.  If all you have working is the boot repair iso on a DVD, I don't see how any of the rest of this would work because it isn't an operating system and doesn't have the directories/files necessary.  If you could boot any Ubuntu on a DVD, I would expect it would not be difficult to resolve this problem but I have no idea why you cannot boot any OS but only the boot repair software.

---

