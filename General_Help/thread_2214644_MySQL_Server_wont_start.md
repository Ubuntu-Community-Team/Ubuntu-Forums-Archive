---
title: "MySQL Server wont start"
date: 2014-04-02
forum: General Help
---

### Post by Alan_Killian on 2014-04-02
Hello once again,
I am setting up a new LAMP server with Ubuntu Server 13.10 and MySQL 5.5 and was in the middle of migrating mysql databases to new server when I realized mysql server is not running. All was fine last time I checked a couple of days ago. I get this when I try to launch server from command line:

**@Ubuntu:~$ sudo mysqld start
[sudo] password for ***:
140402 10:32:07 [Warning] Using unique option prefix key_buffer instead of key_buffer_size is deprecated and will be removed in a future release. Please use the full name instead.
140402 10:32:07 [Warning] Using unique option prefix myisam-recover instead of myisam-recover-options is deprecated and will be removed in a future release. Please use the full name instead.
140402 10:32:07 [Note] Plugin 'FEDERATED' is disabled.
mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
140402 10:32:07 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
140402 10:32:07 InnoDB: The InnoDB memory heap is disabled
140402 10:32:07 InnoDB: Mutexes and rw_locks use GCC atomic builtins
140402 10:32:07 InnoDB: Compressed tables use zlib 1.2.8
140402 10:32:07 InnoDB: Using Linux native AIO
140402 10:32:07 InnoDB: Initializing buffer pool, size = 128.0M
140402 10:32:07 InnoDB: Completed initialization of buffer pool
140402 10:32:07  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.

also when I try this:
***@Ubuntu-SHS:~$ sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                         [ OK ]
 * Starting MySQL database server mysqld                                         [fail]

P.S.- Nothing in the error logs

Would appreciate if anyone has idea what has happened to my setup. Thanks.

---

