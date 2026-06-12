---
title: "Pidgin closes instantly"
date: 2007-06-21
forum: General Help
---

### Post by Taleman on 2007-06-21
I Installed Pidgin 2.0.2 on Feisty but anytime I try running it opens and then instantly closes itself. it wasn't always like this, it was working for a while but then it just all of  a sudden closed itself and ever since its been instantly closing everytime i try to run it. Any ideas on what the problem might be?

---

### Post by Happy_Man on 2007-06-21
Try running Pidgin from a terminal and post back with any errors it throws.

---

### Post by NeoLithium on 2007-06-21
Try running it from terminal with the command ```
pidgin
``` and paste any errors that showed up.  Have you installed any of the plugins recently?

---

### Post by Taleman on 2007-06-21
ok i get a :

"Segmentation fault (core dumped)" Error

---

### Post by NeoLithium on 2007-06-21
Hmmm, I've found a few things about segfault problems.  How did you install it, and from what source?

---

### Post by Taleman on 2007-06-21
I basically followed the instructions described here:
[http://jhcore.com/2007/06/04/install-pidgin-in-ubuntu/](http://jhcore.com/2007/06/04/install-pidgin-in-ubuntu/)

---

### Post by NeoLithium on 2007-06-21
Ahh, ok. There's a better version, at [http://www.getdeb.net](http://www.getdeb.net)  What you may want to do, is cd back to the directory where you compiled and installed it, then type ```
sudo make uninstall
``` and then grab the debian file from GetDeb, I installed that one on Feisty and it seems to work just fine :)

Hope this helps,

---

### Post by Taleman on 2007-06-21
Awesome, thanks that worked! :D

---

### Post by Saxomophone on 2007-08-08
I'm having the same problem. I've uninstalled pidgin, but how do I install from the .deb?

sudo dpkg -i "filename".deb gave me "Errors were encountered while processing pidgin


Am I doing something wrong?


EDIT: Never mind, i needed to install some dependencies, and pidgin didn't uninstall very cleanly. I'm good now.

---

