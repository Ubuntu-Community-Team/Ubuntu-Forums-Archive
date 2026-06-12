---
title: "X Server or GNOME Freeze in Fiesty"
date: 2007-07-09
forum: General Help
---

### Post by Fezzler on 2007-07-09
Running 7.04 on 1.2 gHz Athlon with 628 meg memory, integrated sound and Nvidia FX GeoForce 5500 AGP.  All software was up to date and running well for months.  Have Beryl installed but off.

Started learning/loading graphics software (GIMP, Blender, Inkscape, recordmydesktop, Qcad).  I also have Samba 3+ to provide home network file sharing.

Started noticing that after I logged in, the time to Gdm and wallpaper theme loading was getting longer.  This weekend, my system started freezing after I click on Applications Places or System.  The menu system is there, but unresponsive.  I also notice one pixel of addition boarder image occurs.

I can still hit Ctrl Alt F1 to get to command line session.  Also, if I'm running gaim, it will continue to run in window.  Also, other apps continue to function (Beryl, Volume, Network, trash) but desktop switching (botton left or right) does not.  

If I hit Crtl Alt F7, then the menu will be gone.  If I hit Ctrl Alt Backspace, the login sequence will restart, I can log in, but then all I get is a blank light blue screen with a gray rectangle in upper left.  Interestingly, the mouse cursor changes to the text editor type cursone when placed in the gray box, but no keystrokes are recognized.  The only way to get back to X server GNOME (Applications Places System) is to reboot by using power button.  Sudo shutdown now doesn't work.

I have reinstalled x server.  I have reinstalled nvidia.  I'm lost now.

The last thing I did was load and use recordmydesktop and made some tweaks to ALSA and the Sound settings in Systems menu.  I had some issues with $HOME /.dmr at login but fixed with new Chmod settings.

The only other software I installed a week ago was a file manager that gives me split screens.

Any ideas beyond backing up data files and starting again?  I'm amazed how stable the kernal is.  I can always get to a command line session.

---

