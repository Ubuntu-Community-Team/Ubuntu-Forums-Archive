---
title: "[SOLVED] ubuntu boots and loads (all) programs very slowly"
date: 2008-06-10
forum: General Help
---

### Post by malachi1990 on 2008-06-10
I've noticed over the past week that my laptop has slowed down considerably in booting into hardy, and then any program I load.  It takes about 2 minutes for any one of them to load, and about 3-5 for the OS to load.

I have 3 GB of ram, and the laptop is fairly new.  The processor is AMD Turion dual core.

Many thanks for help.

btw, I've already tried killing trackerd, with no discernible affect.

---

### Post by sdennie on 2008-06-10
Can you start a terminal and post the output of the top command?  Also, is the hard drive light on constantly when this is happening?

---

### Post by malachi1990 on 2008-06-10
Top gave me Xorg most of the time, with about 8-9% of cpu dedicated to it.  A couple of other things came up, but only for a couple seconds.

No, the light stays off, except for the occasional blink.

---

### Post by malachi1990 on 2008-06-11
Apparently, the problem is with GNOME or X-Windows systems, as when I chose GNOME as my session, everything sped up a bit.  Not back to orignal speed, but getting there.

---

