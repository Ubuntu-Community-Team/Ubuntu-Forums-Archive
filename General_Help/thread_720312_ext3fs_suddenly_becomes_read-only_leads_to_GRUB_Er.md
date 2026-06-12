---
title: "ext3fs suddenly becomes read-only leads to GRUB Error 17 and two partitions missing"
date: 2008-03-10
forum: General Help
---

### Post by kariloy on 2008-03-10
Hello,

I'm not sure where to start so I'll chronologically start this horror story. 
I went to bed last Saturday and as always I leave my laptop on during the night, when I wake up there was some sort of error dialog box from emesene app. I decide to screen shot it but the screen shooting app goes get stuck using nearly 100% CPU cycles, hence I force quit it and after a couple of unsuccessful tries I just decide to ignore it. I start to suspect something was not quite right later when first I can't download some files because it complain somewhere in /tmp being read-only and even more so when I'm trying to edit /etc/apt/sources.list with vim which complains something about the swap file and thought I was running with sudo it does not let me save the changes. The final straw was when I realized that I wasn't able to run programs that weren't already running and I got always a message complaining about being read-only. So innocently I thought "Well maybe this will go away with a reboot" and certainly something did, just not what I would expect. As I reboot I get a nice GRUB Error 17. (and I was even unable to access grub command line by pressing "c"). So even after a few problems trying to run a live CD I actually did it and I went to try and assess the damage.

TWO partitions seemed to be gone, the one with the ubuntu / system and a FAT32 partition with a windows XP instalation. I've read some threads addressing each of my three main problem events but was unable to do anything in order to restore the missing partitions.

Here follows some 'diagnostics':

```
bt ~ # fdisk -l

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         243     1951866   1b  Hidden W95 FAT32
/dev/hda2   *         244        2854    20972857+   c  W95 FAT32 (LBA)
/dev/hda3            4722       12161    59761800    5  Extended
/dev/hda4            2855        4721    14996677+  83  Linux
/dev/hda5           11993       12161     1357461   82  Linux swap
/dev/hda6            4722       11992    58404244+  83  Linux
```

The partitions missing are /dev/hda2 and /dev/hda4. I've tried to fsck and mount them without sucess at any the tasks.

```
bt ~ # fdisk /dev/hda4

Unable to open /dev/hda4
bt ~ # fdisk /dev/hda2

Unable to open /dev/hda2
bt ~ # df -a
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                   1242464     12020   1230444   1% /
proc                         0         0         0   -  /proc
sysfs                        0         0         0   -  /sys
usbfs                        0         0         0   -  /proc/bus/usb
/dev/hda1              1948040   1394712    553328  72% /mnt/hda1
/dev/hda6             57487008  37724684  16842112  70% /mnt/hda6

bt ~ # cat /etc/fstab
aufs / aufs defaults 0 0 # AutoUpdate
devpts /dev/pts devpts gid=5,mode=620 0 0 # AutoUpdate
proc /proc proc defaults 0 0 # AutoUpdate
sysfs /sys sysfs defaults 0 0 # AutoUpdate
/dev/hdb /mnt/hdb iso9660 noauto,users,exec 0 0 # AutoUpdate
/dev/hda1 /mnt/hda1 vfat auto,noatime,users,suid,dev,exec,quiet,umask=0,check=s,shortname=mixed 0 0 # AutoUpdate
/dev/hda5 /mnt/hda5 swap auto,defaults 0 0 # AutoUpdate
/dev/hda6 /mnt/hda6 ext3 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/fd0 /mnt/floppy vfat noauto,noatime,users,suid,dev,exec 0 0 # AutoUpdate

bt ~ # cat /etc/mtab
aufs / aufs rw 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
/dev/hda1 /mnt/hda1 vfat rw,noatime,quiet,umask=0,check=s,shortname=mixed 0 0
/dev/hda6 /mnt/hda6 ext3 rw,noatime 0 0
``` 

At least the /home partition was auto-mounted and I was able to backup the relevant information from there. So any ideas if there are chances of salvaging the partitions that gone AWOL? :s

---

