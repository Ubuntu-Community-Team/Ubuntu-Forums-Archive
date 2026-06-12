---
title: "cannot mount SD card as RW"
date: 2013-05-26
forum: General Help
---

### Post by Synoc on 2013-05-26
I followed this thread
[http://ubuntuforums.org/showthread.php?t=1985599](http://ubuntuforums.org/showthread.php?t=1985599)

it doesn't work. I made the /media/temp folder (where i want to mount the drive) owned by me. As soon as I mount the drive it changes the owner back to root. if I set the UID=1000 keeps the folder in my name, however it still mounts the drive as read only.

any advice?

incidently I was able to copy the files as root, but i should not have to

---

### Post by Synoc on 2013-05-30
bump

---

### Post by Bashing-om on 2013-05-30
[COLOR=#000000]Synoc; Hi !

Give us somethings to work with.
```

lsb_release -a
uname -r
sudo fdisk -lu
cat /etc/fstab
```
In addition what machine, is it a desk top, laptop or else ?
[/COLOR][INDENT][COLOR=#000000]NTFS access, 'most set in stone on mounting
[/COLOR][/INDENT]
[INDENT=2][COLOR=#000000]
recon that will get the ball rolling

[/COLOR][/INDENT]

---

### Post by Synoc on 2013-06-01
Lsb_release -a
```

LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:  Ubuntu
Description:      Ubuntu 12.04.2 LTS
Release:            12.04
Codename:       precise

```
 
Uname –r
```

3.2.0-45-generic

```
 
Sudo fdisk –lu
```

/dev/sda1            2048    24578047    12288000   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *    24578048   268771327   122096640    7  HPFS/NTFS/exFAT
/dev/sda3       268773374   976771071   353998849    f  W95 Ext'd (LBA)
/dev/sda5       268773376   771971071   251598848    7  HPFS/NTFS/exFAT
/dev/sda6       957243392   976771071     9763840   82  Linux swap / Solaris
/dev/sda7       771973120   957233151    92630016   83  Linux


Partition table entries are not in disk order


Disk /dev/mmcblk0: 32.0 GB, 32018268160 bytes
170 heads, 53 sectors/track, 6940 cylinders, total 62535680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1            8192    62535679    31263744    c  W95 FAT32 (LBA)

```
 
Cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=5c659798-b13e-415e-a439-819ba1445369 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7ebc15c6-1741-48c5-a6c6-d5bc51c7aeee none            swap    sw  

```
 

It is a an ASUS G72X laptop. and of course when attempting to duplicate the problem to get the same result, I an unable to replicate despite using the same card and the same circumstances. so I don't know if this information even useful.

---

### Post by Bashing-om on 2013-06-01
[COLOR=#000000]Synoc; Hi !

The device in question is 
[/COLOR]> [COLOR=#000000][FONT=Ubuntu Mono]Disk /dev/mmcblk0: 32.0 GB, 32018268160 bytes[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]?[/FONT][/COLOR]?

As it is Windows's formatting... as a guess  ...that device has in the past NOT been safely removed and thus has a "file lock" on it.

I suggest ya take it to a windows machine and there "safely remove" the device; then try it in ubuntu again.

Let us know how this goes.[INDENT=2]
just try'n to help

[/INDENT]
[INDENT=2]

[/INDENT]

---

### Post by Synoc on 2013-06-03
it's only ever been in my android tablet. Attached it to a Linux system to load songs and such on it, but kept the original formatting. But like I said it is working now... though I never was able to add anything do it until I put it back into my tablet and took it out after making a playlist.

---

### Post by Bashing-om on 2013-06-04
[COLOR=#000000]Synoc; Hey.

My last post I may have been out in left field and jumped to a conclusion. We are looking at access rights on the  device with fat32 formatting.

Linux file access/write manipulations do not correlate to these types of formatting. These rights are set when the device is mounted and can not be (re-)set external to the mounting's access setting.

I am having a bit of a time finding the documentation as I am tired and not thinking to well presently. I will continue in my AM and get back to ya. 
[/COLOR][INDENT=2][COLOR=#000000]best regards

[/COLOR][/INDENT]

---

### Post by Bashing-om on 2013-06-04
[COLOR=#000000]Synoc; Hey.

Fresh mind, and here is the excellent documentation on mounting...your attention is invited to the section on usb devices in general and VFAT in particular; Great explanation of the process and how to set the options.
[/COLOR][http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
and then there is:
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
[COLOR=#000000]that has additional links for further information.
[/COLOR][INDENT][COLOR=#000000]
let me know how you progress, it is my reward to know I help
[/COLOR][/INDENT]
[INDENT=2][COLOR=#000000]
[/COLOR][/INDENT]
[INDENT=3][COLOR=#000000]best regards

[/COLOR][/INDENT]

---

### Post by Synoc on 2013-06-04
next time I have that problem I will. as of right now, however it is working fine. so I can't test anything :( what would cause the same MicroSD card to sometime mount RO and something RW on the same computer? I unmount it properly every time.

---

### Post by Bashing-om on 2013-06-04
[COLOR=#000000]Synoc; 

In a situation as you describe, what pops to mind is: --the kernel detects "some" kind of a problem, and to protect that file system from any additional damage, it will only mount that file system in "read only" mode. Then one generally goes and reads what the system has logged, say (/var/log/syslog, /var/log/kern.log or maybe /var/log/Xorg.0.log) and looking into the booting process to determine a possible cause.

[/COLOR][INDENT][COLOR=#000000]
complex system, lots going on
 [/COLOR][/INDENT]

---

### Post by ionplay on 2013-08-20
why would there be something that windows can do that linux(ubuntu) can not?
if its a hardware file lock - then move the switch
if its a software file lock - then there is a way to flip it
no?



> **Bashing-om said:**
> [COLOR=#000000]Synoc; Hi !

The device in question is 
[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]?[/FONT][/COLOR]?

As it is Windows's formatting... as a guess  ...that device has in the past NOT been safely removed and thus has a "file lock" on it.

I suggest ya take it to a windows machine and there "safely remove" the device; then try it in ubuntu again.

Let us know how this goes.[INDENT=2]
just try'n to help

[/INDENT]
[INDENT=2]

[/INDENT]


---

