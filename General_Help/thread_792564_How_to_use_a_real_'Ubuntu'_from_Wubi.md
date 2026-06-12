---
title: "How to use a real 'Ubuntu' from Wubi"
date: 2008-05-13
forum: General Help
---

### Post by Arkold Thos on 2008-05-13
Heya, I have been a Debian Sid user for years, but I have bought a new computer and I have several problems with the hardware. Ubuntu at least doesn't have that much. Before testing Ubuntu I have read about Wubi, so I installed it. Now I am happy with Ubuntu and I want to move completely to Ubuntu, making partitions and stuff.

Anyone know if that is possible? And if it is, how?

Thanks.

---

### Post by zenwalker on 2008-05-13
Well just boot u r system from Ubuntu Cd, then ull get a nice desktop from Live cd feature of it. Then on the desktop ull see icon. Doublie clicking it will launch an installation process. Then move on as u see things on screen. Then a Gparted Tool will be presented when it comes to partitioning the HDD. Allocate a partition for / and another for /home (if u want to keep all personal long time data). ANother for SWAP (Usually it will double size of RAM). If u have huge RAM of abt 2 Gigs, then u can keep lil space for SWAP. Then move on.

---

### Post by Arkold Thos on 2008-05-13
Okay, I tough there was a tool to do that from a ubuntu installed with wubi. thanks.

---

### Post by Vadi on 2008-05-13
I do believe there's a howto for moving over, but as for a user-friendly tool to migrate, that hasn't been finished yet.

---

### Post by Arkold Thos on 2008-05-13
Well, just reinstalled. All working for now :)

---

### Post by sunstriker on 2008-05-14
I've read the ubuntu devs are working on a tool that makes it possible to migrate a wubi to a native partition. As for now I would tar my home dir and untar it in a fresh native install if i want to keep my settings and files....

---

### Post by ago on 2008-05-14
There is LVPM but at the moment 8.04 is not supported yet. There will be a long term solution soon. In the meantime I will provide a simple script to patch the hole...

---

