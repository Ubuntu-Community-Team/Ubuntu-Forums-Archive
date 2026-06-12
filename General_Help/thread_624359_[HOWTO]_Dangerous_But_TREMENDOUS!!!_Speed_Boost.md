---
title: "[HOWTO] Dangerous But TREMENDOUS!!! Speed Boost"
date: 2007-11-26
forum: General Help
---

### Post by 1337455 10534 on 2007-11-26
I would not suggest this for people who do not use Fusion/Emerald because you probably don't need it. But for people who have felt and stung from a speed loss after getting Compiz Fusion, LISTEN UP!
Go to GNOME system monitor, right-click on x-session-manager and Change its Priority to -20. Do this for Emerald, Compiz-Real, gnome-panel, and Firefox. Increase priority number for unused or rarely used applications, like trackerd.
Then, close all open applications, and goto System-Pref-Session and save your current session.
Then Restart, or just restart X (Ctl+Alt+Backspace).

Everything is a LOT faster for me, and all of the Fusion plugins have stopped glitching! :)!

---

### Post by 1337455 10534 on 2007-11-27
After reboot, my settings are not remembered...
Is there a script someone can write to tell these process to tune it up (or down) during boot?

---

### Post by rich.bradshaw on 2007-11-27
Try using this to make a command that sets the prioties... [http://www.computerhope.com/unix/upriocnt.htm](http://www.computerhope.com/unix/upriocnt.htm)

---

### Post by 1337455 10534 on 2007-11-28
:)

---

### Post by A-dogg on 2007-12-03
i use emerald, but... why is it dangerous?

---

### Post by jflaker on 2007-12-03
> **A-dogg said:**
> i use emerald, but... why is it dangerous?

I work with the as/400 (IBM iSeries) which has many similarities to linux.  The danger in pushing a running task to a higher priority is the possibility of losing control of your system.  

Setting a priority of one running application over an interactive application can cause an unresponsive console.  The system will seem to freeze when in fact, the background or or another foreground application has more processor time leaving you with crumbs.

---

### Post by A-dogg on 2007-12-03
ahhh... as things seem to be running pretty smoothly right now, I guess I'll just leave things are they are.

---

### Post by 1337455 10534 on 2007-12-04
Yes, while doing this I wouldn't run 5 different FF windows, GIMP, and Google Earth. In any situation, that might Uberlag my computer, but it would be even sillier still with whacky process priorities.

---

### Post by rune0077 on 2007-12-04
So, if I have so much processing power that Ubuntu practically never ever uses more than 50% of it in total (and usually *a lot* less than that), would this be perfectly safe?

---

### Post by spupy on 2007-12-04
You can also change the priority of a process with this command:
```
renice X Y
```
where X is the new priority and Y is the process id (pid). 
I personally won't use this, although it applies to all processes, not just compiz related. I am just studying about this things - it is not matter of processing power, but of processing time. A process with  higher priority will have a bigger chance to receive processor time from the kernel, meaning it would execute more often. I'm not pretty familiar with the Linux daemons (since they are the once that run at the highest priorities) so i can't tell if this practice will mess anything.

---

### Post by 1337455 10534 on 2007-12-05
Spupy would be the better one to answer that question... But I do this on a 2.5 year-old HP (P4) with a GB of RAM, and I've been fine.

---

### Post by rune0077 on 2007-12-05
Oookay. I am still not entirely reassured. I'll just hang around this thread and see how other people gets away with it (or don't get away with it, as the case may be) before trying this myself.

---

### Post by spupy on 2007-12-05
> **1337455 10534 said:**
> Spupy would be the better one to answer that question... But I do this on a 2.5 year-old HP (P4) with a GB of RAM, and I've been fine.

Well, don't really take my words for true. I am still _learning_:). But i am interested to see the opinions of other who have more knowledge than me.

---

### Post by sloggerkhan on 2007-12-05
I don't think it's that bad. I regularly reduce the priority of intensive stuff that runs in the background, like thoggen, and have no problems, in fact, if anything, stuff's been smoother. Of course I don't go extreme. I usually use 10 for background stuff that defaults to 0.

---

### Post by 1337455 10534 on 2007-12-05
> 
I don't think it's that bad. I regularly reduce the priority of intensive stuff that runs in the background, like thoggen, and have no problems, in fact, if anything, stuff's been smoother. Of course I don't go extreme. I usually use 10 for background stuff that defaults to 0.

In my opinion, smartest thing we've heard yet! :)

rune0077;
You'll be fine, fiddling around *rarely* breaks your system now days... I remember the "install-Automatix-and-bam-your-Feisty-is-dead" era...

---

### Post by steveneddy on 2007-12-05
> **1337455 10534 said:**
> ... I remember the "install-Automatix-and-bam-your-Feisty-is-dead" era...

LOL - yeah

:popcorn:

---

