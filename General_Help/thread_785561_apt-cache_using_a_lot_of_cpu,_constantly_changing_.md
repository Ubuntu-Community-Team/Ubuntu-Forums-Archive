---
title: "apt-cache using a lot of cpu, constantly changing pid"
date: 2008-05-07
forum: General Help
---

### Post by moodog on 2008-05-07
basically the same as this thread here:

[http://ubuntuforums.org/showthread.php?p=4769731](http://ubuntuforums.org/showthread.php?p=4769731)

apt-cache chews up a lot of cpu - currently sitting pretty stable at 92% and 75% of dual core. It appears to change it's PID every second (well, every time top updates). Any idea why?

---

### Post by punischdude on 2008-05-09
similar problem here,


apt-cache using 100% CPU and freezes some applications a few seconds.

any idea?

---

### Post by llano on 2008-05-09
Same problem for me. apt-cache goes to 100% cpu usage. freezes whatever program I am using for a few seconds, then dies. rinse repeat. Extremely annoying.

Responses appreciated.

---

### Post by Chin@ski on 2008-05-10
same thing for me , from logging-in apt-cache takes 100% of the cpu

---

### Post by moodog on 2008-05-15
Anyone got any ideas? it can take a very long time to settle down, and seems to happen nearly every time I boot up...

---

### Post by punischdude on 2008-05-17
Dunno why, but using firefox-2.0 instead of firefox-3.0 fixes the problem for me.

---

### Post by pluckypigeon on 2008-05-21
If you have a lot of repos in sources.list the apt-cache will cache all the programs. try removing some of your 3rd part repos this will solve most problems:)

---

### Post by pluckypigeon on 2008-05-21
also dont forget to run ```
sudo apt-get update
```after

---

### Post by Magario on 2009-04-18
My computer was having the same problem...what was is weird is that i've placed the cpu and memory monitor on the bottom toolbar and it was showing 100%, and i've placed the sysmonitor screenlet too...but as I opened the SYSTEM MONITOR it was showing only 8, 10, 9 % of usage while the screenlet and the toolbar were showing 100%...but the cooler was going nuts...so i've tried to close the system-monitor app on the system monitor itself...it reduced the usage of CPU...
that was waaaay too weird

---

### Post by jimbob22 on 2009-04-20
I get the same problem when I log in - it freezes kde and I often have to kill apt-cache from the console (or wait an unspecified amount of time for it to unfreeze). I would like to ask

1) why is apt-cache started when I log in?

2) what is it doing at that time?

3) how can I control it, e.g. to do whatever needs to be done at another time more convenient for me?

---

