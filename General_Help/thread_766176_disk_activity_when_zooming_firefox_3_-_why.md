---
title: "disk activity when zooming firefox 3 - why?"
date: 2008-04-25
forum: General Help
---

### Post by thehighhat on 2008-04-25
installed hardy 8.04 LTS amd64

working fine after lots of hacketry.

strange issue with firefox 3:


zooming any page (ctrl-+, ctrl--) or using ctrl mousewheel up/down results in heavy disk i/o.

nothing i can do prevents this.  even tried disabling disk cache in about:config


i cannot find where the writes/reads/seeks are occurring.  it's not in /tmp /var or profile.


what gives?

why does ff3 need to write/read/seek a webpage that is already be loaded in memory, just to do a zoom?


my hdd is noisy during zoom, but quiet most all other time.  not even loading a new page/tab/etc results in so much noisy disk activity.


thoughts?





----- fyi
amd64 2.33ghz 8core 4gb mem 1gb swap raid1_sata_ext3_writeback  server_kernel (same issue with generic kernel) nvidia (nv or nvidia)

---

### Post by thehighhat on 2008-04-26
^^^

---

### Post by thehighhat on 2008-05-09
^^^

---

### Post by thehighhat on 2008-05-13
Found problem.  FF is writing the zoom value to db for future access.  This is poor design and not good for your disks health.  SSD users beware!  Multi-user environments beware.  

See bug report:  [https://bugzilla.mozilla.org/show_bug.cgi?id=417732](https://bugzilla.mozilla.org/show_bug.cgi?id=417732)

Stop-gap solution:  disable  browser.zoom.siteSpecific

---

