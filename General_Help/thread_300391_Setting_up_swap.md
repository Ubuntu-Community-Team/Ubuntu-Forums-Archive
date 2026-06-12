---
title: "Setting up swap"
date: 2006-11-15
forum: General Help
---

### Post by Mazin on 2006-11-15
How do I set up swap space on Edgy?  I have a 512 mb swap partition, and another 6gb swap partition.  How do I get Ubuntu to use them?

---

### Post by taurus on 2006-11-15
That's going to be a lot of swap space...  Just add them to your /etc/fstab.

```
sudo cp /etc/fstab  /etc/fstab.bak
gksudo gedit /etc/fstab
```
Add these two lines to the end of it and assuming those two partitions are /dev/hda1 & /dev/hda2!!!

```

/dev/hda1   none   swap   sw   0   0
/dev/hda2   none   swap   sw   0   0

```
Either reboot or "sudo mount -a" to mount them...

---

### Post by Mazin on 2006-11-15
Well, the 6 gb was from a failed experiment.
I found out that I could use GParted by right-clicking the swap partition and choosing swapon if I wanted to activate it w/o rebooting.  sudo mount -a didn't seem to work for some reason.

---

### Post by taurus on 2006-11-15
What happens if you reboot?

```
free
```

---

