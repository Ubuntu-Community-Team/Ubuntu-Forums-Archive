---
title: "help installing beryl"
date: 2007-01-13
forum: General Help
---

### Post by cptjaben on 2007-01-13
I'm attempting to instal Beryl follow [this guide]("http://doc.gwos.org/index.php/BerylOnEdgy#ATI").  In this section it asks to edit my xorg.conf, but I'm not exactly sure what I should put in for various fields.

```
Section "Device"
	
Identifier "{your card model}" <-do not edit this line in your xorg.conf
Driver "ati"
Option "DRI" "true"
Option "ColorTiling" "on"
Option "EnablePageFlip" "true"
## Some may experience very poor performance without hashing the following line.
Option "AccelMethod" "EXA"
## If above is hashed, change the following to "XAANoOffscreenPixmaps"
Option "EXANoOffscreenPixmaps"
Option "RenderAccel" "true"
#Option "AGPMode" "x" <- x may be 1, 2, 4, or 8 depending on your system
Option "AGPFastWrite" "on"
EndSection	"PCI:1:0:0"
```

I have an ati radeon 9700 pro, what excatly should I write in the identifier field, and how do I find out what to put in for the "AGPMode" field. Thanks much.

---

### Post by Waappu on 2007-01-13
Hi

Don't change what already exists on identifier field. AGPmode is what is your system AGP speed. If you don't know you can try 4. AGPmode option isn't mandatory.

---

### Post by PriceChild on 2007-01-13
And make sure you're using the "radeon" driver... not "ati" or "fglrx"

---

