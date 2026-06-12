---
title: "need help installing arch linux in virtualbox"
date: 2007-07-15
forum: General Help
---

### Post by TheRingmaster on 2007-07-15
I am trying to get arch installed in a virtualbox virtual machine. I get to the point where you pick the file system and then I get this error. I posted a screenshot to try and explain my problem to you. Hopefully some brainy dude will see this and come up with a really good answer.:KS

I have been researching arch linux for a few days now and I am liking it more and more. KDE-mod looks really awesome!

---

### Post by strider1551 on 2007-07-16
Could you tell us what /dev/tty5 says?  (Hitting ctrl+alt+F5 should take you there)

---

### Post by TheRingmaster on 2007-07-16
I already solved this problem by creating a new virtual machine for arch. I have successfully installed a base arch system.

---

### Post by troymcdavis on 2007-11-26
I know this thread was old, but I ran into the exact same problem. The terminal output said something to the effect of:

```
Error: 7057 blocks allocated, only 3796 blocks available.
sfdisk: bad input
```

My diagnosis is something like this:
With the automatically expanding virtual hard disk, there is some sort of discrepancy in the available space when the machine makes the initial request to suggest values for the different partitions, and then when it begins actually making the partitions, thus leading to the error. That, or the deafault values correlate in no way to the available space, and thus when it goes to make the partition, it finds less space than you requested, so it exits and spits out the error.

Solution:
Request less space, or create a fixed size virtual disk big enough for the installer. I let it have the default values for all the partitions, but only gave it 3000 blocks for home, and everything went smoothly.

---

