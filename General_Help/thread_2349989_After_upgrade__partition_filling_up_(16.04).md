---
title: "After upgrade / partition filling up (16.04)"
date: 2017-01-20
forum: General Help
---

### Post by jeromeo2 on 2017-01-20
After a recent upgrade to 16.04 the root partition fills up to almost 100% overnight.  After rebooting in the AM the space is cleared and below 20%.  I can slowing watch the disk space diminish as the day wears on. Again, it fills up to almost 100% and in the morning the reboot clears whatever files are written.  Does anyone know what might be going on?  I did not have this issue with 15.04.

Thanks,
jeromeo

---

### Post by oldfred on 2017-01-20
What Brand/model system.

Some Asus have a run away log file issue.

 Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

---

### Post by SeijiSensei on 2017-01-20
The fact that the disk usage drops after a reboot is a bit mysterious.  If it were a problem with log files, then those files would persist through a reboot.  A browser cache might display these symptoms, but caches are rarely big enough to exhaust free space.

Do you have everything including /home and /var in a single filesystem?  How big is it?  Next time, before rebooting run the command

```
cd /; sudo du -s *
```

and post the results inside [noparse]```

```[/noparse] tags so we can see where the large directories are.

---

### Post by jeromeo2 on 2017-01-20
I'm running a Dell PowerEdge T110 with Kubuntu only (no windows, no dual boot).  The Server is 1 year old and has been running 15.04 since with no issues.  When I upgraded to 16.04 this started to occur.  Yes /home and /var are on the same filesystem.  /var total is 1.3G  and /home is 1.6G and these never waver far from those sizes.  The hard drive itself is 500 GB.  I actually have 2 500G drives the 2nd is mirroring the main drive.  I will post the results tomorrow morning.  Thanks.

---

### Post by jeromeo2 on 2017-01-20
I'm sorry /home and /var are not in the same file system.

---

### Post by jeromeo2 on 2017-01-20
Found the file that keeps growing.  It is in the /tmp directory and named "file6clzKH".  I believe it is some sort of log when the system boots.  It is filled with 
log_kioremote: RemoteDirNotify::FilesChanged and it continues to write this same message to the file the entire time the system is running.  I believe it has something to do with xsessions.  I have two users who log in use use X11 to run GUIs for a pagination application.  I believe it is a bug with no reported fix.  Unless someone else has found a fix.

---

### Post by SeijiSensei on 2017-01-20
I have a vanilla Kubuntu 16.04 installation running in a VM.  I don't have any files like that.  Sounds like that pagination application might be at fault.  Have you tried deleting the file, then running that application to see whether it generates those errors?

---

### Post by jeromeo2 on 2017-01-21
Yes it is not the application it's running on a separate partition and includes all users, configurations, scripts, application, and files.  This application is proprietary and we have been using it for years on Unix and an updated version for linux for 2 years and never had this issue until I upgraded to 16.04 for security reasons and stay up-to-date.  I just found out I was wrong about finding the problem. The / partition is at 83% this morning.

The /export is reporting correctly it is on a separate partition, in fact it is simply an access point for Mac's to get to production files and is on the /Penta partition.
The /mnt is is correct as it is where the backup drive is located.

**administrator@LS16**:**~**$ cd /; sudo du -s *
[sudo] password for administrator: 
12908	bin
101416	boot
4	cdrom
0	cr
84	dev
13376	etc
149787168	export
1668316	home
0	initrd.img
0	initrd.img.old
4	jcameron-key.asc
522612	lib
16	lost+found
20	media
172960808	mnt
4	opt
du: cannot access 'proc/14226/task/14226/fd/3': No such file or directory
du: cannot access 'proc/14226/task/14226/fdinfo/3': No such file or directory
du: cannot access 'proc/14226/fd/3': No such file or directory
du: cannot access 'proc/14226/fdinfo/3': No such file or directory
0	proc
680400	root
83940	run
12856	sbin
4	snap
4	srv
0	start
0	stop
0	sys
80	tmp
4177260	usr
1323320	var
0	vmlinuz
0	vmlinuz.old
4	webmin-setup.out


Filesystem     1K-blocks      Used Available Use% Mounted on
udev             4111732         0   4111732   0% /dev
tmpfs             826144     81792    744352  10% /run
/dev/sda2       16067384  12583460   2648344  83% /
/dev/sda5       24059020   4222248  18591588  19% /usr
tmpfs            4130716        84   4130632   1% /dev/shm
tmpfs               5120         0      5120   0% /run/lock
tmpfs            4130716         0   4130716   0% /sys/fs/cgroup
/dev/sdb1      372908864    510720 353432384   1% /mnt/HD2
/dev/sda1       10079084    123884   9443200   2% /boot
/dev/sda6        7932336   1360984   6145368  19% /var
/dev/sda7      395511172 149855168 225542136  40% /Penta
tmpfs             826144         0    826144   0% /run/user/117
tmpfs             826144        12    826132   1% /run/user/1000
/dev/sdd1      307529848 172582476 119302700  60% /mnt/RD1000-320GB

Thanks

---

### Post by geeksmith on 2017-01-21
Have you tried using lsof to see which process is writing to that file?

---

