---
title: "Energy Manager port? Alternative?"
date: 2015-01-25
forum: General Help
---

### Post by josh112 on 2015-01-25
I'm not sure if this article is appropriate for this section but I have Ubuntu on my Lenovo yoga 2 11 and apparently the internal battery slowly loses it's maximum battery life over time. The energy manager on the yoga 2 11 helped reset to maximum by draining and refilling it. Is there a port for the energy manager for Ubuntu or is there an alternative battery reset tool for Ubuntu? Thanks for reading, please help.

---

### Post by tgalati4 on 2015-01-26
The built-in battery monitor in the standard desktop tracks the battery capacity over time.  I think the Energy Manager just estimates the total battery capacity and uses that to better track the battery-time-remaining.  Draining and recharging the battery does not improve the battery life for lithium batteries.  You get 3 years or 300 charge cycles, whichever happens first.  Most IBM/Lenovo computers have decent recharge circuits such that the battery life is already maximized through fast charging and then trickle charging when full.  I bet your charging cord or the battery light goes from yellow to green to indicate this.

Click on the battery icon in Ubuntu and look through the statistics.  It's a sophisticated algorithm and probably similar to Energy Monitor.  You need to use your battery 10 times or so to collect enough information about the battery's capacity to make better time estimates.  This is probably what Energy Monitor was doing.

---

