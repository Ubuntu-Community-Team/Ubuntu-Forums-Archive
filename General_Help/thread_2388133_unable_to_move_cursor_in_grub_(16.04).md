---
title: "unable to move cursor in grub (16.04)"
date: 2018-03-28
forum: General Help
---

### Post by Robbyx on 2018-03-28
For no obvious reason I find that I can not move around the grub on startup. 

As the computer enters the grub stage on startup the usb keyboard light goes off. This means I can not access repair mode in the grub. The direction keys do not work. Probably the keyboard  is not active. Once the boot routine goes beyond the grub options the keyboard comes on again.

uname -r
4.14.30-xanmod27

I want to fsck on my system partition from within repair mode of the grub.

How do I correct the keyboard failing just for during the grub phase of the boot.


Robin

---

### Post by Robbyx on 2018-04-05
Does anyone have a solution?

> **Robbyx said:**
> For no obvious reason I find that I can not move around the grub on startup. 

As the computer enters the grub stage on startup the usb keyboard light goes off. This means I can not access repair mode in the grub. The direction keys do not work. Probably the keyboard  is not active. Once the boot routine goes beyond the grub options the keyboard comes on again.

uname -r
4.14.30-xanmod27


How do I correct the keyboard failing just during the grub phase of the boot.


Robin

---

### Post by cruzer001 on 2018-04-05
That option should be located in your computer BIOS and only arrow keys will work.

Exact wording will vary among computers.

[https://www.google.com/search?client=ubuntu&hs=KMW&channel=fs&ei=6F_GWvTSFcaB0wK52q-4Dw&q=bios+keyboard+settings&oq=bios+keyboard+settin&gs_l=psy-ab.1.0.0j0i22i30k1l9.21190.25694.0.28372.7.7.0.0.0.0.716.3370.0j1j0j1j2j2j1.7.0....0...1.1.64.psy-ab..0.7.3362....0.8Sgg0AHLPWU](https://www.google.com/search?client=ubuntu&hs=KMW&channel=fs&ei=6F_GWvTSFcaB0wK52q-4Dw&q=bios+keyboard+settings&oq=bios+keyboard+settin&gs_l=psy-ab.1.0.0j0i22i30k1l9.21190.25694.0.28372.7.7.0.0.0.0.716.3370.0j1j0j1j2j2j1.7.0....0...1.1.64.psy-ab..0.7.3362....0.8Sgg0AHLPWU)

---

