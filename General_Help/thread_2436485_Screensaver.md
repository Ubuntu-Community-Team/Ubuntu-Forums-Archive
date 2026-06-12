---
title: "Screensaver"
date: 2020-02-07
forum: General Help
---

### Post by Philip_Edwards on 2020-02-07
Hi, Just trying to get the screensaver to work. I think I've downloaded all of the packages and it does sort of work....but everytime I start my computer it won't work until I go to Preferences>Screensaver and then I get this error message "The XScreenSaver Daemon doesn't seem to be running.on display 0.0 Launch it now?

How do I get xScreenSaver to run automatically?

Phil

---

### Post by guiverc on 2020-02-07
Which release of Lubuntu? 

Screensaver is on by default on the latest *stable* version of Lubuntu; ie. 19.10

[https://manual.lubuntu.me/stable/3/3.2/3.2.20/screensaver.html](https://manual.lubuntu.me/stable/3/3.2/3.2.20/screensaver.html)

---

### Post by Philip_Edwards on 2020-02-07
Pretty sure I'm using 18.04

Should I upgrade yet?

---

### Post by Dennis N on 2020-02-07
> I get this error message "The XScreenSaver Daemon doesn't seem to be running.on display 0.0 Launch it now? How do I get xScreenSaver to run automatically?
In Lubuntu 18.04, xscreensaver needs to be added to your startup applications. Menu > Default Applications for LX Session >  Autostart (tab). Add the command to "Manual autostarted applications": 

The command I have entered is:
```
xscreensaver -no-splash
```

---

### Post by GhX6GZMB on 2020-02-07
Just *where* did you get your installation .ISO and other files from?
FYI, lubuntu.net is NOT the official site for Lubuntu, lubuntu.me is the correct one. I've no idea what spoofed and infected files lubuntu.net contains, I've stayed away from there.
Unless you have a 32-bit machine, there's no reason not to install 19.10, it runs perfectly (including XScreensaver).

---

### Post by guiverc on 2020-02-07
> **Philip_Edwards said:**
> Pretty sure I'm using 18.04

Should I upgrade yet?

If you're happy on LXDE and it does everything you want, you can stay there. It's supported until 2021-April (3 years from 2018-April or release), and on x86 (32-bit) systems it makes the most sense.

Lubuntu 18.04 LTS was the last Lubuntu using the LXDE (*light X11 desktop*) desktop, the LXQt (the same but using Qt5 libraries) hit prime time in 18.10 becoming default (it was released prior to this only as a test version, ie. Lubuntu Next)

[https://lubuntu.me/blog/](https://lubuntu.me/blog/) states the following

> [COLOR=#555555][FONT=Ubuntu]Note, due to the extensive changes required for the shift in desktop environments, the Lubuntu team does not support upgrading from 18.04 or below to any greater release. [/FONT][/COLOR]**Doing so will result in a broken system.**[COLOR=#555555][FONT=Ubuntu] If you are on 18.04 or below and would like to upgrade, please do a fresh install.[/FONT][/COLOR]

ie. moving from 18.04 with LXDE to a LXQt install should be done via re-install.

When you do that is up to you, I'll suggest downloading the ISO, writing it to media, booting it and trying it before install.  Refer [https://manual.lubuntu.me/stable/1/Installing_lubuntu.html](https://manual.lubuntu.me/stable/1/Installing_lubuntu.html) where you can do everything except the install itself (ie. download, write to media, start lubuntu & just stop there, explore what LXQt will look like).

To me it's more modern, it's what our manual assumes (ie. 19.10), but every choice has it's pros & cons. 

LXDE was very light, but based on GTK+2 or a depreciated software stack, and required you to have both GTK2 (for desktop) libraries in memory if you used any modern GNOME or GTK3 application wasting memory.  GTK3 was heavier/slower, and thus the LXDE team joined with RazorQt and formed the newer LXQt. LXQt isn't really at a disadvantage when using GTK3 apps as it requires it's own Qt5 & GTK3 libs to be in memory; but wins out for Qt based apps.  The GTK2 apps where LXDE really soared are depreciated now anyway (XFCE moved itself to GTK3)

You'll note a number of programs have thus changed, whilst `pcmanfm` became `pcmanfm-qt` (ie. was ported from GTK2 to GTK3 for testing, then re-done GTK2 to Qt5) where it's the same real program with minor changes, programs life `leafpad` are gone, being replaced by `featherpad` (a Qt based text editor), `gpicview` (picture viewer) replaced by `lximage-qt` etc.  So the desktop has changed, along with many of the programs.

As such I'd suggest giving it a trial first, in a 'live' session (boot the install media; selecting *Start Lubuntu*) and just try it.  It won't be as fast as if installed, but you'll get a good 'taste' of Lubuntu's present & future. Remember any files saved to the home directory during a 'live' session will be lost on shutdown or reboot (so save to hdd/ssd/network storage).

---

### Post by Philip_Edwards on 2020-02-08
I've installed 18.04 on two really old laptops. They are both running Lubuntu really well. Hoping to get a newer laptop soon.

---

### Post by Philip_Edwards on 2020-02-08
Thanks for the advice.

I'm currently using an aging HP 530 laptop.  [https://www.cnet.com/products/hp-530/specs/](https://www.cnet.com/products/hp-530/specs/)

Everything is working just fine so I'm reluctant to try anything drastic.
It is a 32 bit system so my options are limited.
Hoping to get a newer laptop soon.

Phil

---

