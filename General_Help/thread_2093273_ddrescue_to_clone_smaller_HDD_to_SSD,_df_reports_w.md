---
title: "ddrescue to clone smaller HDD to SSD, df reports wrong size after"
date: 2012-12-10
forum: General Help
---

### Post by zim2dive on 2012-12-10
Started with a 60GB laptop HDD as my boot drive.. I used ddrescue to close to a 90GB SSD (already partitioned to 1 80-something GB partition).

After the clone, df -h on the new drive it reporting it as 48GB...

Disk Utility says its an 86GB partition.

I'm perplexed...I thought I might have to adjust the partition size after the copy.. but I didn't expect the conflicting info.

thanks!
Mike

---

### Post by zero2xiii on 2012-12-10
Hay,

Remember that ddrescue coppies the files as an image. NOT as a copy-paste command. Thus the actual partition you see will be the partition from the original drive. Just resize the partition and it should be fixed :)

Cherz

---

### Post by zim2dive on 2012-12-10
> **zero2xiii said:**
> Hay,

Remember that ddrescue coppies the files as an image. NOT as a copy-paste command. Thus the actual partition you see will be the partition from the original drive. Just resize the partition and it should be fixed :)

Cherz

Well I expected something like that... except when I go to Disk Utility for the SSD, it only shows 1 partition.. and that partition is already the 86GB size.. even tho "df -h" is claiming its a 48G partition...

---

### Post by oldfred on 2012-12-10
Did you clone drive or partition?

Often issues cloning as most users want both drives. So then you have duplicate UUIDs, reinstall grub issues, and fstab issues. 
If not using both drives it should work, but may need partition or drive fixes. One user was never able to fix it with Linux and had to download a drive vendor reset tool to reset sizes correctly.

I prefer just a new clean install and copy /home over for settings. Usually with an SSD you then have data on a rotating drive. If a laptop then copy /home over to SSD also.

SSD's do require different settings also and the Arch site suggests the new gpt partitioning if not using Windows.

Post this - if SSD is sda:
       sudo fdisk -lu /dev/sda
sudo parted /dev/sda unit s print


       
 Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by Pjotr123 on 2012-12-10
A clean installation is definitely the best way. Not only for an SSD, but in general. See it as a chance to start again with a shiny clean and new Ubuntu.... The time investment is small: two hours max, including tuning and tweaking after installation. :)

This may come in handy: I've written a how-to for optimizing an SSD for Ubuntu: [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by zim2dive on 2012-12-10
> **oldfred said:**
> Did you clone drive or partition?

Often issues cloning as most users want both drives. So then you have duplicate UUIDs, reinstall grub issues, and fstab issues. 
If not using both drives it should work, but may need partition or drive fixes. One user was never able to fix it with Linux and had to download a drive vendor reset tool to reset sizes correctly.

I prefer just a new clean install and copy /home over for settings. Usually with an SSD you then have data on a rotating drive. If a laptop then copy /home over to SSD also.

SSD's do require different settings also and the Arch site suggests the new gpt partitioning if not using Windows.

Post this - if SSD is sda:
       sudo fdisk -lu /dev/sda
sudo parted /dev/sda unit s print


       
 Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

I removed the old drive.. only the SSD plugged in.

```
>sudo fdisk -lu /dev/sda

Disk /dev/sda: 90.0 GB, 90028302336 bytes
255 heads, 63 sectors/track, 10945 cylinders, total 175836528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006e006

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   167469055    83733504   83  Linux
/dev/sda2       167471102   175833087     4180993    5  Extended
/dev/sda5       167471104   175833087     4180992   82  Linux swap / Solaris

>sudo parted /dev/sda unit s print
Model: ATA Corsair Force 3 (scsi)
Disk /dev/sda: 175836528s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system     Flags
 1      2048s       167469055s  167467008s  primary   ext4            boot
 2      167471102s  175833087s  8361986s    extended
 5      167471104s  175833087s  8361984s    logical   linux-swap(v1)

>df -h .
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        48G   22G   24G  49% /

```

Added the df at teh end, as that is the part I find confusing.

I'm not at all (yet) aiming for performance with the SSD... step 1 was simply to copy things over from the slow 2.5HDD I had been using.

thanks!

---

### Post by oldfred on 2012-12-10
The total size matches as 512 * 175836528 is your 90028302336.

But 167469055 - 2048 is not 83733504 so the sectors used is not correct. 

Not sure best way to fix.

First backup partition table and copy file to another device.

       First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sda > parts_sda.txt

See what this shows, if not ok, DO NOT do the w.

 sudo fdisk /dev/sda
x  # enter expert mode
f  # fix  partition table
r  # return
p  # to print
v  # to verify partition 
if ok
w  #  write the changes to disk
q  # quit

---

