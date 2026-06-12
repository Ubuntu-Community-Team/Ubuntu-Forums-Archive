---
title: "boot partition full"
date: 2015-09-09
forum: General Help
---

### Post by zandu on 2015-09-09
Hi  I made an error using photorec in xfce which has resulted in photorec  placing files in my boot partition so how can I delete them ?     Thanks in advance

---

### Post by Bashing-om on 2015-09-09
zandu; Hello;

I would expect one to be able to remove them with the elevated privileges of "sudo"/ Please show us what the partition contains, for direct instruction.
```

ls -al /boot/

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]no step for a stepper
[/INDENT]

---

### Post by zandu on 2015-09-10
Hi  Bashing-om   ,  here is a copy of what is in the boot, 
mine@mine-System-Product-Name:~$ sudo ls -al /boot/
[sudo] password for mine: 
total 74876
drwxr-xr-x  3 root root     4096 Sep  6 10:00 .
drwxr-xr-x 22 root root     4096 Sep  6 09:54 ..
-rw-r--r--  1 root root  1168937 Dec  9  2014 abi-3.13.0-43-generic
-rw-r--r--  1 root root  1169421 Aug 15 08:58 abi-3.13.0-63-generic
-rw-r--r--  1 root root   169815 Dec  9  2014 config-3.13.0-43-generic
-rw-r--r--  1 root root   169833 Aug 15 08:58 config-3.13.0-63-generic
drwxr-xr-x  5 root root     4096 Sep 11 09:01 grub
-rw-r--r--  1 root root 28161761 Sep  6 09:40 initrd.img-3.13.0-43-generic
-rw-r--r--  1 root root 28176695 Sep  6 10:00 initrd.img-3.13.0-63-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  2699011 Dec  9  2014 System.map-3.13.0-43-generic
-rw-------  1 root root  2701418 Aug 15 08:58 System.map-3.13.0-63-generic
-rw-r--r--  1 root root  5833296 Dec 30  2014 vmlinuz-3.13.0-43-generic
-rw-------  1 root root  5845456 Aug 15 08:58 vmlinuz-3.13.0-63-generic
mine@mine-System-Product-Name:~$

---

### Post by Bashing-om on 2015-09-10
zandu; Hey;

Your boot is good as is ;
For reference my /boot:
```

sysop@1404mini:~$ ls -al /boot/
total 58952
drwxr-xr-x  4 root root     4096 Sep  3 23:27 .
drwxr-xr-x 25 root root     4096 Sep  8 20:39 ..
-rw-r--r--  1 root root  1165261 Aug 11 11:15 abi-3.13.0-62-generic
-rw-r--r--  1 root root  1165204 Aug 14 18:07 abi-3.13.0-63-generic
-rw-r--r--  1 root root   165763 Aug 11 11:15 config-3.13.0-62-generic
-rw-r--r--  1 root root   165763 Aug 14 18:07 config-3.13.0-63-generic
drwxr-xr-x  5 root root     4096 Sep  9 15:47 grub
drwxr-xr-x  5 root root     4096 Jun  9  2014 grub_backup
-rw-r--r--  1 root root 19349389 Aug 18 12:07 initrd.img-3.13.0-62-generic
-rw-r--r--  1 root root 19349082 Sep  3 14:36 initrd.img-3.13.0-63-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3392306 Aug 11 11:15 System.map-3.13.0-62-generic
-rw-------  1 root root  3392068 Aug 14 18:07 System.map-3.13.0-63-generic
-rw-------  1 root root  5820896 Aug 11 11:15 vmlinuz-3.13.0-62-generic
-rw-------  1 root root  5821152 Aug 14 18:07 vmlinuz-3.13.0-63-generic
sysop@1404mini:~$

```

The only small thing I see amiss in your /boot is that your backup kernel is the -43 version rather than the -62 . No real biggy.

As the copies are not in the /boot partition. maybe we can locate them - ?
```

cd /
sudo du -sx * | sort -n
cd

