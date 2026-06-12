---
title: "Gnome issues"
date: 2006-11-02
forum: General Help
---

### Post by Scheater5 on 2006-11-02
I recently upgraded to Kubuntu Edgy.  A somewhat painful, but ultimately worthwile endeavor.   KDE upgraded fine, Xfce and Enlightenment both are gone (which is fine, I was going to uninstall them anyway), but Gnome has had some bizarre issues.  
Signing into Gnome, the first thing that happens is a series of Bug Buddies pop up, even before the desktop background changes from the KDM blue to my background picture.  Then a window pops up saying Nautilus crashes - shouldn't Gnome itself crash if Nautilus is no longer there?  But, assume I get through all this without the desktop locking up, I'm left with an essentially fully functional Gnome.  What is going on, and what can I do about it?  I think that reinstalling Gnome is probably the way to go, but the only way I know to do that is reinstall "ubuntu-desktop," and how would that effect my programs, settings, ect?
If it is important, I originally started with 6.06 Ubuntu, then installed KDE, made that default and changed the bootsplash, ect to essentially make it Kubuntu. In the time between then and the upgrade I installed Xfce and Enlightenment, but never did any further configuration related to them.  Post-upgrade, I am left with only KDE and Gnome.

---

### Post by Scheater5 on 2006-11-02
Poking around in my Synaptic shows that Kubuntu-desktop is installed, but Ubuntu-desktop isn't.  Would installing Ubuntu-desktop remedy this problem?  I know it doesn't directly have anything to do with the problems, but my instinct is that it has something to do with the upgrade - and simply installing Ubuntu-desktop may, by defult, return things to a usable setting.  Any ideas?

---

### Post by hexion on 2006-11-02
It's recommended to install ubuntu-desktop (or kubuntu-desktop in kubuntu) before dist-upgrading.

Maybe your KDE files were upgraded but your gnome ones are still from dapper...

I don't know... anyway dist-upgrades never went fine for me since hoary :-?

---

### Post by Polygon on 2006-11-02
yeah, kubuntu-desktop and ubuntu-desktop are just metapackages that simply point to all the required files needed for both kde and gnome as dependencies, so try installing ubuntu-desktop and see if that fixes it.

---

### Post by d3v1ant_0n3 on 2006-11-02
I had Ubuntu 6.10 with kubuntu-desktop package installed.

For some reason ( I really wish I knew exactly what caused this), if I had Gnome apps set to my KDE theme in Kubuntu, when I logged into GNOME, I would get similar symptons to yours. I solved it by using a GTK theme for GTK apps in Kubuntu.

I hope this makes sense to you?

---

### Post by Scheater5 on 2006-11-07
Thanks for the replies, guys.  Sorry it took me so long to try this.  Installing Ubuntu-desktop didn't cause any problems, but it didn't fix any, either.  The "Bug Buddies" sitll pop up, but now they go away immediatly, and the desktop takes longer loading up.  Nautlis still crashes, and then after that everything seems to function normally.  I'm running aptitude right now, and I'll restart the X server to see if the upgrade helps (fglrx is among the updates, as well as what I think is a kernal upgrade - we'll see if that helps).

---

### Post by Scheater5 on 2006-11-07
Alas, no sale.  Essentially the same problems.  This time the Gnome Settings Daemon refused to start - but Nautilus didn't crash.  What do you guys thing reinstalling Ubuntu-desktop would do?

---

