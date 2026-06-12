---
title: "Ubuntu 21.04. How do I check an rsync backup set?"
date: 2021-11-25
forum: General Help
---

### Post by Advait on 2021-11-25
I’ve been using Timeshift and have about 200+ snapshots (190GB) in my Timeshift backup set. What are the commands to check this backup set? I want to make sure the backup set is not corrupted.

Restic has the commands ‘check’, ‘prune’ and  ‘cleanup’. What are the similar commands for rsync? I checked an rsync command list page and didn’t find anything relevant.

---

### Post by HermanAB on 2021-11-25
Rsync copies files.  It ensures that a file was copied correctly using a CRC.  That is all it does.

If you want to check a file, go there with a file browser and open it.

---

### Post by Advait on 2021-11-26
> **HermanAB said:**
> Rsync copies files.  It ensures that a file was copied correctly using a CRC.  That is all it does.

If you want to check a file, go there with a file browser and open it.

So the rsync backup set requires no "mainetence" like restic does. Nice. Thanks. Issue resolved.

---

