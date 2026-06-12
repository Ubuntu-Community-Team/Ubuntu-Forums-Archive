---
title: "Can't write to file system even though there is free space as said by df -h"
date: 2016-11-17
forum: General Help
---

### Post by dink123 on 2016-11-17
I was writing files (large amount of small files) to the file system in a java programme and then it suddenly threw a 'No space left on device' exception. Then I checked the output of df-h and it says there is enough free space on the disk. The specific file system that i'm trying to write is `/media/sam/Sam`.


Now if I try to create a file (`touch test.txt`) it says `touch: cannot touch ‘test.txt’: No space left on device`. This is true for only /media/sam/Sam as I could create files in other file systems (/media/sam/Sam is a ntfs partition that is coming from my Windows box). 




Here is the current output of df-h:


```
    Filesystem                          Size  Used Avail Use% Mounted on
    udev                                5.9G  4.0K  5.9G   1% /dev
    tmpfs                               1.2G  1.4M  1.2G   1% /run
    /dev/sda5                           156G  134G   15G  91% /
    none                                4.0K     0  4.0K   0% /sys/fs/cgroup
    none                                5.0M     0  5.0M   0% /run/lock
    none                                5.9G   71M  5.8G   2% /run/shm
    none                                100M   24K  100M   1% /run/user
    /dev/sda3                           176G  154G   23G  88% /media/sam/Sam //where i'm writing
    /dev/sda2                           105G  103G  2.3G  98% /media/sam/System
    /dev/sda1                           100M   25M   76M  25% /media/sam/Windows

```



And here is the curent output of df -i (Says I have enough free inodes as well):


   ```
 Filesystem                           Inodes    IUsed    IFree IUse% Mounted on
    udev                                1523763      552  1523211    1% /dev
    tmpfs                               1526458      584  1525874    1% /run
    /dev/sda5                          10362880  4740267  5622613   46% /
    none                                1526458        2  1526456    1% /sys/fs/cgroup
    none                                1526458        3  1526455    1% /run/lock
    none                                1526458      163  1526295    1% /run/shm
    none                                1526458       25  1526433    1% /run/user
    /dev/sda3                          46666376 23011679 23654697   50% /media/sam/Sam //where i'm writing
    /dev/sda2                           3523948  1108920  2415028   32% /media/sam/System
    /dev/sda1                            142516      100   142416    1% /media/sam/Windows

```

- Few things I tried:


 - I tried clearing up some space (say 10GB) but my java code throws the exception again **before** it fills the newly cleared 10GB space (Happened after using 1GB space). Then I can't write anything even from the terminal.


 - I also tried running `chkdsk /f` after booting from Windows as I saw elsewhere, that solved the problem for someone else, but didn't work for me. I'm really out of things to try now and this is the second day I'm trying to fix this issue so any help is highly appreciated. Let me knkow if you need more information.
 - Restarting doesn't help either. 


My OS is Ubuntu 14.04 with Kubuntu desktop manager installed. 


**EDIT**


Output of fdisk -l : 


  ```
  Disk /dev/sda: 500.1 GB, 500107862016 bytes
    255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    Disk identifier: 0xde15f6b0
    
       Device Boot      Start         End      Blocks   Id  System
    /dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
    /dev/sda2          206848   219014144   109403648+   7  HPFS/NTFS/exFAT
    /dev/sda3       219015168   587653119   184318976    7  HPFS/NTFS/exFAT
    /dev/sda4       628611070   976771071   174080001    f  W95 Ext'd (LBA)
    Partition 4 does not start on a physical sector boundary.
    /dev/sda5       628613120   960174079   165780480   83  Linux
    /dev/sda6       960186368   976771071     8292352   82  Linux swap / Solaris

```

---

### Post by TheFu on 2016-11-17
/dev/sda3       219015168   587653119   184318976    7  HPFS/NTFS/exFAT

NTFS?  Use Windows to troubleshoot.

---

### Post by dink123 on 2016-11-18
Do you know how to troubleshoot it from Windows?

---

### Post by TheFu on 2016-11-18
> **dink123 said:**
> Do you know how to troubleshoot it from Windows?

Nope. Sorry. 

Can you write the files to native Linux storage? Call it troubleshooting.  If the Linux userids to Windows userids map isn't setup, POSIX permissions don't get mapped.  Could that be the issue?

---

