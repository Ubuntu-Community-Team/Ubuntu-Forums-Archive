---
title: "Trouble setting desktop resolution in KDE?  Look here . . ."
date: 2007-04-24
forum: General Help
---

### Post by mageus on 2007-04-24
For all the people who complain that the KDE Display control panel doesn't show any usable resolutions for the screen size:

- edit the file ~/.kde/share/config/displayconfigrc with a text editor

- Edit one of the [ScreenX] sections with the resolution (and other settings) you want.

- Presumably you can add any number of [ScreenX] sections for all the different resolutions you want to have access to.

- Add krandrtray to your Autostart folder.  This puts an applet in your kicker bar that you can control screen resolution and screen rotation from.  Should work in any freedesktop compliant taskbar.


My situation:
I use IceWM.  I booted into KDE and used the Display control panel to turn on the power save feature for the monitor. (serves me right for using it)  When I went back into IceWM the screen always defaults to 800x600.  Then the Display control panel only showed 800x600 as a resolution option.
The above fix is a kludge, but it works.

---

