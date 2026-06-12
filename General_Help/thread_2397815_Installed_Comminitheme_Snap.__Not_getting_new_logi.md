---
title: "Installed Comminitheme Snap.  Not getting new login screen."
date: 2018-08-03
forum: General Help
---

### Post by Hewjr100 on 2018-08-03
That about sums it up.

Gort

---

### Post by Holger_Gehrke on 2018-08-03
A snap -- which is confined by an AppArmour profile -- should never be able to change the login screen. If you want to change the login-screen, you need to change the appearance of the greeter that gets started by your display manager. On XUbuntu there's a tool in the settings menu to do that It's called 'LightDM GTK+ Appearance Settings'. To start it directly from the command line, you'd use 'lightdm-gtk-greeter-settings-pkexec'. I'm rather certain that there's something similar available on whichever flavour of Ubuntu you're using.

Holger

---

### Post by PaulW2U on 2018-08-03
From what I've read elsewhere there are undocumented and unsupported ways to get the new log-in and lock screens in Ubuntu 18.04 so I'm not going to point anyone towards them. :)

Ubuntu 18.10 will be the first release for which Communitheme, now renamed Yaru, will be the default theme and will include new log-in and lock screens. It's still unfinished and there are continuing discussions about some of the theme's features. Ubuntu 18.04 users have been given a **preview** of the theme through use of the Communitheme snap so that they can give feedback to the developers. Using snaps allows updates to be pushed to users very quickly, important in a rapidly changing development environment and something that is not possible using the Ubuntu archive or a PPA.

The theme will be provided to Ubuntu 18.10 users in conventional deb packages and presumably any customisation will be done through Settings or Tweaks.

---

### Post by Hewjr100 on 2018-08-03
Well I guess I’ll wait for Ubuntu 18.10

Gort.

---

