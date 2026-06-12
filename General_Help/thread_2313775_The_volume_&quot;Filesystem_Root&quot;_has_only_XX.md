---
title: "The volume &quot;Filesystem Root&quot; has only XXX MB disk space available."
date: 2016-02-15
forum: General Help
---

### Post by Mark_in_Hollywood on 2016-02-15
Check if Already Posted asks for different search terms. I'm not computer literate enough to know any.

```
mark@Lexington:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
. . . 
/dev/sda1        20G   18G  556M  98% /

```

Ubuntu Tweak shows 195 meg can be cleaned. This msg. has been popping up for about two weeks.

What needs doing? I used to see 12g out of 20g used.

---

### Post by yancek on 2016-02-15
If you don't clean some files up it will soon be unable to function.  You can find large files to remove with simple commands such as the one below which finds all files over 50MB.  If you have data files you don't need, remove them.  You might check for old log files under /var/log.

> find / -size 50M

---

### Post by grahammechanical on 2016-02-15
At the Grub boot menu you can select Advanced options for Ubuntu and then select a recovery mode kernel and at the recovery menu select clean - try to make free space. That will run both the clean command and the autoremove command.

You might want to prepare for resizing that partition and increasing its size as you need a larger / partition. Do you have a separate /home partition? do you store data files on a separate partition? Either of these methods will prevent the Ubuntu partition from filling up.

Regards.

---

### Post by Mark_in_Hollywood on 2016-02-16
By the Numbers:

Following this [Recover Lost Disk Space]("https://help.ubuntu.com/community/RecoverLostDiskSpace"), I performed the following commands in the order given in this Help document. When I got to lost+found:

`lost+found` Folders
Each ext2/3/4 partition will contain a lost+found folder. This folder contains corrupted files discovered by the system during an fsck check.

How to Find It:

You can run the following to locate each lost+found folder and, optionally, see the size of each folder:

```
sudo find / -name `lost+found` | sudo xargs du -h
```

What I did was: ```
sudo find / -name `lost+found` | sudo xargs du -h > ~lostfiles.txt
```

That returns a lot of files, too many, files. Over 67,000 lines of filenames appear. Is there a way to remove "lost" files with a command line string? I tried:

```
mark@Lexington:/$ locate lost+found
/lost+found
/usr/sbin/mklost+found
/usr/share/man/man8/mklost+found.8.gz
mark@Lexington:/$ cd /lost+found
bash: cd: /lost+found: Permission denied
mark@Lexington:/$ sudo cd /lost+found
[sudo] password for mark: 
sudo: cd: command not found
```

no joy.

Next using gksudo nautilus to look inside the lost+found directory is confusing. It is _empty_, at least gksudo nautilus and +h, shows no objects in it. 

I tried to find the lost+found directory to do this:

