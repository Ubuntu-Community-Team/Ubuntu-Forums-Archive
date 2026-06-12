---
title: "Autostarting PCMCIA cards"
date: 2007-06-18
forum: General Help
---

### Post by crokett on 2007-06-18
Am test-driving Ubuntu on my Thinkpad A22M.  Wireless card works fine except that when I reboot I have to remove/reinsert the PCMCI card after Ubuntu is up for the interface to activate.  ifconfig does not list it as an interface before I do this.  I suspect it has something to do with when PCMCIA support gets loaded.  Is there a way to tweak this to load before networking does?

---

### Post by timcredible on 2007-06-18
the startup scripts are in /etc/rcS.d.  if you want a script to run at startup, put in there with a capital S at the beginning of the filename.  make is S39filename if you want it to run before S40networking.

---

### Post by crokett on 2007-06-18
Of course you can.  :roll:  Thanks.  That was my dumb question for today.

---

