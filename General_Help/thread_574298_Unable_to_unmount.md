---
title: "Unable to unmount"
date: 2007-10-12
forum: General Help
---

### Post by [Johnny] on 2007-10-12
Well i installed the read/write program for NTFS with automatix, thinking i could throw some files on my external.

It wouldnt let me copy anything there so i uninstalled it, but it left the drives on my desktop.... they have an unmount option but when i try this happens:

[IMG]http://i24.tinypic.com/2a7h8nq.png[/IMG]

how can i get rid of them?

---

### Post by Pumalite on 2007-10-12
Check on the left column in Places>Home. See if you can unmount them there.

---

### Post by [Johnny] on 2007-10-12
> **Pumalite said:**
> Check on the left column in Places>Home. See if you can unmount them there.

same error :(

---

### Post by thomasaaron on 2007-10-12
Did you try re-booting your computer?

If that doesn't work, post the output of:
cat /etc/fstab

---

### Post by &#61472;&#61472;&#61472; on 2007-10-12
reboot

---

### Post by Pumalite on 2007-10-12
Check if they are in /media and maybe you can unmount them from the terminal:
sudo umount /media/???

---

### Post by waawaawee on 2007-10-12
try that with -f option

umount -f /media

---

