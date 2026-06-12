---
title: "ubuntu 15.04 very slow apt-get update"
date: 2015-04-24
forum: General Help
---

### Post by walker17x on 2015-04-24
hi !

i have a problem with ubuntu 15.04 , the apt-get update process is very slow !

on previous versions of ubuntu it was only the first apt-get update after install that was slow and after that it was very quick

but now everytime i do an apt-get update it's slow !

---

### Post by matt_symes on 2015-04-24
Hi

> **walker17x said:**
> hi !

i have a problem with ubuntu 15.04 , the apt-get update process is very slow !

on previous versions of ubuntu it was only the first apt-get update after install that was slow and after that it was very quick

but now everytime i do an apt-get update it's slow !

How slow is slow ? Metrics would be useful.

Is it the update or upgrade process or both that is slow ?

Kind regards

---

### Post by Ankush_Menat on 2015-04-24
I am facing similar problem. It's not slow, but it's not caching packages db like it used to do in 14.04. Everytine when I apt-get update it downloads 10-14MB of database.

Should I file a bug report?

---

### Post by matt_symes on 2015-04-24
Hi

> **Ankush_Menat said:**
> I am facing similar problem. It's not slow, but it's not caching packages db like it used to do in 14.04. Everytine when I apt-get update it downloads 10-14MB of database.

Was this an upgrade from 14.10 or a fresh install of 15.04 ? I assume the latter.

> Should I file a bug report?

Maybe. I would wait a couple of days personally.

Kind regards

---

### Post by walker17x on 2015-04-25
> **Ankush_Menat said:**
> I am facing similar problem. It's not slow, but it's not caching packages db like it used to do in 14.04. Everytine when I apt-get update it downloads 10-14MB of database.

Should I file a bug report?

yes this is the problem

---

### Post by Ankush_Menat on 2015-04-25
> **matt_symes said:**
> Hi



Was this an upgrade from 14.10 or a fresh install of 15.04 ? I assume the latter.



Maybe. I would wait a couple of days personally.

Kind regards

Fresh install. Wiped Fedora and installed Vivid yesterday.
 [IMG]http://i.imgur.com/8hxCAKg.png[/IMG]


EDIT (29/4/15):

It's working properly now!

---

