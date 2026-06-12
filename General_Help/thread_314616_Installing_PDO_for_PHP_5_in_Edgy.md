---
title: "Installing PDO for PHP 5 in Edgy"
date: 2006-12-07
forum: General Help
---

### Post by NunoCorreia on 2006-12-07
Hi folks.

Has anyone succeeded in installing PDO for PHP 5 in Edgy, or the respective drivers for PostgreSQL access? Doing "pecl install pdo" or "pecl install pdo_pgsql" ends up with
```

Fatal error: Allowed memory size of 8388608 bytes exhausted (tried to allocate 117 bytes) in /usr/share/php/PEAR/Registry.php on line 1012

Fatal error: Allowed memory size of 8388608 bytes exhausted (tried to allocate 32 bytes) in /usr/share/php/PEAR.php on line 766

```
even though I've set the memory limit for scripts to 64 megabytes in both /etc/php5/cli/php.ini and /etc/php5/apache2/php.ini (just to be sure)...

Any idea? Thanks.

---

