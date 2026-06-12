---
title: "strange adesklets issue with recent edgy upgrades"
date: 2006-10-31
forum: General Help
---

### Post by moore.bryan on 2006-10-31
[I]need a little help guys and gals... the recent series of updates for edgy stops adesklets from working for me.  when i try to start it in term, i get:
```

*** glibc detected *** adesklets: double free or corruption (out): 0x0909dd18
====== Backtrace: =======

``` in the first two lines.  after many lines, it hangs at 
```

ffffe000-fffff000 ---p 00000000 00:00 0              [vdso]
```
help?
[/I]

---

### Post by moore.bryan on 2006-11-03
*is anybody out there?  just nod if you can hear me; is there anyone at all?*

---

### Post by moore.bryan on 2006-11-03
[I]not entirely sure why, but i was able to force a downgrade to an older libfontconfig and fontconfig-config and it worked.

for all other adesklets users out there, good luck!
[/I]

---

