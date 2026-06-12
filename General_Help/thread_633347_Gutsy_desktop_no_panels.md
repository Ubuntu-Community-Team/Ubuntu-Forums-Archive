---
title: "Gutsy desktop no panels"
date: 2007-12-06
forum: General Help
---

### Post by frankzen on 2007-12-06
Running Gutsy. This morning when I booted through to the Gnome desktop, it had no panels, and no icons. When I click (right or left) onthe desktop NOTHING happens. Going to a console and running top shows me my dual cpu being dragged to its knees 100% usage. There seem to be several copies of various Gnome programs such as gnome-appearance running. What the H*ll is going on. Is Gutsy really this buggy?

---

### Post by ajgreeny on 2007-12-06
Sounds like your gnome configuration is all shot somehow, so try making a new user (in terminal if necessary) and then start up using that username and password to see if all is OK.  If it is, then it's gnome at fault, so rename the .gnome, .gnome2 and .gnome2_private folders in the original home folder, and try again.

---

### Post by frankzen on 2007-12-06
OK tried that, no happiness. Same problem. No panels, no icons and multiple copies of various things running and consuming 100% of a dual core cpu.
Maybe I'll just reinstall Dapper ( had no trouble with that).

Judging by the posts here Gutsy is the buggiest yet.

---

### Post by g2g591 on 2007-12-06
well, perhaps you could try installing kde-core (which will pull in a pretty bare kde envrionment, if you like what you see install kubuntu-desktop, which will pull in a bunch of additional stuff for kde) and see if kde works out (only ever used gnome in fiesty for about 2 weeks then tried and liked kde better)

---

### Post by -grubby on 2007-12-06
that's happened to me before.....well at least no right clicking...that was nautilus crashing. It also might be gnome-panel crashing too

---

### Post by frankzen on 2007-12-07
> **nathangrubb said:**
> that's happened to me before.....well at least no right clicking...that was nautilus crashing. It also might be gnome-panel crashing too



Forget it. FIXED!

Well in my case...the desktop eventually does load..after 2 or 3 minutes. Strange thing is it loads instantly IF I pick Gnome-Failsafe at the GDM menu. It also loads fine for another user on this machine.

---

