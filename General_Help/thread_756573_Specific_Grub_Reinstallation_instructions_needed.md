---
title: "Specific Grub Reinstallation instructions needed"
date: 2008-04-16
forum: General Help
---

### Post by thepocketdrummer on 2008-04-16
Ok, I have looked at a few threads, but it seems that there is no definite way to do this without worries.

I have a windows partition with recordings that I CANNOT LOSE. I don't really have a way to back all this information up, nor do I have the money to obtain equipment that is capable of doing so. If all else fails, I either won't try to fix grub, or I'll just wipe it and start (the linux partition) over with Ubuntu 8.04.


Anyway, what happened is simple. I had windows XP and Ubuntu 7.10 dual booted. Then I had to reformat windows XP. In doing so, I lost the Grub, so I can't get to my linux partition.

I need VERY specific, "for Dummies" level instructions on how to reinstall Grub without destroying my windows XP partition. I'd also like instructions on how to save Windows XP at all costs if something does go wrong.

Please help. :confused:

---

### Post by sekinto on 2008-04-16
Boot up from your live CD and open up a terminal:

```
sudo grub
root (hdX,Y)
setup (hdX)
exit
```

X = # assigned to hard drive that Ubuntu is on. -1.
Y = # assigned to partition that Ubuntu is on. -1.

Say Ubuntu is on the third partition of your first hard drive:
X = 1 - 1 =  0
Y = 3 - 1 = 2

So you would do this:


```
sudo grub
root (hd0,2)
setup (hd0)
exit
```

---

### Post by thepocketdrummer on 2008-04-16
> **sekinto said:**
> Boot up from your live CD and open up a terminal:

```
sudo grub
root (hdX,Y)
setup (hdX)
exit
```

X = # assigned to hard drive that Ubuntu is on. -1.
Y = # assigned to partition that Ubuntu is on. -1.

Say Ubuntu is on the third partition of your first hard drive:
X = 1 - 1 =  0
Y = 3 - 1 = 2

So you would do this:


```
sudo grub
root (hd0,2)
setup (hd0)
exit
```

I only have 1 hard drive, but technically 3 partitions. The first (in the menu when I made the partitions) is Windows XP, the next is Ubuntu, the next is the swap partition.

Is there a way to find out for sure what I should type? Also, when I reboot, will windows boot properly when selected?

---

### Post by Tigairius on 2008-04-16
Use a ubuntu live CD.
Do 'sudo grub' and then 'find /boot/grub/stage1'
The find command should return a hdX,Y
After that do:
root (hdX,Y)  <- From above
setup (hd0)
exit

If for some reason that doesn't work then you should still have a working GRUB you can just edit the path to the partition.

---

