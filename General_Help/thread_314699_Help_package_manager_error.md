---
title: "Help package manager error"
date: 2006-12-07
forum: General Help
---

### Post by manopb on 2006-12-07
I just received the following error message:
> E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

This is the file:
> # automatically added by gnome-app-install on 2006-11-27 10:39:36.172401
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates universe

Can someone see what is wrong?:-k 

Thanks

---

### Post by K.Mandla on 2006-12-08
> **manopb said:**
>  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
Should there be a final slash after the word 'ubuntu'? In other words ...

> **manopb said:**
>  deb [http://security.ubuntu.com/ubuntu/]("http://security.ubuntu.com/ubuntu") edgy-security universe

---

