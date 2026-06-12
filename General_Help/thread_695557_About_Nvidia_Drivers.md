---
title: "About Nvidia Drivers"
date: 2008-02-13
forum: General Help
---

### Post by JisgorE on 2008-02-13
hello reader!!,

im new to ubuntu and the forums, this is my first time running ubuntu 7.10 and i noticed under Administration-->Restrcicted Drivers manager there is and Nvidia option to enable drivers, so the question is if i enable those will i be able to use beryl or do i still have to install the drivers from another source.

thanks for your answears. have a great day.

---

### Post by njparton on 2008-02-13
Feel free to do that, or I use 'envy' to install my nvidia drivers.

Google 'envy ubuntu' to find out more.

Make sure you use the 169.09 drivers or later as earlier drivers have a fan speed bug that will cause your ears to bleed!

---

### Post by kpkeerthi on 2008-02-13
Beryl has now become Compiz(Fusion). Ubuntu has Compiz fusion installed by default. You need to enable nvidia driver in restricted driver manager (or install envy) and then choose System -> Preference -> Appearance -> Visual Effects to enable Compiz. 

You need Compiz Config Settings Manager (search and install using Synaptic), if you need to tweak the settings.

---

### Post by JisgorE on 2008-02-13
thank you for the help, is working perfectly and actually the compiz fusion is more organized.......

I have this other problem that i tough it wll be solved once i installed the nvidia drivers, everytime a login or logout i get a screen saying "cannot display this video mode" i beleive that what it should be there is the ubuntu loading screen, i looked in the forums but i only found solutions for ATI cards, can anyone help me out, is actually not an issue right now but i know that soon it will become one....lol, plus i see that i can't put the refresh rate higher that 55.....

Thanks again for the help..

---

### Post by njparton on 2008-02-13
You may need to delve into the "xorg.conf" file and change some settings.  Search the forum for help on X settings.

You can find it at:

/etc/X11/xorg.conf

reboot or restart x afterwards to apply the settings.

---

