---
title: "Made a mistake mounting - need a fix!"
date: 2015-05-22
forum: General Help
---

### Post by Kit_Allen on 2015-05-22
Hi all,
Long story, but I managed to mount my secondary partition (used for media files) to '/'. As I'm new to Ubuntu, didn't know this was an issue. Now Ubuntu won't boot, and I'm in desperate need of a fix asap!

The error that pops up when I boot is something along the lines of "P[COLOR=#000000]ress S to skip, or M to manually edit". Pressing S causes nothing to load (black screen forever), and pressing M I get a terminal-looking screen. Any ideas how to manually change the mount location, or is there another workaround?

Thanks!
Kit[/COLOR]

---

### Post by Elfy on 2015-05-22
Boot with whatever you installed Ubuntu with.

Open a terminal and run 

```
sudo fdisk -l
```

Paste the result here. 

You should be able to mount the real / in that session and check and then edit the fstab file.

---

### Post by Kit_Allen on 2015-05-22
Thank you for the speedy response!

> **Elfy said:**
> Open a terminal and run 

```
sudo fdisk -l
```

Here it is:
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x98b56e86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   153602047    76800000   83  Linux
/dev/sda2       153602048   204802047    25600000   82  Linux swap / Solaris
/dev/sda3       204802048  1953519615   874358784    7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x467de907

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   234438655   117115904    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 8011 MB, 8011120640 bytes
255 heads, 63 sectors/track, 973 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           2    15646719     7823359    c  W95 FAT32 (LBA) 
```

Just for some general info, sdb is running Windows with sda3 being a HDD partition for storing media to be shared between both boots. It is sda3 that I mounted incorrectly.
Thanks for your help :)
Kit

---

### Post by Elfy on 2015-05-22
ok - still in the live session 

```
sudo mount  /dev/sda1 /mnt
```

```
cat /mnt/etc/fstab
```

post that output please

---

### Post by Kit_Allen on 2015-05-22
Here we are:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=3ce07f18-a107-478c-960a-a70e8f477a83 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=0c2587d5-8fa5-4425-a06b-a19e12367428 none            swap    sw              0       0
/dev/disk/by-uuid/D0C2AD4DC2AD391C / auto nosuid,nodev,nofail,x-gvfs-show 0 0
```

---

### Post by Elfy on 2015-05-22
that looks right. 

How did you actually get this partition mounted to / ?

---

### Post by Kit_Allen on 2015-05-22
I used the Disks application (not terminal),  clicked the gear icon with the partition selected, turned off Automatic Mount Options, and changed the Mount Point simply to '/'. Should that usually create issues?

---

### Post by Elfy on 2015-05-22
> Should that usually create issues? Not sure - never use it nor tried mount something to / ;)

Can you try booting normally again and doublecheck the error and warning you get. Words there you might think unimportant could be.

---

### Post by Kit_Allen on 2015-05-22
Just rebooted and took images of the error :P easiest way I suppose.

After selecting the OS to boot as per usual, I get the error:
```
[    7.380447] EXT4-fs (sda1): Unrecognized mount option "x-gvfs-show" or missing value
```

No clue where to go from here. Might get some sleep and check back first thing when I wake, thanks for your help tonight/today (or whatever time it is where you are)!

---

### Post by Elfy on 2015-05-22
> **Kit_Allen said:**
> Here we are:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=3ce07f18-a107-478c-960a-a70e8f477a83 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=0c2587d5-8fa5-4425-a06b-a19e12367428 none            swap    sw              0       0
/dev/disk/by-uuid/D0C2AD4DC2AD391C / auto nosuid,nodev,nofail,x-gvfs-show 0 0
```
sigh - I'm a numpty.

This doesn't look right at all ... 

Do what we did earlier in the livesession to get sda1 mounted to /mnt

Now we'll edit that file in a terminal,

```
sudo nano /mnt/etc/fstab
```

That'll open up the file in a terminal text editor - while it might be new to you, always useful to know how todo that, if you end up in recovery mode ever you'll need it.

Anyway, use the keyboard arrow keys to get to the very last line

/dev/disk/by-uuid/D0C2AD4DC2AD391C / auto nosuid,nodev,nofail,x-gvfs-show 0 0

press Ctrl+k 

that line should disappear, now 

Ctrl+O then enter
Ctrl+X to exit

Reboot.

---

### Post by deadflowr on 2015-05-22
Perhaps comment out the last line in your fstab file.
Follow the advice of mount the system from post #4
but instead of using 
```
cat /mnt/etc/fstab
```
use
```
sudo nano /mnt/etc/fstab
```
then go down to the last line
```
/dev/disk/by-uuid/D0C2AD4DC2AD391C / auto nosuid,nodev,nofail,x-gvfs-show 0 0
```
and add a # symbol to the front like so
```
#/dev/disk/by-uuid/D0C2AD4DC2AD391C / auto nosuid,nodev,nofail,x-gvfs-show 0 0
```
this will mark the line as ignored by the system.
Then save and exit.
(ctrl + x, then press y, and then press enter to save and exit.)

After this you should be able to boot normally and then you can try over...

Hope it helps, and good luck.

Whoops ninja'd.
But I'll keep this as a slightly altered method to elfy's.

---

### Post by Kit_Allen on 2015-05-22
Wow, that worked! I was able to boot into Ubuntu :)

So if mounting at '/' was a bad idea, where is a good location to mount?

Thank you so much for your help Elfy; I'm loving the Ubuntu community and how willing users are to help each other out. I hope to become a knowledgeable Ubuntu user one day and repay my debt!

---

### Post by Kit_Allen on 2015-05-22
Oh and deadflowr, I can see why that would have potentially been a safer idea, but I didn't even see your post - just went right ahead and deleted it hehe. All is working well now though, but thanks for the tip!

---

### Post by Elfy on 2015-05-23
> **Kit_Allen said:**
> ...

So if mounting at '/' was a bad idea, where is a good location to mount?...

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Basically the methodology is create somewhere to mount partitions, then add the necessary information to fstab.

I mount mine in /mnt/foo

```
ls /mnt
films  Links  music  music2  Spare
```

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=6bcbfcc1-c493-4dbe-9421-ef270047a82a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=8291875f-57da-49e2-9c1b-ec41818352d6 none            swap    sw              0       0

##media
UUID=14ee47cc-54cb-4887-8773-fd53121efe10 /mnt/music ext4 defaults 0 2
UUID=aa678306-da8e-4a7d-a2a2-e1de2d3cdedc /mnt/Spare ext4 defaults 0 2
UUID=55dee67a-fcfe-4f61-bec1-b9fd8b583749 /mnt/music2 ext4 defaults 0 2
UUID=7811e4f0-2635-4b1e-bfba-bdd9a09e5ff4 /mnt/Links ext4 noatime,defaults 0 2
UUID=07d4976a-5941-4b0a-b350-aff27bf09209 /mnt/films ext4 defaults 0 2
```

You were on the right track with disks - you just picked the wrong place.

You could - I assume, as I said never used disks for this,make the mountpoint

```
sudo mkdir /mnt/*mymountpoint*
``` changing the name to suit you. 

Then do what you did in disks before hand but choose /mnt/*mymountpoint* instead of / 

You could also use /media/*mymountpoint* instead - some use /mnt some /media

If you do this and get an issue - start a new thread.

---

