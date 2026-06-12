---
title: "Trying to install codecs.....im so confused!"
date: 2007-12-28
forum: General Help
---

### Post by boxxy27 on 2007-12-28
when i try to get the ugly and bad gstream codec from either of the add or remove programs list or when i try to play a file that i need the codec with....whenever i try i always get this error and dont know what to do!

Cannot install 'gstreamer0.10-plugins-bad-multiverse'

This application conflicts with other installed software. To install 'gstreamer0.10-plugins-bad-multiverse' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

I went to synaptic package manager but i dont know what to do right there and then...

Also i try to install vlc from the manager....but when i try i get the error...

"could not mark all packages for installation or upgrade....packages have unresolvable dependences..." then it says this

vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libsdl-image1.2 (>=1.2.5) but it is not installable
 Depends: ttf-dejavu  but it is not installable

and iv been stuck for soo long, i just installed this last night and finally got the realtec sound working which took a long time...

---

### Post by rsambuca on 2007-12-28
First make sure that all of your repositories are enabled.  To do this, go to your top menu bar and select:  "System - Administration - Software Sources".  On the tab that opens, make sure the four boxes are checked (main, universe, multiverse, restricted).  Close the window, and update the repositories when prompted.

Then open a terminal:  Applications -> Accessories -> Terminal

Enter the following code and tell us what happens:```
sudo apt-get update && sudo apt-get upgrade
```

If you get no error messages, then enter the following:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by boxxy27 on 2007-12-28
woha! thanks, im pretty sure its going to work...but im on dial up and it needs to download 39mb of data which is going to take a couple of hours....omg lol

but thanks anyway....is this going to also solve my vlc media player problem?

---

