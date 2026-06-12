---
title: "Uninstall + Grub"
date: 2007-12-12
forum: General Help
---

### Post by Borealis on 2007-12-12
Hi everyone,

I have a Dell latitude D620 laptop which is currently dual booting Windows Vista and Ubuntu. I am fairly new to Ubuntu.

The laptop only has a 40GB hard drive in which I have three partitions : NTFS(18.3GB), EXT3(2.5GB),EXT3(15.3).

I made a bit of a mess of things when I installed Ubuntu in terms of partitioning. I will be getting a new hard drive at some point but until then i need all the space for windows.

I resized some partitions and now Ubuntu won't boot (im not too concerned about this - i have a ext3 reader for windows to get all my data off). I want to format the partitions to NTFS and continue to boot off windows.

If i remove both my ext3 partitions and format them, will GRUB be removed and if so, will the laptop know where to look to boot Vista off?

Thanks

David

---

### Post by louieb on 2007-12-12
Good call. You remove Ubuntu without replacing grub 1st and poof the PC won't boot. Here how:  [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

