---
title: "change when files in /tmp are deleted?"
date: 2006-12-09
forum: General Help
---

### Post by likes2skate on 2006-12-09
Hello,

I am a refugee from RedHat.  There, files in /tmp are deleted after a week or so.  

Files in /tmp disappear much more quickly in ubuntu, way too quickly for my tastes.  

Is this customizable?  I would like to set it longer.  

Thanks,

likes2skate aka Rick Graves

---

### Post by bapoumba on 2006-12-09
> **likes2skate said:**
> Files in /tmp disappear much more quickly in ubuntu, way too quickly for my tastes.
Hello,
by default on debian and debian-based distributions, /tmp is cleared every reboot. You may want to have a look at :
[http://www.pathname.com/fhs/pub/fhs-2.3.html#TMPTEMPORARYFILES]("http://www.pathname.com/fhs/pub/fhs-2.3.html#TMPTEMPORARYFILES")
[http://www.pathname.com/fhs/pub/fhs-2.3.html#VARTMPTEMPORARYFILESPRESERVEDBETWEE]("http://www.pathname.com/fhs/pub/fhs-2.3.html#VARTMPTEMPORARYFILESPRESERVEDBETWEE")
[http://www.debian-administration.org/articles/83]("http://www.debian-administration.org/articles/83")

/var/tmp ? ;)

---

### Post by likes2skate on 2006-12-10
bapoumba,

Exactly what I needed.

Thanks,

---

### Post by bapoumba on 2006-12-11
Welcome ;)

---

