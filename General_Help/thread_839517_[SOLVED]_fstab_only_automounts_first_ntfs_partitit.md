---
title: "[SOLVED] fstab only automounts first ntfs partitition.."
date: 2008-06-24
forum: General Help
---

### Post by UB_DS45 on 2008-06-24
Having trouble getting fstab to automount /media/SEA-2E and /media/SEA-2F
the first line works fine..

Thanks
SD

I've also added a file called pmount.allow with..
/dev/sda5
/dev/sda6
/dev/sda7

-------------------------------------------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=40a6b5b5-0130-408e-9977-76072acf5087 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=40b9c78f-4ae3-4f7c-888e-721dfc530838 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda5	/media/SEA-2D	ntfs	user,fmask=0111,dmask=0000   0   0
/dev/sda6	/media/SEA-2E	ntfs	user,fmask=0111,dmask=0000   0   0
/dev/sda7	/media/SEA-2F	ntfs	user,fmask=0111,dmask=0000   0   0

---

### Post by Nikitas350 on 2008-06-24
Try replace the two last lines with:
/dev/sda6 /media/SEA-2E ntfs defaults,umask=007,gid=46 0 1 
/dev/sda7 /media/SEA-2F ntfs defaults,umask=007,gid=46 0 1

---

### Post by bodhi.zazen on 2008-06-24
naw, just change "user" to auto.

```
/dev/sda6 /media/SEA-2E ntfs auto,fmask=0111,dmask=0000 0 0
/dev/sda7 /media/SEA-2F ntfs auto,fmask=0111,dmask=0000 0 0
```

user = allow users to mount (and umount).
auto = mount @ boot .
You may use both auto and user or users.

@Nikitas350 : Two small "suggestions" if you will.

First umask=000 will make all files executable. IMHO, better to user dmask and fmask (as in the original post).

Second, the last digit should be 0. The 6th digit is used by fsck to check partitions at boot. There are only 3 options, 0 , 1, and 2.

0 = do not check and is best for vfat (FAT) and NTFS.

1 = test first. Use this for root /

2 = test after root. Non root partitions marked with 2 are tested sequentially (in disk order) and you do not need to specifically mark them as 2 , 3, 4 ...

I know it is a little geeky, HTH

---

### Post by UB_DS45 on 2008-06-25
Thanks for the help, unfortunately after two reboots it's still not working. I'll carry on tomorrow as it's been a long day and I'm needing sleep..

PS: I tried both scenarios..

SD

---

### Post by UB_DS45 on 2008-06-25
Let's try again, here's a paste of my entire fstab. This time only the first drive automounts /dev/sda5. I'm also wondering if the file I created pmount.allow is necessary? Also does it matter if their are tabs between the sections in the lines?


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=40a6b5b5-0130-408e-9977-76072acf5087 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=40b9c78f-4ae3-4f7c-888e-721dfc530838 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda5	/media/SEA-2D	ntfs	user,fmask=0111,dmask=0000	0 2
/dev/sda6	/media/SEA-2E	ntfs	auto,fmask=0111,dmask=0000	0 2
/dev/sda7	/media/SEA-2F	ntfs	auto,fmask=0111,dmask=0000	0 2

ALSO MOUNT -A
---------------------
root@Ubuntu-FS:/home/atlantis# mount -a
fuse: failed to access mountpoint /media/SEA-2E: No such file or directory
fuse: failed to access mountpoint /media/SEA-2F: No such file or directory

FDISK FOR DRIVES
---------------------
Disk /dev/sda: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x6a2a9c6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       40632    20478496+   7  HPFS/NTFS
/dev/sda2           40633      484521   223720056    5  Extended
/dev/sda5           40633      203171    81919624+   7  HPFS/NTFS
/dev/sda6          203172      321981    59880208+   7  HPFS/NTFS
/dev/sda7          321982      484521    81920128+   7  HPFS/NTFS

Disk /dev/sdb: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5e395614

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3579    28748286   83  Linux
/dev/sdb2            3580        3738     1277167+   5  Extended
/dev/sdb5            3580        3738     1277136   82  Linux swap / Solaris


Thanks
SD

---

### Post by drs305 on 2008-06-25
/media/SEA-2E and /media/SEA-2F exist, correct? Sorry if that's too obvious.

You say SEA-2D mounts correctly. If you swap SEA-2D and SEA-2E in fstab (so that /sda6 is mounted on SEA-2D) does it mount ok?

You can quickly check this (ignore the in use error messages):
```
sudo umount -a
sudo mount -a
```

---

### Post by bodhi.zazen on 2008-06-25
It is right there in the cryptic error message :

> fuse: failed to access mountpoint /media/SEA-2E: No such file or directory
fuse: failed to access mountpoint /media/SEA-2F: No such file or directory

```
#note this command makes both directories
sudo mkdir /media/SEA-2E /media/SEA-2F

# mount
sudo mount -a
```

---

### Post by UB_DS45 on 2008-06-25
Perfect, all three drives now show on the desktop after reboot..

Now is there a way to have the drives mounted and not have them appear on the desktop :) ??

Thanks
SD

> **bodhi.zazen said:**
> It is right there in the cryptic error message :


---

### Post by drs305 on 2008-06-25
> **UB_DS45 said:**
> Perfect, all three drives now show on the desktop after reboot..

Now is there a way to have the drives mounted and not have them appear on the desktop :) ??

Thanks
SD

Run this. To reset, change 'False' to 'True':
```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'

```

Please mark thread solved with Thread Tools if this is the case.

---

### Post by bodhi.zazen on 2008-06-25
> **UB_DS45 said:**
> Perfect, all three drives now show on the desktop after reboot..

Now is there a way to have the drives mounted and not have them appear on the desktop :) ??

Thanks
SD

My solution to this problem is to mount them outside of /media (/mnt for example). Works for multiple desktops (gnome, xfce, kde) and all users (it is easier to make this "simple" change then change settings for multiple users on multiple desktops).

---

### Post by drs305 on 2008-06-25
> **bodhi.zazen said:**
> My solution to this problem is to mount them outside of /media (/mnt for example). Works for multiple desktops (gnome, xfce, kde) and all users (it is easier to make this "simple" change then change settings for multiple users on multiple desktops).

Those are valid and good points. On the other hand, in ubuntu I can have shortcuts on my panel and can view or not view them with a single click.

---

### Post by bodhi.zazen on 2008-06-25
8)

One of the nice things with Linux, there are multiple ways to skin the cat ...

Works out well unless you are a cat :twisted:

This also means learning new tricks. I guess my problem is I like Fluxbox / XFCE and it is rare I run gnome. :popcorn:

You should be able to do the same regardless of mount point (if interested).

---

### Post by UB_DS45 on 2008-06-26
All I can say is "Pity that poor puddycat" LOL..

Thanks for the help, just when I thought I was a computer guru I installed Linux..

SD

---

