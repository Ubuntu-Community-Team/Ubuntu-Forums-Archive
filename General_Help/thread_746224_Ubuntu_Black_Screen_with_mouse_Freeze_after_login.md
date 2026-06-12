---
title: "Ubuntu Black Screen with mouse Freeze after login"
date: 2008-04-05
forum: General Help
---

### Post by greekboy777 on 2008-04-05
Hi everyone!

Go easy on me, im a 1 month old Ubuntu user - and today i finally signed up because i had my first problem that i am unable to resolve myself.

OK the first thing i did when installing Ubuntu was get my video card working properly (Radeon) using 3rd party drivers, and then installed Compiz. It worked fine.

This afternoon ubuntu had a whole buch of updates, so natrually i installed them. Upon reboot i have had so many problems. It started with a black screen after loading, then i ran the reconfigure xorg command and then got a login screen, but now it just FREEZES after logging in (in the gui). It loads to a black screen with a white bar at the top and bottom and the mouse is moving, basically seconds after the music finishes the mouse freezes, the computer stops loading and the only thing i can do is hold the power button.

I tried recovery mode, and im getting frustrated!?!?

Anyone have any suggestions?? :(

---

### Post by SorryGoFish on 2008-04-13
Is it failing when compiz is starting?

You can swith to a terminal with ctrl+alt+f1, then edit your xorg config manually, with emacs or vi or some other editor.
```
sudo emacs /etc/X11/xorg.conf 
```
and comment out the line
```
Option "Composite" "Enable"
```
By adding a # at the beginning of the line.

You could also try just updating from the command line first
```
sudo apt-get update
sudo apt-get upgrade
```

---

