---
title: "AT-SPI: Could not obtain desktop path or name"
date: 2017-03-14
forum: General Help
---

### Post by bkline on 2017-03-14
I've got a fresh install of Xubuntu 16.10 and every time I launch emacs the console window from which I run the editor fills up with (many times over) with dozens of the same warning message:

```
** (emacs:20614): WARNING **: AT-SPI: Could not obtain desktop path or name
```

It's not a fatal error, but it's pretty annoying to have to scroll back through all the warning all the time to see what was in the console window. Googling isn't turning up much beyond a handful of others who are experiencing the same behavior but not getting any useful information telling them what's going on. Anyone have any clues?

---

### Post by bkline on 2017-03-15
Responding to my own post (a little disappointed that no one on Ubuntu Forums -- which used to be the most valuable go-to resource for Ubuntu users -- had any insight to offer). I compared packages between two machines -- this one and another which did not exhibit this behavior -- and I saw that the other one had the gnome package installed and this one didn't. So I ran sudo apt install gnome on the new Xubuntu machine. I was dismayed to see how many additional packages (543!) this dragged in. Sort of defeats the purpose of using Xubuntu for its lighter footprint. But it appears to have solved the problem, as I can run emacs without my terminal window flooding with the same AT-SPI warning over and over. If anyone has a less drastic way I could have solved the problem, I'd be most grateful. Or if there's a more appropriate set of forums for asking such questions these days, please let me know.

Thanks.

---

### Post by 3togo on 2017-09-16
"sudo apt install gnome" won't help. But I am with you, it is a very annoying warning issue.

---

### Post by anshumankmr on 2018-08-22
Hello sir ,  I am running Ubuntu 18.04 and I have the same but with nautilus and gnome apps like the terminal and clockl

---

