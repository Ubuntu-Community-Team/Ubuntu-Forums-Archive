---
title: "libgtk3-nocsd.so.0 cannot be preload"
date: 2021-06-02
forum: General Help
---

### Post by monkeybrain20122 on 2021-06-02
```
ERROR: ld.so: object 'libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
```

I am often seeing this message in the terminal. Fresh install of Ubuntu 20.04 and I have checked that libgtk3-noscd is always installed.

According to google this cropped up since Ubuntu 18.04 and a way to fix it is to install libgtk3-nocsd:i386. But there is no i386 package for libgtk3-noscd in focal [https://bugs.launchpad.net/ubuntu/+source/gtk3-nocsd/+bug/1897458](https://bugs.launchpad.net/ubuntu/+source/gtk3-nocsd/+bug/1897458)
I am seeing this not only when running 32 bit apps (as in wine), but maybe a few other places too.

What is libgtk3-noscd for? Can we unset preloading it once and for all (without unsetting preloading other things)? What would be the consequence?

Thanks.

---

### Post by Dennis N on 2021-06-02
Synaptic Pkg. Manager describes it as "Library to disable gtk+3 client side decorations". It's not installed in my Ubuntu 20.04.2, so maybe you can remove it without harm.

---

### Post by monkeybrain20122 on 2021-06-02
Hi, removing libgtk3-nocsd got rid of the error and so far doesn't seem to affect anything. Don't know how it got installed in the first place. Thanks!

---

