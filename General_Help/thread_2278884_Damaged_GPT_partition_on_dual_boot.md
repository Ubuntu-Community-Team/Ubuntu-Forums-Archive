---
title: "Damaged GPT partition on dual boot"
date: 2015-05-19
forum: General Help
---

### Post by davidphayden on 2015-05-19
Hello,

I'm new here so thanks in advance for your help!

I have a dual boot Ubuntu / Windows 8.1 situation on my laptop and suddenly ubuntu won't boot; it appears that the GPT partition table is damaged. I've backed up all my files and would be happy just to reinstall ubuntu, but I don't want to mess up windows (which currently works fine). When I run the ubuntu installer it doesn't recognise either OS or any disk partitions, so my question is: what is the best way to fix this?

Some details:

I created the root, home and swap partitions using the "something else" option of the ubuntu installer a few weeks ago and everything worked fine.

Now when I try to boot it drops to BusyBox with the following message:
```
Gave up waiting for root device.
...
ALERT! /dev/disk/by-uuid/xx...xx does not exist. Dropping to a shell!
```

The directory /dev/disk/by-uuid is apparently empty. If I run fdisk -l it lists one partition of /dev/sda and says that /dev/sdb doesn't contain a valid partition table.

Booting from a USB and running gdisk gives very similar results to those in [this thread]("http://ubuntuforums.org/showthread.php?t=1956173"):
```
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda GPT fdisk (gdisk) version 0.8.8


Warning! Disk size is smaller than the main header indicates! Loading
secondary header from the last sector of the disk! You should use 'v' to
verify disk integrity, and perhaps options on the experts' menu to repair
the disk.
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.


Warning! One or more CRCs don't match. You should repair the disk!


Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged


****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************
Disk /dev/sda: 250069680 sectors, 119.2 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 61A53D2D-D9F0-44D7-90EA-B451D65D6F97
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 500121566
Partitions will be aligned on 2048-sector boundaries
Total free space is 4029 sectors (2.0 MiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          821247   400.0 MiB   2700  Basic data partition
   2          821248         1435647   300.0 MiB   EF00  EFI system partition
   3         1435648         1697791   128.0 MiB   0C01  Microsoft reserved part
   4         1697792       342362111   162.4 GiB   0700  Basic data partition
   5       469338112       470259711   450.0 MiB   2700  
   6       470259712       500119551   14.2 GiB    2700  Basic data partition
   7       342362112       381423615   18.6 GiB    8300  
   8       381423616       445876223   30.7 GiB    8300  
   9       445876224       469338111   11.2 GiB    8200 


Command (? for help): v


Caution: The CRC for the backup partition table is invalid. This table may
be corrupt. This program will automatically create a new backup partition
table when you save your partitions.


Problem: The secondary header's self-pointer indicates that it doesn't reside
at the end of the disk. If you've added a disk to a RAID array, use the 'e'
option on the experts' menu to adjust the secondary header's and partition
table's locations.


Problem: Disk is too small to hold all the data!
(Disk size is 250069680 sectors, needs to be 500121600 sectors.)
The 'e' option on the experts' menu may fix this problem.


Problem: GPT claims the disk is larger than it is! (Claimed last usable
sector is 500121566, but backup header is at
500121599 and disk size is 250069680 sectors.
The 'e' option on the experts' menu will probably fix this problem


Problem: partition 4 is too big for the disk.


Problem: partition 5 is too big for the disk.


Problem: partition 6 is too big for the disk.


Problem: partition 7 is too big for the disk.


Problem: partition 8 is too big for the disk.


Problem: partition 9 is too big for the disk.


Identified 10 problems!

```


I have read the gdisk documentation but am hesitant to try to use it because I don't really know what I'm doing.

Finally, in Windows, if I run the Disk Management utility I can see the three linux partitions (just listed as free "healthy partition"s) and there is an option to delete them. If I did this, could I reinstall ubuntu from scratch?

Thank you!

---

### Post by oldfred on 2015-05-19
It is normal that fdisk does not work on gpt drives.

If you have not fully backed up Windows do it now. With my new system which I never plan to run windows I created the Dell recovery, the Windows backup, a Windows repair flash drive and a full backup. 

