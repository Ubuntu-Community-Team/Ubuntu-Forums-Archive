---
title: "icmp_seq=7 Destination Host Unreachable ...somebody help."
date: 2015-11-03
forum: General Help
---

### Post by hoboy on 2015-11-03
I am trying to ping an ubuntu 14.04 machine witch is on same net I am on
but getting this "icmp_seq=7 Destination Host Unreachable
"

---

### Post by ajgreeny on 2015-11-03
Can you ping the router which both machines are attached to?

---

### Post by hoboy on 2015-11-04
> Can you ping the router which both machines are attached to?
How do I do that ?

---

### Post by ajgreeny on 2015-11-04
In the same way, I presume, that you tried to ping the machine that you can't reach, ie with command ```
ping -c 5 192.168.#.#
```where the **192.168.#.#** is the IP of your router.

---