```
where 'du' is disk usage and reports on where space is being used. and sorted by size.

[INDENT][INDENT][INDENT]we see what is
[/INDENT][/INDENT][/INDENT]

---

### Post by XBNCPRk on 2015-09-10
... Perhaps its just me, but I dont see anything there that shouldnt be.

---

### Post by zandu on 2015-09-10
ok perhaps I have got it wrong then .. This is what I get when Itry to run synaptic package manager 
E: Write error - write (28: No space left on device)
E: Can't mmap an empty file
E: Failed to truncate file - ftruncate (9: Bad file descriptor)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Gparted shows that shows that /

---

### Post by JKyleOKC on 2015-09-11
Use the command bashing-om gave you in Post #4 above; it will tell you where in the file system the offending files are located.

The entire file system, if installed in the usual default configuration, will be in the "/" tree; that's not just the "/boot" node. The photorec files are most likely in your home directory, or some subdirectory thereof, but the "disk usage" command will give you more details.

---

### Post by zandu on 2015-09-11
Hi   thanks for your help  I partitioned  the installation giving the / 20gib . /home 95gib and swap 2gib

---

### Post by Bashing-om on 2015-09-11
zandu; Hey !

We are here to help. However, if you do not follow our thought process to isolate this fault, and you do not know what to do, you are spinning your wheels to no effect .
If you want my help, please show me the condition that the condition is in.
```

cd /
sudo du -sx * | sort -n
cd

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We find where those space constraints are, and then fix the package manager.

[INDENT][INDENT]help us to help you
[/INDENT][/INDENT]

---

### Post by zandu on 2015-09-11
> **Bashing-om said:**
> zandu; Hey !

We are here to help. However, if you do not follow our thought process to isolate this fault, and you do not know what to do, you are spinning your wheels to no effect .
If you want my help, please show me the condition that the condition is in.
```

cd /
sudo du -sx * | sort -n
cd

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We find where those space constraints are, and then fix the package manager.

[INDENT][INDENT]help us to help you
[/INDENT][/INDENT]
[sudo] password for mine: 
du: cannot access ‘proc/2553/task/2553/fd/3’: No such file or directory
du: cannot access ‘proc/2553/task/2553/fdinfo/3’: No such file or directory
du: cannot access ‘proc/2553/fd/3’: No such file or directory
du: cannot access ‘proc/2553/fdinfo/3’: No such file or directory
0	initrd.img
0	initrd.img.old
0	proc
0	sys
0	vmlinuz
0	vmlinuz.old
4	cdrom
4	dev
4	mnt
4	srv
8	tmp
16	lost+found
172	root
1284	run
9768	bin
16164	sbin
16908	etc
82060	boot
431320	lib
490784	var
527468	opt
1196212	home
3454632	usr
13513212	media
mine@mine-System-Product-Name:/$

---

### Post by Bashing-om on 2015-09-11
zandu; Hey. 

Now I think we are making progress.
> 
13513212	media


So what is this directory ? - The normal mount point for removable devices -
```

df -h
df -i
ls -al /media
ls -al /media/<user_name>

```
is this what we are seeking to find ?
The use of code tags, makes reading so much easier  !
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]looks likely
[INDENT][INDENT][INDENT]sticking out like a sore thumb
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by zandu on 2015-09-12
> **Bashing-om said:**
> zandu; Hey. 

Now I think we are making progress.


So what is this directory ? - The normal mount point for removable devices -
```

df -h
df -i
ls -al /media
ls -al /media/<user_name>

```
is this what we are seeking to find ?
The use of code tags, makes reading so much easier  !
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]looks likely
[INDENT][INDENT][INDENT]sticking out like a sore thumb
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

mine@mine-System-Product-Name:/$ ```

