---
title: "Update Broken - dpkg: &quot;no space left on device&quot;"
date: 2015-08-19
forum: General Help
---

### Post by fxscully on 2015-08-19
The last automatic update was broken. Now it says I must: "sudo dpkg --configure -a" That does not work because dpkg claims that I am out of disk space - but that is completely untrue. Any suggestions?

---

### Post by Bashing-om on 2015-08-19
fxscully; Hello;

My bet is that it is a true condition. The system would not lie to you would it ?

Let's take a look at the disk space allocation.
Activate a terminal and execute:
```

df -h
df -i

```
My bet is that the /boot partition is full . In any event we will cope with the situation as presented.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by dino99 on 2015-08-19
hold the 2 latest kernel versions and purge the others ('synaptic' can easily help you doing that removal)

---

### Post by fxscully on 2015-08-19
Re: Disk Space: Did that already: /dev/sda8        22G   14G  7.3G  65% / The above says I have 7.3 G available. Also: I thought about purging the other kernels - takes some time, and (I think) would not solve this problem. The real root problem is that dpkg is not correctly reading the disk space. And another thing! I fell back to another (older) kernel and it would not "see" my wifi network! Kinda looks like a re-install situation.

---

### Post by ian-weisser on 2015-08-19
> **fxscully said:**
> Re: Disk Space: Did that already: /dev/sda8        22G   14G  7.3G  65% / 
Did you check your inodes, too?
Do you have a separate /boot partition on that list?
 
> **fxscully said:**
> The real root problem is that dpkg is not correctly reading the disk space.
Perhaps. Perhaps not.
Of the many dozens of "dpkg says I'm out of disk space" threads in this forum, I recall none where dpkg was incorrectly reading the disk space. I recall many with a full separate /boot partition or full inodes.
Nevertheless, congratulations if you have uncovered a new dpkg bug.

---

### Post by matt_symes on 2015-08-19
Hi

Reinstalling is a very windows solution and a bit premature I think ;) You are new to Ubuntu ?

Let bashing-om or Ian help you first.

Kind regards

---

### Post by fxscully on 2015-08-20
Since I don't have a lot of time my hands, I took the weasel way out: I did a new install on /dev/sda6.
The busted install is on /dev/sda8, which DF reports is not full up!
Inodes? Sorry, I don't know that much about linux!
Some day, when I have lots of time on my hands, I'll attempt a recover.
Thanks all!!
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        22G  4.0G   17G  20% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           397M  912K  396M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  136K  2.0G   1% /run/shm
/dev/sda9       181G   43G  130G  25% /home
/dev/sda1        22G   19G  3.8G  83% /windows
/dev/mmcblk0p1  7.5G  1.7G  5.8G  22% /media/3566-3732
/dev/mmcblk0p2  7.4G  4.1G  2.9G  59% /media/8gig_ext4
/dev/sda8        22G   14G  7.4G  65% /media/298b7668-d5a6-4923-a143-61a4d05b4560

---

