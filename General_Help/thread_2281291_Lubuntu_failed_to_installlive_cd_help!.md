---
title: "Lubuntu failed to install/live cd help!"
date: 2015-06-06
forum: General Help
---

### Post by Aetherite on 2015-06-06
I have an old laptop.  it has:
intel celeron M @ 1.2ghz
780ish mb of ram

its called dynabook c7/212cmhn

it currently run windows XP

when i inserted the lubuntu (i've tried lubuntu 14.04, and 15.04, both failed D[IMG]http://m.bestofmedia.com/sfp/images/design/usr/smilies/smile.gif[/IMG] , i am able to select language, then i hit either *try without install* or install

then i see APCI probing failed

then after a while of loading i get
[103.167632] ali1535_smbus 0000:00.  can't enable device BAR 13

`` `` can't enable device

`` `` region uninitialized. upgrade bio or force_addr=0xaddr

`` `` module not inserted

then i see black screen and i need to restart my laptop

please help!

---

### Post by sudodus on 2015-06-06
Welcome to the Ubuntu Forums :-)

Your computer is old and there may be problems to get a new operating system working with it. See this link for general recommendations
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]


***1. Continue trying with Lubuntu:***

Try with some boot options!

 See this link how to enter boot options [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I suggest that you start trying with the following three boot options (all of them or one or two each time)

```
acpi=off forcepae nomodeset
```

[I][B]
2. Try some other light-weight linux distro,[/B][/I] that is even lighter than Lubuntu or that might have drivers for the hardware in your old computer:

***ToriOS, Wary Puppy, TahrPup, Tiny Core***. You find them easily via the internet.


***3. LXLE and Bodhi*** are not lighter than Lubuntu, but if you try the versions that are based on Ubuntu 12.04 LTS, there might be drivers for your hardware.

---

