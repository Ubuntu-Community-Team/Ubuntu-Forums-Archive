---
title: "Multiple network cards at boot.. Once a network is found, stop ifup? help!"
date: 2005-07-16
forum: General Help
---

### Post by dudinatrix on 2005-07-16
I've got two network cards in my laptop:  eth0 and wlan0.

At home, I use my wireless (wlan0).  At work, I use eth0.  

Every boot, the "* Configuring network interfaces..." takes over a minute because both interfaces are set to auto in /etc/network/interfaces

This is a two part question:

(1)  Is it possible to STOP ifup once it finds an active network?  Say it does wlan0 and then eth0, in that order. Is it possible to do something like this.... (pseudo code, obviously)

 ```
ifup wlan0
ping www.google.com
if not resolved then ifup eth0

``` 

That way, it wont attempt to start eth0 since wlan0 is now active.

(2)  Another way I thought of doing this was setting up a time test.  If its monday-friday, between 8 to 4:30 (work), start up eth0 first, using the idea presented in question 1.  Otherwise, I'm likely at home, so start up wlan0 first.

Any ideas on implementing something like this? :)

---

