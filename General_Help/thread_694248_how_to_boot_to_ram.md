---
title: "how to boot to ram"
date: 2008-02-11
forum: General Help
---

### Post by markp1989 on 2008-02-11
i have installed ubuntu on a 1gb CF card, the install takes about 700-800 mb up, the computer that i am using it in has 2gb of ram, so  i asume it must be posible to copy the entire system to ram un boot, similar to how DSL and KNoppix can, how do i go about doing this in ubuntu?

---

### Post by MighMoS on 2008-02-11
Short answer: not easily.  The reason is that if your entire system lives in RAM (probably excluding your homedrive) and your system unexpectantly shuts down, well, bad things could happen.

The long answer is that you'd have to mount a tmpfs file sytem somewhere, copy everything over on startup, bind your home drive to to a directory in there (not nessisary, but recommended), then chroot into that tmpfs filesytem. On shutdown, you'd have to copy EVERY changed file *back* over to the hard drive which could lead to very slow shutdown times.

It doesn't sound very stable or fun, but I assume it would be *quite* fast if you got it working.

I know these aren't step by step rules for what you wanted, but its the general idea.

---

### Post by markp1989 on 2008-02-12
i thought it would involve installing a new kernel that supported the "toram" paramater, but i have no idea how to do that or if that is how to do it.

---

### Post by markp1989 on 2008-04-01
bump. any one know how to do this, my current install is 700 mb

i no that its posible to boottoram , but i dont know how, does any one know how?

thankyou in advanced

---

### Post by intense.ego on 2008-04-27
For anyone that needs it:

[https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)

---

