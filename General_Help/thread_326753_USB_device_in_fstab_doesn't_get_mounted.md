---
title: "USB device in fstab doesn't get mounted"
date: 2006-12-28
forum: General Help
---

### Post by Zaggy on 2006-12-28
I put my usb hdd drive in /etc/fstab to be mounted at boot like this:

#case
/dev/sdb1	/media/case ntfs umask=0222 0 0

But it isn't mounted after I login.
If I do a 'sudo mount -a' it does get mounted, what gives?

---

### Post by jc750kwak on 2006-12-28
Before umask put "auto" to get it automatically mounted at bootup

---

### Post by Zaggy on 2006-12-28
thanks!

---

