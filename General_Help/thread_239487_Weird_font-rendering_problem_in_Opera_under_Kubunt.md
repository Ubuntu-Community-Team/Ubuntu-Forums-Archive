---
title: "Weird font-rendering problem in Opera under Kubuntu"
date: 2006-08-19
forum: General Help
---

### Post by allix on 2006-08-19
Check out the screen shot. The fonts looks like they have been squeezed together on some websites. Digg, Wikipedia and slashdot all have this problem. This is not the first time this happens under Kubuntu but I have never had the same problem under Windows, Suse or even Ubuntu. Has anyone else seen this before?

This seems to be a problem with QT under kubuntu(as far as I know, Opera uses QT for font rendering) because the Static-qt version from Opera.com does not have this problem. I've tried deleting my Opera profile, reinstalled (--purge). What else can I do?

[[IMG]http://img106.imageshack.us/img106/2751/operacm4.th.jpg[/IMG]](http://img106.imageshack.us/my.php?image=operacm4.jpg)

---

### Post by allix on 2006-08-19
Nevermind, I found a solution. Here it is in case someone else needs it. :)

[http://my.opera.com/community/forums/topic.dml?id=144404](http://my.opera.com/community/forums/topic.dml?id=144404)
Discussion and details:
[http://my.opera.com/community/forums/topic.dml?id=144371](http://my.opera.com/community/forums/topic.dml?id=144371)
[http://my.opera.com/community/forums/topic.dml?id=141272&t=1156011296&page=1#comment1645876](http://my.opera.com/community/forums/topic.dml?id=141272&t=1156011296&page=1#comment1645876)

> Just purge scim-qtimm package and it should work correctly.

"sudo apt-get remove --purge scim-qtimm"

---

### Post by samwyse on 2006-10-26
Still needs to be done in Edgy.

---

