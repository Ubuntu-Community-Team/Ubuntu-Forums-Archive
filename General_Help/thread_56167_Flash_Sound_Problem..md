---
title: "Flash Sound Problem."
date: 2005-08-11
forum: General Help
---

### Post by chadwick359 on 2005-08-11
Working on a Dell Inspiron 9300 laptop, and most everything seems to be going fine, but in any flash content I try to view on the net, i get no sound. I'm using firefox, and have tried both the flashplayer-mozilla and the flashplayer-nonfree packages, as well as having

---

### Post by varunus on 2005-08-11
This is a bug in flash.  The fix:

Open up a terminal and type the following:
```
sudo ln -s /usr/lib/libesd0.so.0 /usr/lib/libesd0.so.1
```

I think its a typo in flash that looks for the wrong number, this makes a shortcut to the correct file.

---

### Post by anarki on 2005-08-11
If you, maybe, listen to some music or something during surf, than it's quiet possible that the other application lock /dev/dsp, so flash cant open it for writing (mean playing music).
If so, try to use artsd and artsdsp, or some other sound server as esd.

---

### Post by gmc on 2005-08-12
[QUOTE=varunus]This is a bug in flash.  The fix:

Open up a terminal and type the following:
```
sudo ln -s /usr/lib/libesd0.so.0 /usr/lib/libesd0.so.1
```

I think its a typo in flash that looks for the wrong number, this makes a shortcut to the correct file.[/QUOTE]

I think there's another typo there. When I checked /usr/lib, there was no file called libesd0.so.0 -- I did however find libesd.so.0 -- that being said, your fix should read:

```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```

All in all, it works perfectly. Thank you!

G.

---

