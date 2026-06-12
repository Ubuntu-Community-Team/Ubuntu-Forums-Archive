---
title: "Update fills root partition"
date: 2012-12-18
forum: General Help
---

### Post by Statia on 2012-12-18
Hi,

Something went horribly wrong. I checked for updates today (last time I did that was about two and a half day ago) and there were important security updates, kernel 3.2.0.35 and some apport updates. I noticed a lot of big writes to my root partition looking at gkrellm and then I saw my root partition filling up quickly. It was using about 13GB, now it is 100% full, using 28.931MB and the update process is stuck at 61%. 
Where do I start trouble-shooting this and have more people encountered this problem?

My system:
Kubuntu 12.04.1
KDE 4.9.4
kernel 3.2.0-34-generic.

```
$ df -h
Filesystem                            Size  Used Avail Use% Mounted on
/dev/sda5                              29G   29G     0 100% /
udev                                  3.9G  4.0K  3.9G   1% /dev
tmpfs                                 3.9G  144K  3.9G   1% /tmp
tmpfs                                 1.6G  1.4M  1.6G   1% /run
none                                  5.0M  4.0K  5.0M   1% /run/lock
none                                  3.9G   44M  3.9G   2% /run/shm
/dev/sda1                             179M   72M   97M  43% /boot
/dev/sda3                              27G  4.9G   21G  20% /mnt/data
/dev/sdb1                             450G  226G  202G  53% /home
/dev/sdb6                             704M   17M  651M   3% /srv
/dev/sdb5                             1.2G  1.1G   98M  92% /var
tmpfs                                 3.9G   12K  3.9G   1% /var/spool
tmpfs                                 3.9G  324M  3.6G   9% /var/tmp
tmpfs                                 3.9G  191M  3.8G   5% /var/cache/apt/archives

```

---

### Post by dannyboy79 on 2012-12-18
I can't believe your root partition is 29GB in size. first go to /var/log/ and remove any gigantic log files, you don't need them and are there only for informational purposes. See if that makes any difference.


also run the following commands (they may fail due to an update process is in effect which has effectively locked changes to apt.

```
sudo apt-get clean
```
this will Clear out the local repository of retrieved package files. It removes everything but the lock file from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/

```
sudo apt-get autoclean
```
Like clean, autoclean clears out the local repository of retrieved package files. The difference is that it only removes package files that can no longer be downloaded, and are largely useless. This allows a cache to be maintained over a long period of time without it growing out of control. The configuration option APT::Clean-Installed will prevent installed packages from being erased if it is set to off.

---

### Post by SeijiSensei on 2012-12-18
Since the big things like /home are stored elsewhere, I'd suggest there are a couple of possibilities.

First try taking a census of the directories on /.  

```

cd /
sudo du -s *

```

You'll get a list of each directory and the amount of space it is using.

Most of the time the largest consumers of space are in /var, particularly /var/log.  If you only have very large files like /var/log/syslog, but no previous versions with names like /var/log/syslog.1 or /var/log/syslog-20121130, then [logrotate]("http://articles.slicehost.com/2010/6/30/understanding-logrotate-on-ubuntu-part-1") is not running correctly.  

Usually the root partition is pretty small, less than 10 GB, if you have separately mounted filesystems for things like /home.  On this Kubuntu 12.04 installation, I have about 3 GB in /usr, another 900 MB in /var, and a total of about 5 GB in the root filesystem.

One other thing you can try is booting into recovery mode and unmounting all the other filesystems like /home.  Then run du.  If a filesystem fails to mount, anything written there, say to /home, will be placed in the filesystem root where the mount point resides.  Then when the problem is fixed, and /home is remounted, the stuff written before is hidden from the operating system but still takes up space in the root partition.

---

### Post by Statia on 2012-12-18
> **dannyboy79 said:**
> I can't believe your root partition is 29GB in size.

It wasn't before I started the upgrade, that is the whole problem.
I appreciate that you try to help, but did you read my post?

>  first go to /var/log/ and remove any gigantic log files,/var is on a separate partition. Again, I fear you did not take the time to read my post attentively.

 

> 
also run the following commands (they may fail due to an update process is in effect which has effectively locked changes to apt.As I said, the update process is stuck at 61%, so yes, this fails indeed.

---

### Post by dannyboy79 on 2012-12-18
> **Statia said:**
> It wasn't before I started the upgrade, that is the whole problem.
I appreciate that you try to help, but did you read my post?

/var is on a separate partition. Again, I fear you did not take the time to read my post attentively.

 

As I said, the update process is stuck at 61%, so yes, this fails indeed.i noted you had a seperate /home but didn't notice the seperate /var/, sorry. Perform what SeijiSensei suggests to find the culprit large files.

---

### Post by Statia on 2012-12-18
Thanks both. Cheers for the quick response! Nor du nor Baobab revealed anything wrong.
I have tried a reboot and that hung. Alt-SysRq-REISUB to the rescue. Rebooted and selected the normal 3.2.0-34, not even recovery mode and the system runs again, root partition is back at 13.209MB. Still big, but I have everything and the kitchen sink installed.
I am going to try this upgrade again, but this time from the command line, so I will have a better view of what is happening.

---

### Post by Statia on 2012-12-18
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```And running that completed what went wrong before (and somehow shat all over my root partition).
Now a reboot to see if 3.2.0-35 will boot.

---

### Post by Statia on 2012-12-18
Running 3.2.0-35 now, disk usage still normal.
I'll mark this thread as solved in the sense that I have a healthy, running system again, but it remains a mystery what happened.

---

### Post by SeijiSensei on 2012-12-18
13 GB is plausible, but still awfully high for a system that has separate /home and /var.  I really suggest the method I described before of unmounting everything and running du against just the root filesystem.  I bet you might find some mount points that have files stored in them that appear invisible when the actual filesystems are mounted on top of them.

---

### Post by Statia on 2012-12-18
There is about 12 Gig in /usr. Mostly games that take up lots of space: Sauerbraten, FlightGear, Alien Arena, Unigine Heaven, Doom 3. Doom3 alone is 1.6G.
So I don't think there's any hidden cruft.

---

### Post by Statia on 2012-12-18
As for the cause of the snafu: I think the system was upset because my gf had been working on it yesterday. She's like the dude in this comic:

[http://xkcd.com/1084/](http://xkcd.com/1084/)

---

### Post by dannyboy79 on 2012-12-18
> **Statia said:**
> There is about 12 Gig in /usr. Mostly games that take up lots of space: Sauerbraten, FlightGear, Alien Arena, Unigine Heaven, Doom 3. Doom3 alone is 1.6G.
So I don't think there's any hidden cruft.ah, makes sense. Im shocked you have seperate partitions for all those other folders but not /usr IF you are a big gamer and install your games to /usr

glad you got it sorted.

---

### Post by Statia on 2012-12-18
> **dannyboy79 said:**
> ah, makes sense. Im shocked you have seperate partitions for all those other folders but not /usr IF you are a big gamer and install your games to /usr



The fun thing is, I'm not even that much of a gamer. I just install stuff and try it out. I'm not sure if having a separate /usr has much additional value for me, but I might consider it if I ever do a reinstall or move to a new pc. Half of my SSD is not used now, maybe I should move /usr there.

---

