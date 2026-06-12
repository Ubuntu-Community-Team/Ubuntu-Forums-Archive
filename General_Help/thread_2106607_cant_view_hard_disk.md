---
title: "cant view hard disk"
date: 2013-01-19
forum: General Help
---

### Post by Agent26 on 2013-01-19
Hi there all,
I am having trouble veiwing my other hard drive on ide2, it's the primary.
The weird thing is my system infomation program shows the drive is there but Xububtu does not display it in my home folder?
Ive read around and im stuck now.
It's been formated in NTSC format and has vista 32 bit.

I know windows is unable to veiw Xubuntu but know linux can get at the other drive somehow.
Thank you

:D

---

### Post by sudodus on 2013-01-19
Try with some terminal window commands and let us know the results

```
sudo fdisk -lu
```
```
sudo blkid
```
```
df
```
```
cat /etc/fstab
```

This will make it easier to give advice.

---

### Post by Agent26 on 2013-01-19
Heres the results from the first code...

dave@Systemax-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8c8fbd1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   321667071   160832512    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005adfe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   306569215   153283584   83  Linux
/dev/sdb2       306571262   312580095     3004417    5  Extended
/dev/sdb5       306571264   312580095     3004416   82  Linux swap / Solaris
dave@Systemax-desktop:~$

---

### Post by Agent26 on 2013-01-19
and the second....

dave@Systemax-desktop:~$ sudo blkid
/dev/sda1: UUID="AA8CC7D48CC79969" TYPE="ntfs" 
/dev/sdb1: UUID="fd3809a0-92a2-47a8-8d76-32e8c9c631b5" TYPE="ext4" 
/dev/sdb5: UUID="f0813497-5b21-4bc7-9f1a-17ce1d0420c3" TYPE="swap" 
dave@Systemax-desktop:~$ 


third...

dave@Systemax-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1            150877404  20986408 122226820  15% /
none                   1544236       352   1543884   1% /dev
none                   1548476      1128   1547348   1% /dev/shm
none                   1548476        84   1548392   1% /var/run
none                   1548476         0   1548476   0% /var/lock
none                   1548476         0   1548476   0% /lib/init/rw
dave@Systemax-desktop:~$

---

### Post by Agent26 on 2013-01-19
and the fourth...

dave@Systemax-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fd3809a0-92a2-47a8-8d76-32e8c9c631b5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f0813497-5b21-4bc7-9f1a-17ce1d0420c3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/fd1        /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0
dave@Systemax-desktop:~$

---

### Post by Laurent B on 2013-01-19
I guess you meant NTFS...

Basically everything is explained here on how to mount Windows partitions:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Honestly I don't like mounting NTFS filesystems read/write as there are always issues related to Windows credentials, locale etc...
I would recommend to mount your NTFS partition read only and setup a small FAT32 partition for data exchanges between the 2 systems.

---

### Post by sudodus on 2013-01-19
> **Laurent B said:**
> I guess you meant NTFS...

Basically everything is explained here on how to mount Windows partitions:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Honestly I don't like mounting NTFS filesystems read/write as there are always issues related to Windows credentials, locale etc...
I would recommend to mount your NTFS partition read only and setup a small FAT32 partition for data exchanges between the 2 systems.
+1
Another alternative is to use a separate NTFS ***data*** partition.

A third alternative is to install a tool into Windows to read ext file systems:
[[COLOR="Red"]http://sourceforge.net/projects/ext2fsd/[/COLOR]]("http://sourceforge.net/projects/ext2fsd/")
--
I see from the output of those commands, that your computer sees not only the drive, but also the NTFS partition with Windows. But there are no labels.

In the file browser (I guess you use Thunar), there is usually a pane at the left side, where you can see available partitions (including your Windows partition). If you click on it, it should be mounted (and visible in the file browser as well as with the command df).

Things will be easier if you add ***labels*** to your partitions. Use easy-to-understand labels: for example ***windows*** for the windows partition.

You can edit partitions with the command line tool tune2fs,
for example
```
sudo tune2fs -L windows /dev/sda1
```

---

### Post by Agent26 on 2013-01-19
NTFS, oh yes thats the one, I beleive NTSC was the American games/video format in the snez days.

---

### Post by Agent26 on 2013-01-19
Thanks for that to both, all taken on board,
Yep, i am using the Thunar file manager but my drive does not show in the left hand pane.
I would like to have it mount as read only as I only want to veiw some videos and access the music folder.

---

### Post by Agent26 on 2013-01-19
Thanks again for the help, im heading off now but will spend some time with this tommorow afternoon and I will have time to read that article fully.
Hopefully I can report what I did and how it went then mark solved.

---

### Post by sudodus on 2013-01-19
To make the mounting permanent, add the following line into
/etc/fstab with some editor, for example nano

```
sudo nano /etc/fstab
```

```
UUID=AA8CC7D48CC79969  /mnt/windows  ntfs  defaults,ro  0  0
```

Before rebooting, you must also create the directory (only once) ```
sudo mkdir /mnt/windows
```

---

### Post by Agent26 on 2013-01-20
Hi there all, thats me all sorted now.
By going into gedit and selecting open this will show up and mount the hard disk on /dev/sda1.

Thats fine but I wanted it to automaticly mount so heres what I did...

open /etc/fstab in a text editor with root privileges by typing gksudo gedit /etc/fstab

then added the line to the bottom of gedit and changed the UUID bit to my number found from the command sudo blkid.

checked locale language by typing locale-a and confirmed to change the language from US to UK

Saved, rebooted and thats that, now I have a windows drive that mounts on boot up, and is now visible in my thunar pane home folder.:D:D
Thank you for the help.

---

