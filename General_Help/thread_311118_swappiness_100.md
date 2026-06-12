---
title: "swappiness 100"
date: 2006-12-02
forum: General Help
---

### Post by veli on 2006-12-02
I was playing with the swappiness thing a bit. I tried with 0, 10, 15 and 60 (the default). Yesterday I decided to tried with 100. 

I don't know, but I've got the feeling that my system is more responsive with 100 setting. especially when I'm working with large ppt presentations, a couple of pdf opened in Evince, as if it's running smoother. I didn't measured application load times or other benchmarks. I'm gonna run the system for a couple of days with 100 setting and see the performance.

Likely, the guy from kernel dev, is right?
[http://kerneltrap.org/node/3000](http://kerneltrap.org/node/3000)

My comp is PIII, 256 RAM, 512 MB swap, kernel 2.6.18 on Dapper.

---

### Post by az on 2006-12-02
That is correct, but your mileage may vary.  It depends on whether your system will spend more time caching stuff that the time you save by reading it back from swap.  It depends on a lot of things, like how slow your disks are, what kind of useage, how much ram, etc...

---

