---
title: "Two Grubs- Confusing"
date: 2013-01-07
forum: General Help
---

### Post by fantab on 2013-01-07
I have both Precise and Quantal installed on separate partitions on same HDD.

While installing Quantal, in my forgetfulness I let it install Grub. No issues so far. Machine works fine.

However, whenever there is Grub version upgrade on either versions of Ubuntu or if I run update-grub in either the Grub gets replaced by the version where the upgrade or update happened.

Let me be more clear. When I run update-grub in Precise I get the Grub from Precise and when I update-grub in Quantal I get Quantal-grub. Both work fine and no issues in performance. It just that it is an inconvenience. (I have my favourite Wallpaper set as background in one. And offcourse my default OS keeps changing accordingly).

**I would like to REMOVE one grub completely, say from Precise. How do I go about it?**

Can I just run :

$ sudo apt-get remove grub

Or is there more to it?

I was also thinking of keeping 'em both and configuring them both alike... not sure if this will cause any problems in the future. 

Confirmation and Advice needed.

Thanks......

---

### Post by dcstar on 2013-01-07
> **fantab said:**
> 
.........
Or is there more to it?

I was also thinking of keeping 'em both and configuring them both alike... not sure if this will cause any problems in the future. 

Confirmation and Advice needed.

Thanks......

You only ever use one thing to boot a system, so just choose (and boot off) the system which is to be the boot controller and set it with:
```

sudo dpkg-reconfigure grub-pc
```
Then boot up the other Linux version and totally remove Grub so any updates don't stuff-up the other system.

---

### Post by fantab on 2013-01-07
Okay.. I will REMOVE one.

Thanks dcstar fro the quick reply.

---

