---
title: "gnome-system-monitor is a snap &amp; still doesn't work in 18.04.1"
date: 2018-08-04
forum: General Help
---

### Post by lostmoonofsaturn on 2018-08-04
Gnome-System-Monitor is installed as a Snap in 18.04. Ditto gnome-calculator.

Neither snap has ever worked for me. They do not launch.  So, I remove them and install the normal packages.

Why ship broken packages?  Even in the first point release.

---

### Post by PaulW2U on 2018-08-04
> **lostmoonofsaturn said:**
> Why ship broken packages?  Even in the first point release.
Did you install 18.04.1 afresh or upgrade from a previous version?

I think bug [#1772844]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1772844") might be relevant here.

I'm still seeing snap issues when installing or trialling the development release (18.10) even though the bug report implies that various issues have been fixed. :confused:

---

### Post by lostmoonofsaturn on 2018-08-04
Fresh install. It was there in 18.04, as well.

---

### Post by PaulW2U on 2018-08-05
Do you have other snaps that don't start? What's the output of
```
snap list
```
I think you should have a list of seven unless you've installed any yourself.

I see that a new bug report has been created since I last posted: [Can not open Gnome snaps as they are not connected to «gnome platform snap»]("https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1785410"). Seems to be more relevant than the one I linked to earlier which is now shown as "Fix Released" in 18.04.

---

