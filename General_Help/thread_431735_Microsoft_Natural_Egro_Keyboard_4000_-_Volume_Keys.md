---
title: "Microsoft Natural Egro Keyboard 4000 - Volume Keys"
date: 2007-05-03
forum: General Help
---

### Post by kiranlightpaw on 2007-05-03
Hola!

This is an odd behaviour. I have a Microsoft Natural Ergonomic Keyboard 4000 v1.0 USB keyboard. The volume controls (at the top) work in the Live CD environment, but refuse to work on the install. I've checked the Keyboard Bindings between the Live CD and the install and they're the same.

When I click it in the Live CD enviro, I get the popup volume control as would be expected, but when I click it in the installed enviro, I get a weird thing happening to the screen that looks like something crashing and all the widgets reverting to what looks like a default GTK appearance. It lasts for about two or three seconds, then reverts to standard Ubuntu theme.

Any thoughts? I'm aware of the other thread that describes the special keys - that's not the issue I'm working on (yet). It just seems odd to me that this would work in the Live enviro and not in the installed enviro.

EDIT: I'm using Feisty on an  AMD Athlon 64 Processor 3700. All updates (at least from the manager) have been installed. A8N-SLI motherboard.

---

### Post by kiranlightpaw on 2007-05-04
Here's an update.

I've determined that it isn't the volume keys but apparently whatever they run that's messing up. I can reassign the keycodes (0xae and 0xb0) using gconf-editor to do other things (like launch calculator) that work. So whatever those keys by default launch is crashing or something.

Anyone? Bueller? Bueller?

---

### Post by kiranlightpaw on 2007-05-04
Update:

The volume actually changes, at least according to alsamixergui. But whatever little program that runs on the desktop in the Live Environment is crashing on my installed enviro.

Thoughts?

---

### Post by kiranlightpaw on 2007-05-04
Update:

gnome-settings-daemon appears to be crashing whenever I press the volume up / down buttons. I finally got a message after I pressed it enough. This would kind of explain the reversion to GTK widgets.

Does ANYONE have ANY help on this? I am REALLY running out of troubleshooting ideas!

---

### Post by kiranlightpaw on 2007-05-04
Day two of trying to get this to work.

I think something concerning the nvidia drivers is causing gnome-settings-daemon to crash. I reinstalled the OS this morning and lo and behold my buttons were working fine just as in the live environment. However, after I installed and configured the nvidia restricted drivers, gnome-settings-daemon crashes when I push the button.

Umm ... help?

---

### Post by kiranlightpaw on 2007-05-04
FIXED!

[This bug]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232") is related. Apparently nVidia + Xinerama + Gnome Settings Daemon don't mix without putting in some tweaks in the xorg.conf file. The workaround is in the bug.

Christ, that was a f***ing pain.

---

### Post by cybersmoker on 2008-07-05
kiranlightpaw,
What tweaks did you make. I was running ubuntu 8.04 and installed the kubuntu pack to try it out and worked beautifully until I started messing with the dbus, I believe. I was used to using Banshee under ubuntu and when I switched sessions to kubuntu, I was getting a dbus error. So I started using Amorak. Nice player lots of features. But I digress. Now the keys dont work like yours didnt.

Any help would be appreciated.

PS. I was trying to get dual monitors working. Though all the keys still worked after that. The only thing that I can think of that was after that was  the DBUS issue.

AMD Athlon 64 x2 5200 / XFX GeForce 7900 / 2gb DDR800

---

