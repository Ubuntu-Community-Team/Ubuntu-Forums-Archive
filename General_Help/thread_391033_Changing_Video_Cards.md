---
title: "Changing Video Cards"
date: 2007-03-22
forum: General Help
---

### Post by ComputerGuy56 on 2007-03-22
I had to change my video card to get Ubuntu to not get the X Server thing. I need to get my other Video Card as it speeds up my computer a whole ton.

---

### Post by fragos on 2007-03-22
Are you asking for help?

---

### Post by hikaricore on 2007-03-22
```
sudo dpkg-reconfigure xserver-xorg
``` ?

---

### Post by ComputerGuy56 on 2007-03-22
It says to find out which PCI number(I don't know what it's called). I tried```
lspci -X
```
But that didn't even exist. I tried ```
lspci -x
```
That doesn't tell me what number though. Main Question: How do I find my PCI card number thing?

---

### Post by ComputerGuy56 on 2007-03-23
How do I find the PCI slot my Video Crad is in? (Example: PCI:0:16:0) I can't seem to find which slot my new Video Card is in:confused:

---

### Post by fenian on 2007-03-23
when you do the lspci -x command it gives you an output like...


> 01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1)
00: de 10 21 02 06 01 b0 02 a1 00 00 03 00 f8 00 00
10: 00 00 00 fd 08 00 00 d0 00 00 00 fc 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 60 00 00 00 00 00 00 00 0b 01 05 01

the 01:00.0 at the begining is the PCI bus number, I think thats what you need to use.

---

### Post by ComputerGuy56 on 2007-03-25
Thanks, I was looking at the wrong part.

---

