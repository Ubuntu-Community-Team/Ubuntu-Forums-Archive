---
title: "Problem with the terminal"
date: 2007-11-09
forum: General Help
---

### Post by Lufkin on 2007-11-09
Hi.

When I'm trying to install something with the terminal, they are saying :

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What is the problem ? 

Thanks a lot !

---

### Post by rsambuca on 2007-11-09
You can only have one installation program running at a time.  In order to complete your task, you will have to close your Synaptic Package Manager and/or your Add Remove Packages program.

---

### Post by ppl on 2007-11-09
Hi, I think you need sudo apt-get install ??
to give you administrator right to make it working

---

### Post by ardchoille42 on 2007-11-09
> **Lufkin said:**
> Hi.

When I'm trying to install something with the terminal, they are saying :

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What is the problem ? 

Thanks a lot !

Do you have another package manager app (aptitude, synaptic, apt-get, adept, etc) running? if so, close it. You can only run on at a time.

---

### Post by Lufkin on 2007-11-09
Ah, okay, Synaptic was running at the same time ... :roll: Thank you ! ... And sorry for this stupid question, lol ! ... :P

---

