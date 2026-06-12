---
title: "changed GDM now I no longer get login window"
date: 2008-06-18
forum: General Help
---

### Post by L0stAngel on 2008-06-18
I have an inspiron 1520, and just changed my login window to the following via the login window theme changer in ubuntu 8.10.
[http://gnome-look.org/content/show.php/FBI_Terminal?content=82380](http://gnome-look.org/content/show.php/FBI_Terminal?content=82380)

Now, when I turn my computer on...instead of being prompted by a login window, I am just prompted with the ubuntu 'waiting' pointer...aka the equivelent of the windows hourglass, and nothing happens. How can I get my login back to allow me to login?

---

### Post by NikoC on 2008-06-18
What if you delete the folder containing the theme? Gnome doesn't find it anymore and it should choose the default provided by ubuntu instead...

e.g. in a terminal type (or failsafe boot):
ls /usr/share/gdm/themes

This will get you a list of all your installed login themes, now knowing the name of the theme that you have recently chosen and is thus messing up your system you can in a terminal type:

sudo rm -r /usr/share/gdm/themes/theme_name

Then just reboot... hope it works,

Cheers.

---

