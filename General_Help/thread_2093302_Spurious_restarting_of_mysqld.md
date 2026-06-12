---
title: "Spurious restarting of mysqld"
date: 2012-12-10
forum: General Help
---

### Post by defaria on 2012-12-10
I have a process I developed that runs continually and updates a mysql database. It works find for days and weeks on end but every once in a while I get an error message from mysql of "MySQL server has gone away". It comes back and I've coded my application to note but handle this situation by retrying the request. But why does mysql go away?

It happened again today so I checked /var/log/mysqld.log and find the following. It really doesn't seem to make sense to me - it seems like it just decides to restart and when it is doing that it opens up a window for applications to fail. Is this normal? How can I configure this to not happen?

```

121129  0:30:25 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.5.28-0ubuntu0.12.04.2'  socket: '/var/run/mysqld/mysqld.sock'  port:
 3306  (Ubuntu)
121210  7:40:30 [Note] /usr/sbin/mysqld: Normal shutdown

121210  7:40:30 [Note] Event Scheduler: Purging the queue. 0 events
121210  7:40:32 [Warning] /usr/sbin/mysqld: Forcing close of thread 40  user: 'c
learwriter'

121210  7:40:33  InnoDB: Starting shutdown...
121210  7:40:36  InnoDB: Shutdown completed; log sequence number 1540348566
121210  7:40:36 [Note] /usr/sbin/mysqld: Shutdown complete

121210  7:41:37 [Note] Plugin 'FEDERATED' is disabled.
121210  7:41:37 InnoDB: The InnoDB memory heap is disabled
121210  7:41:37 InnoDB: Mutexes and rw_locks use GCC atomic builtins
121210  7:41:37 InnoDB: Compressed tables use zlib 1.2.3.4
121210  7:41:37 InnoDB: Initializing buffer pool, size = 128.0M
121210  7:41:37 InnoDB: Completed initialization of buffer pool
121210  7:41:37 InnoDB: highest supported file format is Barracuda.
121210  7:41:38  InnoDB: Waiting for the background threads to start
121210  7:41:39 InnoDB: 1.1.8 started; log sequence number 1540348566
121210  7:41:39  InnoDB: Starting shutdown...
121210  7:41:41  InnoDB: Shutdown completed; log sequence number 1540353631
121210  7:41:41 [Note] Plugin 'FEDERATED' is disabled.
121210  7:41:41 InnoDB: The InnoDB memory heap is disabled
121210  7:41:41 InnoDB: Mutexes and rw_locks use GCC atomic builtins
121210  7:41:41 InnoDB: Compressed tables use zlib 1.2.3.4
121210  7:41:41 InnoDB: Initializing buffer pool, size = 128.0M
121210  7:41:41 InnoDB: Completed initialization of buffer pool
121210  7:41:41 InnoDB: highest supported file format is Barracuda.
121210  7:41:41  InnoDB: Waiting for the background threads to start
121210  7:41:42 InnoDB: 1.1.8 started; log sequence number 1540353631
ERROR: 1064  You have an error in your SQL syntax; check the manual that corresp
onds to your MySQL server version for the right syntax to use near 'ALTER TABLE 
user ADD column Show_view_priv enum('N','Y') CHARACTER SET utf8 NOT ' at line 1
121210  7:41:42 [ERROR] Aborting
121210  7:41:46  InnoDB: Starting shutdown...
121210  7:41:49  InnoDB: Shutdown completed; log sequence number 1540353631
121210  7:41:49 [Note] /usr/sbin/mysqld: Shutdown complete

121210  7:41:50 [Note] Plugin 'FEDERATED' is disabled.
121210  7:41:50 InnoDB: The InnoDB memory heap is disabled
121210  7:41:50 InnoDB: Mutexes and rw_locks use GCC atomic builtins
121210  7:41:50 InnoDB: Compressed tables use zlib 1.2.3.4
121210  7:41:50 InnoDB: Initializing buffer pool, size = 128.0M
121210  7:41:50 InnoDB: Completed initialization of buffer pool
121210  7:41:50 InnoDB: highest supported file format is Barracuda.
121210  7:41:51  InnoDB: Waiting for the background threads to start
121210  7:41:52 InnoDB: 1.1.8 started; log sequence number 1540353631
121210  7:41:52 [Note] Server hostname (bind-address): '0.0.0.0'; port: 3306
121210  7:41:52 [Note]   - '0.0.0.0' resolves to '0.0.0.0';
121210  7:41:52 [Note] Server socket created on IP: '0.0.0.0'.
121210  7:41:52 [Note] Event Scheduler: Loaded 0 events
121210  7:41:52 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.5.28-0ubuntu0.12.04.3'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)


```

Note if this is not the correct place to ask this question kindly point me in the right direction.

Thanks.

---

### Post by Ms. Daisy on 2012-12-11
I had a similar instance happen. In my case I determined for me that my DHCP router would reassign the IP after several hours.  Once I set a static IP for my Ubuntu box (which housed the mysql server), then it didn't recur.  This happened both when it was NAT'd and when it was bridged through virtualbox.

---

### Post by tgalati4 on 2012-12-11
A lot of services use mysql, so when it crashes and has to restart, those services will fail until mysql starts responding again.  So, what is causing your mysql to fail?  What services are you running that use mysql?  Check the log files of those services as well as other log files in /var/log to see if there is some other condition (such as dhcp reassignment as Ms Daisy suggested).

By running phpmyadmin in a webpage you can see the status of the tables in mysql and resources required and perhaps see a pattern that causes it to fail.

Don't forget to check your /etc/mysql/my.cnf settings.  There are a lot of cache and query sizes--hitting one of those will surely cause your mysql instance to fall over.

---

### Post by defaria on 2012-12-20
My IPs are statically assigned, have been forever.

No other services use mysqld - 'cept the one I specifically wrote! I know this because mysqld service was not on before I developed this application myself and when I did I specifically turned on mysqld. It has been working for literally years without issue 'cept lately when I started getting this spurious restarting.

Spurious restarting is just what it means - it just restarts for no apparent reason. There is no "crash" of mysqld - it just decides for some unknown reason, to restart. THAT's the question.

---

