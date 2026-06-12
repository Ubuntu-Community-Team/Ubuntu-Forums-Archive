---
title: "Feisty: Repartitioned. Now fsck fails on startup."
date: 2007-10-30
forum: General Help
---

### Post by impalerau on 2007-10-30
I originally installed ubuntu with 3 partitions (plus swap); a boot partition, one for public data, and another for image backups.

The other night I decided to remove the 3rd partition and extend the 2nd one.  I did this with gparted running off a SystemRescueCD.  Now when I reboot I gat a fsck failure (see attached screen image).  Apart from that everything seems to be fine.  System starts, data is accessible etc.  I've tried recreating the 3rd partition again but that didn't help.

What do I need to do to correct this?

I also notie that after the failure the system attempts to start a shell but isn't able to.  Is that a symptom of another problem that I should address?

Thanks in advance,
Vlad.

---

### Post by dcstar on 2007-10-31
> **impalerau said:**
> I originally installed ubuntu with 3 partitions (plus swap); a boot partition, one for public data, and another for image backups.

The other night I decided to remove the 3rd partition and extend the 2nd one.  I did this with gparted running off a SystemRescueCD.  Now when I reboot I gat a fsck failure (see attached screen image).  Apart from that everything seems to be fine.  System starts, data is accessible etc.  I've tried recreating the 3rd partition again but that didn't help.

What do I need to do to correct this?

I also notie that after the failure the system attempts to start a shell but isn't able to.  Is that a symptom of another problem that I should address?

Thanks in advance,
Vlad.

Ok, when you modify partitions you generate a new UUID for that partition, and your /etc/fstab file is set to use the old UUID (which no longer exists.......)

Edit your /etc/fstab file and change the entry with the bad UUID to use the old "/dev/hd...." designation associated with that partition (if it is the partition you deleted - then comment that entry out!) - then things should work fine again after the reboot:
```

sudo nano /etc/fstab
sudo init 6
```

---

### Post by impalerau on 2007-10-31
Thanks David.  That worked a treat.

Anyone have an idea about the shell failure?

Regtards,
Vlad.

---

