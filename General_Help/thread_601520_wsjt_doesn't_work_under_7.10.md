---
title: "wsjt doesn't work under 7.10"
date: 2007-11-03
forum: General Help
---

### Post by Chasoid on 2007-11-03
I'm trying to use **wsjt** (amateur radio weak-signal program) under 7.10.  It worked perfectly under 7.04.

After I upgraded to 7.10, I tried starting wsjt, but received the following error:
> 
ImportError: No module named numpy.core.multiarray
Traceback (most recent call last):
  File "/usr/share/wsjt/wsjt.py", line 10, in <module>
    import Audio
ImportError: numpy.core.multiarray failed to import

So I installed the "numpy" package via:

> sudo apt-get install numpy.

(Actually, since wsjt is part of the Ubuntu library, I was surprised that this dependency wasn't detected and resolved during the upgrade process.)  :confused:

**My current status:**
I no longer get the above error ... but the program starts and then displays a screen that looks like wsjt for about a second and then exits.  Tthe screens disappear without displaying any error message.  If I start the program from the command line, it tells me that there was a "Segmentation fault".

Any ideas?  Does anyone else have wsjt working successfully under 7.10 (Gutsy)?

Thanks!

---

### Post by w8iss on 2007-11-04
I am having the same problem with the Segmentation fault (core Dump) message.

I have found with some programs that I install that are not part of a certain install,
that I have to go back to an earlier version to have it work properly. Not this time.
Getting the same error with earlier versions too. I was hoping to have this tested
out and running for the next ARRL EME weekend this month.

I upgraded to 7.10 because of problems with WSJT in Feisty Fawn 7.04 with it just
sitting there and not doing anything. I just thought I needed to update the system
which did need to be done anyways because of other things I do.

I am running a IBM Intellistation E PRO 900Mhz Intell processor with 256Megs of
memory.

James W8ISS

---

### Post by ubuntu1sttimer on 2008-02-08
Same problem here. Using 7.10 and WSJT just pops on the screen and then closes. Would like to try it out on Ubuntu but not going to be able with it this way. 

Do not know who got it into the Ubuntu repository or who you would contact to see about doing something about it.   - KV9P

---

### Post by ubuntu1sttimer on 2008-02-10
Did some digging and found in:

[https://bugs.launchpad.net/ubuntu/gutsy/+source/wsjt/+bug/159734](https://bugs.launchpad.net/ubuntu/gutsy/+source/wsjt/+bug/159734)

that this has been reported and that python-numby needs to be installed.

Tried it and the program opens and seems ready to work. Have never used WSJT so can't say for sure that it works, So if someone tries it, post here to let the rest of us know.

-  KV9P

---

### Post by ubuntu1sttimer on 2008-02-11
Appears that I should have waited to post my "good news". Today when I tried WSJT on Ubuntu it didn't work like it did last evening. Now it flashs on and within a second or two it is all closed and gone. 

Don't know what is happening but I should not be surprised as I have not had much luck with installing programs on Ubuntu. Great for surfing the web, playing some games, and using OO, but can't seem to get much beyond that. Thought this might be a turn around but it does not seem so.  -  KV9P

---

### Post by andy9a3jh on 2008-02-18
Same here, Ubuntu Gusty package wsjt (5.9.7.r383-1ubuntu1) not work but Debian package work normal with some warning:

/usr/share/wsjt/wsjt.py:10: RuntimeWarning: Python C API version mismatch for module Audio: This Python has API version 1013, module Audio has version 1012.

Try debian package from [http://packages.debian.org/lenny/wsjt](http://packages.debian.org/lenny/wsjt)

bye

Andy

---

### Post by andy9a3jh on 2008-02-18
Hmmm... aslo last version of Ubuntu packages not work (Hardy universe wsjt (5.9.7.r383-1ubuntu2)). I made complete removal and reinstall Debian package, now again working with same warning.

wsjt (5.9.7.r383-1ubuntu2) show:
WSJT Version 5.9.7 r383 , by K1JT
Revision date: 2007-05-04 23:17:52 +1000 (Fri, 04 May 2007) 
Run date:   Mon Feb 18 19:40:20 2008 UTC
Segmentation fault (core dumped)

bye

Andy

---

