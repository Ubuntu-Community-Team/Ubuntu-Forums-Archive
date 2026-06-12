---
title: "Post-installation... adding swap"
date: 2005-10-20
forum: General Help
---

### Post by eraos on 2005-10-20
How can I mount(?) a swap partition after I've installed and set up Ubuntu?

---

### Post by KnottyMan on 2005-10-20
swapon /dev/swap_partition

It might already be there.  You don't really need to 'mount' swap.  Run top and see if it lists how much swap memory you have.

---

### Post by matthew on 2005-10-20
If the swap partition was created, but not formatted you may need to do this:
```
sudo mkswap /dev/swap_partition
```
then
```
sudo swapon /dev/swap_partition
```

where "swap_partition" is the location of the swap partition on your machine, i.e. /dev/hda5 or wherever.

---

### Post by rmjokers on 2005-10-20
Dont forget to add an entry to /etc/fstab so that it is used each time you reboot.  Might look something like this:

/dev/sda2       none            swap    sw              0       0

---

### Post by eraos on 2005-10-20
alright, cool, that worked.

thanks, all

---

