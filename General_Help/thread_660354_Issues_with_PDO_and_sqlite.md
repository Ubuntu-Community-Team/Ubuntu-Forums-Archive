---
title: "Issues with PDO and sqlite"
date: 2008-01-06
forum: General Help
---

### Post by dazealex on 2008-01-06
Hi everyone,

I am using Ubuntu Gutsy, and have been at it trying to get the appropriate modules working for working on PHP with sqlite. But I get the following errors:

```
/var/log/apache2/error.log
PHP Fatal error:  Unable to start pdo_sqlite module in Unknown on line 0
PHP Warning:  Module 'PDO' already loaded in Unknown on line 0
PHP Warning:  Module 'pdo_mysql' already loaded in Unknown on line 0
PHP Warning:  Module 'pdo_sqlite' already loaded in Unknown on line 0
PHP Fatal error:  PDO: driver sqlite requires PDO API version 20060511; this is PDO version 20060409 in Unknown on line 0

```

Infact, now apache2 doesn't even run anymore due to those error messages.

Please help!!!

Daze

---

### Post by dazealex on 2008-01-06
I was able to get Apache2 to run again by removing the PDO_*s by:

```
  542  sudo pecl uninstall  PDO_MYSQL
  543  sudo pecl uninstall  PDO_PGSQL
  555  sudo pecl uninstall  PDO_sqlite
  545  sudo pecl uninstall  PDO

```
Any ideas how I can get SQLITE3 to work with PHP? There is an Open Source project that'd like to start on with this setup. :)

Thanks.

Daze

---

