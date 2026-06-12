---
title: "zero free space - zero still available after files deleted"
date: 2016-04-08
forum: General Help
---

### Post by JamButty on 2016-04-08
System (14.04) was unable to complete login. Accepted correct password, then hung. Via livedisk I see that partition is listed as free space=0. I copied some files from there onto an external HD, then deleted 5GB of files (rm). Confirmed thru terminal (ls) and gui file manager that those files were deleted, but that partition still shows as zero free space.

Df output looks like this

> df -h /media/ubuntu/96a6d7c5-db48-45e7-9da0-dceab06ce2a9
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6       886G  881G     0 100% /media/ubuntu/96a6d7c5-db48-45e7-9da0-dceab06ce2a9


It appears to show 5 GB not used (I deleted 5 GB), but zero available. How do i get space obtained thru deleting files to become available (via livedisk)
I am guessing the lack of free space is what is preventing the completion of the login, but that is just a guess. It still hangs.

---

### Post by frostschutz on 2016-04-08
If your root reserve is larger than 5GB and it was used up, then it would still show 0 free after deleting 5GB of files, because it's still reserved for root. You can check the size of the root reserve using `tune2fs -l /dev/thing`. By default it is 5% which is a bit much for very large filesystems. It can be changed with `tune2fs -m`

Apart from that, if any process is still using the deleted files, the space is not freed.

You can check where the most space is wasted using xdiskusage. Example for the root partition /

```

sudo mount --bind / /mnt/root
sudo xdiskusage /mnt/root/

```

xdiskusage is a very old program but I still prefer it over newer alternatives. But if you prefer newer ones you might want to have a look at baobab.

---

### Post by JamButty on 2016-04-08
I need to amend those commands to address the partition in question (/media/ubuntu/96a6d7c5-db48-45e7-9da0-dceab06ce2a9) from the livedisk system, but it not clear to me how. I tried tune2fs and got
> tune2fs -l /media/ubuntu/96a6d7c5-db48-45e7-9da0-dceab06ce2a9
tune2fs 1.42.9 (4-Feb-2014)
tune2fs: Attempt to read block from filesystem resulted in short read while trying to open /media/ubuntu/96a6d7c5-db48-45e7-9da0-dceab06ce2a9
Couldn't find valid filesystem superblock.


I will continue deletions and see if anything moves over to "available"

---

### Post by JamButty on 2016-04-08
ok if I understand the below tune2fs output, the root reserve is  11788736 blocks and free blocks are  1353769.
Current  state is
> Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6       886G  871G     0 100% /media/ubuntu/96a6d7c5-db48-45e7-9da0-dceab06ce2a9


so I have deleted 15 GB and still zero available. Since I am on the livedisk system, I don't think any of the files on that partition could be in use. If 15GB only comes to 1.3M blocks and I need 11.7M blocks to meet root reserve, I'm not gonna get there unless I can find some insanely huge garbage file(s) I can delete.
>  sudo tune2fs -l /dev/sda6
tune2fs 1.42.9 (4-Feb-2014)
Filesystem volume name:   <none>
Last mounted on:          /media/ubuntu/96a6d7c5-db48-45e7-9da0-dceab06ce2a9
Filesystem UUID:          96a6d7c5-db48-45e7-9da0-dceab06ce2a9
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              58949632
Block count:              235774720
Reserved block count:     11788736
Free blocks:              1353769
Free inodes:              33629398
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      967
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Tue Feb  2 07:16:32 2016
Last mount time:          Fri Apr  8 19:57:05 2016
Last write time:          Fri Apr  8 19:57:05 2016
Mount count:              8
Maximum mount count:      -1
Last checked:             Wed Mar 30 23:50:20 2016
Check interval:           0 (<none>)
Lifetime writes:          15 TB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      37726c7b-c0f8-4dec-ac7d-118f0649c68d
Journal backup:           inode blocks


---

### Post by grahammechanical on 2016-04-08
Are you deleting files from /home? That may not alter things for /

At boot menu>Advance options for Ubuntu>recovery mode>recovery menu>clean - Try to make free space. That will run 2 commands - clean & autoremove. It may remove some old kernels. You can also go to Root shell prompt and run apt-get update & apt-get upgrade and that may list packages that are no longer required and that can be removed with autoremove.

With Ubuntu 14.04 you may find that autoremove only removes one kernel for every time it is run. Also, once you have run Clean or fsck or dpkg or network the file system will be put into read/write mode. Now you can go to Root shell prompt and remove some applications such as games. If you think that will help. To get back to the recovery menu type exit.

There is another solution. Enlarge the partition.

Regards.

---

### Post by JamButty on 2016-04-09
I tried the recovery menu path a few days back. Can't remember if it pulled an error or just did not yield any space, did not work in any event.

I had no luck with baobab or xdiskusage. I was getting some useful feedback from
>  du -h --threshold=100000000 /media/ubuntu/96a6d7c5-db48-45e7-9da0-dceab06ce2a9 | more


but did not find anything out of the ordinary in those directories I had permission for. Adding sudo to that line causes it to hang. There is/are either some monster garbage file(s) or some kind of corruption as that partition is nearly a TB and was about 90% free space. I ran a disk cleanup program with free space overwrite (bleachbit) before this problem occurred. There was no error display in the program, but given the timing that is the likely source of the problem.
I will try the sudo du and let it run overnight.

---

### Post by pqwoerituytrueiwoq on 2016-04-09
in my exp every time i ran out of disk space it was in root cause of either massive log files or too many kernels i just reboot after cleaning up space, i know there should be a cleaner way to get the system to see the free space

---

### Post by JamButty on 2016-04-09
overnight sudo du brought nothing -I could hear the system crunching away all night, but it was hung and screen display could not return, so just had to power if off.  The partition fix problem is not with Ubuntu, which I can always reinstall, but with a Win10 on the other partition that I would be taking from. The pre-installed system plopped an unmovable set of system blocks right in the middle of the drive. The Linux partition already abuts those now and can't move further out. I have no way to reinstall the Windoze.

---

### Post by JamButty on 2016-04-09
From recovery on normal system, root option, I uninstalled all user-installed programs. That only got me about 1 GB. If the root reserve=5% holds then I need about 45GB more freed up and my total user files are less than that. Throwing in the towel. Made hopefully valid copies of user files to external HD formatted to EXT4 with cp -prv. Wiping and reinstalling, once again.

---

