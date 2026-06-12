---
title: "aMule takes all CPU usage"
date: 2007-04-08
forum: General Help
---

### Post by abelthorne on 2007-04-08
Hello,
I've encountered a problem that seems to have happened recently with aMule (although I don't use it often).
While browsing the web with Firefox, display started to be very slow (moving into the page, moving from one desktop to another, etc.) and I saw with the system monitor that aMule was taking a lot of CPU usage (up to 85 %). It stayed that way about 1 minute and then get back to about 5 % of CPU usage. But it started again and again every 10 minutes or so. Since this morning, I get these "full CPU usage" cycles every few minutes and it happens only with aMule. I tried to quit and restart it and all seemed fine until it started again maybe one hour later.

I'm considering that it might come from a hardware issue as, from monthes now, I sometimes hear a "click" in my PC that I haven't been able to track down (a fan stopping and restarting ? hard drive heads ?...) and I have the impression that these clicks appear far often today and seem to coincide with the moment aMule CPU usage drops back to a normal rate.

Anyway, has anybody encountered this kind of problems with aMule recently ?

---

### Post by btlee on 2007-04-24
I confirm this bug. 
On my laptop, which has centrino 1.8MHz cpu and 2 giga ram and is not relatively behind the times, aMule consumes a lot of CPU (up to 80%).
Actually, this bug had been fixed some times ago, as shown by the following link.

[http://ubuntuforums.org/showthread.php?t=372875&highlight=amule+cpu](http://ubuntuforums.org/showthread.php?t=372875&highlight=amule+cpu)

What happened after the fixation?

---

### Post by abelthorne on 2007-04-24
I'm not sure it is the same bug (although it looks like) as I searched on Google and it seems that it is a known amule bug related to Gtk that has not been fixed "upstream". But the amule website was down when I checked so the only advice I found was not to run amule with GUI but to use the no-GUI amuled instead (which can be controlled from a browser).

---

### Post by another_sam on 2008-06-11
Same problem here. Uses 45-50% of CPU on a core duo.

Nobody else has this problem currently?

My system: Ubuntu 8.04 updated.

edit.: not always. right now uses 2-3%. but this evening was at 45-50% for 60+ minutes.

---

### Post by Hallvor on 2008-06-12
I confirm it. It just started recently. Try updating aMule to version 2.2.1 and see if it helps. It was released yesterday, and there are stable builds for Ubuntu on the aMule webpage.

---

### Post by another_sam on 2008-06-13
Summarizing for nubs:

System > Administration > Software Sources > Third-Party Software > Add

copy n paste this:
deb [http://ppa.launchpad.net/festor90/ubuntu](http://ppa.launchpad.net/festor90/ubuntu) hardy main

click on Add Source and follow the wind...

source:
[http://www.amule.org/](http://www.amule.org/)
[http://forum.amule.org/index.php?topic=15230.0](http://forum.amule.org/index.php?topic=15230.0)

Thank you Hallvor !!

---

### Post by keyser.soze on 2008-06-25
> **Hallvor said:**
> I confirm it. It just started recently. Try updating aMule to version 2.2.1 and see if it helps. It was released yesterday, and there are stable builds for Ubuntu on the aMule webpage.

It doesn't fix the problem. 
Same story even with ICH and AICH disabled, less than 200 connections
(default is 300) per download and UPLOAD COMPLETE CHUNK disabled.

---

### Post by Friedel on 2008-06-28
They wont fix it, looks like you have to compile it yourself and when you're lucky it works.

[http://forum.amule.org/index.php?PHPSESSID=a262f6724c4f718f6e3c73316ed8db6b&topic=15317.msg80706#msg80706](http://forum.amule.org/index.php?PHPSESSID=a262f6724c4f718f6e3c73316ed8db6b&topic=15317.msg80706#msg80706)

---

