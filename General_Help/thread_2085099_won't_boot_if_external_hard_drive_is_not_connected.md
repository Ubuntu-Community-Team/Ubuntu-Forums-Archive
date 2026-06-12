---
title: "won't boot if external hard drive is not connected"
date: 2012-11-17
forum: General Help
---

### Post by ieee488 on 2012-11-17
I have some data files on an external hard drive.

I just did a clean install of 12.04.

I noticed this morning that if I don't have the external hard drive connected, Ubuntu won't boot.

Why?

---

### Post by ieee488 on 2012-11-17
I deleted the external hard drive's entry from /etc/fstab file.
Ubuntu was wanting to automount it at boot.

---

### Post by rnerwein on 2012-11-17
> **ieee488 said:**
> I have some data files on an external hard drive.

I just did a clean install of 12.04.

I noticed this morning that if I don't have the external hard drive connected, Ubuntu won't boot.

Why?
hello
another way is - edit your fstab and insert "noauto" in the line with your external drive:

e.g.: /dev/sxx UUID=blablabla  ext3 defaults,suid,[COLOR=Blue]noauto[/COLOR]   0   0

---

