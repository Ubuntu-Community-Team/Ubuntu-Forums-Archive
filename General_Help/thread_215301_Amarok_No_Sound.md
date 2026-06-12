---
title: "Amarok: No Sound"
date: 2006-07-13
forum: General Help
---

### Post by Soda Ant on 2006-07-13
I just installed Amarok on my recently installed Dapper system (AMD64) and I get no sound when playing MP3 files. Everything works fine when I play the same files with XMMS.

How do I fix this?

---

### Post by linuksamiko on 2006-07-13
Which engine do you use to play sound in amarok? It is most likely that your installed engine doesn't support mp3. Try it out with ogg!

this should fix the problem:
install the packages amarok-xine, libxine-extracodecs, libxine-main1

after installation you go into the options of amarok an set audio-engine to xine (maybe it is set to xine allready)
Now it should work

---

### Post by Soda Ant on 2006-07-13
I'm using the xine engine.

What repository is libxine-extracodecs in? It's not in any of the standard ones (universe, multiverse, etc.)

---

### Post by Jucato on 2006-07-13
Amarok uses the xine engine. libxine-extracodecs is needed to play restricted formats. It's located in the Dapper (not dapper-upgrades, not dapper-backports, just plain dapper) multiverse repository.

---

### Post by Soda Ant on 2006-07-13
Got it. Thanks. I'm now getting sound with Amarok.

---

### Post by alwiap on 2007-09-13
sorry to bump, but I have the same problem.  I was using Rhythmbox Media Player and it can play anything fine, I get sound, and I've been wanting to use Amarok.

Just to be sure, I made sure that the packages 'packages amarok-xine, libxine-extracodecs, libxine-main1' were installed in Synaptic Pkg Manager, they all were, but I reinstalled them to be sure.  Xine was the engine that was in use in the Amarok Preferences.  I still get no sound in Amarok and sound everywhere else.  Help!

ty

---

