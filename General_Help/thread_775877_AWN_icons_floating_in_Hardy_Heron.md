---
title: "AWN icons floating in Hardy Heron"
date: 2008-04-30
forum: General Help
---

### Post by tijmz on 2008-04-30
Hi all,

I recently upgraded to Hardy Heron, from Gutsy 7.10. On my previous installation, I used Avant Windows Navigator (AWN), but right now it won't work properly.

I already deinstalled/reinstalled the version available from Add/Remove programs and did the same with avant-window-navigator-trunk via Synaptic. I also updated my ATI driver using EnvyNG (this because Compiz was acting slow on me, which was fixed by the update).

The problem is best shown by a screenshot. What happens is that AWN loads properly, but once I use an icon one or two times, the icon list starts floating.

[IMG]http://hangmat.etv.cx/stout/awn.png[/IMG]

Does anyone have any idea what could be causing this, or how to fix it?

---

### Post by moonbeam on 2008-04-30
There's a potential fix listed in the following bug that has worked for at least one person.

[https://bugs.launchpad.net/awn/+bug/222300](https://bugs.launchpad.net/awn/+bug/222300)

After doing the recursive unset you will need to reconfigure awn.

---

### Post by tijmz on 2008-04-30
Thanks for the quick and useful reply! It works perfectly now.

---

