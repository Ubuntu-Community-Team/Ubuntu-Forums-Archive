---
title: "Can not copy backup"
date: 2007-10-25
forum: General Help
---

### Post by lsutiger on 2007-10-25
I am trying to copy my backup folder to an empty formated (EXT3) usb drive. The drive is 60GB. The backup folder is 26 GB.

When I try to copy it from CLI I get:
```
root@complexity-laptop:/var/backup/Backup# cp * /media/disk/
File size limit exceeded (core dumped)

```
Now this happens after writing to the disk for a while.

When I browsed to the drive, the folder size was 4.0GB
So I tried it graphically, and it just died. So I browsed to the folder and it was once again 4.0GB

What with this 4.0 GB limit?
Thanx in advance!

---

### Post by lsutiger on 2007-10-25
bump

---

### Post by lordlollo on 2007-10-25
> **lsutiger said:**
> I am trying to copy my backup folder to an empty formated (EXT3) usb drive. The drive is 60GB. The backup folder is 26 GB.

When I try to copy it from CLI I get:
```
root@complexity-laptop:/var/backup/Backup# cp * /media/disk/
File size limit exceeded (core dumped)

```
Now this happens after writing to the disk for a while.

When I browsed to the drive, the folder size was 4.0GB
So I tried it graphically, and it just died. So I browsed to the folder and it was once again 4.0GB

What with this 4.0 GB limit?
Thanx in advance!


I'm not an expert, but the file limit size is related to the block size of the filesystem. If I remeber well, in ext3 there's a limit of 16GB if the block size is 1 kb. So, your error is somehow strange... It reminds fat32 filesystems...

Good luck.

---

### Post by lsutiger on 2007-10-25
Well here is the output of this code```
complexity@complexity-laptop:~$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 20
file size               (blocks, -f) unlimited
pending signals                 (-i) unlimited
max locked memory       (kbytes, -l) unlimited
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) unlimited
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) unlimited
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

```

To me that says unlimited.
Still looking for an answer....
Thanx though!

---

### Post by lsutiger on 2007-10-25
Bump

---

### Post by mapman on 2007-11-12
If you type in the mount command you'll get a description of the filesystems.  If the usb drive says vfat then that will be the reason for the 4gb limit.  I'm running into the same issue.

---

### Post by SgtDude on 2008-03-12
I'm having the same problem cp ing to an XFS partition on a samba share.  Strange...

---

### Post by nisarg on 2008-03-15
i am having a similar problem. the copying dies with an "limit exceeded" error.
I am trying to recover a disk using ddrescue. the disk that i am trying to copy the img to is a fat32 partition.

i mounted the partition using the following command
```
 mount -t vfat /dev/sdb1 /mnt/xdisk 
```

my external drive is a big drive, 160gb, and has a lot of data. the backup i am trying to copy over is roughly 40-50gb. 

I am going to try and format the ext drive with NTFS, but its got a lot of data on it.. around 70gb. 

Any ideas anyone? am I heading in a right direction? copying 70gb, formatting the ext drive and trying to copy 70gb back on, and hitting a limit again will really be very painful.
Can anyone tell me what file-system should i use to overcome is this issue?

thanks a lot in advance.

---

### Post by SgtDude on 2008-05-12
Sorry guys.  I used NFS to solve my problem, and forgot about this thread.  But I just ran across this command
```
mount -t smbfs -o lfs //server/share /localdir
```
at
[http://www.linuxquestions.org/questions/linux-networking-3/samba-file-size-limit-372039/](http://www.linuxquestions.org/questions/linux-networking-3/samba-file-size-limit-372039/)

Apparently the problem is in the client, not the server.  And the "lfs" should enable "large file support" which may solve your problems.  As I said, I used NFS to solve my problem, so I haven't tried this.  Good luck.

---

