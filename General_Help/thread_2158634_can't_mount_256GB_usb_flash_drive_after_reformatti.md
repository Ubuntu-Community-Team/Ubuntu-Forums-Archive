---
title: "can't mount 256GB usb flash drive after reformatting to ext3 or ext4"
date: 2013-06-29
forum: General Help
---

### Post by goodbye-windows(tm) on 2013-06-29
I just bought a 256GB flash drive on ebay. It came formatted FAT32. 

It appears to hold 256GB in FAT32, but it has errors when I try to copy another HDD to it. I didn't document the errors, but did track down one of them--the file being copied had a ':' in it. So, I wanted to convert it to ext3 or ext4. 

I used gparted to do the reformat (guick format), it completed without errors. 

But, when I try to mount it so I can actually use it for something, I get the following error:

```
Error mounting /dev/sdc1 at /media/artie/d00088ac-46d4-46e8-8e83-1cda4612e4ec: Command-line `mount -t "ext3" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdc1" "/media/artie/d00088ac-46d4-46e8-8e83-1cda4612e4ec"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdc1, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail  or so
```

What does this error message mean and how do I return this drive to proper operation with an ext4 type partition???

TIA

Art

---

### Post by fantab on 2013-06-29
Post the output of:

```
sudo blkid
```

and post the contents of */etc/fstab*

> exited with non-zero exit status 32: mount: wrong fs type

If there an entry in the /etc/fstab about the said disk then compare the UIDs from 'sudo blkid'.

Also, were you able to mount, read and write to the disk when it was fat32?

---

### Post by goodbye-windows(tm) on 2013-06-29
```
artie@xyz-System-Product-Name:~$ sudo blkid
[sudo] password for artie: 
Sorry, try again.
[sudo] password for artie: 
/dev/sda1: UUID="354e83c9-150c-4c0c-bec2-aed6dc748191" TYPE="ext4" 
/dev/sda5: UUID="fd281375-0ce4-4961-afb0-be2102f23a68" TYPE="swap" 
/dev/sdb1: LABEL="backup_10_3_2012" UUID="37c52709-e825-4f6a-ae6d-73ebb0bbfc80" TYPE="ext2" 
/dev/sdb3: LABEL="storage" UUID="95a63f08-8061-48ce-aab1-f77cc1d8652d" TYPE="ext4" 
/dev/sdc1: UUID="d00088ac-46d4-46e8-8e83-1cda4612e4ec" SEC_TYPE="ext2" TYPE="ext3" 
artie@xyz-System-Product-Name:~$ 

```

sdbx is the source drive that contains the data I want to copy to the usb flash drive.

sdc1 is the usb flash drive that is not operating properly.

> 

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=354e83c9-150c-4c0c-bec2-aed6dc748191 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fd281375-0ce4-4961-afb0-be2102f23a68 none            swap    sw              0       0

/etc/stab only mentions my installation drive and the swap partition.

When the drive was formatted to fat32, I wrote to it, filled it with data (up to 256 GB) and deleted data just fine, with the exception of files and folders that were illegal in fat32.

Art

---

### Post by goodbye-windows(tm) on 2013-06-30
I poked around the forum and found lots of folks with similar issues. I don't understand how they resolved their issues however, it's clear that many did not....or that they didn't post how/if the problem was resolved.

After running the crap out of the flash drive with the stock fat32 formatting, I used gparted to format the drive to ext3. I just ran gparted again and noticed a red circular symbol with an exclamation point in the middle of it. Not sure if this is significant.

I ran the following, based on ifo found in similar posts:

```
artie@xyz-System-Product-Name:~$ dmesg | tail
[70358.812226]  sdc: sdc1
[70358.816455] sd 10:0:0:0: [sdc] Attached SCSI removable disk
[70368.176528] JBD: no valid journal superblock found
[70368.176534] EXT3-fs (sdc1): error loading journal
[70378.583547] JBD: no valid journal superblock found
[70378.583560] EXT3-fs (sdc1): error loading journal
[70552.813521] JBD: no valid journal superblock found
[70552.813533] EXT3-fs (sdc1): error loading journal
[71582.576297] JBD: no valid journal superblock found
[71582.576305] EXT3-fs (sdc1): error loading journal
artie@xyz-System-Product-Name:~$ 
```

```
artie@xyz-System-Product-Name:~$ sudo umount /dev/sdc
umount: /dev/sdc: not mounted
artie@xyz-System-Product-Name:~$ sudo e2fsck /dev/sdc1
e2fsck 1.42.5 (29-Jul-2012)
Superblock has an invalid journal (inode 8).
Clear<y>? cancelled!
e2fsck: Illegal inode number while checking ext3 journal for /dev/sdc1

