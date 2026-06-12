---
title: "Set maximum directory size?"
date: 2006-12-09
forum: General Help
---

### Post by pichalsi on 2006-12-09
Is this possible?
My situation is following : Im on my hostel network, sharing some files through Samba and also I have one directory that gives write permission to everyone, for incoming files. Is it possible to set size of a directory so that noone floods my partition? Thanks
P.S. i hope i put it in right category...

---

### Post by po0f on 2006-12-09
pichalsi,

You can set up quotas if everyone logs in under one account name (anonymous login).

---

### Post by pichalsi on 2006-12-10
> **po0f said:**
> pichalsi,

You can set up quotas if everyone logs in under one account name (anonymous login).

Thanks but the thing is samba with anonymous make file owned by nobody :(

---

### Post by nikhilk on 2006-12-10
You can create a common account say "hostel" with a simple password and restrict the permissions only to the directory you have shared.

---

### Post by pichalsi on 2006-12-10
Thanks i used user nobody it should work now probably... my biggest problem was finding quota documentation, this helped me if someone else looks for something similar 
[http://www.debian-administration.org/articles/47](http://www.debian-administration.org/articles/47)

---

