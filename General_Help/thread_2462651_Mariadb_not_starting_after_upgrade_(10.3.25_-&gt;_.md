---
title: "Mariadb not starting after upgrade (10.3.25 -&gt; 10.3.29)"
date: 2021-05-25
forum: General Help
---

### Post by ironmonkey2 on 2021-05-25
Running Ubuntu server 20.04 and after Mariadb upgrade 10.3.25 to 10.3.29 it does not start anymore.


journalctl:

```
May 24 20:16:39 xxx systemd[1]: Starting MariaDB 10.3.29 database server...
May 24 20:16:39 xxx mysqld[263457]: 2021-05-24 20:16:39 0 [Note] /usr/sbin/mysqld (mysqld 10.3.29-MariaDB-0ubuntu0.20.04.1) starting as process 263457 ...
May 24 20:16:39 xxx systemd[1]: mariadb.service: Main process exited, code=exited, status=1/FAILURE
May 24 20:16:39 xxx systemd[1]: mariadb.service: Failed with result 'exit-code'.
May 24 20:16:39 xxx systemd[1]: Failed to start MariaDB 10.3.29 database server.
```






/var/log/mysql/error.log:

```
2021-05-24 20:16:39 0 [Note] InnoDB: Using Linux native AIO
2021-05-24 20:16:39 0 [Note] InnoDB: Mutexes and rw_locks use GCC atomic builtins
2021-05-24 20:16:39 0 [Note] InnoDB: Uses event mutexes
2021-05-24 20:16:39 0 [Note] InnoDB: Compressed tables use zlib 1.2.11
2021-05-24 20:16:39 0 [Note] InnoDB: Number of pools: 1
2021-05-24 20:16:39 0 [Note] InnoDB: Using SSE2 crc32 instructions
2021-05-24 20:16:39 0 [Note] InnoDB: Initializing buffer pool, total size = 128M, instances = 1, chunk size = 128M
2021-05-24 20:16:39 0 [Note] InnoDB: Completed initialization of buffer pool
2021-05-24 20:16:39 0 [Note] InnoDB: If the mysqld execution user is authorized, page cleaner thread priority can be changed. See the man page of setpriority().
2021-05-24 20:16:39 0 [Note] InnoDB: 128 out of 128 rollback segments are active.
2021-05-24 20:16:39 0 [Note] InnoDB: Creating shared tablespace for temporary tables
2021-05-24 20:16:39 0 [Note] InnoDB: Setting file './ibtmp1' size to 12 MB. Physically writing the file full; Please wait ...
2021-05-24 20:16:39 0 [Note] InnoDB: File './ibtmp1' size is now 12 MB.
2021-05-24 20:16:39 0 [Note] InnoDB: Waiting for purge to start
2021-05-24 20:16:39 0 [Note] InnoDB: 10.3.29 started; log sequence number 134078645; transaction id 11982
2021-05-24 20:16:39 0 [Note] InnoDB: Loading buffer pool(s) from /var/lib/mysql/ib_buffer_pool
2021-05-24 20:16:39 0 [Note] Plugin 'FEEDBACK' is disabled.
2021-05-24 20:16:39 0 [Note] Server socket created on IP: '127.0.0.1'.
2021-05-24 20:16:39 0 [ERROR] Fatal error: Can't open and lock privilege tables: 'mysql.user' is not of type 'TABLE'
```

Any ideas how to proceed?


EDIT: Turned out my database was broken already before this update.  Something in my database dump broke mysql.user table. Worked around that  importing databse like this
```

mysql --user='marie' --password='marie2' sales_dept < '/tmp/prospects.sql'

```
so that import has no rights to modify mysql.user table.

---

### Post by TheFu on 2021-05-27
Please save the community time by using the "Thread Tools" button and marking this thread "SOLVED", plesae.

---

