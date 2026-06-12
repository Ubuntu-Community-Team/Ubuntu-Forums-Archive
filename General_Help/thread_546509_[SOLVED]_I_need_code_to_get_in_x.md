---
title: "[SOLVED] I need code to get in x"
date: 2007-09-08
forum: General Help
---

### Post by DougieFresh4U on 2007-09-08
I need to get in my X file to change my default depth from 24 to 16 so DRI will be enabled. :)
Can some one please provide code?
Thanks so much
Dougie

---

### Post by steveneddy on 2007-09-08
In terminal

```
sudo gedit /etc/X11/xorg.conf
```

It's kinda close to the bottom of the file - and yes, you do need to change every line for the resolution.

---

### Post by DougieFresh4U on 2007-09-08
> **steveneddy said:**
> In terminal

```
sudo gedit /etc/X11/xorg.conf
```

It's kinda close to the bottom of the file - and yes, you do need to change every line for the resolution.

Got it, thanks so much ):P

---

