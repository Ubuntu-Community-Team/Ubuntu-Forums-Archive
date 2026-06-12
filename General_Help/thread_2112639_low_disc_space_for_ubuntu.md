---
title: "low disc space for ubuntu"
date: 2013-02-05
forum: General Help
---

### Post by lenypl on 2013-02-05
i am using ubuntu12.04. i have a 320 gb hard disc. partitioned 275-32-13. i use 13gb for ubuntu. 32for windows7.275for my common files like videos,songs etc. now my system shows low disc space in ubuntu drive .also say to move unused programes to other drive. i am not a computer expert. i want to know which one is unused. is there any application to find this out?. is there any way to increase my drive space. i have enough space in 275 gb file system.

---

### Post by ibjsb4 on 2013-02-05
13 gig is enough for an ubuntu install, but your not going to be able keep many files on it,  Lets see what it looks like.  In terminal:

```
df -TH
```

---

### Post by Impavidus on 2013-02-05
I don't see why you would move unused programs to the other partition (drive in windows parlance). Uninstalling seems easier.

You can make the partition bigger. Make backups of your important files on an external drive, boot using a live cd (the one you used to install ubuntu), shrink the shared partition and expand the ubuntu partition. If this requires moving the windows partition things get more complicated. For changing partitions you can use gparted, included on the live cd.

I suggest you make the ubuntu partition about 25GB.

---

### Post by Bucky Ball on 2013-02-05
*Thread moved to **General Help**.*

> **ibjsb4 said:**
> 13 gig is enough for an ubuntu install ...

```
df -TH
```

Agreed. Providing you haven't got loads of personal data stored in the /home directory on the / partition. 

Have you installed thousands of apps? Can you think of anything on the Ubuntu install / partition that might be taking up all that space? A few large HD video files?

---

### Post by elliotn on 2013-02-05
I once had such problem too , only to find that I deleted staff while I was in root only to find that the items moved in a root trash.... am not sure if its /bin/trash I can remember

---

### Post by Bucky Ball on 2013-02-05
Good point. You might have something real bulky in trash. Just a shot ...

> **elliotn said:**
> ... am not sure if its /bin/trash I can remember

/usr/bin I think.

---

### Post by Impavidus on 2013-02-05
Of course, some applications need lots of data (flight simulators and planetarium programs come to mind, they can use tens of GBs). If that's the case you may be able to move their data directory to another partition.

---

### Post by Bucky Ball on 2013-02-05
Better still another drive. ;)

---

### Post by vanadium on 2013-02-05
13 GB should be plenty for the linux system files, even if you have many applications installed. Next to the already mentionned root trash, there are other possibilities why a (relatively) small root partition in combination with a separate /home can fill anyway.

- TEMPORARY FILES: In a standard install, /tmp and /var/tmp are also on the root partition. If you use applications such as audacity, that write a lot of temp data in one of these directories, you may run into trouble.

With my 9.3 GB system directory, I redictect /tmp and /var/tmp to my large /home partition. This can be achieved with mount bind commands in /etc/fstab.
* Make directories in your /home and give them the same permissions as the original temp directories:
```

mkdir -p /home/temp/tmp /home/temp/var/tmp
sudo chmod -R u+rwx,g+rwx,o+rwt /home/temp

```

* In /etc/fstab, include the lines
```

/home/temp/tmp /tmp none bind
/home/temp/var/tmp /var/tmp none bind

```
to redirect both system temporary directories to the large /home partition. (A more "classical" approach is to have separate partitions for each. This is suited for servers, but unwieldy on personal computer systems).

- HUGHE LOG FILES: When a root partition fills up, an unfortunate reaction of linux is that it starts to log as crazy. These logs can become hughe and in their own be the main culprit of a filled system dir. You should then rotate the logs and delete the massive log files. I once had to do that using these instructions: [http://ubuntuforums.org/showpost.php?p=10114103&postcount=3](http://ubuntuforums.org/showpost.php?p=10114103&postcount=3)
> 
if you want to force a log rotation, you can run the command /usr/sbin/logrotate -f /etc/logrotate.d/rsyslog and it will rotate the log. If you want to delete the massive file (since by default, on Ubuntu, logrotate needs 7 days before it deletes syslog and syslog related file which includes daemon.log) then run rm -v /var/log/syslog /var/log/daemon.log && /usr/sbin/logrotate -f /etc/logrotate.d/rsyslog. This will make sure the new file is properly created so that the daemons which log to it can continue to run.

---

### Post by lenypl on 2013-02-13
in terminal df-th shows

---

### Post by ibjsb4 on 2013-02-13
Yep, its full.  Lets see if you have any files larger than 1G.

```
**sudo find / -name '*' -size +1G**
```

And here's some reading material :)

[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by lenypl on 2013-02-22
hi,
i format  and install ubuntu from a live cd. now my some other problems alsofixed.previously i do a internet upgrade. now i am experiencing a faster and better ubuntu

---

