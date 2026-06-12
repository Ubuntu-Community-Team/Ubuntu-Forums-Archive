---
title: "Can not boot up ubuntu.  Suddenly has stopped working please help me!!!"
date: 2007-02-09
forum: General Help
---

### Post by jfrancis on 2007-02-09
Dear all,

Please help me.  I have been running Ubuntu for a few months now and this morning when I switched on it would not boot up.  I can not even get anywhere by choosing the 'recovery' option at boot.  

I think it is a problem with the root file system ???


Here is what happens:

While the system is loading, and you get the color bar that shows the progress moving from left to right as the system loads, well it will stop around 50% and the system starts a sort of hard drive checking program which every time never reaches 100%.  It gets so far and then it outputs the following:

> 
/DEV/sda2: UNEXPECTED INCONSISTENCY ; RUN fsck MANUALLY

fsck died with exit status 4

* An automatic file system check (fsck) of the root filesystem failed.

A manual fsck must be performed in maintenance mode with the root filesystem mounted in read-only mode.

The root filesystem is currently mounted in read-only mode.

A maintenance shell will now be started.

Give root password for maintenance:


So I enter my root password and I get this:

> 
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: dircolors: command not found


Then it just sits there.  I am clueless about this stuff.  I had no warnings when I last used the computer of any problems.  I always shutdown the computer in ubuntu, never pull the power.  So why have I got this problem?  The system is a dual boot with windows which is what I am using now, so the harddrive is obviously ok (i assume as I am using it).


If anyone can help me I would so appreciate it.  I love using ubuntu and this has really thrown me.

Kind Regards,

J

---

### Post by logos34 on 2007-02-09
Try fsck from a terminal on the ubuntu livecd:
> sudo fsck /dev/sda2

---

### Post by jfrancis on 2007-02-09
Logos34 - THANK YOU!!! 

That worked a treat.  At one point while it was sorting itself out it told me that some value was showing 18 but should be zero, then asked me if I wanted to clear it.  I had no idea what this meant but hit (y) and all is working now.

Much appreciated :)

---

