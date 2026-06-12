---
title: "Graphics Drivers"
date: 2007-03-18
forum: General Help
---

### Post by LilTricky on 2007-03-18
Heyy

Ok im new to linux and ive installed Ubuntu, now when i move or scroll down it scrolls really slowly and bit by bit...its hard to explain that part, but my guess is, its the graphics drivers, ive installed the Ati 8.32.5...(i think thats the number) but now im not tooo sure on how to enable it or use the aticonfig thingy

Someone please help me, wunna use this and Beryl, looks good.

---

### Post by Ocxic on 2007-03-18
type "sudo aticonfig --initial"  and that should get you goin, 

or you cout open /etc/X11/xorg.conf  and change your driver to "fglrx"

or 
"sudo dpkg-reconfigure xserver-xorg"  just accept the defaults, and select fglrx as your driver

---

### Post by r4ik on 2007-03-18
Like you're sig Ocxic,

As an alternative to the install,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

