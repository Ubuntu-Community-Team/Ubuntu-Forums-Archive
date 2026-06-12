---
title: "cloning using command from terminal but have some problem!!! invalid port System!!"
date: 2007-11-04
forum: General Help
---

### Post by S@nM0_0n on 2007-11-04
hi,
 i got some problem with cloning... i open the system port 9000 from destination computer with command "nc -l -p 9000 | dd of=/dev/sda" from terminal and when i start the port 9000 from source computer it gives me "invalid port system" and i can't clone anymore.... pls pls give solution for this, i need it urgent... i m quite new to ubuntu...Thanks in advance

---

### Post by petteriIII on 2007-11-05
> **S@nM0_0n said:**
> hi,
 i got some problem with cloning... i open the system port 9000 from destination computer with command "nc -l -p 9000 | dd of=/dev/sda" from terminal and when i start the port 9000 from source computer it gives me "invalid port system" and i can't clone anymore.... pls pls give solution for this, i need it urgent... i m quite new to ubuntu...Thanks in advance

Isn't dd command incomplete ? Maybe something like if=/dev/sdb must be appended to it ?

---

### Post by geirha on 2007-11-05
The command on the destination computer looks correct at least. What program is giving the "invalid port system" message?

---

