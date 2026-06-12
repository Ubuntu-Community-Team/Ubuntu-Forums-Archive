---
title: "Avahi making Wubi not work"
date: 2007-08-10
forum: General Help
---

### Post by AcworthJack on 2007-08-10
I had installed Wubi Ubuntu on this PC a few months back - and it worked fine.

I removed it - and tried to re-install - but Avahi keeps messing up the network and I can't get this to work.

Is it possible to install Wubi now WITHOUT Avahi or any ZeroConf software to get it working?

thanks!

---

### Post by AcworthJack on 2007-08-12
Here is the solution.

As documented elsewhere - I unplugged my PC for a minute, rebooted into Ubuntu (without going into Windows) and all worked fine!

see [http://gentoo-wiki.com/HARDWARE_RTL8168#Troubleshooting](http://gentoo-wiki.com/HARDWARE_RTL8168#Troubleshooting) for details

:)

First, my apologies to Avahi folks – I had pegged you as the bad guys and had visions of flaming you and all the ZeroConf folks.  Mia culpa – I was wrong.

This turned out to be a driver problem with my Ethernet eth0 interface card: Realtek RTL 8139 (8100 family).  As penance – I will tell at least 3 people this week about Avahi and ZeroConf.  :)

---

