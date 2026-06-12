---
title: "GRUB losing commands"
date: 2007-04-21
forum: General Help
---

### Post by SethP on 2007-04-21
I have two copies of GRUB installed on my system (one on hd0/hda1, and the other on hd1/sda1), to ensure that no hard drive is too dependant on the other. The commands I use to swap between one and the other are:

```

rootnoverify (hd0) # or hd1, depending
chainloader +1
boot

```

The odd part is that on hd1, the rootnoverify line gets lost somewhere between my menu.lst file and the actual bootup. Anyone know how to resolve this?

---

### Post by SethP on 2007-04-23
Sorry to reply to my own post, but hopefully someone can learn from my stupidity. Turns out instead "rootnoverify (hd0)" I had typed "rootnovery (hd0)". It seems grub just ignores whatever lines in menu.lst it doesn't understand :oops:

---

