---
title: "Not getting 75hz!"
date: 2007-10-18
forum: General Help
---

### Post by BBin on 2007-10-18
Hey, having a bit of a problem here!
My monitor (LG L194WT, [http://www.lge.com/products/model/detail/l194wt.jhtml](http://www.lge.com/products/model/detail/l194wt.jhtml)) supports 1440x900 and 56-75hz. It is not on the list for monitors in Ubuntu 7.10, but auto-detect seems to get the right values. When I choose any resolution under 1440x900 i can use 75hz, but 1440x900@75hz tells me to log out for changes to take effect. When I log back in it's at 60hz and the 75hz choice has disappeared.
I'm on: 7.10, ATi Radeon 9700PRO, LG L194WT, radeon driver and compiz

Thanks!
//Robin

---

### Post by dcstar on 2007-10-18
> **BBin said:**
> Hey, having a bit of a problem here!
My monitor (LG L194WT, [http://www.lge.com/products/model/detail/l194wt.jhtml](http://www.lge.com/products/model/detail/l194wt.jhtml)) supports 1440x900 and 56-75hz. It is not on the list for monitors in Ubuntu 7.10, but auto-detect seems to get the right values. When I choose any resolution under 1440x900 i can use 75hz, but 1440x900@75hz tells me to log out for changes to take effect. When I log back in it's at 60hz and the 75hz choice has disappeared.
I'm on: 7.10, ATi Radeon 9700PRO, LG L194WT, radeon driver and compiz

Thanks!
//Robin

You may want to comment out any Refresh settings in xorg.conf, or add in a specific modeline to that resolution/refresh rate combo.

You can search out threads with all the details on how to adjust things like this.

---

### Post by fragos on 2007-10-18
LCD monitors have a longer persistance than CRTs and don't flicker for that reason.  60 should be more than sufficient for LCD monitors.

---

