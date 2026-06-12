---
title: "Kubuntu unstable?"
date: 2006-07-06
forum: General Help
---

### Post by GoodPanos on 2006-07-06
I have two issues that happen randomly.

1)  I have created a desktop icon that opens Konqueror as root.  I also do *sudo konqueror* at the terminal to accomplish the same thing.

It seems that almost half of the times it doesn't work.  :confused:   I'll run Konqueror as root and nothing will happen.  When I do it through the terminal it just hangs there.  Mind you this never failed once in 5.10.

2) When I shut down or restart the screen will flicker and then it will go blank and just sit there.  Normally it will flicker and then display the shutdown process.  I'm thinking this could be related to the ATI drivers, but I don't know.

Dell Inspiron 6000; ATI Mobile X300 128MB; SATA 80GB; 1.25GB RAM.

I could put Ubuntu but I am going to miss Quanta (what a great program that is).

---

### Post by blackjack6.21.91 on 2006-07-06
You will probably have more success running the command
> gksu konqueror
And you are free to switch to Ubuntu, KDE apps are available (GNOME and Quanta!)

---

### Post by GoodPanos on 2006-07-06
Thank you for the advice but that didn't work.  I'm sure it will work if I reboot.

Isn't Quanta a KDE app?  So running it from Gnome I would have to load all the KDE libraries?

---

### Post by user1397 on 2006-07-06
[quote=GoodPanos]Thank you for the advice but that didn't work.  I'm sure it will work if I reboot.

Isn't Quanta a KDE app?  So running it from Gnome I would have to load all the KDE libraries?[/quote]the command for running graphical programs as root is **kdesu <command>**. For example ```
kdesu konqueror
```if you run graphical apps as root just with sudo, you might get into some big problems.  the gnome equivalent would be ```
gksudo nautilus
``` 
and yes, kde apps can be run under gnome and vice versa, but you would need all those extra kde libs, but oh what the hell, if you have 80 Gigs of hdd space, why bother with a few extra megs of libs?

---

### Post by D!mon on 2006-07-06
or

kdesu konqueror 

if you are using kde

---

### Post by GoodPanos on 2006-07-09
Any ideas on issue 2?

---

### Post by vem0m on 2006-07-09
possibly it might be due to it going into a higher resolution then ur screen supports try logging out and if nothing shows up after a minute type urpassword blindly into ur computer and see if it relogs u back into KDE. it happens to me as i have a small monitor and KDE and X11 insists on a higher resolution then my montior can do lol but anyways might be it let us know!

---

### Post by jimmygoon on 2006-07-09
Um... can someone explain gksudo vs sudo? thanks.

---

### Post by ozorba on 2006-07-09
> **jimmygoon said:**
> Um... can someone explain gksudo vs sudo? thanks.

Very simple:

I use sudu for terminal commands.
I use gksudo/kdesu to start up gnome/kde applications in root mode. 

OZ

---

