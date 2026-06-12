---
title: "Excessive hard drive activity"
date: 2007-11-02
forum: General Help
---

### Post by adamklempner on 2007-11-02
Ever since I installed and set up Kubuntu 7.10 on my desktop I have been getting a lot of hard drive activity even when the computer is idle.  Most of the time I will get the hard drive noise every 3 seconds or so.  I uninstalled strigi (the desktop search thing) based on what others have said on the forums.  That did not help.  

I can check "top" but that doesn't reveal anything obvious.  My processor usage doesn't go much above 2% ever at idle and nothing seems to be coinciding with the hard drive accessing.  Xorg is the only thing that seems to be going up and down noticeably.

What could be causing all of this activity in Gutsy that wasn't there before?  And how do I figure out what is actually hitting the hard drive all of the time?

---

### Post by kolinab on 2007-11-03
Check these threads. I made some of the changes suggested therein and think I've done good things for my HD!

[http://ubuntudemon.wordpress.com/2007/10/27/laptop-hardrive-killer-bug-is-worse-than-i-thought/](http://ubuntudemon.wordpress.com/2007/10/27/laptop-hardrive-killer-bug-is-worse-than-i-thought/)

[http://ubuntuforums.org/showthread.php?t=432472](http://ubuntuforums.org/showthread.php?t=432472)

[http://www.linuxquestions.org/questions/ubuntu-63/hdparm-apm-hard-drive-clicking-sound-588770/](http://www.linuxquestions.org/questions/ubuntu-63/hdparm-apm-hard-drive-clicking-sound-588770/)

That's enough to get you started anyway . . . !

K

---

### Post by BigSilly on 2007-11-03
The OP is talking about a desktop PC. Isn't this a problem/discussion around laptop usage?

I used to get loads of HDD noise when I used XP. Even after fresh installs it would make an amazing amount of racket even when idle. I have to say that since switching completely to Linux I don't get anything like that any more. Even the missus has noted how quiet the drive is! 

I'd be curious to know if this is an issue that's supposed to affect desktop users too.

---

### Post by kolinab on 2007-11-03
I'm sorry. My bad. The OP is talking about a desktop.

I wonder if any of the discussions I linked to would be relevant anyway? I really haven't a clue. That's what I get for opening my mouth before opening my brain. . . 

K

---

### Post by adamklempner on 2007-11-04
Thanks for the replies guys.  I think I have at least partly solved my issue.  It turns out that superkaramba had crashed with KDE-trash theme running, and that seemed to be hitting the hard  drive even though it wasn't visible.  Closing that made a pretty big difference.

However, a question still remains as to why Kubuntu hits the hard drive from time to time, maybe once a minute or so, now at idle.  I created a new user account, logged out of this one, and went in there to see if there was any difference and there was not.  

Does anyone know of anyway to monitor what exactly is accessing the hard drive?

Back in my XP days (long ago) this computer at idle would truly be at idle.  After a while of inactivity windows would power down the drive.  I have never had Kubuntu do this for me on my main drive (it does power down my storage drive though). I'll guess and say that has something to do with the fact that Linux is always hitting up the hard drive for some reason or another...

---

### Post by adamklempner on 2007-11-04
Also, typing that previous message I notice that if I am doing anything, such as typing right now, I get hard drive activity every few seconds.  It is not heavy activity, just very brief accessing.   If I stop surfing/typing/etc. it gets quiet after a little while.

I have ~200MB of ram free and nothing has hit swap yet.

---

