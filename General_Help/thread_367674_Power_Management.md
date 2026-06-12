---
title: "Power Management"
date: 2007-02-22
forum: General Help
---

### Post by deeemster on 2007-02-22
Hi all,
    I've installed and become an Ubuntu user recently.  I have searched for help on Power Management but only find information on Laptop info.  I have a Desktop that I would like to go into stand-by after a certain amount of time.  Currently the screen saver comes on and stays on.  I don't want to have to manually select stand-by or hibernate.  I'm running KDE.  TIA for your help.

---

### Post by DagMan on 2007-02-24
If nothing else works, you can bind xscreensaver to a command that runs hibernate.  It would have to be run as sudo and put into the suders file.  I'm assuming that KDE uses xscreensaver.  On my laptop the scripts to initiate power saving things like hibernate are in /etc/acpi but I don't know if they would be in a differant place or not on a desktop.
I don't remember specifically, but you'de pick a screensaver and then hit advanced or settings and advanced or something like that and there is a name of the screen saver or the command to run it which can be edited.  There is also a file in your home directory ~/.xscreensaver or ~./Xscreensaver or the likes of that which you can look at.  Doing this is annoying because the computer actually hibernates every time you go in to adjust the timeout because it trys to show a preview of the screensaver.
The downside to this also is that you wouldn't have a screensaver since your screensaver would be the hibernate command.
First thing would be to find out where your computer initiates hibernate from and then work from there.

Hope something works out for you with it.

---

### Post by Trebaruna on 2007-02-28
Deeemster, I have the exact same problem. I installed Kubuntu yesterday, and have been fiddling to find and tweak settings ever since. Especially the power management features are missing.

DagMan, what deeemster and I (if I am not mistaken) are looking for is a menu or something in Control Center for example to simply and clearly setup suspend after idle time, behavior of the power button, etc.
I know that I can probably dig around in scripts for that, but distinctly recall GNOME having a GUI for that, and was really hoping KDE had a similar arrangement.

Any help? (And also, if I do need to dig around in scripts or settings files, which should I go for?) Many thanks in advance.

---

