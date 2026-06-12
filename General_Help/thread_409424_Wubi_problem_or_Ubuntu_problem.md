---
title: "Wubi problem or Ubuntu problem?"
date: 2007-04-14
forum: General Help
---

### Post by danbutter on 2007-04-14
Just wondering if my issues are Wubi related or just plain ubuntu related.

I have a bluetooth mouse that I use and can get it going and it works great, but I have to run a command in a terminal every time I start the computer up to get it working.

Sorta the same issue with wireless.  
Not every time...sometimes it will remember it, but other times it wont and I need to go through the entire process of setting up a new wireless network to get back on.
Also sometimes when I go to set up a new wireless network it will only have WEP available to use and I use WPA2 so I can't even get it working at this point.

So does anyone think this is related to Wubi in and of itself?  OR Are these things ubuntu problems in general?

Any input is appreciated.
Thanks

---

### Post by ago on 2007-04-14
It should not be a wubi issue. Anyway, it's fairly easy to run things at startup or load some special modules.

---

### Post by myoldryn on 2007-04-14
for mouse:
sudo gedit /etc/default/bluetooth  and there change option HIDD_ENABLED=0 to 1.
As far as i know the networkmanager works with wpa only with some wifi chipsets. For more information see [http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware)

---

