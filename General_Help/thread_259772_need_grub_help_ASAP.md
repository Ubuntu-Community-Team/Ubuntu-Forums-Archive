---
title: "need grub help ASAP"
date: 2006-09-17
forum: General Help
---

### Post by Polygon on 2006-09-17
i need help FAST

i have a homework assignment due monday on my ubuntu drive

i reinstalled windows yesterday, so it wiped out the mbr

so... i follow numerous guides to reinstall grub, mostly this one: [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

ive successfully mounted my ubuntu boot partiton and installed it to there, no luck, still boots to windows

i tried going into my bios to change my third (after floppy and cdrom) boot disk, but all 4 choices do nothing and it still boots to windows


do i need to install grub to my windows drive?


and also, any reason on why i cannot access my root partion? ive tried every live cd i have and all of them say that my root partiton is an "unknown fs and none is specified", so i cannot rescue my assignment and work on it in windows

help please =/

---

### Post by raldz on 2006-09-17
install GRUB to the MBR of your first hard disk.. 

if anything goes wrong, you could always restore Windows XP's boot loader by inserting the Windows CD, go in Rescue mode.. then type: c:\>FIXMBR

---

### Post by Polygon on 2006-09-18
i tried that, i did

```

sudo grub

root (hd1,0) (this is the ubuntu boot partition)

setup (hd0) (my first disk, the windows partion mbr)

quit

```

after that nothing came up, and after "boot from disk:" it just sat there. (which means it couldent boot anything)

so... i pop in my win xp installation disk and restore the mbr... and i try again, this is what i tried:

```

    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd1,0)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "install /grub/stage1 d (hd0,0) /grub/stage2 p /grub/menu.lst "... suc
ceeded
Done.

grub>
```

i would really prefer if i could restore grub without reformatting, because i have something on there that i want to keep, but i cant retreive it because for some reason the root filesystem does not mount for anything else cause it does not have a filesystem specified.... or something

suggestions please.

---

### Post by hearnden on 2006-09-18
The quickest path I can think of to getting files of your Ubuntu partition is to use an ext2/ext3 driver in Windows:

[http://www.fs-driver.org](http://www.fs-driver.org)

This one is really easy to use and I use it to access Ubuntu partitions from Windows.  If this tool can't see your drive, then there's a reasonable chance that something's gone bad.

Another approach is to see what kind of FS is on your Ubuntu partition, you can use fdisk or parted, and I think both should be on the Live CD.  You can run 'parted /dev/hdb' or 'fdisk /dev/hdb', and then print the partition table.  If your Ubuntu partition shows up as something other than ext2, ext3, or fat16/32, then you might have a problem.  If it shows up as something sensible for a Linux partition, then if mount can't figure it out you can tell it explicitly what kind of partition it is:

```

$ mount -t ext2 /dev/hdb1 /my/mount/point

```

where /dev/hdb1 is whatever device corresponds to the first parititon on your second drive.  If that also fails, then you may have a problem.

---

### Post by hearnden on 2006-09-18
In your first grub attempt (which looks right, you definitely want 'setup (hd0)', not 'setup (hd0,0)'), did you get similar output to the second attempt that you pasted, and did grub load at all when you rebooted?  Or did the boot process not get that far before the 'Boot from disk' message?  If you can get grub loaded at all, then you can enter manual boot commands in case your menu.lst is wrong.

---

