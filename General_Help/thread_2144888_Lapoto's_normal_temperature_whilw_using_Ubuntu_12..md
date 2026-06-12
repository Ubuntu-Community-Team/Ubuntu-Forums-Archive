---
title: "Lapoto's normal temperature whilw using Ubuntu 12.04"
date: 2013-05-13
forum: General Help
---

### Post by tushar21nov on 2013-05-13
[B]I have some questions:
 1. What is the normal temperature of a laptop while using Ubuntu 12.04 ? (specially the system, HDD, Processor and Motherboard)
 2. How much temperature will harm the laptop (system, hdd, precessor and matherboard)
 3. Is there any software which can be used to determine the temperature of the system, HDD, Processor and Motherboard ?[/B]

I am using Ubuntu 12.04 on my Laptop. It is a Dell INSPIRON N4050. What will be the normal temperature of my laptop while using Ubuntu 12.04 ? 

Please let me know as soon as possible.

---

### Post by pqwoerituytrueiwoq on 2013-05-13
depends on the hardware what normal is, that also determines the max temps
[http://www.specsbox.com/628/dell-inspiron-n4050-14-laptop.html](http://www.specsbox.com/628/dell-inspiron-n4050-14-laptop.html) - specs for the OP's system
use the [FONT=courier new]hddtemp /dev/sda[/FONT] command for the HDD
use the [FONT=courier new]sensors[/FONT] command for the other temps
use the [FONT=courier new]aticonfig --od-gettemperature[/FONT] command for a AMD GPU temperature if you have one, that command may be outdated

---

