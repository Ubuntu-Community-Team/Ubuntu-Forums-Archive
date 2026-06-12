---
title: "unable to access my backup"
date: 2018-06-01
forum: General Help
---

### Post by jacko777 on 2018-06-01
Hello all, it seems I have another problem on ubuntu 16.04.  I am unable to access the area where I stored my backups.  The history.. I changed to ubuntu 18.04 and meandered around it for a week or so, it didn't have the things I was used to so I formatted the drive and reinstalled 16.04.  My backups are on an external hard drive which I haven't fooled with and hoped to restore all my old programs and data, no go.  I will enclose the error message.
```

Error mounting /dev/sdb4 at /media/rod/2fbed22f-6238-482e-af83-9daaa16ab9f9: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb4" "/media/rod/2fbed22f-6238-482e-af83-9daaa16ab9f9"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb4,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

I hope someone can advise me if things are recoverable, or have I lost the lot.?

Regards,
Rod

---

### Post by TheFu on 2018-06-01
How was the backup made? Which program was used?  Was it tested previously?  Meaning, did the test restore work?

Gather some info:
* sudo fdisk -l
Is the partition really ext4?   That is most likely, but best to be certain.

Attempt to run fsck against the correct partition.
* sudo fsck /dev/sdb4

Keep any error messages, and post them.   The problem could be minor or it could be a total loss. Can't tell yet.  The program used to make the backup is very important to know.  Hopefully, it is the former.  Wouldn't hurt to use a different USB port and cable. 

Searched these forums and found a few other similar problems with some other ideas for a solution. 1 was to use a different version of Linux. For that person, it connected the disk to a different USB port, with a different cable, with different versions of the software.

---

### Post by jacko777 on 2018-06-01
Hello The Fu,
The original backups were done using back in time, I have used them on numerous occasions when I messed something up.  No problems then.  It is only since I installed ubuntu 18.04 and played with it for a week finding the dash too different to manage.  I reformatted drive /dev/sda and reinstalled ubuntu 16.04.  This is when things went pear shaped.
I enclose the results from the two tests that you asked.
```

  	 	 	 	   rod@rod:~$ sudo fdisk -l
 [sudo] password for rod:  
 Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 Disklabel type: dos
 Disk identifier: 0xaf044255
 
 
 Device     Boot      Start        End    Sectors  Size Id Type
 /dev/sda1  *          2048 3899244543 3899242496  1.8T 83 Linux
 /dev/sda2       3899246590 3907028991    7782402  3.7G  5 Extended
 /dev/sda5       3899246592 3907028991    7782400  3.7G 82 Linux swap / Solaris
 
 
 Partition 2 does not start on physical sector boundary.
 
 
 
 
 Disk /dev/sdb: 931.5 GiB, 1000204885504 bytes, 1953525167 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disklabel type: dos
 Disk identifier: 0x1e363c21
 
 
 Device     Boot      Start        End   Sectors   Size Id Type
 /dev/sdb1  *          2048   98435071  98433024    47G 83 Linux
 /dev/sdb2         98437118  498669567 400232450 190.9G  5 Extended
 /dev/sdb3        498669568 1318356991 819687424 390.9G 83 Linux
 /dev/sdb4       1318356992 2058717183 740360192   353G 83 Linux
 /dev/sdb5         98437120  243357695 144920576  69.1G 83 Linux
 /dev/sdb6        243359744  490885119 247525376   118G 83 Linux
 /dev/sdb7        490887168  498669567   7782400   3.7G 82 Linux swap / Solaris
 
 
 Partition table entries are not in disk order.
 rod@rod:~$  

```

and..

```

  	 	 	 	   
rod@rod:~$  sudo fsck /dev/sdb4
 fsck from util-linux 2.27.1
 e2fsck 1.42.13 (17-May-2015)
 The filesystem size (according to the superblock) is 92545024 blocks
 The physical size of the device is 79396021 blocks
 Either the superblock or the partition table is likely to be corrupt!
 Abort<y>? no
 /dev/sdb4 contains a file system with errors, check forced.
 Pass 1: Checking inodes, blocks, and sizes

 Pass 2: Checking directory structure
 Pass 3: Checking directory connectivity
 Pass 4: Checking reference counts
 Pass 5: Checking group summary information
 Error reading block 79691776 (Invalid argument) while reading inode and block bitmaps.  Ignore error<y>? yes
 Force rewrite<y>? yes
 Error reading block 80216064 (Invalid argument) while reading inode and block bitmaps.  Ignore error<y>?  

