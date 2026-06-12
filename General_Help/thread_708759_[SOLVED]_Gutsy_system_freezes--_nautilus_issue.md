---
title: "[SOLVED] Gutsy system freezes-- nautilus issue?"
date: 2008-02-26
forum: General Help
---

### Post by belfasttim on 2008-02-26
Hi-- I've been having strange system freezes in 7.1 on a Dell laptop. It's a dual core with 4GB RAM, and at random times the display will flash, all desktop icons and menus will disappear (though the desktop background sticks around)-- after a second or two the menus/icons will return, but there will be about 100 instances of nautilus open to my home directory. The mouse still moves, I can open a terminal (but not type in it) and nothing else works (eg. I can't close any of the nautilus windows). 

I can't use ctrl-alt-Fx due to another bug, so I'm usually reduced to restarting X with the ctrl-alt-backspace, though sometimes it goes into a hard freeze and I cna't do anything except power down.

Any help much appreciated. This seems to happen once or maybe twice a day, and doesn't seem to be any rhyme or reason to it as far as what apps are running etc.

thanks

---

### Post by Crafty Kisses on 2008-02-26
That's weird, you think it could possibly be overheating issues?

If your worried you can always check your X server logs.

```
nano /var/log/Xorg.0.log
```

---

### Post by belfasttim on 2008-02-26
Hi Codename-- yeah, I thought about overheating as a possible issue. I guess I could grab one of those cooler mats and see if that helps. 

I checked /var/log/Xorg.0.log and the file is empty. That seems a bit odd.

thanks for the reply

---

### Post by belfasttim on 2008-04-17
Just to finish this thread in case anyone searches this issue, the cooling fans didn't help-- freeze ups continued.

It turns out it may have been the tracker indexer. There's bugs reported with the indexer on dual core systems, like mine, where the tracker will eat up all resources of one CPU. THis is what was happening to me, and causing instability and freezes.

I uninstalled tracker (apt-get remove tracker-search-tool tracker-utils) and so far so good-- no problems. 

Hope this helps someone.

---

