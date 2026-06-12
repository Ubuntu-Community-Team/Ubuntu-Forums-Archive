---
title: "Installing Nvidia driver"
date: 2007-01-11
forum: General Help
---

### Post by OneOfaKindDPC on 2007-01-11
First off thanks to all who help me out on this. I'm very new to linux, but I'm sick of Bill gates taking all my money and doing a bad job with it.





I'm trying to install the Nvidia geforce driver, I'm running Ubuntu 6.10. I finally figured most of it out. I was able to figure out who to get into the root, close the gui and x server, even got the darn program to run. 

Here's my problem  (its ok to laugh)

The disclaimer for the installer pops up and it asks me to accept or decline........ how the heck to I "push" accept to move forward? I hit enter but it just makes the cursor blink in the middle of the screen til I hit enter again and then brings me back to prompt.


I renamed the .run file to nvidia.run (make it easy for me lol) the command I used was 

sh nvidia.run


Where'd I go wrong?


Thanks for the help again

---

### Post by bodhi.zazen on 2007-01-11
That's sooooo old school vintage nvidia

Try Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Go for the Latest, beta driver. It is just fine re: stability and will give you better gui for monitor configuration (including dual monitors).

Just run ```
nvidia-settings
``` in a terminal :)

If you must, follow this link:

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by dabl on 2007-01-11
I also used the site bodhi pointed to, for the latest Nvidia driver, and I would characterize that driver as MOSTLY stable & fine, running on my Kubuntu Edgy system.

- The "autodetect" feature of overclocking does not work correctly on my 7900GS/PCI card

- Beryl can be made to work, with some tweaks, but not under Kubuntu with Aquamarine as a Window Decorator. Emerald works fine as the Window Decorator.

Your mileage may vary ...

:cool:

---

### Post by OneOfaKindDPC on 2007-01-11
thank you guys, did the trick :-D

---

### Post by OneOfaKindDPC on 2007-01-11
ok guys, new problem now....

I wanted to do the nvidia update in hopes it would allow me to change my resolution to something higher then 800 x 600 at 60hz. I normally run 1680 x 1050 at 60hz. Since the update I can only get it up to 1024 x 768 but here's the kicker 60 hz is not an option anymore and it has me set for 75hz.


Where do I go from here to get it to where I would like to be?


Thank again!

---

### Post by OneOfaKindDPC on 2007-01-11
Nevermind, figured it out :D

---

### Post by bodhi.zazen on 2007-01-12
post your xorg.conf

---

