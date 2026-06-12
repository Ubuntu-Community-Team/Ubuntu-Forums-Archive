---
title: "Internet connection very slow"
date: 2004-10-26
forum: General Help
---

### Post by Pieter on 2004-10-26
I recently installed Ubuntu and everything works just fine, except for one thing: the ADSL connection is very slow.
I searched this forum and came across two possible solutions:
1. enter DNS from my provider
2. turn off IPv6 in modules.conf

Both of the solutions did not have the desired result. Does anyone have another solution to this problem. Before Ubuntu I used Mandrake 9.1 and before that Red Hat 7.2. Both did not show this problem.

Some extra info:
- I have a dual boot system with Ubuntu and WinXP
- I connect over a LAN through a Vigor 2200 router

---

### Post by jdong on 2004-10-26
Can you define slow? Low bandwidth or latent? What speed do you download large files (ISO's) at? Can you post the output of an ifconfig?

---

### Post by Pieter on 2004-10-26
well, slow as in Google takes about one minute to load and that is when I just type in [www.google.com](www.google.com)
downloading large files is not something I want to do with my current speed

I will post the output of ifconfig tonight, because I'm at work right now and can't access my system

---

### Post by sfw5000 on 2004-10-26
If you are using FireFox, there's like a 99% chance that the ipv6 thing is your problem, did you see this thread:

[http://ubuntuforums.org/showthread.php?t=171](http://ubuntuforums.org/showthread.php?t=171)

You need to do all the steps there, including the ver last one where you delete the ipv6.ko file. We did this last night and it did not work after doing the first two steps, but when did the last step it did work. We did have to re-boot, though, before the web was back to normal.

hth,

sam

---

### Post by Pieter on 2004-10-27
Well, just as an update: removing IPv6.ko indeed solved it
It deed introduce a new fatal error when booting Ubuntu, but that is just something I have to live with I guess

---

