---
title: "ubuntu having huge slowdowns"
date: 2007-05-30
forum: General Help
---

### Post by pspawn on 2007-05-30
I am using Ubuntu 7.04 on a Pentium 4 (3Ghz), 512MB RAM.
I do not have Desktop Effects on.

More than once a day, the whole system starts to slowdown, the mouse gets slow and sometimes not moving for a time.

It happens when 5 or 6 programs are open at the same time. The last time it was Swiftfox, aMsn, Bluefish Editor, the Terminal, and Apache running on the background. Then it started to lag like hell, and it took me almost 2 minutes to switch to the Terminal and kill swiftfox to free some ram.

It 512MB not enough RAM?? I'm a former windows user, and 512mb was enough on the other OS, even with 10 or 12 programs at the same time.

Is there any solution?

PS: Sorry if my engilsh is not perfect.

---

### Post by andrew.46 on 2007-05-30
Hi,

 I read your post with interest:

> **pspawn said:**
> 512MB not enough RAM?? I'm a former windows user, and 512mb was enough on the other OS, even with 10 or 12 programs at the same time..

 Not sure what your problem is but I doubt that it is a RAM issue. You can easily see the actual RAM + Swap file usage at any time by opening a Terminal and typing:

```
free -m -t -o
```

 Perhaps have a look at the System Monitor which should show (on Dapper at least!) running processes and how much memory / cpu percent use? There is a neat Terminal way to do all this but if I ever knew I have forgotten it :-)

              Andrew

---

### Post by pspawn on 2007-05-31
I'm guessing this is a RAM problem because i started to check the amount of free ram since the first time the problem happened.

Right after i kill something and the system starts to recover its speed, i see it's using more than 450mb of ram. And maybe, before killing some process, it was using it all.

RAM usage is always above 300mb, and i have stopped a lot of the default process/services that i don't use.

CPU usage varies beetween 0 and 10%, most of the time near 0. I have the cpu usage monitor on my gnome panel.

---

### Post by rillip on 2007-05-31
To see what's using the most, try using the command 

top

It may be one or more of those programs is trying to use too much RAM and is causing massive paging to your swap file.

Also, you stat you're running appache, what services?  It could be your receiving an unanticipated ammount of traffic that's driving process load up.

---

### Post by pspawn on 2007-05-31
apache was on at the moment, but it happens even with apache off.

I think the biggest "ram monster" is firefox, that is sometimes using near 100mb of ram.
I just think linux can't handle this amount of ram usage, when it's very near of the limit, or over the limit.

---

### Post by cookies on 2007-05-31
Linux handles RAM fine. I have 493MBs of it on my Desktop, and at MOST I use half of it, usually a 1/3 of it, even with Firefox.

So, you must have a nasty Firefox extension.

Try this

Applications > Accessories > Terminal 

And type 

```
firefox --safemode
```

And hit Continue In Safe Mode

This will disable all but core Firefox, and if it uses less RAM then, you have a bad extension. Open Firefox in normal mode again, disable all extensions, and then enable them one by one to see which it is. 


If that doesn't help, try checking for Zombie Processes in System Monitor, and right click them, and hit Kill. 

*You may need to do  Applications > Accessories > Terminal  and type:
```
sudo gnome-system-monitor
``` to kill the processes if it says something like "Denied".

Or, your SWAP partition is too small.

---

### Post by pspawn on 2007-06-01
What is a good Swap partition size?
Mine is 200mb, and it is even bigger than the ubuntu installer recommended.

---

### Post by DrMega on 2007-06-01
Linux is generally less memory hungry than Windows. I have two machines, one is a media centre with a decent CPU, huge hard disk and 1GB of RAM, running various multimedia processes over the course of a saturday evening, the system monitor tells me I'm using around 200MB in all.

On my other machine, which experiences go slows just as you describe, RAM isn't an issue but I've only given an ancient 8GB drive to Linux, which has less than half a gig of available space left.

Have you checked the disk space available to Linux?

---

### Post by pspawn on 2007-06-01
My main linux partition have a total size of 50GB, where 26GB is free.

---

### Post by rich.bradshaw on 2007-06-01
I run with 256MB and it's fine - as mentioned, what firefox extensions have you got?

---

### Post by pspawn on 2007-06-01
I made some tests. Running firefox in normal mode, it uses 50mb of ram, with no tabs open. In safe mode it's using 45mb.
So i think it's not really the extensions.

The slowdown happened again today. I had firefox, amsn, terminal, DBDesigner and Bluefish editor open. It's not really a lot of programs.

I'm getting a bit disapointed with ubuntu. People suggest me a lot o things, like compiling the kernel on my own, or changing the windows manager. I really don't think this is the answer.

I'm really thinking about formatting everything, and install it all from zero. I'll lose everything, but I really don't want to go back to an illegal copy of windows.

---

### Post by Lucifiel on 2007-06-01
Maybe you can try installing smartmontools and seeing if there are hard disk errors. Run this code in Terminal to get an output of your hard disk status. 
> sudo smartctl -d ata -a /dev/hdc 

Replace "hdc" with your hard disk label like sda, hda, etc. 

Or try running memtest from the Livecd.

---

### Post by pspawn on 2007-06-01
I think I found the cause of all my problems.

I decided to check the amount of swap being used (expecting it to be 0) and then i found: swap 0bytes used out of 0 bytes.

It was a surprise. 0 bytes of swap available? Where are my 200mb?

Then i edited /etc/fstab. Somehow, when I updated to Ubuntu Feisty, it screwed fstab. I am sure the swap was working before the update.

Now I edited it and i have again 200mb of swap, and I hope this solves my problems.

---

