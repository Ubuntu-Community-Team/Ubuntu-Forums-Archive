---
title: "n00b and &quot;mounting /home&quot; ?"
date: 2006-09-08
forum: General Help
---

### Post by rbprogrammer on 2006-09-08
ok, so i have been using kubuntu for about 9 months or so.... i have had a couple of problems, mainly with the graphics card on my laptop, with not being able to log into my system.  then only option i have is to reinstall kubuntu b/c i dont have the time to figure out exactly what i did and then try and fix it.  ususally i'll at least try and if i'm going no where, i'll reinstall kubuntu.

but as i look for solutions i am seeing people discussing the idea of mounting the [/home] directory on a separate partition.  now, if i install all my programs that i do manually (not through synaptic) in something like [/home/ProgramFiles] and any binaries in [/home/hbin], could i some how mount the [/home] directory on a seperate partition and if something should go wrong where i have to reinstall the OS, i could just reinstall it and then change some things to mount the home directory from that partition?

i'm thinking of this so i dont have to reinstall all my programs and reinstall/configure my settings.

is this a good idea?  if it is, how would i go about doing that?

i know how to create a new partition, i'll boot up windows and use partition magic (if that is safe to change the size of one partition in order to create another), and then i would probably add something in [/etc/fstab] (or i could use the GUI in system settings->disk and filesystems, which would edit that file for me).

---

### Post by skymt on 2006-09-08
Yes, it's probably a good idea. I don't do it, but a lot of people do. Adding a partition and setting it to auto-mount at /home will work. You can actually do the entire thing from the Ubuntu installer during the partitioning step. That would be easiest.

---

### Post by aysiu on 2006-09-08
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by Solver on 2006-09-08
It's a good idea if you think you may screw up your system often. Basically, it gives you a lot of space for experimenting with Ubuntu - even if you screw everything up, you can do a reinstall, while keeping your /home intact.

---

