---
title: "Giving (K)ubuntu Gentoo-like speed"
date: 2007-12-09
forum: General Help
---

### Post by Capricori on 2007-12-09
I was just wondering...
Gentoo's superior speed is down to the fact that you compile everything for your machine, with the options you want, right?

So, if I were to grab the source for a Ubuntu program, and compile it myself, am I likely to see an improved speed over the .deb/repository version of the program?

Capricori.

---

### Post by p_quarles on 2007-12-09
If you were to compile all of your applications from source, you wouldn't really be running Ubuntu. Furthermore, you wouldn't be running Gentoo, either: you would need to keep track of the security notices for each app that you'd compiled, without any help from Emerge. 

If you just want a more efficient version of K/Ubuntu, I'd recommend the following:
1) Download and burn the "alternate" install disk
2) Choose the "CLI installation" option after booting
3) Install the base packages for the desktop of your choice:
For Gnome:
```
sudo apt-get install gnome-core xorg gdm
```
For KDE:
```
sudo apt-get install kde-core xorg kdm
```
4) Start the desktop manager:
```
sudo /etc/init.d/gdm start
```
For KDE, replace "gdm" with "kdm."

---

### Post by Capricori on 2007-12-09
I was looking at installing a CLI-only system on my other machine, actually :)
And the point about having to track each app manually, good point, I forgot that :S

This whole line of thinking came from playing with Kontact's options, and thinking to myself that I'll never use half of them, and wondering how much quicker the program would be without them.
Just another of my many theories that are going nowhere :)

Thanks for the reply.
Capricori.

---

