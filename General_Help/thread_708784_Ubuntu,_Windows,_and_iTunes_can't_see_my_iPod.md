---
title: "Ubuntu, Windows, and iTunes can't see my iPod"
date: 2008-02-26
forum: General Help
---

### Post by mb184 on 2008-02-26
I have an iPod 5g and i have been messing around with it and i discovered the problem of iTunesLock preventing me from accessing the iPod and putting itself back on. Well in a stroke of genius I deleted the Play Counts and iTunesLock files also trying to see if that would stop iTunesLock from reappearing every time i plug in my iPod.
Now my computer (running Ubuntu 7.10) does not see it at all. Also windows does not see it, until i remove it then it says my iPod is corrupted, but when i connect it, iTunes denies any knowledge of seeing it.

I tried to use this website to help and it did nothing for me.
[http://www.macworld.com/article/38851/2004/09/trubipod.html](http://www.macworld.com/article/38851/2004/09/trubipod.html)

Right now when i turn it on it shows the "Connect to computer. Use iTunes to restore iPod."
then it goes into disk mode.  Strangely, even in disk mode neither windows nor Linux can see it.

I went into the diagnostics menu and everything seems to check out fine. 

i know there is a .Trash-matthew file on the iPod and i have a great suspicion that if i can get on the iPod and see the hidden files then i could just put the file back.

Also BIOS does see it so I don't think its completely bricked yet.

I am using linux but I have access to Windows Vista. So I can work in either format.

for those versed in Linux here are some commands and their outputs for you to use:

This is the immediate output of dmesg
```
matthew@matthew-laptop:~$ dmesg | tail
[ 4127.628000] scsi 9:0:0:0: Direct-Access Apple iPod 1.62 PQ: 0 ANSI: 0
[ 4127.632000] sd 9:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[ 4127.632000] sd 9:0:0:0: [sdb] Write Protect is off
[ 4127.632000] sd 9:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 4127.632000] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 4127.632000] sd 9:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[ 4127.636000] sd 9:0:0:0: [sdb] Write Protect is off
[ 4127.636000] sd 9:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 4127.636000] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 4127.636000] sdb:

```


This is the output of dmesg after it has been connected for like 5 or 10 minutes
```
matthew@matthew-laptop:~$ dmesg |tail
[ 9694.884000] Buffer I/O error on device sdb, logical block 0
[ 9775.112000] sd 19:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY
[ 9775.112000] end_request: I/O error, dev sdb, sector 0
[ 9775.112000] Buffer I/O error on device sdb, logical block 0
[ 9853.396000] sd 19:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY
[ 9853.396000] end_request: I/O error, dev sdb, sector 0
[ 9853.396000] Buffer I/O error on device sdb, logical block 0
[ 9933.328000] sd 19:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY
[ 9933.328000] end_request: I/O error, dev sdb, sector 0
[ 9933.328000] Buffer I/O error on device sdb, logical block 0
```

Realizing it wasn't mounted tried to mount it and got this response:
```
matthew@matthew-laptop:~$ sudo mount /media/sdb
[sudo] password for matthew:
mount: can't find /media/sdb in /etc/fstab or /etc/mtab
```

I tried to fdsk it and got this:
```
matthew@matthew-laptop:~$ sudo fdisk /dev/sdb
last_lba(): I don't know how to handle files with mode 40755
You will not be able to write the partition table.

Unable to read /dev/sdb
```

The last thing that I tried was mkfs.vfat /dev/sdb2:
```
matthew@matthew-laptop:~$ mkfs.vfat /dev/sdb2
mkfs.vfat 2.11 (12 Mar 2005)
]/dev/sdb2: No such file or directory
```

Any input would help would be greatly appreciated.

---

### Post by Crafty Kisses on 2008-02-26
Hmmm, have you tried to sync your iPod with gtkPod?

---

### Post by mb184 on 2008-02-26
> **Codename said:**
> Hmmm, have you tried to sync your iPod with gtkPod?

I have now and i got this output 
```
Error initialising iPod: Problem creating iPod directory or file: '/media/ANTHONY RAM/iPod_Control'.
```

Right now I can only see the iPod in BIOS and through dmesg | tail

---

