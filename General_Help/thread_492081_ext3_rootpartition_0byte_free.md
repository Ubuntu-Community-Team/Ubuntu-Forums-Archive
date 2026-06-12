---
title: "ext3 rootpartition 0byte free"
date: 2007-07-04
forum: General Help
---

### Post by -maxx on 2007-07-04
hi.
the size of my rootpartition **(sda1)** is about 13gb and normaly, about 8gb are free...

but since I checked **sdc1** with **e2fsck -y -f -v -c -c -C 0 /dev/sdc1**, there are 0byte free on **sda1**...
I have to say that i got many errors whyle checking sdc1, and after 5min of pressing Enter I stoped it and rebooted my pc...
so now I can't login because the seassion crashes!

i checked my sda1 with e2fsck, but there were no errors or sth else...
the confusing question are 0byte free, but there are only 4,xGB data?
and i also can create new files and save them on sda1, so sda1 isnt full....

[IMG]http://img245.imageshack.us/img245/6771/linuxbf6.jpg[/IMG]

can someone help me??
thanx, -maxx

---

### Post by -maxx on 2007-07-05
help? :-k:-k:-k:-k:-k

---

