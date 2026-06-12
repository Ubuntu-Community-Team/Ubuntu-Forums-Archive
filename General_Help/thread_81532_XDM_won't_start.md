---
title: "XDM won't start"
date: 2005-10-24
forum: General Help
---

### Post by ToneDispenser on 2005-10-24
Hi everyone,

I installed Ubuntu/PPC on my old G3 Wallstreet Powerbook and I had no problems so far. I did the "standard" installation procedure (did not do a "server" install) and everything worked.

Now I want to switch from GDM to XDM, because my powerbook is old an slow...

I used synaptic to install the XDM package. But XDM won't startup.
The last line before the login prompt says "Starting X display manager: xdm".
But it won't start.

When I login and type 'startx' my Powerbook starts GNOME (not the gdm).

/etx/X11/default-display-manager says:
/usr/bin/X11/xdm

I ran "dpkg --configure xdm" and "dpkg-reconfigure xdm" but it's still not working.

I also can't find any trace of a XDM log file...

Does that mean my xserver doesn't start?
Any config files I should post?

Thanx for your future tips/hints/help.. :)

---

