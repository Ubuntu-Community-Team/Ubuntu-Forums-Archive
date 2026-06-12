---
title: "Installation package failure"
date: 2016-10-18
forum: General Help
---

### Post by george110 on 2016-10-18
There was a problem with a failed package update installation. I waited some days & tried to update again & the same pronouncement appeared although the number of updates had increased. I tried their suggestions to fix the problem ( standard suggestions ) & made no progress.

Has anyone got any ideas that would enable downloading of continuing updates ?  Can't continue with confidence until this problem is fixed.

George

---

### Post by howefield on 2016-10-18
Can't help with confidence on the basis of the information supplied.

From a terminal, what do you get with..
```
cat /etc/*-release
```
```
sudo apt update
```
```
sudo apt upgrade
```

---

### Post by george110 on 2016-10-23
Following up immediately from my last post to you ( minutes ago ) I was wondering whether you may agree with the idea of a complete reinstallation of Ubuntu ?

The files are backed up.

Were you to be agreeable to that idea then could you suggest how I ought go about a re-installationl. Does one just download the latest version & it takes care of itself ie repairs the faults in the existing OS ?

If not so then perhaps you could suggest how to go about such an activity.

You may have other courses of action which could be tidier.

The difficulty, of course, is that I can no longer update. Also, I lost sound some time ago.

---

### Post by CantankRus on 2016-10-23
If you provide the information asked for by **howefield** someone may have an easy solution.

Reinstalling the OS will overwrite everything if that's the way you want to go.
Sometimes is easier when you can't figure out what you did to mess it up.
I just copy my home folder to another disk as the backup.
This enables you to copy back some of the hidden application configs if needed.

Reinstall with 16.04LTS as this is supported for 5 years whereas the latest 16.10 is only 9 months.

---

### Post by howefield on 2016-10-23
> **george110 said:**
> Following up immediately from my last post to you ( minutes ago ) I was wondering whether you may agree with the idea of a complete reinstallation of Ubuntu ?

Well, your machine, your choice. It should take much less than an hour to do a reinstall, update and configure, even quadrupling for inexperience means 4 hours max :) 

> The files are backed up.

Very prudent :)

> Were you to be agreeable to that idea then could you suggest how I ought go about a re-installationl. Does one just download the latest version & it takes care of itself ie repairs the faults in the existing OS ?

How did you do the initial installation, it is very easy although it always is when you know how, all you need to do is download the appropriate image and create a Live media with a DVD or USB stick. Then install over the top of your existing installation providing you mark it for formatting, (not formatting means your existing /home folder will survive). As CantankRus said this will give you a pristine install and wipe the previous install out.

Were you to go down this road there are other considerations that might make life easier in the future, like having a separate /home folder or better a Data partition for your documents, ect. 

> The difficulty, of course, is that I can no longer update. Also, I lost sound some time ago.

Without the information asked for, we can go no further, we have to understand why your system is failing to update in order to suggest a fix, which is highly likely to be very simple and easy to remedy.

The sound is a separate issue and would require a separate thread.

---

### Post by RobGoss on 2016-10-23
Are you getting some sort of error message if so please post the output of that message here using the **code tag **so we can take a look I'm sure someone will pinpoint the problem

---

### Post by george110 on 2016-10-23
The message is " the package system is broken " & " Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f "

Well I'm not using 3rd party repositories & when I put in the command I am requested for my password which when i put it in is rejected. So, I can't supply the " coda " info which would begin to allow someone to begin analysing the problem.

Thanks for replying.
I can't supply howefield with info because my password is rejected at the code requests.That's the first problem

