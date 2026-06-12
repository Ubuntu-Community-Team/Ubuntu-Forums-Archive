---
title: "Ip release and reniew in Ubuntu"
date: 2005-07-12
forum: General Help
---

### Post by Omnios on 2005-07-12
I have a dual boot XP Ubuntu set up. My internet connection is a 32kbs cable connection and I find I have a few problems with the cable modem. The Ubuntu connection conflics with the xp set up periodicly wich I can fix by ip release and reniew in Xp. What Im wondering is how do I accomplish a ip release and reniew this in Ubuntu?

---

### Post by varunus on 2005-07-12
Assuming your ethernet card is called "eth0," to release and renew in Ubuntu, open a terminal and type the following:

sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0

Good luck.

---

### Post by Omnios on 2005-07-12
Works like a charm.

 Thanks!

---

