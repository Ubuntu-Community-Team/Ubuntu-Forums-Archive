---
title: "ubuntu feisty+xampp"
date: 2007-05-15
forum: General Help
---

### Post by chameleon150259 on 2007-05-15
I have installed xampp on Ubuntu Feisty and I can view the interface at [http://localhost](http://localhost).
However, no matter what I do I cannot get to the page from the web.
I have tried different ports eg.80,8080,8000
I have tried various port forwarding configs in my router.
I have no firewall running.

Is there something obvious I am missing?
I have heard that Ubuntu is problematic with port config.:confused:

---

### Post by knightnet on 2007-05-16
By default it should be on [http://localhost:8080/](http://localhost:8080/)

However, Ubuntu/Debian can be a little odd on its localhost settings. Check your HOSTS file and find out what you have set as localhost. Also try:
[http://127.0.1.1:8080/](http://127.0.1.1:8080/)
to see if that works.

---

