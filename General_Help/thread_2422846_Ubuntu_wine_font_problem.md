---
title: "Ubuntu wine font problem"
date: 2019-07-13
forum: General Help
---

### Post by gerhard-rauniak-gmail on 2019-07-13
I've a problem with wine, because fonts smoothing doesn't work. I already found a solution for my problem. If I use

```
xrdb -query | grep -vE 'Xft\.(anti|hint|rgba)' | xrdb
```

fonts smoothing works perfect. Unfortunately I haven't found a solution to adopt it permanently. Whenever I restart or suspend I've to apply it once again, which drives me crazy.

I would be very grateful for any help!

---

