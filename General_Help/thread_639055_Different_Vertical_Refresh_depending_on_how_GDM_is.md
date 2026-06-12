---
title: "Different Vertical Refresh depending on how GDM is invoked?"
date: 2007-12-12
forum: General Help
---

### Post by kellyplace on 2007-12-12
I have a strange problem where when I start GDM with the "automatic login",
I get GDM/Gnome coming up at 72Hz Vert. refresh at 1600x1200 res.  This 
is to high for my SyncMaster 204B which wants 60Hz max. at that res.   The 
width of the 1600 res. puts items off each side of the screen.

Here's the strange one, I have modified xorg.conf with settings which should
work and hold the monitor to 60Hz.   When I boot to root and invoke GDM via 
shell command I do indeed get 60Hz for the monitor in this case and all is fine.

What does the "automatic login" do differently than command line invoking
of GDM that I haven't discovered yet?  I know that the "gdmgreeter" probably
has run and is what transitions from login prompt to a running Gnome desktop

I am running "915resolution" for my system as recommended and I can get
the correct settings only on manual GDM startup.

Anybody got a clue?

Cheers,
Marc

---

