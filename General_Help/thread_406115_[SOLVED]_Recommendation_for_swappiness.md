---
title: "[SOLVED] Recommendation for swappiness"
date: 2007-04-10
forum: General Help
---

### Post by FuturePilot on 2007-04-10
I have a laptop with 768MB of RAM, and that seems to be more than enough, but for some reason after a while I start using swap with a little over 600MB in cache. Does it really need to swap with all that in the cache? So I want to adjust the swappiness. What would be a good setting? I was thinking of vm.swappiness=20
Any suggestions?

---

### Post by FuturePilot on 2007-04-10
Anyone?

---

### Post by heimo on 2007-04-11
Well. experiment with values 0 and 100 - couple days for each, and tell us the difference between swap usage. :)

---

### Post by FuturePilot on 2007-04-11
Thanks, I've got it set to 20, I'll see if I'm using any swap in the morning after leaving it on tonight.:)

---

### Post by pingpongboss on 2007-04-11
most guides say 0 - 10 for 1 gig of ram. so i'd say ur value is about right

---

### Post by FuturePilot on 2007-04-12
Ok, so 20 didn't make a difference so I put it to 0 and it made a big difference.:)

---

### Post by whatshisname on 2008-02-16
This is one trick that did not work for me.  I'm running Mepis 6.5 32.

If you're going to play with this, make sure you change it from the command line with:

sysctl -w vm.swappiness=nn

Unfortuately, I edited /etc/sysctl.conf, forgot about the tweak and then suffered for a month before realizing what I had done.

---

### Post by galileon on 2008-05-20
how exactly did you suffer? i set mine to 10 using the console right now, and  my system is flying!

---