```

I hope this sheds some light on the problem.

Rod

---

### Post by TheFu on 2018-06-02
I've used B-i-Time before, at Mom's place.  Works fine, provided it is run as root so file ownership and permissions are maintained.
Bad superblock isn't good.  The size reported and the actual size are way off.  [https://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](https://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/) has some steps. Just be certain you use ext4 where needed.

Also might need to boot off alternate media - i.e. a flash boot of Ubuntu - to get this working.  I'll cross my fingers for you.

Unrelated, but I have to say something.   The sda disk install partitions are misaligned. On spinning disks, this can cause a 30% performance hit.  That's what this message is saying:  > Partition 2 does not start on physical sector boundary.
It needs to be corrected.

As long as you have to repartition, might as well handle the other issue. Having a single huge partition is a bad idea.   / should never be more than 25G, IMHO. Limiting the partition for / solves all sorts of issues later, before they can happen.  Backups normally happen at the partition or LV levels, so keeping / small is smart and makes backups more manageable.  The best practice is to have / separate from /home and if you are doing server-stuff like running DBs or virtual machines, have a separate /var/ too.
And while you are at it, switching from MBR partitioning to GPT would be good.  GPT also solves some issues, mainly by placing the partition table copies on opposite ends of the disk media, but also by removing the practical limitations on the number of partitions possible.
Why does the installer not do these things for us?  Windows. Windows only works with GPT for 64-bit UEFI installations. Since many people dual boot and the older MBR (MSDOS) style partitioning does work, it is a safe, if less great choice.  Linux doesn't tied the partition table type to the OS.  All supported major linux releases work fine with GPT.

Plus GPT removes the "extended" partition hack.

---

### Post by jacko777 on 2018-06-02
Thank you again The-Fu,
I have just had an awful thought.... I reinstalled ubuntu 16.04 from a disk I made some time ago.
If memory serves me, and it usually doesn't, I made the disk from a system that probably had errors on it.  Hence, I have possibly reloaded a faulty copy of ubuntu.
Once again, if I have to wipe everything, I will reformat the drive with GPT and then reinstall from the ubuntu home.  Then burn another disk and save a copy of the correct parameters.

I tried the 2 tests you suggested but both came up with stacks of errors.
Thank you again for your help, I appreciate your time to help out an old bloke (guy) who seems to mess things up very easily.

Regards,
Rod.

---

### Post by TheFu on 2018-06-03
Ouch.

Nothing can replaced automatic, versioned, backups.  Versioning is absolutely critical, since corrupted files can happen at any point.  A single mirror (like rsync does) just means that the last backup is all you have.  With versioning, any changes to files are seen whether intentional changes or due to corruption/malware.  We get another version and malware doesn't accidentally wipe the only copy.  

B-i-Time does versioning and can be efficient.  Actually, the way that B-i-Time does backups in "automatic" mode is pretty cool.  Basically, it makes a new "snapshot" copy every hour, and selectively deletes a backup "set" over time, leaving daily, weekly, and monthly "sets" as time passes.   B-i-Time does have some failures due to underlying techniques they use with hardlinking between the different versions.  I used B-i-Time for my mother's computer for a few years.

Good luck.

---

### Post by oldfred on 2018-06-03
I also am a proponent of gpt partitioning. 
I started converting to gpt back in 2010 and all new or reformatted drives since then have been gpt, including larger flash drives.

But with gpt you need a bios_grub partition if booting with BIOS or an ESP - efi system partition if booting with UEFI. When I starting to think I may get a newer UEFI system I made new drives with both the ESP  (for future) and bios_grub to work with my BIOS system.

You can use gparted or gdisk to create gpt partitioned drives.
       If drive is only going to be Ubuntu (never Windows in BIOS boot mode), I would suggest using gpt not MBR as the partitioning scheme. You then do not have any logical partitions, they are all primary and it has a backup in case of problems. You do have to create a tiny bios_grub partition to correctly install grub2's boot loader to the drive.
If using gpt with BIOS create a 1MB bios_grub partition with no format. 
 Use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... Or
sudo parted /dev/sda mklabel gpt
Create a mebibyte partition (+1M with gparted, fdisk (only 18.04) or gdisk) on the disk with no file system and with partition type BIOS boot. Select BIOS boot and partition type number 4 for fdisk, ef02 for gdisk, and bios_grub for parted. This partition can be in any position order but has to be on the first 2 TiB of the disk.

---

### Post by jacko777 on 2018-06-04
Many thanks to you both.  Yes.! ouch indeed, ah well I have previously lost the lot a couple of times before and I suspect with my lack of knowledge, I'll lose it all again somewhere down the track.
Also hello to you again Old Fred, I must look through the help list again and find out about the gpt partitioning part of things.  These are things I had never heard of before so I will take the advice and learn how to use it after I clean out all my hard drives and reformat them again.  The backup I had is now useless because when I tried 18.04 for the week or so it did a backup of all my files as ubuntu 18.04.

Again,  BOTHER.!   What a hard way to learn a system.

Thanks both for the guiding hand, I better start learning new things again so I can get started afresh tomorrow or Wednesday.

Kind regards to you both
Rod.

---

### Post by oldfred on 2018-06-04
Do you think drive may ever be in a newer UEFI system? Even if you purchase a used less than 5 year old system, it will be UEFI.
If so I like to include both the ESP & bios_grub partitions.
And I like to have an install even if just for emergency boot on every drive, even data only drives.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[*]/swapfile                                 none            swap    sw              0       0
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

---

### Post by jacko777 on 2018-06-07
Hello oldfred, thank you for those references to people who have had similar problems.
I have read them and saved them in favourites.  The one theme kept popping up.  The format of the system.  I am booting under UEFI, it seems like I should use GPT.
I guess this must be done before starting the installation.

What I have done is found the trial of ubuntu 18.04 lts.  I was searching for my backups on the 1TB drive, it had disappeared, but the other ubuntu was still there.
I was happy enough with it to give it a try because the 16.04 system had no folders or files left in it.  When I opened 18.04 sigh of relief, all my files and folders were in it.

I reformatted both the 2TB disks and copied the 18.04 to both of them, one to fiddle with, the other to keep as a starting point if I mess up one.

I will have to open a new topic because the 18.04 has a problem with the right hand keyboard (number board) does not work at all.  I have to use the main part of the keyboard and delete and use the * and can't use any plus or minus keys.
Oh well !!

I will mark your last reply as the answer to this problem.  Thanks again to both yourself and TheFu for your help.

Kind regards, Rod.

---

### Post by oldfred on 2018-06-07
Not sure how you copied.
But you cannot have duplicate UUID and with gpt cannot copy just one partition as GUID are in partition and in both partition table & backup partition table.
I find it easier to just reinstall & copy data back from backu or run a script for most of the configuration, if testing something different.

---

### Post by TheFu on 2018-06-07
> **oldfred said:**
>  
I find it easier to just reinstall & copy data back from backu or run a script for most of the configuration, if testing something different.

I also do a fresh install, then restore my HOME and application/system settings and DB files, then take a list of packages from the prior backup (I use apt-mark to generate 2 lists), reinstall those packages, and finally recover any huge data while the packages are being re-installed.  Each part takes about 15 minutes, so in 45 min I have a working system that is just missing huge files/media.  The core functionality is there.  Most of my systems really don't have much "data" or anything substantial under /home/, so a restore is usually 30 min of effort to get a working system from the last backup (usually 2am the same day).  

I've gone the custom script-per-system route. Lots of work to maintain and things are forgotten over time.

I've done the DevOps stuff with Ansible and Puppet.  For servers, this isn't too bad, but again, maintaining it is a hassle because the tools deprecate previously fine constructs. It gets frustrating. For a while, standard APT stuff didn't work under Ansible because they broke backwards compatibility.  Puppet is a worse problem than using doing the scripting method. IMHO.

For a desktop system, all my tweaks and settings are back and at login it "feels" like my system.  If I used a DE de-jure, that would be much more complicated from release to release.  But I prefer a simple, lite, environment. No DE, so settings are much easier to manage. There are only 2 files for the GUI on my desktop systems and I haven't seen any huge changes in about 10 yrs through 3-4 LTS migrations.  I care about platform stability, not "cheese" in a GUI.

---

