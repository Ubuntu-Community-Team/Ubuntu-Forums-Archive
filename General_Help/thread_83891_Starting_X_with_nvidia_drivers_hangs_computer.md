---
title: "Starting X with nvidia drivers hangs computer"
date: 2005-10-29
forum: General Help
---

### Post by vhogemann on 2005-10-29
Hello folks,

I just swiched my MotherBoard and processor, from a ASUS A7N266 + Athlon XP 1800 to an ECS 760GX-M + Semprom64 2600+.

Almost everything went just fine, but my GeForce 440 MX now refuses to work with the nvidia-glx drivers. The machine hangs the moment X tries to start.

My kernel version is 2.6.12-9-k7.

Can anybody help me?

THX

---

### Post by ippiraman on 2005-10-30
Don't know if this would work, but could you try running this...

sudo nvidia-glx-config enable

I was wondering if you changed from a different kernel?

HTH

---

### Post by Qrk on 2005-10-30
If you changed kernels (say to the k7) after installing the nvidia package, xorg might not work. Then you just need to install the restricted modules for your new kernel. 

sudo apt-get install linux-restricted-modules-k7

With this, you shouldn't have to reconfigure xorg, because you didn't change anything about it by changing kernels. 

But this fix might not work; there are a lot of things that can break x.

---

### Post by Breezy Badger on 2005-10-30
what do you mean it hangs, does it freeze? start? go black screen?

need more info

---

### Post by vhogemann on 2005-11-02
Actualy I found out that the linux-restricted-modules-k7 provides nvidia module with a lower version than the nvidia-glx expects!

Sometimes X refuses to start, sometimes it freezes the whole machine... no response from keyboard, can't ssh to it, dead... looks like a kernel panic to me.

---

### Post by wylfing on 2005-11-02
You don't need linux-restricted-modules-k7, you need linux-restricted-modules-2.6.12-9-k7.

---

