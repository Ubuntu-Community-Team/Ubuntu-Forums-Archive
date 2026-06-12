---
title: "graphics problem - nvidia"
date: 2017-05-30
forum: General Help
---

### Post by jaarvidsen on 2017-05-30
hi, im using ubuntu gnome 17.04 64 bit, skylake 6700 and gigabyte nvidia gtx 1070 and the 375 drivers. also tried the newer drivers from the ppa, but the results are identical
i have a problem with graphics when i scroll or move see this screenshot: [http://i.imgur.com/De9TG9e.png](http://i.imgur.com/De9TG9e.png)
the ace of spades im moving to the left, it half disappears. in corebird im just scrolling

im not even sure what this is called as english is not my first language so i dont even know what to search for.

ive trid adding
CLUTTER_PAINT=disable-clipped-redraws:disable-culling
CLUTTER_VBLANK=True
to /etc/enviroment but that just makes things a lot worse, with artifacts displayed everywhere on my desktop when trying to move a window

any help appreciated, if even just telling me what this 'effect' is called so  i know what to search for

thanks

---

### Post by jaarvidsen on 2017-06-03
Bump

---

### Post by Autodave on 2017-06-03
Before you scroll, does the screen look OK?  Assuming this is a desktop, how is the monitor connected to the PC: VGA, DVI, HDMI?

---

### Post by jaarvidsen on 2017-06-03
yes all is fine before i scroll. its connected via displayport. ive tried hdmi too, same thing

---

