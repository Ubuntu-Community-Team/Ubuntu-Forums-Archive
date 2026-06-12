---
title: "Any way to perform a backup of the partition while the system is live?"
date: 2015-07-15
forum: General Help
---

### Post by timonoj on 2015-07-15
Hi! I usually arrive late at home, and would like to transfer all the partition "as is" of my banana pi to a new memory card (faster). Is it possible for me to do a backup of the current memory card while the system is running (i.e, from SSH)? That way I could just transfer the data to a new card while at work and do the swap overnight without any further configuration. Also, wanna see how difficult can it be to back up a server "in production". Not that much of "productivity" here yet, but eh. 

Thanks!

---

### Post by monkeybrain20122 on 2015-07-15
Do you mean cloning the partition? fsarchiver works for live cloning (with options -a and -A)

[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

For the first example of the quickstart guide, you would run 
```
sudo fsarchiver -v -a -A -j4 savefs /media/username/backup/ubntubk.fsa /dev/sda1
```

Where /dev/sda1 is the partition that you are currently using and running fsarchiver from, /media/username/.. would be an external media you want to save the clone to. -v means verbose so you can see printout on terminal while cloning is in progress. -j4 means using 4 threads, change 4 to the number of threads you use.

fsarchiver is in the repository.

---

### Post by timonoj on 2015-07-15
Thanks for your help! It refused to copy a small 60MB vfat partition (unsupported fs), but it seems to be happily backing the 4GB ext4 partition...I think I can just recreate the vfat later on. 
Thanks!

---

### Post by monkeybrain20122 on 2015-07-15
Hi, I have never done anything that requires vfat before. My understanding is that it is needed for UEFI systems. It would be greatly appreciated if you can report back how successful it is to restore your clone.

---

### Post by timonoj on 2015-07-15
...I guess I'll do it the quickest way...I'll re-download the Lubuntu image, so it re-creates the vfat partition, then step the ext4 section with my backup.

---

### Post by timonoj on 2015-07-15
Annnd I messed up the restore. When backing up the filesystem, I chose to back only the second partition, the ext4.

So, the SD looks on my running Banana as follows:
```

NAME        FSTYPE   SIZE MOUNTPOINT LABEL
mmcblk0              7.4G            
|-mmcblk0p1 vfat      60M            
`-mmcblk0p2 ext4     3.4G /     
_______________________________________
        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1            2048      124927       61440   83  Linux
/dev/mmcblk0p2          124928     7167999     3521536   83  Linux

```

So, I chose to back the second partition, ext4, 3.4GB:
```

sudo fsarchiver -v -a -A -j4 savefs ./BananaPi.ext4.fsa /dev/mmcblk0p2

```
But when I restore back to the new SD, which also has a 60MB vfat (FAT16 on gparted) partition, I get the following:

```
$ sudo fsarchiver -vv restfs ./BananaPi.ext4.fsa id=0,dest=/dev/mmcblk0p2
oper_restore.c#150,convert_argv_to_strdicos(): "/dev/mmcblk0p2" is not a valid block device

```

---

### Post by monkeybrain20122 on 2015-07-16
/dev/mmcblk0p2 has to be mounted.

---

### Post by timonoj on 2015-07-16
Hmm...I rebooted the PC, because something went rather wrong, and the results of lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL were no longer matching those of gparted. 
After mounting it, fsarchive complained that it needed to be unmounted :D
But after the reboot, it seems to now behave more properly, and it's restoring the image as expected. Clearly something was fudged up at the OS level. Let's see if this works tonight after all this messing.

---

### Post by tgalati4 on 2015-07-16
Linux has a very handy *cp* command which works with partitions or entire drives:

```
sudo cp /dev/sda /dev/sde
```

The receiving device needs to be the same size or slightly larger.  Understand that the UUID's will be different, so that the copy will not boot until your fix the UUID's or modify the boot scripts and /etc/fstab to use /dev/sdX notation.

For */etc/fstab*:

```
tgalati4@Mint17 ~ $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on **/dev/sdb1** during installation
**UUID=3990b10f-2930-411f-b3b7-0a5f9b236076** /               ext4    errors=remount-ro 0       1
# swap was on **/dev/sdb2** during installation
**UUID=ba9eb8f3-7ab2-4852-96e7-ec1cd703c242** none            swap    sw              0       0

```

For GRUB2:

Substitute all UUID references for their correct /dev/sdX reference.  There are tutorials for how to modify GRUB2.

I have used this method to quickly copy images to 10 embedded pc's bootable SD cards.  So I know it works.

The UUID serves many purposes, including improving security, since you can't substitute a disk drive and boot from it with possible malicious code without manual intervention.  It interferes with quickly copying entire bootable images for multiple devices that work out-of-the-box.

And *cp* works on a running system.

---

### Post by timonoj on 2015-07-16
Thanks! Seems to be working all good after the restore. Thank you guys for your help!

---

