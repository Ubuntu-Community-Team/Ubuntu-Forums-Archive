---
title: "programs take forever to load ubuntu 14.04"
date: 2015-01-31
forum: General Help
---

### Post by thomas_margotta on 2015-01-31
whenever i click on a program it takes at least 10 seconds to load. this deffinately should not happen. i have a samsung ativ book 4 with an i5 processor and 6 gb of ram. its not like im doing that much at a time. is their a program in ubuntu that is intended to clean it up and make it run better? by the way, when i was installing wine it didnt work properly and i had to terminate the terminal window while it was running and run sudo dpkg --configure -i or something. im not sure if that would affect it.

---

### Post by TheFu on 2015-01-31
Linux systems don't usually get slower over time.  That means there is probably something wrong with your system - hardware.  
So - as with all Linux troubleshooting - I ask, what do the log files say?  Any warnings or errors in them?

Thinking a little more about this. There are 2 ways for a system to get slower.
a) the root file system, /, is almost full
b) RAM is fully used and swap is being used for most things.  Modern web browsers are notorious for sucking RAM, especially if there are flash parts.  So, which processes are using all the RAM?

Sometimes having slow DNS can lead to slow program loading too. This generally doesn't impact stand-alone programs.

---

### Post by ajgreeny on 2015-01-31
Start one of those slow-starting applications in terminal to see if you get any clues.
You could also open a terminal and run **top**, hit upper case M to sort by memory, then start one of the problem programs and while it is opening keep a watch on the program at the top of the top terminal window.

---

### Post by mc4man on 2015-01-31
If poor performance extends past just the openings then maybe you're using lvmpipe. Check in System Settings > Details > Overview or install mesa-utils & this could show - 
```
glxinfo |grep 'OpenGL renderer string'
```

---

### Post by thomas_margotta on 2015-02-01
how do i get to log files. their stored in /var/log, but their are lots of files there. and how do i tell what in the file tells me something is wrong..

---

### Post by thomas_margotta on 2015-02-01
also once the program is open it works fine. it just takes too long to open things. and its everything. not just a singular program. and mesa-utils? idk what that even is. i was a windows person until they decided to release crap operating systems bloated with adds and nothing useful whatsoever.

---

### Post by thomas_margotta on 2015-02-01
and chrome is taking up most the memory according to TOP if i understand it correctly. i hit M and the instances of chrome were up top. i say instances because their were more than one. in windows that was normal. not sure about ubuntu..

---

### Post by thomas_margotta on 2015-02-01
also my computer likes to send an error report when it starts for some reason...

---

### Post by Bucky Ball on 2015-02-01
Please post that error report here.

---

### Post by TheFu on 2015-02-02
> **thomas_margotta said:**
> how do i get to log files. their stored in /var/log, but their are lots of files there. and how do i tell what in the file tells me something is wrong..

I hear that normal ubuntu desktop has a GUI for this.
I do it this way: [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)

Linux systems come with lots of tools, especially for text processing. Most "beginning linux" books cover these, provided they don't condone point-n-click all the time.

---

### Post by thomas_margotta on 2015-02-02
executable path
   /usr/lib/x86_64-linux-gnu/hud/hud-service
package
   hud 14.04+ 14.04.20140604-0ubuntu1
problem type
   crash
title
   hud-service crashed with SIGABRT in QMessagelogger::fatal()
ApportVersion
   2.14.1-0ubuntu3.6
architecture
   amd64
CoreDumb
   (bianary data)
current desktop
   Unity
Date
   mon feb 2 21:21:50 2015
dependencies


how do i automatically select this crap and copy it, i cant just select all of it and click copy. or what parts do you need? theres another error report as well.

---

### Post by thomas_margotta on 2015-02-02
also, i found updates to chrome, base, and something else, just ran the updater. gonna restart and see if it wants to make error reports still.

---

### Post by thomas_margotta on 2015-02-02
doesnt seem to have any error reports, still running slowly. on a slightly related matter, does anyone else experience problems with tribler, the torrent client? because i'll start it, and it will take forever to load. grey itself out for a bit sometimes. say loading torrents forever. the anonymity service itself is a nightmare as well so i dont use it. even if all the torrents are stopped itll take a long time to load. also, if i pause or stop or start a torrent i will have to restart tribler in order for it to show up started, and sometimes download. its a real pain in the a$$. probably going to be uninstalled unless their is an easy immediate solution seeing how transmission works flawlessly.

---

### Post by thomas_margotta on 2015-02-02
also ubuntu wanted to check my harddrive after installing the updates. and i just got a brand new western digital blue 1tb hard drive so if its failing so is the company western digital.

---

### Post by Bucky Ball on 2015-02-02
The torrent issue is the stuff of a new thread. You will improve your chances of getting help with it as your new support request is buring on a thread with an unrelated title. Gets confusing trying to fix more than one issue a thread so we try to avoid doing it, for everyone's benefit. ;)

PS: Ubuntu wants to check hard drives after every 25-30 or so boots (can't remember the exact number). It is normal and in NO WAY indicates there is anything wrong with the drive.

---

### Post by thomas_margotta on 2015-02-02
ahh, understandable. yeah, honestly i dont care about tribbler. im going to finish seeding everything, move it, and remove tribler. it kinda just sucks. and the hard drive, i assumed so.

---

