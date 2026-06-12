---
title: "[lubuntu 15.10] How to disable guest session in lightdm"
date: 2016-01-13
forum: General Help
---

### Post by Angelin_Lalev on 2016-01-13
Greetings, 

I tried the following solution, which should work in 15.04 (or at least people say). 
I created file: 

/etc/lightdm/lightdm-gtk-greeter.conf.d/50_noguest.conf

With the following 2-line content:

[SeatDefaults] 
allow-guest=false 

Rebooted ... and nothing happened. Guest is still there and I can log in with him. 

By the way, I'm curious what motivates the decision to leave this session enabled by default. Maybe there is a discussion on a list or forum somewhere?

---

