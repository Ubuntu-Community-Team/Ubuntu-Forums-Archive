---
title: "Order of autostart programs in session"
date: 2007-02-13
forum: General Help
---

### Post by MasterZ on 2007-02-13
Hello,

I wanted to make my conky startup after beryl when I log on in gnome, but I did not find a way to modify the order of my session startup programs. 

I made a script which 'sleep 10' before starting conky, but it's not very clean. 

Is there a way to define an order for the session startup programs ? :confused: 

Thanks, 

MasterZ

---

### Post by sagara on 2007-03-31
I had a similar issue were I needed beryl to start after a certain program.  No matter what I tried in the session manager it seems you can't force any order in it.

Writing my own startup script and setting **sleep**s in between was the only way to get around this.

It aint the cleanest solution like you say, but it gets the job done : )

---

### Post by tuxalot on 2008-03-01
Hardy Heron has a nice feature to accomplish just what you're mentioning.  Perhaps other releases do as well (I'm still figuring things out in the Linux world).  See attached screen.

Cheers,

Tuxalot

---

### Post by Anduu on 2008-03-01
> **tuxalot said:**
> Hardy Heron has a nice feature to accomplish just what you're mentioning.  Perhaps other releases do as well (I'm still figuring things out in the Linux world).  See attached screen.

Cheers,

Tuxalot

Youve been able to do that for a long time ...since at least pre Dapper.....

Anyways you can only change the values so much and it tends to act flakey at  times.I would avoid that and just use sleep values....much safer imho.

---

