---
title: "LiveUSB booting to black screen"
date: 2014-09-21
forum: General Help
---

### Post by quadrplax on 2014-09-21
I have made a lubuntu 14.04.1 LiveUSB to and am trying to use it on my Dell Dimension 4550. The first time I tried to boot it and selected "Try lubuntu without installing" it gave me an error that started something like this: "Kernel panic - not syncing: Fatal exception in interrupt". I wish I had written the whole thing down, it was taking up most of the screen. Also, the scroll lock and caps lock lights were flashing. Now, whenever I try to boot to install lubuntu or try lubuntu I just get a black screen. I can still run a memtest. I can still interact with the caps lock, num lock, and scroll lock keys on the black screen. My best guess would be that it's related to the graphics card: Nvidia GeForce4 MX 420. There's no built-in graphics I can test off of, and the menu where you select how to boot works fine, albeit not at my monitor's native resolution. Any good way to solve this?

---

### Post by yancek on 2014-09-21
When you see the first menu, hit the e key on your keyboard.  You should see some code and a line beginning with linux.  Use your mouse arrow keys to go to the end of that line, hit the space bar once and type:  nodmodeset  There should be a message at the bottom telling you which key to hit to exit the menu, I think it's F10 but check.

---

### Post by ajgreeny on 2014-09-21
> **yancek said:**
> When you see the first menu, hit the e key on your keyboard.  You should see some code and a line beginning with linux.  Use your mouse arrow keys to go to the end of that line, hit the space bar once and type:  nodmodeset  There should be a message at the bottom telling you which key to hit to exit the menu, I think it's F10 but check.
That info is for an installed system, not a live system as far as I'm aware, but on the first screen after booting to the USB you sghould be able to hit F6 and there choose the various boot-options available.

As yancek said, nomodeset is the first one to try, but if that does not work try the others one by one.

---

### Post by Mike_Walsh on 2014-09-21
Elderly Dells can be a RIGHT pain in the proverbials. I have a truly ANCIENT Inspiron 1100 laptop which came with Win XP, nearly 13 years ago. The Intel 'Extreme' graphics chipset has given me a REAL headache; you try to install something like Lubuntu (best distro for an old 'brick' like that, by a country mile), and, although it installs OK, you end up with a 640x480 display jammed into the top left corner of the screen, and can't do anything with it. NOBODY has any ideas as to how to fix it; and there's nothing on the sticky in the General Help forum that works, either. 'Nomodeset' doesn't do anything except move the tiny display into the middle of the screen..!

The only way I've been able to make it usable is to install Lubuntu to USB flashdrive with UNetbootin, and basically run it as a PERMANENT 'Live' session.....the screen seems to work in full resolution when I do that, 'cos it must be running off the default Linux drivers. At least I can still use the small (20 Gb) hard drive for storage this way... ;) 

There does appear to be a Linux driver for the chipset, but it's a horribly long, convoluted process to install it (according to Intel's notes); and for an old 'lappie' that's only a basic back-up system, it just isn't worth the effort it would take.  I'M happy to use it like that.....it DOES at least work!

It's not the fault of the OS, certainly. Dell were well-known for using some very odd combinations of hardware over the years (!); but when all's said and done, the 'brick' has served me well during that time. Dell DID build 'em to last in those days (this thing's built like a tank!), and it's still got the best keyboard I think I've ever used; that alone is one reason I'm loathe to put the old girl out to pasture... :p

Regards,

Mike.

---

### Post by quadrplax on 2014-09-22
nomodeset worked fine...except now I can't go above 1024x768.

---

### Post by quadrplax on 2014-09-25
So, should I go ahead and install it with the 1024x768 issue, or deal with that now?

---

