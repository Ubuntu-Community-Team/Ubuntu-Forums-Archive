---
title: "can i stop beagled indexing"
date: 2007-06-03
forum: General Help
---

### Post by xpan on 2007-06-03
Hi,

Is there any way to stop beagled-helper (which lies on the background) to stop indexing and start it again after some time?

The only thing that works for me is >kill -9 (not even simple kill) but it stops the process completely...

---

### Post by moterpent on 2007-06-03
If you want to stop beagle completely, just do a "beagle-shutdown".

If you want to disable indexing and crawling but would still like to perform searches against your indexed beagle info, restart beagled with the "beagled --disable-scheduler".

From what I can tell this puts beagle into a sort of query only mode allowing you to still perform searches but prevents it from running any crawling or indexing.

You could always automate something, such as turning it off during work hours and back on at night, with a basic cron job.

From what I've seen, even though beagle is frequently indexing various things, it is very non-intrusive due to it's process(es) running at a very low priority (nice value of 12).  Basically what that means is almost anything you do would take priority over whatever beagle is doing.  If you're only doing so much as basic web browsing or reading your email you are likely pushing beagle into the background -- until the system is more idle.

Good luck and I hope this helps.

---

### Post by xpan on 2007-06-03
thank you very much for your response. 
 
The problem is not the CPU. But the CPU fan which runs at full speed (making noise) when beagled is indexing files

---

### Post by paulHayes on 2007-10-18
In KDE, under the "start" menu, select "Configure Desktop", then "KDE Components" then pick "Desktop Search" which has the Beagle picture on mine.  From there you should be able to "disable" or "uncheck" the "Start Beagle indexing service"  and also uncheck any associations as well.  I also unchecked "Index my home folder".  Then I has to hunt down the running versions via "ps -ef | grep beagle" and kill each off "kill  PID PID PID PID" where PID is each PID I found from the ps command.

beagled-shutdown did not work for me.. but stopping it in the KDE panels does seem to halt it.  OpenSuSE10.2, 10.3 and KDE

beagle is of little use to me, so this process appear to kill it off completely.

---

### Post by jago25_98 on 2008-02-14
beagle hammers my IDE hard drive when it feels like it when I'm busy doing something on this laptop slowing everything to a halt.

Shame I can't get it to kick in at the right time.

---

### Post by dbera on 2008-02-14
Try any of the 0.3.x releases (its in Hardy and someone backported it to Gutsy). They behave much better.

---

