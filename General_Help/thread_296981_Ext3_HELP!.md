---
title: "Ext3 HELP!"
date: 2006-11-10
forum: General Help
---

### Post by jrsteffes on 2006-11-10
I cannot figure out how to make my 2nd Hard Drive useable!  I would like to create access to it from the desktop and name it storage.  I have messed with it for hours and figured out how to get it formated in ext3 but cant use it.

PLEASE HELP!

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18666   149934613+  83  Linux
/dev/sda2           18667       19457     6353707+   5  Extended
/dev/sda5           18667       19457     6353676   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   83  Linux

---

### Post by taurus on 2006-11-10
Open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo cp /etc/fstab  /etc/fstab.bak
gksudo gedit /etc/fstab
```
Now, add the following line to the end of it.

```

/dev/sdb1   /media/storage   ext3   defaults   0   2

```
Save it and run these commands at the prompt.

```

sudo mkdir /media/storage
sudo mount -a
sudo chmod 777 /media/storage
df -h

```
Enjoy...

---

### Post by aysiu on 2006-11-10
For future reference, taurus, you can save yourself some typing if you link to this tutorial:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

The extra effort you put out is commendable, however.

---

### Post by taurus on 2006-11-10
> **aysiu said:**
> For future reference, taurus, you can save yourself some typing if you link to this tutorial:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Yes, I have used your site a few times (okay, many times) before.  ;) 

> The extra effort you put out is commendable, however.

Thanks.  Just try to get some circulation in my fingers...  :mrgreen:

---

