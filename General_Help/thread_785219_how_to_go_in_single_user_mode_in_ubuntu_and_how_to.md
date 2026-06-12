---
title: "how to go in single user mode in ubuntu and how to fsck ?"
date: 2008-05-07
forum: General Help
---

### Post by tusharhiwse on 2008-05-07
hi friends, 
as mentioned above my system needs fsck. i want to know that how would i do fsck and how can i go in single user mode.

thanks in advance.

from 
tushar

---

### Post by prshah on 2008-05-07
> **tusharhiwse said:**
> 
as mentioned above my system needs fsck. i want to know that how would i do fsck and how can i go in single user mode.


When booting, select recovery mode from the grub menu, and then run ```
fsck -a /dev/xxx1
``` on whichever partition you want.

Unless the partition is in active use (Eg, "/" or "/home"), you do not need to go into recovery mode. You can just unmount the device and use fsck on it. Eg:```

sudo umount /dev/sxx
sudo fsck -a /dev/sxx1
```

Note that in multiuser mode, you need "sudo", but not in single user (recovery) mode.

fsck will automatically try to detect the partition type and run the correct recovery tool. Remember to pass a partition parameter (Eg /dev/sxx1) to fsck and not a device parameter (Eg /dev/sxx)

---

### Post by unutbu on 2008-05-07
To get to the grub menu, press ESC while booting up. 

You can also boot from the LiveCD, open a terminal, and run 

```
sudo fsck -a /dev/xxxx
```

from there. (Like prshah mentioned, you need to change xxxx to the right device name.)

---

### Post by eriqjaffe on 2008-05-07
You can also just run

```
shutdown -rF now
```

...whill will reboot your system and force fsck to run, similar to rebooting after running "chkdsk /r" in Windows.

---

### Post by nick_h on 2008-05-07
You could also create a file called *forcefsck* in the root directory using:
```
touch /forcefsck
```
and then reboot.

---

### Post by dbyrne on 2008-05-08
Running Gutsy 7.10, neither "sudo touch /forcefsck" nor "shutdown -Fr now" cause an fsck to be run. Is this only applicable to older versions of Ubuntu ?

(Trying to recover disk space not released on a ext2fs/RAID-1 array ... if only Ubuntu wasn't so bl**dy oblique :confused:)

---

### Post by tubezninja on 2008-05-08
> **dbyrne said:**
> Running Gutsy 7.10, neither "sudo touch /forcefsck" nor "shutdown -Fr now" cause an fsck to be run. Is this only applicable to older versions of Ubuntu ?

That's very odd.  "sudo touch /forcefsck" always worked for me in 7.10.  Just tried it now on a development server running 8.04; it also works.

---

### Post by chrisccoulson on 2008-05-08
Also, please bare in mind - **never run fsck on a mounted volume. Ever!!**. This means that it is no good booting to recovery mode to check the root partition - it **must** be unmounted first.

The suggestions posted here (sudo touch /forcefsck) should work. If not, then the alternative is booting the live CD and running fsck from there.

---

### Post by dbyrne on 2008-05-09
Hmm, not sure what happened then, but the /forcefsck file is gone so the system must have checked and removed it. Maybe it did a really fast fsck :)

I forced it to fsck by doing "tune2fs -c 2 /dev/md2 ; tune2fs -C 3 /dev/md2 ; reboot", and confirmed that everything checked out by looking in the /var/log/fsck/checkfs file.

---

### Post by stream303 on 2008-05-09
That's exactly what happened.  After the fsck after reboot, the /forcefsck file is removed automatically.

---

### Post by Denbert on 2009-04-29
> **nick_h said:**
> You could also create a file called *forcefsck* in the root directory using:
```
touch /forcefsck
```
and then reboot.

Wow, you are my personal hero :guitar:

This advice should be added to the [https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck) documentation.

---

### Post by Denbert on 2009-04-29
There is 2 logfiles after the fsck:

```
nano /var/log/fsck/checkroot
``` says:

Log of fsck -C -f -a -t ext3 /dev/sda1
Wed Apr 29 15:34:31 2009

fsck 1.40.8 (13-Mar-2008 )
/dev/sda1: 42919/427392 files (1.2% non-contiguous), 329475/1708906 blocks

Wed Apr 29 15:34:49 2009
----------------

```
nano /var/log/fsck/checkfs
``` says:

Log of fsck -C -R -A -a -f
Wed Apr 29 15:34:49 2009

fsck 1.40.8 (13-Mar-2008 )
/dev/sda6: 30562/13615104 files (35.9% non-contiguous), 4341646/27218118 blocks

Wed Apr 29 15:36:20 2009
----------------

My question is now, is it fixed or do I need to do something besides eating :popcorn: while enjoying my Hardy?

---

### Post by itismike on 2010-11-01
I'm running Linux Mint (a derivation of Ubuntu) and fsck seems to be broken. When I place a file called forcefsck in the / directory and reboot, a line of text claims that fsck is running, but I wait for hours and it never changes. (and I don't hear the hard drive working)

There is nothing listed in these logfiles, which just have creation dates around the time I installed the OS:
```
michael@clamshell /var/log/fsck $ ls -aFl
total 16
drwxr-xr-x  2 root root 4096 2010-04-27 05:42 ./
drwxr-xr-x 13 root root 4096 2010-11-01 12:38 ../
-rw-r-----  1 root adm    31 2010-04-27 05:42 checkfs
-rw-r-----  1 root adm    31 2010-04-27 05:42 checkroot
michael@clamshell /var/log/fsck $ cat *
(Nothing has been logged yet.)
(Nothing has been logged yet.)
michael@clamshell /var/log/fsck $
``` 

The CD-ROM is broken on this laptop so using a rescue disk is tricky. I could make a boot-USB, but I'd rather fix the apparently broken fsck than go through this method.

---

