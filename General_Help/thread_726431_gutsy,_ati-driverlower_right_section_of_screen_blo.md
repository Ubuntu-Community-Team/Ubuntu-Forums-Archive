---
title: "gutsy, ati-driver:lower right section of screen blotched"
date: 2008-03-16
forum: General Help
---

### Post by stephan0h on 2008-03-16
Hi Group,

I've got a strange problem.

I've got the proprietory ATI driver installed on a gutsy-system. Since a few weeks now at the lower left of my screen there is a rectangular section which is becoming inreadable - it looks like some of the pixels are inverted, but not all. Moreover sometimes the mouse-pointer is also "dragging" a rectangular section of blotched pixels. Restarting X-windows solves the problem for some time. I wanted to attach a screenshot of this, but on the screenshot everything looks normal.

I'm wondering if this is a hardware of a software problem. Any ideas?

Thanks,
Stephan

---

### Post by stephan0h on 2008-04-17
just wanted to say i solved this by installing the newest version of the ati-driver.

---

### Post by strabes on 2008-04-17
This is a known bug with the fglrx driver in the hardy repositories and was fixed several fglrx releases ago. It has been fixed in in the hardy version. You could upgrade now or wait a week until final release.

---

