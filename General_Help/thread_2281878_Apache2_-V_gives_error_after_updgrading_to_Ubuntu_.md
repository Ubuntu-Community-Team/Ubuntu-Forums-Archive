---
title: "Apache2 -V gives error after updgrading to Ubuntu 14.04 LTS"
date: 2015-06-10
forum: General Help
---

### Post by rob134 on 2015-06-10
```
        :/$ apache2 -V
    [Wed Jun 10 19:42:10.167410 2015] [core:warn] [pid 5778] AH00111: Config     variable ${APACHE_LOCK_DIR} is not defined
    [Wed Jun 10 19:42:10.167726 2015] [core:warn] [pid 5778] AH00111: Config variable ${APACHE_PID_FILE} is not defined
    [Wed Jun 10 19:42:10.167846 2015] [core:warn] [pid 5778] AH00111: Config variable ${APACHE_RUN_USER} is not defined
    [Wed Jun 10 19:42:10.167931 2015] [core:warn] [pid 5778] AH00111: Config variable ${APACHE_RUN_GROUP} is not defined
    [Wed Jun 10 19:42:10.179098 2015] [core:warn] [pid 5778] AH00111: Config variable ${APACHE_RUN_DIR} is not defined
    AH00526: Syntax error on line 61 of /etc/apache2/apache2.conf:
    Invalid Mutex directory in argument file:${APACHE_LOCK_DIR}

```





"source /etc/apache2/envvars" did the trick for me. 


```
        /$ apache2 -V
    Server version: Apache/2.4.7 (Ubuntu)
    Server built:   Mar 10 2015 13:05:59
    Server's Module Magic Number: 20120211:27
    Server loaded:  APR 1.5.1-dev, APR-UTIL 1.5.3
    Compiled using: APR 1.5.1-dev, APR-UTIL 1.5.3
    Architecture:   32-bit
    Server MPM:     prefork
      threaded:     no
        forked:     yes (variable process count)
    Server compiled with....
     -D APR_HAS_SENDFILE
     -D APR_HAS_MMAP
     -D APR_HAVE_IPV6 (IPv4-mapped addresses enabled)
     -D APR_USE_SYSVSEM_SERIALIZE
     -D APR_USE_PTHREAD_SERIALIZE
     -D SINGLE_LISTEN_UNSERIALIZED_ACCEPT
     -D APR_HAS_OTHER_CHILD
     -D AP_HAVE_RELIABLE_PIPED_LOGS
     -D DYNAMIC_MODULE_LIMIT=256
     -D HTTPD_ROOT="/etc/apache2"
     -D SUEXEC_BIN="/usr/lib/apache2/suexec"
     -D DEFAULT_PIDLOG="/var/run/apache2.pid"
     -D DEFAULT_SCOREBOARD="logs/apache_runtime_status"
     -D DEFAULT_ERRORLOG="logs/error_log"
     -D AP_TYPES_CONFIG_FILE="mime.types"
     -D SERVER_CONFIG_FILE="apache2.conf"

```

There's been a thread before on this here: [http://askubuntu.com/questions/452042/why-is-my-apache-not-working-after-upgrading-to-ubuntu-14-04](http://askubuntu.com/questions/452042/why-is-my-apache-not-working-after-upgrading-to-ubuntu-14-04)


And the solution worked only for a short period of time before "not defined" errors appear again. How come?

---

