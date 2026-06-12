---
title: "Inconsistent Gnome 3.28 packaging - why?"
date: 2018-05-02
forum: General Help
---

### Post by Drone4four on 2018-05-02
Some components in my Gnome packages by default in my recent 18.04 upgrade are 3.26 while others are 3.28. I understand that Nautilus 3.26 was deliberately packaged to allow for icons to still show on the desktop. [A report on OMG Ubuntu explains the issue]("https://www.omgubuntu.co.uk/2018/01/ubuntu-18-04-lts-will-ship-older-version-nautilus"):

> Finally, this decision only affects the file manager. The rest of Ubuntu 18.04 LTS is expected to use the latest, greatest GNOME 3.28.

 But I noticed that the gnome-system-monitor application is still 3.26. Was this a mistake or deliberate as well?  Another minor quirk I noticed is that my gnome-calculator is 3.28 but is still unaffected by my materia GTK3 theme.  

[Here]("https://imgur.com/a/Gj0g0Ms") is an image on imgur of my desktop showing my system monitor at version 3.26 and my calculator showing 3.28 but with inconsistent GTK themes.  

These are just minor quirks which I can live with. Just wondering if someone could make sense or clarify as to why?

Thanks for your attention.

---

### Post by kerry_s on 2018-05-02
cause sometimes they need to be the same version to work. others are not as tied in & can be upgraded.

---

### Post by Dennis N on 2018-05-02
> Another minor quirk I noticed is that my gnome-calculator is 3.28 but is still unaffected by my materia GTK3 theme.

Gnome Calculator is one of the snap packages that are installed by default. I noticed that they do not use the application theme you select in tweak tool. I removed it and then installed the regular non-snap package with Synaptic Package manager. The regular version does use the selected theme.

There are 5 default snap applications - I think all have this problem.

> an image on imgur of my desktop showing my system monitor at version 3.26 and my calculator showing 3.28 but with inconsistent GTK themes.

Gnome System Monitor in 18.04 is another snap package and version 3.26. If you instead installed the one that is available with apt it is 3.28 and it will conform to the selected theme. I haven't seen any reason not to use the package installable with apt. It's been working fine on my system.

---

