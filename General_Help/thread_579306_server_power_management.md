---
title: "server power management"
date: 2007-10-18
forum: General Help
---

### Post by Andra on 2007-10-18
hello group,

I have two ubuntu servers:
1) i386 with ubuntu 6.10, with graphical kubuntu
   attached to an old APC ups
2) 64-bit Intel with  ubuntu 7.04, no graphical mode
   attached to a newer APC ups (model AP9617)

It is expected that on some day this month the power will be switched off completely for about an hour. The servers are attached to upses. I would like they shutdown gracefully and when power is returned they wake up. I may not be on the place myself to shutdown and power on by hand.

Is graceful shutdown (and wake-up) already in the system, or how could I set it up?


Andra

---

### Post by expatCM on 2007-10-18
If you have a look in the repositories you will find a program called apcupsd.  This should manage your system when the power fails and there is insufficient charge in the battery to keep going.  An ordered shut down should be delivered.  You will need to connect your APC UPS to the computer USB port using the cable with a USB plug on one end and an Ethernet plug on the other.  Normally supplied with the UPS.

Bringing the system up again may be a bit different.  I think the easiest approach here is to have a look at your BIOS.  In many BIOS versions there is an option for returning a system to the last state when the power is resumed.  Basically it just starts the system up again automatically.  If your BIOS supports this it may or may not help you ...   it all will depend on how you have set up your system for security in whether or not a user name and password needs to be entered during power on ....  :)

---

