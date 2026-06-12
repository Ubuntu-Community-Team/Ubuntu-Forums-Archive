---
title: "Firefox doesn't rec. Flashplayer ~ Screwy Situation"
date: 2013-03-08
forum: General Help
---

### Post by neu5eeCh on 2013-03-08
So... I have two Firefox installations - two profiles. It's always  worked beautifully on every other system (so I can use different  Google/Gmail profiles at the same time). 
[INDENT] 
[/INDENT]
For some reason, which I cannot wrap my head around, the second firefox  install on this system (64bit Xubuntu 12.04) refuses to acknowledge the  flashplayer installation that works just fine with my default profile  and Firefox installation. Any ideas? How do I get the second install (of  Firefox) to recognize libflashplayer.so!?! I see it right there: [INDENT] 
/usr/lib/flashplugin-installer/libflashplayer.so

[/INDENT]
Can I create a symbolic link somewhere or where I can I copy libflashplayer so the second install will recognize and use it? (I've tried Flash Aid - no luck.)

---

### Post by neu5eeCh on 2013-03-08
Okay. Solved. If I could throw every four letter word in my vocabulary at these jerks... Firefox, the whole bunch of them, really **ticked** me off. 

Here's the deal. I guess Firefox is quietly trying to kill their 64 bit version of Linux (or that's the rumor). But the ----'s don't tell you this. They just let you download the 32-bit version and give you no indication, none, none whatsoever, that you're doing so. This means that a second install, like mine, isn't going to work with any plugins. They don't even tell you this on the ABOUT page. I had to carefully read the automatically generated pluginreg.dat to see that I wasn't using the 64 bit version. I wasted an entire afternoon on this. I had to go to their FTP site to download the 64 bit version. Anyway... if this happens to anyone else in the future, make sure you're using the 64 bit version.

---

### Post by neu5eeCh on 2013-03-08
Moderators: Please mark this thread solved. I don't know how to since ya'll changed this forum around.

---

### Post by ajgreeny on 2013-03-08
You should have installed firefox with synaptic or software-centre then you would have got the correct architecture version.

Why did you download direct from mozilla?  I assume that is what you must have done to get into this situation.

---

### Post by neu5eeCh on 2013-03-08
> **ajgreeny said:**
> You should have installed firefox with synaptic or software-centre then you would have got the correct architecture version.

Why did you download direct from mozilla?  I assume that is what you must have done to get into this situation.

Because this was a second install. I have two separate Firefox installations that I run simultaneously (and independently under different profiles). This can be incredibly handy for a variety of reasons. For me, it allows me to keep separate g-mail accounts open at the same time.

---

### Post by gordintoronto on 2013-03-09
I manage this challenge by having Firefox and Chrome installed, and having them both open most of the time. Much simpler solution.

At the top of the messages, look at "Thread Tools." I think you will find "solved" there.

---

### Post by vasa1 on 2013-03-09
> **gordintoronto said:**
> ...
At the top of the messages, look at "Thread Tools." I think you will find "solved" there.
To mark threads solved in the upgraded forum, see this: [http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730](http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730)

---

