---
title: "root partition full"
date: 2016-09-21
forum: General Help
---

### Post by BigYellowDog on 2016-09-21
Somehow my root partition is full, how do I determine which directory and which process is filling my drive?

---

### Post by oldfred on 2016-09-21
Root partition or /boot?

       RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573) 

    Post this, first mount any other partitions also:
       
 df -Th | grep sd| sort 
           
 cd / or cd /home
sudo du -hc --max-depth=1

---

### Post by BigYellowDog on 2016-09-21
[SIZE=3][FONT=tahoma]I'm running server (16.04.1 LTS) my root (/) partition is only used for the OS.  Files that get changed frequently go into my /home partition, that one has plenty of space.  I had a gigabytes free, but today my / partition is 100% full[/FONT][/SIZE]

> /dev/sda1      ext4       12G   12G     0 100% /
/dev/sda2      ext4      1.8T  1.4T  387G  78% /home


[SIZE=3][FONT=tahoma]
/var/cache/apt/archives is using 23M, and lost+found is empty.

I did find / -mtime 5 to see what files have been added in the last 5 days and when I checked the directories they seemed to be using normal space.

I know I can use gparted to resize my root (/) partition, but I'm trying to avoid that.  Something may suck up free space again.
[/FONT][/SIZE]

---

### Post by bab1 on 2016-09-21
> **BigYellowDog said:**
> [SIZE=3][FONT=tahoma]I'm running server (16.04.1 LTS) my root (/) partition is only used for the OS.  Files that get changed frequently go into my /home partition, that one has plenty of space.  I had a gigabytes free, but today my / partition is 100% full[/FONT][/SIZE]


[SIZE=3][FONT=tahoma]
/var/cache/apt/archives is using 23M, and lost+found is empty.

I did find / -mtime 5 to see what files have been added in the last 5 days and when I checked the directories they seemed to be using normal space.

I know I can use gparted to resize my root (/) partition, but I'm trying to avoid that.  Something may suck up free space again.
[/FONT][/SIZE]
Check /boot.  This is where old kernel images are.

---

### Post by BigYellowDog on 2016-09-21
/boot is using 102M.

 I de-installed MongoDB, /var/lib/mongodb/journal was using about 4Gb.  Not using MongoDB currently, but I was going to try and do some learning exercises with it.

How much space is recommended for server?

---

### Post by bab1 on 2016-09-21
> **BigYellowDog said:**
> /boot is using 102M.

 I de-installed MongoDB, /var/lib/mongodb/journal was using about 4Gb.  Not using MongoDB currently, but I was going to try and do some learning exercises with it.

How much space is recommended for server?
I use 20GB for the root partition ( / ) with the rest for the home partition ( /home ).  I find the newer district offerings have become fatter.  Most of my machines have about the same files size as you have (12 -14GB).  Most of my machines use 120 GB SSD's.

---

