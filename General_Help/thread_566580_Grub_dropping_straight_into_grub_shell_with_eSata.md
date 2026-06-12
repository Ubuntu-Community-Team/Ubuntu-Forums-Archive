---
title: "Grub dropping straight into grub shell with eSata"
date: 2007-10-03
forum: General Help
---

### Post by cocodude on 2007-10-03
Hello there,

Feisty generally works very nicely for me. However, I've put my main hard drive in an external case and want to be able to boot off it using the eSata port on my motherboard. The problem is that when I try this, I simply get chucked straight into the grub shell, i.e

[B]          GNU GRUB  version 0.95  (637K lower / 1046464K upper memory)

[ Minimal BASH-like blah blah blah....  ]

grub>[/B]

To me, with my limited knowledge of grub, this sounds as though grub can't load its own menu.lst file. I've tried typing things like **root (hdX,Y)** for lots of Xs and Ys but always get:

**Error 21: Selected disk does not exist**

When popping back the hard drive into a normal SATA controller on the motherboard, everything works as expected. I'm a little stuck. I've also tried the grub as part of Gutsy and grub-installed this, but this made no difference. My hardware is as follows:

Motherboard: Asus M2N-SLI Deluxe

lspci lists the JMicron (eSata) controller as:
06:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
06:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)

(I'm not sure what one it's actually using)

Please help!

Marc

---

