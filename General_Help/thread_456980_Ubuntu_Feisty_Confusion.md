---
title: "Ubuntu Feisty Confusion"
date: 2007-05-28
forum: General Help
---

### Post by Rob500 on 2007-05-28
I installed Ubuntu Feisty yesterday in a dual boot with Windows XP. When I rebooted, the boot menu appeared with the options.. fair enough. The first option was to boot in Ubuntu 2.6.20-15 generic.

This morning, I installed updates but it was only a partial upgrade for some reason. Now I have two sets of Ubuntu boot options on the boot menu: 2.6.20-16 generic and the recovery mode, then 2.6.20-15 generic and the recovery mode, then the memtest 386 thing.

What is this all about and what can I do to rectify this? I am fairly new to Ubuntu.

Many thanks.

---

### Post by Cicatrix on 2007-05-28
It is two different kernel versions.
You only really need the one with the highest number, except if it doesn't work, so to "rectify" this, you can just remove the "linux-image-2.6.20-15" package. But really it doesn't do anything bad, except use about 100 mb of space.

---

### Post by Lucifiel on 2007-05-28
My suggestion is not to touch anything. 

This is because should Feisty encounter problems, then you can try selecting a different kernel version and booting into it. Trust me, this has saved many people from hours of intensive troubleshooting. :)

---

### Post by Rob500 on 2007-05-28
> **Lucifiel said:**
> My suggestion is not to touch anything. 

This is because should Feisty encounter problems, then you can try selecting a different kernel version and booting into it. Trust me, this has saved many people from hours of intensive troubleshooting. :)

They both work, the only difference being that I have lost my desktop wallpaper in the old kernel version.

---

### Post by Lucifiel on 2007-05-28
I see but still, just leave them as it is.

---

### Post by strabes on 2007-05-28
If it really bothers you, just run this: ```
sudo aptitude remove linux-image-2.6.20-15-generic
```

Your menu.lst will be updated automatically.

---

