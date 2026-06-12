---
title: "Can't remove wireframe animations after xgl/compiz"
date: 2006-09-13
forum: General Help
---

### Post by chipsdeluxe on 2006-09-13
I'm having trouble removing the wireframe animations that occur when launching an application from the panel. I've gone into gconf-editor and unchecked the '/apps/panel/global/enable-animations' key and the '/desktop/gnome/interface/enable-animations' key. 

Is there any other way to remove the animations?

Thanks!

---

### Post by pravuil on 2006-09-13
Oooh, I really hate that. I would like to know how to get rid of that stuff too. I get kind of blindsided when I'm running apps through wine all the time. It's weird, it works fine on every other distro. That's the only reason I don't use Compiz on Ubuntu. :evil:

---

### Post by chipsdeluxe on 2006-09-14
I've tried starting up with a standard gnome session (no xgl) and making the changes in gconf-editor there, but still no luck. Anyone else have any luck?

*edit*

After the updates today, the enable_animations check box was automatically reselected. After unchecking it again, the wireframe animations are gone. Problem solved!

---

