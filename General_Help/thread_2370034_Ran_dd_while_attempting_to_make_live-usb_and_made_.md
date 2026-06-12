---
title: "Ran dd while attempting to make live-usb and made a mess of it! Wiped my partitions."
date: 2017-08-29
forum: General Help
---

### Post by fiddybux on 2017-08-29
Hi all,

I made a grave error this evening. I ran dd while trying to make a live-usb and I made a huge mistake.

Essentially, I think, I instructed dd to overwrite the whole hard drive, rather than the usb drive.

Fortunately, only weeks ago, I posted the current partition data for my current setup, and I hope this can be of use to someone well-informed that can advise me.

[https://ubuntuforums.org/showthread.php?t=2369121]("https://ubuntuforums.org/showthread.php?t=2369121")

```
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags	Description
 1      1049kB  112GB  112GB   primary   ntfs            boot	Windows 7
 3      112GB   128GB  16.1GB  primary   ext4			Ubuntu /root
 4      128GB   181GB  53.6GB  primary   ext4			Ubuntu /home
 2      181GB   250GB  68.7GB  extended
 5      181GB   197GB  16.1GB  logical   ext4			Debian /root
 6      197GB   246GB  48.3GB  logical   ext4			Debian /home
 7      246GB   250GB  4294MB  logical   linux-swap(v1)		Shared swap-space
```

So, I do still have the exact structure of my hard drive before I made the dd error this evening.

I am currently typing this from a live-media which is now booting from the first couple of blocks on /dev/sda (rather than /dev/sdb1, as it should have been)! My grub2 has gone (it's the live media one - Debian 9.1 non-free actually).

I haven't done anything with the hard disk yet...only run testdisk to see what it finds in analyse mode. It's found all my tux partitions, but not the Windows 7 partition that resides in partition 1.

I gather that having the specific UUID's of the partitions is not relevant here, since it's likely I need to rebuild the partitions (if this is at all possible).

My partitions currently look like this, as checked from the Debian live-media (currently booting from /dev/sda!):

```
user@debian:~$ sudo fdisk -l
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6eb1f60b

Device     Boot Start     End Sectors  Size Id Type
/dev/sda1  *        0 4532511 4532512  2.2G  0 Empty
/dev/sda2        1568    2399     832  416K ef EFI (FAT-12/16/32)

Disk /dev/loop0: 2 GiB, 2090766336 bytes, 4083528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

As you can see, it looks nothing like it should do any more. Oops! I done a stupid. :(:(

The output of 'testdisk' in Analyse mode shows this:

```

TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63

     Partition                  Start        End    Size in sectors

 1 * FAT12                    0  24 57     0  38  6        832 [NO NAME]
 2 P Linux                13576 117 46 15534 149 39   31457280
 3 P Linux                15534 149 40 22046 160  2  104615936
 4 E extended LBA         22046 160  3 30401  75 10  134217728
 5 L Linux                22046 192 35 24004 224 28   31457280
 6 L Linux                24005   1 61 29879  32 41   94367744
 7 L Linux Swap           29879  65 11 30401  75 10    8386560
```

I still have connectivity, I can install packages within this live-media. I have no idea if it is persistent - probably not.

Can anyone help me out of this pickle?

I'm hoping that I can get everything back by rebuilding the partition table and MBR (based on the information I've provided here), then reinstalling grub2 and all will be well.

If not, I've been meaning to install a 64-bit Linux anyway, so maybe now is the time.

There is nothing majorly critical on any of these partitions. I've backed up the most important stuff, but still, I'd like not to have to start again if at all possible.

Thank you kindly good people of Ubuntuforums!

---

### Post by oldfred on 2017-08-29
If you used the dd to install the ISO to the flash drive, but installed to the HDD, then you overwrite the first 2GB of drive. So while only the first 2GB of Windows is gone, that is usually a lot and it would be impossible to restore a working Windows. You can recover some/most data with tools like photorec, although those that are Windows users suggest similar Windows tools may work a bit better.

You can use testdisk or parted rescue to restore partitions, and could edit partition table to include the NTFS partition. And re-install grub boot loader for either Ubuntu or Debian with Boot-Repair or manually.

 Used parted rescue
[https://ubuntuforums.org/showthread.php?t=2362656](https://ubuntuforums.org/showthread.php?t=2362656)
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405)

Normally suggest backup, but it does not look like you have much to backup. If after recovering Linux partition, you want to edit partition table, then you need backup and manually edit backup before restoring it.
backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print 


 Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. 
Also fdisk -lu shows start & blocks, blocks * 2 also equals size in sectors
Newest versions of fdisk can show sectors now instead of blocks.

---

### Post by HermanAB on 2017-08-30
Hmm, Data Definition (dd) is perhaps better known as Disk Destroyer and there is likely no easy way to recover.  Therefore reinstall the system and get your data from backup.

---

### Post by fiddybux on 2017-08-30
Thanks all. I thought as much. I'll give testdisk a proper whirl...I think that will recover my Linux partitions without many issues, then I'll wipe the entire machine after recovering any days I might fancy keeping, and go for a simple one distro machine. Cheers.

---

### Post by sudodus on 2017-08-30
I'm sorry to read that dd has caused problems again. I agree with the advice of the previous posts (by oldfred and HermanAB).

I would add: if there are really important data to recover, you can **clone the drive and use recovery tools on the cloned copy** according to the following link.

[Repair the partition table and file system of a pendrive](https://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

When nothing else works, you can resort to **PhotoRec**, but it means a lot of hard work, and you will only recover some of the data (those that are not overwritten by dd, and fragmented files are problematic).

-o-

I suggest that in the future you should use a **tool with a final checkpoint**, so that you can double-check that you are cloning from the iso file to the correct drive (to avoid overwriting valuable data).

You can do this in Linux with

- the **Ubuntu Startup Disk Creator** in Ubuntu 16.04 LTS and newer versions

- **Disks** alias gnome-disks

- **mkusb** according to this link: [help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

and in Windows with

- **Win32 Disk Imager** according to this link: [wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by fiddybux on 2017-08-30
> **sudodus said:**
> I'm sorry to read that dd has caused problems again. I agree with the advice of the previous posts (by oldfred and HermanAB).

I would add: if there are really important data to recover, you can **clone the drive and use recovery tools on the cloned copy** according to the following link.

[Repair the partition table and file system of a pendrive](https://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

When nothing else works, you can resort to **PhotoRec**, but it means a lot of hard work, and you will only recover some of the data (those that are not overwritten by dd, and fragmented files are problematic).

-o-

I suggest that in the future you should use a **tool with a final checkpoint**, so that you can double-check that you are cloning from the iso file to the correct drive (to avoid overwriting valuable data).

You can do this in Linux with

- the **Ubuntu Startup Disk Creator** in Ubuntu 16.04 LTS and newer versions

- **Disks** alias gnome-disks

- **mkusb** according to this link: [help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

and in Windows with

- **Win32 Disk Imager** according to this link: [wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

Thank for this.

I recall now that I simply neglected to add 1 or 2 to the end of my /dev/sdxn command...very simple mistake, and sudo'ed so done and done. Oops.

dd really should have a confirm options - I agree.

I have a day of data recovery in front on me...we've all been here, sorry that I'm here yet again!

Thanks for the support.

On the bright side, I've been meaning to put 64bit Ubuntu on for ages! ;)

---

### Post by sudodus on 2017-08-30
Good luck with the recovery work and with your new 64-bit Ubuntu version :-)

---

