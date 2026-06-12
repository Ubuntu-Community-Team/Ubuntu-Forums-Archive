---
title: "Was there ever a solution for the nforce problems? (no network)"
date: 2006-11-20
forum: General Help
---

### Post by Morientes on 2006-11-20
Hi

I have just installed ubuntu on my new Asus P5N32-SLI Premium and the network refuses to work. It finds the onboard network adapters ok but they simply cant connect. They get no IP-adress, they never receive any DHCPOFFERS and setting the IP manually doesnt help either.
I have seen several posts on here about problems with the nforce chipset (my mobo uses nforce 590-sli intel edition) so could this still be the problem or should these problems be fixed in edgdy? I have tried the trick with unplugging the computer for a while and then booting directly into linux...and it still doesnt work.

Any ideas? I would be quite sad if I couldnt use ubuntu on my new comp...

---

### Post by anaconda on 2006-11-20
I think I have nForce 430
but I had the same problem, and I had to go to system/arministration/network, and disable the netvorking card and then enable it again. This made it working until next reboot (dont know why?)
Since then I installed the nvidia drivers and havent had problems..

---

### Post by Morientes on 2006-11-20
Whats the nvidia drivers and how do I install them?

Also I heard something about that it should work on Kubuntu..can anyone confirm this?

---

### Post by Morientes on 2006-11-22
bump!

---

### Post by jeff47 on 2006-11-26
I'm having the same problem with my nForce board (Gigabyte GA-M55SLI-S4).  Disabling/re-enabling the card in network manager doesn't fix it.

---

### Post by Morientes on 2006-11-27
Please someone! There must be a solution to this problem?

I have also tried in Kubuntu and it has the same problem.

HEEELP!

---

### Post by Morientes on 2006-11-27
My problem is solved!!

All I needed to do was add irqpoll as a parameter to the kernel in grub!

Yeeees! Writing from Kubuntu now!

---

