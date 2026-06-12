---
title: "Disable Gnome Right-click?"
date: 2007-08-02
forum: General Help
---

### Post by Bakey on 2007-08-02
I've seen seen some threads about editing the right-click menu in Gnome, but I can't find anything about disabling it altogether.  I'm setting up an Internet kiosk and I've already got everything setup like I want it, I just need to disable right-click and I'll be good to go. I don't want to change window managers now, so can anyone tell me how to do this?  Can it be done with some utility, or in gconf-editor or in xorg.conf?

---

### Post by Bakey on 2007-08-02
No one?  *bump*

---

### Post by Bakey on 2007-08-02
Someone just suggested formatting the mouse section of my xorg.conf like so:

```

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver	"mouse"
    Option "Protocol"    "IMPS/2"
    Option "Device"      "/dev/mouse"
    Option "Buttons" "1"
    Option "ZAxisMapping" "4 5"
EndSection

```

The important section being the Options "Buttons" "1" part.  Anyone care to confirm/deny this?

---

### Post by Bakey on 2007-08-03
OK, the above xorg.conf hack did not work, I've still got both buttons working.  Anyone else got an idea?

---

### Post by anselm13 on 2007-10-12
Did you ever get an answer?  I'm trying to do the same thing.  The gnome lockdown editor does the rest and just modifying the layout manually.  But the menu is unacceptable.  I'm setting this up in a regulated environment where the kiosk HAS to be controlled.

---

### Post by anselm13 on 2007-10-12
This document was helpful to me when making a kiosk out of ubuntu and gnome:
[http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/ch-ddg-lockdown.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/ch-ddg-lockdown.html)

Also, to disable the desktop menu (i.e. the menu that appears when you right click on the desktop), run gconf-editor.  Within gconf-editor ensure the "/apps/nautilus/preferences/show_desktop" option is unchecked.

---

### Post by tra4d on 2008-03-18
Has anyone gotten this to work?  The link for redhat/gnome was not helpful since I am using xfce.  Might there be another method that works that would be similar in xfce?

I would really like to be able to completely disable the right-click (I have tried to get rid of the menus, which I can do, but you can still right click on desktop icons and open up programs).

Thanks,
Scott

---

