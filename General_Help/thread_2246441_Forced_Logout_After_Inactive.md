---
title: "Forced Logout After Inactive"
date: 2014-09-30
forum: General Help
---

### Post by dunn-stephen on 2014-09-30
Hi, I just upgraded to 14.04 LTS from 12.04, and I'm having an annoying issue: If I leave my computer inactive for ~20 minutes, I am forcefully logged out. I have disabled suspending in gnome-control-center and I have also disabled locking altogether. My xscreensaver also has this disabled. I am not using unity, I have openbox installed. My xsession-errors shows nothing unusual. Does anyone have advice for how I should investigate and resolve this?

---

### Post by Bucky Ball on 2014-09-30
Welcome. Do you have lightlocker installed?

---

### Post by dunn-stephen on 2014-10-01
No I don't, but I figured it out. The PacMan screensaver is incompatible with 14.04.1 for some reason and causes a crash whenever it randomly loads (per my xscreensaver prefs). Disabling it resolved the issue so far.

---

