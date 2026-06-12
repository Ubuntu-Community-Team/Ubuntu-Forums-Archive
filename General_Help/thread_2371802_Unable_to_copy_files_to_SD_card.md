---
title: "Unable to copy files to SD card"
date: 2017-09-19
forum: General Help
---

### Post by satimis on 2017-09-19
Hi all,

Ubuntu 16.04 desktop

Unable to copy files to SD card which has been partitioned (one partition using the entire SD card) and formatted as ext4

The card is detected and mounted automatically.

$ lsblk```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 111.8G  0 disk 
&#9500;&#9472;sda1   8:1    0 103.9G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   7.9G  0 part [SWAP]
sdb      8:16   1  59.5G  0 disk 
&#9492;&#9472;sdb1   8:17   1  59.5G  0 part /media/satimis/386b6c26-9c60-41fd-aeb7-b07093af
sr0     11:0    1  1024M  0 rom  

```

$ ls -al /dev/sdb```

brw-rw---- 1 root disk 8, 16 Sep 19 12:43 /dev/sdb

```

Start File Manager
Only lost+found folder is there

Right-click -> Properties -> Permissions```

Owner:  root
Group:  root
(You are not the owner, so you cannot change thsee permissions)

```


Please help.  Thanks

Regards
satimis

---

### Post by Bashing-om on 2017-09-19
satimis; Hello once more .

As is now, only root can access that drive .

If "you" want access to that drive you will have to change these rights .

One can do :
```

sudo chown -R satimis:satimis /media/satimis/386b6c26-9c60-41fd-aeb7-b07093af

```
with the device connected. To give the user "satimis" access .

my bit to try and help

---

### Post by satimis on 2017-09-19
> **Bashing-om said:**
> satimis; Hello once more .

As is now, only root can access that drive .

If "you" want access to that drive you will have to change these rights .

One can do :
```

sudo chown -R satimis:satimis /media/satimis/386b6c26-9c60-41fd-aeb7-b07093af

```
with the device connected. To give the user "satimis" access .

my bit to try and help

Hi,

Thanks for your advice.

The strange thing happened here is:
After replugin the SD card whihc is mounted on a cardreader, I could not find it.  It is already mounted

I have to re-run;
$ sudo mkfs.ext4 /dev/sdb1```

mke2fs 1.42.13 (17-May-2015)
/dev/sdb1 contains a ext4 file system
        last mounted on Tue Sep 19 12:45:41 2017
Proceed anyway? (y,n) y
Creating filesystem with 15591675 4k blocks and 3899392 inodes
Filesystem UUID: 97771230-f2a2-4018-b077-8c197313caa7
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done   

```

$ lsblk```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 111.8G  0 disk 
&#9500;&#9472;sda1   8:1    0 103.9G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   7.9G  0 part [SWAP]
sdb      8:16   1  59.5G  0 disk 
&#9492;&#9472;sdb1   8:17   1  59.5G  0 part /media/satimis/97771230-f2a2-4018-b077-8c197313
sr0     11:0    1  1024M  0 rom  
```

$ sudo chown -R satimis:satimis /media/satimis/97771230-f2a2-4018-b077-8c197313caa7```

chown: changing ownership of '/media/satimis/97771230-f2a2-4018-b077-8c197313caa7/lost+found': Read-only file system
chown: changing ownership of '/media/satimis/97771230-f2a2-4018-b077-8c197313caa7': Read-only file system

```

$ sudo mount /dev/sdb /mnt```

mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```

$ dmesg | tail```

[ 4586.727789] blk_update_request: critical target error, dev sdb, sector 0
[ 4586.727803] JBD2: recovery failed
[ 4586.727809] EXT4-fs (sdb1): error loading journal
[ 5041.636680] sd 15:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5041.636686] sd 15:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[ 5041.636691] sd 15:0:0:0: [sdb] tag#0 Add. Sense: Invalid command operation code
[ 5041.636696] sd 15:0:0:0: [sdb] tag#0 CDB: Synchronize Cache(10) 35 00 00 00 00 00 00 00 00 00
[ 5041.636701] blk_update_request: critical target error, dev sdb, sector 0
[ 5041.636785] JBD2: recovery failed
[ 5041.636791] EXT4-fs (sdb1): error loading journal

```