### Post by phrawzty on 2008-03-10
> **kariloy said:**
> ```
bt ~ # fdisk /dev/hda4

Unable to open /dev/hda4
bt ~ # fdisk /dev/hda2

Unable to open /dev/hda2

You cannot use fdisk to open particular partitions on drives - only the entire drive at once, i.e. :
[CODE]$ sudo fdisk /dev/hda
```

I would strong suggest trying to mount the "missing" partitions manually and seeing if the data is still intact :

```
$ sudo mkdir /mnt/hda4
$ sudo mount /dev/hda4 /mnt/hda4
$ cd /mnt/hda4 && ls -l
```

Do the same for hda2 as well (of course).  If the data is still there, you can always add the drives back to fstab (and mtab, as you like) manually.

---

### Post by tgalati4 on 2008-03-10
Check your /var/log/syslog for read/write errors.  It sounds like a hard disk that is failing.  How old is the laptop?

---

### Post by kariloy on 2008-03-10
Although I don't show it in the code above I've already tried conventional mounting and other less conventional stuff I found from diverse posts.
When I try to mount it complains:

```
mount: /dev/hda4 is not a valid block device
```

and e2fsck also complains:

```
e2fsck: No such device or address while trying to open /dev/hda4
Possibly non-existent or swap device?
```

But i still can see the partitions in /proc/partitions

```
bt ~ # cat /proc/partitions
major minor  #blocks  name

   3     0   97685784 hda
   3     1    1951866 hda1
   3     2   20972857 hda2
   3     3          1 hda3
   3     4   14996677 hda4
   3     5    1357461 hda5
   3     6   58404244 hda6
... 

```

There's seem to be something gone bad with the superblocks and I can't seem to tackle it down.
I read somewhere that and ext3fs becoming read-only is a self-protect mechanisc when finding bad sectors. What baffles me is that not only it gone to read-only... to not read at all and took with it a FAT32 partition. I also wonder if me having a ~ 1.6 .iso file mounted as loop might contributed to the current situation. Or if I might have just been a victim of a nefarious attack...

> Check your /var/log/syslog for read/write errors. It sounds like a hard disk that is failing. How old is the laptop?

The laptop is only about 17-18 months old. As for the /var/log/syslog here it is in attachment and it sure does seem to point to where some badness might lie :s

---

### Post by tgalati4 on 2008-03-10
I can't open syslog.gz, perhaps it's empty.  Just attach the entire syslog (delete any private information).

---

### Post by kuja on 2008-03-10
If the partitions "disappeared", why not try to recover them with testdisk? (This can be attempted from a livecd if necessary) If testdisk isn't installed you should be able to find it in the universe repository.

---

### Post by chrisccoulson on 2008-03-10
> **tgalati4 said:**
> I can't open syslog.gz, perhaps it's empty.  Just attach the entire syslog (delete any private information).