Thank you howefield.
Well I've decided to reinstall.
Can you see a problem here ? The current Ubuntu is on a partitioned drive ( windows 10 on one partition & Ubuntu on the other.
Let's say I put a raw image of Ubuntu 16.04 onto a USB which is in progress as I write ( downloading from _U_buntu now.
Now how do I go about formatting & downloading Ubuntu onto the partition that already contains Ubuntu ?

---

### Post by RobGoss on 2016-10-23
If you're using** Windows **you can simply delete that **Ubuntu partition** and use that **unallocated space** for the new installation, did you choose install Ubuntu alongside Windows if so you should be able to use that same method and this time choose the unallocated space for your new installation of Ubuntu

**NOTE**: Make sure you have a recovery disk for Windows just in case something goes wrong it's better to be safe then sorry

---

### Post by lisati on 2016-10-23
> **george110 said:**
> Thanks for replying.
I can't supply howefield with info because my password is rejected at the code requests.That's the first problem
A password can be rejected for a number of reasons. Does the user you're logged into your machine with have "sudo" (admin) rights on your machine?  

(Side note: the request for "code tags" is about formatting your forum posts correctly, and can be used for any terminal output, not just code listings.)

---

### Post by george110 on 2016-10-24
Thank you RobGoss.
The current installation of Ubuntu is on a separate partition. It occupies space identified as dev/ dev4 & dev/ dev5 each about 93 Giga bytes - whatever that means.
However there exists the option according to howefield of just running the raw ubuntu installation, now on a disc, & minimising hassles.
Question RobGoss. Would you expect that by just running the installation from the USB that the current problems of the existing Ubuntu OS will auomatically be rectified ? Ie downloads functioning properly again & sound returns.

---

### Post by george110 on 2016-10-24
seems not.

---

### Post by howefield on 2016-10-24
> **george110 said:**
> seems not.

What exactly seems not ?

Out of interest can you supply the output of the following terminal command..

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by RobGoss on 2016-10-24
> **george110 said:**
> Thank you RobGoss.
The current installation of Ubuntu is on a separate partition. It occupies space identified as dev/ dev4 & dev/ dev5 each about 93 Giga bytes - whatever that means.
However there exists the option according to howefield of just running the raw ubuntu installation, now on a disc, & minimising hassles.
Question RobGoss. Would you expect that by just running the installation from the USB that the current problems of the existing Ubuntu OS will auomatically be rectified ? Ie downloads functioning properly again & sound returns.

In some cases reinstalling the OS will fix some issues depending on the hardware. The forums are in place to help us with our issues and to help us trouble shoot at the same time, we also learn what we need to know to maintain our systems which is a good thing

In most cases running a simple command from the command line will detect problems and allow you to correct them

I recommend reinstalling the OS on fresh installations and sometimes stand alone machines in some cases if there's only one OS on it and again, depending on the issue. Dual booting is altogether different and has to be handled differently

---

### Post by george110 on 2016-11-02
Howefield, can you work with this ? The following packages have unmet dependencies:
 linux-generic : Depends: linux-headers-generic (= 4.4.0.42.44) but 4.4.0.38.40 is to be installed
 mailagent : Depends: libperl4-corelibs-perl but it is not going to be installed
             Depends: exim4 but it is not going to be installed or
                      postfix but it is not going to be installed or
                      sendmail but it is not going to be installed or
                      mail-transport-agent
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
george@george-pc:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by jerome1232 on 2016-11-02
You must use sudo to escalate your privileges to root.

```
sudo apt-get -f install
```

You will be asked for your users password, type it in, nothing will be shown on screen while you are typing, this is normal for terminals, just type it and hit enter.

---

### Post by ian-weisser on 2016-11-02
> **george110 said:**
> linux-generic : Depends: linux-headers-generic (= 4.4.0.42.44) but 4.4.0.38.40 is to be installed
 mailagent : Depends: libperl4-corelibs-perl but it is not going to be installed
             Depends: exim4 but it is not going to be installed or
                      postfix but it is not going to be installed or
                      sendmail but it is not going to be installed or
                      mail-transport-agent

This error means that you have introduced a version conflict.
Reinstalling seems unlikely to help - you are likely to recreate the problem on a newly-installed system.
Your system will not install nor receive security updates until the conflict is resolved.

Version conflicts like these sometimes occur when you install non-Ubuntu software from PPA or third-party sources.
What did you recently install...before you began encountering problems?

---

### Post by howefield on 2016-11-03
> **george110 said:**
> Howefield, can you work with this ? The following packages have unmet dependencies:

Yes, **I** can, not so sure I could assist **you** though. My attempts to elicit further information in this thread have failed miserably :)

ian-weisser is putting you on the correct path, try and follow what he asks.

---

