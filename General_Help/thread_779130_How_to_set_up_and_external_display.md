---
title: "How to set up and external display?"
date: 2008-05-02
forum: General Help
---

### Post by amazoohwawa on 2008-05-02
I was wondering if anyone can guide as to how to connect my laptop with an external display. I need to connect the laptop to an overhead projector. I had no problem when I used 7.10 but since upgrading to 8.04 the laptop is unable to connect to the projector.

help is always appreciated!

---

### Post by bnl on 2008-05-05
If i plug the VGA cable and then log out and in (or CTRL-ALT-BACKSPACE to restart X), it works.

Right now i'm getting resolution problems which i'm hunting for an answer.  I'm not sure if there's automatic adjustment like in Windows.  For now, you can use xrandr to change resolutions:

Type xrandr and you'll see the valid outputs (LVDS and VGA-0 on mine) and resolutions for your laptop and the projector (if it's connected).

Then you can type

xrandr --output <output> --mode <resolution>

to set the output.

---

### Post by jimv on 2008-05-05
Do you have a Switch-Display key on your laptop?  I think it's usually Fn+F4

---

### Post by bnl on 2008-05-06
On mine, it's Fn-F7, but it doesn't work.  I just made some scripts that call xrandr to activate the external output.

It also looks like the projectors i'll be using can project to the resolution of my laptop (1400x1050), though a tiny, tiny bit of it is cut off from two edges, which i can live with.

---

