---
title: "Drivers problem. Message popping up &amp; random freezes.{SOLVED}"
date: 2015-01-06
forum: General Help
---

### Post by Reding on 2015-01-06
Hi all,

After turning on my computer without changing anything previously i'm suddenly encountering what seems to be a driver problem.

After turning on my computer a pop up window appears on the screen with this following message

> Could not apply the stored configuration for monitors
Error on line 1 char 1:Document must begin with an element (e.g. <book>)

I can barely use my computer now as my top bar panel disappeared as well and encounter random freezes.

Thanks in advance for your help.

Red

---

### Post by ibjsb4 on 2015-01-07
```
sudo apt-get -f install
```
Does that spit out any errors?

Also check what driver your on.
```
gksudo software-properties-gtk
```

---

### Post by grahammechanical on 2015-01-07
Does it tell you what stored configuration file it is referring to? Now depending upon whether you are using the open source video driver or a proprietary video driver you can either go to system settings of the settings manager of the proprietary video driver and use Detect Displays to see if that changes anything.

---

### Post by Reding on 2015-01-08
It didn't spit out any errors.

I guess i'm using the default drivers. I have no additional drivers available.

Cheers for your much appreciated answers.

---

### Post by ibjsb4 on 2015-01-08
Like graham said, be nice to know what generated that error.  I wonder if you have any crash reports.  Look in /var/crash.

Are you set for automatic updates?  Maybe a kernel upgrade has cause this?  You could try the previous kernel.

A shot in the dark would be to purge (this removes config files) and reinstall xorg.  Any custom configurations will probably be lost.  This could be done in console (Ctrl+Alt+F1).
```
sudo apt-get remove --purge xorg && sudo apt-get install xorg && sudo reboot
```
Could get lucky :)

What kind of video are you running?
```
lspci | grep VGA
```

---

### Post by Reding on 2015-01-10
> Mon Jan  5 17:26:22 CST 2015 crash report /var/crash/_usr_bin_file-roller.1000.crash detected 
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00Mon Jan  5 17:31:14 CST 2015 crash report /var/crash/_usr_bin_file-roller.1000.crash detected 
Mon Jan  5 17:33:44 CST 2015 crash report /var/crash/_usr_bin_file-roller.1000.crash detected 
Mon Jan  5 17:34:51 CST 2015 crash report /var/crash/_usr_bin_file-roller.1000.crash detected 
Mon Jan  5 17:36:19 CST 2015 crash report /var/crash/_usr_bin_file-roller.1000.crash detected 
Mon Jan  5 17:41:09 CST 2015 crash report /var/crash/_usr_bin_file-roller.1000.crash detected 
Mon Jan  5 17:46:25 CST 2015 crash report /var/crash/_usr_bin_file-roller.1000.crash detected 
Mon Jan  5 17:49:04 CST 2015 crash report /var/crash/_usr_bin_file-roller.1000.crash detected

Mon Jan  5 17:26:22 CST 2015 crash report /var/crash/_usr_bin_nautilus.0.crash detected 


nautilus 
new reports but apport disabled 
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00Mon Jan  5 17:31:14 CST 2015 crash report /var/crash/_usr_bin_nautilus.0.crash detected 
nautilus 
new reports but apport disabled 
Mon Jan  5 17:33:44 CST 2015 crash report /var/crash/_usr_bin_nautilus.0.crash detected 
nautilus 
new reports but apport disabled 
Mon Jan  5 17:34:51 CST 2015 crash report /var/crash/_usr_bin_nautilus.0.crash detected 
nautilus 
new reports but apport disabled 
Mon Jan  5 17:36:19 CST 2015 crash report /var/crash/_usr_bin_nautilus.0.crash detected 
nautilus 
new reports but apport disabled 
Mon Jan  5 17:41:09 CST 2015 crash report /var/crash/_usr_bin_nautilus.0.crash detected 
nautilus 
new reports but apport disabled 
Mon Jan  5 17:46:25 CST 2015 crash report /var/crash/_usr_bin_nautilus.0.crash detected 
nautilus 
new reports but apport disabled 
Mon Jan  5 17:49:04 CST 2015 crash report /var/crash/_usr_bin_nautilus.0.crash detected 
nautilus 
new reports but apport disabled

Mon Jan  5 17:26:22 CST 2015 crash report /var/crash/_usr_lib_evolution_evolution-calendar-factory.1000.crash detected 
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00Mon Jan  5 17:31:14 CST 2015 crash report /var/crash/_usr_lib_evolution_evolution-calendar-factory.1000.crash detected 
Mon Jan  5 17:33:44 CST 2015 crash report /var/crash/_usr_lib_evolution_evolution-calendar-factory.1000.crash detected 
Mon Jan  5 17:34:51 CST 2015 crash report /var/crash/_usr_lib_evolution_evolution-calendar-factory.1000.crash detected 
Mon Jan  5 17:36:19 CST 2015 crash report /var/crash/_usr_lib_evolution_evolution-calendar-factory.1000.crash detected 
Mon Jan  5 17:41:09 CST 2015 crash report /var/crash/_usr_lib_evolution_evolution-calendar-factory.1000.crash detected 
Mon Jan  5 17:46:25 CST 2015 crash report /var/crash/_usr_lib_evolution_evolution-calendar-factory.1000.crash detected 
Mon Jan  5 17:49:04 CST 2015 crash report /var/crash/_usr_lib_evolution_evolution-calendar-factory.1000.crash detected

