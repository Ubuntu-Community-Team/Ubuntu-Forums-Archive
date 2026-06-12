---
title: "dd command question"
date: 2013-06-13
forum: General Help
---

### Post by goodbye-windows(tm) on 2013-06-13
I need to clone my existing 32 GB drive before attempting to recover missing files, files which I think were deleted by accident.

I believe the files are still there but that I have to avoid writing to the drive in order to avoid overwriting them.

So, I want to use the dd command, with sda being my source (input), sdb being my destination (output).

```
[CODE]sudo dd if=/dev/sda of=/dev/sdb
```[/CODE]

SDA is unmounted, a 32 GB SSD and contains the raw data I need to duplicate.

SDB is a new 64 GB USB drive. 

I am using a live cd, ver 13.04.

Gparted would not allow me to do anything to the 64 GB USB drive, saying it was 'in use'. I tried to format it to ext4 (same as my source/input drive), but Gparted wouldn't let me format the drive either.

In order to format the drive, I had to exit from the live cd, then boot from my primary drive. Only then, would it allow me to format the 64 GB usb memory to ext4 (I created a 39 GB ext4 partition).

However, now I can't mount the 39 GB USB drive, getting the following error:

```
[CODE]Error mounting /dev/sdb1 at  /media/artie/f2d6e163-61fe-45f1-9225-ed0093254591: Command-line `mount  -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb1"  "/media/artie/f2d6e163-61fe-45f1-9225-ed0093254591"' exited with  non-zero exit status 32: mount: wrong fs type, bad option, bad  superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```[/CODE]

I have attached screen captures obtained from the Disks tool which comes with my Xubunto 12.10.

I have 2 questions..........

Do I need to format the 64 GB destination/output memory before attempting to use the dd command as stated above?

And, are there changes in 13.04 that make it necessary to do the dd command differently?

TIA.

Art

---

### Post by ahallubuntu on 2013-06-13
~

---

### Post by Cheesemill on 2013-06-13
> **goodbye-windows(tm) said:**
> Do I need to format the 64 GB destination/output memory before attempting to use the dd command as stated above?

No.

If you did any formatting or partitioning on the new drive it would be overwritten anyway when you run the dd command.
The dd command copies everything from the source to the destination, including the partition table and MBR (if any).

---

### Post by goodbye-windows(tm) on 2013-06-13
Thanks to you both, I'll go back to the live cd and try it again.

Art

---

### Post by goodbye-windows(tm) on 2013-06-13
No Joy,

I booted from the live cd, checked the designation on both drives (to confirm I have the correct input and output drives, then confirmed that both drives were unmounted.

I then issued the following and received the following output:

```
xubuntu@xubuntu:~$ dd if=/dev/sda of=/dev/sdb bs=2048
dd: opening ‘/dev/sda’: Permission denied
xubuntu@xubuntu:~$ 
```

I'm using the live cd, so permissions shouldn't be a problem.............

Just before returning to this forum, I tried mounting the 39 GB USB drive (destination/output drive) using a right click on the desktop icon and got the following error:

```
Error mounting /dev/sdb1 at /media/xubuntu/f2d6e163-61fe-45f1-9225-ed0093254591: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb1" "/media/xubuntu/f2d6e163-61fe-45f1-9225-ed0093254591"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Prior to trying to use the 39 GB drive to copy using the dd command, there was other data on it-but I thought anything written on it would be overwritten anyway.

I'm lost.

Art

---

### Post by oldfred on 2013-06-13
I still might try sudo. Sometimes even with liveCD it seems to be needed, but there is no user or password. 

       Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

   from caljohnsmith post #7
> I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)

---

### Post by Bashing-om on 2013-06-13
[COLOR=#000000]goodbye-windows(tm);

And If I may add: In Gparted... make sure that the swap partitions on the hard disk(s) are not mounted (key icon in the "work" display). Seems if the liveCD can find a swap partition on the hard disk... it will use that swap partition.. hence mounted ... and GParted balks.
[/COLOR][INDENT=2][COLOR=#000000]
just a thought

[/COLOR][/INDENT]

---

### Post by ahallubuntu on 2013-06-13
~

---

### Post by wrkrbee1650 on 2013-06-13
First from what I have found is that you can't just make a copy of a drive to usb....you have to create a mount point.

So:

$sudo fdisk -l 

to see your devices.  Determine based upon size what is your 32GB source drive and your destination drive.

Create a folder to mount to:

$ mkdir /mnt/data


Mount your source drive:

$ mount /dev/drivename# /mnt/ddata

Then use dc3dd or program of choice to create image file:

$ dc3dd if=/dev/# of = /mnt/data/imagename.dd

---

### Post by prodigy_ on 2013-06-13
**dd** isn't the best choice for the task. Especially when you're cloning to SSD as it leads to more writes than necessary.

I'd simply create a (large enough) partition on /dev/sdb and then copy system files using one of the commands suggested [here](http://serverfault.com/questions/306538/how-to-move-linux-to-another-partition). Then (assuming /dev/sdb1 is mounted as /mnt/sdb1): ```
sudo grub-install --boot-directory=/mnt/sdb1/boot /dev/sdb
``` and then change the root partition UUID in **/mnt/sdb1/boot/grub/grub.cfg** and** /mnt/sdb1/etc/fstab** to that of sdb1.

To display UUIDs:
```
sudo blkid
```

That's all.

---

