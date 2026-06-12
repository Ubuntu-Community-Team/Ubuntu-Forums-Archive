---
title: "/dev/sda3/ missing from launcher"
date: 2017-11-18
forum: General Help
---

### Post by mbott on 2017-11-18
The Music partition I set up on my hard drive has gone missing from the launcher in 14.04LTS. Whether it is mounted or unmounted, it no longer appears. Is there a quick-fix to return this icon to the launcher?

Thanks,

-- 
Mike

---

### Post by ajgreeny on 2017-11-18
Much more info is needed for us to help you with this problem.

Let's see the output of command ```
sudo parted -l
``` to see all the details of your current partitions.

Is this a dual boot with Windows?  Depending on your Windows fast start setup this may leave NTFS partitions hibernated and therefore not available in Ubuntu.

---

### Post by mbott on 2017-11-18
Model: ATA WDC WD10JPVX-22J (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  248GB   248GB   primary   ext4            boot
 3      248GB   992GB   744GB   primary   ntfs
 2      992GB   1000GB  8472MB  extended
 5      992GB   1000GB  8472MB  logical   linux-swap(v1)

Not dual boot. Ubuntu 14.04 is the only OS.

---

### Post by ajgreeny on 2017-11-18
It looks as if your lost partition is ntfs.

Why have an ntfs if you have no Windows on the machine; is that historical?  

If there is a problem with the ntfs partition's filesystem it really needs Windows to repair it as there is nothing I know in Linux that can be depended on to do this properly, though I may be out of date on that point.

---

### Post by mbott on 2017-11-19
Interesting as that partition has existed since 14.04 was installed.

Thanks

-- 
Mike

---

### Post by ajgreeny on 2017-11-19
But did it exist before you installed 14.04?  I assume it did and you left it unformatted at that time.

One of the problems of using ntfs without a Windows OS available is exactly what you've seen here, and unfortunatley, I have no experience of  Windows any more so can't really help.

Keep looking back here and bump the thread (post the word "Bump"  only) after a day or so if no-one else comes along to help. That will raise it in the Activity page that many forum users visit daily.

---

### Post by mbott on 2017-11-19
If memory serves, I used linux to create & format that partition. Anyway, I just reformatted the partition as Ext4 and reloaded the 300GB of music. 

-- 
Mike

---

### Post by ajgreeny on 2017-11-20
Great!
Much more sensible if you do not have a Windows OS to do any repairs to an NTFS partition.

---

