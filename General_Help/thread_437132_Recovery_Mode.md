---
title: "Recovery Mode"
date: 2007-05-08
forum: General Help
---

### Post by Haywood on 2007-05-08
In GRUB it gives you the option for "Recovery Mode".  I have two questions...
1) How, When & When would you use this? OK, that was probably 3 questions.
2) During recovery mode it says "type root password for maintenance or Control-D to continue."  If the root account is locked, what purpose does this serve?

R/  Bill

---

### Post by zvacet on 2007-05-08
You will use it only if you have some problem wich you can not resolve other way.I think that the name say it all (**recovery**).Locked root acount prevent other people to mess with your file system.This is very short description.

---

### Post by aysiu on 2007-05-08
You won't be prompted for a root password unless you've already set one.

Recovery mode comes in handy if you've screwed up your user accounts in some way--can't log in as user, forgot your password, accidentally took away *sudo* privileges from your last *admin* user...

---

