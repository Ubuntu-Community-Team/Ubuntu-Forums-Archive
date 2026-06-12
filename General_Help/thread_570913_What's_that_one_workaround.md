---
title: "What's that one workaround?"
date: 2007-10-08
forum: General Help
---

### Post by Aidan1234 on 2007-10-08
I need the workaround for using nvidia geForce 7800GT in Feisty Fawn.

The one where it can't boot because you have to rename the driver from nv to nvidia or something?

Step by step instructions preferable.

i checked google and this forum for it, but no luck.

Thanks, and sorry if it's a repost.

---

### Post by Pumalite on 2007-10-08
You boot and you end up with a blank screen, or are you IN the system?

---

### Post by Shazaam on 2007-10-08
In terminal...
```
sudo dpkg-reconfigure xserver-xorg
```

or... 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

