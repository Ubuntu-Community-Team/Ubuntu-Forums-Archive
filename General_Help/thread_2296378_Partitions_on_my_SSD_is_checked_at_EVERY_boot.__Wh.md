---
title: "Partitions on my SSD is checked at EVERY boot.  Why?"
date: 2015-09-25
forum: General Help
---

### Post by sheriff-pointing on 2015-09-25
Hi All, I have Ubuntu Gnome 15.04 installed on a Dell XPS15 (project sputnik hardware) and my SSD is checked on every boot.  It passes without error, but is checked again on the next boot.  I booted into a live USB, and manually checked the partitions, and the filesystem is clean, with no errors reported during fsck.  Any ideas where to start looking to see what is causing this behavior?

My var/log/boot.log shows the behaivior (UUIDs have been changed):

```

[  OK  ] Reached target Local File Systems (Pre).
         Starting File System Check on /dev/disk/by-uuid/a9a9321b-630c-4533-a114-763e497f1fbe...
         Starting File System Check on /dev/disk/by-uuid/AEB9-FB18...
         Starting Load/Save RF Kill Switch Status of rfkill3...
[  OK  ] Started Load/Save RF Kill Switch Status of rfkill2.
[  OK  ] Started Load/Save Random Seed.
[  OK  ] Started Load/Save RF Kill Switch Status of rfkill1.
[  OK  ] Started Load/Save RF Kill Switch Status of rfkill0.
[  OK  ] Started Load/Save RF Kill Switch Status of rfkill3.
[  OK  ] Started Flush Journal to Persistent Storage.
[  OK  ] Started File System Check on /dev/disk/by-uuid/AEB9-FB18.
         Mounting /boot/efi...
[  OK  ] Mounted /boot/efi.
[  OK  ] Started Load/Save Screen Backlight Brightness of backlight:intel_backlight.
[  OK  ] Started File System Check on /dev/disk/by-uuid/a9a9321b-630c-4533-a114-763e497f1fbe.
         Mounting /home...
[  OK  ] Mounted /home.
[  OK  ] Reached target Local File Systems.

```

---

### Post by oldfred on 2015-09-25
Post this, change to correct partition:
Mine shows 0? And it does not work on the FAT32 formatted ESP.
 sudo tune2fs -l /dev/sda3
also shows settings of mount count & how often it will run fsck on reboots

Last checked:             Tue Sep 30 12:27:45 2014
Check interval:           0 (<none>)

I do run my own cron job for trim.

Also post this:
cat /etc/fstab
pass for / & efi are normally 1, meaning it uses system parameter to run fsck every 40 or 60 boots. But mine shows setting is 0, so maybe they have changed default?

---

### Post by sheriff-pointing on 2015-09-25
Hi oldfred, thanks for your help.

```
sheriff@xps-linux:~$ sudo tune2fs -l /dev/sda8
tune2fs 1.42.12 (29-Aug-2014)
Filesystem volume name:   <none>
Last mounted on:          /home
Filesystem UUID:          a9a9421b-610c-4813-c114-763cd97f1fbe
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              19349504
Block count:              77381591
Reserved block count:     3869078
Free blocks:              10116328
Free inodes:              18024870
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1005
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
RAID stride:              32747
Flex block group size:    16
Filesystem created:       Mon Aug 31 11:10:38 2015
Last mount time:          Fri Sep 25 23:11:25 2015
Last write time:          Fri Sep 25 23:11:25 2015
Mount count:              1
Maximum mount count:      -1
Last checked:             Fri Sep 25 23:11:18 2015
Check interval:           0 (<none>)
Lifetime writes:          933 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
First orphan inode:       16191443
Default directory hash:   half_md4
Directory Hash Seed:      e80e781c-ee8f-4a36-89cc-47f28c5abd8c
Journal backup:           inode blocks

```

```
sheriff@xps-linux:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda10 during installation
UUID=b59e369b-42c8-4f85-8a2c-dcfec0657d88 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=AEB9-FE18  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sda8 during installation
UUID=a9a9421b-610c-4503-a114-763ed97f1fbe /home           ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=ff91bc8d-f7ef-4650-80e0-608068f4f8cb none            swap    sw              0       0

# the follwoing lines added by mp035
//192.168.2.10/users /media/mybook cifs uid=1000,gid=1000,credentials=/home/sheriff/.smbcredentials,iocharset=utf8,sec=ntlm,user,noauto 0 0 

```

---

### Post by oldfred on 2015-09-25
I do not see a difference there to mine.
Other than your count is 1, which means it is being checked every time. My count is 262.

There must be something else.
Is system shutting down normally?
Do you have a cron task running fsck or something related that causes it?

---

### Post by sheriff-pointing on 2015-09-25
It shuts down normally (ie. menu->Shutdown Icon->ok).
I have only recently installed Ubuntu, it is a stock install, no special features at all, this is what has me stumped, the system reports no faults at all, but every boot it checks the file system.

The only clue is that if I shutdown, boot into windows, then shut down, the next boot into Ubuntu doesn't check the disk.

EDIT: Also, I have checked for a forcefsck file in both home and root.  Nothing.

---

### Post by oldfred on 2015-09-26
Try running chkdsk from Windows on the efi partition.

Or this, from live installer, your efi partition will be mounted in your install:
       sudo /sbin/fsck.vfat -V <the fat32 device>
or
sudo fsck -t vfat /dev/sda1

 Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit

---

### Post by sheriff-pointing on 2015-10-01
Hi again OldFred,
Sorry it took me so long to get back to you.  I have applied the latest kernel update, but the problem persists.

I tried your suggestion on the EFI partition, but it showed no errors:

```
sheriff@xps-linux:~$ sudo dosfsck -tr /dev/sda1
fsck.fat 3.0.27 (2014-11-12)
/dev/sda1: 342 files, 13940/126976 clusters
sheriff@xps-linux:~$
```

I used 'r' instead of 'aw' so that it would report any errors.  It checks /boot/efi (vfat) and /home (ext4) according to the boot log in my OP.

---

### Post by oldfred on 2015-10-01
I would include the -a on the dosfsck.

I might try the full e2fsck on /home also, but I am grasping at straws.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

