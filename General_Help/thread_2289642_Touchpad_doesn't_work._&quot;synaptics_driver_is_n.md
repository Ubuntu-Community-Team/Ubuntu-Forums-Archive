---
title: "Touchpad doesn't work. &quot;synaptics driver is not installed (or is not used)&quot;"
date: 2015-08-05
forum: General Help
---

### Post by Linuxour on 2015-08-05
Hello,

I've Kubuntu 14.04.02 64-bit. Cann't use my touchpad, When I open Touchpad settings this message appears  "synaptics driver is not installed (or is not used)".
I've tried the first answer in the following link but it didn't work.

[http://askubuntu.com/questions/397677/synaptics-drivers-are-not-loading-on-kubuntu-13-10-on-dell-vostro-2420](http://askubuntu.com/questions/397677/synaptics-drivers-are-not-loading-on-kubuntu-13-10-on-dell-vostro-2420)

As for the second answer, I have many files and don't know what should I copy.

10-evdev.conf10-quirks.conf
11-evdev-quirks.conf
11-evdev-trackpoint.conf
50-synaptics.conf
51-synaptics-quirks.conf

PS: I don't have vostro 2420. I've Inspiron N5050.

---

### Post by TheFu on 2015-08-06
Synaptics is used on a C720 chromebook. Under 14.04, with every new kernel, I have to rebuild the drivers from source. For me, that is preferred over using a newer release where the drivers are included in the stock kernel.  The script is specific to this model, so it will not help you.

I know that isn't a solution, but perhaps it sets expectations?

---

### Post by Linuxour on 2015-08-06
Thanks for sharing info, TheFu. I don't know what happened but it just worked and the message doesn't appear anymore.

---

