---
title: "conky graph scaling"
date: 2013-04-30
forum: General Help
---

### Post by kurja on 2013-04-30
I'm trying to get my head around how to set conky graphs to display non-adaptive graphs, so that half way point is 50% of max, not 50% of highest point during measured period...

I've read that the up/down networking graphs need to have their scale set in Kib, but if I set the scale to 1500 it maxes out on my 8Mbps connection? Conky shows only abt 800KiB, which seems realistic but why is my graph maxing out? I'm having similar problems with cpu and mem garphs, too.

This is what I've set for networking:
```

${color}down:${color white} ${downspeed wlan0} k/s ${color}  up:${color white} ${upspeed wlan0} k/s${color #888888}${downspeedgraph wlan0 20,150 grey grey 1500}   ${color #888888}${upspeedgraph wlan0 20,150 grey grey 1000}

```

---

### Post by kurja on 2013-05-01
help?

---

