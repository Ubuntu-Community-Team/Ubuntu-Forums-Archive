---
title: "Another CPU problem"
date: 2008-01-10
forum: General Help
---

### Post by blackenedbloodx on 2008-01-10
What's up. My CPU is averaging about 90% usage when doing nothing. there is serious lag and my fan is louder than a mutha. any options?

Gutsy 7.10
Pentium 4 - 3.2GHZ
2GB RAM
256 MB GPU
430 Watt PSU

---

### Post by rfruth on 2008-01-10
Do any folding ? both cores of my AMD x2 are near 100 percent :)

---

### Post by blackenedbloodx on 2008-01-10
what do u mean by folding???? and damn u and ur AMD!!! i want an athelon... >.>

And also would you know anything about how to do this?

i see links do download programs but all it is a page with a bunch of letters and numbers, PGP code. how exactly do i run that?

---

### Post by rfruth on 2008-01-10
run "top" & see whats eating up your CPU, see my sig for folding@home stuff :)

---

### Post by blackenedbloodx on 2008-01-10
...yea i looked at that before... but im the biggest linux noob srry i have no idea what it is :P

it says User:root and command:kacpid.

---

### Post by rfruth on 2008-01-10
Forget folding@home for now, need to figure out whats eating up all that CPU time, what says user:root ? (here is my top without folding running) 

[ATTACH]56018[/ATTACH]

---

### Post by blackenedbloodx on 2008-01-10
its at the top of top lol and from your pic i see you gots a Randy Rhoads open? right on man i gots the flying V RR3 from his line :D

[http://i209.photobucket.com/albums/bb159/Neofountain/toproot.png](http://i209.photobucket.com/albums/bb159/Neofountain/toproot.png)

---

### Post by blackenedbloodx on 2008-01-11
ok i have narrowed it down to kacpid, i put in my boot/grub/menu.lst and i put   asci=off and apm=off. that works. but now i cant seem to detect my home wireless connection. there is a signal for the one near me but i dont have the password. i even tried to connect to it manually. it doesnt recognize it. please help!

---

