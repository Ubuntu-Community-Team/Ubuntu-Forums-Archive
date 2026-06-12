---
title: "SOLVED! 17.10  - Gnome extensions: AppIndicators and Window List"
date: 2017-10-20
forum: General Help
---

### Post by Kris_M on 2017-10-20
[COLOR=#000000]A couple Gnome extensions show "error" and don't work.:[/COLOR]
[COLOR=#000000]Ubuntu AppIndicators (app indicators in top panel)[/COLOR]
[COLOR=#000000]Window List (bar at bottom of screen)

Thanks.[/COLOR]

---

### Post by JonPaul on 2017-10-20
Some of them dont work in ubuntu-session but do in gnome-session...

---

### Post by Kris_M on 2017-10-20
Oh DUH!!! - Thanks!!!  I had indeed logged on as ubuntu on xorg instead of Gnome on xorg. Thanks!!!

---

### Post by ilya-prihlop on 2017-10-21
> **Kris_M said:**
> Oh DUH!!! - Thanks!!!  I had indeed logged on as ubuntu on xorg instead of Gnome on xorg. Thanks!!!

You solved this issue?
Please write how you did it.

---

### Post by Kris_M on 2017-10-21
as I said in my reply - when you start ubuntu and get to the logon, click on the little icon and choose whatever you want - The correct choice for me, since Nvidia, is Gnome on xorg.
This fixed the window list.(yay)  However AppIndicators does not seem to work, but at least doesn't show an error. I think there is a later version but it hasen't trickled down yet?

---

### Post by ilya-prihlop on 2017-10-21
Hm... It work for me too, errors not shown but indicators not shown too.

---

### Post by Kris_M on 2017-10-21
I tried with topicon and I can get them to show up like every other boot, if I change the extension on or off. No consistancy.

---

### Post by Kris_M on 2017-10-21
indicators are supposed to have been moved to the top in gnome 3.26 and indeed they are there if I turn "system-monitor" off in tweak extensions.

---

### Post by Kris_M on 2017-10-21
fix

I had uninstalled kstatusnotifieritem hoping that would help(I had it from 17.04)(had Software uninstall it). It didn't help.

Now I read that it is intentionally packaged with 17.10 Gnome.
[http://www.omgubuntu.co.uk/2017/08/ubuntu-sees-sense-will-support-indicator-applets-ubuntu-17-10](http://www.omgubuntu.co.uk/2017/08/ubuntu-sees-sense-will-support-indicator-applets-ubuntu-17-10)
So I just put it back on with the extension link from the above link.
So it has been uninstalled and installed since upgrade from 17.04 . I think this is important.

Now I can dependably boot and have both system monitor and status icons appear on the desktop top bar.
Interestingly software doesn't think it is installed.

What is _**off**_ in tweak extensions is very important.

---

