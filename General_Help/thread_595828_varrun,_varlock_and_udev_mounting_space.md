---
title: "varrun, varlock and udev mounting space"
date: 2007-10-29
forum: General Help
---

### Post by mauro_ita on 2007-10-29
Hello world,

checking my HD space utilization I've seen that there are 3 directories mounted with a fix space usage that is huge accordingly to my personal use.

Here the df result:
varrun                  517888       224    517664   1% /var/run
varlock                 517888         0    517888   0% /var/lock
udev                    517888       152    517736   1% /dev
devshm                  517888         0    517888   0% /dev/shm
lrm                     517888     33788    484100   7% /lib/modules/2.6.20-16-generic/volatile


how can I reduce the space amount?
Which kind of problem I could have if I'll reduce them?
Which configuration file I have to look to and how to change it if I need a special command format?!

Thanks a lot

mauro

---

