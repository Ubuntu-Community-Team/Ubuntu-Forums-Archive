---
title: "Improving mouse speed?"
date: 2007-04-25
forum: General Help
---

### Post by Bliz0r on 2007-04-25
Hello, I'm used to a very high sensitivity, and even when I've maxed the mousespeed and acceleration it's still too slow. Are there any way that I can improve the speed alot more than just  the mouse preference?

---

### Post by aidanr on 2007-04-25
what mouse? with logitech mice you can increase the dpi with lomoco

---

### Post by Bliz0r on 2007-04-25
Ah, sorry, I should of told you what mouse.. Logitech mx510 :)

---

### Post by strabes on 2007-04-25
Sorry for the non-answer, but do you have all of the buttons on that mouse working under linux? If so, care to explain how? I'm thinking about purchasing a logitech mouse and I'm looking for as much information as I can get about their linux functionality.

---

### Post by aidanr on 2007-04-25
ok, so install lomoco (it's in the repos)

then type in a terminal
```
sudo lomoco -8
```
and that'll be faster

you can have that automatically done on each boot by doing the following

```
sudo visudo
```
add
```
%admin ALL=(ALL) ALL, NOPASSWD:/usr/bin/lomoco
```
and then adding
```
sudo lomoco -8
```
to system -> preferences -> sessions

---

### Post by aidanr on 2007-04-25
strabes, the gentoo wiki has some good info about that
[http://gentoo-wiki.com/HOWTO_Advanced_Mouse/Individual_Configurations#Logitech_MX510.2C_MX518.2C_MX900](http://gentoo-wiki.com/HOWTO_Advanced_Mouse/Individual_Configurations#Logitech_MX510.2C_MX518.2C_MX900)

---

### Post by Bliz0r on 2007-04-25
Thanks alot, was just what I needed. :)

---

