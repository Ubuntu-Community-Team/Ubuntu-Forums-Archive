---
title: "Cleaner output of xev"
date: 2015-11-09
forum: General Help
---

### Post by vasa1 on 2015-11-09
In Jan 2014 I posted a link to code about cleaning up the output of xev when one wanted to find a keycode/keysym: [http://ubuntuforums.org/showthread.php?t=2201166&p=12907845#post12907845](http://ubuntuforums.org/showthread.php?t=2201166&p=12907845#post12907845)

I visited that page today and they've now got a different code:```
xev | awk -F'[ )]+' '/^KeyPress/ { a[NR+2] } NR in a { printf "%-3s %s\n", $5, $8 }'
```

---