Still failed


Why an USB stick doesn't need taking this step?

USB stick 1G
$ lsblk```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 111.8G  0 disk 
&#9500;&#9472;sda1   8:1    0 103.9G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   7.9G  0 part [SWAP]
sdb      8:16   1   3.8G  0 disk 
&#9492;&#9472;sdb1   8:17   1   3.8G  0 part /media/satimis/7276-8C47
sr0     11:0    1  1024M  0 rom  

```

satimis@PC2:~&#10219; ls -ald /media/satimis/7276-8C47/```

drwxr-xr-x 4 satimis satimis 4096 Jan  1  1970 /media/satimis/7276-8C47/

```

Please advise.  Thanks

Edit
====
On replugin the SD card again, following warning popup
```

Unable to mount 64 GB Volume
Error mounting /dev/sdb1 at /media/satimis/97771230-f2a2-4018-b077-8c197313caa7: 
Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb1"
 "/media/satimis/97771230-f2a2-4018-b077-8c197313caa7"' 
exited with non-zero exit status 32: mount: /dev/sdb1: can't read superblock
						[OK]

```


Regards
satimis

---

### Post by Bashing-om on 2017-09-19
Oh satimis :)

Consider what is : and what changes .
when you "sudo mkfs.ext4 /dev/sdb1" you got a new UUID
was: 386b6c26-9c60-41fd-aeb7-b07093af
changed to : 97771230-f2a2-4018-b077-8c197313

" . It is already mounted " then you failed to safely unmount it the last time you connected , leaving the file system in a inconsistent state .

" /media/satimis/7276-8C47" looks like now a fat 16 file system identifier rather than a ext4 ( linux) file system .

I can not know what you have done . 

How about at this point you re-format the device to ext4
and while the device is connected post back:
```

sudo fdisk -lu
sudo blkid
mount

```

And we try again to give you access to that device - with the now changed UUID - mountpoint .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by satimis on 2017-09-19
> **Bashing-om said:**
> Oh satimis :)

Consider what is : and what changes .
when you "sudo mkfs.ext4 /dev/sdb1" you got a new UUID
was: 386b6c26-9c60-41fd-aeb7-b07093af
changed to : 97771230-f2a2-4018-b077-8c197313

" . It is already mounted " then you failed to safely unmount it the last time you connected , leaving the file system in a inconsistent state .

I succeeded to eject the SD card

Right-click on the SD card icon on the left panel -> Eject
An sign popup saying it is safely ejected

On replugin the SD card, lsblk shows another path.  I don't know why it happened


> 
" /media/satimis/7276-8C47" looks like now a fat 16 file system identifier rather than a ext4 ( linux) file system .

I can not know what you have done . 

That is an USB stick which I tested on this PC, not the SD card

> 
How about at this point you re-format the device to ext4
and while the device is connected post back:
```

sudo fdisk -lu
sudo blkid
mount

```

And we try again to give you access to that device - with the now changed UUID - mountpoint .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]
I'm now checking badbloks

$ sudo badblocks -sv /dev/sdb1```

Checking blocks 0 to 62366702
Checking for bad blocks (read-only test):  27.47% done, 22:18 elapsed. (0/0/0 errors)

```

It''ll take a while to finish.  I'll test your advice later

Regards
satimis

---

### Post by satimis on 2017-09-19
Hi,

Continue:-

$ sudo badblocks -sv /dev/sdb1```

....
....

62366702
done                                                 
Pass completed, 26776367 bad blocks found. (26776367/0/0 errors)
```

$ lsblk```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 111.8G  0 disk 
&#9500;&#9472;sda1   8:1    0 103.9G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   7.9G  0 part [SWAP]
sdb      8:16   1  59.5G  0 disk 
&#9492;&#9472;sdb1   8:17   1  59.5G  0 part 
sr0     11:0    1  1024M  0 rom  

