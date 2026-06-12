---
title: "So many bugs"
date: 2013-04-11
forum: General Help
---

### Post by KiD4EvA on 2013-04-11
Hi there new to ubuntu! 
So recently installed ubuntu over a skype call which I was very impressed how easy it was and you can do it using a memory stick! Sadly though, about three days ago I installed an automatic update which has led to so many bugs/problems:

-Ubuntu sometimes just randomly logs out(no known intervals)
-Youtube often crashes saying plugin has failed
-Minecraft window crashes very often(when i open it and just random intervals)
-Random times I get a black screen with loads of white writing(don't understand it)

There others but not of the top of my head, 
Much appreciated for any help
Tim

---

### Post by sanderj on 2013-04-12
In Ubuntu open a terminal, and type:

```
df -h
uname -a

```

and post the output here

---

### Post by KiD4EvA on 2013-04-12
Its in the attachment :)

---

### Post by sanderj on 2013-04-12
I thought you were running from memory stick? Not so ... you installed to harddisk. That's good.

If Ubuntu is unstable, reboot it and choose "memtest86" from the boot menu, and leave memtest running for a few hours. If there is any error, you've found the cause ...

---

### Post by KiD4EvA on 2013-04-12
Im guessing that you boot memtest86 via the bios any tips on how?

---

### Post by Locus Kiesselbachi on 2013-04-12
memtest via grub. Restart, hold shift after POST (the beep at the beginning), that should take you to grub.

reminds me that my rig-s HDD died right after I put Linux on it. :)

---

### Post by sanderj on 2013-04-13
> **KiD4EvA said:**
> Im guessing that you boot memtest86 via the bios any tips on how?

No, not BIOS. It's in the same GRUB menu that shows Ubuntu (and other operating systems on your harddisk as seen by GRUB)

---

