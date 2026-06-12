---
title: "File server and problems with cron"
date: 2008-04-08
forum: General Help
---

### Post by mufloni on 2008-04-08
Im trying to get a file server online but i have encountered some problems. Main problem is that im trying to get cron to move uploaded files under specified dates tree. So that if I today put some files into /share/Upload folder, cron will move them at midnight to /share/4.8.08. But for some reason, it doesnt move files, only make the folder. Heres my .cron file

#!/bin/bash

DIRECTORY=/user/samba/`date +%d.%m.%y_%T`/

mkdir -p $DIRECTORY

mv -r /user/samba/upit/* $DIRECTORY

Weird is that some time ago (like 6 months) i remember that this worked just fine. Then i had to reinstall my linux system but..
So could someone help me with this?

---

### Post by asbjorne08 on 2008-04-08
try running the script manually from a terminal  to see if it gives some error message

A wild guess would be some kind of permission problem, or a typo somewhere.

Hope it helps
-- 
a

---

