---
title: "Ubuntu 8.04 Slow Menus on x64"
date: 2008-06-19
forum: General Help
---

### Post by masterpop on 2008-06-19
Hi,
I'm running ubuntu 8.04, gnome desktop with no funky effects. I'm finding that menu drawing when you click Applications/Places/System seems to slow down after awhile.. it literally takes 1-2 seconds to load. This issue is also evident when maximising windows.

Could someone point me in the right direction to debug this issue.

I have a GeForce 8600 GTS graphics card, on a quad-core 2.4Mhz with 8GB of RAM. Not a slow machine by any stretch of the imagination.

I am running Twinview with the other screen being a 40" Sony TV.. but that works fine...Interestingly enough there doesn't appear to be any delay on the Sony TV.. so perhaps something goes wrong with the X-server?

Any idea, tips would be greatly appreciated.

---

### Post by nikgare on 2008-06-20
Do you have the restricted drivers for nvidea installed?
You can check here:

System->Adminstation->Hardware Drivers

---

### Post by masterpop on 2008-06-20
Hi, yes I do have restricted drivers installed. From memory i belive they are version 169.12.

---

### Post by nikgare on 2008-06-20
This sounds like the sort of thing that happens when memory is tight and your system has to swap loads of stuff out - I used to have a similar experience when I had 256Mb.
But you have 8GB - that should be more than enough ;-)
Is the whole amount being recognised by the bios and the OS?
Other than that I have absoltely no idead what could be going on- apart from the nvidea driver not being correctly installed.
Do you get the nvidea splash logo when GDM kicks in?

---

### Post by masterpop on 2008-06-20
Hi,

Thank you for taking the time to help.

I went into the BIOS, but couldn't see where it read how much ram I have. However, under System Monitor it can see 7.8Mib.
The nvidia logo shows up as expected.

I am running compiz (spinning cube): all smooth and very fast..

Quite frustrating really... the more I hover over the menu's the more systematic it seems.. like there's a deliberate 2sec lag... again, similar for maximising windows.

I'll continue searching.... i cannot believe it can be that slow...

---

### Post by nikgare on 2008-06-20
Does this happen for all users, or just your account?

---

### Post by masterpop on 2008-06-21
Hi,

This happens for all users (i created a new one to test it out). However, not sure if it's related, but I have dual-output to a 40" Sony TV which runs as a separate X-screen. The menu on this screen are fine- split second to draw and flicking between menus is also fine.

I attach my xorg.conf file. It feels like something with the drivers... because when using nv or VESA with the same monitor configuration doesn't exhibit the same problem.

However, with nv or VESA i can't get decent full TV screen playback of movies..

What do you think?

---

### Post by masterpop on 2008-06-23
for anyone else having the same issue, i found this thread on nvnews:
[http://www.nvnews.net/vbulletin/showthread.php?t=114239](http://www.nvnews.net/vbulletin/showthread.php?t=114239)

at present there doesn't appear to be a solution for the problem.

---

### Post by nikgare on 2008-06-23
Could you fle a bug on launchpad if there isn't already one there?

---

### Post by RESID3NT on 2008-06-25
> **nikgare said:**
> Does this happen for all users, or just your account?

I have the same issue

---

### Post by masterpop on 2008-06-25
Hi, I have posted the bug on launchpad: [https://bugs.launchpad.net/ubuntu/+bug/242735](https://bugs.launchpad.net/ubuntu/+bug/242735)

If you think you have additional information which could help the developers please post a follow up on that thread.

Hopefully, it will be resolved at some point.

---

