---
title: "laptop touchpad control.."
date: 2005-10-17
forum: General Help
---

### Post by eitan on 2005-10-17
hello,

  one of the minor things that tripped me with ubuntu is the issue of 
  being able to turn off your touchpad when working on a notebook.

  i used to use ksynaptics with hoary and had to make sure to wrap
  the call with kdesu so as not to muck my .ICEauthority file ownership.
  this no longer worked today after upgrading to breezy.  i finally 
  stumbled upon the very nice qsynaptics which works great for me
  under gnome.  it appears that i have to turn off the touchpad 
  controls again each time i reboot, which is somewhat annoying.

  a. am i overlooking a standard package for controlling the touchpad
  that's already bundled with ubuntu?  if not, i highly recommend including
  qsynaptics along with the mouse and keyboard control applets in the next
  version.

  b. anyone know the command-line equivalent for turning off the touchpad?
   (so i can automate this step).

thanks, 
/ eitan

---

### Post by eitan on 2005-12-07
i solved this problem with
  synclient TouchpadOff=1

---