[code]: command not found
mine@mine-System-Product-Name:/$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdc1        19G   18G     0 100% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           403M  1.3M  402M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   84K  2.0G   1% /run/shm
none            100M   32K  100M   1% /run/user
/dev/sdc5        92G  1.2G   86G   2% /home
overflow        1.0M  8.0K 1016K   1% /tmp
/dev/sdb2       2.8T  204M  2.8T   1% /media/mine/backup2
mine@mine-System-Product-Name:/$ df -i
Filesystem         Inodes  IUsed      IFree IUse% Mounted on
/dev/sdc1         1222992 354351     868641   29% /
none               213695      2     213693    1% /sys/fs/cgroup
udev               206595    547     206048    1% /dev
tmpfs              213695    563     213132    1% /run
none               213695      1     213694    1% /run/lock
none               213695      6     213689    1% /run/shm
none               213695     22     213673    1% /run/user
/dev/sdc5         6111232  28905    6082327    1% /home
overflow           213695      9     213686    1% /tmp
/dev/sdb2      2929992932     28 2929992904    1% /media/mine/backup2
mine@mine-System-Product-Name:/$ ls -al /media
total 28
drwxr-xr-x    5 root root  4096 Sep  8 10:26 .
drwxr-xr-x   22 root root  4096 Sep  6 09:54 ..
drwxr-xr-x    2 root root  4096 Dec 30  2014 cdrom
lrwxrwxrwx    1 root root     7 Sep  4 12:49 floppy -> floppy0
drwxrwxr-x    2 root root  4096 Sep  4 12:49 floppy0
drwxr-x---+ 249 root root 12288 Sep 12 16:55 mine
mine@mine-System-Product-Name:/$ ls -al /media/<user_name>
bash: syntax error near unexpected token `newline'
mine@mine-System-Product-Name:/$ 
```

---

### Post by zandu on 2015-09-12
Hi Bashing-om

mine@mine-System-Product-Name:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdc1        19G   18G     0 100% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           403M  1.3M  402M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   84K  2.0G   1% /run/shm
none            100M   32K  100M   1% /run/user
/dev/sdc5        92G  1.2G   86G   2% /home
overflow        1.0M  8.0K 1016K   1% /tmp
/dev/sdb2       2.8T  204M  2.8T   1% /media/mine/backup2
mine@mine-System-Product-Name:~$ df -i
Filesystem         Inodes  IUsed      IFree IUse% Mounted on
/dev/sdc1         1222992 354351     868641   29% /
none               213695      2     213693    1% /sys/fs/cgroup
udev               206595    547     206048    1% /dev
tmpfs              213695    563     213132    1% /run
none               213695      1     213694    1% /run/lock
none               213695      6     213689    1% /run/shm
none               213695     22     213673    1% /run/user
/dev/sdc5         6111232  28914    6082318    1% /home
overflow           213695      9     213686    1% /tmp
/dev/sdb2      2929992932     28 2929992904    1% /media/mine/backup2
mine@mine-System-Product-Name:~$ ls -al /media
total 28
drwxr-xr-x    5 root root  4096 Sep  8 10:26 .
drwxr-xr-x   22 root root  4096 Sep  6 09:54 ..
drwxr-xr-x    2 root root  4096 Dec 30  2014 cdrom
lrwxrwxrwx    1 root root     7 Sep  4 12:49 floppy -> floppy0
drwxrwxr-x    2 root root  4096 Sep  4 12:49 floppy0
drwxr-x---+ 249 root root 12288 Sep 12 16:55 mine
mine@mine-System-Product-Name:~$ ls -al /media/<user_name>

---

### Post by Bashing-om on 2015-09-12
zandu; Hello;

What we know:
sdc1 is filled to capacity per the 'df' result :
> 
/dev/sdc1 19G 18G 0 100% /

And per the 'du' result we can surmise it is within the /media directory:
> 
13513212	media

Now what we do not know is what is in the /media directory that can be moved or deleted to regain some disk space.
There is the sub directory "mine" . With no USB drive at all connected; Take a look and see what you can do :
```

ls -al /media/mine/

```

[INDENT][INDENT]Got to move stuff out
[/INDENT][/INDENT]

---

### Post by zandu on 2015-09-13
Hi Bashing-om  You are correct , I have now deleted them and all is back to normal thanks

---

### Post by Bashing-om on 2015-09-13
zandu; Outstanding !

Welcome to system administration ! Your feet are now wet, and you can jump into it full force.

As this situation is now concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Have fun
[INDENT][INDENT][INDENT]we will meet in the next adventure
[/INDENT][/INDENT][/INDENT]

---

