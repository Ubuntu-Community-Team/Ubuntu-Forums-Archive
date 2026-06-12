---
title: "recovering an MD"
date: 2008-04-07
forum: General Help
---

### Post by vwfix on 2008-04-07
I was wondering if anyone knew a guide on how to recover a deleted MD volume. I need to actually reassemble the pv VG and the LV layers manually without reformatting the partitions and loosing the data they hold.
Here is what my box came up and I need to recover from
> Tue May  8 08:39:35 EDT 2007: mdconfig -a stop -m /dev/md2
Tue May  8 08:39:35 EDT 2007: mdconfig -a delete -m /dev/md2
Tue May  8 08:56:33 EDT 2007: mdconfig -a new -m /dev/md2 -l 5 -c 16 -r /dev/hdc3,/dev/hde3,/dev/hdg3,/dev/hdi3
Thu Apr  3 13:38:09 EDT 2008: [volumescan - INACTIVE PV] mdconfig -a delete -m /dev/md2:mad:

---

