---
title: "MySQL Issue"
date: 2008-04-19
forum: General Help
---

### Post by nami on 2008-04-19
Hi

I have made a few tables in my MySQL database which ended up giving me a warning that my hdd space is low.  Each table was about 500Mb.  So I dropped the tables expecting to free about 5Gb, but absolutely no hdd space was freed.  I even rebooted, but still no freed hdd space.

What is going on?

---

### Post by ibutho on 2008-04-19
Whats the output of running "df -h"?

---

### Post by nami on 2008-04-19
nami@nami-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G   15G  1.9G  89% /
varrun                379M  100K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
udev                  379M   52K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   34M  345M   9% /lib/modules/2.6.22-14-generic/volatile
/dev/scd0             3.2G  3.2G     0 100% /media/cdrom0
nami@nami-laptop:~$

---

### Post by ibutho on 2008-04-19
According to the output above, you have 1.9GB free on /dev/sda1 which is your / (root) partition. If you are positive that the tables were dropped then something else is using up that disk space.

---

### Post by nami on 2008-04-19
But that is the problem, before I deleted the 5Gb worth of tables, I checked the hdd status and it said 89%.  Now after deleting the tables, it still says 89%...

---

### Post by ibutho on 2008-04-19
Thats a strange one. The only thing I can think of, is that you double check whether the tables were actually deleted.

---

### Post by nami on 2008-04-21
It seems the tables are not deleted because the HDD space has not been freed, however, the webpages which accessed those tables no longer work and complain about the table not existing...

---

