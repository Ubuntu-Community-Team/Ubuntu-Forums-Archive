---
title: "[SOLVED] Grub Problems"
date: 2008-03-29
forum: General Help
---

### Post by ptrv2.0 on 2008-03-29
_Background_: I had to reinstall Windows, but HP's install completely wipes the hard drive. So I cloned my Ubuntu partition before the Windows reinstall. Afterwards I reinstalled Windows, and copied the Ubuntu clone back onto the hard drive. Before I left I fixed Grub:

```

sudo grub
grub> find /boot/grub/stage1
grub> root (hd0,2)
grub> setup (hd0)
grub> quit

```

_Problem_: After Grub loads, and I boot into Ubuntu, it goes into the load screen, but never loads. * I hear the hard drive spinning, but I have no clue whats going on.*

How can I view the load in terminal mode, so I can figure out what might be the problem, or better yet, can anyone figure out what the problem might be from this small bit of info?

.....I was so close to repairing my laptop, and am stuck on the home stretch, help.

---

### Post by dcstar on 2008-03-29
> **ptrv2.0 said:**
> _Background_: I had to reinstall Windows, but HP's install completely wipes the hard drive. So I cloned my Ubuntu partition before the Windows reinstall. Afterwards I reinstalled Windows, and copied the Ubuntu clone back onto the hard drive. Before I left I fixed Grub:

```

sudo grub
grub> find /boot/grub/stage1
grub> root (hd0,2)
grub> setup (hd0)
grub> quit

```

_Problem_: After Grub loads, and I boot into Ubuntu, it goes into the load screen, but never loads. * I hear the hard drive spinning, but I have no clue whats going on.*

How can I view the load in terminal mode, so I can figure out what might be the problem, or better yet, can anyone figure out what the problem might be from this small bit of info?

.....I was so close to repairing my laptop, and am stuck on the home stretch, help.

New partitions will have different UUIDs, your original Ubuntu will still have the old ones in it's /etc/fstab file.

You should boot off the Ubuntu Live CD, mount the Ubuntu partition and manually edit the fstab file to use either the new UUIDs or the basic /dev designations.

A search should provide detailed instructions if you need them.

---

### Post by ptrv2.0 on 2008-03-29
Wow dcstar, you just hurled a bunch of acronyms and terminology that flew over my head. What do you mean UUID, and what exactly would I be doing in /etc/fstab? And what command displays terminal mode instead of the load bar during boot *for future reference*?

:confused::?::confused::?:

---

### Post by ptrv2.0 on 2008-03-30
Ok, did some research.

Changed the Ubuntu UUID /etc/fstab and  /boot/grub/menu.lst. I used this to get the UUID:

```

 sudo vol_id -u <partition>

```

After changing the UUID's everything worked. Thank you for pointing me in the right direction.

---

