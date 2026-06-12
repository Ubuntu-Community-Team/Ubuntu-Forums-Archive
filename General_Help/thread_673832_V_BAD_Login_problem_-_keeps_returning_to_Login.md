---
title: "V BAD Login problem - keeps returning to Login"
date: 2008-01-21
forum: General Help
---

### Post by sipickles on 2008-01-21
Hi,

I have a major issue.

Running gutsy 7.10, I get to the login page as normal.

After entering my username and password, I hear the Login audio sounds, but then the screen turns black with white text saying:

Stopping any running daemons....
etc
etc

Then I am presented with the login page again :( Keeps on looping like that

I am now logged in by choosing failsafe GNOME, but this is obviously no good as half my software will not work. I guess this means there is a problem with some startup script. 

The strange thing is, I did not install or change anything between successful and unsuccessful logins.

Please help, this is my work machine! :shock:

Thanks 
Simon

---

### Post by banewman on 2008-01-21
OK Simon, we are going to try and change the runlevel to get around the problem
At the login press ctrl-alt-F2 to get a command line screen - then type - 
telinit 3
press enter and then alt-F7
and you should be at a login prompt.
If the problem is restricted to the default runlevel then you should be able to access the system and we can make the change permanent.
:)

---

### Post by sipickles on 2008-01-21
Hello Banewman, Thanks for the quick help!

I tried the telinit 3 suggestion, but the problem is still the same.

Thanks

Simon

---

### Post by banewman on 2008-01-21
Simon, boot from the live cd and open a terminal and type-
sudo fsck -V /dev/sda 
(if ubuntu is on the first hard drive) - that will try and repaiar the system and tell you what it is doing as it goes along.
:)

---

### Post by sipickles on 2008-01-21
okay, i will


I have dual boot with xp, how can I check which partition ubuntu is on?  

Both xp and ubuntu are on the same physical hard drive so /dev/sda is right, yes?

Si

---

### Post by sipickles on 2008-01-21
Ok, I am using the live cd now, and tried your suggestion:

```
ubuntu@ubuntu:~$ sudo fsck -V /dev/sda
fsck 1.40.2 (12-Jul-2007)
[/sbin/fsck.ext2 (1) -- /dev/sda] fsck.ext2 /dev/sda 
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext2: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?

```

:(

---

### Post by banewman on 2008-01-21
Probably explains your hangup at login issue - did the power cutout or something while ubuntu was running?

---

### Post by sipickles on 2008-01-21
Maybe, the pc is in a workshop so its a bit of a cruel environment.

Not sure why I can access the drive in a failsafe GNOME tho...

Anyway I can fix this, or shall I just re-install?

---

### Post by danwood76 on 2008-01-21
you will need to point to the partition number for fsck.
Could you post the result of:
```

sudo fdisk -l

```

Although I doubt you have any serious disk errors, it sounds more like a login script.
If you login on failsafe gnome and create a new user can you log in normally with that new user?

regards,
Danny

---

### Post by banewman on 2008-01-21
Since fsck says the os is in use I'm out of suggestions for a recovery.
If you reinstall can I suggest a separate /home partition - any further upgrades or installs will let you keep the files in /home if you select it during install.
sorry :)

---

### Post by sipickles on 2008-01-21
Thanks for your efforts Ban,

Fortunately, I have my home dir on its own partition so a fresh install is not a scary proposition, just slow!

Dan, here is the output:
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd53d826f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   1b  Hidden W95 FAT32
/dev/sda2   *         244        4852    37021792+   7  HPFS/NTFS
/dev/sda3            4853       12161    58709542+   f  W95 Ext'd (LBA)
/dev/sda5            4853        8218    27037363+   7  HPFS/NTFS
/dev/sda6            8219        8340      979933+  82  Linux swap / Solaris
/dev/sda7            8341       10164    14651248+  83  Linux
/dev/sda8           10165       11380     9767488+  83  Linux
/dev/sda9           11381       12161     6273351    7  HPFS/NTFS
```

The 14gb(sda7) disk has Ubuntu system on it, with the 9gb(sda8 ) having my home directory

-------------------------

I added another user in failsafe mode, but they cannot log in either :(

----------------------------

So I did: sudo fsck -V /dev/sda8 and it said it checked it, but my symptoms persist

---

### Post by sipickles on 2008-01-21
I'd like to the LiveCD have a 'REPAIR' option, to restore faulty logon scripts.

---

### Post by banewman on 2008-01-21
Do you have the prog ntfs-3g installed to read/write to your windows partitions?

---

### Post by sipickles on 2008-01-21
I'm not sure. I guess so, I've always been able to access them since installation.


EDIT: yes i do:

ntfs-3g 1.913 - Third Generation NTFS Driver

---

### Post by sipickles on 2008-01-22
*bump ;)

Still having this bad problem...... Thought I'd try one last ask before doing a clean install

---

### Post by danwood76 on 2008-01-22
> **sipickles said:**
> *bump ;)

Still having this bad problem...... Thought I'd try one last ask before doing a clean install

I think a clean install would be your best bet.
It wont take long and as you already have your /home on a seperate partition it wont be too hard.
If you've done a lot of configuring its best to backup /etc aswell (you can do it from the live CD of course) just incase you need some of your old config files to get things working the way you had before.

regards,
Danny

---

