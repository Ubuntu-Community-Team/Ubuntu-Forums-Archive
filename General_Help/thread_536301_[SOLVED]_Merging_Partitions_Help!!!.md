---
title: "[SOLVED] Merging Partitions Help!!!"
date: 2007-08-27
forum: General Help
---

### Post by xavier_r on 2007-08-27
This is my computer configuration...

[** /dev/hda1 FAT32 9.77 GB **][ **/dev/hda2 ext3 26.24GB ]**[** 1.26GB swap **]

Now I previously had window on FAT32 /dev/hda1
But since I removed it, I no longer required that partition

UBUNTU is installed on /dev/hda2
So i thought of merging /dev/hda1 and /dev/hda2 and making it just one big partition

I thought it would be simple...

I booted from LiveCD and started GNOME Partition Editor
I deleted /dev/hda1
Then I wanted to resize /dev/hda2 to fill up the blank space
But I couldnt resize it
Neither could I move it

I am stuck...
Can anyone please help?!?

---

### Post by davidjmayo on 2007-08-27
Try it using the GParted Live CD it's more recent and better
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

---

### Post by xavier_r on 2007-08-27
> **davidjmayo said:**
> Try it using the GParted Live CD it's more recent and better
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

Isnt GParted LiveCD the same as GParted on UBUNTU LiveCD ?
EDIT: GParted LiveCD is the same as GParted on UBUNTU LiveCD

---

### Post by davidjmayo on 2007-08-27
> **xavier_r said:**
> Isnt GParted LiveCD the same as GParted on UBUNTU LiveCD ?
EDIT: GParted LiveCD is the same as GParted on UBUNTU LiveCD

No GParted on the LiveCD is an older frozen version and  nowhere near as sophisticated
(this info comes from a thread I can't find but thanks to bodhi.zazen)

---

### Post by xavier_r on 2007-08-28
GParted LiveCD sure did the trick...
It worked perfectly... My problem is solved...
Thanks :)

---

