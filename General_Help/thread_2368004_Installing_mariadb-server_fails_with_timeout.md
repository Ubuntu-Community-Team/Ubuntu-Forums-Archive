---
title: "Installing mariadb-server fails with timeout"
date: 2017-08-05
forum: General Help
---

### Post by cesera on 2017-08-05
I am using kubuntu 17.04 and am trying to switch from mysql (5.7) to mariadb. However the install fails with a timeout and I am not sure what to do about this.

The error I am getting is this (the first line takes a few minutes and then the rest follows straight-away), any help would be greatly appreciated:

Setting up mariadb-server-10.1 (10.1.25-0ubuntu0.17.04.1) ...
Job for mariadb.service failed because the control process exited with error code.
See "systemctl status mariadb.service" and "journalctl -xe" for details.
invoke-rc.d: initscript mysql, action "start" failed.
&#9679; mariadb.service - MariaDB database server
   Loaded: loaded (/lib/systemd/system/mariadb.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sat 2017-08-05 19:38:12 BST; 6ms ago
  Process: 2709 ExecStartPost=/etc/mysql/debian-start (code=exited, status=203/EXEC)
  Process: 2682 ExecStart=/usr/sbin/mysqld $MYSQLD_OPTS $_WSREP_NEW_CLUSTER $_WSREP_START_POSITION (code=exited, status=0/SUCCESS)
  Process: 2670 ExecStartPre=/bin/sh -c [ ! -e /usr/bin/galera_recovery ] && VAR= ||   VAR=`/usr/bin/galera_recovery`; [ $? -eq 0 ]   && systemctl set-environment _WSREP_START_POSITION=$VAR || exit 1 (code=exited, status=0/SUCCESS)
  Process: 2667 ExecStartPre=/bin/sh -c systemctl unset-environment _WSREP_START_POSITION (code=exited, status=0/SUCCESS)
  Process: 2664 ExecStartPre=/usr/bin/install -m 755 -o mysql -g root -d /var/run/mysqld (code=exited, status=0/SUCCESS)
 Main PID: 2682 (code=exited, status=0/SUCCESS)
   Status: "MariaDB server is down"

Aug 05 19:38:09 aragorn mysqld[2682]: 2017-08-05 19:38:09 140608605203200 [Note] /usr/sbin/mysqld: Normal shutdown
Aug 05 19:38:09 aragorn mysqld[2682]: 2017-08-05 19:38:09 140608605203200 [Note] Event Scheduler: Purging the queue. 0 events
Aug 05 19:38:09 aragorn mysqld[2682]: 2017-08-05 19:38:09 140607909500672 [Note] InnoDB: FTS optimize thread exiting.
Aug 05 19:38:09 aragorn mysqld[2682]: 2017-08-05 19:38:09 140608605203200 [Note] InnoDB: Starting shutdown...
Aug 05 19:38:10 aragorn mysqld[2682]: 2017-08-05 19:38:10 140608605203200 [Note] InnoDB: Waiting for page_cleaner to finish flushing of buffer pool
Aug 05 19:38:12 aragorn mysqld[2682]: 2017-08-05 19:38:12 140608605203200 [Note] InnoDB: Shutdown completed; log sequence number 1617431
Aug 05 19:38:12 aragorn mysqld[2682]: 2017-08-05 19:38:12 140608605203200 [Note] /usr/sbin/mysqld: Shutdown complete
Aug 05 19:38:12 aragorn systemd[1]: Failed to start MariaDB database server.
Aug 05 19:38:12 aragorn systemd[1]: mariadb.service: Unit entered failed state.
Aug 05 19:38:12 aragorn systemd[1]: mariadb.service: Failed with result 'exit-code'.
Hint: Some lines were ellipsized, use -l to show in full.
dpkg: error processing package mariadb-server-10.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            dpkg: dependency problems prevent configuration of mariadb-server:
 mariadb-server depends on mariadb-server-10.1 (>= 10.1.25-0ubuntu0.17.04.1); however:
  Package mariadb-server-10.1 is not configured yet.

dpkg: error processing package mariadb-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mariadb-server-10.1
 mariadb-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

