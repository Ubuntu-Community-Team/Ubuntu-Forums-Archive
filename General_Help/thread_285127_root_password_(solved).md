---
title: "root password? (solved)"
date: 2006-10-26
forum: General Help
---

### Post by jhenager on 2006-10-26
I don't recall being asked for a password for root, and I can't guess it. Anyone know what it would be for a typical install of Dapper 6.06?

---

### Post by PriceChild on 2006-10-26
Please read [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

In short... ubuntu uses "sudo" as a security feature.

use it to preceded any command to give root to it.

e.g. ```
sudo nano /etc/X11/xorg.conf
```use gksudo (gnome) or kdesu (kde) for graphical apps:```
gksudo nautilus
```

---

### Post by jhenager on 2006-10-26
Found it on Google, but thanks.
I am just used to using root on FreeBSD, SuSE, and all my other nix es.
Guess I can get used to not having it. Just couldn't figure out what the password could be. It would be nice to get an 'Account disabled' message instead of 'Invalid password', tho.

---

### Post by PriceChild on 2006-10-26
No problem :)

btw there was a little message at the top of the terminal the first time you openned it explaining things ;)

have fun in ubuntu!

---

### Post by jhenager on 2006-10-26
> **PriceChild said:**
> No problem :)

btw there was a little message at the top of the terminal the first time you openned it explaining things ;)

have fun in ubuntu!

I am having fun. It is an awesome distro.
Now I wish I could change my habits of skipping all that README stuff.

---

