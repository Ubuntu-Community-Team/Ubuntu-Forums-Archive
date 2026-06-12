---
title: "5 linux,xp seperate home on same hdd"
date: 2008-05-15
forum: General Help
---

### Post by medic2000 on 2008-05-15
Hi everyone! I want to partition my hdd so i can install a lot of linuxes and xp. Also i will make partition for installing games and seperate shared /home directory(i know it can cause problems).Any suggestion shall appreciated.

Will it be okay to make /stash/home_arch, /stash/home_ubuntu etc...?

---

### Post by Oldsoldier2003 on 2008-05-16
> **medic2000 said:**
> Hi everyone! I want to partition my hdd so i can install a lot of linuxes and xp. Also i will make partition for installing games and seperate shared /home directory(i know it can cause problems).Any suggestion shall appreciated.

Will it be okay to make /stash/home_arch, /stash/home_ubuntu etc...?

Yep you'll have to mount them in your fstab though.
example fstab entry:

```
/stash/home_ubuntu /home none bind
```
This depends on /stash being present and mounted before attempting to mount /home

 Personally, I don't think a separate home partition is the answer I prefer a separate data partition and symlinks, leaving each distro with its own home.

---

### Post by medic2000 on 2008-05-18
Thanks for the answer OldSoldier2003. Can you explain a little more about your partition type?(the symlinks etc..) I want to see your partiton table if possible.

And stash will also be my data partition where i store all my music,films.  How about the root partition. How much space do you allocate it? 

One last thing. How can i tell ubuntu to install /home files there to separate partition before installing ubuntu?

---

