---
title: "Xserver error - won't start after reboot..."
date: 2007-04-01
forum: General Help
---

### Post by tiger.woods on 2007-04-01
I just rebooted my box and am getting the "Fatal Server error: no screens found" from X server.

What's the best way to go about finding out what happend and fixing it...

TIA

TW,

---

### Post by djrosen on 2007-04-01
First, just in case, back up the xorg.conf 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup-<put date here>

next try reconfiguring your xserver

sudo dpkg-reconfigure xserver-xorg

---

### Post by tiger.woods on 2007-04-01
I get "Error running install command for Nvidia"...

followed by:

"Fatal server error: no screens found"

TW,

---

### Post by zvacet on 2007-04-02
Try to replace **nvidia** with **nv**.

---

### Post by tiger.woods on 2007-04-02
So, a quick follow up...

If everything was fine, ubuntus been running for about a month or so with no issues on reboots and I haven't installed anything new in the last few day's, etc. to cause the problem.

Why in the world would my Xserver.conf be messed up or need changing? It doens't make any sense...

tw,

---

