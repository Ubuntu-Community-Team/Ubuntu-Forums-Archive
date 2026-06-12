---
title: "Reset (re-enable) touchpad scrolling"
date: 2014-05-08
forum: General Help
---

### Post by Benone_Sinulescu on 2014-05-08
Hello everyone,

Although I love Unity, there is one thing that's been getting on my nerves: when I use my touchpad for two-finger scrolling, it very often happens that I trigger the (three-finger tap) Dash menu. So I thought I'd have a go at disabling the Dash gesture. I went on and installed Compiz Config Settings Manager and unticked a few boxes and all of the sudden my touchpad stopped working completely. After a great deal of scouring through forums, I managed to gain back the basic functionality of moving the pointer around and left and right clicks. However, absolutely no gestures are being recognised (as I have found from using Touchegg, which has no reaction no matter how many fingers or limbs I touch or bash the pad with).

I also did an upgrade from 12.10 to 13.10, in the hope that the touchpad settings will be reset (they weren't).

I have a Dell XPS 13 laptop.

Any help would be greatly appreciated!
Thanks,
Victor

---

### Post by Benone_Sinulescu on 2015-02-19
Meanwhile, I've been regularly trying to solve this issue as I've been building up frustration, scavenging forums and man pages for a solution, but alas, everything I tried so far has failed. I've very recently tried to use **tpconfig** to investigate my issue, from which I got this output:

$ tpconfig -i
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;        no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.


I couldn't agree more with the above output: **no tap gestures.** I tried to fix this by running:

$ tpconfig --tapmode=1
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Corner taps disabled;        no tap gestures.

Again, **no tap gestures.** 

Any ideas would be much appreciated.
Victor

---

