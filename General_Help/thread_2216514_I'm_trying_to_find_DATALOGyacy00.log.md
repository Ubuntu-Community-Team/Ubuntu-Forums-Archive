---
title: "I'm trying to find DATA/LOG/yacy00.log"
date: 2014-04-12
forum: General Help
---

### Post by coljohnhannibalsmith on 2014-04-12
Hello,

I'm trying to find I'm trying to find [COLOR=#ff0000]*"DATA/LOG/yacy00.log."*[/COLOR] I have Ubuntu 12.04 Precise Pangolin, and I'm using the [COLOR=#ff0000]*"Classic"*[/COLOR] desktop.

I've already used "ctl h" to find the hidden files and folders; but I can't do this in Nautilus Preferences.

Thanks Hannibal

---

### Post by Habitual on 2014-04-12
terminal >
```
find `pwd` . -name [COLOR=#ff0000]*yacy00.log*[/COLOR]
```
If you can't find it from that, then 
cd /
```
sudo find `pwd` . -name [COLOR=#ff0000]*yacy00.log*[/COLOR]
```

---

