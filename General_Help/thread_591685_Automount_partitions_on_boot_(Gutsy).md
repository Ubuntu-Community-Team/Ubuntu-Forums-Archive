---
title: "Automount partitions on boot (Gutsy)"
date: 2007-10-25
forum: General Help
---

### Post by kub-fu on 2007-10-25
Hi,

I just installed Gutsy from scratch (had Feisty before), and I cannot seem to be able to mount some partitions on boot.

This is my fstab file:

proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=51f9e9ba-388c-4b0a-b5ac-f8f681271c9d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=3c105ea1-5f0b-4c7d-9ea8-fc7b2ed8e2af none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

# here's the problem
UUID=... /home/kubfu/local ext3 defaults 0 1
UUID=... /home/kubfu/working ext3 defaults 0 1
UUID=... /home/kubfu/portable ext3 defaults 0 1

Weird thing is, the first two partitions are on internal disks, and the third one is an external drive, which does get mounted on boot when it's attached.

The other two, I have to sudo mount -a to get them mounted...

Anyone knows why this behavior? It worked fine on Feisty.

Thanks!

---

### Post by drs305 on 2007-10-25
Edited after response #3: Okay, now I see what you're saying. You aren't individually mounting them to get them to work. You're right, it's not UUIDs if sudo mount -a works.

Original:

About eight months ago when I upgraded a kernel the UUIDs changed - nobody knew why. Or perhaps a complete reformatting did it. Anyway, if I was in your position, if I manually mounted them I'd not bother with UUIDs and they would probably work. Are you sure the UUIDs are still the same?

```
blkid
```

Just a thought...

---

### Post by kub-fu on 2007-10-25
If the UUIDs changed, sudo mount -a wouldn't mount anything, but thanks for the thought.

---

