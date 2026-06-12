---
title: "[SOLVED] disabling the system beep"
date: 2008-01-14
forum: General Help
---

### Post by charlescarroll1 on 2008-01-14
I've looked through other threads, and I still can't find an answer to my problem. 

Whenever I backspace in the terminal I get a loud system beep from my laptop.  I also get this when I am in the appearance preferences window (change background) and I reach the bottom of the list and press the down key. 

I went to System > Preferences > Sound > System Beep and unchecked the system beep box, yet I still get this annoying beep.

Anyone have ANY suggestions?

---

### Post by Whiffle on 2008-01-14
Your problem is the pcspkr module.  Try 

sudo modprobe -r pcspkr 

and see if it goes away.  If it does, i think you can blacklist the module in /etc/modprobe.d/blacklist

by adding 

blacklist pcspkr

---

### Post by charlescarroll1 on 2008-01-14
Problem solved.

Thanks Whiffle!

---

### Post by Whiffle on 2008-01-14
Anytime :)

---

### Post by tom957 on 2008-02-20
thanks! it's so much better now :)

---