### Post by deadflowr on 2015-08-20
> [COLOR=#000000]Inodes? Sorry, I don't know that much about linux![/COLOR]
The inodes would be listed in the second df command, the one with -i.

---

### Post by fxscully on 2015-08-20
Deadflowr:
Wow!! df -h reports 65% used; df report 65% used; df -i reports 100% used.!!
Now I am completely confused.
I kind of suspect that the dpkg failure caused the file system to fill w/ worthless stuff.
Been trying to find it to delete. Put several locked folders in my home directory.
What fun!

---

### Post by Bashing-om on 2015-08-20
fxscully; Hey hey;

Hanging with you; let me see what I can do to UNconfuse you .
inodes;
Consider it like this -overly simple, every file has to have an address in the file system. These 'addresses' are the inodes. When the partition is created there is a limited number of addresses that the system can allocate. When one runs out of addresses, can no longer create any files. A whole bunch of little bitty files can lead to a big problem.
On the plus side if you KNOW that you will require more inodes than is the default, when the partition is created there is a means to tell the system ya want MORE .

[INDENT][INDENT][INDENT]all in the process of learning
[/INDENT][/INDENT][/INDENT]

---

### Post by fxscully on 2015-08-21
Bashing-om!
Got it! Now I understand what is going on.
I moved the entire /var (directory and contents) to a different partition, updated fstab.
Still out of inodes for /.
Any suggestions as to where I might find a bunch of worthless files?

---

### Post by fxscully on 2015-08-21
Bashing-om!
Got it! Now I understand what is going on.
I moved the entire /var (directory and contents) to a different partition, updated fstab.
Still out of inodes for /.
Any suggestions as to where I might find a bunch of worthless files?

---

### Post by Bashing-om on 2015-08-21
fxscully; Yikes:

This is cause for just a bit of stress:
> 
I moved the entire /var (directory and contents) to a different partition, updated fstab.
Still out of inodes for /.


And yeah, we can look:
> 
Any suggestions as to where I might find a bunch of worthless files?


There is the tool 'du' for (d)isk (u)sage .
Let's see:
```

cd /
sudo du -sx * | sort -n
cd

```
Give the system some time to "work" and ignore " du: cannot access ‘proc " as "proc" is a virtual file system constantly changing and 'du' can not get a handle on it . If you need to drill down further, use cd to move to a directory of interest then repeat the du command.
The results are in megabytes, (The "x" switch limits du to a single file system, in this case the root file system.)

In many cases house cleaning helps - and if the system is stable will not hurt to run:
```

sudo apt-get update
sudo apt-get upgrade ##because I like to see what is going on and any 'held' packages
sudo apt-get dist-upgrade ##will duplicate 'upgrade'; the above applies
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get -f install
sudo dpkg -C

```

The results of 'du' will give us a strong hint on where to look for those "worthless files" .

[INDENT][INDENT]strong advocate here of
[INDENT][INDENT][INDENT]keep it simple
[INDENT][INDENT][INDENT][INDENT]keep it clean
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by fxscully on 2015-08-21
"cd /
sudo du -sx * | sort -n
cd"
That told me the most stuff was in /usr/scr.
I finally just erased everything in that folder.
I also erased all the old kernel stuff in the boot folder.
ran apt-get install -f
the update manager would now work and finished what it was doing.
Upshot: it looks like that installation (on sda8) is now recovered.
Also did the other apt-get things you suggested (but not the upgrade).
So, after about 5 hours of putzing around, problem fixed - but I did learn a lot though!!
Thanks Bashing-om!!

---

### Post by Bashing-om on 2015-08-21
fxscully; Well !

Making progress. look'n better allah the time.

> 
 but I did learn a lot though!!
Thanks Bashing-om!!

I am pleased to be of some small help - I do look forward to those situations that I too learn from.

BUT, I am concerned if you removed:
```

sysop@1404mini:/$ ls -al /usr/src/
total 40
drwxr-xr-x 10 root root 4096 Aug 18 12:06 .
drwxr-xr-x 10 root root 4096 May 19  2013 ..
drwxr-xr-x 24 root root 4096 Jul 23 10:47 linux-headers-3.13.0-58
drwxr-xr-x  7 root root 4096 Jul 23 10:47 linux-headers-3.13.0-58-generic
drwxr-xr-x 24 root root 4096 Jul 28 13:32 linux-headers-3.13.0-59
drwxr-xr-x  7 root root 4096 Jul 28 13:32 linux-headers-3.13.0-59-generic
drwxr-xr-x 24 root root 4096 Jul 30 11:10 linux-headers-3.13.0-61
drwxr-xr-x  7 root root 4096 Jul 30 11:10 linux-headers-3.13.0-61-generic
drwxr-xr-x 24 root root 4096 Aug 18 12:06 linux-headers-3.13.0-62
drwxr-xr-x  7 root root 4096 Aug 18 12:06 linux-headers-3.13.0-62-generic
sysop@1404mini:/

```
As with out the latest headers files one can not build any packages, or update the system properly.

And ---> " after about 5 hours of putzing around, " ->. generally if one is at the keyboard - not then getting into trouble, the likely hood of going to jail is minimal. That in and of it's self says this has not been a waste of your time and you have not been bored !

I consider this thread as having resolution to the original query If you agree then
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

IF there is consequent/other problems please open a new thread.

[INDENT][INDENT]otherwise ->
[INDENT][INDENT][INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

