---
title: "Azureus Opens and Crashes"
date: 2007-05-18
forum: General Help
---

### Post by flowingfire on 2007-05-18
Hi everybody.  Azureus just opens and crashed immediately.  Any ideas?

I re-installed it: same issue.

---

### Post by Jason Boyle on 2007-05-18
What firewall or spyware prevention programs are you running. Or even antivirus?

---

### Post by flowingfire on 2007-05-18
I'm not running any anti-spyware, antivirus, or firewall programs as far as I'm aware of....

Of course, I think I may have attempted a seemingly-failed installation of an anti-virus program through Synaptic or something a few days ago... Maybe it is installed and I don't know it, but if it is, it doesn't show up in my system tray or have any indicator that it's installed whatsoever.

---

### Post by jackmc on 2007-05-18
uninstall it, then install it from their website. It is a bug.

---

### Post by scooper on 2007-05-18
It's more of a pain to install from the azureus website.  You may want to try replacing Azureus2.jar with the one from the website installer.  Search the forum.  There's more specific instructions.  Try searching "Azureus2.jar" or "azureus crash", or whatever...

I had an immediate crashing problem that was fixed by doing this.  If you can't find it we can figure out a way for me to get my copy to you, if you'd like.

---

### Post by fenian on 2007-05-18
If you don't want to install from the website or replace the jar file you can run these commands to get Azureus up and running...
> 
rm .azureus/.lock
rm .azureus/logs/*.log
rm .azureus/logs/save/*

---

### Post by multi.lectical on 2007-05-30
WOW, thanks, that was definitely the easy way

---

### Post by zhinker on 2007-06-01
Sorry for the hijack (the problem's solved anyways) but anyone know how to subcribe to a thread without posting two it?  this is the second time I've had this problem with azureus and i would've liked to save it (by subscribing to it) without having to write a post...too late for that now though :p

---

### Post by mgmiller on 2007-06-02
At the top of the thread click on "Thread Tools", then click on subscribe to thread.  You will have choices about e-mail notification, etc.

---

### Post by jackmc on 2007-06-03
> **fenian said:**
> If you don't want to install from the website or replace the jar file you can run these commands to get Azureus up and running...

Way too easy, thanks heaps. Better than installing from Soundforge!

---

### Post by FaceLeg on 2007-06-08
> **fenian said:**
> If you don't want to install from the website or replace the jar file you can run these commands to get Azureus up and running...

Thanks a lot, this really helped!

I reinstalled Feisty because of this problem...

Do you know why this happens?

---

