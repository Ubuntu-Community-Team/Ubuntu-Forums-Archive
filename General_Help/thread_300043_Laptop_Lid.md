---
title: "Laptop Lid"
date: 2006-11-15
forum: General Help
---

### Post by Milambar on 2006-11-15
Whenever I close the laptop lid, it goes into some kind of suspend mode.

I don't want this, because when at home, I hook the laptop up to an external monitor and keyboard, and close the lid, mostly because the cat seems to love walking over the laptop keyboard, but secondly to save the laptops LCD backlight which tends to be expensive to replace.

Google searches suggest to deactivate this behaviour in gnome-power-manager, however when I check gnome-power-manager, there is nothing to alter that would affect that, probably because I have to acpi=off to even get the laptop to boot?

So, given that, is there any other way to stop it hibernating or suspending whenever I close the lid? An equivalent to window's "When I close the lid of the laptop: Do nothing"?

Thanks

Milambar

---

### Post by Titus A Duxass on 2006-11-15
Have a look in the BIOS, sometimes there is an option there.

---

### Post by Milambar on 2006-11-15
Yeah, already checked, theres nothing relevant.

I edited the /etc/acpi/events/lidbtn script and... basically commented everything out. Its kinda done something, the laptop no longer suspends, but the keyboard and mouse stops responding until I re-open the lid.

I cannot see anything else that might be relevant..

Any other ideas?

---

### Post by Milambar on 2006-11-17
I guess nobody knows the answer. Chalk one up for windows, sadly.

---

### Post by Aranel on 2006-11-17
For me, in System > Preferences > Power Management (that's gnome-power-manager), there's a "When laptop lid is closed" option under the "Running on AC" tab. That's how I set my laptop to just turn off the display when I close the lid, but if that option isn't there, I'm not sure what to tell you. Sorry. :(

---

### Post by Milambar on 2006-11-17
Yeah, its not there, because the laptop has to be booted with acpi=off, I think. Hunted high and low through /etc/ for any config file that might look relevant, without joy :(

---

