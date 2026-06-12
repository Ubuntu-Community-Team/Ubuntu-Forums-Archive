---
title: "Bugs/Annoyances/Recommendations"
date: 2013-03-11
forum: General Help
---

### Post by a111111111 on 2013-03-11
Hello there!
I've recently made a switch from Windows to Lubuntu for an aging netbook and am really loving it. So much in fact, that I'm trying to make it better by posting some bugs/annoyances/recommendations I've noticed while using the OS. I'd try fixing this myself as a developer, but I don't have time recently so this is as much as I can muster up at the moment. I'll try and update this post if I find more stuff.

Before I dive in, here are my specs:
AMD E-350 APU
Radeon HD 6310
8 GB RAM
Lubuntu 12.10 + all updates as of 3/11/13

**Bugs:**
_live CD_ - Lubuntu loads every single locale (ar_AE.UTF-8, ar_BH.UTF-8, etc.) when preparing for an install (using a USB created with LinuxLive USB Creator). This tends to make the boot time much longer than it needs to be - for example, Linux Mint only loads English locales. I think Lubuntu can go further and just load one language when doing the live boot (the one selected prior to the user choosing whether or not to install Lubuntu).
_lxpanel_ - the desktop pager applet does not seem to redraw when windows are closed. Redraws do happen when windows are opened and the desktop is switched. This issue seems to have appeared in 2010, but is still not fully fixed: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=598824](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=598824).
_lubuntu-desktop_ - when an application window has focus, other applications will open behind that one. I think this only works when using keyboard shortcuts to open application windows, because opening applications through the menu removes focus from all windows.
_fullscreen terminal_ - sometimes the menu button becomes unresponsive, and pressing ctrl+alt during that time will switch the DE to a fullscreen terminal, as if ctrl+alt+[f1-f6] were pressed. I was able to trigger this a couple times (especially prior to running software updates), but forgot how. Note: this still happens occasionally with a fully updated Lubuntu 12.10.

**Annoyances:**
The ability to scroll through desktops with a touchpad is slightly annoying since it can be accidental.
Skype changes the cursor theme to black for me. I suppose this is a bug, but a could-care-less one.

**Recommendations:**
Nowhere in the DE is there animation except when iconifying windows. This seems slightly inconsistent, so might as well default animateIconify to 'no' in ~/.config/openbox/lubuntu-rc.xml.
I like all the keyboard shortcuts - maybe consider setting one as default for Chromium? ctrl+alt+c?
Seeing as Lubuntu is geared at a very light footprint, I don't see a need to include ace-of-penguins. Users can get it if they really want games, or something better.

Also, sorry if this is a very unofficial way of posting bugs. I don't have a launchpad account or am very familiar with bug reporting in the linux world, so if some kind soul would offer to make these issues more official, feel free.

---

### Post by oldos2er on 2013-03-11
See [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Ideas for improving or adding features to Ubuntu should be posted to brainstorm.ubuntu.com

---

### Post by a111111111 on 2013-03-11
Thanks for the reply. I just didn't have time to set up a new account (never used launchpad) and was hoping someone in the Lubuntu team might traverse by this. I'll probably just keep it on the forums, then transfer it to the devs once I collect some more data and have some spare time.

---

### Post by oldos2er on 2013-03-11
As far as I know, the devs rarely or never visit the forums.

---