```

$ sudo mkfs.ext4 /dev/sdb1```

mke2fs 1.42.13 (17-May-2015)
/dev/sdb1 contains a ext4 file system
        last mounted on Tue Sep 19 13:27:15 2017
Proceed anyway? (y,n) y
Creating filesystem with 15591675 4k blocks and 3899392 inodes
Filesystem UUID: 6d12c99c-97f1-44b5-9a92-9ad021389997
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done   

satimis@PC2:~&#10219; 

```

$ sudo fdisk -lu```

Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00009fb6

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 217866239 217864192 103.9G 83 Linux
/dev/sda2       217868286 234440703  16572418   7.9G  5 Extended
/dev/sda5       217868288 234440703  16572416   7.9G 82 Linux swap / Solaris

Disk /dev/sdb: 59.5 GiB, 63864569856 bytes, 124735488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 27177C91-C3DF-40E0-85C8-8C38C89A2DD5

Device     Start       End   Sectors  Size Type
/dev/sdb1   2048 124735454 124733407 59.5G Linux filesystem

```

$ sudo blkid```

/dev/sdb1: UUID="6d12c99c-97f1-44b5-9a92-9ad021389997" TYPE="ext4" PARTUUID="c3de1c8c-cf92-4be2-b3b6-d2383e930b13"
/dev/sda1: UUID="63e5cf5d-2c63-4cea-af77-860783763825" TYPE="ext4" PARTUUID="00009fb6-01"
/dev/sda5: UUID="c05489f4-d7d7-463e-be33-8878854612c2" TYPE="swap" PARTUUID="00009fb6-05"

```

&#10219; mount ```

sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=3983912k,nr_inodes=995978,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=807452k,mode=755)
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids,release_agent=/run/cgmanager/agents/cgm-release-agent.pids)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)

cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=26,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=807452k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)

```

Now it mounts

Right-click SD card icon on left panel -> Open
lost+found folder is there


$ ls /mnt/
No printout
$ ls /dev/sdb1```

/dev/sdb1

```
&#10219; ls /dev/sdb1/```

ls: cannot access '/dev/sdb1/': Not a directory

```

&#10219; lsblk```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 111.8G  0 disk 
&#9500;&#9472;sda1   8:1    0 103.9G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   7.9G  0 part [SWAP]
sdb      8:16   1  59.5G  0 disk 
&#9492;&#9472;sdb1   8:17   1  59.5G  0 part /media/satimis/6d12c99c-97f1-44b5-9a92-9ad02138
sr0     11:0    1  1024M  0 rom  

```


$ sudo chown -R satimis:satimis /media/satimis/6d12c99c-97f1-44b5-9a92-9ad021389997/```

chown: changing ownership of '/media/satimis/6d12c99c-97f1-44b5-9a92-9ad021389997/lost+found': Read-only file system
chown: changing ownership of '/media/satimis/6d12c99c-97f1-44b5-9a92-9ad021389997/': Read-only file system

```

$ ls -al /media/satimis/6d12c99c-97f1-44b5-9a92-9ad021389997```

total 24
drwxr-xr-x  3 root    root     4096 Sep 19 16:25 .
drwxr-x---+ 5 satimis satimis  4096 Sep 19 16:30 ..
drwx------  2 root    root    16384 Sep 19 16:25 lost+found

```

What shall I do next?  Thanks

Regards
satimis

---

### Post by Bashing-om on 2017-09-19
satimis; 

Well; we have the UUID :
6d12c99c-97f1-44b5-9a92-9ad021389997 from mke2fs ;
6d12c99c-97f1-44b5-9a92-9ad021389997 blkid confirms ;

/media/satimis/6d12c99c-97f1-44b5-9a92-9ad02138 ## the UUID truncated ?? 

I do not understand why in the mount command that sdb1 is not identified . Was the device not connected at the time you ran the command ?

fdisk sees the device as sdb1.

I have to question that the device is connected .

Now as to 
> 

$ ls /mnt/
No printout
$ ls /dev/sdb1
Code:
/dev/sdb1
&#10219; ls /dev/sdb1/
Code:
ls: cannot access '/dev/sdb1/': Not a directory

No output from "ls mnt/" is valid IF you have made no directories in /mnt .
//
" ls /dev/sdb1/ " again the system is correct. Here with the ending / ( sdb1/) you are telling the system to point to a directory, this directory does not exist and the system tells you the target is not a directory as the response - ( it is a device ) .

The proper way to address the device is as a device (/dev/) and what it is (sdb1):
```

