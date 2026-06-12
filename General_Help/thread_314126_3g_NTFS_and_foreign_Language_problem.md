---
title: "3g NTFS and foreign Language problem"
date: 2006-12-07
forum: General Help
---

### Post by hadiriazi on 2006-12-07
Hi all;

After installing the 3g NTFS for my NTFS drives to have read/write access a new problem occurred. Can't see my folders, the ones with  some foreign language text (Farsi).

I have checked the fstab file and for nls I have nls=UTF8

Plz help me on this

---

### Post by hadiriazi on 2006-12-07
bump1

---

### Post by hadiriazi on 2006-12-08
bump, any solutions?

---

### Post by szaka on 2006-12-08
Use the 'locale' mount option with the right (Farsi) value. See here more: [http://forum.ntfs-3g.org/viewtopic.php?p=134#134](http://forum.ntfs-3g.org/viewtopic.php?p=134#134)

---

### Post by hadiriazi on 2006-12-09
Thanks, I will try it and post the results

---

### Post by hadiriazi on 2006-12-09
> **szaka said:**
> Use the 'locale' mount option with the right (Farsi) value. See here more: [http://forum.ntfs-3g.org/viewtopic.php?p=134#134](http://forum.ntfs-3g.org/viewtopic.php?p=134#134)

Hi;

Where could I find the file "glibc-i18ndata"?
I'm using Ubuntu 6.10 Edgy

---

### Post by szaka on 2006-12-09
The package is called 'locales' on Ubuntu, probably. If you don't have it then intall it.

---

