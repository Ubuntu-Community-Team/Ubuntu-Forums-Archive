---
title: "Automatically mount drive"
date: 2007-05-27
forum: General Help
---

### Post by AWerner32 on 2007-05-27
i have several partitions on my hard drive, is there a way i can make the computer automatically mount a partition on startup rather than having to go mount it manually every time i log on?

---

### Post by ryanVickers on 2007-05-27
I think there is a file somewhere that says where all the partitions are, what to mount them as, and so on.  See if anyone remembers where this is or what I'm talking about - I know it exists!

---

### Post by taurus on 2007-05-27
You can add entries for those partitions in /etc/fstab to have them mount automatically upon boot.  What's the output of this command from a terminal and which release (Dapper, Edgy, or Feisty) are you running right now?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by tact on 2007-05-27
...its /etc/fstab

Have a look at it.  back it up before you edit it.  if you edit it do so as root (sudo).  after editing you can have it executed without rebooting by typing at a prompt: ~$ sudo mount -a

I am not so well versed with the options to help you with concrete suggestions.  Below is a sample - dont use this as it is! - the actual line will depend on the file system and options you want to use.


======================
The basic format is:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

## eg..
/dev/sda3               /                      ext3    defaults,errors=remount-ro 0       1

## or using UUID references
UUID=fa4d5196-9d3b-49ef-8d30-f8d5f78e3266     /home           ext3    defaults        0       2
=====================

---

