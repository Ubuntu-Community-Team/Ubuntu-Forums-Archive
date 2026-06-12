---
title: "UUID's? How do I find them?"
date: 2007-05-09
forum: General Help
---

### Post by Vinze on 2007-05-09
Hey, I've been messing around with my partitions, which comes down to me having new partitions containing the same files as the previous ones, but these partitions are of different sizes. However, / and /home are no longer mounted automatically which can be very annoying. I now see in /etc/fstab that I need UUID's for that, but I don't know what the UUID's are. My hard disks are:

/dev/hdb1 for /
/dev/hdb3 for /home
/dev/hdb4 for swap

And does anyone know what's up with this 134 instead of 123?

Thanks in advance.

---

### Post by Lord Illidan on 2007-05-09
You can still use /dev/hdb in your fstab.

In any case, to find UUID, use this : 

```
ls /dev/disk/by-uuid/ -alh
```

---

### Post by Vinze on 2007-05-09
> **Lord Illidan said:**
> You can still use /dev/hdb in your fstab.

In any case, to find UUID, use this : 

```
ls /dev/disk/by-uuid/ -alh
```

Thanks a lot! I'm going to reboot now and if it works, I'll edit this post.

**Edit:** You're really awesome, it worked!

---

### Post by ikonia on 2007-05-09
also try "blkid"

---

### Post by Vinze on 2007-05-09
> **ikonia said:**
> also try "blkid"

That would've worked well too, thanks.

---