ls /dev/sdb1

```

To address the file system on the device:
```

ls -al /media/satimis/6d12c99c-97f1-44b5-9a92-9ad021389997

```
where the mountpoint ownership has been changed to you . else root owns it and will have to be addressed as root ( sudo ).

That brings up the point:
> 
changing ownership of '/media/satimis/6d12c99c-97f1-44b5-9a92-9ad021389997/

again, the meaning of the final '/' is telling the system this is a directory - not true !

AND : a matter of high concern :
> 
lost+found': Read-only file system


Huh ? why ? read only ? Is the system mounting such to protect it's self from further damage ? Or what !

And what I suggest here is to create the partition(s) on the device, then change the ownership to "you" . then you have access to these file systems. See what happens here .. we must gain read/write access to the file system(s) .

We will want to delete the directories you have made presently in /media/ to avoid future confusion .

At this time we have made no partition(s) on sdb. While will work as is .. it is the better practice to partition the device as that is what the system expects . As the system administrator, it is your decision as to the partitioning . As the system administrator it is your decision as to what access you will permit to the file systems on these partition(s) .

see:
```

man chown
man chmod

```

small steps
[INDENT][INDENT]we will arrive at the end
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2017-09-19
I would also suggest that to make life a lot easier for you when it comes to finding the SD card mounted in the filesystem that you give the partition on that card a label that means something to you, so that when attached it will always automount to the same "label" mountpoint, ie, /media/username/label.  It will not automount in /mnt and there is little point in getting it to do so in my opinion; /media/username/label is the correct place for removable memory cards or flash drives to automount.

So my recommendation is:-
[LIST=1]
[*]Give the ext4 partition a label, eg **SDCARD** 
[*]Attach it and allow it to automount at /media/satimis/SDCARD, 
[*]Finally with it still attached run ```
sudo chown -R satimis:satimis /media/satimis/SDCARD
```
[/LIST]

---

### Post by satimis on 2017-09-19
> **ajgreeny said:**
> I would also suggest that to make life a lot easier for you when it comes to finding the SD card mounted in the filesystem that you give the partition on that card a label that means something to you, so that when attached it will always automount to the same "label" mountpoint, ie, /media/username/label.  It will not automount in /mnt and there is little point in getting it to do so in my opinion; /media/username/label is the correct place for removable memory cards or flash drives to automount.

So my recommendation is:-
[LIST=1]
[*]Give the ext4 partition a label, eg **SDCARD** 
[*]Attach it and allow it to automount at /media/satimis/SDCARD, 
[*]Finally with it still attached run ```
sudo chown -R satimis:satimis /media/satimis/SDCARD
```
[/LIST]
Hi,

Thanks for your advice.

$ sudo fdisk -l```

Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00009fb6

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 217866239 217864192 103.9G 83 Linux
/dev/sda2       217868286 234440703  16572418   7.9G  5 Extended
/dev/sda5       217868288 234440703  16572416   7.9G 82 Linux swap / Solaris

Disk /dev/sdb: 59.5 GiB, 63864569856 bytes, 124735488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 27177C91-C3DF-40E0-85C8-8C38C89A2DD5

Device     Start       End   Sectors  Size Type
/dev/sdb1   2048 124735454 124733407 59.5G Linux filesystem

```

I suppose "27177C91-C3DF-40E0-85C8-8C38C89A2DD5" is the label of the SD card

Shall I run following command;
```

sudo mlabel -i /dev/SDCARD ::{27177C91-C3DF-40E0-85C8-8C38C89A2DD5}

