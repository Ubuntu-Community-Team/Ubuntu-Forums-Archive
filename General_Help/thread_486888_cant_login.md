---
title: "cant login"
date: 2007-06-28
forum: General Help
---

### Post by Denn1s on 2007-06-28
i was folowing this guide to speed up feisty:

[http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/](http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/)

and the next time i tried to log in to ubuntu my computer would send me to an extremely minimalistic desktop environment with only one terminal, if i close it the sistem would go to the user login screen, if i close it in les than 10 seconds a warning will promt askin me to check .xession-errors in my home, the file said something about access denied to /dev/null, so i thought about doin 

$ sudo chmod 666 /dev/null

and then i can log in, i trace back wath i did when folowin that guide with no change, how can i log in normaly again? thanks for ur help everyone

---

### Post by mouseboyx on 2007-06-28
Try:
```
sudo apt-get install gnome
```then choose the gnome session from the options

---