```
Mar 10 04:40:15 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:40:15 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477055, high=10, low=2704895, sector=170477055
Mar 10 04:40:15 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:40:15 (none) kernel: end_request: I/O error, dev hda, sector 170477055
Mar 10 04:40:15 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914883, block=11829258
Mar 10 04:40:32 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:40:32 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=145769951, high=8, low=11552223, sector=145769951
Mar 10 04:40:32 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:40:32 (none) kernel: end_request: I/O error, dev hda, sector 145769951
Mar 10 04:40:35 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:40:35 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=176271495, high=10, low=8499335, sector=176271495
Mar 10 04:40:35 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:40:35 (none) kernel: end_request: I/O error, dev hda, sector 176271495
Mar 10 04:40:55 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 04:40:55 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:40:55 (none) kernel: ide0: reset: success
Mar 10 04:41:34 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 04:41:34 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:41:34 (none) kernel: ide0: reset: success
Mar 10 04:42:09 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:42:09 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=190399935, high=11, low=5850559, sector=190399935
Mar 10 04:42:09 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:42:09 (none) kernel: end_request: I/O error, dev hda, sector 190399935
Mar 10 04:42:09 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=7159831, block=14319618
Mar 10 04:42:13 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:42:13 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=190399935, high=11, low=5850559, sector=190399935
Mar 10 04:42:13 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:42:13 (none) kernel: end_request: I/O error, dev hda, sector 190399935
Mar 10 04:42:13 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=7159818, block=14319618
Mar 10 04:42:19 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:42:19 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477055, high=10, low=2704895, sector=170477055
Mar 10 04:42:19 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:42:19 (none) kernel: end_request: I/O error, dev hda, sector 170477055
Mar 10 04:42:19 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914912, block=11829258
Mar 10 04:42:27 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:42:27 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=86853087, high=5, low=2967007, sector=86853087
Mar 10 04:42:27 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:42:27 (none) kernel: end_request: I/O error, dev hda, sector 86853087
Mar 10 04:42:27 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=688259, block=1376262
Mar 10 04:42:30 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:42:30 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=174671295, high=10, low=6899135, sector=174671295
Mar 10 04:42:30 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:42:30 (none) kernel: end_request: I/O error, dev hda, sector 174671295
Mar 10 04:42:30 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=6176770, block=12353538
Mar 10 04:42:33 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:42:33 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=86853087, high=5, low=2967007, sector=86853087
Mar 10 04:42:33 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:42:33 (none) kernel: end_request: I/O error, dev hda, sector 86853087
Mar 10 04:42:33 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=688261, block=1376262
Mar 10 04:42:35 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:42:35 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=174671295, high=10, low=6899135, sector=174671295
Mar 10 04:42:35 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:42:35 (none) kernel: end_request: I/O error, dev hda, sector 174671295
Mar 10 04:42:35 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=6176772, block=12353538
Mar 10 04:42:40 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:42:40 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=190399935, high=11, low=5850559, sector=190399935
Mar 10 04:42:40 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:42:40 (none) kernel: end_request: I/O error, dev hda, sector 190399935
Mar 10 04:42:40 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=7159809, block=14319618
Mar 10 04:42:48 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:42:48 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477007, high=10, low=2704847, sector=170477007
Mar 10 04:42:48 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:42:48 (none) kernel: end_request: I/O error, dev hda, sector 170477007
Mar 10 04:42:48 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914698, block=11829252
Mar 10 04:42:52 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:42:52 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=145786287, high=8, low=11568559, sector=145786287
Mar 10 04:42:52 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:42:52 (none) kernel: end_request: I/O error, dev hda, sector 145786287
Mar 10 04:43:01 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:43:01 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=190399935, high=11, low=5850559, sector=190399935
Mar 10 04:43:01 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:43:01 (none) kernel: end_request: I/O error, dev hda, sector 190399935
Mar 10 04:43:01 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=7159811, block=14319618
Mar 10 04:43:05 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:43:05 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=81954415, high=4, low=14845551, sector=81954415
Mar 10 04:43:05 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:43:05 (none) kernel: end_request: I/O error, dev hda, sector 81954415
Mar 10 04:43:18 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 04:43:18 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:43:18 (none) kernel: ide0: reset: success
Mar 10 04:44:00 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 04:44:00 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:44:01 (none) kernel: ide0: reset: success
Mar 10 04:44:13 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:44:13 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=190399935, high=11, low=5850559, sector=190399935
Mar 10 04:44:13 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:44:13 (none) kernel: end_request: I/O error, dev hda, sector 190399935
Mar 10 04:44:13 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=7159812, block=14319618
Mar 10 04:44:29 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:44:29 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477055, high=10, low=2704895, sector=170477055
Mar 10 04:44:29 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:44:29 (none) kernel: end_request: I/O error, dev hda, sector 170477055
Mar 10 04:44:29 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914903, block=11829258
Mar 10 04:44:32 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:44:32 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477047, high=10, low=2704887, sector=170477047
Mar 10 04:44:32 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:44:32 (none) kernel: end_request: I/O error, dev hda, sector 170477047
Mar 10 04:44:32 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914878, block=11829257
Mar 10 04:44:34 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:44:34 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477047, high=10, low=2704887, sector=170477047
Mar 10 04:44:34 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:44:34 (none) kernel: end_request: I/O error, dev hda, sector 170477047
Mar 10 04:44:34 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914879, block=11829257
Mar 10 04:44:36 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:44:36 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477047, high=10, low=2704887, sector=170477047
Mar 10 04:44:36 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:44:36 (none) kernel: end_request: I/O error, dev hda, sector 170477047
Mar 10 04:44:36 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914880, block=11829257
Mar 10 04:44:39 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:44:39 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477055, high=10, low=2704895, sector=170477055
Mar 10 04:44:39 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:44:39 (none) kernel: end_request: I/O error, dev hda, sector 170477055
Mar 10 04:44:39 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914881, block=11829258
Mar 10 04:44:41 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:44:41 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477055, high=10, low=2704895, sector=170477055
Mar 10 04:44:41 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:44:41 (none) kernel: end_request: I/O error, dev hda, sector 170477055
Mar 10 04:44:41 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914882, block=11829258
Mar 10 04:44:43 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:44:43 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477055, high=10, low=2704895, sector=170477055
Mar 10 04:44:43 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:44:43 (none) kernel: end_request: I/O error, dev hda, sector 170477055
Mar 10 04:44:43 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914885, block=11829258
Mar 10 04:44:46 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:44:46 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477055, high=10, low=2704895, sector=170477055
Mar 10 04:44:46 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:44:46 (none) kernel: end_request: I/O error, dev hda, sector 170477055
Mar 10 04:44:46 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914887, block=11829258
Mar 10 04:44:48 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:44:48 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477055, high=10, low=2704895, sector=170477055
Mar 10 04:44:48 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:44:48 (none) kernel: end_request: I/O error, dev hda, sector 170477055
Mar 10 04:44:48 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914888, block=11829258
Mar 10 04:44:50 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:44:50 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477055, high=10, low=2704895, sector=170477055
Mar 10 04:44:50 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:44:50 (none) kernel: end_request: I/O error, dev hda, sector 170477055
Mar 10 04:44:50 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914890, block=11829258
Mar 10 04:44:53 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:44:53 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477055, high=10, low=2704895, sector=170477055
Mar 10 04:44:53 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:44:53 (none) kernel: end_request: I/O error, dev hda, sector 170477055
Mar 10 04:44:53 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914891, block=11829258
Mar 10 04:44:55 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:44:55 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477055, high=10, low=2704895, sector=170477055
Mar 10 04:44:55 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:44:55 (none) kernel: end_request: I/O error, dev hda, sector 170477055
Mar 10 04:44:55 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914892, block=11829258
Mar 10 04:44:57 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:44:57 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477055, high=10, low=2704895, sector=170477055
Mar 10 04:44:57 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:44:57 (none) kernel: end_request: I/O error, dev hda, sector 170477055
Mar 10 04:44:57 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914893, block=11829258
Mar 10 04:45:00 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:45:00 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477055, high=10, low=2704895, sector=170477055
Mar 10 04:45:00 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:45:00 (none) kernel: end_request: I/O error, dev hda, sector 170477055
Mar 10 04:45:00 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914894, block=11829258
Mar 10 04:45:02 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:45:02 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477055, high=10, low=2704895, sector=170477055
Mar 10 04:45:02 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:45:02 (none) kernel: end_request: I/O error, dev hda, sector 170477055
Mar 10 04:45:02 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914895, block=11829258
Mar 10 04:45:04 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:45:04 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477055, high=10, low=2704895, sector=170477055
Mar 10 04:45:04 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:45:04 (none) kernel: end_request: I/O error, dev hda, sector 170477055
Mar 10 04:45:04 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914896, block=11829258
Mar 10 04:45:07 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:45:07 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477055, high=10, low=2704895, sector=170477055
Mar 10 04:45:07 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:45:07 (none) kernel: end_request: I/O error, dev hda, sector 170477055
Mar 10 04:45:07 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914900, block=11829258
Mar 10 04:45:09 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:45:09 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477055, high=10, low=2704895, sector=170477055
Mar 10 04:45:09 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:45:09 (none) kernel: end_request: I/O error, dev hda, sector 170477055
Mar 10 04:45:09 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914902, block=11829258
Mar 10 04:45:12 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:45:12 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=86853055, high=5, low=2966975, sector=86853055
Mar 10 04:45:12 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:45:12 (none) kernel: end_request: I/O error, dev hda, sector 86853055
Mar 10 04:45:12 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=688136, block=1376258
Mar 10 04:45:14 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:45:14 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477007, high=10, low=2704847, sector=170477007
Mar 10 04:45:14 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:45:14 (none) kernel: end_request: I/O error, dev hda, sector 170477007
Mar 10 04:45:14 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914704, block=11829252
Mar 10 04:45:17 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:45:17 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=86853055, high=5, low=2966975, sector=86853055
Mar 10 04:45:17 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:45:17 (none) kernel: end_request: I/O error, dev hda, sector 86853055
Mar 10 04:45:17 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=688131, block=1376258
Mar 10 04:45:19 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:45:19 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=98649551, high=5, low=14763471, sector=98649551
Mar 10 04:45:19 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:45:19 (none) kernel: end_request: I/O error, dev hda, sector 98649551
Mar 10 04:45:19 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=1425479, block=2850820
Mar 10 04:45:22 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:45:22 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=86853087, high=5, low=2967007, sector=86853087
Mar 10 04:45:22 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:45:22 (none) kernel: end_request: I/O error, dev hda, sector 86853087
Mar 10 04:45:22 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=688258, block=1376262
Mar 10 04:45:24 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 04:45:24 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=86853055, high=5, low=2966975, sector=86853055
Mar 10 04:45:24 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:45:24 (none) kernel: end_request: I/O error, dev hda, sector 86853055
Mar 10 04:45:24 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=688129, block=1376258
Mar 10 04:45:54 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 04:45:54 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:45:54 (none) kernel: ide0: reset: success
Mar 10 04:46:11 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 04:46:11 (none) kernel: ide: failed opcode was: unknown
Mar 10 04:46:12 (none) kernel: ide0: reset: success
Mar 10 11:07:17 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 11:07:17 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=170477055, high=10, low=2704895, sector=170477055
Mar 10 11:07:17 (none) kernel: ide: failed opcode was: unknown
Mar 10 11:07:17 (none) kernel: end_request: I/O error, dev hda, sector 170477055
Mar 10 11:07:17 (none) kernel: EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=5914909, block=11829258
Mar 10 13:27:25 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 13:27:25 (none) kernel: ide: failed opcode was: unknown
Mar 10 13:27:25 (none) kernel: ide0: reset: success
Mar 10 13:28:31 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 13:28:31 (none) kernel: ide: failed opcode was: unknown
Mar 10 13:28:31 (none) kernel: ide0: reset: success
Mar 10 13:30:55 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 13:30:55 (none) kernel: ide: failed opcode was: unknown
Mar 10 13:30:55 (none) kernel: ide0: reset: success
Mar 10 13:31:13 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 13:31:13 (none) kernel: ide: failed opcode was: unknown
Mar 10 13:31:14 (none) kernel: ide0: reset: success
Mar 10 13:32:46 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 13:32:46 (none) kernel: ide: failed opcode was: unknown
Mar 10 13:32:47 (none) kernel: ide0: reset: success
Mar 10 13:34:14 (none) kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Mar 10 13:34:14 (none) kernel: hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=125130213, high=7, low=7689701, sector=125130213
Mar 10 13:34:14 (none) kernel: ide: failed opcode was: unknown
Mar 10 13:34:14 (none) kernel: end_request: I/O error, dev hda, sector 125130213
Mar 10 13:35:12 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 13:35:12 (none) kernel: ide: failed opcode was: unknown
Mar 10 13:35:12 (none) kernel: ide0: reset: success
Mar 10 13:37:28 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 13:37:28 (none) kernel: ide: failed opcode was: unknown
Mar 10 13:37:28 (none) kernel: ide0: reset: success
Mar 10 13:41:09 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 13:41:09 (none) kernel: ide: failed opcode was: unknown
Mar 10 13:41:09 (none) kernel: ide0: reset: success
Mar 10 13:43:16 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 13:43:16 (none) kernel: ide: failed opcode was: unknown
Mar 10 13:43:16 (none) kernel: ide0: reset: success
Mar 10 13:43:26 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 13:43:26 (none) kernel: ide: failed opcode was: unknown
Mar 10 13:43:27 (none) kernel: ide0: reset: success
Mar 10 13:43:41 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 13:43:41 (none) kernel: ide: failed opcode was: unknown
Mar 10 13:43:42 (none) kernel: ide0: reset: success
Mar 10 13:43:54 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 13:43:54 (none) kernel: ide: failed opcode was: unknown
Mar 10 13:43:54 (none) kernel: ide0: reset: success
Mar 10 13:44:11 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 13:44:11 (none) kernel: ide: failed opcode was: unknown
Mar 10 13:44:12 (none) kernel: ide0: reset: success
Mar 10 14:03:53 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 14:03:53 (none) kernel: ide: failed opcode was: unknown
Mar 10 14:03:53 (none) kernel: ide0: reset: success
Mar 10 14:04:03 (none) kernel: hda: irq timeout: status=0xd0 { Busy }
Mar 10 14:04:03 (none) kernel: ide: failed opcode was: unknown
Mar 10 14:04:03 (none) kernel: ide0: reset: success
```

