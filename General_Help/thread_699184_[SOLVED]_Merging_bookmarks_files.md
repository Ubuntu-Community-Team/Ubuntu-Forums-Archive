---
title: "[SOLVED] Merging bookmarks files"
date: 2008-02-17
forum: General Help
---

### Post by borobudur on 2008-02-17
Hi, I merged several times the bookmarks.html file from firefox from two computers with the sdiff command:
```
sdiff bookmarks.html .mozilla/firefox/rc8md477.default/bookmarks.html -o merge.html
```But suddenly I get this error at the end of the files:
```
sdiff: subsidiary program `ed' failed
```Has anyone an alternative?

---

### Post by Sokertes on 2008-02-17
I have used kdiff3 many times and it works great. I just looked in the repository and seen that it is there. Never used in ubuntu but have used it in gentoo.

matter of fact I am going to install it now on my ubuntu machine

---

### Post by borobudur on 2008-02-18
Very nice tool indeed (even if it's kde based :) )
Thanks!

---

