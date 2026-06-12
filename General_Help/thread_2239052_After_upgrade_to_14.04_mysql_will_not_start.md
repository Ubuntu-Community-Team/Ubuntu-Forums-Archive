---
title: "After upgrade to 14.04 mysql will not start"
date: 2014-08-11
forum: General Help
---

### Post by n41076jem-2 on 2014-08-11
did os update to ubuntu 14.04 lts, which included mysql release 5.6


The following is what happened when I try to start mysqld:




---------------------------------------------------------------------------
root@atria:/var/log/mysql# mysqld
140811 13:41:00 [Warning] Using unique option prefix key_buffer instead of key_buffer_size is deprecated and will be removed in a future release. Please use the full name instead.
root@atria:/var/log/mysql#
root@atria:/var/log/mysql#
root@atria:/var/log/mysql#
root@atria:/var/log/mysql#
root@atria:/var/log/mysql#
root@atria:/var/log/mysql# cat error.log
140811 13:41:00 [Warning] Using unique option prefix myisam-recover instead of myisam-recover-options is deprecated and will be removed in a future release. Please use the full name instead.
140811 13:41:00 [Note] Plugin 'FEDERATED' is disabled.
140811 13:41:00 InnoDB: The InnoDB memory heap is disabled
140811 13:41:00 InnoDB: Mutexes and rw_locks use GCC atomic builtins
140811 13:41:00 InnoDB: Compressed tables use zlib 1.2.3.4
140811 13:41:00 InnoDB: Initializing buffer pool, size = 128.0M
140811 13:41:00 InnoDB: Completed initialization of buffer pool
140811 13:41:00 InnoDB: highest supported file format is Barracuda.
InnoDB: 1 transaction(s) which must be rolled back or cleaned up
InnoDB: in total 1 row operations to undo
InnoDB: Trx id counter is 41F700
InnoDB: Cleaning up trx with id 41EF4A
140811 13:41:00  InnoDB: Waiting for the background threads to start
140811 13:41:01 InnoDB: 5.5.38 started; log sequence number 2298919436
140811 13:41:01 [Note] Server hostname (bind-address): '127.0.0.1'; port: 3306
140811 13:41:01 [Note]   - '127.0.0.1' resolves to '127.0.0.1';
140811 13:41:01 [Note] Server socket created on IP: '127.0.0.1'.
140811 13:41:01 [Note] Event Scheduler: Loaded 0 events
140811 13:41:01 [Note] mysqld: ready for connections.
Version: '5.5.38-0ubuntu0.12.04.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
140811 13:41:01  InnoDB: Assertion failure in thread 140677452908288 in file trx0purge.c line 840
InnoDB: Failing assertion: purge_sys->purge_trx_no <= purge_sys->rseg->last_trx_no
InnoDB: We intentionally generate a memory trap.
InnoDB: Submit a detailed bug report to [http://bugs.mysql.com](http://bugs.mysql.com).
InnoDB: If you get repeated assertion failures or crashes, even
InnoDB: immediately after the mysqld startup, there may be
InnoDB: corruption in the InnoDB tablespace. Please refer to
InnoDB: [http://dev.mysql.com/doc/refman/5.5/en/forcing-innodb-recovery.html](http://dev.mysql.com/doc/refman/5.5/en/forcing-innodb-recovery.html)
InnoDB: about forcing recovery.
20:41:01 UTC - mysqld got signal 6 ;
This could be because you hit a bug. It is also possible that this binary
or one of the libraries it was linked against is corrupt, improperly built,
or misconfigured. This error can also be caused by malfunctioning hardware.
We will try our best to scrape up some info that will hopefully help
diagnose the problem, but since we have already crashed,
something is definitely wrong and this may fail.


key_buffer_size=16777216
read_buffer_size=131072
max_used_connections=0
max_threads=151
thread_count=0
connection_count=0
It is possible that mysqld could use up to
key_buffer_size + (read_buffer_size + sort_buffer_size)*max_threads = 346700 K  bytes of memory
Hope that's ok; if not, decrease some variables in the equation.


Thread pointer: 0x0
Attempting backtrace. You can use the following information to find out
where mysqld died. If you see no messages after this, something went
terribly wrong...
stack_bottom = 0 thread_stack 0x30000
mysqld(my_print_stacktrace+0x29)[0x7ff21c67bb09]
mysqld(handle_fatal_signal+0x483)[0x7ff21c540e23]
/lib/x86_64-linux-gnu/libpthread.so.0(+0xfcb0)[0x7ff21b28acb0]
/lib/x86_64-linux-gnu/libc.so.6(gsignal+0x35)[0x7ff21a8f5425]
/lib/x86_64-linux-gnu/libc.so.6(abort+0x17b)[0x7ff21a8f8b8b]
mysqld(+0x60bc24)[0x7ff21c72dc24]
mysqld(+0x60c0a4)[0x7ff21c72e0a4]
mysqld(+0x6d2cff)[0x7ff21c7f4cff]
mysqld(+0x6c9335)[0x7ff21c7eb335]
mysqld(+0x60df0e)[0x7ff21c72ff0e]
mysqld(+0x5fedec)[0x7ff21c720dec]
mysqld(+0x603273)[0x7ff21c725273]
/lib/x86_64-linux-gnu/libpthread.so.0(+0x7e9a)[0x7ff21b282e9a]
/lib/x86_64-linux-gnu/libc.so.6(clone+0x6d)[0x7ff21a9b33fd]
The manual page at [http://dev.mysql.com/doc/mysql/en/crashing.html](http://dev.mysql.com/doc/mysql/en/crashing.html) contains
information that should help you find out what is causing the crash.
root@atria:/var/log/mysql#

---