```
to name the SD card ?

Thanks

Regards
satimis

---

### Post by Bashing-om on 2017-09-19
satimis; Hummm ..

As AJ suggested - something easy to remember and easy to type for the partition label. 
The terminal command(s) e2label or tune2fs :
[https://www.cyberciti.biz/faq/linux-partition-howto-set-labels/](https://www.cyberciti.biz/faq/linux-partition-howto-set-labels/)

-getting there - half the fun

---

### Post by satimis on 2017-09-19
> **Bashing-om said:**
> satimis; Hummm ..

As AJ suggested - something easy to remember and easy to type for the partition label. 
The terminal command(s) e2label or tune2fs :
[https://www.cyberciti.biz/faq/linux-partition-howto-set-labels/](https://www.cyberciti.biz/faq/linux-partition-howto-set-labels/)

-getting there - half the fun
Hi,

&#10219; sudo e2label /dev/sdb1```



```
Blank, no printout

&#10219; sudo e2label /dev/sdb```

e2label: Bad magic number in super-block while trying to open /dev/sdb
Couldn't find valid filesystem superblock.

```

Shall I run;```

$ sudo e2label /dev/sdb SDCARD

```
?

satimis

---

### Post by Bashing-om on 2017-09-19
satimis; Oh Boy ...

> 
Hi,

&#10219; sudo e2label /dev/sdb1
Code:
Blank, no printout

well, yes - as there is no label to this time . So nothing to show .

> 
Shall I run;
Code:
$ sudo e2label /dev/sdb SDCARD

No !
1) A partition (sdb1) is what is labeled - not the device (sdb)
2) Have you made up a partition(s) on the device ? -> do you require guidance here ? Have you thought this through for what you desire to be ?

3) would you prefer some other name for the label than SDCARD ? The choice is yours .

[INDENT]ain't nothing but a thing
[/INDENT]

---

### Post by satimis on 2017-09-19
> **Bashing-om said:**
> 
- snip -
1) A partition (sdb1) is what is labeled - not the device (sdb)
2) Have you made up a partition(s) on the device ? -> do you require guidance here ? Have you thought this through for what you desire to be ?

I ran "fdisk" to partition the SD card, using the entire card without partition.  But /dev/sdb1 was automatically created.  I can't resolve?  Whether this is a small partition created automatically for storing the info of this SD card?

> 
3) would you prefer some other name for the label than SDCARD ? The choice is yours .

I have 3 SD cards.  So label this card as sdcard01 and others as sdcard02, sdcard03 etc.

So the command should be; ?
$ sudo e2label /dev/sdb1 sdcard01

satimis

---

### Post by Bashing-om on 2017-09-19
satimis; Uh Huh .
> 
So the command should be; ?
$ sudo e2label /dev/sdb1 sdcard01


yepper, that is good - should work .

[INDENT][INDENT]good work
[/INDENT][/INDENT]

---

### Post by satimis on 2017-09-20
> **Bashing-om said:**
> satimis; Uh Huh .


yepper, that is good - should work .


$ sudo e2label /dev/sdb1 sdcard01
[sudo] password for satimis:
No complaint

Reboot PC with the SD card on USB port.

After reboot the SD card couldn't be found
$ lsblk ```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 111.8G  0 disk 
&#9500;&#9472;sda1   8:1    0 103.9G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   7.9G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom  

```

Replug the SD card following warning popup
```

Unable to mount 64 GB Volume
Error mounting /dev/sdb1 at /media/satimis/6d12c99c-97f1-44b5-9a92-9ad021389997: Command-line `mount -t
"ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb1" "/media/
satimis/6d12c99c-97f1-44b5-9a92-9ad021389997"' exited with non-zero 
exit status 32: mount: /dev/sdb1: can't read superblock

```

$ lsblk```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 111.8G  0 disk 
&#9500;&#9472;sda1   8:1    0 103.9G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   7.9G  0 part [SWAP]
sdb      8:16   1  59.5G  0 disk 
&#9492;&#9472;sdb1   8:17   1  59.5G  0 part 
sr0     11:0    1  1024M  0 rom 

```
The SD card is there.