---

### Post by chrisccoulson on 2008-03-10
What is the output of:
```
sudo smartctl -a /dev/hda
```

---

### Post by kariloy on 2008-03-11
Well I've already tried to run smartctl before but as I was running back track live CD it was not installed and I was just to angered to go through the dependency hell to install its rpm. Anyway the reason I'm not running a Ubuntu Live CD is because I get yet another problem and I'm unable to do so. (ata1.00 error complains... DRDY ERR ... UNC and so forth. Tried ubuntu 7.04, 7.10 (ubuntu, xubuntu) and 8.04 alpha6 and well end-up with the same behaviour).

Meanwhile using the backtrack live CD i notice that even my /home partition (one escaping the initial carnage) was getting "degraded". That is folders in there where getting progressively inaccessible. Hence I've unmonted it and ran a e2fsck on it overnight. At the end of it it didn't seem to finished up very nicely mentioning some read/write error about swap? and something else I can't recall.

Anyway now I'm running the GParted Live CD. As it reaches the console prompt it starts spewing out errors similar to the ones on my previous syslog but mainly referring themselves to hda4 (the linux / partition). Even with that noise I was able to start fluxbox and after some scanning time the GParted show me the partitions seemingly ok, except for hda4 which was of unknown filesystem (when it was supposed to be ext3).

