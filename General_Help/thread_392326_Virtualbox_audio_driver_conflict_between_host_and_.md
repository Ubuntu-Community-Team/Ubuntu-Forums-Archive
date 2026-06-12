---
title: "Virtualbox audio driver conflict between host and guest."
date: 2007-03-24
forum: General Help
---

### Post by Barleyman on 2007-03-24
Hi, I am currently running the following:

HOST: virtualbox 1.3.8 binary version - Ubuntu Edgy (firefox 2/flash 9)

GUEST: XP home edition SP2

Hardware: P4 3.0ghz 2GB ram

The problem: When guest is running with alsa sound driver enabled, my host firefox will crash/freeze on certain sites running flash with sound. (eg. justin.tv)

Running host firefox from the terminal gives me the following: 

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2) 
etc.

I am a little unsure of what to try next.

---

### Post by elyk on 2007-04-07
I've got the same problem. Virtualbox hogs the sound card for the whole time it's open. Setting to null solves the problem. Is there a way to force virtualbox to use esd?

---

### Post by Barleyman on 2007-04-07
Check out this thread from the vbox mailing list archive.

[http://vbox.innotek.de/pipermail/vbox-users/2007-March/001265.html](http://vbox.innotek.de/pipermail/vbox-users/2007-March/001265.html)

It seems this is an issue with the 2.6.17 kernel and vbox.

---

### Post by elyk on 2007-04-12
Then I guess I'll try waiting a week or so until Feisty is released with kernel 2.6.20, and post back if it works then.

---

### Post by naseem on 2007-04-14
I'm in feisty but the problem persist, if I louch the gust first than alsa on the host results locked out, if I play a media on the host "feisty" and then open vb guest it pops up an error window about sound

---

