---
title: "Ubuntu and Windows"
date: 2007-11-02
forum: General Help
---

### Post by Koziasty on 2007-11-02
Hi there.

I have a problem - I need to reinstall windows - for games -, but i really am afraid of playing around with gparted and my partitions (theres some stuff id rather not lose). 

I remember, I read somewhere that it was possible to create a space (a virtual drive) for ubuntu and boot it up from grub as a normal system.
Would that be possible with windows, too?

---

### Post by p_quarles on 2007-11-02
This might not be the answer you're looking for, but I think it's a good one: If you have stuff on your hard drive that you'd rather not lose, you need to find a way to back it up. Irrespective of whether you fiddle with partitions, you have absolutely no guarantee that the information you're keeping on one storage device is going to be there tomorrow. 

Anyway, I suspect what you're remembering reading about it Wubi, and there's nothing like that available for installing Windows. You can certainly run Windows as a virtual machine, but you'll get pretty lousy performance with any graphics-intensive apps, including games. 

Your best bet here is to back up everything you want to keep, use gparted to make some free, unformatted space (and resizing an ext3 partition is actually pretty safe, as these things go) and doing a regular Windows installation.

---

### Post by Koziasty on 2007-11-03
thanks. Ill give it a try, then

---

### Post by indytim on 2007-11-03
One of many backup options (assuming you have the storage space available) is to use Partimage to do a partition backup.  It's in the repositories and invoked from the command line ( $sudo Partimage ).  Just remember that you can't backup your mounted "/" partition.

IndyTim

---

