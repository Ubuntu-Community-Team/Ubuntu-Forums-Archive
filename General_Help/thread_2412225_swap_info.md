---
title: "swap info"
date: 2019-02-09
forum: General Help
---

### Post by j3984 on 2019-02-09
18.04 has a swap file instead of a swap partition...from what I understand... If I have extra space on the SSD would it hurt to create a 9 gig swap partition anyway???
I am not needing most of my SSD. this is for a new install ..

---

### Post by CatKiller on 2019-02-09
It won't hurt, but it won't particularly help, either.

---

### Post by oldfred on 2019-02-09
If you want faster system add more RAM. 
Swap, even on SSD, is orders of magnitude slower than RAM.
So you do not want system to ever use swap. My older system with only 4GB of RAM almost never used swap.

And Linux uses all of RAM.
       Linux ate my RAM! -  memory use cache
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by HermanAB on 2019-02-10
A swap partition is no better than a swap file.  All the details are explained nicely in 'man swapon'.

---

### Post by j3984 on 2019-02-10
I guess I will skip swap partition. I have 8 gig ram.

---

