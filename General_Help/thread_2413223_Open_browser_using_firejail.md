---
title: "Open browser using firejail"
date: 2019-02-22
forum: General Help
---

### Post by crockett98 on 2019-02-22
I am trying to get Brave web browser to open using firejail but without using firetools. 

I'm new to Ubuntu and have come from Mint. It was pretty straight forward in Mint but I'm tripping up somewhere with Ubuntu. 

So far i've opened the .desktop file
> sudo gedit /usr/share/applications/brave-browser.desktop

The command I am changing is "/usr/bin/brave-browser %U"  

I've (naively!) added "firejail" in front of this but it isn't working. 

I checked in Terminal and "firejail brave-browser" gives...
```
Reading profile /etc/firejail/default.profile
Reading profile /etc/firejail/disable-common.inc
Reading profile /etc/firejail/disable-passwdmgr.inc
Reading profile /etc/firejail/disable-programs.inc


** Note: you can use --noprofile to disable default.profile **


Parent pid 10739, child pid 10740
Warning: cleaning all supplementary groups
Child process initialized in 67.86 ms


Parent is shutting down, bye...



``` 

If I change the command to "firejail --noprofile /usr/bin/brave-browser" (in the .desktop file) Brave starts up and works OK but I have no idea what "--noprofile" is doing.

Please can someone help me out?! Is it OK/safe to use --noprofile?

Thank you

---

### Post by crockett98 on 2019-02-22
Sorry!

Solved

I removed the "%U"

Took me 35mins to work that out!

---

