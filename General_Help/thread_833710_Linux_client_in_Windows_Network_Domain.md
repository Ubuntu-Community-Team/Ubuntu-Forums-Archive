---
title: "Linux client in Windows Network Domain"
date: 2008-06-18
forum: General Help
---

### Post by j3r3my86 on 2008-06-18
Hi

I'm currently trying to implement Linux Workstations in a school that already has a Windows AD Domain infrastructure and I need some help. My AD is Windows 2003 and my Linux clients are Ubuntu 8.04

I've successfully manage to join my linux client to the windows AD environment and get it to logon using AD's accounts n etc.

However, in the AD there is 2 groups of users, Student and Teachers. They form two different OUs. And all users of student n teachers have their own student or teacher logon script for windows clients

The logon scripts mainly sets up file sharing and creating network drives for its users to access folders that they need. A number of drives are created from 2 servers hosting these files n folders

I need to know if it is possible and how do I solve this issue of creating a logon script that will work on Linux clients that served the same purposes as the windows logon script.

Do i place it on the clients or servers ? How do I make it work correctly such that scriptA is for student accounts only and scriptB for teachers accounts only.

Please provide me some assistance on this, I'm quite new to this and already had a hard time getting my Ubuntu clients to join the domain including allowing all users to logon.

Thx in advance

Jeremy

---

### Post by Imran83 on 2009-05-28
Anybody please answer this answer. I have the same query as above.

---

### Post by dmizer on 2009-05-28
> **Imran83 said:**
> Anybody please answer this answer. I have the same query as above.

As that post is almost a year old, you're probably better off creating a new one yourself.

Thank you!

---

