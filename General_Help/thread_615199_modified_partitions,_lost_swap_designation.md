---
title: "modified partitions, lost swap designation"
date: 2007-11-16
forum: General Help
---

### Post by kefurd06 on 2007-11-16
k, so i used gparted to shrink my windows partition and expand my linux partition. i also double my linux-swap to 4 gigs. because of the stupid way i laid the partitions out in the firstp lace, i had to delete and remake the linux swap. now i have zero bytes of swap space. i'm still pretty new to linux. how do i tell my system that i want to use the 4 gig linux-swap partition for swap? thanks.

---

### Post by taurus on 2007-11-16
Maybe you need to replace the UUID in /etc/fstab for swap back to /dev/sda3 or whatever the new partition for swap is.  If not sure how to do it, post the outputs of these commands from a terminal.

```
sudo fdisk -l
cat /etc/fstab
free
```

---

### Post by skymera on 2007-11-16
i dont ave any swap.

it never uses it,
if you have 1GB or more of RAM you should be safe.

but to turn swap on

sudo swapon /dev/device name
sudo gedit /etc/sysctl.conf

in that file (should have lots of stuff) add:

vm.swappiness=0

that will make sure it uses RAM before swap
60 is default
100 will use swap more than ram.

---

### Post by kefurd06 on 2007-11-16
i got it! i used vol_id to get the uuid, then put that in fstab file in place of the old one designated as swap. thanks for the help guys. ya, i've got 2 gigs of ram on this computer, so i really didn't even need to resize the 2 gig swap to 4. oh well.

---

