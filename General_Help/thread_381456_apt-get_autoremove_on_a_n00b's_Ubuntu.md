---
title: "apt-get autoremove on a n00b's Ubuntu?"
date: 2007-03-10
forum: General Help
---

### Post by CaptSaltyJack on 2007-03-10
If I set up Ubuntu or a n00b, and they install/uninstall a bunch of games/etc., will the system ever automatically do an "apt-get autoremove" to keep their system free of orphan libs/apps?

---

### Post by Famicommie on 2007-03-10
As long as you uninstall with [code]sudo aptitude remove[/url] you should be fine.

Use aptitude, not apt-get. [Click here for an explanation](Click here for an explanation)

---

### Post by CaptSaltyJack on 2007-03-10
Nope.. any n00bs I know will be using Synaptic or most likely the Add/Remove Programs menu option, no shell stuff.

---

### Post by aysiu on 2007-03-10
Will the "noobs" even care about the orphaned libraries?

---

### Post by CaptSaltyJack on 2007-03-10
Probably not.. but the orphaned libs are still hanging around & eating up space, especially if some of those orphaned files are game data packages exceeding 40-50MB..

---

### Post by aysiu on 2007-03-10
Considering most Windows users leave .dll files installed after removing programs, I don't think it should matter.

Are these people using 4 GB hard drives? Is hard drive space that tight?

---

### Post by Famicommie on 2007-03-11
I suppose the best option in this case would be to tell them to uninstall via Synaptic, and have them select the "Complete Removal"

Also, I can't imagine that game data packages would be orphaned.

---

### Post by danbh on 2007-04-04
gtkorphan

sudo aptitude install gtkorphan

Hey, its a short answer, but it will be self explanatory.  

Here is the website that I found it at:  [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)


I wanted to clean out my installation of ubuntu.  I had installed all sorts of codecs, video card drivers, easyubuntu and the such, which was messing my upgrade to feisty.
I added ubuntu-desktop/standard/minimal to the hibernate list, along with about 5 other packages that I knew that I wanted (wireless card drivers and some other stuff).  Then, I removed everything, several times, until nothing left was listed.  I was fine.

I suggest running this, just to be safe:
sudo apt-get install ubuntu-desktop^

---

