---
title: "resize2fs seems to do nothing but use cpu"
date: 2014-05-19
forum: General Help
---

### Post by joerg_ac on 2014-05-19
Hi,

I hope somebody can help me with an issue I have rezising a filesystem using resize2fs with ubuntu 14.04. I am extending a RAID 6 using mdadm. I did add 2 additional disks which did extend the array size from 20TB to 28TB. Reshaping the array has finished without problems. Now I have started resize2fs for having the ext4 filesystem using all 28TB.
The command used is: 

```
root@marvin:~# resize2fs -f -S 128 /dev/md2
resize2fs 1.42.9 (4-Feb-2014)
```

The problem is that it stays like this for hours without any output from resize2fs like for example status updates.
Nevertheless top shows the resize2fs process using 99% CPU. Its memory consumption is quite small and constant.
I use online resize now, but it is the same with offline resize.

I did a filesystem check before running the resize. 

As it is online resize I would expect that df would show continuous increase of size, but it does not show any changes.

I also tried and offline resize with the -p option, but also without any status output being provided. 

dmesg does not show anything related. 

This are the details of the underlying raid:

```
root@marvin:~# mdadm --detail /dev/md2
/dev/md2:
        Version : 1.2
  Creation Time : Fri Sep 20 18:11:23 2013
     Raid Level : raid6
     Array Size : 27348195840 (26081.27 GiB 28004.55 GB)
  Used Dev Size : 3906885120 (3725.90 GiB 4000.65 GB)
   Raid Devices : 9
  Total Devices : 9
    Persistence : Superblock is persistent

    Update Time : Tue May 20 03:47:32 2014
          State : clean 
 Active Devices : 9
Working Devices : 9
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : marvin:2  (local to host marvin)
           UUID : c1ec13d3:329cdde8:abd3d14e:53a8f84c
         Events : 4037970

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8       65        1      active sync   /dev/sde1
       2       8       81        2      active sync   /dev/sdf1
       3       8       97        3      active sync   /dev/sdg1
       4       8      113        4      active sync   /dev/sdh1
       6       8       33        5      active sync   /dev/sdc1
       7       8       17        6      active sync   /dev/sdb1
       9       8      161        7      active sync   /dev/sdk1
       8       8      145        8      active sync   /dev/sdj1

```


The following is some information about the filesystem:

```
root@marvin:~# tune2fs -l /dev/md2
tune2fs 1.42.9 (4-Feb-2014)
Filesystem volume name:   data
Last mounted on:          /media/data01
Filesystem UUID:          e3845e15-0336-47ae-8aec-df75acb217c5
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent 64bit flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              305225728
Block count:              4883606400
Reserved block count:     0
Free blocks:              22919919
Free inodes:              302894731
First block:              0
Block size:               4096
Fragment size:            4096
Group descriptor size:    64
Reserved GDT blocks:      1024
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         2048
Inode blocks per group:   128
RAID stride:              128
RAID stripe width:        640
Flex block group size:    16
Filesystem created:       Fri Sep 20 19:45:01 2013
Last mount time:          Tue May 20 02:14:37 2014
Last write time:          Tue May 20 02:14:37 2014
Mount count:              3
Maximum mount count:      -1
Last checked:             Tue May 20 01:34:05 2014
Check interval:           0 (<none>)
Lifetime writes:          34 TB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      569ec5fc-4d5e-4639-bef3-42cde5fbe948
Journal backup:           inode blocks
```

So the filesystem was created above the 16TB limit and with the respective 16TB support.

The system is an i7 with 32 GB RAM. So I guess there are sufficient processing and memory resources.

So to me it looks like resize2fs is calcualting something and got stuck while still using all available cpu, but it is not really performing the wanted resize. I would highly appreciate some hints of what might be the problem or what I should check.

best regards, Joerg

---

### Post by joerg_ac on 2014-05-20
Hi again,

To complete the picture, here is also the output of the filesystem check.

```
root@marvin:~# e2fsck -vfp /dev/md2
                    
     2330890 inodes used (0.76%, out of 305225728)
       14882 non-contiguous files (0.6%)
         949 non-contiguous directories (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 2317190/13041/651
  4868171016 blocks used (99.68%, out of 4883606400)
           0 bad blocks
        1654 large files

     2273776 regular files
       57105 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
           0 symbolic links (0 fast symbolic links)
           0 sockets
------------
     2330881 files
```

I hope somebody has an Idea what could be the problem.

---

### Post by joerg_ac on 2014-05-21
Hi Again,

I downgraded to the earlier version 1.42.8 of e2fsprogs  and then it worked. The 1.42.9 version seems to have a problem at least  with the kernel version of Ubuntu 14.04. 

best regards, Joerg

---

### Post by M_D on 2014-05-21
I am having the same problem, [http://ubuntuforums.org/showthread.php?t=2224488&p=13025489#post13025489](http://ubuntuforums.org/showthread.php?t=2224488&p=13025489#post13025489), what did you do to downgrade?  Also, did you just kill the process?

---

### Post by joerg_ac on 2014-05-21
Hi M_D,

look at this forum thread:
[http://hardforum.com/showthread.php?t=1819418](http://hardforum.com/showthread.php?t=1819418)
I also described my problem there and got many replies, some discussion on filesystems and finally the right hint. I also summarized there what I did. I guess however, there might be some dangers involved in the process.

I have also reported a bug to Ubuntu:
[https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/1321958](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/1321958)

If you are confident that you have the same problem it might be a good idea to report a "me too" of that bug to show that actually multiple users are effected. 

Yes, I did either kill the process or just pressed ctrl-c in the terminal. The command seemed to be stuck before it actually changes anyting in the filesystem. 

best regards, Joerg

---

### Post by M_D on 2014-05-21
Yeah, I came across your bug report and did post on there the 'me too'.  One thing that I noted, was that I didn't have this problem with a raid 5 array just after I changed it to a raid 6.  I did end up doing what you did, but I didn't remove the installed one, i just downloaded the tar.gz and compiled it.  When I do apt echo it still says 1.42.9 but 1.42.8 runs.

---