$ ls /media/satimis/
The SD card is not here

$ sudo blkid```

/dev/sda1: UUID="63e5cf5d-2c63-4cea-af77-860783763825" TYPE="ext4" PARTUUID="00009fb6-01"
/dev/sda5: UUID="c05489f4-d7d7-463e-be33-8878854612c2" TYPE="swap" PARTUUID="00009fb6-05"
/dev/sdb1: LABEL="sdcard01" UUID="6d12c99c-97f1-44b5-9a92-9ad021389997" TYPE="ext4" PARTUUID="c3de1c8c-cf92-4be2-b3b6-d2383e930b13"

```

$ sudo find / -name sdcard01```

find: &#8216;/run/user/1000/gvfs&#8217;: Permission denied
/dev/disk/by-label/sdcard01

```

$ sudo mount /dev/disk/by-label/sdcard01 /mnt```

mount: /dev/sdb1: can't read superblock

```

Also tried;
$ sudo mount -t ext4 /dev/disk/by-label/sdcard01 /mnt```

mount: /dev/sdb1: can't read superblock

```

Very strange still unable to mount the SD card.

I'll try format the SD card with vfat latter to see what will happen

satimis

---

### Post by satimis on 2017-09-20
Hi all,

Found following thread;
HOWTO: Repair a broken Ext4 Superblock in Ubuntu 31Mar10
[https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

Performed following steps:

$ sudo mke2fs -n /dev/sdb1```

mke2fs 1.42.13 (17-May-2015)
/dev/sdb1 contains a ext4 file system labelled 'sdcard01'
        last mounted on Tue Sep 19 16:30:50 2017
Proceed anyway? (y,n) y
Creating filesystem with 15591675 4k blocks and 3899392 inodes
Filesystem UUID: a0ae5010-9c4c-45c3-b14e-3951f2d0da1f
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424

```

$ sudo e2fsck -b 32768 /dev/sdb1```

e2fsck 1.42.13 (17-May-2015)
sdcard01 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inode 1371649 is in use, but has dtime set.  Fix<y>? yes
Inode 1371649 has imagic flag set.  Clear<y>? yes
Inode 1371649 has a extra size (65535) which is invalid
Fix<y>? yes
....

```
Answer "yes" to all questions.  It took long time to finish.

$ sudo mount -t ext4 /dev/disk/by-label/sdcard01 /mnt
No complaint and now it mounts the device

$ ls /mnt/```

lost+found

```
found lost+found folder

$ ls -al /dev/disk/by-label/sdcard01 ```

lrwxrwxrwx 1 root root 10 Sep 20 13:10 /dev/disk/by-label/sdcard01 -> ../../sdb1

```

$ sudo chown -R satimis:satimis /dev/disk/by-label/sdcard01 

$ ls -al /dev/disk/by-label/sdcard01 ```

lrwxrwxrwx 1 satimis satimis 10 Sep 20 13:10 /dev/disk/by-label/sdcard01 -> ../../sdb1

```

Still I couldn't copy files to SD card

$ cp electric_applicance.txt /mnt/```

cp: cannot create regular file '/mnt/electric_applicance.txt': Read-only file system

```

$ sudo umount /mnt 

$ sudo mount -t ext4 /dev/disk/by-label/sdcard01 /mnt```

mount: /dev/sdb1: can't read superblock

```

Same problem.  It looks very funny to me

satimis

---

### Post by ajgreeny on 2017-09-20
Oh dear!
You seem to be doing things the hard way so I am now going to suggest you start again from square one.

It will possibly perhaps easier to use gparted to work on the sdcard; you can install gparted in your Ubuntu OS from the repos in the normal way.
Open gparted and in the dropdown box top right find the card making sure you do not work on your hard disk; it should be obvious from the size you see reported in the gparted window.

You may need to right click in any partition it finds on the card and choose **unmount** to be able to work on it.
Go to **Device ->Create partition table** and choose the default msdos.  This will delete anything on the card so be certain you have everything off it that you may need to keep. Click the [COLOR="#00FF00"]green[/COLOR] tick to allow this.
You will now be left with unallocated space so right click in this space and choose New, ext4, label it sdcard01, and again let this all happen by clicking the green tick.

You should now have an sdcard with one partition of ext4 on it, sdb1, so now remove the card making sure first that it is not mounted, replug it and it will mount at /media/satimis/sdcard01.
Finally run command ```
sudo chown -R satimis:satimis /media/satimis/sdcard01
``` and that should be job done.

Good luck!

---

### Post by satimis on 2017-09-20
Hi all,

Through pain and difficulties follows are found;
1) Unable creating 2 partitions on SD card
2) Ext4 can't work on SD card but vfat can
3) It is NOT necessary to label the SD card.  It'll be mounted automatically after plugin


