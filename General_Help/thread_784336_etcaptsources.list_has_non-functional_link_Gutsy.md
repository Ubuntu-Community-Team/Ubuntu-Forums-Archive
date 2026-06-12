---
title: "/etc/apt/sources.list has non-functional link Gutsy"
date: 2008-05-06
forum: General Help
---

### Post by Xitron on 2008-05-06
I tried Hardy Heron (clean install) and it hosed my system up so badly that I've reinstalled (again, clean install) Gutsy Gibbon.

When I uncomment the /etc/apt/sources.list sources, I'm hitting one that stops the whole show, and yet it's important to me.

[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)

Because the apt-get update line is not informative, I don't know if it's choking on:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

Does anyone have a better link I can insert into the sources.list?

Thanks!

Unca Xitron

---

### Post by shaggy999 on 2008-05-06
I imagine the main archive servers are still getting hammered. I recommend changing the gutsy source links to one of the many mirrors. I use Oregon State University's OSL lab mirror which is very fast for me, but I live in Oregon so of course it's fast. :)

---

### Post by Xitron on 2008-05-06
Perfect, Shaggy!!  I've changed to a mirror and all is well!

Thanks so much!!

Unca Xitron

---

