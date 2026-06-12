---
title: "Space freeing"
date: 2006-11-19
forum: General Help
---

### Post by rsavu on 2006-11-19
Hello. I have kubuntu 6.10. I unfortunately allocated only 10GB for kubuntu and partition is now swamped. How can i mount another partition for other applications? I usually get packages with apt-get and install them with dpkg. Can i copy all /usr/ to another bigger partition and then add that partition to fstab (to free space from /).

Thank you in advance.

---

### Post by az on 2006-11-19
> **rsavu said:**
> Hello. I have kubuntu 6.10. I unfortunately allocated only 10GB for kubuntu and partition is now swamped. How can i mount another partition for other applications? I usually get packages with apt-get and install them with dpkg. Can i copy all /usr/ to another bigger partition and then add that partition to fstab (to free space from /).

Thank you in advance.

You would be better to mount your home drive to another partition - that is more organized approach.

Anyway, your /usr /bin and /sbin directories probably take up less than two gigs or so altogether....

---

### Post by rsavu on 2006-11-19
Actually, my /usr is above 5GB. I have 2 fresh made logical partition of 5GB each. Any tutorials on mounting them as /usr and /home without loosing anything? Do i copy all contents to those partitions, delete content from / and remount them as /home and /usr?

---

### Post by Rui Pais on 2006-11-19
Another thing that i use to do is make a partition (i choose to format it with XFS, that deals nice with big files) and move everything on /var/cache/apt/archives to there, replacing that folder with a link to the mounted partition.
That way i have an easier control of deb packages, either manually download as automatically get it from updates, and avoid mixing with system files (better to avoid fragmentation too)...

Edit: to copy your /usr, you can copy all the contents with cp **-a** and then add the needed line to your fstab and then do a mount -a or reboot.

---

### Post by rsavu on 2006-11-19
With what param do i mount my /home and /usr? defaults 1 2 is ok? I don't think so. I want to be able to ./configure and run things from my /home directory. Thanks.

---

### Post by Rui Pais on 2006-11-19
My /home is set to 0 1 and the one with damped debs and other download software as 0 0.

---

