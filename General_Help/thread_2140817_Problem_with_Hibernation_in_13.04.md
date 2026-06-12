---
title: "Problem with Hibernation in 13.04"
date: 2013-04-30
forum: General Help
---

### Post by keita112 on 2013-04-30
Hey guys anyone else  have problems with hibernating on Lubuntu 13.04? I would put the laptop into hibernation and only turn it on to find the battery dry.

This occurs when:
I set the closing of the lid to hibernation, so when i close the lid.
I select the hibernation option when I log off.

It's getting quite annoying, and i've been searching google for the soloution. However since i can't find one i figured i'd as for one.

Thanks guys

---

### Post by loot270 on 2013-05-01
i'm with xubuntu 13.04 and couldn't put my laptop into hibernation, it only go into lock. This is how i fix it:

All as root:
 set to "yes" in /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
[Disable hibernate by default in upower]

and add "hibernate" in /etc/default/acpi-support
SUSPEND_METHODS="dbus-pm dbus-hal pm-utils hibernate" 

maybe this is not right way but works. 

You can look and here [http://ubuntuforums.org/showthread.php?t=2140494&p=12626012#post12626012](http://ubuntuforums.org/showthread.php?t=2140494&p=12626012#post12626012)

---

