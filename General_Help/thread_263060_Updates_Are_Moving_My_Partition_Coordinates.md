---
title: "Updates Are Moving My Partition Coordinates"
date: 2006-09-22
forum: General Help
---

### Post by fatsheep on 2006-09-22
When I first installed Ubuntu Dapper 64-bit, it was located at **/dev/hdc2**.  However, to resize it, I had to move the partition to **/dev/hdc4**.  Do to this GRUB could not find the partition until I corrected the coordinates in **/boot/grub/menu.lst** to reflect the new position of my partition.  After I made the changes, Ubuntu starts up fine.  I have no problems until the next update which reverts my partition's coordinates back, causing the same GRUB error.  This has happened twice so far and it's looking that everytime Ubuntu updates I am going to have to boot up on a LiveCD, mount my partition, and make the necessary editing to /boot/grub/menu.lst.  This is pain in the neck to be honest so any help at all would be very much appreciated.

---

### Post by fatsheep on 2006-09-22
I've updated the first post to make it easier to understand and more to the point.  I'm figuring that's why no one has responded so far...

---

### Post by lha on 2006-09-24
Find lines that look something like 
```
# kopt=root=/dev/hdc2 ro
```
and
```
# groot=(hd0,3)
```
Those values will be used to create new menu entries when you upgrade kernels. Adjust them to suit your situation, i.e.
```
# kopt=root=/dev/hdc4 ro
```
and
```
# groot=(hd0,5)
```
and try if menu.lst looks good after you execute
```
sudo update-grub
```

---

