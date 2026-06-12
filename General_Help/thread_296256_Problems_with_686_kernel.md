---
title: "Problems with 686 kernel"
date: 2006-11-09
forum: General Help
---

### Post by Orion Cthulhu on 2006-11-09
I was trying to figure out which kernel I had to use for my Pentium 4 D, so I installed the following packages with synaptic:
linux-686-smp (2.6.15.25)
linux-doc-2.6.15 (2.6.15-27.48)
linux-headers-2.6.15-27-686 (2.6.15-27.48)
linux-image-2.6.15-27-686 (2.6.15-27.48)
linux-image-686 (2.6.15.25)
linux-restricted-modules-2.6.15-27-686 (2.6.15.12-1)
linux-restricted-modules-686 (2.6.15.25)
When I rebooted, I selected (in grub) the 686 kernel, but it wasn't able to mount the file tree! I can't even enter the login screen. Can someone give me a hint of what I have to do? (I can still use Ubuntu when I select the 386 kernel in grub)
PS: I use Dapper Drake (6.06) and I'm new to Ubuntu and Linux
PS2: I wasn't really sure if I had to use the 686 kernel or the 686 with SMP enabled, so I choosed the 686 with SMP.
PS3: I apologize for using such a broken english. ^^''' 
PS4: Should I give you information about my pc?
Thanks. =)

---

### Post by autocrosser on 2006-11-09
Try in a terminal: sudo apt-get install linux-image-686

That should clear up your problems

---

