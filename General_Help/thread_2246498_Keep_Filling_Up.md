---
title: "Keep Filling Up /"
date: 2014-10-01
forum: General Help
---

### Post by Quarkrad on 2014-10-01
I did a clean install of 14.04 with separate** /** and **/home** using a 30GB partition for** /** and  93GB partition for** /home** - I had an error with Filesystem Root havng no disk space left so in the end I reinstalled 14.04 yesterday.  I chose the option of putting **/** on the 30GB partition and formating it, so there was a clean install, and putting **/home** on the 93GB partition but not formatting so I keep my old files/folders.  Today I now find **/ **is full up again - the attached picture shows GParted showing the 30GB partiton is full.  This cannot be right - any advice appreciated.

---

### Post by ian-weisser on 2014-10-01
Boot from a LiveUSB, mount sda1, and look around.

Look for a /home that's on the wrong drive.
Look for a huge log in /var/log

You can also install any of the several disk utilities that will graphically display disk usage.

---

### Post by Quarkrad on 2014-10-01
That helped a lot.  83% of **/** is taken up by **media/xxx**.   Prior to having a separate **/ **and **/home** I had other partitions for things like backup and personal files - these appeared in nautilus as **/media/xxx** etc and as I have got use to Ubuntu I accept that other partitions appear under **/** as** /media/xxx**.  Now I have a separate** / **and **/home** I also see **/media/xxx** under **/** but it looks as if there is a duplicate **media/xxx** installed in my 30GB **/** partition.  What I do not know is how to look in each partition - this way I could see if I have a duplication of **/media/xxx** or some other issue.  To be honest I do see how the data in my other partitions are appearing/filling up my 30GB **/** partition.

---

### Post by sotiris2 on 2014-10-01
I may be misunderstanding you but partition mounted on /media are not copied to the / partition and so do not actually take up space.  Is /media/xxx the actual folder? Or do you mean /media/homefiles? Because in the second case they are on a different partition and are not 'counted' in / . If its really /media/xxx (or generally media/nothomefiles) then it could be actually on the root partition but you should first check with ```
mount
``` to see if anything is mounted on it.

---

### Post by Quarkrad on 2014-10-01
I have two hard disks.  The first HD has three active partitions - sda1 (30GB) which is **/**, sda2 (93GB) which is **/home** and sda4 (337GB) which is called homefiles.  The second HD has just one partition sdb1 (465GB) called backup.  The output of the mount command is[B]:

liz@lizubuntu:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)
/dev/sda2 on /home type ext4 (rw)
/dev/sdb1 on /media/backup type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)[/B]

I'm a newbie with all this but I'm suprised **sda4 homefiles** is not shown above.  I'm confused a little as Disk Usage Analyser shows **/ ** as 29GB/29GB (I assume this means full up as per GParted confirms) but when I expand it I get bab1 (attached) that, seems to me, say it is 100% used and is 4.8GB in size.

---

