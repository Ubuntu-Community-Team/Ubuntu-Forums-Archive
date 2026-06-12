---
title: "KDM hangs on startup"
date: 2007-02-01
forum: General Help
---

### Post by StarsAndBars14 on 2007-02-01
Okay I think I have a bit of a problem.  I have KDM installed from 3.5.6 repos (upgraded a few days ago) and to do that 
- because I wanted GNOME off - I had to downgrade a few packages such as **kcontrol** and **kdebase-kio-plugins**.  
Now I'm getting strange results in my logging screen (from Ctrl-Alt-F7, Ctrl-Alt-F9 is my Xserver) which say:

> 
kdm: :0[5397]: Hung on XOpenDisplay(:0), aborting.
kdm: :0[5397]: Cannot connect to :0, giving up.
kdm[5382]: Display :0 cannot be opened.


This is after I symlinked the KDM startup file into my runlevel directories so it should be starting up at the bottom of 
the boot process.  But its not.  What's going on?

PS if I run KDM like 'sudo /etc/init.d/kdm restart' from the command line like I did just now it works fine.

---

