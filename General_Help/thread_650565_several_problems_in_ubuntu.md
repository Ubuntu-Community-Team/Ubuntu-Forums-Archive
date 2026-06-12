---
title: "several problems in ubuntu"
date: 2007-12-26
forum: General Help
---

### Post by tisa on 2007-12-26
hi all,
well, I'm trying to install compiz, and as many users of ati i have problems. i've installed the drivers, so it shoud work. but when I type compiz at terminal it says:
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
so probably the problem is xgl, so i've searched how to install xgl, and it's supposed to install  xserver-xgl.And here comes the big problem: when I try to install with sudo apt-get install xserver-xgl something the terminal always says that:
E: Couldn't find package compizconfig-settings-manager
E: Couldn't find package xserver-xgl
and always the same error. does anybody know what's going on?
thx

---

### Post by TidusBlade on 2007-12-26
Maybe try using the Syanptic manager to do so? If your lucky, it might work!

---

### Post by tisa on 2007-12-26
hi,
well, the synaptic also doesn't work, it doesn't find the packets
any idea?
thx

---

### Post by oldos2er on 2007-12-26
Check your software sources and make sure all repositories are enabled.

---

### Post by Don1500 on 2007-12-26
Let me know if you get it running, I've been trying for a week. (Once you get xgl loaded  before anything else fire up firefox and try some scrolling.)

---

