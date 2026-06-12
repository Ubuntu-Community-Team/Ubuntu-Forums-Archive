---
title: "Fan keeps spinning after wake up from hibernate"
date: 2005-10-17
forum: General Help
---

### Post by msturm10 on 2005-10-17
On my NEC Versa P520 laptop the hibernate functionality works as expected in Breeze Badger (while it didn't on Hoary, so this is a big improvement imho). But after I turn the system on when it was hibernated, the fan of my laptop keeps spinning (while normally it is almost always off, and only spins when I'm doing some processing intensive work). This is quite annoying, because the fan is pretty noisy. Is there a (known) way to fix this problem? This minor 'bug' keeps me from using the hibernate feature, because I know have to reboot my computer in order to get the fan working properly.

Unfortunately it seems that suspend to ram doesn't work on my laptop. When waking up my computer, the screen doesn't work anymore. Is there a possible fix for this problem?

The specs of my laptop: Centrino 1st gen. with Pentium M 1,4GHz (Banias core).

---

### Post by noof on 2005-10-17
I have the same suspend to ram problem as you. It kinda turns on but the lcd doesn't. I've only tried 3 times and at one of them it actually started again, after like 1 min. To turn the fan off you can type:
echo -n 3 > /proc/acpi/fan/FAN/state
in a root terminal. Dunno if it'll turn on when the computer gets hot though.

---

### Post by msturm10 on 2005-10-17
[QUOTE=noof]I have the same suspend to ram problem as you. It kinda turns on but the lcd doesn't. I've only tried 3 times and at one of them it actually started again, after like 1 min. To turn the fan off you can type:
echo -n 3 > /proc/acpi/fan/FAN/state
in a root terminal. Dunno if it'll turn on when the computer gets hot though.[/QUOTE]
Hm.. I'll try your tip for the fan problem. However, it would be nice when the fan cool the computer when it gets hot... If that works, it is possible to add that line to one of the acpi scripts.

---

### Post by msturm10 on 2005-10-18
Well, this solution seems to work (and is very trivial, so I should have found it myself). I'm not sure if the fan turns on when it gets to warm, but according to the Suse Linux adminguide, this should work:

> /proc/acpi/fan/FAN/state
Shows if the fan is currently active. Activate or deactivate the fan manually by writing 0 (on) or 3 (off) into this file. However, both the ACPI code in the kernel and the hardware (or the BIOS) overwrite this setting when it gets too warm.

I don't know how to verify this statement.
Now, I only have to figure out how I get this fixed automatically on resume.

---

