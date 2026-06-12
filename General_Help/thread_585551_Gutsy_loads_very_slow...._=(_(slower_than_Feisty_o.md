---
title: "Gutsy loads very slow.... =( (slower than Feisty or XP)"
date: 2007-10-21
forum: General Help
---

### Post by styxie on 2007-10-21
When I boot Gutsy, it takes ages (a lot more than Feisty, which I also installed) to load. But when I hit CTRL+ALT+F1, it loads quickly. When I hit CTRL+ALT+F1 after a few minutes during the normal slow booting, it says:

FWH not detected

Among other things, but this is the only thing I could record. Also, I don't see the Ubuntu logo and the orange loading bar. The screen is totally black (not turned off, just plain black). What should I do?

---

### Post by seventyeights on 2007-10-21
I don't have your problem, but I was curious, and I found [_this_]("https://bugs.launchpad.net/ubuntu/+bug/102982") and [_this_]("http://sidux.com/PNphpBB2-viewtopic-t-257.html"). 

Give those a good read and see if you want to risk blacklisting that module.

```
# echo "blacklist intel_rng" >> /etc/modprobe.d/blacklist
```

---