Currently I'm running testdisk to see what can be done. Once I'm sure there's physical damage to the hard drive or I am unable to determine for sure what the damage is and do something about it then I guess I'm taking the laptop to the store, complain about the hard drive and hope to get a new one and have the problem fixed. :|

**Edit**

After running testdrive the only partition it offered for rescue was hda1 which was the only one that (at least seemingly) was unaffected by all this mess, so I just continued and exited testdrive. On GParted however I decide to delete all partitions above hda3 (hda3, hda4, hda5 and hda6), I tried that and I get some error saying it could do it. However GParted does a rescan and the whole drive disappears.

By the way the log of testdrive:

```
Tue Mar 11 11:59:09 2008
Command line: TestDisk

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
Linux version (ext2fs lib: 1.40.2, ntfs lib: 9:0:0, reiserfs lib: 0.3.1-rc8, ewf lib: none)
Using locale 'pt_PT'.
disk_get_geometry BLKGETSIZE64 /dev/hda number of cylinders 16383 !=  12161 (calculated)
Hard disk list
Disk /dev/hda - 100 GB / 93 GiB - CHS 12161 255 63, sector size=512
Disk /dev/hdb - 53 MB / 51 MiB - CHS 2 255 63 (RO), sector size=2048
Disk /dev/sda - 254 MB / 243 MiB - CHS 31 255 63, sector size=512

Disk /dev/hda - 100 GB / 93 GiB
Partition table type: Intel

Analyse Disk /dev/hda - 100 GB / 93 GiB - CHS 12161 255 63
Geometry from i386 MBR: head=255 sector=63
FAT32
test_FAT size boot_sector 3903732, partition 3903732
FAT1 : 32-3839
FAT2 : 3840-7647
start_rootdir : 8208 root cluster : 72
Data : 7648-3903727
sectors : 3903732
cluster_size : 8
no_of_cluster : 487010 (2 - 487011)
fat_length 3808 calculated 3805
file_read(4,16,buffer,3903795(243/0/1)) read err: Input/output error
file_read(4,1,buffer,3903795(243/0/1)) read err: Input/output error
file_read(4,1,buffer,3903796(243/0/2)) read err: Input/output error
file_read(4,1,buffer,3903797(243/0/3)) read err: Input/output error
check_FAT: Read error
check_part_i386 failed for partition type 0C
file_read(4,16,buffer,45849512(2854/0/3)) read err: Input/output error
file_read(4,1,buffer,45849512(2854/0/3)) read err: Input/output error
file_read(4,1,buffer,45849513(2854/0/4)) read err: Input/output error
file_read(4,16,buffer,45849511(2854/0/2)) read err: Input/output error
file_read(4,16,buffer,45849510(2854/0/1)) read err: Input/output error
check_part_i386 failed for partition type 83
get_geometry_from_list_part_aux head=255 nbr=10
get_geometry_from_list_part_aux head=8 nbr=4
get_geometry_from_list_part_aux head=16 nbr=2
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=10
Current partition structure:
 1 P hid. FAT32               0   1  1   242 254 63    3903732 [RECOVERY]
check_FAT: Read error
 2 * FAT32 LBA              243   0  1  2853 254 63   41945715
 2 * FAT32 LBA              243   0  1  2853 254 63   41945715
 3 E extended              4721   0  1 12160 254 63  119523600
No EXT2, JFS, Reiser, cramfs or XFS marker
 4 P Linux                 2854   0  1  4720 254 63   29993355
 4 P Linux                 2854   0  1  4720 254 63   29993355
 5 L Linux Swap           11992   1  1 12160 254 63    2714922
   X extended              4721   0  2 11991 254 63  116808614
 6 L Linux                 4721   2  1 11991 254 63  116808489
Ask the user for vista mode
Computes LBA from CHS for Disk /dev/hda - 100 GB / 93 GiB - CHS 12162 255 63
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/hda - 100 GB / 93 GiB - CHS 12162 255 63
FAT32
FAT1 : 32-3839
FAT2 : 3840-7647
start_rootdir : 8208 root cluster : 72
Data : 7648-3903727
sectors : 3903732
cluster_size : 8
no_of_cluster : 487010 (2 - 487011)
fat_length 3808 calculated 3805

FAT32 at 0/1/1
   D FAT32                    0   1  1   242 254 63    3903732 [RECOVERY]
     FAT32, 1998 MB / 1906 MiB
file_read(4,16,buffer,3903797(243/0/3)) read err: Input/output error
file_read(4,1,buffer,3903797(243/0/3)) read err: Input/output error
file_read(4,1,buffer,3903798(243/0/4)) read err: Input/output error
file_read(4,16,buffer,3903795(243/0/1)) read err: Input/output error
file_read(4,1,buffer,3903795(243/0/1)) read err: Input/output error
file_read(4,1,buffer,3903796(243/0/2)) read err: Input/output error
file_read(4,1,buffer,3903799(243/0/5)) read err: Input/output error
file_read(4,16,buffer,41648254(2592/123/26)) read err: Partial read
file_read(4,16,buffer,45849512(2854/0/3)) read err: Input/output error
file_read(4,1,buffer,45849512(2854/0/3)) read err: Input/output error
file_read(4,1,buffer,45849513(2854/0/4)) read err: Input/output error
file_read(4,16,buffer,45849510(2854/0/1)) read err: Input/output error
```

the log file goes one with truckloads of this "read err" lines. Total file size is ~481Mb.

Interesting thing is that I think "Oh well the whole disk disappeared but let me try to reboot and run again the live CD and see if I can find it again". Unfortunately now I don't even get past boot.

I have a "nice message":
```
Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key
```  

I've tried to change boot order in BIOS, also tried several live CDs and a boot Pen drive... and always the same message.

I guess it's time to return the machine to the store and hope the warranty isn't void yet. I've done enough damage for now :X

Anyway thanks for trying to help!

---

### Post by articpenguin on 2008-03-11
sounds like your harddrive is on its way out.

---

