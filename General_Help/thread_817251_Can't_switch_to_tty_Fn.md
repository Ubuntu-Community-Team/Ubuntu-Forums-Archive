---
title: "Can't switch to tty Fn"
date: 2008-06-03
forum: General Help
---

### Post by saltydog on 2008-06-03
In my ubuntu Hardy, if I switch to any tty other than 7 (Ctrl-Fn), I see just a blank screen and cannot type anything.
This is quite a problem, as I need to switch forth and back to other tty's when debugging.
I use nvidia-new drivers, and these are my defotions in menu.lst:

```
# defoptions=vga=791 quiet splash

```

I have tried removing the vga=791, with no luck.

---

### Post by HalPomeranz on 2008-06-03
Odd problem.  Are your getty processes running?

```

$ **ps -ef | grep getty**
root      4515     1  0 14:33 tty4     00:00:00 /sbin/getty 38400 tty4
root      4516     1  0 14:33 tty5     00:00:00 /sbin/getty 38400 tty5
root      4518     1  0 14:33 tty2     00:00:00 /sbin/getty 38400 tty2
root      4520     1  0 14:33 tty3     00:00:00 /sbin/getty 38400 tty3
root      4522     1  0 14:33 tty6     00:00:00 /sbin/getty 38400 tty6
root      5987     1  0 14:33 tty1     00:00:00 /sbin/getty 38400 tty1
hal      16808 14112  0 17:13 pts/3    00:00:00 grep getty

```

These are supposed to be started by the /etc/event.d/tty* scripts run by the init process at boot time.

---

### Post by saltydog on 2008-06-04
Yes ,they are running.

I was used to switch from a tty to another, until I installed compiz and enabled desktop effects...

---

### Post by HalPomeranz on 2008-06-04
> **saltydog said:**
> I was used to switch from a tty to another, until I installed compiz and enabled desktop effects...

So I suppose the next thing to try is to revert to something like metacity and see if you still have the problem.  But you knew that already.  :-)

---

### Post by bingoUV on 2008-06-04
what happens when you run this?

```

sudo chvt 1

```

---

### Post by saltydog on 2008-06-04
> **bingoUV said:**
> what happens when you run this?

```

sudo chvt 1

```

The same as pressing Ctlr-F1... I get a blank screen with a blinking cursor. Nothing else.

---

### Post by bingoUV on 2008-06-04
Have you tried rebooting? In this incarnation something might have happened to the gettys, but maybe they'll be fine after a reboot?

---

### Post by saltydog on 2008-06-04
> **bingoUV said:**
> Have you tried rebooting? In this incarnation something might have happened to the gettys, but maybe they'll be fine after a reboot?

Rebooting?? It's a month that I have this problem, and I switch on the PC at least twice a day...

---

### Post by tealio on 2008-12-27
i was wondering if you ever solved this problem... i have the same issue.  the ttys have never worked since install, and it's finally bothering me... i typicalaly use several ttys instead of cluttering up my desktop with a bunch of terminal windows.  but i haven't been able to since i installed ubuntu... my getty processes are running, but don't seem to be doing anything.

i tried killing the getty processes since they respawn, but no luck.  the processes respawned, but again, no tty! ... HELP!

---

### Post by tmastran on 2009-01-13
I've posted this very same problem before. Can't "see" ttys, but if I type blind, they are there. This started after upgrading to 8.10. It seems like they work after initial booting from either the GDM login, or in Gnome or KDE. But If I leave a while, and come back, they no longer work.

This makes it very hard to manage the machine. change run levels, etc.

---

### Post by tealio on 2009-01-23
no i see no one has come up with a solution.  

> Can't "see" ttys, but if I type blind, they are there.

i tried that, but my ttys are completely unresponsive...

---

### Post by mattydee on 2009-02-03
Same problem here. Using 8.10 and kdm as login manager.

---

### Post by NateMan on 2009-02-22
I am having this same problem as well with ubuntu 8.10. It formerly worked, even with desktop effects, however I recently was using it with dual screen with an hdtv till I had overscan problems. In order to fix this I had to drop to another tty and quit gnome. This however didn't work. I'm using Nvidia graphics driver 177 with a geforce 8600m gt. Its a rather important feature, and I have used it many times in the past. All of my getty processes are also running just fine. It also seems that my laptop screen doesn't even come on, which is strange, since it works showing other low resolutions. Any help or troubleshooting advice would be helpful.

---

### Post by mattydee on 2009-05-01
If you want to do "crazy" things like switch to VTs and restart the X server using ctrl-alt-backspace (in Jaunty), then it seems you need to switch to a proper linux distro...

+ oh ya, if you want a stable OS switch to Vista or again a proper linux distro... 

Ubuntu (but especially kubuntu) freezes more often than windows xp and vista these days. When it does and you can't switch to a VT or restart the X server... combine that with KDE4 being a piece of ...

---

### Post by poisoneggs on 2009-09-02
> **tmastran said:**
> I've posted this very same problem before. Can't "see" ttys, but if I type blind, they are there. This started after upgrading to 8.10. It seems like they work after initial booting from either the GDM login, or in Gnome or KDE. But If I leave a while, and come back, they no longer work.

This makes it very hard to manage the machine. change run levels, etc.

Same problem, I can type and navigate around, just can't see anything.

Help!

---

### Post by aneganov on 2010-07-13
Same here, 9.10 Ubuntu.
NVIDIA drivers
NO visual effects are used.
One more monitor plugged.

Any solutions? TTY1 is empty!

---

### Post by mzlichen on 2010-08-02
It seems I had a same problem.
 
When I changed to shell mode there is only a cursor and can't type anything.
 
Some one ask me to check in the log. The log was saying the pulseAudio was having a problem.
 
Then I fix the pulseAudio. With luck!
 
Hope it helps.

---

### Post by benbloom on 2010-08-25
I too have this problem.

---

### Post by hero1900 on 2012-06-12
i have same problem on 12.04

---

### Post by overdrank on 2012-06-12
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

