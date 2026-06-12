---
title: "Dual booting two linux distros"
date: 2007-07-04
forum: General Help
---

### Post by moljac024 on 2007-07-04
Hi, after having some issues with Ubuntu i decided to try out Fedora 7 and i like it so far but now i want to install debian to test that one out, here are my partitions :

primary:

sda1 -  /boot
sda2 -  /swap
sda3 -  /home

logical:

sda4 -  / (root) (fedora 7)
sda5 -  free space (9 GB)

How would i go about installing debian's  /(root) on the free space, and being able to dual-boot with fedora ?

P.S. I left that free space intentionally for trying out various other distros, and debian 4.0 is the first in line :)

---

### Post by Nythain on 2007-07-04
when installing debian/ubuntu just tell it to create a partition on the free space and mount that partition as /

where partitions get mounted is decided during distro boot up... so you can have to different partitions, on mounted as / in fedora and the other mounted as / in debian... i would recomend two different /homes due to software version differences... from what i gather they can both and should both share the same /boot so that grub knows about them both... when you install debian/ubuntu grub will recognize fedora and add it to its menu list accordingly, similar to dual booting with xp

they can also share swap... so you are good there

---

### Post by moljac024 on 2007-07-04
I would use the same /home partition but with different user names so that shouldn't be a problem...

I was mainly worried about debian overwriting my existing GRUB, should have asked the question differently..

So, it should be safe to go ahead with the debian install ?

Should i backup something first (just in case) ?

---

### Post by Nythain on 2007-07-04
yeah... i would go ahead... it should be fine... once you get passed the partitioning issue the rest is similar to dual booting xp in all reality...

---

### Post by jespdj on 2007-07-04
Why don't you use something like [VMWare](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html) if you only want to try out another Linux distro? It's much easier than reconfiguring partitions etc.

---

### Post by moljac024 on 2007-07-04
Ok, thanks for the help, just one last question :

When partitioning in the debian install should i select my /boot partition and tell it to install GRUB there ?

---

### Post by louieb on 2007-07-04
> **moljac024 said:**
> 
primary:
sda1 -  /boot
sda2 -  /swap
sda3 -  /home
logical:
sda4 -  / (root) (fedora 7)
sda5 -  free space (9 GB)

Hello moljac024, This does not seem right.  Your partition numbers I mean. You are allowed 4 primary partitions. In order to have a logical partition you must have an extended partition. Linux always starts numbering  logical partitions with 5. As it stands now I don't believe you will be able to allocate your unused space to another partition.     [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")
But anyway heres a good place to find out about booting multiple Linux distributions. [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

---

