---
title: "Gnome Tweak Tool doesn't recognize .themes folder"
date: 2017-06-22
forum: General Help
---

### Post by damnporthos on 2017-06-22
I'm trying to change my Gnome Shell theme. In order to do that, I've downloaded a theme ([https://www.opendesktop.org/s/Gnome/p/1013030/](https://www.opendesktop.org/s/Gnome/p/1013030/)), created a *.themes* folder inside *home* and extracted my theme there.
Despite this, Tweak Tool doesn't seems to recognize my *.themes* folder, using an Icon to mark it. When I click this button/Icon, a window - setted on *home* - opens, letting me free to select whatever folder I want; unfortunately, there's no way to set a folder default this way. 

Any tips?

Prints: [http://imgur.com/a/GSnv0](http://imgur.com/a/GSnv0)

---

### Post by again? on 2017-06-22
The "User themes" extension has to be enabled in tweak tool and you need to go into the 
**Flat-Remix-GNOME-theme-master** folder and put the **Flat Remix** folder into ~/.themes.

---

### Post by damnporthos on 2017-06-22
@guber2, thank you very much.

The *User theme* was already enabled, but I thought i should put the entire **Flat-Remix-GNOME-theme-master** onto .themes, not just the **Flat Remix**.

Now it's working perfectly. All thanks to you. Seriously, I'm glad.

---

### Post by again? on 2017-06-22
> **damnporthos said:**
> @guber2, thank you very much.

The *User theme* was already enabled, but I thought i should put the entire **Flat-Remix-GNOME-theme-master** onto .themes, not just the **Flat Remix**.

Now it's working perfectly. All thanks to you. Seriously, I'm glad.
No problem.
Even the auto install from your link installs the entire **Flat-Remix-GNOME-theme-master** folder.
A theme folder will use the theme name and the next level down will contain folders such as gnome-shell, gtk-2.0, gtk-3.0 etc for different environments/applications.

---

