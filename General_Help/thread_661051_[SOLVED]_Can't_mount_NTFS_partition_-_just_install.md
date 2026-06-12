---
title: "[SOLVED] Can't mount NTFS partition - just installed Gutsy Gibbon"
date: 2008-01-07
forum: General Help
---

### Post by markoman on 2008-01-07
Hi there

I can't access any of my files (photos, music, everything) and I would really appreciate some help - I looked for similar threads but haven't found anything quite the same.

I have a Gateway laptop with windows XP, and I've just installed Ubuntu Gutsy Gibbon, (on the same hard drive using partitions).

Gateway had already partitioned the hard drive in two: a small 'recovery partition' (3.7GB) and the main partition which had XP - I've shrunk the main one a bit (now 45GB) to make space for Ubuntu.

In Ubuntu, I can access the small recovery partition, but not the main one, which has all my files on it!! Annoyingly, and I don't know if this is related, I can't boot into Windows now either - it looks like it goes to (Windows logo and progress bar), but then restarts again and loops over and over.

So now I CAN'T ACCESS ANY OF MY FILES AAAAAGGGGHHHH!!!!!!!!
(I know I should have backed them up but I didn't really have the means (no DVD writer, etc.)

Here is the output of fdisk -l:

----------------------------------------------
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         488        6356    47142742+   7  HPFS/NTFS
/dev/sda2               1         487     3911796    b  W95 FAT32
/dev/sda3            6357        7249     7173022+  83  Linux
/dev/sda4            7250        7296      377527+   5  Extended
/dev/sda5            7250        7296      377496   82  Linux swap / Solaris

Partition table entries are not in disk order
-----------------------------------------------------------------------

And if I try to mount using ntfs or ntfs-3g, I get the following:

> sudo mount -t ntfs /dev/sda1 /media/oldhd
-------------------------------------------------------------------------------
ntfs_attr_pread: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
Unmounting /dev/sda1 ()
----------------------------------------------------------------------------

If anyone can help me I'll be extremely grateful, as I've got to the head-bashing stage where I just don't know what to do, and I need to access these files.

Thanks so much

---

### Post by emptythevoid on 2008-01-07
Load up your Windows and allow it to boot normally.  If it begins to run the hard disk check, let it run and finish (resizing partitions usually causes Windows to run this - otherwise the drive is flagged as "dirty" and Ubuntu won't mount it correctly).  Once Windows has loaded, shut it down completely (don't hibernate - hibernating Windows causes it to make all NTFS drives "dirty").  See if that makes any difference.

Gutsy should automatically mount any NTFS drives unless Windows wasn't shut down correctly (is hibernating) or something else has caused the NTFS partitions to be flagged as dirty.

---

### Post by Craigus on 2008-01-07
```
Partition table entries are not in disk order
```

I haven't seen that before, and it seems odd.

What happens if you try to mount the ntfs partition with:

```
sudo mount -t ntfs /dev/sda[COLOR="Red"]2[/COLOR] /media/oldhd
```

Also, can you post your /boot/grub/menu.lst ...

---

### Post by markoman on 2008-01-07
Hi Guys

Thanks ever so much for replying.

emptythevoid - unfortunately I can't boot up Windows either now. It goes to the Windows XP logo as normal, then for a split second there's a blue screen with writing which is too quick to read, then it reboots, and it keeps doing this in a loop.
Do you know of any other ways of flagging the partition as 'not dirty'?

Craigus - Looking at other posts about Gateway laptops it seems as though the partitions are in the order sda2 then sda1.
When I use 'sudo mount -t ntfs /dev/sda2 /media/oldhd' I get:
```
NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```
I guess it's just that that partition is FAT32.

My /boot/grub/menu.lst is as follows (I've omitted a lot of the commented sections):
```

## default num
default         0

## timeout sec
timeout         10

## hiddenmenu
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# password topsecret

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=336b4294-558f-47f8-b196-3f113ecd3404 ro

## Setup crashdump menu entries
# crashdump=0

## default grub root device
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
# alternative=true

## should update-grub lock alternative automagic boot options
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
# defoptions=quiet splash

## should update-grub lock old automagic boot options
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
# howmany=all

## should update-grub create memtest86 boot option
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=336b4294-558f-47f8-b196-3f113ecd3404 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=336b4294-558f-47f8-b196-3f113ecd3404 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# Added by me (markoman) to get it to point to correct Gateway partition (i.e. not the recovery partition)
# Copied from http://www.geocities.com/hammerjw/gateway7422gx_linux.html 06 Jan 2008

title Gateway Restore
        root (hd0,1)
        makeactive
        chainloader +1

title Windows XP
        root (hd0,0)
        makeactive
        chainloader +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2 (commented out by markoman)
#title          Windows NT/2000/XP
#root           (hd0,1)
#savedefault
#makeactive
#chainloader    +1


```

Thanks again.

---

### Post by logos34 on 2008-01-07
It seems to me that you need to find a way to get windows to run checkdisk all the way through.  Try to get your hands on a XP install cd and run it from the recovery console:

chkdisk /r

But even that may not prevent it from boot looping

---

### Post by Craigus on 2008-01-07
You have a pm.

---

### Post by markoman on 2008-01-09
Joy!!!! I've managed to both log in to windows and mount the partition in linux (obviously was the same problem).

Was fixed by running chkdsk (needed to do it twice for some reason) on the partition from the windows recovery console as suggested by logos34.

Thanks everyone for your help - much appreciated.

---

### Post by logos34 on 2008-01-09
> **markoman said:**
> Joy!!!! I've managed to both log in to windows and mount the partition in linux (obviously was the same problem).

Was fixed by running chkdsk (needed to do it twice for some reason) on the partition from the windows recovery console as suggested by logos34.

Thanks everyone for your help - much appreciated.

Wonderful.  Enjoy.  Go to 'thread tools' and mark as 'Solved'.

---

