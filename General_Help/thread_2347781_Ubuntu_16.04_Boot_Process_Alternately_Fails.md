---
title: "Ubuntu 16.04 Boot Process Alternately Fails"
date: 2016-12-28
forum: General Help
---

### Post by jonathan81 on 2016-12-28
My Ubuntu 16.04 machine alternately boots, or freezes during boot. Problems started occurring after installing NVidia Proprietary drivers.


When it freezes:


 - My GRUB screen appears as a blank purple screen. I do not see any menu items. This uggests that it is related to my gfx card.
 - After the grub screen I get a hires Ubuntu startup screen asking me to unlock my HD, as I encrypted it... The screen reads "Please unlock disk sda5_crypt".


When it works:


 - I get a GRUB screen with menu items.
 - The "Please unlock disk sda5_crypt" screen is in lowres. Perhaps 640x480.


The machine alternates consistently between booting and not booting.


When frozen, I can use CTRL+ALT+F1 to F7 to go the the tty's, but while I can type text and press enter, none of the commands get executed. The cursor blinks.


Through pressing lots of keys, I have discovered that I can may sysrq appear by pressing Super+Print Screen.


How can I further debug why my machine alternately boots and freezes during boot? I think it is something to do with nvdia, but am not sure.

---

