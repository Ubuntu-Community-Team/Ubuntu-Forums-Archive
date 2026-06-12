---
title: "System Monitor Discrepancy"
date: 2018-02-09
forum: General Help
---

### Post by typos1 on 2018-02-09
In system monitor "free" space and "available" space have always been the same on my system, but since upgrading to17.10, I have about 6Gb listed as "free" and only 200Mb listed as "available". 

I thought maybe the system had been re-partitioned after the upgrade as I d read that 17.10 doesnt use swap anymore, but gparted says theres still a swap partition of the same size it was before. 

I should have about 6Gb available. Can anyone tell me whats causing this ? Thanks

---

### Post by TheFu on 2018-02-10
df -Th ?  Some file systems (cough ... btrfs) don't tell the truth about their space use.

---

### Post by vasa1 on 2018-02-10
And what does```
sudo fdisk -l
```show?

---

### Post by typos1 on 2018-02-10
The output of "sudo fdisk -l" is :


```
Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1050623   1048576   512M EFI System
/dev/sda2    1050624 219351039 218300416 104.1G Linux filesystem
/dev/sda3  219351040 234440703  15089664   7.2G Linux swap
```


But that doesnt realy help - its exactly as I expected - 512 for boot, 7Gb for swap and the rest for use. 

I should have about 6Gb free, its like something is with holding it and not making it available for some reason.

"df-Th" just gives an error message.

---

### Post by TheFu on 2018-02-10
> **typos1 said:**
>  
"df-Th" just gives an error message.

Because it is missing a space?  df is the command.  -Th are the options.

---

### Post by typos1 on 2018-02-10
Oops, soz.

The output is

```
~$ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.5G     0  7.5G   0% /dev
tmpfs          tmpfs     1.5G  9.9M  1.5G   1% /run
/dev/sda2      ext4      103G   97G  310M 100% /
tmpfs          tmpfs     7.5G   43M  7.4G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.5G     0  7.5G   0% /sys/fs/cgroup
/dev/sda1      vfat      511M  4.7M  507M   1% /boot/efi
tmpfs          tmpfs     1.5G   16K  1.5G   1% /run/user/128
tmpfs          tmpfs     1.5G  184K  1.5G   1% /run/user/1000
```

But all it does it confirm the discrepancy on sda2, it doesnt help me find out what it is and how to sort it, unless I m missing something.

---

### Post by TheFu on 2018-02-10
Now that we've confirmed the type of file system (not btrfs or zfs) ...

An OS drive with less than 1G of free storage will be an issue for any modern computer.
It is common practice to withhold a few % (default is 5%) for root only access.  This is to prevent the file system from filling completely, which WILL CAUSE a system crash.

You can see the actual amounts using tune2fs.

```
$ sudo tune2fs -l /dev/sda2
```
Look at the *Reserved block count*.

For non-OS drives, 5% isn't needed, so changing it is a reasonable practice, especially on 2TB+ disks.  5% is huge on those.

If that doesn't match up with what you are seeing ... we can look farther. I'd guess it is drive fragmentation in that case.  The solution for that is to use a file-system based backup and restore process, so that allocated block waste is minimized.

---

### Post by typos1 on 2018-02-10
> **TheFu said:**
> Now that we've confirmed the type of file system (not btrfs or zfs) ...

An OS drive with less than 1G of free storage will be an issue for any modern computer.
It is common practice to withhold a few % (default is 5%) for root only access.  This is to prevent the file system from filling completely, which WILL CAUSE a system crash.

You can see the actual amounts using tune2fs.

```
$ sudo tune2fs -l /dev/sda2
```
Look at the *Reserved block count*.

For non-OS drives, 5% isn't needed, so changing it is a reasonable practice, especially on 2TB+ disks.  5% is huge on those.

If that doesn't match up with what you are seeing ... we can look farther. I'd guess it is drive fragmentation in that case.  The solution for that is to use a file-system based backup and restore process, so that allocated block waste is minimized.

I had approx 6Gb of free space that also showed as "available", then suddenly for no apparent reason approx 6Gb is showing as "free" but not "available". I have effectively lost 6Gb. 

In all the time I ve used Ubuntu "free" was always "available". 

I always monitor my available space, but, on occasion there have been situations (maybe I forgot about a large file somewhere) where I have 0bytes left and I have to delete something, I ve never had this 5% thing.

I recently upgraded to 17.10 and it was after about a day that this 6Gb became unavailable, could it be something to do with the update ?

```
tune2fs 1.43.5 (04-Aug-2017)
Filesystem volume name:   <none>
Last mounted on:          /
Filesystem UUID:          1710be8d-b4ba-497d-b46a-585e827333b2
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              6823936
Block count:              27287552
Reserved block count:     1364377
Free blocks:              1450153
Free inodes:              6514918
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1017
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Sat Nov 21 21:27:52 2015
Last mount time:          Sat Feb 10 11:22:11 2018
Last write time:          Sat Feb 10 11:22:11 2018
Mount count:              391
Maximum mount count:      -1
Last checked:             Tue May  2 15:00:26 2017
Check interval:           0 (<none>)
Lifetime writes:          5423 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
First orphan inode:       791399
Default directory hash:   half_md4
Directory Hash Seed:      028c5a6b-fdb8-4961-b434-41f5beaecb29
Journal backup:           inode blocks
```