[https://www.howtoforge.com/community/threads/lost-found-directory.4450/](https://www.howtoforge.com/community/threads/lost-found-directory.4450/)

```
cd /path/to/lost+found
rm -fr *
``` 

but cannot get to that directory (folder). 

The 'puter is starting to run erratically now, anybody got a clue as to how to delete the files in lost+found?

---

### Post by Mark_in_Hollywood on 2016-02-16
Your advice finds files in my /home at 50+M, but the problem is in root or /

Thanks.

---

### Post by Mark_in_Hollywood on 2016-02-16
> **grahammechanical said:**
> At the Grub boot menu you can select Advanced options for Ubuntu and then select a recovery mode kernel and at the recovery menu select clean - try to make free space. That will run both the clean command and the autoremove command.

You might want to prepare for resizing that partition and increasing its size as you need a larger / partition. Do you have a separate /home partition? do you store data files on a separate partition? Either of these methods will prevent the Ubuntu partition from filling up.

Regards.

I had run:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

prior to asking for help, this forum.

Yes, /home is a separate partition.

```
mark@Lexington:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on

/dev/sda1        20G   19G     0 100% /

/dev/sda2       890G  166G  680G  20% /home
```

I had used Ubuntu Tweak to remove old kernels prior to asking for help, this forum. It showed only 150± Meg to free. Two weeks ago, the / had 12 of 20 gig in use, 8 gig free. Something isn't adding up. 

Thanks.

---

### Post by dragonfly41 on 2016-02-16
Perhaps run[COLOR=#000000][FONT=courier new] **df -i** to check inodes?

[/FONT][/COLOR][http://www.ivankuznetsov.com/2010/02/no-space-left-on-device-running-out-of-inodes.html](http://www.ivankuznetsov.com/2010/02/no-space-left-on-device-running-out-of-inodes.html)

And another suggestion .. run System Tools > Disk Usage Analyser

It will take some time to render a picture of diskusage.

---

### Post by Mark_in_Hollywood on 2016-02-16
```
mark@Lexington:~$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
udev             495046    525   494521    1% /dev
tmpfs            505986    578   505408    1% /run
/dev/sda1       1281120 347611   933509   28% /
```

DU Analyzer runs and makes a bar chart but how does that help me solve this (becoming a) crisis?

---

### Post by dragonfly41 on 2016-02-16
Actually Disk Usage Analyser does not allow inspection of root folder. Sorry about that. It is useful for /home inspection.

It is a matter of inspecting root folder to see where the space is taken up.

You have used gksu nautilus. You can use Nautilus to look through the contents of computer > /root.

What I use as a GUI (and it is a personal choice) is Krusader file manager (krusader is in Ubuntu Software Centre) although some say it comes with too much kde baggage.

Krusader > Tools > Start Root Mode Krusader allows inspection of root folder. Hidden files can be enabled by
View > Show Hidden Files.

---

### Post by Mark_in_Hollywood on 2016-02-16
Does this help anybody to advise me what to do?

```
mark@Lexington:~$ sudo du -s -h -x /*
[sudo] password for mark: 
9.7M	/bin
91M	/boot
4.0K	/cdrom
4.0K	/dev
97M	/etc
165G	/home
0	/initrd.img
333M	/lib
3.7M	/lib32
4.0K	/lib64
16K	/lost+found
8.0K	/media
4.0K	/mnt
604M	/opt
0	/proc
22M	/root
1.4M	/run
13M	/sbin
4.0K	/selinux
4.0K	/srv
0	/sys
1.1G	/test4.img
4.0K	/tmp
6.8G	/usr
9.6G	/var
0	/vmlinuz
```

---

### Post by matt_symes on 2016-02-16
Hi

Please post back

```
sudo du -csh /var/*
```

I would be looking for the sizes of */var/crash* and */var/log*.

Kind regards

---

### Post by Mark_in_Hollywood on 2016-02-16
Thnx.

```
mark@Lexington:~$ sudo du -csh /var/*
[sudo] password for mark: 
18M	/var/backups
240M	/var/cache
[COLOR="#FF0000"]4.0K	/var/crash[/COLOR]
4.0K	/var/games
356M	/var/lib
4.0K	/var/local
0	/var/lock
[COLOR="#FF0000"]7.8M	/var/log[/COLOR]
4.0K	/var/mail
4.0K	/var/metrics
4.0K	/var/opt
0	/var/run
94M	/var/spool
8.9G	/var/tmp
9.6G	total

```

---

### Post by dragonfly41 on 2016-02-17
Viewing contents of my /var/tmp it is only a few MB. 
I would explore purging caches in that location ..

read here ... [http://ubuntuforums.org/showthread.php?t=2020676](http://ubuntuforums.org/showthread.php?t=2020676)

---

### Post by dragonfly41 on 2016-02-17
[Added Notes to above post]

You can continue using cli as you are doing .. but as an exercise I would run Disk Usage Analyser again (as suggested earlier). 
The low space issue is Filesystem Root ("/"  and not "/root").  That description can be confusing.

Bottom right of Disk Usage Analyser panel you can switch display between Rings Chart and Treemap Chart.  
Choose Rings Chart.

Now navigate to var > tmp to inspect content. Hover over the pie slices to see what is using up nearly 9 GB.

After you release space you might consider installing Ubuntu Tweaks to keep your system ship shape (clearing caches from time to time).

---

### Post by Mark_in_Hollywood on 2016-02-17
Mr. Dragon:

The search icon that brings up the "search your computer . . .", top left corner of my screen cannot find any program. That's a problem for another time.

I ran Ubuntu Tweak about 2 weeks ago and cleared the old kernels and all other useless cruft at that time. My problem persisted.

Running baobab via cli, as calling Disk Usage Analyzer thru the search icon cannot find anything, shows that /var/tmp has 307 files created by (probably) the printer's scanner driver. Because 305 identical filename all start with: cnijpwgtmp; I netsearched for that, up came from some site: [alatest]("http://alatest.com/reviews/printer-reviews/canon-maxify-mb2320/po3-211523072,31/") saying this:

[COLOR="#800000"]"If you have one and your (Linux) machine will not boot correctly do this from a command prompt: :/ >ls /var/tmp (look for files named "cnijpwgtmp". There may be a LOT of them) :/ >sudo rm /var/tmp/cni* (You will need to have administrator rights..."[/COLOR]

Then, after running the rm, /var/tmp went from 9gig to 12meg.

But while this may be the solution, it's temporary, as the scanner is dumping unneeded objects in /tmp and not cleaning them up upon exiting. That is also a problem for another day.

I'm going to mark this post as solved.

Thank you, Ubuntu Community.

---

### Post by dragonfly41 on 2016-02-17
Since you might have printer jobs queued look at [http://localhost:631/jobs/](http://localhost:631/jobs/)

---

