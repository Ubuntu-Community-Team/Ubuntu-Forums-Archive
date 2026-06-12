---
title: "Expand RAID5 Volume - GPT"
date: 2022-01-11
forum: General Help
---

### Post by penguinpages2 on 2022-01-11
I built out a NAS and trying to test through situations of Day2 events and tasks.

One of those is to expand array with new disk. 


# Disk layout
 ```

root@pandora:~# lsblk
NAME        MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda           8:0    0   1.8T  0 disk
`-md0         9:0    0   5.5T  0 raid5
  `-md0p1   259:0    0   3.2T  0 part  /media/md0
sdb           8:16   0   1.8T  0 disk
`-md0         9:0    0   5.5T  0 raid5
  `-md0p1   259:0    0   3.2T  0 part  /media/md0
sdc           8:32   0   1.8T  0 disk
`-md0         9:0    0   5.5T  0 raid5
  `-md0p1   259:0    0   3.2T  0 part  /media/md0
sdd           8:48   0   1.8T  0 disk
`-md0         9:0    0   5.5T  0 raid5
  `-md0p1   259:0    0   3.2T  0 part  /media/md0

```



##Initial Array create ##
 ```

mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda /dev/sdb /dev/sdc
parted /dev/md0  -> gpt 3.5TB partition (leaving a few GB for breathing room if out of space happens)
mkfs.ext4 /dev/md0p1 -L md0
//-->
</script>

```

## A few weeks later I install new drive ### All drives same exact size / manufacture to KISS
# Ex:  Add new /dev/sde drive
 ```

root@pandora:/media/md0/camera# df -h |grep md0
/dev/md0p1      3.2T  1.9T  1.1T  64% /media/md0
root@pandora:/media/md0/camera# mdadm --add /dev/md0 /dev/sde
mdadm: added /dev/sde
root@pandora:/media/md0/camera# mdadm --grow --raid-devices=4 /dev/md0
root@pandora:/media/md0/camera# cat /proc/mdstat
Personalities : [raid1] [raid6] [raid5] [raid4]
md0 : active raid5 sde[4] sdc[3] sda[0] sdb[1]
      3906764800 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      [>....................]  reshape =  0.1% (3172876/1953382400) finish=2407.8min speed=13498K/sec
      bitmap: 0/15 pages [0KB], 65536KB chunk
 
unused devices: <none>
 
root@pandora:/media/md0/camera#

<two days later it finished>


Now I need to expand the partition and then file system.
root@pandora:/# umount -l /media/md0
root@pandora:~# resize2fs /dev/md0p1
resize2fs 1.44.5 (15-Dec-2018)
resize2fs: Device or resource busy while trying to open /dev/md0p1
[COLOR=#ff0000]Couldn't find valid filesystem superblock.[/COLOR]


root@pandora:~# parted /dev/md0
GNU Parted 3.2
Using /dev/md0
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p
Warning: Not all of the space available to /dev/md0 appears to be used, you can fix the GPT to use all of the space (an extra 3906764800 blocks) or continue with the current setting?
Fix/Ignore? [COLOR=#ff0000]fix[/COLOR]
Model: Linux Software RAID Array (md)
Disk /dev/md0: 6001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  3500GB  3500GB  ext4         primary
(parted) resizepart 1
End?  [3500GB]? 5800GB
(parted)

alignment type(min/opt)  [optimal]/minimal? optimal
Partition number? 1
1 not aligned

(parted) quit

root@pandora:~# mount -a
root@pandora:~# df -h |grep md0
/dev/md0p1      3.2T  2.0T  1.1T  65% /media/md0

root@pandora:~# fdisk -l |grep md0
Disk /dev/md0:[COLOR=#00ff00] 5.5 TiB[/COLOR], 6000790732800 bytes, 11720294400 sectors
/dev/md0p1  2048 11328125000 11328122953  5.3T Linux filesystem
root@pandora:~#



root@pandora:~# umount /media/md0
umount: /media/md0: target is busy.
root@pandora:~# umount -l /media/md0
root@pandora:~# umount /media/md0
umount: /media/md0: not mounted.
root@pandora:~#
root@pandora:~#
root@pandora:~#
root@pandora:~# resize2fs /dev/md0p1
resize2fs 1.44.5 (15-Dec-2018)
resize2fs: [COLOR=#ff0000]Device or resource busy while trying to open /dev/md0p1[/COLOR]
Couldn't find valid filesystem superblock.
root@pandora:~#


```





Not sure what I am missing.  Seems like this should just be simple to expand file system now that the partition is expanded.
Also not happy about alignment error.

---

### Post by penguinpages2 on 2022-01-11
Update:

Even though the file system unmounted, figured .. maybe there was some weird lock going on.   So I remarked out entry in /etc/fstab and reboot
[COLOR=#000000]```
[/COLOR]
[COLOR=#000000]<script type="text/javascript">[/COLOR]
[COLOR=#000000]<!--[/COLOR]
root@pandora:~# cat /etc/fstab |grep md
#LABEL=md0      /media/md0  ext4 defaults 0 0
<reboot>

root@pandora:~# resize2fs /dev/md0p1
resize2fs 1.44.5 (15-Dec-2018)
Please run 'e2fsck -f /dev/md0p1' first.


root@pandora:~# e2fsck -f /dev/md0p1
e2fsck 1.44.5 (15-Dec-2018)
Pass 1: Checking inodes, blocks, and sizes
Inode 90963972 extent tree (at level 2) could be narrower.  Optimize<y>? yes
Inode 90963985 extent tree (at level 2) could be narrower.  Optimize<y>? yes
Inode 91488280 extent tree (at level 2) could be narrower.  Optimize<y>? yes
Pass 1E: Optimizing extent trees
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information


md0: ***** FILE SYSTEM WAS MODIFIED *****
md0: 28420/213630976 files (19.3% non-contiguous), 528006048/854491904 blocks
root@pandora:~# e2fsck -f /dev/md0p1
e2fsck 1.44.5 (15-Dec-2018)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
md0: 28420/213630976 files (19.3% non-contiguous), 528006048/854491904 blocks
root@pandora:~#
root@pandora:~# resize2fs /dev/md0p1
resize2fs 1.44.5 (15-Dec-2018)
Resizing the filesystem on /dev/md0p1 to 1416015369 ([COLOR=#ff0000]4k)[/COLOR] blocks.

<about 20 min later>
The filesystem on /dev/md0p1 is now 1416015369 (4k) blocks long.


root@pandora:~#
root@pandora:~# vi /etc/fstab
LABEL=md0      /media/md0  ext4 defaults 0 0


root@pandora:~# mount -a
root@pandora:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/mmcblk0p2   49G  2.8G   46G   6% /
tmpfs           249M   19M  231M   8% /lib/modules
tmpfs           249M   28K  249M   1% /etc/network
devtmpfs        243M     0  243M   0% /dev
tmpfs           249M     0  249M   0% /dev/shm
tmpfs           249M  7.5M  242M   4% /run
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           249M     0  249M   0% /sys/fs/cgroup
tmpfs            50M     0   50M   0% /run/user/0
/dev/md0p1      5.2T  2.0T  3.1T  39% /media/md0

[COLOR=#000000]//-->[/COLOR]
[COLOR=#000000]</script>[/COLOR]
[COLOR=#000000]
```[/COLOR]



So not much help of root cause, but maybe this will help someone else with this similar issue

---

### Post by TheFu on 2022-01-11
Whenever posting commands and output, please, please, please use code-tags.  Please edit the post above and wrap it in code-tags.
How-to: [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)

Too hard to read as it is. Sorry.

---

