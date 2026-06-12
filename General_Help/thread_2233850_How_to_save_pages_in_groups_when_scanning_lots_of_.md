---
title: "How to save pages in groups when scanning lots of pages?"
date: 2014-07-11
forum: General Help
---

### Post by 171742 on 2014-07-11
Hello,

I use xsane scanner on ubuntu 14.4 lts with a caonon pixma mx310. Works fine, especially for the intake of multiple pages. When it comes to saving though, I can only do so saving all under one name numbered: scanned page 1, scanned page2 and so on. I would like to save files in groups though. For example: 10 pages intake, 3 saved as this1,2,3, 7 saved as that1,2,3. How to do this? I cant seem to mark several pages with ctrl or the like in the xsane window. desktop solution would be appreciated, as im pretty bad with the terminal. but if nothing else is possible, then terminal is ok as well.

Thanks!

---

### Post by tgalati4 on 2014-07-11
Support by Canon is weak in linux.  Open a terminal:

```
scanimage -L
man scanimage
```

There is a --batch-count switch that might do what you want.  If you spend some time learning *scanimage*, then you can write some scripts to semi-automate what you want to do.

Write down all of the manual steps that you currently perform (in detail) and we can help assemble a script to reduce the Agony Units.

---

