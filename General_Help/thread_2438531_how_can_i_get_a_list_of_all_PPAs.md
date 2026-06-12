---
title: "how can i get a list of all PPAs?"
date: 2020-03-13
forum: General Help
---

### Post by Skaperen on 2020-03-13
how can i get a list of all PPAs?

---

### Post by oldfred on 2020-03-13
This should show what you have installed.
ls -l /etc/apt/sources.list.d/*.list

---

### Post by Skaperen on 2020-03-14
sorry for being unclear.   i want a list of what i, or anyone else, *could* install.

---

### Post by Frogs Hair on 2020-03-14
I don't know of any comprehensive list and if there is you have to get it from Launchpad. There are thousands of packages in the PPA pool for any given release and Launchpad is no longer the only hosting option. 

 [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

---

### Post by TheFu on 2020-03-14
Impossible.  

Anyone in the world can make a PPA.  You could, i could.  Your sister's, brother's, friend, can.
There cannot be a comprehensive list, obviously, since that would include tracking, which nobody wants.

There may be a way to get a list from launchpad, but that would be a tiny fraction of the PPAs out in the world.

---

