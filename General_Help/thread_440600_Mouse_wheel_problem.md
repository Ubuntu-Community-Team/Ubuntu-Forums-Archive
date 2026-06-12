---
title: "Mouse wheel problem"
date: 2007-05-11
forum: General Help
---

### Post by shahgols on 2007-05-11
Hi everyone,

When I use the mouse wheel to go up a page, it acts like a right click.  In Firefox, it will open the menu, on the desktop, it opens a menu, etc.  Here's a portion of my xorg.conf:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Any help would be appreciated.  Tx.

---

### Post by shahgols on 2007-05-14
Please help, this is annoying.

---

### Post by JohanL on 2007-05-14
Hi, here's a link. Tells you how it should look. Can't check my own xorg.conf, since I am on the wrong computer.

[http://linuxreviews.org/howtos/xfree/mouse/]("http://linuxreviews.org/howtos/xfree/mouse/")

---

### Post by DonQuichotte on 2007-05-15
I have the very same problem and I'm also very much interested in a solution to this.

---

### Post by DonQuichotte on 2007-05-17
bump

---

### Post by DonQuichotte on 2007-05-20
I think I've found the source of this problem. Do you have an Avocent Switch (to control multiple computers with 1 mouse) connected to your pc?

---

### Post by TechnoSwiss on 2007-11-03
Avocent KVM is the source of the problem, however the problem didn't show up till xorg7. (at least, that's when I noticed it)

Anyone found an answer to this?

Seems to be the same information in this thread...
[http://ubuntuforums.org/showthread.php?t=415058&highlight=mouse+kvm+back+button&page=2](http://ubuntuforums.org/showthread.php?t=415058&highlight=mouse+kvm+back+button&page=2)

---

### Post by TechnoSwiss on 2007-11-03
I found an answer to this problem, and posted in the thread I mentioned above.

Used a PS/2 to USB converter to plug the KVM mouse into the PC, then ran the usual steps for a multi-button mouse in Linux.

---

