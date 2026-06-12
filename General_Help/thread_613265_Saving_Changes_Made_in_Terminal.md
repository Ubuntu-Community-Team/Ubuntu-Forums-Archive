---
title: "Saving Changes Made in Terminal"
date: 2007-11-14
forum: General Help
---

### Post by kevo214 on 2007-11-14
First off, in order to get my wireless card to work with Ubuntu but I had to do a lot of fiddling with different things and whatnot (adding drivers from windows and blah). However, everytime I want my wireless card to work I need to run the commands 
> sudo depmod -a
sudo modprobe ndiswrapper
in the terminal. I want to know if there's a way I can have these commands run at startup so I don't have to go into the terminal and enter them everytime. I also have to do this with rmmod pcspkr command to shut that beep off.

---

### Post by scorp123 on 2007-11-14
Put those commands into this file:  **/etc/rc.local**  .... before where it says "exit 0"

---

