---
title: "Random system freeze"
date: 2007-03-13
forum: General Help
---

### Post by novabox on 2007-03-13
I'm seeing a rather strange issue with my desktop (a slightly old IBM ThinkCentre Desktop, 2.5GHz Celeron, Ingegrated Intel graphics), which is running Ubuntu 6.10 (all the latest updates).

Once the system is booted, the system will freeze anywhere from an hour to a few days later (once it seemed to freeze while still at the login screen).

When this freeze happens, I can still perform some operations via the GUI (click on webpage links, etc), but they process very slowly, and pretty soon it stops responding all together. Also, the system monitor applet doesn't show any CPU activity, despite the fact that the limited actions I can take clearly do take at least some processor time.

If I try to do something like shut down the system, I can click on the button to shut down, which brings up the dialog with the various options (shut down, restart, lock screen,etc). However, at that point I cannot click on any of those buttons, and the system is completely non-responsive. Ctrl-Alt-Del does nothing, and I am forced to hard-reboot the system.

The only applications I typically have running are Gaim and Firefox, though I've seen this happen with neither of those running.

I've already tried updating the BIOS for my system, thinking it might be some weird motherboard glitch, but that had no effect.

Anyone know of some possible causes or things I should be checking?

---

### Post by novabox on 2007-04-29
Well, after week's of searching, I appear to have found the answer on my own.  Posting here for the benefit of anyone else who encounters similar issues:

Found a few other posts spread out all over the interwebs that suggest adding the following kernel boot options:

acpi=off noapic nolapic

Apparently those features (mostly related to power control features, like sleep mode, hibernate, etc) can have problems with Linux on some mobo's.  The drawback is that I can't set my system to to turn off the monitor after a set period of time.  But I'm okay with that.

---

