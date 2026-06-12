---
title: "[SOLVED] Mythtv adds login manager and xfce"
date: 2008-02-05
forum: General Help
---

### Post by The Avatar of Time on 2008-02-05
Hello, I have an annoying little problem installing Mythtv. What I have is a command line install of Ubuntu Gutsy 64 bit, which I then add xorg and fluxbox along with other irrelevant apps. Then I install mybuntu-control-centre. 

The reason is it is the only way I have gotten Mythtv to work without getting a 'could not connect to database' error. Now this installs Mythtv just fine. The downside is that it adds a login manager and xfce, and I do not want either of those two things. Also I can't seem to remove them either. 

So my question is this, is it possible to install Mythtv without getting xfce and a login manager put on my computer? Can it be done with mythbuntu-control-centre? I don't care if I have mybuntu-control-centre or not so long as I can get mythtv working without getting stuck with xfce and a login manager. What would be the proper way to accomplish this? 

Also I would prefer to use the command line to install Mythtv but agian I don't really care how I have to go about it. Thanks for any help.

---

### Post by The Avatar of Time on 2008-02-09
Hmm, solved that. Seems to make a big difference as to using 'sudo aptitude install mythtv' instead of 'sudo apt-get install mythtv'. I do not really see why it should but that worked for me.

---

