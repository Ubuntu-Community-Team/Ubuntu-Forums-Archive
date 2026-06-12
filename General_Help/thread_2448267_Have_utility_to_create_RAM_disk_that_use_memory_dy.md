---
title: "Have utility to create RAM disk that use memory dynamically ?"
date: 2020-08-05
forum: General Help
---

### Post by aug7744 on 2020-08-05
I wait create an ramdisk in Lubuntu 20.04 being that only allocate memory if is using to use how being an temp folder.
Create an ramdisk 1 GB size that only will use 1GB when was writed 1GB data and when files are deleted free the ram space used.
Any tool to create it ?
Thanks for reply.

---

### Post by HermanAB on 2020-08-05
You should be able to cobble something together using *tmpfs* for the RAM disk and *logrotate* to manage the contents.

---

### Post by aug7744 on 2020-08-13
Thanks.

---

