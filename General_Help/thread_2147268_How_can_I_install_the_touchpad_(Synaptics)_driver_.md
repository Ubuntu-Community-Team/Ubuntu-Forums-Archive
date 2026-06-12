---
title: "How can I install the touchpad (Synaptics) driver from 11.04 (Natty) while on 13.04?"
date: 2013-05-21
forum: General Help
---

### Post by djxcon on 2013-05-21
On my eeepc (model 1001px), it seems that at a certain point in time, the touchpad has been negatively affected. I believe the last stable touchpad was with the 11.04 release and everything after that has a problem where the cursor jumps while typing. No, I do not want to use the option to "disable touchpad while typing." That is definitely not the cause of the jumping (have tested extensively). I have written a script to temporarily set values in synaptic, but that script no longer works in 13.04 and I am not sure why). 

What I would like to do is remove the synaptics driver being used in 13.04, and revert it back to the days when all was well in Natty 11.04. How can I do this?

---

### Post by ibjsb4 on 2013-05-21
Are you talking about xserver-xorg-input-synaptics?

I did not dig for the 11o4 package, but took a look at 10o4.  All dependencies seem to be in place in 13o4 for using this package, but don't know what results you will get.

 [http://packages.ubuntu.com/lucid/xserver-xorg-input-synaptics](http://packages.ubuntu.com/lucid/xserver-xorg-input-synaptics)

---

### Post by djxcon on 2013-05-21
Thanks for the help! Is that the package responsible for handling the touchpad itself? In a Windows world, I would have immediately thought to replace/update the driver. If this package is the "driver," then I think that is what I need (10.04 should be fine). If you think I might be dealing with something else, like perhaps a setting in X, please let me know. The symptom is that the cursor loses it's focus and lands at random places on the screen while typing. It makes it impossible to type consistent coherent sentences. Instead, I end up with one sentence that you can read and another that is completely messed up...missing words, letters, or just suddenly stops halfway through the sentence. Sometimes the missing words show up in other sentences, I am guessing because that's where the cursor decided to land.

---

### Post by ibjsb4 on 2013-05-21
I live a charmed life :) I have never had a touchpad problem so I really can't say for sure this is the way to go.

Given your situation, it looks like a good possibility.

---

### Post by djxcon on 2013-05-21
I'll give it a go and if it works, I will update the thread! Thanks again.

---

### Post by djxcon on 2013-05-21
Wishful thinking....this is what happened when I uninstalled the latest package and installed the Lucid package in it's place. Then I lost control of the touchpad completely :)

> Selecting previously unselected package xserver-xorg-input-synaptics.
(Reading database ... 135936 files and directories currently installed.)
Unpacking xserver-xorg-input-synaptics (from .../xserver-xorg-input-synaptics_1.2.2-1ubuntu4_i386.deb) ...
dpkg: dependency problems prevent configuration of xserver-xorg-input-synaptics:
 xserver-xorg-core (2:1.13.3-0ubuntu6) breaks xserver-xorg-input-synaptics (<= 1.2.2-1ubuntu4) and is installed.
  Version of xserver-xorg-input-synaptics to be configured is 1.2.2-1ubuntu4.
 xserver-xorg-core (2:1.13.3-0ubuntu6) breaks xserver-xorg-input-7 and is installed.
  xserver-xorg-input-synaptics (1.2.2-1ubuntu4) provides xserver-xorg-input-7.

dpkg: error processing xserver-xorg-input-synaptics (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 xserver-xorg-input-synaptics



---

### Post by ibjsb4 on 2013-05-21
Not going to work with the core package, that ship sunk :(

---

### Post by djxcon on 2013-05-22
Well dang! Is there some other generic touchpad device driver that I can use instead of the Synaptic package? Kind of like VESA for video cards?

---

