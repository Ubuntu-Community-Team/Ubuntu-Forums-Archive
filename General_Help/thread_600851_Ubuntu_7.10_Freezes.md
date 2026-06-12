---
title: "Ubuntu 7.10 Freezes"
date: 2007-11-02
forum: General Help
---

### Post by ExtraordinaryGentlemen on 2007-11-02
First of all, i would like to say hello to all Ubuntu users! I'm new on this board as you can see...

I've downloaded Live CD and installation was freezing. (Not on the same spot. Time when ubuntu freezes is random.) After numerous times of trying to install Ubuntu, I've downloaded alternate CD.

I've installed Ubuntu from 1st try with alternate CD. When Ubuntu booted, same problem that was happening to me with live CD started to happen now. Ubuntu freezes again. And again, it freezes in random time. Sometimes it freezes 10 sec after it boots, sometimes it takes minute or two.

When it's frozen, i can't even turn on or off num lock or caps lock on my keyboard.

I have Gainward nVidia 6600GT video card and I'm suspecting that can be a problem, but if it is, I don't understand the problems with my keyboard.

Other specs of my computer:

Asrock 775Dual-880Pro (sound and network integrated)
Intel pentium 4 sock. 775 3.0 GHz
Gainward nVidia 6600 GT
Kingmax 2x512 MB DDRII
Hitachi 160 GB SATA

Every help is appreciated. Thanks in advance!

---

### Post by agurk on 2007-11-02
How far do you (sometimes) get? Do you ever see the login screen, GDM?

---

### Post by ExtraordinaryGentlemen on 2007-11-02
I log in to the desktop... I can browse menus for a while, sometimes even open the terminal...

---

### Post by agurk on 2007-11-02
Gotcha. Have you tried disabling Compiz Fusion desktop effects? System-->Preferences-->Appearance-->Visual Effects - None

---

### Post by ExtraordinaryGentlemen on 2007-11-02
Please note that i had have same problems with 7.04 version of Ubuntu where compiz fusion was not enabled by default...

---

### Post by agurk on 2007-11-02
I see, that is indeed useful information. I have no ideas at this point but will post here again should something spring to mind.

---

### Post by Felipaus on 2007-11-03
What Kernel are you using? generic, i386 or server?
I suppose you're using generic. Try i386: you'll lose a CPU (till a generic kernel update that, we hope, will solve some bugs), but no more freezes (for me it worked).

---

### Post by agurk on 2007-11-03
Having given your problem some more consideration (and googling ;)), I would recommend you to experiment with adding some boot options to your Grub. Especially the "noapic", "nolapic" and "acpi=off" options seem to have helped people with very similar problems.
There is a good how-to at [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

