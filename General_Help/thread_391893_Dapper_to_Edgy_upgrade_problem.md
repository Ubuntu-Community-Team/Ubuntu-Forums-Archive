---
title: "Dapper to Edgy upgrade problem"
date: 2007-03-23
forum: General Help
---

### Post by gannina on 2007-03-23
Hi, I just recently did an upgrade from Ubuntu Dapper to Ubuntu Edgy. When the system rebooted it added two new sets of builds I could choose to load, the following are those builds:

Ubuntu, kernel 2.6.17-11-386
Ubuntu, kernel 2.6.17-10-386


The first build in the list does not load, it just goes to a black screen with a minus symbol flashing in the upper left corner. The second build loads, but I'm not sure if that is the most up-to-date one? Why did the upgrade add two builds to my startup? Is there a way I can get the first one to work? 

Thanks in advance

---

### Post by raja on 2007-03-23
If there is a problem with that kernel, I dont see any issues with sticking to the one that works. In you /etc/boot/.menu.lst, you can change the default to 1 so that the second entry if used for default boot.

---

### Post by zvacet on 2007-03-24
You just have black screen problem.That can be solved this way
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")
And you will be able to use newer kernel.

---

