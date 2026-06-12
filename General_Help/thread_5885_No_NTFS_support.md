---
title: "No NTFS support"
date: 2004-11-22
forum: General Help
---

### Post by mjjohansen on 2004-11-22
I am wondering. I just installed Ubuntu, which is just beautiful. I cracked WinXP in the process, which was my intention. I kept my NTFS storage partition, though, so I could transfer the data without having to burn 40 GB of backups (y'know?).
Now, however, I don't seem to have NTFS access. From the howto for automounting, I gathered that it was standard with NTFS access, but I don't have NTFS in /proc/filesystems. 
/me is wondering. Any pointers? Just an installation glitch? Everything else, except hotplugging my USB Flash drive, works.

---

### Post by spirospr on 2004-11-23
Well i can't see in ubuntu my other NTFS partitions too. I enabled samba to connect to my winodws network with succes but i can not see the other partitions on my laptop. I think some configuration should be done. I'll try to find a solution...

---

### Post by ubuntu_demon on 2004-11-23
I have an ntfs partion I want to read and write to as a user on hda5  and I like to name it "data".

sudo mkdir /mnt/data
sudo pico /etc/fstab

and add the following line :

/dev/hda5       /mnt/data       ntfs    umask=0222      0       0

PS see : [http://kitech.com.my/ubuntu/4.10/index.html](http://kitech.com.my/ubuntu/4.10/index.html)

---

### Post by p!=f on 2004-11-23
If you use stock Ubuntu kernel there's no support for NTFS write.
```

 * 15:36:26 * pef @ agonicus *
[~] > grep NTFS /boot/config-2.6.8.1-3-k7
CONFIG_NTFS_FS=m
# CONFIG_NTFS_DEBUG is not set
# CONFIG_NTFS_RW is not set

```

---

### Post by ubuntu_demon on 2004-11-23
m stands for manual right ?
So you have to manual load a module or something like it? Or do you have to recompile the kernel ?

---

### Post by p!=f on 2004-11-23
M stands for a module.
And yes if you want NTFS write support you have to recompile your kernel and turn that support on. Note that writting onto the NTFS partition might break things down and this options is considered highly experimental.
You've been warned. :)

If you mount NTFS partition, the module should be loaded automagically but you can modprobe to load it by hand if you want to.
```

 * 16:39:17 * pef @ agonicus *
[~] > sudo modprobe ntfs

```

---

### Post by mjjohansen on 2004-11-23
I am not the man for harsh language on debating forums. But:
I could kiss you.
The straightforward instructions at [http://kitech.com.my/ubuntu/4.10/index.html](http://kitech.com.my/ubuntu/4.10/index.html) did it.

---

### Post by ubuntu_demon on 2004-11-23
I don't understand why ntfs writing is turned off by default. I thought it was experimental in kernel 2.4 but not anymore in 2.6.

---

### Post by p!=f on 2004-11-23
[QUOTE=demon666_nl]I don't understand why ntfs writing is turned off by default. I thought it was experimental in kernel 2.4 but not anymore in 2.6.[/QUOTE]
Because you can lose datas on NTFS partition. I know that. :)

Until you force Micro$oft for releasing the source code for NTFS, it probably still will be an experimental option. :)

---

### Post by ubuntu_demon on 2004-11-23
Those MS suckers!

---