/dev/sdc1: ********** WARNING: Filesystem still has errors **********

artie@xyz-System-Product-Name:~$ 

```

It looks like the drive needs a journal-not sure how to make it happen though. Do I have to do something different when I format the drive in order to have the system create a journal???

I'm going to look at the 'format' command and see if there are options to create a journal during formatting.

Art

---

### Post by HermanAB on 2013-06-30
Howdy,

Some of the older controller chips inside the flash drives only work with Fat32.  If you use another file system on it, it will cause errors when the device switches pages.  That is probably what is going on here too.

Soooo, format it with Fat32 and sell it on Ebay...

---

### Post by goodbye-windows(tm) on 2013-06-30
> **HermanAB said:**
> Howdy,

Some of the older controller chips inside the flash drives only work with Fat32.  If you use another file system on it, it will cause errors when the device switches pages.  That is probably what is going on here too.

Thanks so much for this information Harold. Based on the info, I tested the heck out of the drive and tend to believe this might be the issue.

I tried every format that gparted supports, only ext2 and fat32 produce a formatted drive that appears to be functional.

However, fat32 doesn't like the ':' in the filenames and it refuses to copy some files that point to other resources (I forget the exact error wording). I think these are legitimate errors for fat32, so I tend to believe fat32 (as supplied on the drive by default) is functioning normally.

Ext2 looks good after reformatting. And, it accepts data when I try to copy it. However, many many of the files are actually corrupted when I try to read them, many files are missing (empty folders and no subfolders). I had errors creating some folders and had to skip them in order for the copying to proceed. When I was done, the source drive was 143GB with 62K files...the USB flash drive only contained 13 GB with 13K files.

So, despite the fact that ext2 looked like it was marginally functional during the copy, it really wasn't.

> 
Soooo, format it with Fat32 and sell it on Ebay...

I bought it on ebay, and was worried about getting a counterfeit or fake flash drive. Many of the drives sold on ebay falsify the amount of data they can actually store, see google for other info. While my drive does actaully store ~256GB, it definately won't allow itself to be formatted in anything other than fat32.

I guess I have to decide whether to keep it or return it......

I want to thank all who commented and helped me. Without this forum, I would not be running Linux right now. So, I hope the form continues and prospers.

Regard,

Art

---

### Post by elliotn on 2013-06-30
256GB flash drive? come one that thing is fake, fake as fake, that's why it will not work ever, the biggest flash drive I know is 64GB. so advice just toss it on the bin coz it might be 256mb

---

### Post by goodbye-windows(tm) on 2013-06-30
> **elliotn said:**
> 256GB flash drive? come one that thing is fake, fake as fake, that's why it will not work ever, the biggest flash drive I know is 64GB. so advice just toss it on the bin coz it might be 256mb

I thought the same thing....it's gotta be fake, but bought it anyway. 

In its original fat32 configuration, I loaded it up and it holds 256 GB. Transfer (write) rate is around 16.6 MB per second. 

After i loaded it up, I spot checked some of the files to see if they would indeed open properly, and they did.

I couldn't find any software for testing them in linux, so I manually dropped and dragged files to fill the drive.

I have no reason to doubt it is indeed a 'for real' 256 GB capacity. The drive is physically larger than other usb drives by quite a bit (thicker, longer and slightly wider than most).

If you know of a better way to test it, let me know. If you want me to show you the ebay auction link, I'll be happy to do that as well.

Regards,

Art

---

### Post by kurt18947 on 2013-07-01
Here might be something to try if you feel like tinkering.  Try formatting your drive to exfat.  There are two packages in the repositories 'exfat-utils' & 'exfat-fuse'.  You could install them and try to format your 256 GB. drive to exfat.  I tried these when they were in a ppa rather than in the repositories.  I could read & write to the flash drive, I didn't try formatting using exfat-utils rather formatting in Windows because I wanted to see if these utilities would read & write Windows exfat formatted flash media.  Microsoft has pretty restrictive licensing on exfat so I'm not sure about legalities.  I believe companies who want to produce devices that use exfat have to cough up around $300,000.

---

