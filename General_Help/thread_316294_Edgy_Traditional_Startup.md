---
title: "Edgy Traditional Startup"
date: 2006-12-10
forum: General Help
---

### Post by jasonchewy on 2006-12-10
I like the idea of edgy having that ubuntu animation for startup and shutdown...but I still like the traditional linux startup/shutdown with all the things it's loading or terminating.
How do I get that back?
Thanx

---

### Post by tkjacobsen on 2006-12-10
Find this line in your /boot/grub/menu.lst

kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash

and just remove the "splash" option

---

### Post by jasonchewy on 2006-12-10
ahh....and taking out quiet will give you all those crap like before.
nice..
thanx!

---

