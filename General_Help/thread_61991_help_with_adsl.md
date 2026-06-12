---
title: "help with adsl"
date: 2005-09-02
forum: General Help
---

### Post by Eric P. on 2005-09-02
I just got my Ubuntu 5.04 from a friend and I need help to connect it into my adsl. im using Windows XP to internet and I have the Ubuntu in another partition. I've used Knoppix KDE Live-CD too.

Please help!  :)

---

### Post by Eric P. on 2005-09-02
P.S. its a dynamic ip adsl modem so i cant use proxy (i think, im new to linux)

---

### Post by bjweeks on 2005-09-03
The easist thing to do imo is to buy a router. There only 15-50$ and connects to adsl modom and does all the dialing so no softwear to deal with.

---

### Post by trash on 2005-09-03
I have no clue really what the problem is... is your modem USB or ethernet?

have you tried to type this in a terminal:

sudo pppoeconf

---

### Post by Eric P. on 2005-09-03
3 things:

it IS a router
its ethernet
and i cant sudo  coz it says that im not sudoer and cant login as root

---

### Post by trash on 2005-09-03
you should be using your user password when asked to log in after a sudo command :)

---

### Post by Eric P. on 2005-09-03
i did but it says im not  sudoer, im talking from Windows xp, Ubuntu KdE 5.04 is on another boot, im waiting for some real solution for that

---

### Post by trash on 2005-09-03
on a fresh install of Ubuntu your user created during the install is given sudo powers by default, what have you changed since the install?
It is an easy fix but sorry i don't have the answer.

---

### Post by Eric P. on 2005-09-03
i did nothing, it asked for root password and i made it the same as the user one, but in login, when i put root as username, and the password, it says tht the administrator cant login from that screen, i need know how to enter as root for edit user eric as sudoer

---

### Post by trash on 2005-09-03
OH! I got confused about that when i first installed Ubuntu...sudo will give you the user(admin) root access.

so login as your user

open up a terminal and enter 'sudo pppoeconf'

then enter your user password

BTW, you cannot login as root by default.

---

### Post by Eric P. on 2005-09-07
YAY im on linux and my friend helped me (the same that gave me ubuntu) but i still want know how to login as root to acess partitions, it says im not authorized to see them

---

### Post by facefur on 2005-09-22
I just signed up for DSL and I have an adsl modem.  It ties into my 4 port hub on the ethernet conneciton.

When the installer was there, he specified that the modem needs to be set for PPP for that type of connection, but changed to :"Bridging" when used with a router or switch.

You might want to check your adsl modem data for that.

facefur

---

