---
title: "Virtual Terminal unfix"
date: 2008-02-18
forum: General Help
---

### Post by caleb_yau on 2008-02-18
I was having some trouble with my virtual terminal so I read the fix in the known gutsy bugs to try to and fix it myself. This is the advice I followed

> 
Code:

```
sudo modprobe vga16fb
sudo modprobe fbcon
```

Checking... After that commands I can use Ctrl+Alt+Fx to open a virtual terminals again...
I just added this lines :
Code:

```
vga16fb
fbcon
```

into /etc/modules
and Ctrl+Alt+Fx works for me after reboots, too.



Unfortunately my virtual terminal has gone from slightly malfunctioning to displaying the craziest colors and then constantly moving towards a pure white. Its actually quite scary looking at it. Needless to say i got rid of the etc/modules text but i cant figure out a way to get rid of the original modprobe mods. I've tried these commands:

```
sudo rmmod vga16 
sudo rmmod fbco
```

but I only get back these errors:

ERROR: Module vga16 does not exist in /proc/modules
ERROR: Module fbcon is in use

I will be happy to get it back to its formal disfunctional self but i can't even do that. Any help would be greatly appreciated!

oh yeah I am running Gutsy Gibbon Xubuntu and have a ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] 
graphics card

---

### Post by caleb_yau on 2008-02-18
bump

---

### Post by caleb_yau on 2008-02-19
bump

---

### Post by NullHead on 2008-02-28
Well your solution fixed my problem with a nvidia card ... it seems to work just fine.

---

