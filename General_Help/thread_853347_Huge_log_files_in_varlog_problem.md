---
title: "Huge log files in /var/log problem"
date: 2008-07-08
forum: General Help
---

### Post by Hamstermerc on 2008-07-08
Hey so i booted up today to find my / directory apparently full. I have separate partitions for / and /home so i was confused as to how it got this big as most things for me are stored in /home (i think). I opened up the disk analyzer and found most of the taken up space was from /var/log .

Big offenders are syslog.0 (2GB+) daemon.log.0 (2GB+) syslog (800MB) and daemon.log (800MB)

I need to increase my / partition size anyway but can anyone tell me the importance of these files and if they can be completely removed or at least cleaned up. From what i've read they probably shouldn't be this big. 

Using Ubuntu 8.04 Hady Heron (fairly new user)

Any help much appreciated :)

---

### Post by Hamstermerc on 2008-07-08
bump

---

### Post by jocko on 2008-07-08
There should be no problem deleting those logs (or any other log).
```
sudo rm /var/log/syslo* /var/log/daemon.*
```But there must be something very weird with your system if the logs can become that large... As a reference, my /var/log only takes up totally 6.7 Mb (the largest file is 1.1 Mb, the rest ranges between 0 bytes to a few hundred kB).

My advice is that you run a fsck on your root (/) filesystem.
To force a fsck on the next reboot:
```
sudo touch /forcefsck
```

---

### Post by Hamstermerc on 2008-07-08
Cheers will give that a try. I thought it was a bit fishy that the files were so big

---

### Post by Hamstermerc on 2008-07-08
Well i deleted them and nothing majorly bad has happened. The scan on reboot didn't seem to find anything so i'm still left wondering why the logs are so big :(

---

### Post by SuperSlickNick2000 on 2008-11-20
Hi I am running Intrepid and I have the same problem. One thing I noticed is that this happens when the applications dd and klogd are running (and eating 30% and 20% of my cpu time respectively). I think this is a bug.

---

### Post by PMDirac on 2008-11-23
I also have this problem in Intrepid. I also noticed that this occured when dd and klogd were at the top of top. THis may have happened when an application (pidgin) crashed.


In my case, these 3 files: messages, kern.log, syslog are each > 4GB.

Does anyone konw what is causing this problem?

---

### Post by lswb on 2008-11-23
For the short term quick fix you can delete the log files.

The log files are normally kept at a reasonable size by a program called logrotate. This in turn is normally called by cron. So there a few possible points of failure here. If cron wasn't running you'd probably notice other problems as well, but check by running "pgrep -fl cron" in a terminal. If it doesn't return anything post back here.

Next make sure that these files exist: /etc/cron.daily/logrotate and etc/logrotate.conf

If either is missing try reinstalling logrotate.

---

### Post by c1rcu17 on 2008-11-25
> **SuperSlickNick2000 said:**
> Hi I am running Intrepid and I have the same problem. One thing I noticed is that this happens when the applications dd and klogd are running (and eating 30% and 20% of my cpu time respectively). I think this is a bug.

I have the exact same problem. These processes are filling up the logs like crazy. Thats why our log files are so incredibly bloated.

---

### Post by madverb on 2008-11-25
Here's an idea... read the logs and see what is filling them up.

```
tail /var/log/syslog
```

---

### Post by wknight8111 on 2009-01-18
I'm having the same problem, but at a larger magnitude. My three largest log files are all > 18GB and growing. Also, some of the archived tarballs are very large in their own right (> 350 MB). If the tarballs are so huge, it doesn't matter if logrotate is working properly because eventually my disk is going to fill up with logfile tarballs!

cron is installed and running. 

tail didn't reveal anything interesting about the logfiles, at least not to my eyes.

I'm reinstalling logrotate now and I've deleted most of the offending logfiles and tarballs now.

---

### Post by pablopancho on 2009-01-19
What kernel do you have? After I upgraded to kernel 2.6.27-10 this problem was solved. Apparently there was a bug in kernels 2.6.27-8 and 2.6.27-9.

---

### Post by kbloem on 2009-02-03
I have this problem also.....

---

### Post by ollesbrorsa on 2009-02-03
Hello all,

This seems familiar... ;)

