---
title: "phppgadmin install"
date: 2006-11-08
forum: General Help
---

### Post by ryanmacleod on 2006-11-08
I am trying to install phppgadmin on my Ubuntu machine. From instructions on the web I think I should be able to do a simple apt-get install phppgadmin

But I get the following error:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package phppgadmin

What do I need to do to get this working?

Thanks!

---

### Post by ryanmacleod on 2006-11-08
Don't worry. I managed to get it to work by editing 
/etc/apt/sources.list

I un-hashed: 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

then ran:
apt-get update
apt-get install phppgadmin

---

