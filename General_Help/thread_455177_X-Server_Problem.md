---
title: "X-Server Problem"
date: 2007-05-26
forum: General Help
---

### Post by Eminem on 2007-05-26
I just finished installing Ubuntu on a 4GB partition using Wubi. All went well until I wasn't able to boot into the OS because of a "X Server Problem" or something of that sort. It asked me to check for a version of some sort in wiki.x.org or something.

I have an ATI Radeon 7000 Graphics Card, any help?

---

### Post by hessiess on 2007-05-26
> I have an ATI Radeon 7000 Graphics Card, any help?

that would be your problem. nividia cards have mutch better support under linux

---

### Post by Eminem on 2007-05-26
> **hessiess said:**
> that would be your problem. nividia cards have mutch better support under linux

Is there a way to get into the Recovery Mode or some kind of command line for Ubuntu using Wubi?

---

### Post by hessiess on 2007-05-26
you can boot into recovery mode from grub, it should give you an option. dos your mobo have a bult in graphics card? if so try using that. 

try googaling for "linux driver ATI Radeon 7000", if you canot find anything you may haft to see if its posable to swap/ sell that card. and get a nvidia one. nvidia do have linux drivers.

---

### Post by happy-and-lost on 2007-05-26
> **hessiess said:**
> that would be your problem. nividia cards have mutch better support under linux

That's not very helpful now, is it? ;)

ATi cards *do* work fine under Linux, just not as well as nVidia cards do when under high demand (eg. running Beryl, full 3D games) . When it complains that X has crashed, does it then take you to a command line interface, or does it just reboot itsself?

If you find yourself at a black screen like this:

```
username@machine:~$
``` the you're in business.

type into that command line *sudo nano /etc/X11/xorg.conf* 

Scroll down to where it says *Section: "Device"*

And if it says Driver: "vesa", that's your problem. Change "vesa" to "ati", save (<Ctrl>+O) and exit (<Ctrl>+X), then *sudo reboot*. Should work now.

If the vesa driver is not a problem, post back what it *does* say there.

---

