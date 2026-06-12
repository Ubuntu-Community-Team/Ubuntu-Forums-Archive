---
title: "how to force rm comand?"
date: 2006-09-23
forum: General Help
---

### Post by lex1 on 2006-09-23
Trying to delete /mnt/share?

 rm -rf /mnt/share
rm: cannot lstat `/mnt/share': Input/output error

lex1

---

### Post by kerry_s on 2006-09-23
Did you try sudo? that is on the root side. you can go in nautilus as root(sudo nautilus /mnt) make sure it's unmounted first then delete it.

---

### Post by lex1 on 2006-09-23
i was in root when I inviked the commad 
umount gives same error message

---

### Post by henriquemaia on 2006-09-23
When all else fails, reboot.

---

### Post by ayoli on 2006-09-23
> **lex1 said:**
> Trying to delete /mnt/share?

 rm -rf /mnt/share
rm: cannot lstat `/mnt/share': Input/output error

lex1

sounds like a "ghost mount" (i mean like you have a samba share mounted on this path but remote host has disconnected) or a corrupted inode, then you may check your fs.

---

### Post by lex1 on 2006-09-23
how to check please?

lex

---

### Post by Pinkydead on 2007-08-17
(I know this is old but...)

I had a mount point and when you do 'ls -l' you end up with:

?--------- ? ? ? share

Any attempts at rm -fr fail with cannot lstat.

Bits and pieces from around the place suggested a solution:

```
sudo smbumount share

```

Released the connection (obviously I'm assuming that you are using samba) and allows 'rm -fr'

Then from there on in use cifs instead of smbfs (see man mount.cifs).  Change fstab to use cifs instead of smbfs, and see the man page for how the options differ.

---

