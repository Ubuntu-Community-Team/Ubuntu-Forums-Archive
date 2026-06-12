---
title: "hard drive is full... which one?"
date: 2013-11-17
forum: General Help
---

### Post by dorlow on 2013-11-17
Ok, I just got the pop up from my disk analyzer saying my hard drive is full.  I have two hard drives.  With linux showing all my drives as one huge file system, how do I tell which drive is full?  I have a 160 GB drive and a 1 TB drive.  I don't put hardly anything on my 160 GB drive because it's so small.  But I do have a lot on my 1 TB drive that I've been adding to for years, so it might be that drive.  But it's hard to tell in disk analyzer because both drives appear as one.  Is there a way to see them separate like a Windows machine would show you?

---

### Post by Petro Dawg on 2013-11-17
Please post the output for the following command in terminal...

```
df -h
```

---

### Post by dorlow on 2013-11-17
david@david-pc:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       144G  136G  1.2G 100% /
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           607M  892K  606M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G  408K  1.5G   1% /run/shm
/dev/sdd1       1.4T  805G  593G  58% /media/New Volume__
/dev/sdc1       466G  112G  354G  25% /media/Images

Ok, it looks like it's my first sata hd.  How do I run a treesize analyze only on my 160 GB HD?

---

### Post by Petro Dawg on 2013-11-17
Not sure if its what you are looking for, but you might find [GDMap]("http://gdmap.sourceforge.net/") useful.  I've used it before to quickly identify what's eating up all my space.  I believe its available in the software center.

---

### Post by deadflowr on 2013-11-17
Which version of Ubuntu?

Baobab, or as it is called Disk Usage Analyzer, shows the current disk usage, but not total drive space.

if you run it, it will show where the space is being used, from largest to smallest.
The /dev/sda1 will be marked /, and the /dev/sdd1 (1TB) will be marked under the /media.
The default will show the /  with the /media somewhere under that.

---

### Post by SeijiSensei on 2013-11-17
> **dorlow said:**
> Ok, it looks like it's my first sata hd.  How do I run a treesize analyze only on my 160 GB HD?

```

cd /
sudo du -sx * | sort -n

```

The "x" switch tells du not to follow mounted filesystems outside of / itself.  You'll get a list of the directories and their associated sizes.  If you need to drill down further, use cd to move to a directory of interest then repeat the du command.

You'll get a result like this:
```

du: cannot access &#8216;proc/27868/task/27868/fd/4&#8217;: No such file or directory
du: cannot access &#8216;proc/27868/task/27868/fdinfo/4&#8217;: No such file or directory
du: cannot access &#8216;proc/27868/fd/4&#8217;: No such file or directory
du: cannot access &#8216;proc/27868/fdinfo/4&#8217;: No such file or directory
0	initrd.img
0	proc
0	sys
0	vmlinuz
4	cdrom
4	dev
4	mnt
4	opt
4	srv
8	media
16	lost+found
84	root
400	tmp
1400	run
9368	bin
10332	etc
10468	sbin
32700	boot
223848	lib
978356	var
3030768	usr
37626552	home

```

Don't worry about those errors from proc.  They refer to a process that was running at the time du began which terminated before du was finished.  In this case the process had ID 27868.  Given the nature of Unix-based systems, processes come and go all the time.  I have filesystems mounted under /media which are ignored because of the "x" switch.

This is a fairly typical result where /usr, /var and /home are the largest directories.  The results are in megabytes, so home is about 37 GB in size.  Adding the "h" switch to du ("du -shx") gives "human-readable" results like "400K" or "37G", but they won't sort correctly.

Also, you'll find that even though other filesystems like the ones you have mounted under /media may have free space, trying to write to them if the root ("/") is full will fail.

---

### Post by dorlow on 2013-11-18
ok, i thought i had it figured out and today getting error messages again that i have less than a gig left.  what i figured out was to unmount all my drives except my system drive then run disk usage alayzer.  

well, if i run df, I show I'm 100% full...

david@david-pc:~$ df
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda1      150609124 141988068    963840 100% /
udev             1543288         4   1543284   1% /dev
tmpfs             620608       896    619712   1% /run
none                5120         0      5120   0% /run/lock
none             1551516       460   1551056   1% /run/shm
david@david-pc:~$ 


but disk usage analyzer shows i'm using 145 GB of 154 GB and have 8.8 GB left?  But I'm also getting pop ups saying I have less than a gig left.  Not sure why disk usage analyzer is disagreeing with the pop-up and the df command.

---

### Post by Impavidus on 2013-11-18
> **SeijiSensei said:**
> 

This is a fairly typical result where /usr, /var and /home are the largest directories.  The results are in megabytes, so home is about 37 GB in size.  Adding the "h" switch to du ("du -shx") gives "human-readable" results like "400K" or "37G", but they won't sort correctly.
Kilobytes, of course. And using sort with the option -h correctly sorts human-readable output from du:
```

cd /
sudo du -shx * | sort -h

```

Edit: Didn't see your new post.
5% of the disk space is reserved for root, which explains the 7GB difference. You can reduce that, but it won't matter that much. If you filled 95% of your drive you can (and probably will) fill the remaining 5% is about 1/19 of the time you needed to fill the first 95%. In other words, a month or so. Time to find where you stored all that data and move it over to the bigger disk.

---

### Post by philinux on 2013-11-18
For anyone else following this with similar issues. 
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

