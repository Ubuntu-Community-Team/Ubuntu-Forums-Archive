---
title: "Which Process is Accessing My Disk?"
date: 2007-10-20
forum: General Help
---

### Post by RandySavage on 2007-10-20
I have searched the forums, and elsewhere on-line, and read a lot of stuff, but I have yet to find out the answer to the possibly elementary question.  That question is:

Which process is accessing my drive?  How can I see information related to real-time disk i/o?  

:confused: I guess that's two questions.  

I'm familiar with the standard Gnome & KDE graphical applications that show CPU, Memory, and network activity.  I'm familiar also with many of the console applications, like top, ntop, ps, pstree, etc.  Is there an analogous application for drive, or disk i/o?

In the past I've tried to divine the answer by looking at the activity of processes and assuming that the one accessing the drive must be one of the ones with some CPU activity.  Not the highest CPU activity necessarily because an application could be i/o intensive, but CPU intensive, but still, I figured if something is accessing the drive it'll use at least one CPU cycle.  I abandoned that technique as completely worthless, as it seems processes can run that will not show up with any discernible activity in the utilities designed to show process activity.  For example, I'm running reiserfsck right now and it shows 0% CPU usage.  Also, trying to track this down by looking for open files won't work because something could have files open and be sleeping, plus that doesn't show activity, plus disk i/o may or may not be file i/o (journal activity?, directory access?).

I've seen something that does something like what I describe in a MS Windows scenario, filemon by Mark Russinovich (the guy that found the Sony DRM Rootkit in MS Windows).  That's all well and good, except as one might expect, I'm not running Windows (and please, no WINE suggestions, I don't run WINE, don't plan on running WINE).  

I suspect the answer is painfully obvious to somebody that's been a dedicated UNIX/Linux user for a long time, but I haven't been deep into Linux very long and as anybody can appreciate, it is a rich OS with lots of capabilities, some of them inobvious.

---

### Post by gmaniac on 2007-10-21
lsof. don't know any graphical ones.

ex

```
lsof /
```

---

### Post by kvonb on 2007-10-21
I get the same thing every now and then, my hard disk being thrashed with no process showing up, even in *top*!

I've had the entire machine slow to a crawl while in the middle of writing an email, so bad that I had to power off as nothing was responding!

I also use reiserfs if that makes a difference.

I ended up with an unclean filesystem and had to boot from the liveCD and run 

```
sudo reiserfsck --fix-fixable /dev/hda3
```

It hasn't slowed down yet, but I do get the disk thrashing still!

---

### Post by cwaldbieser on 2007-10-21
Something like "atop" might be helpful.  You may need a kernel patch, though.  

The "systat" tools [http://perso.orange.fr/sebastien.godard/]("http://perso.orange.fr/sebastien.godard/") "pidstat" (-d option) can show this, but you need kernel 2.6.20 or later.

---

### Post by RandySavage on 2007-10-21
> **cwaldbieser said:**
> Something like "atop" might be helpful.  You may need a kernel patch, though.  

The "systat" tools [http://perso.orange.fr/sebastien.godard/]("http://perso.orange.fr/sebastien.godard/") "pidstat" (-d option) can show this, but you need kernel 2.6.20 or later.

Thank you for the suggestion.  Niether atop nor systat/pidstat quite did it for me.  atop will show that some disk activity is occuring, but not give you a run-down of which process called for the i/o.  pidstat didn't list -d as an option, put up the help screen when I provided it -d, and doesn't seem to report on disk i/o, only memory and CPU statistics.

Any other ideas?

---

### Post by cwaldbieser on 2007-10-22
> **RandySavage said:**
> Thank you for the suggestion.  Niether atop nor systat/pidstat quite did it for me.  atop will show that some disk activity is occuring, but not give you a run-down of which process called for the i/o.  pidstat didn't list -d as an option, put up the help screen when I provided it -d, and doesn't seem to report on disk i/o, only memory and CPU statistics.

Any other ideas?

The -d option is listed in the website docs.  I am not sure what version is included with Ubuntu.  I am using dapper, and "uname -a" shows my kernel is too early a version.

In atop, if you press "d" and have the correct patch installed, you should see per-process disk I/O like with filemon for Windows.  You might need to run as root, to do this.  I have never actually done this either, as I have been to lazy to patch my kernel.

---

### Post by RandySavage on 2007-11-02
> **cwaldbieser said:**
> The -d option is listed in the website docs.  I am not sure what version is included with Ubuntu.  I am using dapper, and "uname -a" shows my kernel is too early a version.

In atop, if you press "d" and have the correct patch installed, you should see per-process disk I/O like with filemon for Windows.  You might need to run as root, to do this.  I have never actually done this either, as I have been to lazy to patch my kernel.

Thanks again for the help!

Well, sure, it'll show you "the process" accessing the disk, but its always AVIO.  What's calling AVIO?

I'm sure I'm just missing something here.  Surely this sort of activity can't be too convoluted, Linux seems just too powerful to not offer such a fundamental function.

---

