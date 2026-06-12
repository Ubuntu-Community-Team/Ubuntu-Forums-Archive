---
title: "Unable to use external monitor"
date: 2019-06-01
forum: General Help
---

### Post by dg.aragones on 2019-06-01
Hello all,

I have problems using external monitors with Ubuntu 18.04. I use an HP laptop and I want to connect two different external monitors, one that I have at home (LG) and one that I have at work (Dell). In the two cases I have the same issue: the laptop's screen turns black and never connects.

Any idea how can I do this?

Thank you in advance for any help!

---

### Post by TheFu on 2019-06-01
plug in the monitor via hdmi. Power on the monitor.
Run **lxrandr**, enable the monitor. There's a checkbox. This is the easiest, to-the-point monitor enable, resolution, refresh-rate tool that I know.

If the computer goes through a KVM-switch or any sort of inline converter, like VGA, DVI-whatever, you might have to do some EDID manual settings and xrandr stuff. It can get ugly.

---

### Post by hello98 on 2019-06-30
Hi, everyone. My HP laptop (only intel graphic) runs ubuntu 18.04, when I connect external monitor (just one monitor) and set resolution 800x600, monitor works (although not detect correctly external - unknow VGA) but it do not work when I change it's resolution. the highest solution that laptop display 1024x768 whereas highest monitor resolution is 1366x768. Anyone have any suggestion for me? thanks in advanced.

---

