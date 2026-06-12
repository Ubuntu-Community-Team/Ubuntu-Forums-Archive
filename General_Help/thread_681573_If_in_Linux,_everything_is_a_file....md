---
title: "If in Linux, everything is a file..."
date: 2008-01-29
forum: General Help
---

### Post by hoboken on 2008-01-29
Does that mean that I can do a backup of my entire OS just by copying and pasting it to an external hard disk? 
I think the only problem would probably be that the partitions would have different names afterwards. You see, being a partition n00b when I first began messing with Linux, I topped out at 4 partitions. Now I want to move to another distro and I need to do a major rearranging job. So... back to the question. Can I do a backup simply by pasting my / folder?

---

### Post by Cochise on 2008-01-29
i dont know the answer to your question but love the avator, commander keen rocks

---

### Post by erginemr on 2008-01-29
The answer to your question is YES, but with the exception of a few virtual folders. For backing up your entire system to a smaller-sized backup archive, I suggest you to follow this excellent guide:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by erfahren on 2008-01-29
to the first question, yes. In fact, this HowTo shows how to compress the entire filesystem into a compressed archive: [http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

It sounds as if you just want to back it up to do some repartitioning. If that is the case then you can use GParted with the Ubuntu LiveCD - just boot up into the LiveCD and run "sudo gparted" in the terminal.

GParted does a good job with resizing, moving amd creating new partitions (I've done it with it).
see the documentation at: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

it would be easier to keep your current install in the same place in the order of the partition table - in other words - if it is at /dev/sda3 now you could try to keep it in that same *position* on the disk (the third partition). 

There are a couple of things you need to be aware of. One is the /etc/fstab uses [UUID](http://linux.byexamples.com/archives/321/fstab-with-uuid/) to mount the partitions - those would be subject to change. You could change your /etc/fstab to go by the partition number until you are done instead.
```

[color="blue"]INSTEAD OF:[/color]
# /dev/sda8
UUID=812d6c0e-a20c-4ce5-8c99-54b45e8b79d0 /               ext3    defaults,errors=remount-ro 0       1

[color="blue"]YOU COULD JUST USE:[/color]
/dev/sda8     /     ext3     defaults,errors=remount-ro 0       1

```
[this page](http://users.bigpond.net.au/hermanzone/p10.htm) at hermanzone's site has some info on that as well (there's a page on partitioning basics too).

The other is that if the partition table changed and your bootloader (probably GRUB) was moved to another partition along with Ubuntu (for instance) you'd need to reconfigure it. see: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Attached is a screenshot of my partitions in GParted. Awhile back I shrunk down both my Ubuntu 7.04 root (/dev/sda5) and my Ubuntu 7.04 /home (/dev/sda6) and created partitions to install Xubuntu 7.10

GRUB is in my Ubuntu install and since I didn't change its *position* in the table I didn't have any problems afterwards.

--- anyway, hopefully that will give you some information to help you figure it out. good luck!

---

