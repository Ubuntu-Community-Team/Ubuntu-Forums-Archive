---
title: "find not returning"
date: 2017-09-18
forum: General Help
---

### Post by Frank P on 2017-09-18
I have 2 servers running Ubuntu 16.04LTS

sudo find / -iname fstab 2>/dev/null

Finds the file and returns on one server; it finds the file but never returns on the other

Where can I look for the problem

Thanks

Frank

---

### Post by steeldriver on 2017-09-18
How do you know there's a problem (other than the search is taking a long time)?

---

### Post by Frank P on 2017-09-18
Both servers are virtually identical - ones a back up. Both previously returned from FIND in seconds. Today I left one for over an hour and it didn't return; the other returned in seconds. It seems to me that there's a problem

---

