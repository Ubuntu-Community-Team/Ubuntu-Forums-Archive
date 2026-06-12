---
title: "Help! No Ubuntu Desktop option in Tasksel"
date: 2022-10-23
forum: General Help
---

### Post by nosyarutnubu on 2022-10-23
Hi all, installed Ubuntu Server 22.04 last week. Now I install tasksel and about to install an ubuntu desktop UI but there is no option of it there. The only options were the ff:

-Debian desktop environment
-GNOME
-Xfce
-GNOME Flashback
-KDE Plasma
-Cinnamon
-MATE
-LXDE
-LXQT
-web server
-SSH server
-laptop

Thanks!

---

### Post by TheFu on 2022-10-24
I'm seeing all the desktops as metapackages in 22.04.  Did you run 'apt update' today?

If you need a desktop, it is best to install the desktop ISO you want.  All the normal server stuff is available, but will keep using the desktop methods to configure networking, bluetooth, wifi and all that desktop junk that we never want on a real server.

---

### Post by nosyarutnubu on 2022-10-25
Thank you for the reply man. I ended up installing the Gnome desktop, and there is so many unnecessary things there. Maybe I'll just stick to the LXDE. Appreciate it!

---

### Post by TheFu on 2022-10-25
> **nosyarutnubu said:**
> Thank you for the reply man. I ended up installing the Gnome desktop, and there is so many unnecessary things there. Maybe I'll just stick to the LXDE. Appreciate it!

Actually, you don't need any DE at all. If you load just a WM, Window Manager, you get a GUI that is light.  openbox, icebox, fvwm, suckless, there must be 20 others.  Just depends on how light you want to go.

I use fvwm, but I've been using it off and on for 25 yrs.  Started with LXDE around 2010, found that to be too heavy and dropped back to using openbox, which LXDE sat over, but wanted more control.  Fvwm has extensions and can be customized in nearly anyway I can imagine ... but it uses text config files, which will turn off many people.

We are all a little different. Bloat and "Cheese" for one person is a bare minimum for others, which is fine.

---

