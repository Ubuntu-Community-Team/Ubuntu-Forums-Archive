---
title: "mount solaris partition"
date: 2007-05-13
forum: General Help
---

### Post by leptogenesis on 2007-05-13
Hello,

I've recently triple-booted Ubuntu/Windows/Solaris.  I've managed to edit fstab so that Ubuntu auto-mounts Windows and the ext2 shared partition, but I can't seem to get it to mount the Solaris partition.  I tried what this guide suggests:

[http://www.faqs.org/docs/Linux-mini/Linux+Solaris.html](http://www.faqs.org/docs/Linux-mini/Linux+Solaris.html)

but I get the following output:

```

leptogenesis@leptogenesis-laptop:~$ sudo mount -oufstype=sunx86 /dev/sda3 /solaris
/dev/sda3 looks like swapspace - not mounted
mount: you must specify the filesystem type

```

So I tried specifying the filesystem type:

```

leptogenesis@leptogenesis-laptop:~$ sudo mount -t ufs -oufstype=sunx86 /dev/sda3 /solaris
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

No luck.  Here's what fdisk thinks my partition table is:

```

Command (m for help): p

Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3922    31503433+   7  HPFS/NTFS
/dev/sda2            3923        6794    23069340   83  Linux
/dev/sda3   *        6795        9666    23069340   bf  Solaris
/dev/sda4            9667       14409    38098147+   f  W95 Ext'd (LBA)
/dev/sda5           14345       14409      522112+  82  Linux swap / Solaris
/dev/sda6            9667       14344    37575972   83  Linux

Partition table entries are not in disk order

```

and here's my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d1961a81-b9a4-4a6d-9358-c902e66bbdbc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
/dev/sda6 /shared ext2 defaults 0 1
# /dev/sda1
UUID=A4045005044FD8C6 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
/dev/sda5 none            swap    sw              0       0
# /dev/sda3
/dev/sda3 /solaris ufs ufstype=sunx86 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Ultimately I'd like to have Solaris mount automatically.  Any ideas?

---

### Post by hartz on 2007-05-13
I'm guessing the sda3 Solaris partition is "sliced up" into (up to 8) "Solaris" slices.

The page you linked suggests that dev/hda9 through hda14 maps to the Solaris slices s0,s1,s2,s3,s6,s7

Please can you post the output from the command fdisk -l.

---

### Post by leptogenesis on 2007-05-13
Here it is.

```

leptogenesis@leptogenesis:~$ sudo fdisk -l
Password:

Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3922    31503433+   7  HPFS/NTFS
/dev/sda2            3923        6794    23069340   83  Linux
/dev/sda3   *        6795        9666    23069340   bf  Solaris
/dev/sda4            9667       14409    38098147+   f  W95 Ext'd (LBA)
/dev/sda5           14345       14409      522112+  82  Linux swap / Solaris
/dev/sda6            9667       14344    37575972   83  Linux

Partition table entries are not in disk order


```

It's probably worth noting that, even though they're not listed, /dev actually contains sda7 through sda10.  I know that solaris does further partition its own partition...so perhaps I have to mount sda7 through 10 separately?

**Edit**: I tried doing this, with no success:

```

leptogenesis@leptogenesis-laptop:~$ sudo mount -t ufs -oufstype=sunx86 /dev/sda7 /solaris/main
mount: wrong fs type, bad option, bad superblock on /dev/sda7,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

leptogenesis@leptogenesis-laptop:~$ sudo mount -oufstype=sunx86 /dev/sda7 /solaris/main
mount: wrong fs type, bad option, bad superblock on /dev/sda7,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

leptogenesis@leptogenesis-laptop:~$ sudo mount -t ufs -oufstype=sunx86 /dev/sda8 /solaris/main
mount: wrong fs type, bad option, bad superblock on /dev/sda8,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

leptogenesis@leptogenesis-laptop:~$ sudo mount -oufstype=sunx86 /dev/sda8 /solaris/main
mount: you must specify the filesystem type
leptogenesis@leptogenesis-laptop:~$ sudo mount -t ufs -oufstype=sunx86 /dev/sda9 /solaris/main
mount: wrong fs type, bad option, bad superblock on /dev/sda9,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

leptogenesis@leptogenesis-laptop:~$ sudo mount -oufstype=sunx86 /dev/sda9 /solaris/main
/dev/sda9 looks like swapspace - not mounted
mount: you must specify the filesystem type
leptogenesis@leptogenesis-laptop:~$ sudo mount -t ufs -oufstype=sunx86 /dev/sda10 /solaris/main
mount: wrong fs type, bad option, bad superblock on /dev/sda10,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

leptogenesis@leptogenesis-laptop:~$ sudo mount -oufstype=sunx86 /dev/sda10 /solaris/main 
mount: wrong fs type, bad option, bad superblock on /dev/sda10,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

---

### Post by hartz on 2007-05-14
You have not mentioned what exact kernel / Distro you are running.

Firstly, you should have the ufs module loaded.  Check it like this:
```
lsmod|grep ufs
```

If the command does not return the ufs module (driver), you can load it with this command

```
sudo modprobe ufs
```

And then run the lsmod|grep ufs again to check that it is loaded.  This command is generic, it checks any driver module.  A different way to check whether a specific file system is loaded is to run this command:
```
cat /proc/filesystems
```


You also need to check that you have support for BSD disklabels enabled in your kernel.  Try this command:

```
grep DISKLABEL /boot/config-2*
```

If you have upraded your kernel, you will see multiple lines.  In that case, look at the one marked with the same number that you see in this command:

```
uname -r
```

(If there is only one kernel, then you will not see a kernel version number, just some lines telling you whether the BSD_DISKLABEL support is enabled (y), a loadable module (m), or absent.)

Please cut-and-paste the last few lines from dmesg, as well as your syslog file so I can have a look at that too.

Lastly, what Solaris Distro/version did you use to create the UFS file systems?

You may want to consider mounting the partition read-only until you get this working.

---

### Post by leptogenesis on 2007-05-14
> **hartz3 said:**
> You have not mentioned what exact kernel / Distro you are running.

2.6.20-15-generic with Feisty

> **hartz3 said:**
> Firstly, you should have the ufs module loaded.  Check it like this:

```

leptogenesis@leptogenesis-laptop:~$ lsmod|grep ufs
ufs                    72196  0 

```

```

leptogenesis@leptogenesis-laptop:~$ cat /proc/filesystems
nodev   sysfs
nodev   rootfs
nodev   bdev
nodev   proc
nodev   cpuset
nodev   debugfs
nodev   securityfs
nodev   sockfs
nodev   pipefs
nodev   futexfs
nodev   tmpfs
nodev   inotifyfs
nodev   eventpollfs
nodev   devpts
        cramfs
nodev   ramfs
nodev   mqueue
nodev   usbfs
        ext3
nodev   fuse
        fuseblk
nodev   fusectl
        ext2
        ntfs
        ufs
nodev   binfmt_misc
        udf
        iso9660

```

I assume that means I have it.

> **hartz3 said:**
> You also need to check that you have support for BSD disklabels enabled in your kernel.  Try this command:

```

leptogenesis@leptogenesis-laptop:~$ grep DISKLABEL /boot/config-2*
/boot/config-2.6.17-10-generic:CONFIG_BSD_DISKLABEL=y
/boot/config-2.6.17-10-generic:CONFIG_UNIXWARE_DISKLABEL=y
/boot/config-2.6.17-11-generic:CONFIG_BSD_DISKLABEL=y
/boot/config-2.6.17-11-generic:CONFIG_UNIXWARE_DISKLABEL=y
/boot/config-2.6.20-15-generic:CONFIG_BSD_DISKLABEL=y
/boot/config-2.6.20-15-generic:CONFIG_UNIXWARE_DISKLABEL=y

```

of course, uname -r returns 2.6.20-15-generic.

> **hartz3 said:**
> Please cut-and-paste the last few lines from dmesg, as well as your syslog file so I can have a look at that too.

```

leptogenesis@leptogenesis-laptop:~$ dmesg | tail
[   37.196000] [fglrx] free       LFB  = 110088192
[   37.196000] [fglrx] max single LFB  = 110088192
[   37.196000] [fglrx] total      Inv  = 0
[   37.196000] [fglrx] free       Inv  = 0
[   37.196000] [fglrx] max single Inv  = 0
[   37.196000] [fglrx] total      TIM  = 0
[   38.600000] eth0: no IPv6 routers present
[   89.688000] ISO 9660 Extensions: Microsoft Joliet Level 3
[   89.876000] ISO 9660 Extensions: RRIP_1991A
[  645.112000] ufs was compiled with read-only support, can't be mounted as read-write

```

Interesting...can't remember specifying read-write or read-only.

The last line from the Syslog seems to be the only relevant one:

```
May 14 08:29:18 leptogenesis-laptop kernel: [  645.112000] ufs was compiled with read-only support, can't be mounted as read-write
```

It's " sudo mount -t ufs -oufstype=sunx86 /dev/sda3 /solaris" that causes this message to be written...nothing is written if -t isn't specified.

Lastly, what Solaris Distro/version did you use to create the UFS file systems?

A friend of mine essentially pointed me to a download page on sun's website...I'm pretty sure it's Opensolaris 12 build 52.

> **hartz3 said:**
> You may want to consider mounting the partition read-only until you get this working.

That might be a good idea...I hear that the linux ufs write support is a bit experimental anyway.  Where would I specify that option again?

Thanks for all your help.

---

### Post by hartz on 2007-05-14
I agree with your findings. Check your write-support for UFS with this command:

```
grep UFS /boot/config-2.6.20-15-generic
```

To mount a file-system as readonly, use the -o ro flag.  It is a filesystem-specific flag so it gets passed to the helper-mount command by the mount command.

options after -o is a comma-separated list, so you could try this command:

```
sudo mount -t ufs -o ro,ufstype=sunx86 /dev/sda3 /solaris
```

Note that I don't know for a fact that you are specifying the correct ufstype (sunx86).  I assume that you are.

---

### Post by leptogenesis on 2007-05-14
> **hartz3 said:**
> I agree with your findings. Check your write-support for UFS with this command:

```

leptogenesis@leptogenesis-laptop:~$ grep UFS /boot/config-2.6.20-15-generic
CONFIG_UFS_FS=m
# CONFIG_UFS_FS_WRITE is not set
# CONFIG_UFS_DEBUG is not set

```

> **hartz3 said:**
> To mount a file-system as readonly, use the -o ro flag.  It is a filesystem-specific flag so it gets passed to the helper-mount command by the mount command.

```

leptogenesis@leptogenesis-laptop:~$ sudo mount -t ufs -o ro,ufstype=sunx86 /dev/sda3 /solaris
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

leptogenesis@leptogenesis-laptop:~$ dmesg|tail
[   36.044000] [fglrx] free       LFB  = 110088192
[   36.044000] [fglrx] max single LFB  = 110088192
[   36.044000] [fglrx] total      Inv  = 0
[   36.044000] [fglrx] free       Inv  = 0
[   36.044000] [fglrx] max single Inv  = 0
[   36.044000] [fglrx] total      TIM  = 0
[   39.276000] eth0: no IPv6 routers present
[   57.992000] ISO 9660 Extensions: Microsoft Joliet Level 3
[   58.124000] ISO 9660 Extensions: RRIP_1991A
[  360.392000] ufs_read_super: bad magic number

```

umm...bad magic number?

> **hartz3 said:**
> Note that I don't know for a fact that you are specifying the correct ufstype (sunx86).  I assume that you are.

I have no idea...I'm just doing what the faqs.org page said.  Not sure how I would go about finding it out, either...

---

### Post by hartz on 2007-05-15
Could you log in to the Solaris system and run these commands, and show the output

```
prtvtoc /dev/dsk/c1t0d0s0
```

replace c1t0d0s0 with whatever you see your root is mounted on, eg by looking at the output from "df"

```
ls -l /dev/dsk/
cat /etc/vfstab
cat /etc/release
mount -p
```

Retry the mount command with the ro flag, but using different disk devices, eg /dev/sda7, /dev/sda8, etc.

My brain is a bit frozen at the moment, not sure how to translate /dev/sda7 to start/end sectors as it doesn't show up in fdisk -l....  Probably some GUI or fdisk utility can show that....

You can also try some of the other forums too - this problem is not Ubuntu specific, and it is a good idea to get as many people as possible to look at your problem.  But when you do find a solution from someone else please post it here as I am quite curious about this, I've never had a Linux/Solaris dual-boot computer!!!

---

### Post by ddunham on 2007-05-17
> **hartz3 said:**
> Could you log in to the Solaris system and run these commands, and show the output
My brain is a bit frozen at the moment, not sure how to translate /dev/sda7 to start/end sectors as it doesn't show up in fdisk -l....  Probably some GUI or fdisk utility can show that....

The guide link that has been posted suggests that this translation should appear in the boot output.

> During boot up, you should get something similar to:

```
  hda: [PTBL] [523/255/63] hda1 hda2 < hda5 hda6 hda7 hda8 > hda3 <Polaris: [s0]
  hda9 [s1] hda10 [s2] hda11 [s3] hda12 [s6] hda13 [s7] hda14 >

```
Meaning (in this case): partition 3 (hda3) is a Solaris partition with 6 slices (s0,s1,s2,s3,s6,s7). They are mapped to Linux devices hda9 to hda14.


I'm assuming that if this doesn't appear in the boot output that something is not working properly.

-- 
Darren

---

### Post by leptogenesis on 2007-05-17
i guess this is why you shouldn't start how-to's in the middle.  Turns out I was making two mistakes - I hadn't made a new kernel like the guide says (it turns out you can do read-only with a current kernel, unmodified), and I was indeed trying to mount the wrong partitions.  It's all working now...although it is read-only (I really don't care...I think it would take too much effort to compile a new kernel just for read/write support).  Thanks for all your help, everyone.

---

