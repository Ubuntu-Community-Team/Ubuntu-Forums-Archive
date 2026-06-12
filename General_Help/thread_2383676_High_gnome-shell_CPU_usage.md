---
title: "High gnome-shell CPU usage"
date: 2018-01-28
forum: General Help
---

### Post by neltnerb on 2018-01-28
Since upgrading to 17.10, gnome-shell is frequently taking 10-60% of my CPU with very little activity. It will settle down to 1% or so and then even just moving my mouse causes it to jump to 10%+.

Does anyone have a methodology for finding the issue? I assume gnome-shell is a general renderer or something so I'm not sure how to figure out what is actually telling it to work so hard. I have no gnome extensions enabled and glxinfo | grep -i render reports that direct rendering is enabled. It's a core i5 haswell with iris 6100 graphics, so it's not high end but hardly should have trouble idling.

How can I figure out what actual issue is making it work so much?

---

