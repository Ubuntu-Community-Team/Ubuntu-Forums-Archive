---
title: "Discrepancy between free space reported by disks tool and other programs"
date: 2021-11-21
forum: General Help
---

### Post by spectatorx on 2021-11-21
I have a weird issue where tools like Disks or Gparted say i have 46GB free space available on my ext4 partition but any other program that can write to disk reports i have just 8GB of free space. All that is after i just removed a folder containing 20GB of data. Yes, i emptied trash. Here is a screenshot as a proof of what i'm experiencing at the moment:
[https://i.imgur.com/BqiEQVz.png](https://i.imgur.com/BqiEQVz.png)

Ubuntu budgie 20.04.3.

So far i did basically all things described in this guide:
[https://ubuntuforums.org/showthread.php?t=1122670](https://ubuntuforums.org/showthread.php?t=1122670)
Problem still occurs.

---

### Post by TheFu on 2021-11-23
What file systems are used for each mount?
The best way to see that information, is with these commands:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

---

### Post by KBar on 2021-11-23
Correct me if I'm wrong. I think this discrepancy is due to how these programs invoke the **stat**(2) system call. There is an apparent size of files, which is reported by **stat --format=%s** and some other commands, and disk usage, which is the number of blocks allocated (minimum 8) times the size in bytes of each block, which is usually 512B on Linux systems.

---

### Post by TheFu on 2021-11-23
> **kbar said:**
> Correct me if I'm wrong. I think this discrepancy is due to how these programs invoke the **stat**(2) system call. There is an apparent size of files, which is reported by **stat --format=%s** and some other commands, and disk usage, which is the number of blocks allocated (minimum 8) times the size in bytes of each block, which is usually 512B on Linux systems.

The difference would be in GiB vs GB, which isn't 4x different.
The blocksize on Linux file systems is usually 512b or 4Kb.  No file will use less than 1 block and if there are millions of tiny files, each will use 1 block.  That is highly unlikely in most real-world situations, so the difference turns out to be not so important.

I'm thinking either some advance volume manager is being used, which du/df don't understand or there could be a mounted partition hiding a bunch of data "under the mount".  If a partition or LV is mounted to a directory, then any data already existing there pre-mount would still use space, but not show up in du, but will show up in df.

---

### Post by KBar on 2021-11-23
> **TheFu said:**
> No file will use less than 1 block and if there are millions of tiny files, each will use 1 block.

To be pedantic, it's actually 8 blocks, 512B each totaling 4096B, though the documentation says blocks are 1024 bytes on new kernels, but yes, files cannot be less than 4096 bytes in size, as you wanted to convey. Anyway, don't programs retrieve this information about available blocks specifically when they want to write? That would partly explain the discrepancy spectatorx was talking about. 

**info du** mentions that it is possible to create files with arbitrary large apparent sizes with zero content. Could that be the case here?

---

### Post by TheFu on 2021-11-23
> **kbar said:**
>  **info du** mentions that it is possible to create files with arbitrarily large apparent sizes with zero content. Could that be the case here?

Creating sparse files isn't something that happens accidentally.  Plus, whenever a sparse file gets copied, the apparent size typically explodes.  There are special options for cp, rsync, and tar to handle sparse files.  If you've ever been burned by these before, you won't forget.  My email server uses a sparse file for the LDAP DB.  
```
-rw------- 1 zimbra zimbra 24516902912 Nov 23 23:13 data.mdb
-rw-r----- 1 zimbra zimbra      561447 Nov 23 03:00 data.mdb.tgz
```

The huge file is a sparse file.  I exclude that file from my backup tool - which has a patch to handle sparse files correctly, but not for all the OSes I use. I backup the tgz file.  Nobody wants to backup 24GB of data when it is only 3MB in reality. 

du reports the correct sizes.
```
$ du -sh da*
2.9M    data.mdb
552K    data.mdb.tgz

```

I'm sure there are great uses for sparse files that make sense, but my example shows just how sometimes they are clearly more trouble than they are worth.

The manpage for cp has this:
```
       By  default,  sparse  SOURCE files are detected by a crude heuristic
       and the corresponding DEST file is made sparse as well.  That is the
       behavior selected by --sparse=auto.  Specify --sparse=always to cre&#8208;
       ate a sparse DEST file whenever the  SOURCE  file  contains  a  long
       enough  sequence  of zero bytes.  Use --sparse=never to inhibit cre&#8208;
       ation of sparse files.
```
The manpage for rsync has this:
```
        -S, --sparse                handle sparse files efficiently
```
The manpage for tar (gnutar) has this:
```
     -S, --sparse
           handle sparse files efficiently
```

I don't think being pedantic is bad, especially when it matters.

---

### Post by KBar on 2021-11-23
```
-rw------- 1 zimbra zimbra 24516902912 Nov 23 23:13 data.mdb
-rw-r----- 1 zimbra zimbra      561447 Nov 23 03:00 data.mdb.tgz
```
Woah! That is quite a difference!

Thanks for such an informative post.

---

### Post by LokiScarlet on 2021-11-24
I'm guessing you've rebooted, but if you haven't I'd recommend it. In fact, you may want to go into recovery and run fsck.

I also noticed you have multiple internal hard drives. Do you mind sharing the output of "df -Th"? I understand if you'd rather not, but it could help find the cause of the discrepancy.

---

