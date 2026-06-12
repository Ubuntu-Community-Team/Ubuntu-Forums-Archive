---
title: "How To View Second Hard Drive"
date: 2014-09-06
forum: General Help
---

### Post by bigpappajohn1984 on 2014-09-06
(This is Lubuntu) --- 
I have 2 internal hard drives, one 80GB that Lubuntu is installed on, and a separate 500GB (or somewhere close to that).  I can "see" my second hard drive when I click on disks, but how do i actually navigate to view the files that are stored on that drive?

---

### Post by EuclideanCoffee on 2014-09-06
Have you tried any of this advice?

[http://ubuntuforums.org/showthread.php?t=2164994](http://ubuntuforums.org/showthread.php?t=2164994)

---

### Post by bigpappajohn1984 on 2014-09-06
> **ruze said:**
> Have you tried any of this advice?

[http://ubuntuforums.org/showthread.php?t=2164994](http://ubuntuforums.org/showthread.php?t=2164994)

I ran the commands listed --- sorry i thought I had posted them in my initial

fdisk
```

jo@jo:~$ sudo fdisk -lu
[sudo] password for jo: 


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00042df5


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   156301311    77899777    5  Extended
/dev/sda5          501760   156301311    77899776   8e  Linux LVM


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/sdb doesn't contain a valid partition table


Disk /dev/mapper/lubuntu--vg-root: 78.2 GB, 78223769600 bytes
255 heads, 63 sectors/track, 9510 cylinders, total 152780800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/lubuntu--vg-root doesn't contain a valid partition table


Disk /dev/mapper/lubuntu--vg-swap_1: 1543 MB, 1543503872 bytes
255 heads, 63 sectors/track, 187 cylinders, total 3014656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/lubuntu--vg-swap_1 doesn't contain a valid partition table


Disk /dev/sdg: 259 MB, 259522560 bytes
65 heads, 32 sectors/track, 243 cylinders, total 506880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc195b91f


   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1              32      506879      253424    4  FAT16 <32M

```

Fstab
```

jo@jo~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/lubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=c8ea72d4-d00f-4c95-a807-3a7722fc7f0b /boot           ext2    defaults        0       2
/dev/mapper/lubuntu--vg-swap_1 none            swap    sw              0       0
/dev/sr0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

lsblk
```

jo@jo:~$ lsblk -f
NAME                          FSTYPE LABEL MOUNTPOINT
sda                                        
&#9500;&#9472;sda1                                     /boot
&#9500;&#9472;sda2                                     
&#9492;&#9472;sda5                                     
  &#9500;&#9472;lubuntu--vg-root (dm-0)                /
  &#9492;&#9472;lubuntu--vg-swap_1 (dm-1)              [SWAP]
sdb                                        
sdg                                        
&#9492;&#9472;sdg1                                     /media/jo/LEXAR MEDIA
zram0                                      [SWAP]

```

MOUNT
```

jo@jo:~$ mount
/dev/mapper/lubuntu--vg-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda1 on /boot type ext2 (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=jo15765)
/dev/sdg1 on /media/jo15765/LEXAR MEDIA type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)

```

PARTED
```

jo@jo:~$ sudo parted /dev/sda unit s print
[sudo] password for jo: 
Model: ATA WDC WD800BD-22MR (scsi)
Disk /dev/sda: 156301488s
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start    End         Size        Type      File system  Flags
 1      2048s    499711s     497664s     primary   ext2         boot
 2      501758s  156301311s  155799554s  extended
 5      501760s  156301311s  155799552s  logical                lvm

```

Parted -l
```

jo@jo:~$ sudo parted -l
[sudo] password for jo: 
Model: ATA WDC WD800BD-22MR (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   80.0GB  79.8GB  extended
 5      257MB   80.0GB  79.8GB  logical                lvm




Error: /dev/sdb: unrecognised disk label                                  


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/lubuntu--vg-swap_1: 1544MB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End     Size    File system     Flags
 1      0.00B  1544MB  1544MB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/lubuntu--vg-root: 78.2GB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End     Size    File system  Flags
 1      0.00B  78.2GB  78.2GB  ext4




Model: LEXAR JUMPDRIVE SECURE (scsi)
Disk /dev/sdg: 260MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type     File system  Flags
 1      16.4kB  260MB  260MB  primary  fat16




Error: /dev/zram0: unrecognised disk label  

```

---

### Post by deadflowr on 2014-09-06
Sometimes it is easier to understand what is what with a simple picture.
could you possibly take a screenshot of the disks program as you see it when looking at the disk in question.

(click on the prntscrn keyboard button and a screenashot should be saved to either you home folder or Pictures folder.
Then to post it, in a reply go to the button  Go Advanced and click on the paperclip icon which will be called attachments. From there upload the image click Ok and then post reply.)

---

### Post by bigpappajohn1984 on 2014-09-07
[ATTACH=CONFIG]256235[/ATTACH]

Attached is a screenshot of what I see

---

### Post by Dennis N on 2014-09-07
> I can "see" my second hard drive when I click on disks, but how do i actually navigate to view the files that are stored on that drive?

You don't need the Disks utility -

I have two hard drives in this computer, and running Lubuntu 14.04 - Every partition on both drives is accessible from the file manager "Places" in the side pane. Just single click and it will mount (if unmounted) and open the partition in a window. In addition, mounted ones show up on the Desktop if you have "Show Connected Volumes on Desktop" checked in Desktop Preferences.

---

### Post by deadflowr on 2014-09-07
> **bigpappajohn1984 said:**
> [ATTACH=CONFIG]256235[/ATTACH]

Attached is a screenshot of what I see

I can see the 80GB hard drive, which we know is good to go, but not the 500GB hard drive, which I thought was the problem child.
I thought you were going to click on that one and post the image of its layout scheme.

---

### Post by bigpappajohn1984 on 2014-09-07
My mistake there, thought I posted the other image[ATTACH=CONFIG]256241[/ATTACH]

---

### Post by ajgreeny on 2014-09-07
No partitions are shown on that drive. Have you made any partitions or is it still just a raw empty device?  Is it encrypted, by any chance?

---

### Post by deadflowr on 2014-09-07
Was the drive ever formatted and partitioned?

edit: slightly ninja'd, and +1 to post #9.

---

### Post by bigpappajohn1984 on 2014-09-07
> **deadflowr said:**
> Was the drive ever formatted and partitioned?

edit: slightly ninja'd, and +1 to post #9.

It used to be in a Windows machine --- to my knowledge was never formatted (I thought it still had data on it) -- no big loss if it was erased tho.

[QUOTE=ajgreeny]
No partitions are shown on that drive. Have you made any partitions or is it still just a raw empty device? Is it encrypted, by any chance?
[/QUOTE]

Same answer.  Was not encrypted.

---

### Post by nerdtron on 2014-09-07
If you would just like to use the 500 GB dirve you should format it again. Just install install gparted, and format the drive as new (I'm not using disk utility so I'm not sure if it can format drives too.)
Either way, if data loss is no big deal, formatting the drive either ext4 or ntfs should make it usable again.

---

### Post by bigpappajohn1984 on 2014-09-07
> **nerdtron said:**
> If you would just like to use the 500 GB dirve and format it again, just install install gparted, and format the drive as new (not using disk utility so I'm not sure if it can format drives too.)
Either way, if data loss is no big deal, formatting the drive either ext4 of ntfs should make it usable again.

VERY new to Lubuntu - would this be a good tutorial to follow to do these steps?

[http://www.wikihow.com/Format-a-Hard-Drive-Using-Ubuntu](http://www.wikihow.com/Format-a-Hard-Drive-Using-Ubuntu)

---

### Post by nerdtron on 2014-09-07
Yes that seems to be updated. Just choose the correct drive **(on the upper right corner)** when formatting. And I believe even if you accidentally choose the 80 GB drive and format it, you won't be allowed to do so since it is used by the system. So go ahead.

---

### Post by deadflowr on 2014-09-07
Normally i would say to use gparted to create new partitions on the disk, but as you are using lvm I don't know how that applies to it.
Or if it applies at all.
Some links though, for a starting point, I think
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)


Edit: I was staring at the screen for about 8 minutes and a whole conversation took place.

---

### Post by nerdtron on 2014-09-07
He's using LVM on the main 80GB drive. If he wants to just use the drive as a normal partition then it is straightforward.

---

### Post by Dennis N on 2014-09-07
> VERY new to Lubuntu - would this be a good tutorial to follow to do these steps?

That guide shows you how to format one **partition** on the drive. Not the entire drive. So it is a bit misleading. The first pictire points to sda8, but the next two indicate he is formatting sda2 (see pending operations in bottom window). You probably want to start from scratch and make a new partition table, then add some partitions to it. gparted is a good tool for all that.

Edit: If the LVM on the other drive affects what is done on the 500, I'm not sure how that affects the basic suggestion here. I have never had or used LVM. Better find out first before proceeding.

---

### Post by bigpappajohn1984 on 2014-09-07
> **Dennis N said:**
> That guide shows you how to format one **partition** on the drive. Not the entire drive. So it is a bit misleading. The first pictire points to sda8, but the next two indicate he is formatting sda2 (see pending operations in bottom window). You probably want to start from scratch and make a new partition table, then add some partitions to it. gparted is a good tool for all that.

Edit: If the LVM on the other drive affects what is done on the 500, I'm not sure how that affects the basic suggestion here. I have never had or used LVM. Better find out first before proceeding.

I know what LVM stands for but not sure what I would need it for on that drive.... I just do not need to loose the data that is currently on the 80GB drive.

---

### Post by bigpappajohn1984 on 2014-09-07
> **nerdtron said:**
> Yes that seems to be updated. Just choose the correct drive **(on the upper right corner)** when formatting. And I believe even if you accidentally choose the 80 GB drive and format it, you won't be allowed to do so since it is used by the system. So go ahead.

Perfect, thank you for the assistance!

---

