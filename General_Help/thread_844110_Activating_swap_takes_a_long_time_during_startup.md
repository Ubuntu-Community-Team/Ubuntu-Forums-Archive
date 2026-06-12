---
title: "Activating swap takes a long time during startup"
date: 2008-06-29
forum: General Help
---

### Post by malderhout on 2008-06-29
I succesfully installed wubi (with Wubi-8.04.1-rev503) for Vista (SP1), but every time I start Ubuntu, the acativation of the swap file takes a long time. I have already defrag the swap file under Windows Vista.

Somebody can help?

Greetings
Maikel

---

### Post by ago on 2008-06-30
You can turn swap off from ubuntu, then create a new swap file, and format it as swap

sudo -s
swapoff -a
dd if=/dev/zero of=/host/ubuntu/disks/swap.disk bs=1M count=256
mkswap /host/ubuntu/disks/swap.disk
swapon -a
exit

Or you can turn off swap completely by commenting out the relevant section in /etc/fstab

---

### Post by malderhout on 2008-07-02
Thx 

Succesful commenting out swap line in /etc/fstab

---