Use Windows tools for Windows and Linux tools for Linux. Or use gparted to delete the Linux partitions. But it may not work with the gpt error.

Best to use gdisk to fix error first.
       GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk]("http://www.rodsbooks.com/gdisk/")
            [http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
    
Should be as simple as:
sudo gdisk /dev/sda
 Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR. Details:

---

### Post by davidphayden on 2015-05-19
Hi oldfred,

Thanks a lot for your help.

Here is the result of gdisk /dev/sda attempt to write (option w) and fix (expert option e): (see my first post for options p and v)
```
Command (? for help): x

Expert command (? for help): e
Relocating backup data structures to the end of the disk

Expert command (? for help): w

Warning! Secondary partition table overlaps the last partition by
250049905 blocks!
You will need to delete this partition or resize it in another utility.

Problem: partition 4 is too big for the disk.

Problem: partition 5 is too big for the disk.

Problem: partition 6 is too big for the disk.

Problem: partition 7 is too big for the disk.

Problem: partition 8 is too big for the disk.

Problem: partition 9 is too big for the disk.
Aborting write operation!
Aborting write of new partition table.


```

So it seems the last partition is much too large and gdisk wont update the secondary partition table. I have no idea why this is. I then tried gparted to resize the partition but got this:
```

ubuntu@ubuntu:~$ sudo gparted /dev/sda
======================
libparted : 2.3
======================
(gpartedbin:4581): GLib-CRITICAL **: Source ID 7 was not found when attempting to remove it
...
(gpartedbin:4581): GLib-CRITICAL **: Source ID 44 was not found when attempting to remove it
Invalid argument during seek for read on /dev/sda
The backup GPT table is corrupt, but the primary appears OK, so that will be used.
Backtrace has 9 calls on stack:
  9: /lib/x86_64-linux-gnu/libparted.so.0(ped_assert+0x31) [0x7f5d594b44b1]
  8: /lib/x86_64-linux-gnu/libparted.so.0(+0x3f5f6) [0x7f5d594e45f6]
  7: /lib/x86_64-linux-gnu/libparted.so.0(ped_disk_new+0x49) [0x7f5d594b9f99]
  6: /usr/sbin/gpartedbin() [0x4701e9]
  5: /usr/sbin/gpartedbin() [0x4792d9]
  4: /usr/lib/x86_64-linux-gnu/libglibmm-2.4.so.1(+0x41a4d) [0x7f5d57f45a4d]
  3: /lib/x86_64-linux-gnu/libglib-2.0.so.0(+0x6df05) [0x7f5d57561f05]
  2: /lib/x86_64-linux-gnu/libpthread.so.0(+0x8182) [0x7f5d568b9182]
  1: /lib/x86_64-linux-gnu/libc.so.6(clone+0x6d) [0x7f5d565e600d]
Assertion (last_usable <= disk->dev->length) at ../../../libparted/labels/gpt.c:994 in function _parse_header() failed.
Aborted (core dumped)

```

Any ideas?! Or any other ways to resize the partition?

Thanks again.

---

### Post by oldfred on 2015-05-19
The overlap is too large. I have seen where it is just a few sectors and you then can resize partition to resolve issue.

Do not start graphical applications with sudo. Use gksudo, which I believe is not even included by default in the newest versions of Ubuntu. You can create even larger issues using sudo with graphical apps.

It is even saying partition 4 is an issue, and is that your Windows??
What are the other partitions? Just Ubuntu or a system recovery also? 
Seems like a lot of partitions? Ubuntu default install is just / (root) & swap and you do not even show swap?
What size is drive, it says 119.2GBb with 250 Million sectors, but partitioning shows use of 500 Million sectors.
Did you clone this from a larger drive?

---

### Post by davidphayden on 2015-05-19
OK, thanks. For some reason I'm not able to install gksudo here, but I'm guessing I have bigger problems.

There are two physical drives of 128GB each, but in windows you only see one of 256GB. I am honestly out of my depth here but what it looks like it's doing is trying to fit 256GB of partitioning onto sda, which is half that size. This is a new laptop and the only thing I did was create the three linux partitions: root (#7), home (#8) and swap (#9). The rest are all Windows stuff and were there already.

---

### Post by Vladlenin5000 on 2015-05-19
> **davidphayden said:**
> There are two physical drives of 128GB each, but [COLOR=#ff0000]in windows you only see one of 256GB[/COLOR].

This is the problem. It seems you have some (software) RAID created in Windows.

---

### Post by davidphayden on 2015-05-19
Yes, I think you are right. How did it work for a couple of weeks and then stop? And what should I do now?

---

### Post by Vladlenin5000 on 2015-05-19
You should know, unless it came factory installed that way, in which case what baffles me is how you managed to install Ubuntu in a successful dual boot, without being aware of the RAID.
Something you did in Windows is way more plausible.

---

### Post by davidphayden on 2015-05-20
Thanks Vladlenin.

I have no idea how it managed to work up until now. I'm reading up on ubuntu dual boot with RAID, but for now I'm at a loss as to how to fix this. Since neither gdisk nor gparted are working for me, the only thing I can think of is to wipe the partitions from windows and install ubuntu again from scratch. Any idea if this would work?

---

### Post by oldfred on 2015-05-20
RAID 0 is provided by a few high end systems.
But since we now have SSD, the speed increase from RAID 0 with SSD is minimal. And with RAID 0 you are not using a recommended reliable system, but one that is just for speed.

       Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

Several other users have posted they just break the RAID and have one drive for Windows and one drive for Ubuntu.
But you have to turn RAID off in UEFI/BIOS and probably have to remove RAID metadata from drive. Often that metadata was why desktop Ubuntu would not install to a RAID.

This will break the RAID, so do not run this unless that really is what you want.

 Even if raid not used BIOS may have set parameters, Also check BIOS settings
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Run chkdsk on any NTFS partitions even if they currently work.

---

### Post by davidphayden on 2015-05-20
OK I wiped the linux partitions from the windows disk management, ran chkdsk and will start again from scratch. I'll either remove RAID altogether (which I think would involve reinstalling windows) or try to install ubuntu with RAID (which I'm expecting will be trickier). Thanks for the help, oldfred.

---

### Post by oldfred on 2015-05-20
Several threads where users did different things. Some older, newer versions of Ubuntu should be easier.
 Acer S7 14.04 & Windows 8.1 RAID
[http://askubuntu.com/questions/590644/install-ubuntu-14-04-2-lts-alongside-windows-8-1-dual-boot-on-raid-acer-s7-quest](http://askubuntu.com/questions/590644/install-ubuntu-14-04-2-lts-alongside-windows-8-1-dual-boot-on-raid-acer-s7-quest)

 Sony Vaio  - EFI dualboot Ubuntu 12.04 and Windows 8 in Raid0 
[http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/](http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/)

 Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)

---

### Post by davidphayden on 2015-05-20
OK, I actually have an Acer S7 as well. I tried the first link and it doesn't work (gparted just shows two unformatted disks) then, from the third link, I followed your suggestion:
> Disable the RAID, for me it was using the Intel rapid management thingy  and telling it to disable the acceleration or the use of the SSD. If you  have a different system, just disable the RAID system then install  Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb but also to no avail. Do you know how to re-enable the RAID (since of course now windows can't boot either)?

---

### Post by oldfred on 2015-05-20
It should be a setting in UEFI/BIOS for drive. 
Most that convert also change drive setting from RAID to AHCI. 
Not sure now with UEFI if that makes a difference or not.

---

### Post by davidphayden on 2015-05-20
Hmm it's still set to RAID in UEFI. I switched it to AHCI and back to RAID but it doesn't offer windows as a boot option... by erasing the metadata have I rendered it useless?

---

### Post by oldfred on 2015-05-20
This was the Intel SRT which looks like RAID to Ubuntu, but perhaps your actual RAID is different.

 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

Do you have a Windows repair flash drive? Often it needs refreshing. Either chkdsk or just its repairs run from its repair console.

---

### Post by davidphayden on 2015-05-26
Thanks again for your help, oldfred. I got everything working in the end by disabling RAID and reinstalling both OS's, one on each hard drive.

In case anyone else has the same problem, I would suggest (after backing everything up) disabling RAID and following the advice and links above. For some reason my windows 8 backup didn't work (perhaps because of RAID?) and I had to reinstall it by making a USB from another windows 8 machine as in [this link]("http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html").

---

