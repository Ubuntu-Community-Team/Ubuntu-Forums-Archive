---
title: "Text interface is too big"
date: 2008-06-22
forum: General Help
---

### Post by Ballena on 2008-06-22
Hi

I have installed Ubuntu Server 8.04 and it works like a charm except one thing. The text interface is too big on my screen so I can't nearly type anything. Usually I SSH the machine so normally this is not a problem. But when I actually it in front of the box I can't do much with this big font size.

How do I change the font size to a smaller one? I don't have X installed if you missed that. Thanks!

---

### Post by K.Mandla on 2008-06-22
> **Ballena said:**
> Hi

I have installed Ubuntu Server 8.04 and it works like a charm except one thing. The text interface is too big on my screen so I can't nearly type anything. Usually I SSH the machine so normally this is not a problem. But when I actually it in front of the box I can't do much with this big font size.

How do I change the font size to a smaller one? I don't have X installed if you missed that. Thanks!
If you change the framebuffer resolution you can get a little more text on a screen. Try something like ```
vga=771
``` at the end of your kernel boot line.

---

### Post by Zorael on 2008-06-22
You can also reconfigure **console-setup** to set the font to a smaller size. The resolution will stay the same though, and it works alongside the vga= argument above poster mentioned.
```
$ sudo dpkg-reconfigure console-setup
```
The first seven options should be possible to just skip by mashing enter, but do as you wish. The eight option is the interesting one. Toy around with them to see which one you like most.

---

