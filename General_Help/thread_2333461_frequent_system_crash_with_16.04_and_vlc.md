---
title: "frequent system crash with 16.04 and vlc"
date: 2016-08-10
forum: General Help
---

### Post by anewbie on 2016-08-10
I've upgraded from 14.04 to 16.04 and I am having system crashes mostly due to something with vlc. The machine is a 2500K using the CPU's GPU. If VLC is running full scream that can almost always trigger a system crash.

I'm not sure if the issue is with the new kernel or intel driver. To be honest VLC itself has been a major headache since the upgrade. I'm using with with hdhomerun prime - but it also has problems playing some videos (something to do with the auto decoding; I can specify the decoder to use for the files and that seems to work but then it has problems using that decoder with the hdhomerun prime - this is a side topic - the fact that it can trigger system crashes is more concerning. 

I really don't know what has changed with kernel 4.4 vs 3.18 (ubuntu 14.04) or if the intel video driver changed. I know there were major changes to X but do not know the specific. I do not see anything in syslog around the crash.
-
This was a fresh install not an upgrade from 14.04.3 to 16.04.1

---

### Post by rezam on 2016-08-10
I ran into the same issue, I wanted to give 16.0.1 a try..and ended up with 10 of thousands of crash reports regarding kernel and xorg ... ([https://ubuntuforums.org/showthread.php?t=2333459](https://ubuntuforums.org/showthread.php?t=2333459)).

I now returned back through a re-install with 14.0.4.1 ...and it seems as everything is working ... you shd post / check /var/crash and post the reports here...

---

### Post by anewbie on 2016-08-10
There is nothing useful in /var/crash. My problem is system (kernel?) crash (i.e, system hangs completely) not application crash. I might be mistaken but only applications show up in /var/crash.

btw the thread you link'ed is talking about 14.04.* (all of which ran fine for myself). My problem is with 16.04.1

---

### Post by anewbie on 2016-08-11
I should have noted that most of the crashes occur in full screen-mode (crash might not be the right term because I'm not referring to application crash but system lock up). I know the system is unresponsive remotely (at least the kernel no longer respond to tcp requests). 
-
Perhaps it is the intel driver ? mpv has no issue playing videos and (so far) does not have this issue of killing the system - however I have to use vlc for the homerun prime (mpv as far as I can tell does not support udp plugin but perhaps it would work with just the http url ?

---

### Post by mc4man on 2016-08-11
Seems to be a vlc issue as mpv is fine. Vlc's auto-detection for hw acceleration  is terrible. Do you really need it? (hw accel)
Generally if vaapi was enabled & couldn't be used for this file or that,  then vlc would just not use. (or shouldn't ..

> (mpv as far as I can tell does not support udp plugin but perhaps it would work with just the http url ? 
try & see

---

### Post by anewbie on 2016-08-12
Well VLC is certainly triggering the kernel level crash; If I select the accel manually i have to constantly switch depending on what I am playing; and if i play the video without hw acceleration (on a 2500K) it stutters.

---

### Post by anewbie on 2017-02-24
As an update my crash rate has dropped since the removal of the usb dac (fifo); but it still happens once every couple of other days. Would be nice if there was a way to get a kernel dump of what is happening. I never had this issue with 14.04 (I know vlc crashes are video related but i stopped using it). One thing i noticed is that a couple of times the disk light was on when the system crashed (crash means it stops being responsive to input; all updates on the window freezes and pings on the local net are not responded).

---

### Post by anewbie on 2018-02-15
Just an update to this old thread. The issue was with the video driver for sandybridge i5. It was fixed a while ago and haven't had a crash in 6+ months since the fix.

---

