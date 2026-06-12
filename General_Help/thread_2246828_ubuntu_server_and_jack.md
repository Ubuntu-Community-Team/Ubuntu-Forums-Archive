---
title: "ubuntu server and jack"
date: 2014-10-03
forum: General Help
---

### Post by brilyant on 2014-10-03
Has anyone out there successfully made jackd run on a Ubuntu server (i.e. without dbus available)?  If so, how did you do it?

I really don't want to clutter up a system with X just to run jackd.

---

### Post by carlo4 on 2015-01-06
> **brilyant said:**
> Has anyone out there successfully made jackd run on a Ubuntu server (i.e. without dbus available)?  If so, how did you do it?

I really don't want to clutter up a system with X just to run jackd.

I believe you need to compile jackd yourself without debug support.

I have written here how to do that; since I am solving the same problem as you right now I am continuously updating a small guide:

[http://capocasa.net/jackd-headless](http://capocasa.net/jackd-headless)

Write up if I you run into issues!

Carlo

---

