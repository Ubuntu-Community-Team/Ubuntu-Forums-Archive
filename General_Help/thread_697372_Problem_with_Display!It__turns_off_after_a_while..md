---
title: "Problem with Display!It  turns off after a while."
date: 2008-02-15
forum: General Help
---

### Post by gerod on 2008-02-15
Hi.
I'm trying to do a kiosk application with Dapper. The aim is to make a PC boot and connect automatically to a WinXP machine with VNC.
I did everything creating a new user, editing the .xinitrc adding xvncviewer command and gdm.conf-custom for autologin.
Everything works great, but after about 10 minutes the display turns off even if i disabled all i could (acpi, apm, DPMS, screensaver, power-manager). The problem doesn't appear loading vncviewer after gnome.
Any idea? :confused:  I'd like to avoid running gnome, cause it's easy to edit .xinitrc and run vncviewer just after X.
Thank u.

---

### Post by Toky on 2008-02-20
I'm in the same boat, I need to keep the monitor ON all the time since its going to display live stats constantly.

I've also done some tweaking on the conf files, i'm actually waiting right now for the 10minutes to see of my changes make it work... i'll let you know in about 4 mins....

---

### Post by gerod on 2008-02-21
I solved by adding to /etc/X11/xorg.conf in the "ServerLayout" section the following lines

        Option          "BlankTime"     "4"
        Option          "StandbyTime"   "0"
        Option          "SuspendTime"   "0"
        Option          "OffTime"       "5"

---

### Post by gerod on 2008-02-21
Ops. the parameters are all 0 of course

        Option          "BlankTime"     "0"
        Option          "StandbyTime"   "0"
        Option          "SuspendTime"   "0"
        Option          "OffTime"       "0"

---

