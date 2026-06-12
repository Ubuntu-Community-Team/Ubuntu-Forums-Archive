---
title: "apt-get update - &quot;no public key.....&quot;"
date: 2016-12-12
forum: General Help
---

### Post by grey1beard on 2016-12-12
Trying to solve a terminal issue with downloading a video on i-player, I started by using apt-get update as a first step, but at the end of it running, I got this line

 *There is no public key available for the following key IDs:  1397BC53640DB55*1

Can anyone tell me of the bearing this has on my update, or consequent attempts to sort out get- iplayer.
John

---

### Post by #&amp;thj^% on 2016-12-12
Sorry I can't help on the iplayer issue but you can fix the key error
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 1397BC53640DB551
```
Now try your update again.

---

### Post by grey1beard on 2016-12-13
Many thanks, 1fallen. Worked perfectly, and updated OK
John

---

### Post by #&amp;thj^% on 2016-12-13
Your Welcome...Glad to help.

---

