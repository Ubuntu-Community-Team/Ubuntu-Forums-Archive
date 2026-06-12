---
title: "Usb drive can not format (Read-only)"
date: 2015-05-28
forum: General Help
---

### Post by fairbird on 2015-05-28
I have usb driver and i cannot format it ...
I have tried more things more command but without succeed 
```
raed@fairbird:~$ sudo dosfsck -a /dev/sdb1
dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
  Not automatically fixing this.
Free cluster summary wrong (70801 vs. really 129471)
  Auto-correcting.
Performing changes.
/dev/sdb1: 1019 files, 113153/242624 clusters
Writing 4 bytes at 1000 failed: Operation not permitted

```

```
raed@fairbird:~$ sudo mkfs.ext3 /dev/sdb1
mke2fs 1.42 (29-Nov-2011)
/dev/sdb1: Read-only file system while setting up superblock


```

usb flash can open and read but can not write ...

Any help ?!
Thank you adviced

---

### Post by Nuno_Faria on 2015-05-29
"Operation not permitted"
Have you tried doing sudo -i and then executing these commands? Or logging in to root and typing the commands?
Or, well... restarting computer then go to recovery and just go to the root terminal one enter root password and then type these commands.

---

### Post by slickymaster on 2015-05-29
Have you tried just using Gparted? Delete all existing partitions and start over.

---

### Post by fairbird on 2015-05-29
@[**[COLOR=#000000]Nuno_Faria[/COLOR]**]("http://ubuntuforums.org/member.php?u=1974564")
Of course I tried under root (sudo su) and restarted pc but nothing changed  

@[**[COLOR=#990303][B]slickymaster**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1753126")
Yes I have tried Gparted but doesn't format it said (file system read-only)

Thank you

---

### Post by slickymaster on 2015-05-29
Maybe the drive is physically ruined. You can check that with badblocks. See how it works```
man badblocks
```
For example, your USB pendrive is recognized as /dev/sdb1:```
sudo badblocks -n /dev/sdb1
```

---

### Post by RobGoss on 2015-05-29
Hello and welcome, I was also having   trouble formatting one of my USB drives and this video help [https://youtu.be/DkHbka7_XPo](https://youtu.be/DkHbka7_XPo) for the life of me I could not format it after doing it a number of times on that same USB drive. After I ran these few commands it worked just fine.

---

### Post by fairbird on 2015-05-29
@[**[COLOR=#000000]robert159[/COLOR]**]("http://ubuntuforums.org/member.php?u=1971247")
Already tried that method without luck :(

@[**[COLOR=#990303][B]slickymaster**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1753126")
```
raed@fairbird:~$ sudo badblocks -n /dev/sdb1
/dev/sdb1 is mounted; it's not safe to run badblocks!
raed@fairbird:~$ umount /dev/sdb1
raed@fairbird:~$ sudo badblocks -n /dev/sdb1
badblocks: Read-only file system while trying to open /dev/sdb1
raed@fairbird:~$ 

```

Thank you

---

### Post by RobGoss on 2015-05-29
So there might be something wrong with that flash drive, maybe it's corrupt.

---

### Post by sudodus on 2015-05-29
Have you tried to write to the pendrive in a second and third computer?

You might try to wipe the first megabyte. If it does not work, I think the drive is 'gridlocked'. See this link

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

---

### Post by fairbird on 2015-05-29
@[**[COLOR=#000000]robert159[/COLOR]**]("http://ubuntuforums.org/member.php?u=1971247")      
Flash open just fine and i can copy from it any file but i can not write (Read-only)

     [**[COLOR=#C61919][B]@sudodus**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1499021")      
Yes I have check other pc same issue ...
With wipe method also nothing happen
```
raed@fairbird:~$ sudo -H mkusb wipe-whole-device
Wipe the whole device ... :
ubuntu
livedrive=/sda
ans=1
 
Wiping the whole device /dev/sdb ...
 
< /dev/zero pv  | dd bs=4096  of=/dev/sdb
Please wait for sync (flushing file system buffers to the device)
until 'Done' is written ...
dd: opening `/dev/sdb': Read-only file system
  64kB 0:00:00 [  56MB/s] [<=>                                                 ]
Syncing the device ...
Done, but you should also
check for the line 'dd: writing '/dev/sdb': No space left on device',
which means that the whole device is wiped. (Look in the terminal window) 
Cleanup after mkusb finished :-)
raed@fairbird:~$ 

```

Thank you

---

### Post by sudodus on 2015-05-30
I'm afraid that the pendrive is gridlocked and beyond repair. Anyway, now you have tried the methods, that are available for normal users. [COLOR=#696969]Maybe, but only maybe, a special tool from the manufacturer could solve the problem (depending on what is actually wrong inside the pendrive).[/COLOR]

---

### Post by fairbird on 2015-05-30
Ok ...
Thank you

---

