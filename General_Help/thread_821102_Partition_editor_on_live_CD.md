---
title: "Partition editor on live CD?"
date: 2008-06-06
forum: General Help
---

### Post by Greenbean209 on 2008-06-06
Ok so I'm trying to make a partition for windows 98 and I heard there is a partition editor included with ubuntu. Someone told me it can't be used if your trying to resize the partition your running it on. They said it could be used on the live CD. So how could I get to the partition editor?

---

### Post by iaculallad on 2008-06-06
> **Greenbean209 said:**
> Ok so I'm trying to make a partition for windows 98 and I heard there is a partition editor included with ubuntu. Someone told me it can't be used if your trying to resize the partition your running it on. They said it could be used on the live CD. So how could I get to the partition editor?

The partition editor is called GParted. Boot using the Ubuntu LiveCD until you reach the desktop. Navigate to System->Administration->Partition Editor to open GParted.

---

### Post by nick_h on 2008-06-07
You can install GParted with:
```
sudo apt-get install gparted
```
or by using the Synaptic package manager.

---

### Post by eZtaR on 2008-06-07
> **nick_h said:**
> You can install GParted with:
```
sudo apt-get install gparted
```
or by using the Synaptic package manager.

But don't use it to partition while on the installed ubuntu distro ;)

---

