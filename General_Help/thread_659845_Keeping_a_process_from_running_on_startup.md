---
title: "Keeping a process from running on startup"
date: 2008-01-06
forum: General Help
---

### Post by myst1c on 2008-01-06
When i start up ubuntu, the first thing i have to do is go to gPS Process Manager and end a process called mono. If I don't end it, then within ten minute, my computer is running extremely slow, taking MUCH longer just to do simple tasks. Upon further investigation, I learned that it eats up most of my RAM.  I don't know what this process is for, and ending it seems to have no effect on my system.

Is there a way I could keep it from running when I start up my system?

---

### Post by jeffus_il on 2008-01-06
[Mono (software)]("http://en.wikipedia.org/wiki/Mono_%28software%29"), an open source implementation of the Microsoft .NET architecture

Some application is running under mono, do a "ps -ef | grep mono" at the command prompt and see what follows after mono ...

for example you may see:

mono /usr/lib/tomboy/Tomboy.exe --panel-applet --oaf-activate-iid=OAFIID:TomboyApplet_Factory --oaf-ior-fd=22

Which means the application Tomboy is the one you want to "get rid of"

---

