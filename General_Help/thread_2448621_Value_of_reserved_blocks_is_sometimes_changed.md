---
title: "Value of reserved blocks is sometimes changed"
date: 2020-08-10
forum: General Help
---

### Post by raleigh3 on 2020-08-10
I have set my reserved blocks to 1%.

However sometimes that value is back up to 10%.

What conditions cause that?

Do I need to put a script to set it it 1% in my startup programs?

---

### Post by TheFu on 2020-08-10
Which file system type?  I've not had that issue with ext4.

```
$ sudo tune2fs -l /dev/sdb5 |grep -i Reserv
**Reserved block count:     0**
Reserved GDT blocks:      907
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
```

The default is 5% for ext4.  Ok to change to zero for data file systems, but please don't do that for OS file systems.

---

### Post by raleigh3 on 2020-08-10
I am using ext4.

I found this. What does the underline part mean?

With the help of reserved blocks, operating system keeps running for hours or sometimes days even though _root file system is 100% full_.

---

### Post by The Cog on 2020-08-11
That means there is no more space on the root filestysem (the partition that holds /). Your system is close to crashing when the disk is full. The reserved blocks are reserved for system use, not normal users, and this means the users see disk full problems before the system actually becomes un-bootable.
My guess is that the reserved blocks count goes up when it needs to use them because that's all the space that's left.
[https://askubuntu.com/questions/266825/what-do-i-do-when-my-root-filesystem-is-full](https://askubuntu.com/questions/266825/what-do-i-do-when-my-root-filesystem-is-full)

---

### Post by raleigh3 on 2020-08-11
> **The Cog said:**
> That means there is no more space on the root filestysem (the partition that holds /). Your system is close to crashing when the disk is full. The reserved blocks are reserved for system use, not normal users, and this means the users see disk full problems before the system actually becomes un-bootable.
My guess is that the reserved blocks count goes up when it needs to use them because that's all the space that's left.
[https://askubuntu.com/questions/266825/what-do-i-do-when-my-root-filesystem-is-full](https://askubuntu.com/questions/266825/what-do-i-do-when-my-root-filesystem-is-full)

Thanks.

My hard drive is 2 Tb.

I am using 2%, so running out of space should never be a problem.

---

### Post by TheFu on 2020-08-11
> **raleigh3 said:**
> Thanks.

My hard drive is 2 Tb.

I am using 2%, so running out of space should never be a problem.

Any disk can run out of storage.  Just make certain that /boot and /var never do.  When /boot runs too low, kernel updates fail and you'll end up with all sorts of avoidable problems.  When /var fills, the system will crash and may not boot.  If /boot and /var are shared with /, then correcting the issues is harder, since both are problems.

2% won't prevent root-owned processes from using the storage.  Watch it closely to avoid bad days.

---

### Post by raleigh3 on 2020-08-11
How do I see how much /boot and /var are using?

And what  does "root-owned processes from using the storage" mean?

---

### Post by SeijiSensei on 2020-08-11
```

cd /
du -sh *

```

If you mount remote filesystems from servers, you might want to add the -x parameter to limit the results to just the root filesystem.

---

### Post by TheFu on 2020-08-11
> **raleigh3 said:**
> How do I see how much /boot and /var are using?

And what  does "root-owned processes from using the storage" mean?

It is about _file systems_ running out of space, not directories. If the directories are part of the / file system, then check the / file system
```
df -Th /
```

If they are separate file systems, run 
```
df -Th /var
df -Th /boot
```

A handy alias that removes all the loop and fake file systems, is 
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
```

---

### Post by raleigh3 on 2020-08-11
Does this refer to my 2 Tbytes of space on my hard drive or the reserved blocks being used up?

```
It is about file systems running out of space, not directories. If the directories are part of the / file system, then check the / file system
```

---

### Post by The Cog on 2020-08-11
Can you please post the output of
```
du -sh | grep -v snap
lsblk -fmap | grep -v snap
```
so we can see what partitions and sizes you actually have.

---

### Post by raleigh3 on 2020-08-11
```
du -sh | grep -v snap
1.3G	.

```
```
NAME        FSTYPE   LABEL       UUID                                 MOUNTPOINT                      SIZE OWNER GROUP MODE
/dev/loop3                                                                                                 root  disk  brw-rw----
/dev/loop11                                                                                                root  disk  brw-rw----
/dev/sda                                                                                              1.8T root  disk  brw-rw----
&#9492;&#9472;/dev/sda1 ext4                 81353260-b5a5-4b72-9fce-432e7c620fdc /                               1.8T root  disk  brw-rw----
/dev/sdb                                                                                            298.1G root  disk  brw-rw----
&#9500;&#9472;/dev/sdb1 ext3     MAXTOR_SDB1 b3b0f384-9e2e-45f5-8995-932f1113f59d /media/storagedrive            98.4G root  disk  brw-rw----
&#9492;&#9472;/dev/sdb2 ext3     MAXTOR_SDB2 e0dadb1c-0161-4862-8e95-7c42d8f7fb03 /media/andy/MAXTOR_SDB2       199.7G root  disk  brw-rw----
/dev/sr0                                                                                            562.9M root  cdrom brw-rw----[CODE][CODE]
```[/CODE][/CODE]

---

### Post by TheFu on 2020-08-11
code tags?

---

### Post by The Cog on 2020-08-13
@raleigh3
With my apologies, please can you also post the output of 
```
df -h | grep -v snap
```
However, we can see that you do indeed have a single 2TB partition for Linux, and a 300G external drive. 
At the moment, I expect to see that 2TB is, as you say, 2% full which would leave me wondering what this is all about.
Please can you explain how you set the reserved blocks to 1%, and how you see their usage (post command and output if possible). It's not that we're doubting what you say, but it eliminates the possibility of misunderstandings.

---

### Post by TheFu on 2020-08-13
[QUOTE=raleigh3;13978913]Does this refer to my 2 Tbytes of space on my hard drive or the reserved blocks being used up?

Re-read #9 above.  It is about full **_[COLOR="#FF0000"]file systems[/COLOR]_**.  That's what **df** and **df -i** show.  

Technically speaking, directories don't fill up - well, beyond just having so many files that access becomes slow.  File systems do fill up.  Directories with over about 400 files get slower and slower as more files are added. That's just the nature of having to retrieve and display information on so much file information. When working on directories with 100,000+ files, normal commands just don't work. They break. Best to build a directory tree.

IMHO, having / over about 25G is a poor storage design choice.  Keep the OS separate from all data. A Unix OS will never need over 100G of storage, no matter how bloated the OS may be.  Keep the data separate from the OS.

---

