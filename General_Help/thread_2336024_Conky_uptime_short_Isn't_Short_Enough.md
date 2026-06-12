---
title: "Conky: uptime_short Isn't Short Enough"
date: 2016-09-03
forum: General Help
---

### Post by jakfish on 2016-09-03
Has anyone noticed that in later conky versions, uptime_short has started showing seconds? In earlier version, uptime_short showed just hours and minutes.

Along with tint2, I run conky commands in one line across my netbook top, and space is at a premium.

Is it possible to show uptime in only hours/minutes?

Thanks,
Jake

---

### Post by Frogs Hair on 2016-09-03
$uptime_short on my conky displays minutes and seconds or hours and minutes. $uptime displays hours minutes and seconds. Has your .conkyrc been updated for conky version 1.10 ?

---

### Post by jakfish on 2016-09-03
EDIT: @ Frogs Hair: we crossed posts, but many thanks for weighing in. I was exploring your idea as you were typing it :)

More research tells me that Conky ver. 1.10.1 will show uptime_short without seconds. But I have a legacy machine that uses conky ver 1.8.0, which shows seconds in uptime_short.

The workaround is this:

1) in conky flags, insert: times_in_seconds yes
2) then convert seconds into hours and minutes: ${format_time $uptime_short "\hh\mm"} 

time_in_seconds will affect all conky time readouts, so: ${format_time $battery_time "\hh\mm"} and so on...

Many thanks to this post: [https://bbs.archlinux.org/viewtopic.php?id=165368](https://bbs.archlinux.org/viewtopic.php?id=165368)

Jake

---

