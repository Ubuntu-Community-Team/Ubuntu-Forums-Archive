---
title: "Composite Performance"
date: 2004-11-19
forum: General Help
---

### Post by mkools on 2004-11-19
Hello guys,

First of all, thanks for implementing X.org 6.8.1 into Ubuntu, great work!
Everything works great, except for one thing, composite.

I've updated my xorg.conf and added the following lines:

Section "Extensions"
        Option        "Composite"        "Enable"
EndSection

After that I installed the xcompmgr debian package posted earlier here.
After fixing some dependencie issues it installed without errors.

Xorg performance is ok, but when I start xcompmgr to get some nice
fading and shadow effects the system gets very slow.
Building up a Mozilla Firefox window takes about 2 seconds to fill up the screen.
(I do have my effects though).

I think the problem might be in GNome 2.8, since I didn't had this problem
with other distro's using KDE or Gnome 2.6 but i'm not sure

I'm using a custom 2.6.9 kernel with my DRI module enabled.

When I type: glxinfo | grep direct it says:
direct rendering: Yes

So I assume direct rendering works.

Any idea's where to look at?

Thanks in advance!

---

### Post by mr_ed on 2004-11-19
That's perfoming as expected.  The composite extension is reported to be extremely slow.  That's also why it's disabled by default.  :D

The first version of composit was just to get it to work, period.

---

