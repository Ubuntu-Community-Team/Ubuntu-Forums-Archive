---
title: "Ubuntu 18 is getting slower"
date: 2018-11-13
forum: General Help
---

### Post by elsuzu on 2018-11-13
hey guys!
I upgraded from (I think) ubuntu 16 to 18 a few months ago and i feel like the performance is getting worse. right now i have three apps opened: firefox, officelibre and audacity. and no matter which one i'm using at the moment, one of them keeps lagging, sometimes the app stops and i have to wait for it to de-freeze. it's gotten really annoying over time, i'm trying to record sound with audacity and the video keeps freezing. i try to write something while listening to the recording and both apps crash. what's going on and what can i do to get it running smoothly again?
i didn't have these problems on ubuntu 16 (at least not regularly) and i don't think i had these problems a few months ago when i installed the upgrade.

any help is appreciated! :)

---

### Post by Autodave on 2018-11-13
First of all, some info on your system would probably help us.  Secondly, upgrading from one release to another seldom works well and usually causes more problems than you can imagine or fix.  I always backup everything and do clean installs: much less headaches that way.  But, please give us some specs on your machine.

---

### Post by HermanAB on 2018-11-13
These type of posts always amaze me.

There are little utilities called 'top' and 'ntop', which tells you what is going on in your system.  

Use them.

---

### Post by Skaperen on 2018-11-13
elsuzu: a common cause for this kind of behavior is not enough RAM.  the other processes are swapped *out* to (the swap space on) disk, while the app you are using is swapped *in* to RAM because it is the most active.  i have an old netbook with only 1 GB of RAM and this kind of thing happens when i open too many apps.  my primary laptop has 16 GB RAM and doesn't see this issue nearly as often.  it does happen when i run my backups and do nothing else for a while.  the backups can use a lot of RAM for buffer space since it reads so many files.

they are making programs bigger these days.  some are now many times larger than a whole computer was several years ago.

another thing that can make this worse is a slow disk drive.  older IDE drives can be slow.

lots of technical info about your system can help us see what might be wrong in your case and what to do to figure out the best solution.  if your don't know any info, just say you don't know and we can guide you to find out.  for example, the "top" program shows the amount of RAM, the amount of swap space and its usage level.

do you know how to open up a shell terminal and type in commands?

---

### Post by MSGone on 2018-11-14
Try bleachbit before you try a fresh and clean install. Bleachbit does a great job in deleting trash, orphaned parts of programs you deleted, things that are no longer needed, and general wasted entries.

---

### Post by HermanAB on 2018-11-14
Err... Judging by the number of people on this forum who complain that their computer is unusable after running Bleachbit, I would not use it myself...

The thing is, if your computer is slow, run 'top' and see what is using the computing resources, then kill/disable that problem program.  

Sometimes, when I find a problem piece of software that cannot be cleanly uninstalled, then I just rename it, so that it cannot run anymore (mv program program.bad).  There is always a simple fix, but first, you have to identify the problem.

---

### Post by elsuzu on 2018-11-14
thanks for the replies, guys! i know how to use the terminal as long as someone tells me what commands to use ;) 

my laptop has 4 GB RAM, i can't judge if that's enough, what do you think? 

here's what the terminal says when i type in top:

top - 17:15:35 up 1 day,  3:03,  1 user,  load average: 1,97, 7,10, 7,26
Tasks: 247 gesamt,   1 laufend, 196 schlafend,   0 gestoppt,   1 Zombie
%CPU(s):  7,6 be,  4,4 sy,  0,0 ni, 70,6 un, 17,4 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Spch :  3888804 gesamt,   286052 frei,  2958612 belegt,   644140 Puff/Cache
KiB Swap:  4043772 gesamt,  1764736 frei,  2279036 belegt.   563584 verfü Spch

the numbers are changing by the second even though i'm not doing anything. my system runs in german, i hope you can still make something out of this :) there's a lot listed that i don't know what it is, for example: thermald, xorg, Web content, ibus-daemon. how do i know what to kill if i don't know what it is?


opening the "system monitoring" and then "processes", it shows more than "top". opening "file system", there's a bunch listed that run on 100%, they're on the drive /dev/loop and the type sqaushfs. i don't even know what's that supposed to be lol is it relevant?
if you need more info about my system or anything else please let me know! (and how i can find that info :) )

---

### Post by HermanAB on 2018-11-14
Well, a system that is doing 'nothing', should be 98 to 99% idle.  You should not have any processes that use 100% CPU for multiple seconds.

If you can identify something suspicious, Google search its name together with the key word 'linux', for example 'linux thermald', to see what it is:
thermald - Debian Wiki
[https://wiki.debian.org/thermald](https://wiki.debian.org/thermald)
Jan 11, 2014 - Linux thermal daemon (thermald) monitors and controls temperature in laptops, tablets PC with the latest Intel sandy bridge and latest Intel ...


So that is a legitimate system process and you should leave it alone.


Also see this thread: [https://ubuntuforums.org/showthread.php?t=2405766](https://ubuntuforums.org/showthread.php?t=2405766)

---

### Post by elsuzu on 2018-11-15
hey guys, i just realized that if i put the laptop in and out of sleep mode (when i didn't shut down but instead closed the laptop) it starts to get slow. when i shut down and start again, it's fairly fast (could be faster but it's an old computer, what can i expect? lol)
is there anything to do about it besides not putting it to sleep mode anymore?

---

### Post by Ars_Ivci on 2018-11-15
> **elsuzu said:**
> 
opening the "system monitoring" and then "processes", it shows more than "top". opening "file system", there's a bunch listed that run on 100%, they're on the drive /dev/loop and the type sqaushfs. i don't even know what's that supposed to be lol is it relevant?
if you need more info about my system or anything else please let me know! (and how i can find that info :) )

/dev/loop lines show snap programs and 100% is not the CPU use. Some programs run as snaps in 18.04 and they have /dev/loop1, loop2 etc as device names. Maybe one of them tried to upgade when you were doing stuff.

Someone has mentioned it previously but let me repeat: If you can backup you files, I would also recommend a clean install of 18.04, not an upgrade. I also have a very old computer, 8 years or so and 18.04 was performing nice. I switched to Unity on 18.04 and it is way better now.

---

### Post by wildmanne39 on 2018-11-15
>  Err... Judging by the number of people on this forum who complain that their computer is unusable after running Bleachbit, I would not use it myself... 
+1, I used bleachbit a few times years ago and it always removed packages that broke my system, I mean every time!

---

### Post by HermanAB on 2018-11-16
"it always removed packages that broke my system" - I learned many years ago, when all the Linux installers were absolutely horrible, NEVER to uninstall ANYTHING and I still keep to that philosophy.  

I don't even trust the update features and rather disable auto-updates and re-install my systems from scratch every year or three.  I'm sure this saves me many hours of 'happy debugging' of broken systems...

---

### Post by elsuzu on 2018-11-16
i actually did reinstall Ubuntu 18, I misspoke earlier. I tried updating first and almost made my computer unusable lol it was a hassle to get it working again and i was happy I made it. I really don't want to reinstall again if there's any workaround it.

again, as long as I don't get the computer out of sleep mode it runs fairly smoothly (could be better, but what do i expect from this old, cheap laptop?) but out of sleep mode it's just no fun anymore to use it. It took me 5 minutes to open the terminal, type in "top" and get the info from it.

---

