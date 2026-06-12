---
title: "3d acceleration question"
date: 2006-11-16
forum: General Help
---

### Post by dbbolton on 2006-11-16
i'm trying to get beryl working by following this howto: 
[http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome](http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome)

it says:
> First make sure you have 3d acceleration available in a normal gnome session.
There are lots of howtos for this , Google if you need any help with that.
So if glxinfo shows direct rendering: yes , then you are good to go.
If not xgl and Beryl wont work!

google did not help me. i know one of the gurus in this forum can, though.

i have ATi Radeon XPress 200M (AMD Turion64)


thanks dudes.

---

### Post by eXisor on 2006-11-16
Just type 'glxinfo' in a terminal. If the result shows 'direct rendering yes', you're good to go.

I do not have an ati x200 card, but I recall seeing a few posts around here where beryl and that specific card are mentioned. If I recall correctly, the Edgy aiglx drivers do work, but there is some xorg.conf 'device' section parameter tweaking required to get.

Best thing to do is to give it a go.

Edit: I just did a search om x200m and found severasl posts saying the inbuilt aiglx drivers do not work with dri, and worse, the latest ati proprietary drivers (using fglrx instead of aiglx) don't either.

Seems you're OOL.

---

