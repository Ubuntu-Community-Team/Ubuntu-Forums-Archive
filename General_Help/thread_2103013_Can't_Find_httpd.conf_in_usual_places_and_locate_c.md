---
title: "Can't Find httpd.conf in usual places and locate command does not find it"
date: 2013-01-08
forum: General Help
---

### Post by hcamelion on 2013-01-08
Hi,

For some reason I don't have httpd.conf in /etc/apache2 on my Ubuntu 12.10 machine.  apache2.conf is there. locate httpd.conf is not finding it either.  I may try re-installing apache2 but now I am just curious whats going on?


According to this shouldn't it be in /etc/apache2:

```

/usr/sbin/apache2 -V
Server version: Apache/2.2.22 (Ubuntu)
Server built:   Nov  6 2012 20:27:19
Server's Module Magic Number: 20051115:30
Server loaded:  APR 1.4.6, APR-Util 1.4.1
Compiled using: APR 1.4.6, APR-Util 1.4.1
Architecture:   64-bit
Server MPM:     Prefork
  threaded:     no
    forked:     yes (variable process count)
Server compiled with....
 -D APACHE_MPM_DIR="server/mpm/prefork"
 -D APR_HAS_SENDFILE
 -D APR_HAS_MMAP
 -D APR_HAVE_IPV6 (IPv4-mapped addresses enabled)
 -D APR_USE_SYSVSEM_SERIALIZE
 -D APR_USE_PTHREAD_SERIALIZE
 -D APR_HAS_OTHER_CHILD
 -D AP_HAVE_RELIABLE_PIPED_LOGS
 -D DYNAMIC_MODULE_LIMIT=128
 -D HTTPD_ROOT="/etc/apache2"
 -D SUEXEC_BIN="/usr/lib/apache2/suexec"
 -D DEFAULT_PIDLOG="/var/run/apache2.pid"
 -D DEFAULT_SCOREBOARD="logs/apache_runtime_status"
 -D DEFAULT_LOCKFILE="/var/run/apache2/accept.lock"
 -D DEFAULT_ERRORLOG="logs/error_log"
 -D AP_TYPES_CONFIG_FILE="mime.types"
 -D SERVER_CONFIG_FILE="apache2.conf"

```

Is it possible that I don't have it?

Does anyone know the other usual locations for httpd.conf or a sure fire way to find it's location?

---

### Post by btindie on 2013-01-09
Under Ubuntu the Apache config file is called apache2.conf
>  -D SERVER_CONFIG_FILE="apache2.conf"
You may be confusing it with a RedHat/CentOS based system where it's called httpd/httpd.conf for the binary and config file.

---

### Post by oleink on 2013-01-09
> **hcamelion said:**
> Hi,

For some reason I don't have httpd.conf in /etc/apache2 on my Ubuntu 12.10 machine.  apache2.conf is there. locate httpd.conf is not finding it either.  I may try re-installing apache2 but now I am just curious whats going on?


According to this shouldn't it be in /etc/apache2:

```

/usr/sbin/apache2 -V
Server version: Apache/2.2.22 (Ubuntu)
Server built:   Nov  6 2012 20:27:19
Server's Module Magic Number: 20051115:30
Server loaded:  APR 1.4.6, APR-Util 1.4.1
Compiled using: APR 1.4.6, APR-Util 1.4.1
Architecture:   64-bit
Server MPM:     Prefork
  threaded:     no
    forked:     yes (variable process count)
Server compiled with....
 -D APACHE_MPM_DIR="server/mpm/prefork"
 -D APR_HAS_SENDFILE
 -D APR_HAS_MMAP
 -D APR_HAVE_IPV6 (IPv4-mapped addresses enabled)
 -D APR_USE_SYSVSEM_SERIALIZE
 -D APR_USE_PTHREAD_SERIALIZE
 -D APR_HAS_OTHER_CHILD
 -D AP_HAVE_RELIABLE_PIPED_LOGS
 -D DYNAMIC_MODULE_LIMIT=128
 -D HTTPD_ROOT="/etc/apache2"
 -D SUEXEC_BIN="/usr/lib/apache2/suexec"
 -D DEFAULT_PIDLOG="/var/run/apache2.pid"
 -D DEFAULT_SCOREBOARD="logs/apache_runtime_status"
 -D DEFAULT_LOCKFILE="/var/run/apache2/accept.lock"
 -D DEFAULT_ERRORLOG="logs/error_log"
 -D AP_TYPES_CONFIG_FILE="mime.types"
 -D SERVER_CONFIG_FILE="apache2.conf"

```

Is it possible that I don't have it?

Does anyone know the other usual locations for httpd.conf or a sure fire way to find it's location?

Try using "find" instead of locate.  Locate is setup to search in predefined $PATHs.  find will give you a better chance to locate the file.  Or use some variation of grep command as this seems to be a favorite

---

### Post by hcamelion on 2013-01-09
Yes I am used to centos web servers.  I think I had an httpd.conf in my prior Lucid setup.  I guess apache2.conf is it.

---

