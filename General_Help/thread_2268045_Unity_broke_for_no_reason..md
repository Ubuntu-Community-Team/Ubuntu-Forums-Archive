---
title: "Unity broke for no reason."
date: 2015-03-05
forum: General Help
---

### Post by warren3 on 2015-03-05
Hi,

I was using Ubuntu fine yesterday but when I logged in today I just get a wallpaper.  I can right click and go into settings and use settings, but I cannot bring up a terminal with the keyboard shortcut.  Logging into guest is ok and Unity works fine.

I am running 14.10 and at first I thought it might be the 13.9 rc7 kernel I am using, but I loaded the stock latest kernel for 14.10 and its still the same.

Can I fix this??  I am using a Brix i3.

Thanks.

---

### Post by maria222 on 2015-03-05
Same here.  Using Dell XPS-18inch tablet/ 8GB RAM.  Machine works fine without compiz.  When I made a few changes on compiz and unity; the sidebar and the top menu - all gone.  terminal comes up, and when tried some of the solutions from the forum sometimes things work; but a few times the terminal and windows also freeze.  On screen keyboard (onboard) does not respond.  External keyboard does not respond too.  Have to hard boot.  

May be we should not use compiz at all?  Anyone used kwin  [in place of compiz?] and how that one works with ubuntu?

---

### Post by mc4man on 2015-03-05
> **warren3 said:**
> Hi,

I was using Ubuntu fine yesterday but when I logged in today I just get a wallpaper.  I can right click and go into settings and use settings, but I cannot bring up a terminal with the keyboard shortcut.  Logging into guest is ok and Unity works fine.

I am running 14.10 and at first I thought it might be the 13.9 rc7 kernel I am using, but I loaded the stock latest kernel for 14.10 and its still the same.

Can I fix this??  I am using a Brix i3.

Thanks.
If it works in a guest session then you can certainly fix, how is the question. To see if anything jumps out concerning your compiz settings try this & post results, file will be in home folder - 

```

dconf dump /org/compiz/  > compiz-settings.txt
```

---

### Post by warren3 on 2015-03-07
Hi.

When I tried to access the settings file it would not allow me access - this was with the guest account. 

I decided to reinstall 14.04 and start over.  I was meaning to do this anyway.

Cheers.

---

