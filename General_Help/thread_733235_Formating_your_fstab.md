---
title: "Formating your fstab"
date: 2008-03-23
forum: General Help
---

### Post by EMCGFX on 2008-03-23
By default /etc/fstab is ugly :) No offense! :lolflag:

Simply replacing spaces with tabs and adding some
comments helps ;)

Playing with your fstab ;) Note I've remove some info.
<removed!> or <drive_name> replace with your own.

Here is my fstab, if you are interested ;)
```
#****************************#
#* /etc/fstab
#* fstab: File System Table
#****************************#

#*****************************#
#* mkdir /<drive_name>
#* mkdir /<drive_name>
#* chown -R username:username /<drive_name>
#* chmod -R 755 /<drive_name>
#* mount -a
#*****************************#

## <file system>	<mount point>	<type>	<options>	<dump>	<pass>

## Process File System
proc	/proc	proc	defaults	0	0

## /dev/sda1 - Root
UUID=<removed!>	/	ext3	defaults,errors=remount-ro	0	1

## /dev/sda5 - Swap
UUID=<removed!>	none	swap	sw	0	0

## /dev/sdc1 - Hard Drive
/dev/sdc1	/<drive_name>	ext3	defaults	0	0

## /dev/sdb1 - Hard Drive
/dev/sdb1	/<drive_name>	ext3	defaults	0	0

#*******************#
#* Removable Media *#
#*******************#

## DVD-/+R/RW DL
/dev/scd0	/media/cdrom0	udf,iso9660 user,noauto,exec	0	0

## 1.4mb Floppy Drive
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec	0	0

```

---

### Post by keratos on 2008-03-23
why?


I like mine to be messy



Who cares.



```
daz@desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc             /proc                     proc   defaults      0       0
/dev/hdc1    /                             xfs      defaults      0       1
/dev/hdc9    /home                  xfs      noatime      0       2
/dev/hdc8    /tmp                      ext2    noatime      0       2
/dev/hdc5    /usr                       xfs      noatime      0       2
/dev/hdc6    /var                        ext2    noatime     0       2
/dev/hdc7    none                     swap sw               0       0
/dev/hdd      /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0   auto    rw,user,noauto  0       0

```

---

### Post by ad_267 on 2008-03-23
Why does mine have all this UUID stuff instead of /dev/sda1 etc?

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=82729ea2-00a7-4925-8372-d78406dda1b8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=0848D41548D3FEFE /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=24688D10688CE242 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=9ec61421-ec7b-4836-a0ca-95159f4ac3cc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

---

### Post by K.Mandla on 2008-03-23
Moved to General Help.
> **ad_267 said:**
> Why does mine have all this UUID stuff instead of /dev/sda1 etc? ... 
If I remember right, it's so you have the same drive assignments when you boot into a live system or to another distro. Otherwise drives get assigned different names, and that could be confusing or cause errors.

Or something like that. :roll:

---

### Post by keratos on 2008-03-24
> **K.Mandla said:**
> Moved to General Help.

If I remember right, it's so you have the same drive assignments when you boot into a live system or to another distro. Otherwise drives get assigned different names, and that could be confusing or cause errors.

Or something like that. :roll:

YEP.

To clarify, different kernel versions embrace different nomenclatures for disk names. This is because some use the older "IDE" interface (hd?1, hd?2 etc) and others the newer "libata" interface (sd?1, sd?etc) where ?  = controler interface as in 'a' for IDE-0 master HDD, 'b' for IDE-0 slave, 'c' for IDE-1 master, 'd' for IDE-1 slave.

This is a bit confusing because SCSI disks also received an sd? assignment under the old IDE interface.

With libata, ALL drives receive the sd? assignment.

Some of the libata interface has been found to be buggy so some distros, having moved to newer kernels, then moved back again to old kernels or patched the newer kernel to fix libata.

The reason different distros name HDDs differently is becuase:
1. They are using a kernel with IDE interface
2. They are using a kernel with libata interface

---

### Post by dcstar on 2008-03-24
> **K.Mandla said:**
> Moved to General Help.

If I remember right, it's so you have the same drive assignments when you boot into a live system or to another distro. Otherwise drives get assigned different names, and that could be confusing or cause errors.

Or something like that. :roll:

UUID mounts make the partition mount independent of the physical connection that the kernel detects.

It means you can change the internal/external connections for these drives and they will still mount to the same place.

It is irrelevant for booting "other distros" etc. because they all use their own fstab files.

For removable USB drives, you can create partition labels and then they will be mounted using those labels, rather than arbitrary mount points.

---

### Post by EMCGFX on 2008-03-24
@ad_267, I care ;-)

---

### Post by ad_267 on 2008-03-24
Thanks for explaining that,

Sorry for hijacking the thread, I looked at my fstab to compare and was just curious to find out why it was so different :)

---

### Post by EMCGFX on 2008-03-24
@ ad_267, LOL no problem.

---

### Post by keratos on 2008-03-24
> **EMCGFX said:**
> @ad_267, I care ;-)

you need to get out more buddy ;-) ;-)

---

### Post by lukem on 2008-03-24
Can you explain how to create a partition label and is using the UUID in fstab better?

Thanks

---

### Post by EMCGFX on 2008-03-24
> **keratos said:**
> you need to get out more buddy ;-) ;-)

Yeah, :lolflag:

---

### Post by EMCGFX on 2008-03-24
@lukem, Command to find UUID is > blkid

If you need help with fstab this is a good start:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by keratos on 2008-03-25
> **EMCGFX said:**
> @lukem, Command to find UUID is > blkid

If you need help with fstab this is a good start:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Do you know pal, I have been using linux since the good olde days since RH1 and a [very] difficult text (not even ncurses) install, and...

never knew about that command and used to navigate the /proc or /sys fs

just goes to show , one is never too old to learn anything ... but I wouldnt go as far as to say I'm an "old dawg"

---

### Post by EMCGFX on 2008-03-27
Yeah, glad it helped you ;-) I found that command my self a week ago.

---

