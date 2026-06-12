---
title: "Unity Desktop Problem--Ubuntu 13.04"
date: 2013-05-07
forum: General Help
---

### Post by kc8hr on 2013-05-07
Logging in to the default Unity Desktop gives me a pretty desktop with wallpaper, but no toobars and no launchers.<alt F2> does not function.  Nothing!

My system is a rather elderly Dell Optiplex with onboard Intel video, and lspci provides the following information:

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

---

### Post by dino99 on 2013-05-07
the main issue is named "compiz" (looks like more & more an 'abondonware')
into a terminal, run these 2 commands , one by one:
compiz --replace ccp &
setsid unity

but you can also choose to login gnome-shell : same look as unity (with less headhaches) (prefer installing the 3.8 from gnome3-team ppa)

---

### Post by kc8hr on 2013-05-08
Thanks for the tips dino99, but I give up. Compz just does not work with the standard Intel I915 onboard video. I use Fluxbox as my usual desktop--no errors, no crashes. I fiddled around with Unity for fun, but it is just a pain in the butt.

Ubuntu developers: Give up on the Unity Desktop, go back to either Gnome or KDE Plasma!

---

