---
title: "Stop automount  usb disk"
date: 2006-07-05
forum: General Help
---

### Post by playmobiel on 2006-07-05
Hi, 

I want to format my external usb hard drive, but i need to umount it with gparted te format it, this is no problem , but when the formatting starts, the disk gets mounted again and the formatting fails, does anybody know what to do? Thanks

---

### Post by cowley on 2006-07-05
can this not be done via system>preferences>removable media?  just turn off the mount when inserted or hotplugs

simon

---

### Post by playmobiel on 2006-07-05
[QUOTE=cowley]can this not be done via system>preferences>removable media?  just turn off the mount when inserted or hotplugs

simon[/QUOTE]
yes, that worked, thanks :)

---

### Post by cowley on 2006-07-05
no probs!

---

### Post by linuxa on 2006-07-23
Can someone tell me for curiosity's sake which file controls the automounts behaviour please?

Thanks in advance.

---

### Post by flickerfly on 2008-07-07
How is this accomplished on a server with no GUI?

---

### Post by eldragon on 2008-07-07
> **flickerfly said:**
> How is this accomplished on a server with no GUI?

what, partitioning ?

fdisk

---

### Post by flickerfly on 2008-07-07
> **eldragon said:**
> what, partitioning ?

fdisk

No, the original post is about stopping automount from taking control. I want automount to stop taking responsibility for my server's USB drive mounting. I'd rather handle it myself for various reasons.

How do I turn off automount from the command-line?

---

