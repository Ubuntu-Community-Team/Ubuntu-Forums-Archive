---
title: "[SOLVED] Is it safe to update yet?"
date: 2008-01-22
forum: General Help
---

### Post by EtherBunny on 2008-01-22
I heard that there were some issues regarding the latest X server update and Java applications.

Is that fixed yet?

---

### Post by skymera on 2008-01-22
ive updated fine :wink:

---

### Post by dgib on 2008-01-23
i've been having problems since i updated as well, 
X Server error xxx

i get these problems when opening VLC, KDesklet to mention a few
also eclipse. and i often get out of memory errors as well :/

---

### Post by DMK62 on 2008-01-23
There was a problem with the first x update last week that caused problems with vlc, java, etc. A new version of the xorg-server update was released last week to resolve the problems.

From a terminal run

sudo apt-get update 

and then 

sudo apt-get upgrade

After it is upgraded restart x by logging out and back in or by restarting the computer.

hth 

Dale

---

