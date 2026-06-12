---
title: "swap partition"
date: 2006-07-04
forum: General Help
---

### Post by moore.bryan on 2006-07-04
i have an old 3GB hd installed in my dell i want to use as the swap partition.  how would i set that up?

---

### Post by taurus on 2006-07-04
Assuming it's /dev/hdb1, open a terminal and format it first as
```

mkswap /dev/hdb1 <-- to format it
swapon /dev/hdb1 <-- to mount it
free <-- to make sure it is mounted

```
Then, you need to add the new swap partition to your /etc/fstab so that it will be mounted automatically upon boot.
```

sudo gedit /etc/fstab

```
Now, add this line to the bottom of it...
```

/dev/hdb1       none            swap    sw              0       0

```

---

### Post by kb2wdi on 2006-07-04
One additional note to above;

First, execute "sudo fdisk /dev/hdb", delete old partition(s), and create partition #1 (/dev/hdb1) and set it to type "82  Linux swap"

---

### Post by DoctorMO on 2006-07-04
I wouldn't use a 3GB hard drive for a swap disk, it does have the advantage that it would be on a different ide but it's going to be a much slower speed posibly running at 66Mhz unlike the newer disks which run at 133Mhz (SATA being faster still).

I'd use the 3Gb disk for my home directories, link back a directory to the main disk for media such a music wich I genraly share between users anyway.

---

### Post by moore.bryan on 2006-07-07
thanks for all the tips... i had already configured the other drive as swap and just needed to edit the fstab file a bit.  everything's good now... thanks, again, for all the tips.

---

