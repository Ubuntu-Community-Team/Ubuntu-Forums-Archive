---
title: "continuously asked to log in"
date: 2007-07-15
forum: General Help
---

### Post by bdavies on 2007-07-15
i basically just go ubuntu to work early today and everything seemed to be fine until i tried to change the splash and login screens(i was also trying to change the picture on the cube caps). when i restarted my computer, after i logged in the desktop came up and then it just went back to the login screen. if i try to login in again i get a long error and my desktop is all blurry. when i click ok on the error it just goes back to the login screen. has this happened to anyone before? any suggestions? i am new to ubuntu and linux so the more detail the better

---

### Post by aysiu on 2007-07-16
Maybe change login screen back to the default and disable the splash screen?

Press Control-Alt-F1.

Log in.

Type ```
cd /etc/gdm
sudo mv gdm.conf-custom gdm.conf-custom.old
sudo cp gdm.conf gdm.conf-custom
cd
gconftool-2 --set "/apps/gnome-session/options/show_splash_screen" --type bool "false"
sudo /etc/init.d/gdm restart
``` Here's a translation of what the commands do: ```
Go to the /etc/gdm directory.
Rename my GDM configuration file so that it won't be used.
Take the default GDM configuration file and make that the one that gets used.
Change to my home directory.
Turn off the use of the splash screen.
Restart the login screen manager.
```

---