### Post by Quarkrad on 2014-10-01
Woops - homefiles was not mounted!  I re-ran the mount command and it makes sense - i.e. it shows sda4.   However, what is taking up all the space in **sda1 /**?

[B]liz@lizubuntu:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)
/dev/sda2 on /home type ext4 (rw)
/dev/sdb1 on /media/backup type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda4 on /media/homefiles type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)[/B]

---

### Post by mcduck on 2014-10-01
The Disk Usage Analyser might be a bit confusing, *it's not really meant to be used to tell how much free/used space there is on a drive*, and the percentages you see aren't telling that either.

Instead, it's used to help to figure out *where* the space is used. So the location you are scanning (in your pic "/") is always 100% (as in "100% of the files you are right now looking at".  And the percentage values under it tell how much of that 100% is used by each directory (for example it's telling you that 78.8% of your "/" contents are inside /usr, 14% in /var and so on).

However the interesting thing here is that it only sees 4.8GB of data in all of your / filesystem, while both the warning message and GParted see it as almost full 28GiB...  Did you create the /home partition during install, or afterwards? And if it was created afterwards, did you delete everything inside the /home before mounting the new partition in it's place? There seems to be quite a lot of data around that's not visible to the Disk Usage Analyser...
it's not really meant to be used to tell how much free/used space there is on a drive

edit: Also keep in mind that when you run the Disk Usage Analyser from your desktop, you are running it as normal, unprivileged user, so it's not even able to read lots of the contents of certain locations, like root user's home directory (/root). 

If you just want to check how much space is used/free on various filesystems, I recommend just checking the "File Systems"- tab in the System Monitor. Or running "df -h" in a terminal.

---

### Post by Quarkrad on 2014-10-01
During install.  Originally I  had a clean HD and set up all the partitions via the install process and configured for separate / and /home.  When / became full and I got the warning message I joined in on a similar posting on this site but I got lost in the original posting.  In the end, because I had no answer, I decided to re-install / again by formatting sda1 but not formatting sda4 as per #1 above.  Now / has filled up again I have created this separate post - I did not install sda4 (/home) after the install because it was already there but I can see how you could say it was install afterwards in the sense that all that was installed from the 14.04 USB was sda1. Yes - there does seem to be a lot of data not visible to the Analyser.

---

### Post by mcduck on 2014-10-01
So when you did the reinstall, did you tell it to mount sda4 as your /home *during the install* or afterwards?
Anyway, one thing worth doing is using "*du*" to check the disk usage of various locations. Open a temrinal, cd into /, and run the following command:
```
sudo du -xh -d1 | sort -hr | head
```
(it will check the disk usage of directories on the root filesystem only, and then sort them from highest to lowest and display the largest ones. And isnce youexecute it with "sudo", it's able to look at the sizes of various fiels and directories normal suer's can't access).

If anything looks large, you can then *cd* into that directory, and run the command again. Continue until you find out where the disk space has disappeared. Like this:
```

mcduck@Hyperion:~$ cd /
mcduck@Hyperion:/$ sudo du -xh -d1 | sort -hr | head
[sudo] password for mcduck: 
28G	.
18G	./home
6.3G	./usr
1.8G	./lib
877M	./opt
851M	./var
333M	./boot
73M	./etc
12M	./sbin
9.6M	./bin
mcduck@Hyperion:/$ cd /home/
mcduck@Hyperion:/home$ sudo du -xh -d1 | sort -hr | head
18G	./mcduck
18G	.
mcduck@Hyperion:/home$ cd mcduck/
mcduck@Hyperion:~$ sudo du -xh -d1 | sort -hr | head
18G	.
5.0G	./.local
4.2G	./Programs
2.2G	./.cache
1.3G	./.technic
933M	./Projects
800M	./Pictures
554M	./Downloads
504M	./Desktop
398M	./Documents

```

...and if even that doesn't work and the disk usage stil doesn't seem to add up correctly, I'd place my bets on something being mounted over a directory that already contained files.

---

### Post by Quarkrad on 2014-10-01
I asked Ubuntu to mount sda4 as /home during the install but not to format it (as it is my understanding that this way you keep the original files/folders that are in /home - i.e. you only install a new operating system).   Your command has identified the error I believe:

[B]liz@lizubuntu:~$ cd /
liz@lizubuntu:/$ sudo du -xh -d1 | sort -hr | head
[sudo] password for liz: 
28G	.
23G	./media
3.6G	./usr
640M	./var
281M	./lib
34M	./boot
15M	./etc
12M	./sbin
9.7M	./bin
1.1M	./root
liz@lizubuntu:/$ cd /media
liz@lizubuntu:/media$ sudo du -xh -d1 | sort -hr | head
23G	./backup
23G	.
4.0K	./liz
4.0K	./homefiles
liz@lizubuntu:/media$ [/B]

I have stopped here as it looks to me that the 30GB sda1 partition also contains 23GB of /media.  This is odd to me as /backup is my sdb1 partition on my 2nd HD.  But gparted reports that /backup is 147GB.  There is also something very odd - I have closed everything down on my Desktop and re run the command:

[B]liz@lizubuntu:~$ cd /
liz@lizubuntu:/$ sudo du -xh -d1 | sort -hr | head
[sudo] password for liz: 
4.6G	.
3.6G	./usr
640M	./var
281M	./lib
34M	./boot
15M	./etc
12M	./sbin
9.7M	./bin
1.1M	./root
16K	./media
liz@lizubuntu:/$ [/B]

very different!

---

### Post by mcduck on 2014-10-01
*du -xh* will not access any other filesystems, so anything it sees inside /media would actually be in your /dev/sda1 partition. Perhaps you have at some point accidentally ran the backups while your backup partition wasn't mounted? Make sure /dev/sdb1 is unmounted, and take a look in /media/backup. You should see empty directory...

---

### Post by Quarkrad on 2014-10-01
No - when I do this and look in /media/backup I see two folders **homefiles** and **liz**.  (Which is what I would expect to see as I backup liz (/home) and homefiles (sda4, my personal files) from HD1 to sdb1/backup on HD2.  These two folders in backup equate to 22GB.

---

### Post by mcduck on 2014-10-01
If anything exist in that directory even when your actual backup partition (/dev/sdb1) is unmounted, the data is definitely sitting on your main partition, probably just as I suggested, because of the backup running at some point while sdb1 wasn't mounted. 

In that case I'd recommend checking that the backups on sdb1 are correct, unmounting sdb1, and then simply deleting any contents of /media/backups to clean the files that have ended on sda1 instead of sdb1. (be extra careful, of course, you don't want to delete any of the real backups on the sdb1 by accident so double check it's unmounted before you delete anything!)

edit: If you want to be absloutely sure, you can use the "df" comamnd to check what device a fiel or directory is located in (of course if you have anythign mounted over existign files even df won't report that, but at least this way you can be absolutely sure the files you delete really are on your sda1 before you do anything:
```

mcduck@Hyperion:/media$ ls 
mcduck
mcduck@Hyperion:/media$ df mcduck/
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda5       38314312 28930748   7414108  80% /
mcduck@Hyperion:/media$ cd mcduck/
mcduck@Hyperion:/media/mcduck$ ls
40F24487F2448360
mcduck@Hyperion:/media/mcduck$ df 40F24487F2448360/
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda2      607066108 316115040 290951068  53% /media/mcduck/40F24487F2448360

```

---

### Post by Quarkrad on 2014-10-01
That did it - many many thanks.  For my understanding - are you saying that when I do a backup to sdb1 I must make sure that sdb1 is mounted.  If it isn't the backup could/will(?) end up in /.

---

### Post by mcduck on 2014-10-01
That's correct. If the drive isn't connected, anything you try to write to in ends in the drive where the mount point is (pretty much always your /). So if you are making backups to a removable drive, for example, you probably don't want to set your backups to run automatically, but instead run them manually when you know you have the backup drive connected...

(If the backup drive is internal one, then you might want to configure it in /etc/fstab so that it will always be mounted straight from the boot. On the other hand backups made on a drive that's always connected to the computer aren't really that useful so I'd recommend against doing that, at least unless you also regularly make backups to some removable drive or other location that's separate from your computer...)


Anyway, it's good to hear that this sorted out the problem and you got your disk space back. :)

---

