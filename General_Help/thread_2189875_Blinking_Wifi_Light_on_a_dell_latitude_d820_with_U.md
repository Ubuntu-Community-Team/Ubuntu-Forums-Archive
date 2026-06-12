---
title: "Blinking Wifi Light on a dell latitude d820 with Ubuntu 13.10"
date: 2013-11-24
forum: General Help
---

### Post by worleylevi on 2013-11-24
Hi everyone,
I am dual booting Ubuntu 13.10 and windows 7 but the wifi light is always blinking. I am fairly good with ubuntu but this is starting to annoy me.



Thanks in Advance,
Levi
Dell latitude d820
3gb ram
500gb hard drive
Dual boot windows 7 and ubuntu 13.10

---

### Post by varunendra on 2013-11-26
Is the wireless working? Blinking on activity can be an intentional behaviour caused by some drivers, which is not always controllable (e.g. in ath5k).

Please post the output of -
```
lspci -nnk | grep -iA2 net
```

If the wireless is not working, then instead of above output, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by VinDSL on 2013-12-03
Supposedly (according to posts on Launchpad) this 'problem' is actually a kernel feature.  Whatever.

I own a Dell Latitude D620.  The LED light doesn't blink on Ubu 14.04 with a Linux 3.13-rc2 kernel.

I also own a Dell Latitude D630 ATG. The LED light DOES blink on Ubu 14.04 with a Linux 3.13-rc2 kernel.

The difference between these two laptops is:

[LIST]
[*]The Dell D620 has a Dell Wireless DW1390 mini-card (no blinking)
[*]The Dell D630 ATG has an Intel Wireless Pro 3945abg mini-card (non-stop blinking)
[/LIST]

The 'fix' for the D630 was to swap its 3945 wifi card with the 1390 wifi card from the D620.

Put another way, the 3945abg blinks, and the 1390 doesn't.

BTW, I just bought a new 1390 on Ebay for $3.00 with free shipping.  I'll put it in my D620 and throw the 3945 on the junk pile.

Problem solved... :D

---

