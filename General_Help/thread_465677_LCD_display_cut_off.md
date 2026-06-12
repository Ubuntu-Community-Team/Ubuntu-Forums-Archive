---
title: "LCD display cut off"
date: 2007-06-05
forum: General Help
---

### Post by dentarthurdent on 2007-06-05
When I try to load games that aren't installed by default (eg. wesnoth, lincity, neverball, supertux, etc), , there is a display problem that is sort of hard to describe; the screen splits in half and repeats itself, such that i can't see what is on the right side.

i had a similar problem when installing 7.04 on the same machine (Dell Inspiron 4000 = Pentinum III 700, 512Mb RAM, ATI Rage Mobility); the screen was in thirds. I found a thread that helped that time, which had me add the line HorizSync 28-100 to xorg.conf.

should i change these values to something else? is my machine just not capable of running these games? do i need to install some proprietary graphics driver? thanks!

---

### Post by dentarthurdent on 2007-06-06
hi! just bringing the thread back to try to get some help!

---

### Post by dentarthurdent on 2007-06-07
ok, read some Fedora core forums and someone had the same problem, same machine. problem was solved by changing the default depth to 16. hopefully this helps others!

---

