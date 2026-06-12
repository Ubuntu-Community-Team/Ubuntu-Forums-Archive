---
title: "[SOLVED] Consistently Mount an External Drive at the Same Location?"
date: 2008-05-28
forum: General Help
---

### Post by talkingwires on 2008-05-28
I have simple question that has probably been answered before, but I can't think of how to phrase it in Google search terms...

I'm running Ubuntu on a laptop with an external USB HDD attached. How can I use the UUID of a partition on the HDD to always mount it at the same location?

More specifically, I have an external drive attached through a USB connection with a 128Gb partition for my music collection, and I'd like it to always mount to the same location, regardless of USB thumbdrives, my iPod, or my PSP being connected. As it stands, I never know if the drive will be mounted as disk, disk&#8208;1, or disk&#8208;4815162342, and neither does Amarok.

---

### Post by Kinnza on 2008-05-28
im not really sure how to do that, but i found this when i was browsing earlier:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by talkingwires on 2008-05-29
There's good info in that thread, but nothing about consistently mounting a drive in the same location. But [this]("http://www-128.ibm.com/developerworks/forums/thread.jspa?messageID=13836521") combined with the info from the thread makes me think that labeling the partition will do the trick. I'll check it out...

---

### Post by eriqjaffe on 2008-05-29
> **talkingwires said:**
> How can I use the UUID of a partition on the HDD to always mount it at the same location?Create your mount points (in the following example, /media/old_e_drive), and then add the relevant entries to your /etc/fstab in the following manner:

```
/dev/disk/by-uuid/8A44ED2C44ED1C27 /media/old_e_drive ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

Your fstab may need be slightly different depending on the format of the external disk, etc., but that's the general idea.

At that point, "sudo mount -a" will attempt to mount everything in fstab.  If that works, then you're good, and the drives will auto-mount to the same place next time.

Also, you should back up your /etc/fstab file before editing it, and be sure to edit as root.

```
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
```

---

### Post by talkingwires on 2008-06-02
Thanks!

---

