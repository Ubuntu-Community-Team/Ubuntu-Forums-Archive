---
title: "HELPPP!!!! NO display!!!"
date: 2007-11-01
forum: General Help
---

### Post by kdarkentity on 2007-11-01
Today i used an s-video cable to connect my laptop to my hd-tv and when i did so i changed my display settings and i think i might have switched my display driver by accident. Soo now when i boot into linux Gdm starts up, however i have no display, all i see is a little blinking dash at the to left of my screen, and when i boot into safe mode and run gdm my screen blinks 3 times and all i see is the text still, what do i do?

---

### Post by Pumalite on 2007-11-01
sudo dpkg-reconfigure xserver-xorg
(Ctrl+Alt+F1 to get command line)

---

