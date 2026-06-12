---
title: "Xorg and multiple X Screens"
date: 2020-04-29
forum: General Help
---

### Post by driesz on 2020-04-29
Has anybody successfully configured Xorg to present separate X Screens on a multi-monitor setup?  This would result in the following commands:
```

xterm -display :0.0
xterm -display :0.1
```
displaying on separate monitors.

For systems with Nvidia graphics adapters, this can be configured through the Nvidia utility distributed with their proprietary driver.  I'm trying to figure out a more generic solution, specifically for VirtualBox and the new Raspberry PI 4.

I've spent untold hours futzing with xorg.conf to no avail.  Multiple screen layouts are entirely ignored and the displays are bonded into a single screen.  I feel like I'm back in 1993 trying to get my CRT monitor woking with XFree86.

I need help.  Is what I'm trying to do even supported by Xorg?

---

### Post by CelticWarrior on 2020-04-29
In Virtualbox we're typically using the virtualized graphics so I'm not sure it support it.
I know (almost) nothing about RPi4 but I guess it's also limited.

---

### Post by dragonfly41 on 2020-04-29
I'm not sure if [x-tile]("https://www.giuspen.com/x-tile/") is relevant for you. But giuspen (the author) develops a nice set of tools.

---

### Post by driesz on 2020-04-29
> **dragonfly41 said:**
> I'm not sure if [x-tile]("https://www.giuspen.com/x-tile/") is relevant for you. But giuspen (the author) develops a nice set of tools.
That looks like a neat utility and I may find use for it, but it's not what I'm after.

---

### Post by HermanAB on 2020-04-30
Which version of Ubuntu are you using - does it actually run Xorg?

---

### Post by driesz on 2020-04-30
> **HermanAB said:**
> Which version of Ubuntu are you using - does it actually run Xorg?

I've tried this at various points in time on Xubuntu 16.04, 18.04, and 20.04.  Xorg was definitely used.  In some cases I invoked it directly from the console.

On the RPi, I've used Raspbian.  Still Xorg.

---

### Post by HermanAB on 2020-05-01
Then I suggest you use xrandr to change the configuration.

---

