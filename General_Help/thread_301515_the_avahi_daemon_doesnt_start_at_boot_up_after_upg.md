---
title: "the avahi daemon doesnt start at boot up after upgrade"
date: 2006-11-17
forum: General Help
---

### Post by wangdang on 2006-11-17
i recently upgraded to eft, and now the avahi discover daemon doesnt start at boot up as before....i badly need it to do so, and be available for all users.

We run quite a few avahi findable services in this apartment house, laundry schedule webserver etc (schoolbell)...

So how do i return it to the way it was in dapper?

---

### Post by Paerez on 2006-11-18
I am having the same issue (although it is less critical for me). I'll let you know if I figure anything out.

---

### Post by Paerez on 2006-11-18
OK found it!

edit "/etc/default/avahi-daemon" and change the 0 to a 1. :D

---

