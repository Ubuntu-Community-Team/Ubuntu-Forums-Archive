---
title: "Can't get write access to my external hard drive."
date: 2007-06-26
forum: General Help
---

### Post by Damo1976 on 2007-06-26
Hi,

Hopefully this is an easy one to fix...
I just can't get full access to my external hard drive, and I want to do a backup.
It says the owner is root, but I don't see why that's not me!

Please help.

D

---

### Post by merlinus on 2007-06-26
Is it formatted as ntfs?  If so, you will need to install ntfs-3g.

How is it listed in /etc/fstab?

With it plugged in, what are the results of:

```

sudo fdisk -l

```

l is a lowercase L.

-merlin

---

