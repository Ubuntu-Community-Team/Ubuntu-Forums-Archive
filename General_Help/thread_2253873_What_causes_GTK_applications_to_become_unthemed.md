---
title: "What causes GTK applications to become unthemed?"
date: 2014-11-23
forum: General Help
---

### Post by CaptainMark on 2014-11-23
I'm currently between distros and haven't settled on a specific one, currently testing out Ubuntu Mate 14.10, I'm trying to figure out what makes GTK themes display so erratically between theoretically similar distros, I'm trying to use the Popular theme Mediterranean Night [http://gnome-look.org/content/show.php/MediterraneanNight+Series?content=156782](http://gnome-look.org/content/show.php/MediterraneanNight+Series?content=156782) and whilst it worked fine on vanilla ubuntu 14.04 and 14.10 and Linux Mint 17 displayed it fine, Ubuntu Mate displays some windows without a theme (see included screenshot of synaptic)

Please try not to dismiss this as "Ubuntu Mate is not an official flavour so I'm not helping you" because sometimes it's the other way around and a theme that works fine on say xfce will not show correctly on Ubuntu proper.

My question is more of a general one of, what would cause a GTK theme not to display correctly and how can I begin to discover the cause and fix it?
At the moment I find myself giving up on a distro that I otherwise like because I don't like the default theme and my preffered theme wont display correctly.

Thanks for any help.
Regards
Mark

---

### Post by vasa1 on 2014-11-23
Do you see the problem with applications that don't need to be run with elevated privileges?

---

### Post by buzzingrobot on 2014-11-23
Themes are often sensitive to the GTK2 or GTK3 version in use, especially the latter. 14.10, I believe, uses GTK3 3.12.  Themes requiring a later version, or hardwired to an earlier version, may have problems.

Mate in its current release is GTK2-based.  Themes intended for Mate need to include versions covering both GTK2 and GTK3 apps. If an older GTK2 theme that does not include theming for GTK3 apps is used on Mate, Mate itself will likely look fine, but individual GTK3 apps will not.

Guidance on the web often recommends installing themes in ~/.local/share/themes or ~/.themes.  I've found this often cause themes to malfunction, and always install them in /usr/share/themes.

---

### Post by vasa1 on 2014-11-23
Synaptic v 0.81 on my system, Lubuntu 14.04, is a gtk3 app.

BTW, I've never had themes malfunction in ~/.themes. I prefer them there rather than in /usr/share/themes because I tweak my themes a lot and don't like to sudo/gksudo for such things.

---

### Post by vasa1 on 2014-11-23
One more thing ... look at the contents of /etc/gtk-3.0/settings.ini. Make sure the theme it points to exists on your system.

---