Check out [**this thread**]("http://ubuntuforums.org/showthread.php?p=6200061") and in particular [**this post**]("http://ubuntuforums.org/showpost.php?p=6200061&postcount=8").

Good luck! 
/ollesbrorsa

---

### Post by cyclobs on 2009-02-03
they're not that imprtant. only if you are having a major issue and you need to find out what exacually is causing the problems then that would be the use of them. if they don't hold anything important and using u p THAT much space then defently rm them

---

### Post by ArgentStar on 2009-11-20
I had this same problem.  Two log files in /var/log were ~18GB each.  Every time I open the log file viewer it crashed - unsurprisingly.  So I deleted them, emptied the wastebasket and rebooted.

Now I get the same message, except those files don't exist.  Every time I reboot/log-in I'm told I've only 950MB space left.  But when I click Examine and see where the files are I get something very odd.  At the top it tells me my total space on the partition is ~50GB, my used space it ~47GB and my free-space ~3GB.  However,in the break down of file distribution below, the files only total ~9.5GB.  

I've searched through the whole file system, nothing is taking up that extra ~40GB, yet I'm getting the Low Disk Space error message and the Disk Utility program tells me 98% of the partition is full.

I have a horrible feeling I'm missing something blindingly obvious, but I'll be damned if I can... err... see it.  Look like the two mega log files have been deleted by this isn't being registered properly for some reason.  I've run fsck at boot and had no luck.

Ubuntu 9.10
Kernel Linux 2.6.31-14-generic
Gnome 2.28.1

Hugely appreciative of any help or advice anyone could offer, please. :)

---

### Post by claschxtreme on 2009-11-29
> **ArgentStar said:**
> 

Now I get the same message, except those files don't exist.  Every time I reboot/log-in I'm told I've only 950MB space left.  But when I click Examine and see where the files are I get something very odd.  At the top it tells me my total space on the partition is ~50GB, my used space it ~47GB and my free-space ~3GB.  However,in the break down of file distribution below, the files only total ~9.5GB.  

....

I have a horrible feeling I'm missing something blindingly obvious, but I'll be damned if I can... err... see it.  Look like the two mega log files have been deleted by this isn't being registered properly for some reason.  I've run fsck at boot and had no luck.

Ubuntu 9.10
Kernel Linux 2.6.31-14-generic
Gnome 2.28.1

Hugely appreciative of any help or advice anyone could offer, please. :)

I'm fixing this problem  so i can give you some pointers to solve it:

The reason why these log files are getting huge is usually not a bug but instead some piece of hardware that is malfunctioning or perhaps (ex: old cards) lacks the proper functionality required.
The main approach would be to look into them to see what's wrong, which line is repeated over and over again.
In my case is a faulty sound card, filling up the system partition very quickly, max 3 days, due to the rapid pace with which some alsa modules have to be restarted. As far as i can see there's nothing wrong with Alsa or Pulse Audio.

Now, in your case i assume that you started nautilus with root privileges, went directly to /var/log and sent the abnormally huge files dancing to your trashbin, or so you thought you did. If this is the case you only sent them to /root/.local/share/Trash, to really purge them from your system you need to issue the following command in console:

```
sudo rm -rf /root/.local/share/Trash
```

Don't worry about deleting the whole Trash-folder, it will be automatically recreated if needed. 

Remember that there can be more/many huge files named: messages.0 , messages.1 ... syslog.0 , syslog.1 ... user.log.0 , user.log.1 ... in /var/log
make them go away for good using the same tactic:

```
sudo rm -rf /var/log/messages.*
``` ... and so on
```
sudo rm -rf /var/log/syslog.*
```
```
sudo rm -rf /var/log/user.log.*
```

Good luck and good hunting !!

---

### Post by dcstar on 2009-11-29
> **ArgentStar said:**
> 
........
I've searched through the whole file system, nothing is taking up that extra ~40GB, yet I'm getting the Low Disk Space error message and the Disk Utility program tells me 98% of the partition is full.
........
Hugely appreciative of any help or advice anyone could offer, please. :)

```
gksudo baobab
```

---

### Post by itix on 2009-12-06
This just happened to me and when I checked the log files, nm-pptp was the sole wrongdoer. It had virtually flooded the log files with junk and what seemed to be connectivity problems.

---

