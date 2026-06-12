---
title: "Compiz Uses Too Much CPU"
date: 2008-06-09
forum: General Help
---

### Post by Locutus_of_Borg on 2008-06-09
Normally I idle at about 1-4% CPU usage.

If I turn on compiz it jumps to about 30% and everything starts to lag.

I've used compiz a lot in the past and usually there is no lag and no jump in CPU usage.

At the moment I am dual booting Gentoo and Slackware.  

In Gentoo with compiz and nearly all the effects turned on, I idle at about 2% CPU usage, and compiz takes up 20mb of ram. X takes up 0% CPU and 0 ram (according to gnome-system-monitor)

Now on Slackware using compiz, I idle at 30% and 10 mb of ram for compiz, but 60 mb of ram for X.  If I turn off compiz, CPU drops to about 5% but X still takes up about 50 mb of ram.

xorg.conf is the same on both. compiz is from git on slack, and using live ebuilds through layman on gentoo, so both are essentially the latest versions.  both running xfce. i have intel 945gm graphics, and i810 driver.  i915 module is loaded on both.

What might be causing slackware's compiz to eat up so much CPU?

Thanks.

---

