---
title: "vfat partition suddenly not mounted at boot"
date: 2007-02-12
forum: General Help
---

### Post by hansdan on 2007-02-12
I've been using Edgy on my laptop for a few months and everything has been working great. I've set it up as a dual boot (XP) so I've got a vfat partition as OS share. 

Suddenly, the vfat partition is not mounted during boot. I cannot think of any changes that would have caused this. fstab is unchanged and I can manually mount the partition without problem. The related line in fstab is: 
UUID=06CB-6986  /osshare        vfat    defaults,utf8,umask=007,gid=46 0       1

Anyone got any idea what could have happened and more important how to fix this?

Cheers,
Hans

---

### Post by taurus on 2007-02-12
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace this line in there from

```
UUID=06CB-6986 /osshare vfat defaults,utf8,umask=007,gid=46 0 1
```
to the actual partition.

```
/dev/hda2     /ossshare   vfat   defaults,utf8,umask=007,gid=46   0   1
```
Assuming /dev/hda2 is your fat32 partition.

---

### Post by hansdan on 2007-02-12
wow, that was fast

Yep, that worked. THANKS!

I guess I should change all partitions to use the actual partition.

Out of curiosity, why did it work for a while and then stopped?

Hans

---

### Post by taurus on 2007-02-12
Maybe because you reformat it or change something to it.  Therefore, the UUID is not the same anymore and because of that, it couldn't mount using the old UUID.  But if you change it to an actual device, then it will always be the same even if you format or convert it to another filesystem.  The only thing you need to modify in /etc/fstab is the new filesystem for it.

---

