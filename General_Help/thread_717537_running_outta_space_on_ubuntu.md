---
title: "running outta space on ubuntu"
date: 2008-03-07
forum: General Help
---

### Post by SneakyBooBoo on 2008-03-07
hi i got a problem.

im running out of space on my ubuntu partition fast and i still need to install more apps. is there a way i can create a new partition on another drive and install them there or should i just scrap it and reinstall on a bigger drive :(

---

### Post by kesman on 2008-03-07
Try
```

sudo apt-get clean

```
to remove downloaded packages. You don't need these since they are installed, so the installers(packages) can be removed.

---

### Post by SneakyBooBoo on 2008-03-07
ok but what about setting up a new partition? i've already used apt-get clean before and it doesnt remove enough.

---

### Post by AndyCooll on 2008-03-07
You'll probably need to use GParted. Not only can this help you create a new partition, you could alternatively change the size of your partitions.

:cool:

---

### Post by Josh C on 2008-03-07
I have gparted and i'm in the same situation as the original poster.  I have dual boot vista/ubuntu 7.10.  I have freed up about 15 gb using the vista tools.  I now have that space showing as unallocated in gpart editor.  The only option it will let me choose when highlighting the unallocated space is new and when I choose that I get the error
It is not possible to have more than 4 primary partitions.
If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition

'm stuck.  I want to add that allocated space to my existing partition (the home partition for ubuntu).  All together I will end up with the 2 windows partitions and the 2 ubuntu partitions which is what I already have not counting the space I shrunk from one of the windows partitions.

please help.

Josh

---

### Post by AndyCooll on 2008-03-08
> **Josh C said:**
> I have gparted and i'm in the same situation as the original poster.  I have dual boot vista/ubuntu 7.10.  I have freed up about 15 gb using the vista tools.  I now have that space showing as unallocated in gpart editor.  The only option it will let me choose when highlighting the unallocated space is new and when I choose that I get the error
It is not possible to have more than 4 primary partitions.
If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition

'm stuck.  I want to add that allocated space to my existing partition (the home partition for ubuntu).  All together I will end up with the 2 windows partitions and the 2 ubuntu partitions which is what I already have not counting the space I shrunk from one of the windows partitions.

please help.

Josh
You'll need to resize your Ubuntu partitions by booting from your Ubuntu Live CD and then using the  GParted that's on that (or you could download a GParted Live CD and boot from that). This is because you cannot resize partitions that are currently in use.

:cool:

---