---

### Post by TheFu on 2018-02-10
The system is using 4K blocks and there are 1364377 blocks reserved .... the math says that is 5.3G reserved.  Seem about right to you or is my math wrong?

BTW, reserving 5% by default has been around since at least 1991. It isn't new.

---

### Post by typos1 on 2018-02-10
> **TheFu said:**
> The system is using 4K blocks and there are 1364377 blocks reserved .... the math says that is 5.3G reserved.  Seem about right to you or is my math wrong?

BTW, reserving 5% by default has been around since at least 1991. It isn't new.

Well, it may have been around since 1991 but since 2009 it has never affected any of my Ubuntu installs apart from this update within the last few days and even then it didnt affect it at first. 

Is it somehow made available if space gets low ? And at what point ? Cos I only have 300mb available at the moment and its gone as low as 0bytes since this 6Gb has been taken away from me so I really dont see the point of it being "reserved" if its not going to be made available when the available space gets low.

I dont want to be nannied by my OS - can you tell me how I can revert to the way its always been for me ? Thanks

---

### Post by TheFu on 2018-02-10
tune2fs.

---

### Post by typos1 on 2018-02-10
Thanks. 

tune2fs -r ? 

Will this stop it happening in future ?

---

### Post by TheFu on 2018-02-10
tune2fs manages the settings for 1 file system.  That is either a partition or a logical volume if you use LVM.

The default settings were set using newfs or mkfs during the install.
If you add more disks manually, when you manually run mkfs, it will reserve 5% too.  I have no idea how to change the defaults at install time - perhaps "do something else" in the storage area has a method deeep deeeeeeep deeeeeeeeeep buried in the options?  If you manually add another disk, after you partition it, when you run mkfs, you can modify the options at that point.

The defaults are based on the size of the file system.  So if you have 1 large file system, more storage is reserved.  I generally setup / with 25G or less, so the amount reserved isn't much.  This is a best practice, BTW.  Separate / for the OS and apps.

BTW, every Unix/Linux system does this reserved blocks thing.

You are noticing it for a few reasons.
* 100+G of 4K blocks; 5% of 4K blocks is 8x more storage than 5% of 512b blocks.
* Only 1 partition.

---

### Post by typos1 on 2018-02-10
> **TheFu said:**
> tune2fs manages the settings for 1 file system.  That is either a partition or a logical volume if you use LVM.

The default settings were set using newfs or mkfs during the install.
If you add more disks manually, when you manually run mkfs, it will reserve 5% too.  I have no idea how to change the defaults at install time - perhaps "do something else" in the storage area has a method deeep deeeeeeep deeeeeeeeeep buried in the options?  If you manually add another disk, after you partition it, when you run mkfs, you can modify the options at that point.

The defaults are based on the size of the file system.  So if you have 1 large file system, more storage is reserved.  I generally setup / with 25G or less, so the amount reserved isn't much.  This is a best practice, BTW.  Separate / for the OS and apps.

BTW, every Unix/Linux system does this reserved blocks thing.

You are noticing it for a few reasons.
* 100+G of 4K blocks; 5% of 4K blocks is 8x more storage than 5% of 512b blocks.
* Only 1 partition.

As I said, none of my ubuntu installs since 2009 have had this behaviour before and I have ALWAYS been able to use ALL my storage even if it results in 0bytes left on the disk.

AFAIK upgrading to 17.10 would not have re-partitioned my system (the swap partition is still there), so, unless the upgrade 17.10 somehow changed some settings somewhere to make the available free space unavailable, the settings would have been set when I installed 15.10. 2 years ago and up until a few days ago I could use ALL my available storage.

This was a fresh install 2 years ago and its only started show 6Gb f my free space as unavailable 24 hours after updating to 17.10.

I cant see the point of reserving 5% if it is not going to be used even when disk space is very low, all this does is render my hard drive 5% smaller for no good reason.

I have never manually added extra disks, I have never had more than 1 user partition.

So what you are telling me totally contradicts my 9 years experience of using Ubuntu.

All I want is to have all my free storage available as I always have had.

---

### Post by TheFu on 2018-02-10
I'm very sorry that your beliefs and the facts that I've known for 20+ yrs don't align.

Good luck to you.

---

### Post by typos1 on 2018-02-10
> **TheFu said:**
> I'm very sorry that your beliefs and the facts that I've known for 20+ yrs don't align.

Good luck to you.

Is not a question of "beliefs" - for 9 years I have always been able to use ALL of my available disk space, so someone telling me that I ve actually been imagining it is not going to go down well, is it ?

I came on here for help, not to be told that I ve been imagining things for 9 years.

If you cant offer help or an explanation for this sudden change in Ubuntu's behaviour without an attitude, please dont bother to reply.

---

