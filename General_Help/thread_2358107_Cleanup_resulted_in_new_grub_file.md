---
title: "Cleanup resulted in new grub file ?"
date: 2017-04-09
forum: General Help
---

### Post by raleigh3 on 2017-04-09
I ran these.
```

sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

Why did it generate a grub file ?

```
Generating grub configuration file ...
Found background image: Alien_Sunset_256_colors.png
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic

```

---

### Post by deadflowr on 2017-04-09
Not new, just updated.
When you ran the autoremove command that removed the older, and obsolete kernel images,
When that happens grub's config (grub.cfg) needs to be updated so that it no longer lists those now non-existent kernels.
It does this every time you remove and install a new kernel.

---

### Post by raleigh3 on 2017-04-10
Thanks for the explanation.

How often is a new kernel installed ?

I still have the same version of Ubuntu-Mate for at least 6 months.

---

### Post by deadflowr on 2017-04-10
> **raleigh3 said:**
> Thanks for the explanation.

How often is a new kernel installed ?


Indeterminate
Could be two months.
Could be two days.
More often depends on what security issues arise. 
And often times after a security update for the kernel comes, a day later so does a regression fix that security update caused.
There is no set time table for kernel updates.

---

### Post by raleigh3 on 2017-04-10
Thanks again.

---

