---
title: "[SOLVED] Bin ICON gone"
date: 2008-06-12
forum: General Help
---

### Post by brett123 on 2008-06-12
UBUNTU - not kubuntu, sorry, must have clicked the wrong option....


Have standard latest Ubuntu install, with standard Gnome... The bin icon was always in the bottom panel, to the extreme right of the desktop switching icons.

Now it is gone, or rather the icon is gone. There is a small space a couple of pixels wide that still functions as the bin, but you have to know it is there to click on it.

If I add to panel again, it just adds these same few-pixel-wide invisible blank icons.

Any ideas? I don't think I did anything. :/

---

### Post by brett123 on 2008-06-13
[https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/211604](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/211604)

Specifically:

> Edit: /usr/lib/bonobo/servers/GNOME_Panel_TrashApplet.server

Add this inside the <oaf_server location="/usr/lib/bla/trashapplet"> element
(NOT the one with the location="OAFIID:bla")

    <oaf_attribute name="bonobo:environment" type="stringv">
        <item value="DBUS_SESSION_BUS_ADDRESS"/>
    </oaf_attribute>


Did that, rebooted, and all back to normal.

---

