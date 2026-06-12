---
title: "strange change in attitude..."
date: 2008-01-05
forum: General Help
---

### Post by KaYnemO on 2008-01-05
Hiya all!

Running a Gutsy on an Acer Aspire 5670 ATI Radeon Moblity x1600 etc. I installed it over Feisty from CD, did lotsa upgrades, got Compiz running. Sudden of all (after no apparent changes to the machine or Ubuntu) after OS is loaded and it silently passes the login screen, I get a blinking cursor blank screen. No key combinations work. Reboot in recovery get a 'Hal isn't running' popup, didn't know what to do - checked dependencies with synaptic, reboots fine in normal mode, but with a 'Keyboard Applet isn't responding do you want to delete it from the taskbar? ' popup this time. A didn't care, so I chose 'delete', Haven't rebooted yet - the machine seems to function for now. An ideas? How would you fix a 'Hal isn't running situation?'.

Thanx

---

### Post by Mathijsken on 2008-01-10
There are several other people (including me) who had isues with HAL.
Error messages like: "Internal Error, could not initialise HAL" are very frustrating as they don't really help you any further...
Several solutions have been suggested some of which work, some of which don't depending on the situation.
Running these commands in a terminal or VT solved it for me:
```

sudo update-rc.d -f hal remove
sudo update-rc.d hal defaults
sudo update-rc.d -f dbus remove
sudo update-rc.d dbus defaults

```

I also downgraded HAL and then upgraded back to the current version (using the feisty backports repositry) in the package manager, but I don't think that's neccesary

hope this helps you
Mathijs

---

