---
title: "general question on wine"
date: 2007-11-03
forum: General Help
---

### Post by g.a. on 2007-11-03
Hi,

I'm on the way to switch from winxp tu kubuntu 7.04. There is only one application under winxp that does not have a linux version. So my hard disk is partitioned and I have a double boot, I use winxp once a week to run this application and update some files.

My basic question is: is wine the solution of my problem? from wine can i run an application already installed in the ntfs partition? this application can delete and save files in the ntfs partition?

thanks in advance,
g.

---

### Post by haldean on 2007-11-03
You should be able to run the program from your NTFS partition; whether or not it'll write to the partition is a different story. Also, it won't have access to it's old configuration files or the registry, because it's being run from somewhere different. You could chroot into your NTFS partitiong, but your best bet is probably to reinstall the program using Wine into your Linux partition.

---

### Post by g.a. on 2007-11-03
thanks,

there are some other minor configuration aspects that I still need to tune but the installation under wine-linux is probably the cleanest thing to do.

well, i need to fdisk to 'stole' some space from ntfs to ext3 and this is not so easy for me...

bye,
g.

---

### Post by haldean on 2007-11-03
You might have an easier time changing around partitions with GParted... install it with ```
sudo apt-get install gparted
```

---

### Post by luisromangz on 2007-11-03
For writing support in a ntfs partition, you should use the ntfs-3g driver. And the ability of Wine to run your software depends on that software, the wine project has a web in which they list the compatibility of different software with Wine.

---

### Post by mahousaru on 2007-11-03
The main problem with running program which were initially installed via windows is the bane of any techies life; the registry*.  Programs that work as PortableApps should work, but as soon as it needs to have settings in the registry you are in for a world of pain trying to transfer them into wine.

* What numpty in their right mind came up with the registry?  A lot of things in Windows annoys me, but that is the only thing that drives me into blind rage!

---

### Post by haldean on 2007-11-03
Unless you still have windows installed, because then you can get a copy of the registry keys for the program...

---

### Post by mahousaru on 2007-11-03
> **haldean said:**
> Unless you still have windows installed, because then you can get a copy of the registry keys for the program...

That is true, but dependant on the program.  I still have nightmares about the ones that use uniquely generated keys based on the user account.

---

### Post by haldean on 2007-11-03
Dear god... they did that?
Wow.
Windows developers need to get themselves a life. And a healthy dose of GPL.

---

### Post by g.a. on 2007-11-03
thanks to all,

i think i'm going to try to install the application under linux using wine and i'm going to post another thread about the use of gparted since i now have 10GB unused under the ntfs partition...

g.

---

