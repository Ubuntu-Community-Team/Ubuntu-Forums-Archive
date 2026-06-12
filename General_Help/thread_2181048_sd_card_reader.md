---
title: "sd card reader"
date: 2013-10-16
forum: General Help
---

### Post by Brotell1950 on 2013-10-16
How can I get my HP650 to read my sd card.

Terry

---

### Post by sanderj on 2013-10-16
... put it in your computer, and watch dmesg

---

### Post by Brotell1950 on 2013-10-16
card goes in but is not recognised by computer.

Terry

---

### Post by sammiev on 2013-10-16
Try to plug it into your computer and then boot. It may pick it up on startup.

---

### Post by Brotell1950 on 2013-10-16
Tried that still no joy

Terry

---

### Post by Dennis N on 2013-10-16
If all else fails, try a USB card reader for SD cards. In my case, I bought an inexpensive Targus (brand) SD card reader. It reads many card sizes. Plug it in and it always works. Very inexpensive gadgets - many brands, generally less than $10 U.S.

---

### Post by tgalati4 on 2013-10-17
Open a terminal:

```
lspci | grep Mass
```

It should look something like:

tgalati4@Mint14-Extensa ~ $ lspci | grep Mass
0f:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

If you don't see anything, then boot into BIOS and make sure the card reader is turned on.  Use a torch and check to see there is no Vegemite stuck in the slot.

---

