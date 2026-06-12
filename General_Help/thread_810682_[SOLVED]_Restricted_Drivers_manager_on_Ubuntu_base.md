---
title: "[SOLVED] Restricted Drivers manager on Ubuntu base"
date: 2008-05-28
forum: General Help
---

### Post by Istonian on 2008-05-28
Ok, I am building up my Ubuntu base install. So far it's going good, but there are a couple of things I need. The main thing is the Restricted Drivers Manager. It's obviously not on here. Anyone know how to install it so I can get my ATi driveres installed?

---

### Post by cdenley on 2008-05-28
This should work.
```

sudo apt-get install xorg-driver-fglrx linux-restricted-modules-generic
sudo aticonfig --initial --input=/etc/X11/xorg.conf

```

---

### Post by Istonian on 2008-05-28
Thanks, but I remembered I could just use Envy. Used Envy and works flawlessly.

---

