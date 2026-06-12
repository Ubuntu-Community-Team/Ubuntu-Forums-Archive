---
title: "software cannot be installed"
date: 2013-03-14
forum: General Help
---

### Post by DrScum on 2013-03-14
When I start synaptic package manager I get the following Error Message Box:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

If I do as suggested i.e. run in a terminal sudo dpkg --configure -a the system starts to uninstall a package and ultimately hangs itsself with a black screen and a lot of white gibberish (to me it's gibberish anyway).

How do I diagnose and fix this?

---

### Post by ManamiVixen on 2013-03-14
What package is it?

---

### Post by DrScum on 2013-03-14
module bcmwl seems to be the culprit

from the terminal I gather that an old module is removed and a new one is being built. The building process finishes ok and during sanity check the system crashes.

It crashed now, I had to hit the power button to switch of and now there is no rebooting possible.

---

### Post by oldos2er on 2013-03-14
If you can copy and paste the "gibberish" here it would help.

---

### Post by DrScum on 2013-03-15
that's kind of hard since the machine is dead when the "gibberish" appears on screen. On top of that I can't boot anymore as described in thread # 2125674. For now the problem posted here is obsolete unless I can solve the problem described in post # 2125674. Whether or not the two are connected I can't say. In any case at the moment I am desperate for help to get the system to boot. I am afraid I have to install from scratch.

---

