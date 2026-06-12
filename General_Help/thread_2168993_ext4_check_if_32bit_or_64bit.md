---
title: "ext4 check if 32bit or 64bit"
date: 2013-08-20
forum: General Help
---

### Post by osure on 2013-08-20
Hello,

Can anybody tell me how to see/check whether an already created ext4 is in 32bit or 64bit mode?

I recently run into the ext4 32bit limit (see: [http://blog.ronnyegner-consulting.de/2011/08/18/ext4-and-the-16-tb-limit-now-solved/](http://blog.ronnyegner-consulting.de/2011/08/18/ext4-and-the-16-tb-limit-now-solved/))
I DO have the line
 auto_64-bit_support = 1
in my mkfs.conf in the ext4 section, and i am quite sure that the filesystem in question was created on this machine/system.
Also I have e2fstools 1.42.

Where can I see this information? is it visible somewhere in the output of dumpe2fs? Is there any other way to get information on an ext4 FS?


This is what dump2fs tells me (at least the beginning, didn't wait for it to complete...):

```
$ sudo dumpe2fs /dev/mapper/raid

dumpe2fs 1.42 (29-Nov-2011)
Filesystem volume name:   <none>
Last mounted on:          /DRIVES/raid
Filesystem UUID:          13017c41-adaa-4683-bb5e-674d4d6c46ec
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              457834496
Block count:              3662666368
Reserved block count:     36626662
Free blocks:              46300852
Free inodes:              445840337
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      150
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         4096
Inode blocks per group:   256
RAID stride:              128
RAID stripe width:        512
Flex block group size:    16
Filesystem created:       Wed Nov 14 22:26:01 2012
Last mount time:          Mon Aug 19 06:14:08 2013
Last write time:          Mon Aug 19 06:14:22 2013
Mount count:              22
Maximum mount count:      -1
Last checked:             Sat Dec 29 18:15:16 2012
Check interval:           0 (<none>)
Lifetime writes:          13 TB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      34d8f481-fb66-4e1a-ab3f-76f34ffd9ad7
Journal backup:           inode blocks
Journal features:         journal_incompat_revoke
Journal size:             128M
Journal length:           32768
Journal sequence:         0x000285f9
Journal start:            0
```

---

### Post by slickymaster on 2013-08-20
At a terminal window run:```
getconf LONG_BIT
```See ```
man getconf
```

---

### Post by osure on 2013-08-20
I do not want to know whether my operating system is a 32 or 64 bit one (it is the 64 bit kubuntu 12.04).
I want to knwo how to check whether a freshly created EXT4 FILE SYSTEM was REALLY created using the ext4 64bit option.

---

### Post by slickymaster on 2013-08-20
Sorry, I misread your question.

Information about mounted ext4 file systems can be found in **/proc/fs/ext4**.  Each mounted filesystem will have a directory in **/proc/fs/ext4** based on its device name (i.e., **/****proc/fs/ext4/sda1**, **/proc/fs/ext4/sda2**).

_EDIT:_ 
See this: [https://www.kernel.org/doc/Documentation/filesystems/ext4.txt](https://www.kernel.org/doc/Documentation/filesystems/ext4.txt)

---

### Post by Bucky Ball on 2013-08-20
An EXT4 partition formatted to 64bit or 32bit partitions? Never heard of it. An EXT4 partition is an EXT4 partition, not EXT4 32bit or anything else.

EXT* partitions, access them from a 32bit or 64bit Linux operating system. You might find this of interest:

[https://ext4.wiki.kernel.org/index.php/Ext4_Howto#Bigger_File_System_and_File_Sizes](https://ext4.wiki.kernel.org/index.php/Ext4_Howto#Bigger_File_System_and_File_Sizes)

Not that it has anything to do with *formatting* an EXT4 partition to 64bit but might help clarify what exactly you are trying to do. Are you talking about whether EXT4 has the capabilities of taking full advantage of 64bit hardware and OS?

---

### Post by Cheesemill on 2013-08-20
I'm interested in this myself as I know that ext4 partitions created using the 32-bit version of e2fsprogs have a 16TB limit and I'm about to create a filesystem on an array larger than that.

I've had a look myself but haven't found any definite information so far, just letting you know that it's something I'm looking into as well.

---

### Post by osure on 2013-08-20
@slickymaster:
thanks a lot, i will try this asap and report back.

@BuckyBall:
No, this is not about taking advantage of a 64bit operating system. This is about the 16TB limit that de facto exists with etx4, due to some default 32 bit inodes issue.
Please read (or at least have a brief look at) the link in my very first post, it will clarify the matter.

---

### Post by osure on 2013-08-20
@Cheesemill: be very careful when creating your file system!
As I mentioned in the first post, I am very confident of having created my ext4 with e2fsprogs version 1.42 AND with the auto_64-bit_support = 1 option in mkfs.conf. And yet it has the 16TB limitation.

---

### Post by Bucky Ball on 2013-08-20
> **osure said:**
> 
@BuckyBall:
No, this is not about taking advantage of a 64bit operating system. This is about the 16TB limit that de facto exists with etx4, due to some default 32 bit inodes issue.


In that case, I guessed right and the link in my last post will be of some interest to you.

---

### Post by osure on 2013-08-20
@slickymaster:
thank you very much, I was not really aware of the option of getting info on filesystems in the /proc structure...
Unfortunately, though, it does not really seem to solve my question:

```
$ mount
/dev/sdi2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
rpc_pipefs on /run/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
/dev/mapper/decrypted on /DRIVES/raid type ext4 (rw)
/$ ls /proc/fs/ext4/
dm-0  sdi2
$ ls /proc/fs/ext4/dm-0/
mb_groups
```

Is there information on the 32bit/64bit addressing issue somewhere in there?

---

### Post by osure on 2013-08-20
@Bucky Ball:
yes, thanks, you did guess right, the link is of some interest.

However, while the explanation on the block addressing might be correct, it is far, far from comprehensive.
The main problem here is that the section seems to suggest that ext4 AUTOMATICALLY uses this 48bit mode. This is definitely not true, it is not the default setting for ext4 to use the 48bit addressing mode. It is not even easy to take advantage of it, actually, when creating (formatting) a ext4 FS. At least I seem to have failed.

Also, I am not sure whether the 48-instead-of-64-bit statement is still valid (I did not really bother to compare revisions to find out the age of the according section). But then again, I don't really care, 1 Eib would be fine by me.

---

### Post by djdb2 on 2014-03-19
You can determine this with tune2fs -l or dumpe2fs -h

[root@bkp1 ~]# /opt/e2fsprogs/sbin/tune2fs -l /dev/mapper/vg_bkp1_2-lv_storage2 | grep 'Filesystem features'
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent **64bit** flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize

[root@bkp1 ~]# /opt/e2fsprogs/sbin/tune2fs -l /dev/mapper/vg_bkp1-lv_storage1 | grep 'Filesystem features'
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize

[root@bkp1 ~]# /opt/e2fsprogs/sbin/tune2fs -v
tune2fs 1.43-WIP (4-Feb-2014)





Be aware with version of e2fsprogs you use:
[root@bkp1 ~]# tune2fs -l /dev/mapper/vg_bkp1_2-lv_storage2
tune2fs: Filesystem has unsupported feature(s) while trying to open /dev/mapper/vg_bkp1_2-lv_storage2
Couldn't find valid filesystem superblock.
[root@bkp1 ~]# tune2fs --version
tune2fs 1.41.12 (17-May-2010)

---

