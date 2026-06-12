---
title: "www-data irresponsible owner ?"
date: 2008-07-09
forum: General Help
---

### Post by superheavy on 2008-07-09
I have a php file which is used to upload files.  These files are then to be processed by a servlet.  However, the uploaded files are owned by "www-data" and the servlet can't touch them.  Is there anyway I can make it so that any uploaded file is owned by anyone other than "www-data".

SuperHeavy

---

### Post by jazzgossen on 2008-07-10
You would have to run Apache as another user than the default www-data. Or, possibly, have a cron script or something similar that changes ownership and permissions on all needed files regularly.

---

### Post by superheavy on 2008-07-10
Thank you very much for your response.

---

