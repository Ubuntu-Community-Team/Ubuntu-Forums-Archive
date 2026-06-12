---
title: "Huge problems with mdadm"
date: 2013-12-05
forum: General Help
---

### Post by neoid2 on 2013-12-05
Hi,

Since I've switched from Windows Server to Ubuntu I have struggled alot with mdadm software raid. I guess my HBA is not one of the best (RocketRaid 2720SGL), but mdadm has not proven to be very stable.
Today, for some reason, I got this when booting the server: [http://i.imgur.com/Fg7vPkU.jpg](http://i.imgur.com/Fg7vPkU.jpg)

It looks to me that the drives order has been changed for some strange reason. Before doing anything I tried to run "[COLOR=#000000][FONT=monospace]mdadm --examine /dev/sd[bcdefghijklmn]1 >> raid.status" in order to have some kind of "backup" as far as I understood that part.. Next I tried quite a few things, even re-creating the array, but without any luck. I'll provide any information that is needed.. please help me save my data. :(


[/FONT][/COLOR]

---

### Post by SaturnusDJ on 2013-12-07
Recreating is a last resort. Did you use the --assume-clean flag? Otherwise data most likely is destroyed.

Can you post all those examine's here?

---

