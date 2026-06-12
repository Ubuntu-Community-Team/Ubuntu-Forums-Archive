---
title: "folder turned into a character device, and cannot be deleted"
date: 2008-07-10
forum: General Help
---

### Post by riverfr0zen on 2008-07-10
After performing an rsync on my laptop, I found that one of my folders has somehow been turned into a character device:

c--xrw--wx 30575 1685195018 544435308 121, 109 2021-10-12 07:07 docroot

This used to be a normal directory - not sure exactly what has happened. In any case, I can replace it easily with a backup, but the problem is that I cannot seem to delete the file above at all, even as root.

How do I get rid of it? Thanks for any help.

Edit: I ran fsck from maint. mode, but it didn't find any problems w/ the filesystem.

---

### Post by jimv on 2008-07-10
Maybe try from the Live CD?

---

### Post by riverfr0zen on 2008-07-10
Don't have one around at the moment, but will try it later.

But why would that be any different - the Live CD would simply mount the filesystem the same way the drive install does, wouldn't it?

---

### Post by jimv on 2008-07-10
Yeah, but maybe the file is in use or something when Ubuntu is booted normally, and it won't be when you boot from the disk.

Just an idea.

---

