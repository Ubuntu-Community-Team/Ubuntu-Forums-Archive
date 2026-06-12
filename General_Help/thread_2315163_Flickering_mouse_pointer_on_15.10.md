---
title: "Flickering mouse pointer on 15.10"
date: 2016-02-26
forum: General Help
---

### Post by treesloth on 2016-02-26
I'm having some problems with my display following the installation of Ubuntu 15.10.  First, a bit about the hardware:

Lenovo Thinkstation w/ Core i7-4790 and 32GB RAM
Dual Quadro K600 video cards:
[INDENT]Card 1:  Connected to a Lenovo Thinkvision 24" monitor @1920x1200 via DVI
Card 2:  Connected to (1) another Lenovo Thinkvision 24" monitor @1920x1200 via displayPort and (2) an Acer 22" monitor @1920x1080 via DVI.
[/INDENT]

I installed Ubuntu 15.10 via CD and updated all drivers.  I am currently encountering the following symptoms:

[LIST=1]
[*]On the first monitor, the one with its own video card, the mouse cursor flickers frequently.  This happens even when there is no apparent activity on the system.
[*]Again on the first monitor, almost always when I mouse over a selectable desktop element (such as an icon in the sidebar) or a menu option, or a browser element (like a link or a button from this forum's editor bar), the pointer disappears.  Sometimes if I leave it alone it reappears, but with the usual flickering.  If I move off the selectable element it reappears.
[*]Sometimes, on the first monitor, the pointer appears to "drag".  Moving it, there is a delay and then a jump, or just a delay followed by a normal movement.
[*]On boot, I get the message "could not set the configuration for CRTC 64".  When working in the Displays dialog I also get this message, and sometimes "CRTC 63" instead.
[/LIST]

Some more information:
[LIST=2]
[*]The two monitors on the other video card have had no problems at all.
[*]There is no unknown monitor in the display properties.
[*]All of the monitors worked perfectly in Mint up to the minute I installed Ubuntu.  Cabling is exactly as it was in Mint.
[*]I have tried the Nvidia binary driver (352.63) and the X.Org X server Nouveau driver.  There was no discernible difference between them.
[*]This did not help:  [FONT=Courier New]**gsettings set org.gnome.settings-daemon.plugins.cursor active false**[/FONT]
[/LIST]

This is a very odd thing.  Nothing about this workstation seems especially exotic, and I would have expected it to continue to work just as it did in Mint.  How can I get this to work properly, without flickering or the CRTC error message?

---

