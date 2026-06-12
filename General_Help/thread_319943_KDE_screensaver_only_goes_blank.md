---
title: "KDE screensaver only goes blank"
date: 2006-12-16
forum: General Help
---

### Post by Nathaniel on 2006-12-16
I've selected the Space screensaver, but instead of showing it the screen just goes black. The monitor is set to turn off after 15 minutes, and the screensaver should go off after 5 minutes. Still, all I get is a blank screen.

It doesn't work with other screensavers either, and sometimes I don't even get a blank screen. Every once in a while, the desktop just freezes, and when I move the mouse I get the unlock-dialogue just as I should.

Not that not having a proper screensaver is the end of the world, but it is kind of annoying that they simply don't work... :(

I'm using Kubuntu Edgy on a Thinkpad T43 with Intel chipset, running the i915 kernel module and i810 driver,

---

### Post by C-A on 2007-02-19
You to, huh?
Found a fix?
I am looking but haven't came across anything.

---

### Post by ndube on 2007-02-19
I ran into this problem a while back but it was with gnome screensavers. I had to kill the gnome-power-manager process.

ps aux | grep gnome-power-manager

kill -9 "whatever the process number is"

then try the screensaver again.

A fix has been released but it will not take affect until fiesty.

---

### Post by C-A on 2007-02-19
I just realized that although my chosen screensaver is not working, after a while a large "X" will appear and slowly move around the screen.

---

### Post by mauripop on 2007-03-20
It is a bug in Edgy Eft. You can make it go away by enabling the Dislay's power management in kcontrol. [For more info follow this link.]("https://launchpad.net/ubuntu/+source/kdeartwork/+bug/70991")

---

