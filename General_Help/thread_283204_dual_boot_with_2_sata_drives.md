---
title: "dual boot with 2 sata drives"
date: 2006-10-23
forum: General Help
---

### Post by clblanchard on 2006-10-23
Hello all,

I'm having a problem...I'm not that new to Ubuntu, I've had dual boot before but only one one hard drive (several times...I like to experiment:)  Anyway I have a big problem with grub because I can't get it to see the winxp drive:confused: I've seen the tuts about sata+ide but not 2 sata.  So now the only way I can boot into Ubuntu is to either 1) go into the bios each time I boot (super annoying) or 2) unplug the sata cable and physicaly switch them on the motherboard (even more annoying than #1).  Thought maybe some of you very talented individuals could give me a hand.  Thanks in advance.

---

### Post by adrian15 on 2006-10-24
> **clblanchard said:**
> Hello all,

I'm having a problem...I'm not that new to Ubuntu, I've had dual boot before but only one one hard drive (several times...I like to experiment:)  Anyway I have a big problem with grub because I can't get it to see the winxp drive:confused: I've seen the tuts about sata+ide but not 2 sata.  So now the only way I can boot into Ubuntu is to either 1) go into the bios each time I boot (super annoying) or 2) unplug the sata cable and physicaly switch them on the motherboard (even more annoying than #1).  Thought maybe some of you very talented individuals could give me a hand.  Thanks in advance.

Have you tried to add the map commands inside menu.lst or not... like this:

```

title mywin
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1)
chainloader +1
boot

```

adrian15

---

### Post by clblanchard on 2006-10-24
I have tried that, but for some reason no matter what I put for the map it doesn't work.  I've even tried sda, sdb etc... because of sata.  I think I'm just going to reinstall it and let it put grub on the mbr of windows.  I have a friend I work with and he says it's how he got his to work.  But I really wanted a completely seperate universe for ubuntu.

---

