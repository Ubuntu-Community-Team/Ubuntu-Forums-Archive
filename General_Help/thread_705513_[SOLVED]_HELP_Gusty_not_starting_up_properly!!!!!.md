---
title: "[SOLVED] HELP Gusty not starting up properly!!!!!"
date: 2008-02-23
forum: General Help
---

### Post by nikomax on 2008-02-23
Hey there!

I dont know why but my Gusty install has stopped booting properly. 
Its really hard for me to explain but,

I use grub to select ubuntu.
The splash loads up and goes up like normal.
BUT instead of the gnome login screen I get a terminal login screen.
One thing i have noticed is that the screen flashes every few seconds untill i login in.

I have tried to start gnome by using  sudo /etc/init.d/gdm start  ( Least i think that works ) It comes up saying the process has started but if i try switching to tty7 or anything else for that matter there is nothing!!


I really dont know what has caused this the only difference is a new navida GPU.

Thanks if you cant help

---

### Post by forestpixie on 2008-02-23
that'd be it then - need to reconfigure x for your new card

sudo dpkg-reconfigure xserver-xorg

might be worth checking against the card type to see if anyone's had any other issues with it

---

### Post by nikomax on 2008-02-24
WOOO I love you!!!

:D It worked like a charm.

Good thing too as i had a lot of data i didn't want to lose

thank you!

---

