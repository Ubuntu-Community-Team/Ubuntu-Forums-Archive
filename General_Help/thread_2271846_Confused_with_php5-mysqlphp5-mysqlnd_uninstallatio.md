---
title: "Confused with php5-mysql/php5-mysqlnd uninstallation"
date: 2015-04-02
forum: General Help
---

### Post by mock2u on 2015-04-02
Hi,

Ubuntu 14.04 LTS.

Replace php5-mysql with php5-mysqlnd, then `apt-get remove --purge php5-mysql` will delete /etc/php5/fpm/conf.d/20-mysql.ini and /etc/php5/fpm/conf.d/20-mysqlnd.ini.
But those two configurations now belongs to php5-mysqlnd which I still need.
This behavior will lead to php child process crash in some certain cases.

I'm not sure if it is the intended behavior.

Maybe rename those two ini files will solve the problem.
Or the user need to `apt-get remove --purge php5-mysql` first, then `apt-get install php5-mysqlnd`.

Also this affects those packages which conflict but use the same configurations.

---

