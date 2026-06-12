---
title: "Can't delete or copy files from external hard drive"
date: 2021-04-04
forum: General Help
---

### Post by Brent_Santin on 2021-04-04
I use an external hard drive to backup my computer to. It's always been reliable.
A few days ago I tried to copy some of the backup files to another external hard drive I got from work. This operation failed (I think there's something wrong with and "Acess Denied" tp that latter drive half way through copying).
Now I cannot delete or copy files from the first, normally reliable drive. I've tried plugging the drive into two different computers running Linux and both reported the same problem
I *can* however write a file to the drive and delete it.

Also, Clonezilla started from a live DVD seems to be able to write to it.

I have no idea what is wrong with the drive, but here is the output of "mount" with the drive plugged in. The drive is sdg1 "Elements":

```

brent@tower-i5:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,noexec,relatime,size=3974244k,nr_inodes=993561,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,noexec,relatime,size=804584k,mode=755)
/dev/sda3 on / type ext4 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup2 on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
none on /sys/fs/bpf type bpf (rw,nosuid,nodev,noexec,relatime,mode=700)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=21142)
mqueue on /dev/mqueue type mqueue (rw,nosuid,nodev,noexec,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
debugfs on /sys/kernel/debug type debugfs (rw,nosuid,nodev,noexec,relatime)
tracefs on /sys/kernel/tracing type tracefs (rw,nosuid,nodev,noexec,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,nosuid,nodev,noexec,relatime)
configfs on /sys/kernel/config type configfs (rw,nosuid,nodev,noexec,relatime)
/var/lib/snapd/snaps/core18_1997.snap on /snap/core18/1997 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core18_1988.snap on /snap/core18/1988 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_10908.snap on /snap/core/10908 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gtk2-common-themes_13.snap on /snap/gtk2-common-themes/13 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_1514.snap on /snap/gtk-common-themes/1514 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-34-1804_66.snap on /snap/gnome-3-34-1804/66 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/kompozer_4.snap on /snap/kompozer/4 type squashfs (ro,nodev,relatime,x-gdu.hide)                                                                                         
/var/lib/snapd/snaps/protracker_125.snap on /snap/protracker/125 type squashfs (ro,nodev,relatime,x-gdu.hide)                                                                                 
/var/lib/snapd/snaps/puddletag-snap_3.snap on /snap/puddletag-snap/3 type squashfs (ro,nodev,relatime,x-gdu.hide)                                                                             
/var/lib/snapd/snaps/snapd_11402.snap on /snap/snapd/11402 type squashfs (ro,nodev,relatime,x-gdu.hide)                                                                                       
/var/lib/snapd/snaps/kde-frameworks-5-core18_32.snap on /snap/kde-frameworks-5-core18/32 type squashfs (ro,nodev,relatime,x-gdu.hide)                                                         
/var/lib/snapd/snaps/youtube-dl_3805.snap on /snap/youtube-dl/3805 type squashfs (ro,nodev,relatime,x-gdu.hide)                                                                               
/var/lib/snapd/snaps/synfigstudio_2.snap on /snap/synfigstudio/2 type squashfs (ro,nodev,relatime,x-gdu.hide)                                                                                 
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)                                                       
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=804580k,mode=700,uid=1000,gid=1001)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1001)
/dev/sdg1 on /media/brent/Elements type ext4 (rw,nosuid,nodev,relatime,uhelper=udisks2)
/dev/sdb1 on /media/brent/Media_Drive type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)

```

---

### Post by TheFu on 2021-04-04
Only need the 1-line for the specific partition mounted:
```
/dev/sdg1 on /media/brent/Elements type ext4 (rw,nosuid,nodev,relatime,uhelper=udisks2)
```

Check the file/directory permissions.  
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://www.psychocats.net/ubuntu/permissions](https://www.psychocats.net/ubuntu/permissions)

There's no way to avoid learning these, so take the 30 minutes now, work through a tutorial, and save the hours, days,weeks,months of frustration.

---

### Post by Brent_Santin on 2021-04-04
Okay thanks. 
I did notice I only seem to be able to NOT copy the larger files. And these say some of the perimssions are FORBIDDEN on them and cannot be changed through the GUI.
I'll read the document.

---

### Post by ajgreeny on 2021-04-04
Show us the output of command ```
ls -l /media/brent/Elements
``` as I suspect that partition mount-point is probably owned by root.
If that is the case you will need to run ```
sudo chown -R brent:brent /media/brent/Elements
``` to make you the owner.

However, you say that you are able to write to it which suggests you are owner, and read from it but simply not copy a file from it which seems very unusual.
Try using terminal to copy a file on that partition to somewhere in your home folder with command [copy]cp /media/brent/Elements/**filename** /home/brent[/code] which may give you more of an error that means something.
Use the real name instead of **filename** as I have in my command of course.

---

### Post by Brent_Santin on 2021-04-04
Okay, I will do as ajgreeny suggests in the previous post.

I did some more investigating. It seems this is not a drive corruption error. Clonezilla (backup software that writes to those drives) is doing something to lock the permissions of the larger files in the archive - the files that contain the compressed data.
This makes it difficult for me to delete the folder containing the drive image when the image becomes old and no longer relevant.

---

### Post by TheFu on 2021-04-04
Clonezilla is imaging software, not backup software.   There is a difference.  

Backup software supports versioning, so we can have 20, 50, 180 backup versions with relatively little overhead, usually for less than 2 images in storage used.  Many backup solutions use 30% more for 90-180 days of daily backups - so if the storage to be backed up is 50G, then for 90 days of versioned backups, we'd need 65G.  Just something to consider.

To get a system backup, running as root is required so areas on the file systems only available to root can be included.  It also solves the owner, group, ACL capture issue when files owned by multiple different users are in the backup - say your family shares the same computer and there is 
[LIST]
[*]/home/mom
[*]/home/dad
[*]/home/allison
[/LIST]

to be backed up.  root running the backups will retain the correct permissions, whereas if any other userid is used, then Unix permissions wouldn't allow the owner to be mom, dad, or allison.  This is all standard Unix permissions, so that understanding is worth/necessary to understand to avoid problems later.

---

### Post by Brent_Santin on 2021-04-04
As I said, I'm using a new version of Clonezilla (2.7.x) and it seems to lock permissions on the large archive files within a backup (a drive image).
I've now determined it's not the drive, as I tried Clonezilla on another external drive and the file permission issue is the same (certain large files in the image directory cannot be copied/deleted/etc.).
All I want to do is be able to manually delete or copy a folder containing a drive image.

Here is the output of "ls -l" on one such problematic Clonezilla drive image directory on the external HD:

```

brent@tower-i5:/media/brent/Elements/Lubuntu20^04_backups/2021-04-04-16-img_Lubuntu$ ls -l
total 31757120
-rw-r--r-- 1 root root       1073 Apr  4 12:35 blkdev.list
-rw-r--r-- 1 root root        870 Apr  4 12:35 blkid.list
-rw-r--r-- 1 root root       9823 Apr  4 13:11 clonezilla-img
-rw-r--r-- 1 root root        235 Apr  4 12:54 dev-fs.list
-rw-r--r-- 1 root root          4 Apr  4 12:55 disk
-rw-r--r-- 1 root root       2022 Apr  4 12:55 efi-nvram.dat
-rw-r--r-- 1 root root      21666 Apr  4 13:10 Info-dmi.txt
-rw-r--r-- 1 root root        236 Apr  4 13:11 Info-img-id.txt
-rw-r--r-- 1 root root      26302 Apr  4 13:10 Info-lshw.txt
-rw-r--r-- 1 root root       2274 Apr  4 13:11 Info-lspci.txt
-rw-r--r-- 1 root root       1796 Apr  4 13:11 Info-OS-prober.txt
-rw-r--r-- 1 root root        195 Apr  4 13:11 Info-packages.txt
-rw-r--r-- 1 root root        103 Apr  4 13:11 Info-saved-by-cmd.txt
-rw-r--r-- 1 root root       5288 Apr  4 13:11 Info-smart.txt
-rw-r--r-- 1 root root         20 Apr  4 12:55 parts
-rw------- 1 root root   16458463 Apr  4 12:35 sda1.vfat-ptcl-img.gz.aa
-rw------- 1 root root      73501 Apr  4 12:35 sda2.dd-ptcl-img.gz.aa
-rw------- 1 root root 4096000000 Apr  4 12:37 sda3.ext4-ptcl-img.gz.aa
-rw------- 1 root root 4096000000 Apr  4 12:39 sda3.ext4-ptcl-img.gz.ab
-rw------- 1 root root 4096000000 Apr  4 12:41 sda3.ext4-ptcl-img.gz.ac
-rw------- 1 root root 4096000000 Apr  4 12:43 sda3.ext4-ptcl-img.gz.ad
-rw------- 1 root root 4096000000 Apr  4 12:45 sda3.ext4-ptcl-img.gz.ae
-rw------- 1 root root 4096000000 Apr  4 12:47 sda3.ext4-ptcl-img.gz.af
-rw------- 1 root root 4096000000 Apr  4 12:50 sda3.ext4-ptcl-img.gz.ag
-rw------- 1 root root 3413752090 Apr  4 12:54 sda3.ext4-ptcl-img.gz.ah
-rw------- 1 root root  416766485 Apr  4 12:55 sda4.ntfs-ptcl-img.gz.aa
-rw-r--r-- 1 root root         37 Apr  4 12:35 sda-chs.sf
-rw-r--r-- 1 root root      17408 Apr  4 12:35 sda-gpt-1st
-rw-r--r-- 1 root root      16384 Apr  4 12:35 sda-gpt-2nd
-rw-r--r-- 1 root root      17920 Apr  4 12:35 sda-gpt.gdisk
-rw-r--r-- 1 root root        770 Apr  4 12:35 sda-gpt.sgdisk
-rw-r--r-- 1 root root        512 Apr  4 12:35 sda-mbr
-rw-r--r-- 1 root root        574 Apr  4 12:35 sda-pt.parted
-rw-r--r-- 1 root root        504 Apr  4 12:35 sda-pt.parted.compact
-rw-r--r-- 1 root root        820 Apr  4 12:35 sda-pt.sf
brent@tower-i5:/media/brent/Elements/Lubuntu20^04_backups/2021-04-04-16-img_Lubuntu$ 

```

As you can see, the large files (the compressed data - zip format I believe) have fewer file permissions than the others. The small files I *can* move/copy/delete. It's just the larger ones I cannot and I am unable to change the file permission with the OS gui (i.e. right click on file/permissions tab). It says "Access denied".

Thanks for any help or insight you can provide.

---

### Post by Brent_Santin on 2021-04-04
> **TheFu said:**
> Clonezilla is imaging software, not backup software.   There is a difference.  

Backup software supports versioning, so we can have 20, 50, 180 backup versions with relatively little overhead, usually for less than 2 images in storage used.  Many backup solutions use 30% more for 90-180 days of daily backups - so if the storage to be backed up is 50G, then for 90 days of versioned backups, we'd need 65G.  Just something to consider.

To get a system backup, running as root is required so areas on the file systems only available to root can be included.  It also solves the owner, group, ACL capture issue when files owned by multiple different users are in the backup - say your family shares the same computer and there is 
[LIST]
[*]/home/mom 
[*]/home/dad 
[*]/home/allison 
[/LIST]

to be backed up.  root running the backups will retain the correct permissions, whereas if any other userid is used, then Unix permissions wouldn't allow the owner to be mom, dad, or allison.  This is all standard Unix permissions, so that understanding is worth/necessary to understand to avoid problems later.

Thanks for the clarification. I do make one or two Clonezilla images of the drive when I do a major system update, then use "rsync" to back up the home directory on a more regular basis.

---

### Post by TheFu on 2021-04-04
> **Brent_Santin said:**
> 
```

brent@tower-i5:/media/brent/Elements/Lubuntu20^04_backups/2021-04-04-16-img_Lubuntu$ ls -l
total 31757120
-rw------- 1 root root   16458463 Apr  4 12:35 sda1.vfat-ptcl-img.gz.aa
-rw------- 1 root root      73501 Apr  4 12:35 sda2.dd-ptcl-img.gz.aa
-rw------- 1 root root 4096000000 Apr  4 12:37 sda3.ext4-ptcl-img.gz.aa
-rw------- 1 root root 4096000000 Apr  4 12:39 sda3.ext4-ptcl-img.gz.ab
-rw------- 1 root root 4096000000 Apr  4 12:41 sda3.ext4-ptcl-img.gz.ac
-rw------- 1 root root 4096000000 Apr  4 12:43 sda3.ext4-ptcl-img.gz.ad
-rw------- 1 root root 4096000000 Apr  4 12:45 sda3.ext4-ptcl-img.gz.ae
-rw------- 1 root root 4096000000 Apr  4 12:47 sda3.ext4-ptcl-img.gz.af
-rw------- 1 root root 4096000000 Apr  4 12:50 sda3.ext4-ptcl-img.gz.ag
-rw------- 1 root root 3413752090 Apr  4 12:54 sda3.ext4-ptcl-img.gz.ah
-rw------- 1 root root  416766485 Apr  4 12:55 sda4.ntfs-ptcl-img.gz.aa
brent@tower-i5:/media/brent/Elements/Lubuntu20^04_backups/2021-04-04-16-img_Lubuntu$ 

```

As you can see, the large files (the compressed data - zip format I believe) have fewer file permissions than the others. The small files I *can* move/copy/delete. It's just the larger ones I cannot and I am unable to change the file permission with the OS gui (i.e. right click on file/permissions tab). It says "Access denied".

Thanks for any help or insight you can provide.

You call that a problem, but it isn't.  Those are compressed clones of all the files at the block-level for the partition, split into specific sizes.  Partitions aren't available for the world read for a good reason.  There isn't any use in you having access to those files, unless your goal is to delete them.  If that's the goal, you'll want to delete the entire directory.  Use sudo rm for that.  Be EXTREMELY careful, since a mistake with that command almost ways WILL BE TERRIBLE.

If you want to copy the files, use **sudo** as well and leave them owned by root, so you know to be extra careful with those block files.

---

### Post by Brent_Santin on 2021-04-04
> **ajgreeny said:**
> Show us the output of command ```
ls -l /media/brent/Elements
``` as I suspect that partition mount-point is probably owned by root.

Please see the output of this command in my post a few message back.

> Try using terminal to copy a file on that partition to somewhere in your home folder with command [copy]cp /media/brent/Elements/**filename** /home/brent[/code] which may give you more of an error that means something.
Use the real name instead of **filename** as I have in my command of course.

The output of trying to copy a file from the USB hard-drive was:

```

brent@brent-OptiPlex-GX620:~$ cp /media/brent/Elements/Lubuntu20^04_backups/2021-04-03-18-img_Lubuntu_aftrLowLtcy/sdb1.vfat-ptcl-img.gz.aa /home/brent
cp: cannot open '/media/brent/Elements/Lubuntu20^04_backups/2021-04-03-18-img_Lubuntu_aftrLowLtcy/sdb1.vfat-ptcl-img.gz.aa' for reading: Permission denied
brent@brent-OptiPlex-GX620:~$ 

```

The file I tried to copy was one of the ones that only has the permission flags similar to:

```
-rw------- 1 root root 4096000000 Apr  4 12:37 sda3.ext4-ptcl-img.gz.aa
```

---

### Post by TheFu on 2021-04-04
Try:
```
sudo cp /media/brent/Elements/Lubuntu20^04_backups/2021-04-03-18-img_Lubuntu_aftrLowLtcy/sdb1.vfat-ptcl-img.gz.aa /home/brent
```

But this probably isn't a good idea.  Grabbing just one of those files isn't really useful. You need them all to make the sdb1 "block" file which could be mounted by root and accessed.  If struggling with Unix permissions, manually merging all those .aa, .ab. .ac .... files isn't something you want to tackle without using clonezilla's recovery features.

---

### Post by Brent_Santin on 2021-04-04
> **TheFu said:**
> You call that a problem, but it isn't.  Those are compressed clones of all the files at the block-level for the partition, split into specific sizes.  Partitions aren't available for the world read for a good reason.  There isn't any use in you having access to those files, unless your goal is to delete them.  If that's the goal, you'll want to delete the entire directory.  Use sudo rm for that.  Be EXTREMELY careful, since a mistake with that command almost ways WILL BE TERRIBLE.

If you want to copy the files, use **sudo** as well and leave them owned by root, so you know to be extra careful with those block files.

Okay, thanks for the insight.  I would only ever manipulate these files for two purposes: 


[LIST]
[*]Deleting an out-of-date backup disk image (the entire Clonzilla-created folder containing all the files related to the disk image) so I can free up space on the hard drive to make a new updated disk image or 
[*]To copy that folder containing all files related to the disk image off the drive to a secondary USB backup drive. 
[/LIST]

I would never have a reason to access the files individually. I would only ever be deleting the entire folder created by Clonezilla which contains all the files for a particular disk image.

Could you give me an example of a **sudo rm** and **sudo cp** command so that I can make sure I'm doing it right. I know it might seem pedantic of me to ask, but since I am new to this and I don't want to royally mess things up, I wouldn't mind learning by starting at the basics.
i.e. what would be the commands to copy or delete a folder containing the Clonezilla image if that folder was:
[B]
[FONT=courier new]/media/brent/Elements/Lubuntu20^04_backups/2021-04-04-16-img_Lubuntu/[/FONT][/B]

Also, I would like to understand why this is happening. Do I not have ownership of these folders, as suggested by a poster in a message above?  Who has ownership of the folders then? The Clonezilla Live DVD "user"?

I wonder: if I booted the computer with the Clonezilla Live DVD, and choose to enter a console/terminal/command line within that session, would I have ownership of these folders/files on the external USB hard-drive?

---

### Post by TheFu on 2021-04-04
> **Brent_Santin said:**
>  I wouldn't mind learning by starting at the basics. 

Post #2 has links to understand "the basics" of permissions.  It doesn't appear that you've worked through those.  Please do so. There is a simple elegance to it.

> **Brent_Santin said:**
> Also, I would like to understand why this is happening. Do I not have ownership of these folders, as suggested by a poster in a message above?  Who has ownership of the folders then? The Clonezilla Live DVD "user"? 

They are owned by root - just like the output shows. Work through the links in post #2!

> **Brent_Santin said:**
> I wonder: if I booted the computer with the Clonezilla Live DVD, and choose to enter a console/terminal/command line within that session, would I have ownership of these folders/files on the external USB hard-drive?

Root would have ownership.  I don't use clonezilla, but I can't imagine any way that it doesn't run as root. Most backup tools have to run as root to be effective in multi-user environments like Linux.  Think multi-user.  A user **does not equal** a human.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) has all the stuff you seem to be trying to skip, but it is very important to know.  Almost any Unix book would cover permissions. All Unix is the same when it comes to permissions.  OSX, Linux, Unix, iOS, Android .... all the same.

Good luck to you.

---

### Post by Brent_Santin on 2021-04-04
Okay, I think I have a theory as to what has happened. Look at this directory listing on my external USB backup hard-drive:

```

brent@tower-i5:/media/brent/Elements/Lubuntu20^04_backups$ ls -l
total 24
drwxr-xr-x 2 root  root  4096 Apr  3 07:59 2021-04-03-11-img_Lubuntu_b4LowLtcy
drwxr-xr-x 2 root  root  4096 Apr  3 14:40 2021-04-03-18-img_Lubuntu_aftrLowLtcy
drwxr-xr-x 2 root  root  4096 Apr  4 13:11 2021-04-04-16-img_Lubuntu
drwxrwxrwx 2 brent brent 4096 Mar 28 10:04 Lubuntu_FreshInstall_bkp_img
drwxrwxr-x 3 brent brent 4096 Mar 28 11:10 Home_rsync_bkp
-rwxrwxrwx 1 brent brent  935 Mar 28 09:57 read-me.txt

```

All of the folders that have the word "Lubuntu" in them are "backup images" of my computer's internal hard-drive created with Clonezilla. They were done at various dates and times while I was setting up my new computer and wanted to preserve the state of the drive just before I was about to do something that could potentially mess up the system.

The first one I did on March 28th, just after doing a fresh installation of Lubuntu (folder "**Lubuntu_FreshInstall_bkp_img**").  Now the key here is that I did that one while the external backup USB drive was still formatted with the NTFS file system. You will notice that it has the ownership "**brent**". I believe this is because it was an NTFS drive at the time. I should note that that folder gives me no problems. I can move, copy and delete it or anything within it.

A little while later I wanted to do an "rsync" backup of my home directory to the same external drive. However, I read online that it was better if the destination drive was formatted with the **ext4** file system, so to preserve the special Linux-legal filenames, date stamps, permissions, etc. So at that point I moved the folder "**Lubuntu_FreshInstall_bkp_img**" ***OFF*** the external USB drive and onto my computer's internal hard-drive. I then reformatted the external drive to EXT4 file-system. Finally, I returned "**Lubuntu_FreshInstall_bkp_img**" BACK onto the external USB drive.

Following this I performed the **rsync** backup of my home directory to the external  drive, which you see as a folder called "**Home_rsync_backup**". This folder, too, gives me no  trouble as it has ownership by "**brent**". I can move files off and on, etc. without problem.

**_All subsequent_** Clonezilla images of my computer's drive were save to the external USB hard-drive that had now been formatted with the EXT4 filesystem. These are all the other folders with "Lubuntu" in their names --- and **_all of them have ownership "root"_**! I believe this is because the **EXT4 **filesystem allows Clonezilla to assign (preserve?) ownership of those folders as "**root**" and not "**brent**" (something the NTFS filesystem had previously not permitted - or rather stripped away?).

So as "root" owned folders, I would of course have restricted permissions regarding them if I simply plugged the drive into a session where I was logged in as user "brent". I could not manipulate these root owned folders because of this.

The reason I was so surprised by this behaviour was that during my previous five years of using Clonezilla, I had _**only ever used it with an NTFS formatted**_ external hard drive. Therefore I had never encountered this automatic "root" assignment of folders created by Clonezilla before. 

I think I finally understand why it happened. Does my theory make sense?
I'm still learning about user-permissions in Linux, so please forgive me if this is all basic stuff. It is a revelation for me.

---

### Post by The Cog on 2021-04-05
You are indeed getting the hang of it. Clonezilla runs as root - it has to because only root has the ability to read all the things that are root owned, and you don't want clonezilla to omit things when making a backup.I'm not familiar with clonezilla, but if it is making block-level backups, then is is reading root-only raw disk device interface "files" in /dev. Because it's running as root, the backup files it creates are owned by root.

ntfs cannot store Linux file permissions properties, so yes, it "strips" them. The ownership information is lost.

If you want to copy or edit files that are only readable/writeable by root, prefix the command with "sudo". People often say sudo is "super user do...". It is a direct equivalent of Windows "run as administrator...".

Note the drwxr-xr-x permission markings in the listing. Learing what these mean is a must. It's not that hard, and you will always struggle until you know them. This link [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) that TheFu gives is an excellent resource, but don't try to learn it all because your head will explode. I recommend that you use it for reference and remember the bits that you have to look up that you think will come in handy again. I know some bits well, and I'm sure there are things in there that I don't even know exist.

---

### Post by yancek on 2021-04-05
Windows ntfs filesystem have no concept or understanding of Linux permissions such as "rwx" but rather use default setting with umask, dmask and fmask.  Depending upon those settings, it could be possible for anyone with access to your machine to modify and delete the file on the ntfs partitions.

---

### Post by TheFu on 2021-04-05
There is no way to change from NTFS-->ext4 without formatting that is destructive, so any files or directories on the NTFS partition would be wiped - gone - removed - as part of the process to change to any other file system.  In short, none of the files that were on the NTFS file system made it to the ext4 file system.  So that guess for what happened isn't possible.

Human does not equal userid.  Think multi-user.  Whatever useid a process runs under, that's the owner for any files created by that process (except on NTFS or other file systems that do not support POSIX permissions).

---

### Post by Brent_Santin on 2021-04-05
Thanks guys. I was able to copy the files I needed off the drive and delete the out of date backup disk images using "sudo rm" and "sudo cp".
I read the documents linked to and now understand how file permission flags work in Linux.
So thank you. I've come out of this experience knowing more than I did when I started this will help me in the future when using Linux.
All the best!

---

