---
title: "error messages at startup fsck"
date: 2008-05-08
forum: General Help
---

### Post by macjohn on 2008-05-08
I'm having problems mounting my sdc and sdb drives.  Both were working before I unmounted them and ran a check on them using gparted.  The reason I was trying to do a check is I was getting this message on boot, and I'm still receiving it:


Log of fsck -C3 -R -A -y 
Thu May  8 09:21:13 2008

fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: No such file or directory while trying to open /dev/hdb1


The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: No such file or directory while trying to open /dev/hdc1


The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

e2fsck 1.40.8 (13-Mar-2008)
/dev/hdf1: clean, 82287/2448000 files, 3372005/4887768 blocks
/dev/hde1: clean, 43090/30539776 files, 49750528/61049000 blocks
/dev/hdh1: clean, 3214/2448000 files, 1001190/4887768 blocks
/dev/hdg1: clean, 49420/5003712 files, 8614122/10004470 blocks
fsck died with exit status 8

Thu May  8 09:21:14 2008
----------------

---

### Post by macjohn on 2008-05-08
I was able to get my other partitions to mount... it turns out their locations seem to have changed from hdc to sdc and hdb to sdb.

I still get that error on boot though.

---

### Post by kordite on 2008-05-09
I have just suffered the same error but the suggested solution in another thread failed to resolve the issue.

sudo fdisk -l

[FONT="Courier New"]Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 1912 15358108+ 83 Linux
/dev/hda2 9539 9726 1510110 5 Extended
/dev/hda3 1913 9538 61255845 83 Linux
/dev/hda5 9539 9726 1510078+ 83 Linux swap / Solaris[/FONT]

hda1 is the boot drive with the OS
hda3 is where my home directory is

My etc/fstab looked like this:

[FONT="Courier New"]unionfs / unionfs rw 0 0
tempfs /tmp tmpfs nosuid,nodev 0 0
/dev/hda5 swap swap defaults 0 0[/FONT]

so, as per suggestions in another thread, I changed the hda5 to an sda5 and rebooted to the same result. Booting from the CD showed that fstab file was the same that it had been. Did I just not save it? I made sure it wasn't read only, reopened the file after closing it and made sure that the change had been made and rebooted again to the same result.

I'm sure I'm missing something.

---