on Jan  5 17:26:22 CST 2015 crash report /var/crash/_usr_lib_tracker_tracker-miner-fs.1000.crash detected 
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00Mon Jan  5 17:31:14 CST 2015 crash report /var/crash/_usr_lib_tracker_tracker-miner-fs.1000.crash detected 
Mon Jan  5 17:33:44 CST 2015 crash report /var/crash/_usr_lib_tracker_tracker-miner-fs.1000.crash detected 
Mon Jan  5 17:34:51 CST 2015 crash report /var/crash/_usr_lib_tracker_tracker-miner-fs.1000.crash detected 
Mon Jan  5 17:36:19 CST 2015 crash report /var/crash/_usr_lib_tracker_tracker-miner-fs.1000.crash detected 
Mon Jan  5 17:41:09 CST 2015 crash report /var/crash/_usr_lib_tracker_tracker-miner-fs.1000.crash detected 
Mon Jan  5 17:46:25 CST 2015 crash report /var/crash/_usr_lib_tracker_tracker-miner-fs.1000.crash detected 
Mon Jan  5 17:49:04 CST 2015 crash report /var/crash/_usr_lib_tracker_tracker-miner-fs.1000.crash detected

Here we go.

And my screenshot of some malware !?

Edit: My video

[QUOTE][/Q00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)UOTE]

---

### Post by Bashing-om on 2015-01-10
Reding; Hello;

ibjsb4 has asked me to join this thread, see what we can figure out. I do enjoy a challenge, and this one may well be !

So we have:
> 
Could not apply the stored configuration for monitors
 on a rock solid Intel graphics chip set.

And also we have crashes with file-roller, that I recon is also affecting nautilus (apt-cache show file-roller).

I just do not see how the two are related. Are the crash reports running us out of disk space ?
1) Let's look at disk space usage:
```

df -h
df -i

```

Might then consider deleting those old crash reports, see no value in keeping them on the system.

Let's get rid of the offending application - temporarily, we can (RE-)install when the system is stable.
Purge file-roller:
```

sudo apt-get purge file-roller

```

See now what the state of nautilus is:
```

sudo dpkg-reconfigure nautilus

```
By the way what desktop environment are we working with here ? Xubuntu that 'nautilus' has been added to ?

-----------------------
Let's get the package manager in a happy state, reboot and then take a look at what the system log files relate to us. Maybe then get an idea IF a config file is messed up and where ??

What I would do
[INDENT][INDENT][INDENT]if I were in this situation
[/INDENT][/INDENT][/INDENT]

---

### Post by Reding on 2015-01-10
>  df -h
Filesystem                          Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--gnome--vg-root   43G  8.2G   32G  21% /
none                                4.0K     0  4.0K   0% /sys/fs/cgroup
udev                                7.8G  4.0K  7.8G   1% /dev
tmpfs                               1.6G  1.1M  1.6G   1% /run
none                                5.0M     0  5.0M   0% /run/lock
none                                7.8G   92K  7.8G   1% /run/shm
none                                100M   28K  100M   1% /run/user
/dev/sdb2                           237M   80M  145M  36% /boot
/dev/sdb1                           511M  3.4M  508M   1% /boot/efi

I purged file roller but it didn't change anything. Disk usage isn't the problem for sure, i have plenty of space left.

I'm on Ubuntu Gnome 14.04 LTS.

The weird thing is that now i can use my system properly but it crashes when i try to open applications like Tweak Tool or Guake Terminal.

Should i try to install the latest Intel drivers ? I'm not a big fan of these drivers as it created problems in the past as well..

Thanks a lot for your efforts in helping me to solve this problem

Cheers

Red

---

### Post by Bashing-om on 2015-01-10
Reding; Well, now ;

Not all bad ..

The system crashing when aps are opened is a concern.
A quick check on the health of the package management system:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg -C

```

My advise on Intel drivers: what is supplied with the kernel is great . Intel supports and provides for us very well. Leave well enough alone.

If and when the package manager is in a happy state, we go looking into the logs and see what the system reports .
---------------------
> 
/dev/mapper/ubuntu--gnome--vg-root 43G 8.2G 32G 21% /


We doing (L)ogical (V)olume (M)anagement here or what ? encryption ?
-------------------------------



[INDENT][INDENT]nice to know what we are working with
[INDENT][INDENT][INDENT]finding out where we are headed too[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Reding on 2015-01-11
Yes, LVM.

Ok, it's a bit better now already after doing what you told me to do. Still can't launch Tweak Tool or Guake without crashing though.

All the packages seem fine and i can see my Volume and Brightness widgets after hitting the Fn key again.

---

### Post by Bashing-om on 2015-01-11
Reding; ibjsb4;

I have not messed with Gnome Desk Top, so pardon my ignorance.

Continued thought process on my part:
show us the outputs - Between Code Tags - of those terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg -C

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Let's isolate this to a config problem within your /home directory. Does the guest account or an alternate user account behave ?

[INDENT][INDENT]fault isolation
[INDENT][INDENT][INDENT]poke at it 'til you know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Reding on 2015-01-11
Nevermind !

The problem is gone, by itself. Weird eh, but everything works fine now.

---

### Post by Bashing-om on 2015-01-12
Reding; Ho Kay ! Great.

We mark this one up to the package manager doing it's magic.

As this matter is now concluded;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

