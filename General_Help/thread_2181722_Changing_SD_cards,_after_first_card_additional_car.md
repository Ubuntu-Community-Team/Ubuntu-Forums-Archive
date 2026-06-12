---
title: "Changing SD cards, after first card additional cards are not recognized"
date: 2013-10-18
forum: General Help
---

### Post by oregonbob on 2013-10-18
I have ubuntu 12.04 running standard Unity. I often import SD cards from my cameras. When I insert the first card everything is fine, it is recognized, etc. But after ejecting the first card, additional cards are not recognized. I have to reboot to fix it. Even logout/login does not get it.

---

### Post by tgalati4 on 2013-10-18
Do  you "eject" or "unmount" the SD card before physically ejecting it?  If not, then you can leave the card slot in an indeterminate state.

(I presume that you are already doing this correctly.)  Right click-->Eject on the SD card icon on the desktop  or the unmount/eject (up-arrow symbol) in Nautilus.

Right after ejecting the SD card, open a terminal and post the following:

```
dmesg | tail -40
```

Only post the SD-related stuff.

---

### Post by oregonbob on 2013-10-18
I right-click the icon for the SD card in the task/menu bar and select "eject". It appears to eject OK as the icon then disappears.

---

