---
title: "Executing Binaries as normal User fails - please help."
date: 2005-04-14
forum: General Help
---

### Post by dertony on 2005-04-14
Hi,

I have a very strange problem with my Ubuntu install. It was working 
flawlessly until yesterday, when, for no obvious reason, it suddenly refused
to give me as user permission to execute binary files. Not a nice thing
when you try to run /bin/bash to login...

Investigations didn't really led to anything. It somehow just looks like the
whole permission thing is totally borked. Applications work when logged in as
root, but as soon as I try another user (by trying to log in, sudo and su),
they refuse to do anything. It is definetely not a permission thing - all
files _should_ run fine. Filesystem is mounted with exec as well - at least
that is what fstab says.

I'm not new to linux and usually know how to solve most things, but here I
have no clue at all. Any help would be very welcome and appreciated.

Thanks,
Tony.

---

### Post by Klin'Targ on 2005-04-14
If you make a new user, can they execute binaries?

---

### Post by dertony on 2005-04-15
[QUOTE=Klin'Targ]If you make a new user, can they execute binaries?[/QUOTE]

I've created a test user and the problem stays the same.

Tony.

---