Test-1
======
$ sudo fdisk /dev/sdb```

Command (m for help): F
Unpartitioned space /dev/sdb: 0 B, 0 bytes, 0 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Command (m for help): d
Selected partition 1
Partition 1 has been deleted.

Command (m for help): p
Disk /dev/sdb: 59.5 GiB, 63864569856 bytes, 124735488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 27177C91-C3DF-40E0-85C8-8C38C89A2DD5

Command (m for help): n
Partition number (1-128, default 1): 
First sector (2048-124735454, default 2048): 
Last sector, +sectors or +size{K,M,G,T,P} (2048-124735454, default 124735454): +64G
Value out of range.

Last sector, +sectors or +size{K,M,G,T,P} (2048-124735454, default 124735454): +32G

Created a new partition 1 of type 'Linux filesystem' and of size 32 GiB.

Command (m for help): n
Partition number (2-128, default 2): 
First sector (67110912-124735454, default 67110912): 
Last sector, +sectors or +size{K,M,G,T,P} (67110912-124735454, default 124735454): 

Created a new partition 2 of type 'Linux filesystem' and of size 27.5 GiB.

Command (m for help): v
No errors detected.
Header version: 1.0
Using 2 out of 128 partitions.
A total of 0 free sectors is available in 0 segments (the largest is (null)).

Command (m for help): w
The partition table has been altered.
Calling ioctl() to re-read partition table.
/dev/sdb: close device failed: Remote I/O error

```

Failed, Remote I/O error


Test-2
======
$ sudo fdisk /dev/sdb```


Welcome to fdisk (util-linux 2.27.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

Command (m for help): d
Partition number (1,2, default 2): 2

Partition 2 has been deleted.

Command (m for help): d
Selected partition 1
Partition 1 has been deleted.

Command (m for help): n
Partition number (1-128, default 1): 
First sector (2048-124735454, default 2048): 
Last sector, +sectors or +size{K,M,G,T,P} (2048-124735454, default 124735454): 

Created a new partition 1 of type 'Linux filesystem' and of size 59.5 GiB.

Command (m for help): w

The partition table has been altered.
Calling ioctl() to re-read partition table.
Syncing disks.

```

$ lsblk```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 111.8G  0 disk 
&#9500;&#9472;sda1   8:1    0 103.9G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   7.9G  0 part [SWAP]
sdb      8:16   1  59.5G  0 disk 
&#9492;&#9472;sdb1   8:17   1  59.5G  0 part 
sr0     11:0    1  1024M  0 rom  

```

$ sudo blkid```

/dev/sda1: UUID="63e5cf5d-2c63-4cea-af77-860783763825" TYPE="ext4" PARTUUID="00009fb6-01"
/dev/sda5: UUID="c05489f4-d7d7-463e-be33-8878854612c2" TYPE="swap" PARTUUID="00009fb6-05"
/dev/sdb1: LABEL="sdcard01" UUID="6d12c99c-97f1-44b5-9a92-9ad021389997" TYPE="ext4" PARTUUID="8d78c4d8-7816-48ac-a8a0-63b26c33933e"

```

Strange!  LABEL="sdcard01" is still there.

$ sudo umount /mnt```

umount: /mnt: not mounted

```

