---
title: "Windows partition won't show anymore"
date: 2007-12-11
forum: General Help
---

### Post by WarMonkey on 2007-12-11
I attempted an installation of VandalSniper  (Wikipedia tool I downloaded from sourceforge), all of its dependencies, and ran a synaptec update of my computer; and now I cannot access my windows partition from Ubuntu like I once did before. I checked the fstab file and checked to see if ntfs3g was installed, they were. I can also boot Windows perfectly.

Another important thing is that when I first installed Ubuntu, the Windows partition would show under computer:/// but it wouldn't be mounted (until I installed ntfs3g and modified /etc/fstab). But now, Ubuntu doesn't even detect that its there!

Is there a way to fix this?

---

### Post by scott_g on 2007-12-12
Ok, I'm assuming you have both your Ubuntu parition and Windows partition on the same physical hard drive...  If so, can you post the output of the following commands:

If you have an IDE drive:

```

sudo fdisk -l /dev/hda

```

If you have a SATA drive:

```

sudo fdisk -l /dev/sda

```

The path's: /dev/hda and /dev/sda are typical paths for the hard drives...  You can look up what the actual path is in the GNOME system manager under the HD's section.  The fdisk -l lists the partitions on the drive...

Also, can you post the relevant parts of your fstab file?

Thanks,
Scott

---

### Post by WarMonkey on 2007-12-12
Here is my terminal output:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x695c22f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6709    53890011    7  HPFS/NTFS
/dev/sda2            6710        9698    24009142+  83  Linux
/dev/sda3            9699        9729      249007+   f  W95 Ext'd (LBA)
/dev/sda5            9699        9729      248976   82  Linux swap / Solaris


... and my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=a862f4a0-bb78-4fb2-8b3e-61acfcfcd594 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e334b698-0546-4a17-b61b-ada134960ce5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0

---

### Post by kpkeerthi on 2007-12-12
What happens when you type
```

sudo mount -a

```
in terminal.

I find a few users reporting NTFS partition not mounting due to "unsafe" removal or partition in use error. If the above command reports similar error, boot into windows and ensure clean shutdown and try again.

---

### Post by WarMonkey on 2007-12-12
yitzchakranjbar@ubuntu:~$ sudo mount -a
[sudo] password for yitzchak:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/windows ntfs-3g defaults,force 0 0

---

