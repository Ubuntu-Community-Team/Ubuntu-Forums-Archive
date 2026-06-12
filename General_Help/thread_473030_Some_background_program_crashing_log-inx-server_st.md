---
title: "Some background program crashing log-in/x-server start-up"
date: 2007-06-13
forum: General Help
---

### Post by stickx911 on 2007-06-13
After a recent stream of upgrades from the upgrade manager (not sure what there was, I don't usually look) my boot process is totally hosed.

if I restart the X server (by log-out or ctrl-alt-backspace) and log in, the Ubuntu splash stays up ontop of my desktop for a few minutes and something between my sound manager and anything else starting, locks up because it takes a minute or so for network manager  (gdesklets and others, if those don't also crash) to load. 

On a regular reboot it still takes a while for everything to load, but the splash does not stay up as long.

**things I've done recently that may have done this:**
-Updates from update manager

-I recently installed the mac gnome-panel hack (where the "File Edit View ..." can be put on the panel) but that has worked without a hitch for about a week. 

-I installed some games from add/remove that are kde based games.

**Things I've tried:**
-I first thought it was beryl/emerald because those are common culprits, however, I disabled both and no luck. 

-I disabled _everything_ in Sessions>Start-up and still...no luck. (shouldn't metacity load by default if no other manager is present?)
-------------------
Any ideas?

is there a way for me to see what is loading in the background to see what is crashing or just taking forever to load? And if there is something causing problems how can I disable it, or repair it, if it is not in the sessions>start-up menu?

Do you need anything else to make diagnosis easier?

---

### Post by stickx911 on 2007-06-13
I am using an HP DV2000

Intel everything. :)
Intel gfx, ipw3945, core solo cpu, intel chipset.

anything that says update I always update (usually without as much as glancing at the list), so maybe I updated something while it was still running?

---

### Post by stickx911 on 2007-06-14
anybody even have a guess?
:(

---

### Post by stickx911 on 2007-06-16
I'll try later then I guess....

---