$ sudo find / -name sdcard01```

find: &#8216;/run/user/1000/gvfs&#8217;: Permission denied
/dev/disk/by-label/sdcard01

```

$ sudo umount /dev/disk/by-label/sdcard01```

umount: /dev/disk/by-label/sdcard01: not mounted

```

$ sudo umount /dev/sdb```

umount: /dev/sdb: not mounted

```

$ sudo mkfs.ntfs /dev/sdb1```

Cluster size has been automatically set to 4096 bytes.
Initializing device with zeroes:   2%
...

```

$ sudo blkid```

/dev/sda1: UUID="63e5cf5d-2c63-4cea-af77-860783763825" TYPE="ext4" PARTUUID="00009fb6-01"
/dev/sda5: UUID="c05489f4-d7d7-463e-be33-8878854612c2" TYPE="swap" PARTUUID="00009fb6-05"
/dev/sdb1: PARTUUID="8d78c4d8-7816-48ac-a8a0-63b26c33933e"

```

LABEL="sdcard01" removed

$ sudo e2label /dev/sdb1 sdcard01```

e2label: Bad magic number in super-block while trying to open /dev/sdb1
Couldn't find valid filesystem superblock.

```

$ df```

Filesystem     1K-blocks     Used Available Use% Mounted on
udev             3983912        0   3983912   0% /dev
tmpfs             807452     9616    797836   2% /run
/dev/sda1      107089952 40554208  61072756  40% /
tmpfs            4037256    98772   3938484   3% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
tmpfs            4037256        0   4037256   0% /sys/fs/cgroup
cgmfs                100        0       100   0% /run/cgmanager/fs
tmpfs             807452       84    807368   1% /run/user/1000

```

$ sudo blkid```

/dev/sda1: UUID="63e5cf5d-2c63-4cea-af77-860783763825" TYPE="ext4" PARTUUID="00009fb6-01"
/dev/sda5: UUID="c05489f4-d7d7-463e-be33-8878854612c2" TYPE="swap" PARTUUID="00009fb6-05"
/dev/sdb1: UUID="D722-6ACB" TYPE="vfat" PARTUUID="8d78c4d8-7816-48ac-a8a0-63b26c33933e"

```

$ ls -al /dev/sdb1```

brw-rw---- 1 root disk 8, 17 Sep 20 18:05 /dev/sdb1

```

$ ls -al /dev/sdb```

brw-rw---- 1 root disk 8, 16 Sep 20 17:29 /dev/sdb

```

$ sudo chown -R satimis:satimis /dev/sdb1

$ ls -al /dev/sdb1```

brw-rw---- 1 satimis satimis 8, 17 Sep 20 18:05 /dev/sdb1

```

$ sudo mount /dev/sdb1 /mnt```

mount: /dev/sdb1 is already mounted or /mnt busy
       /dev/sdb1 is already mounted on /mnt

```

$ ls /mnt
no printout

$ cp electric_applicance.txt /mnt/```

cp: cannot create regular file '/mnt/electric_applicance.txt': Permission denied

```

Unable to copy file on SD card as user!

$ sudo cp electric_applicance.txt /mnt/

Root can copy file on SD card

$ ls /mnt/```

electric_applicance.txt

```

$ sudo umount /mnt

Removed SD card and plugin again.  The SD card can be mounted automatically.

Right-click SD card icon on the left vertical panel -> Open
Starts Nautilus

Right-click -> Properties -> Permissions
Owner:  Me
Access:	Create and delete files
Group:	satimis
Access:	Access files

Files can be copied to SD card as user

I still don't understand why ext4 can work on SD card ?

Regard
satimis

---

### Post by Bashing-om on 2017-09-20
satimis; Hey ...

Making progress !

Maybe a good thing to "read the instructions" at this time and gain an understanding of what a mount point is ?
see:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://www.howtogeek.com/106873/how-to-use-fdisk-to-manage-partitions-on-linux/](http://www.howtogeek.com/106873/how-to-use-fdisk-to-manage-partitions-on-linux/)

[INDENT][INDENT]try'n to help
[/INDENT][/INDENT]

---

