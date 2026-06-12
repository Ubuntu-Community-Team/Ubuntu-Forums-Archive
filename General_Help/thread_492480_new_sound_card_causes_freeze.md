---
title: "new sound card causes freeze"
date: 2007-07-04
forum: General Help
---

### Post by creamcheeze77 on 2007-07-04
hi.  i recently set up a dual-boot with windows vista, and due to vista's lack of driver supports, my old sound card no longer worked, so i had to purchase a Sound Blaster Audigy SE.  However, after installing the card, ubuntu now freezes right after the login prompt.  i type my name and password, but then nothing, just a tan screen and a mouse.  i can ctrl alt backspace to get back to the login screen, and ctrl alt f1 just asks me to login again. there seems to be no way to get into the GUI. removing the new card returns Ubuntu to normal.  does anyone have any idea what's causing this, or how to fix it? i was thinking of returning the card (it didnt work in vista either.  the driver installed successfully, and says it's working fine, but i have no sound).  thanks in advance guys.

---

### Post by ubuntu.daemon on 2007-07-04
You need to set up your new sound card as you did your old, that is if you ever did, but if you didnt it just might be that ubuntu is keeping the old settings, so look in the forums for how to install multiple sound cards, bc there is a file you have to edit:  oh found a semi thing which might help
do:
sudo asoundconf list
[example]
Names of available sound cards:
CK804
UART
Audigy2

pick the card you want and:

sudo asoundconf set-default-card Audigy2


lemme kno:popcorn:

---

### Post by creamcheeze77 on 2007-07-05
I tried this, and i tried following the steps at [HTML]http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide[/HTML], and i still have the exact same problem.  i can't even log in to ubuntu. does anyone have a clue what's going on? if i take the sound card out everything runs fine.

---

### Post by creamcheeze77 on 2007-07-06
anyone? :-\

---

