---
title: "Can't re-install Firefox"
date: 2006-08-01
forum: General Help
---

### Post by Roobert on 2006-08-01
I had impatiently installed Firefox 1.5.0.4 in /opt a while back, over-writing the default Ubuntu 6.06 Firefox (I think I created new symbolic links to point to my custom install.) Of course, that prevented Synaptic from being to give me Firefox updates anymore. So, I removed my /opt firefox, and trying to re-install Firefox via Synaptic doesn't allow me to launch the program. Synaptic goes through the motions and seemingly does a successful install, but the program won't launch from the icon on the taskbar or from Applications/Internet/Firefox. 

Typing ```
which firefox
``` doesn't show it being installed anywhere, despite Synaptic showing that it is indeed installed!

What am I doing wrong here?

~ Roobert.

---

### Post by mjm115 on 2006-08-01
did you delete ~/.mozilla/firefox directory?  If you didn't then it still has your old settings and shortcuts.  you have to remove that directory and the installation should work.

---

### Post by Roobert on 2006-08-01
Yes I just tried deleting the .mozilla directory from Home, rebooted, and Firefox still won't load. I can't find anything for it in /bin or /usr/bin, even though Synaptic says it's installed.

---

### Post by mjm115 on 2006-08-01
How about:

> 
apt-get remove --purge firefox


If that doesn't work, I'm fresh out of ideas.

---

