---
title: "molecule screen saver"
date: 2008-04-07
forum: General Help
---

### Post by n4uau on 2008-04-07
I am pretty new to Ubuntu and was looking at the screensaver preferences. When I tried to look at the molecules saver the entire system hung up. Had to unplug the PC to reboot.

1. This seems to be a problem.
2. CTL/ALT/DE,L  CTL-Break, ESC didn't work. Is there another way to terminate an unresponsive program?


Sam U

---

### Post by mixmaster on 2008-04-07
Depending on how badly locked up it was, you could try Ctrl-Alt-F1 to move to a full-screen session and then kill the screensaver process (then CTRL-ALT-F7 to get back).  Failing that, you could ssh in from another box if you had one handy.

I remember in Dapper some of the screensavers would randomly hang my system.  I must admit finding out why was more trouble than it was worth to me so I just used a blank screen as a saver (which is more environmentally friendly anyway).

---

### Post by n4uau on 2008-04-07
Mixmaster, I'd love to get back  to a plain screen but when I go to screen saver it locks up right away. In fact when it came time for the saver to run it ran the locked up program and hung the machine all on its own. Going to have to see if I can remove the screen saver module. Sam

---

### Post by n4uau on 2008-04-09
> **n4uau said:**
> I am pretty new to Ubuntu and was looking at the screensaver preferences. When I tried to look at the molecules saver the entire system hung up. Had to unplug the PC to reboot.

1. This seems to be a problem.
2. CTL/ALT/DE,L  CTL-Break, ESC didn't work. Is there another way to terminate an unresponsive program?

Sam U

I'm going to try again. I found the author of Molecule, Jamie Zawinski , and his answer is that is below. meanwhile I have a system that hangs and I can't use and can't delete the xscreensaver files because I don't have permission because I am not the author.  Surely there is a way to delete Molecule or all the screen savers.
Sam

 I'm sorry. But the fact is that an X server crash is, by definition, a bug in the X server.

The rule is that absolutely nothing a client program throws at the X server should make it crash. When an X client does something wrong, the server is supposed to return an error, causing the client to exit. If the server itself goes down, that's a bug in the server. There may also be a bug in the client -- but probably not.

This also goes for DRI, GL, and any vendor- or hardware-specific libraries you might be using. If something in xscreensaver caused your display to freeze, or logged you out, or made your monitor explode, I can pretty much guarantee you that the bug is in your X server or your video driver, and not in xscreensaver.

Try upgrading your X server and video drivers. If that doesn't help, you can try running each display mode in turn until you figure out which one is triggering the X server bug. It is most likely to be one of the GL (3D) screensavers, since those are the ones that actually take advantage of your video hardware. When you figure out which one is causing the crash, you now have a reproducible test case! Congratulations. Please report that to the vendor of your X server and/or your video drivers so that they can fix the problem.

Turning off acceleration in your X server may also make the problem go away, but that will also slow your machine down a lot.

If that still brings you no joy, then I recommend switching to MacOS. I did.

---

### Post by n4uau on 2008-04-09
I want to Administration and Package Manger and re-installed xscreensave and voila it works again.

---

