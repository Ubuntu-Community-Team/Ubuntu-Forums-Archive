---
title: "Problem after upgrading"
date: 2005-07-16
forum: General Help
---

### Post by mandos on 2005-07-16
Well, i have made a dist-upgrade and after rebooting i get the next error:

> kernel panic-not syncing:VFS:unable to mount rootfs on unkown-block(0,0) 

It doesnt matter what kernel do i choose, i get the same error every time.

What should i do to correct the matter?

Thanks

---

### Post by adrian440 on 2005-07-16
What filesystem were you using? You could try and boot a live-cd of some sort and use that to look, if you can't remember or don't know. 
What were you upgrading from (& to)?

---

### Post by art on 2005-07-17
I compiled a kernel, so it wasn't a dist-upgrade, but I had a similar problem. So the thing was I needed a initrd.img. 
As was posted in another thread on this forum this are the steps

mkdir /lib/modules/"the kernel you run"
cp -a /lib/modules/"the kernel you run"/kernel/security/capability.ko  /lib/modules/"the kernel you run"boot/
mkinitrd -o /boot/initrd.img-"the kernel you run"  "the kernel you run"

So if you can boot a live CD you could do this I guess.

---

### Post by mandos on 2005-07-17
I finally had to format that partition because there wasnt any way to solve the problem. I tried everything I could but it was not posible to return to the previews situation.


 ](*,)  ](*,)  ](*,)

---

