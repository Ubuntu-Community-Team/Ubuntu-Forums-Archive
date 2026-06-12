---
title: "Firestarter: how do I add a network to a rule?"
date: 2006-10-18
forum: General Help
---

### Post by daou on 2006-10-18
Let's say I want to allow all SSH connections to my computer from a network,
123.123.xxx.xxx

where x is any number (within the limits of the IP protocol of course). For example, 123.123.10.1 would be a valid IP. What would I have to type into the "IP, host or network" field in a service rule?

---

### Post by daou on 2006-10-18
Nevermind, found the answer. In CIDR format. If anyone else needs to make a network rule, a CIDR calculator can be found here:

[http://www.subnet-calculator.com/cidr.php]("http://www.subnet-calculator.com/cidr.php")

---

### Post by daou on 2006-10-18
And the answer to my own example would be

123.123.0.0/16

---

### Post by gmc on 2006-10-22
> **daou said:**
> Let's say I want to allow all SSH connections to my computer from a network,
123.123.xxx.xxx

where x is any number (within the limits of the IP protocol of course). For example, 123.123.10.1 would be a valid IP. What would I have to type into the "IP, host or network" field in a service rule?

Tell firestarter to allow connections from **network** *123.123.0.0/16*

G.

---

