---
title: "Can't get Akonadi service started so as to try out Kmail"
date: 2013-03-30
forum: General Help
---

### Post by zerubbabel on 2013-03-30
I thought I'd give Kmail a try, but it results in the following error report. If anyone has been down this path before and can tell me how to get around these errors, I'd appreciate it very much.

> Akonadi Server Self-Test Report
===============================

Test 1:  SUCCESS
--------

Database driver found.
Details: The QtSQL driver 'QMYSQL' is required by your current Akonadi server configuration and was found on your system.

File content of '/home/zerubbabel/.config/akonadi/akonadiserverrc':
[%General]
Driver=QMYSQL

[QMYSQL]
Name=akonadi
Host=
Options="UNIX_SOCKET=/home/zerubbabel/.local/share/akonadi/socket-dz/mysql.socket"
ServerPath=/usr/sbin/mysqld-akonadi
StartServer=true

[Debug]
Tracer=null


Test 2:  SUCCESS
--------

Akonadi is not running as root
Details: Akonadi is not running as a root/administrator user, which is the recommended setup for a secure system.

Test 3:  SUCCESS
--------

MySQL server found.
Details: You have currently configured Akonadi to use the MySQL server '/usr/sbin/mysqld-akonadi'.
Make sure you have the MySQL server installed, set the correct path and ensure you have the necessary read and execution rights on the server executable. The server executable is typically called 'mysqld'; its location varies depending on the distribution.

Test 4:  SUCCESS
--------

MySQL server is executable.
Details: MySQL server found: /usr/sbin/mysqld  Ver 5.5.29-0ubuntu1 for debian-linux-gnu on x86_64 ((Ubuntu))


Test 5:  ERROR
--------

MySQL server log contains errors.
Details: The MySQL server error log file &apos;<a href='/home/zerubbabel/.local/share/akonadi/db_data/mysql.err'>/home/zerubbabel/.local/share/akonadi/db_data/mysql.err</a>&apos; contains errors.

File content of '/home/zerubbabel/.local/share/akonadi/db_data/mysql.err':
130330 19:53:59 [Note] Plugin 'FEDERATED' is disabled.
130330 19:53:59 InnoDB: The InnoDB memory heap is disabled
130330 19:53:59 InnoDB: Mutexes and rw_locks use GCC atomic builtins
130330 19:53:59 InnoDB: Compressed tables use zlib 1.2.7
130330 19:53:59 InnoDB: Using Linux native AIO
130330 19:53:59 InnoDB: Initializing buffer pool, size = 80.0M
130330 19:53:59 InnoDB: Completed initialization of buffer pool
130330 19:53:59 InnoDB: highest supported file format is Barracuda.
InnoDB: No valid checkpoint found.
InnoDB: If this error appears when you are creating an InnoDB database,
InnoDB: the problem may be that during an earlier attempt you managed
InnoDB: to create the InnoDB data files, but log file creation failed.
InnoDB: If that is the case, please refer to
InnoDB: [http://dev.mysql.com/doc/refman/5.5/en/error-creating-innodb.html](http://dev.mysql.com/doc/refman/5.5/en/error-creating-innodb.html)
130330 19:53:59 [ERROR] Plugin 'InnoDB' init function returned error.
130330 19:53:59 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
130330 19:53:59 [ERROR] Unknown/unsupported storage engine: innodb
130330 19:53:59 [ERROR] Aborting

130330 19:53:59 [Note] /usr/sbin/mysqld: Shutdown complete



Test 6:  SUCCESS
--------

MySQL server default configuration found.
Details: The default configuration for the MySQL server was found and is readable at <a href='/etc/akonadi/mysql-global.conf'>/etc/akonadi/mysql-global.conf</a>.

File content of '/etc/akonadi/mysql-global.conf':
#
# Global Akonadi MySQL server settings,
# These settings can be adjusted using $HOME/.config/akonadi/mysql-local.conf
#
# Based on advice by Kris KÃ¶hntopp <kris@mysql.com>
#
[mysqld]

# strict query parsing/interpretation
# TODO: make Akonadi work with those settings enabled
# sql_mode=strict_trans_tables,strict_all_tables,strict_error_for_division_by_zero,no_auto_create_user,no_auto_value_on_zero,no_engine_substitution,no_zero_date,no_zero_in_date,only_full_group_by,pipes_as_concat
# sql_mode=strict_trans_tables

# DEBUGGING:
# log all queries, useful for debugging but generates an enormous amount of data
# log=mysql.full
# log queries slower than n seconds, log file name relative to datadir (for debugging only)
# log_slow_queries=mysql.slow
# long_query_time=1
# log queries not using indices, debug only, disable for production use
# log_queries_not_using_indexes=1
#
# mesure database size and adjust innodb_buffer_pool_size
# SELECT sum(data_length) as bla, sum(index_length) as blub FROM information_schema.tables WHERE table_schema not in ("mysql", "information_schema");

# NOTES:
# Keep Innob_log_waits and keep Innodb_buffer_pool_wait_free small (see show global status like "inno%", show global variables)

#expire_logs_days=3

#sync_bin_log=0

# Use UTF-8 encoding for tables
character_set_server=utf8
collation_server=utf8_general_ci

# use InnoDB for transactions and better crash recovery
default_storage_engine=innodb

# memory pool InnoDB uses to store data dictionary information and other internal data structures (default:1M)
innodb_additional_mem_pool_size=1M

# memory buffer InnoDB uses to cache data and indexes of its tables (default:128M)
# Larger values means less I/O
innodb_buffer_pool_size=80M

# Create a .ibd file for each table (default:0)
innodb_file_per_table=1

# Write out the log buffer to the log file at each commit (default:1)
innodb_flush_log_at_trx_commit=2

# Buffer size used to write to the log files on disk (default:1M for builtin, 8M for plugin)
# larger values means less I/O
innodb_log_buffer_size=1M

# Size of each log file in a log group (default:5M) larger means less I/O but more time for recovery.
innodb_log_file_size=64M

# # error log file name, relative to datadir (default:hostname.err)
log_error=mysql.err

# print warnings and connection errors (default:1)
log_warnings=2

# Convert table named to lowercase
lower_case_table_names=1

# Maximum size of one packet or any generated/intermediate string. (default:1M)
max_allowed_packet=32M

# Maximum simultaneous connections allowed (default:100)
max_connections=256

# The two options below make no sense with prepared statements and/or transactions
# (make sense when having the same query multiple times)

# Memory allocated for caching query results (default:0 (disabled))
query_cache_size=0

# Do not cache results (default:1)
query_cache_type=0

# Do not use the privileges mechanisms
skip_grant_tables

# Do not listen for TCP/IP connections at all
skip_networking

# The number of open tables for all threads. (default:64)
table_cache=200

# How many threads the server should cache for reuse (default:0)
thread_cache_size=3

# wait 365d before dropping the DB connection (default:8h)
wait_timeout=31536000

[client]
default-character-set=utf8


Test 7:  SKIP
--------

MySQL server custom configuration not available.
Details: The custom configuration for the MySQL server was not found but is optional.

Test 8:  SUCCESS
--------

MySQL server configuration is usable.
Details: The MySQL server configuration was found at <a href='/home/zerubbabel/.local/share/akonadi/mysql.conf'>/home/zerubbabel/.local/share/akonadi/mysql.conf</a> and is readable.

File content of '/home/zerubbabel/.local/share/akonadi/mysql.conf':
#
# Global Akonadi MySQL server settings,
# These settings can be adjusted using $HOME/.config/akonadi/mysql-local.conf
#
# Based on advice by Kris KÃ¶hntopp <kris@mysql.com>
#
[mysqld]

# strict query parsing/interpretation
# TODO: make Akonadi work with those settings enabled
# sql_mode=strict_trans_tables,strict_all_tables,strict_error_for_division_by_zero,no_auto_create_user,no_auto_value_on_zero,no_engine_substitution,no_zero_date,no_zero_in_date,only_full_group_by,pipes_as_concat
# sql_mode=strict_trans_tables

# DEBUGGING:
# log all queries, useful for debugging but generates an enormous amount of data
# log=mysql.full
# log queries slower than n seconds, log file name relative to datadir (for debugging only)
# log_slow_queries=mysql.slow
# long_query_time=1
# log queries not using indices, debug only, disable for production use
# log_queries_not_using_indexes=1
#
# mesure database size and adjust innodb_buffer_pool_size
# SELECT sum(data_length) as bla, sum(index_length) as blub FROM information_schema.tables WHERE table_schema not in ("mysql", "information_schema");

# NOTES:
# Keep Innob_log_waits and keep Innodb_buffer_pool_wait_free small (see show global status like "inno%", show global variables)

#expire_logs_days=3

#sync_bin_log=0

# Use UTF-8 encoding for tables
character_set_server=utf8
collation_server=utf8_general_ci

# use InnoDB for transactions and better crash recovery
default_storage_engine=innodb

# memory pool InnoDB uses to store data dictionary information and other internal data structures (default:1M)
innodb_additional_mem_pool_size=1M

# memory buffer InnoDB uses to cache data and indexes of its tables (default:128M)
# Larger values means less I/O
innodb_buffer_pool_size=80M

# Create a .ibd file for each table (default:0)
innodb_file_per_table=1

# Write out the log buffer to the log file at each commit (default:1)
innodb_flush_log_at_trx_commit=2

# Buffer size used to write to the log files on disk (default:1M for builtin, 8M for plugin)
# larger values means less I/O
innodb_log_buffer_size=1M

# Size of each log file in a log group (default:5M) larger means less I/O but more time for recovery.
innodb_log_file_size=64M

# # error log file name, relative to datadir (default:hostname.err)
log_error=mysql.err

# print warnings and connection errors (default:1)
log_warnings=2

# Convert table named to lowercase
lower_case_table_names=1

# Maximum size of one packet or any generated/intermediate string. (default:1M)
max_allowed_packet=32M

# Maximum simultaneous connections allowed (default:100)
max_connections=256

# The two options below make no sense with prepared statements and/or transactions
# (make sense when having the same query multiple times)

# Memory allocated for caching query results (default:0 (disabled))
query_cache_size=0

# Do not cache results (default:1)
query_cache_type=0

# Do not use the privileges mechanisms
skip_grant_tables

# Do not listen for TCP/IP connections at all
skip_networking

# The number of open tables for all threads. (default:64)
table_cache=200

# How many threads the server should cache for reuse (default:0)
thread_cache_size=3

# wait 365d before dropping the DB connection (default:8h)
wait_timeout=31536000

[client]
default-character-set=utf8


Test 9:  SUCCESS
--------

akonadictl found and usable
Details: The program '/usr/bin/akonadictl' to control the Akonadi server was found and could be executed successfully.
Result:
Akonadi 1.9.0


Test 10:  ERROR
--------

Akonadi control process not registered at D-Bus.
Details: The Akonadi control process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 11:  ERROR
--------

Akonadi server process not registered at D-Bus.
Details: The Akonadi server process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 12:  SUCCESS
--------

Nepomuk search service registered at D-Bus.
Details: The Nepomuk search service is registered at D-Bus which typically indicates it is operational.

Test 13:  SUCCESS
--------

Nepomuk search service uses an appropriate backend. 
Details: The Nepomuk search service uses one of the recommended backends.

Test 14:  SKIP
--------

Protocol version check not possible.
Details: Without a connection to the server it is not possible to check if the protocol version meets the requirements.

Test 15:  ERROR
--------

No resource agents found.
Details: No resource agents have been found, Akonadi is not usable without at least one. This usually means that no resource agents are installed or that there is a setup problem. The following paths have been searched: '/usr/share/akonadi/agents'. The XDG_DATA_DIRS environment variable is set to '/usr/share/kde-plasma:/usr/local/share/:/usr/share/'; make sure this includes all paths where Akonadi agents are installed.

Directory listing of '/usr/share/akonadi/agents':
akonadinepomukfeederagent.desktop
akonotesresource.desktop
archivemailagent.desktop
birthdaysresource.desktop
contactsresource.desktop
davgroupwareresource.desktop
facebookresource.desktop
googlecalendarresource.desktop
googlecontactsresource.desktop
icaldirresource.desktop
icalresource.desktop
imapresource.desktop
invitationsagent.desktop
kabcresource.desktop
kalarmdirresource.desktop
kalarmresource.desktop
kcalresource.desktop
kdeaccountsresource.desktop
knutresource.desktop
kolabproxyresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
maildispatcheragent.desktop
mailfilteragent.desktop
mboxresource.desktop
microblog.desktop
mixedmaildirresource.desktop
mtdummyresource.desktop
nepomuktagresource.desktop
nntpresource.desktop
notesresource.desktop
openxchangeresource.desktop
pop3resource.desktop
vcarddirresource.desktop
vcardresource.desktop

Environment variable XDG_DATA_DIRS is set to '/usr/share/kde-plasma:/usr/local/share/:/usr/share/'

Test 16:  ERROR
--------

Current Akonadi server error log found.
Details: The Akonadi server reported errors during its current startup. The log can be found in <a href='/home/zerubbabel/.local/share/akonadi/akonadiserver.error'>/home/zerubbabel/.local/share/akonadi/akonadiserver.error</a>.

File content of '/home/zerubbabel/.local/share/akonadi/akonadiserver.error':
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/home/zerubbabel/.local/share/akonadi/mysql.conf", "--datadir=/home/zerubbabel/.local/share/akonadi/db_data/", "--socket=/home/zerubbabel/.local/share/akonadi/socket-dz/mysql.socket") 
stdout: "" 
stderr: "" 
exit code: 1 
process error: "Unknown error" 
"[
0: akonadiserver() [0x418114]
1: akonadiserver() [0x418451]
2: /lib/x86_64-linux-gnu/libc.so.6(+0x370b0) [0x7ff0fa9fc0b0]
3: /lib/x86_64-linux-gnu/libc.so.6(gsignal+0x37) [0x7ff0fa9fc037]
4: /lib/x86_64-linux-gnu/libc.so.6(abort+0x148) [0x7ff0fa9ff698]
5: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x122) [0x7ff0fc4af5c2]
6: akonadiserver() [0x41a35b]
7: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0xb4) [0x7ff0fc5499f4]
8: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(+0x11662f) [0x7ff0fc55462f]
9: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x3b) [0x7ff0fc55cbcb]
10: akonadiserver() [0x48698a]
11: akonadiserver() [0x41b0b7]
12: akonadiserver() [0x41c035]
13: akonadiserver() [0x41d657]
14: akonadiserver() [0x411f13]
15: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf5) [0x7ff0fa9e6ea5]
16: akonadiserver() [0x4128d1]
]
" 


Test 17:  ERROR
--------

Previous Akonadi server error log found.
Details: The Akonadi server reported errors during its previous startup. The log can be found in <a href='/home/zerubbabel/.local/share/akonadi/akonadiserver.error.old'>/home/zerubbabel/.local/share/akonadi/akonadiserver.error.old</a>.

File content of '/home/zerubbabel/.local/share/akonadi/akonadiserver.error.old':
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/home/zerubbabel/.local/share/akonadi/mysql.conf", "--datadir=/home/zerubbabel/.local/share/akonadi/db_data/", "--socket=/home/zerubbabel/.local/share/akonadi/socket-dz/mysql.socket") 
stdout: "" 
stderr: "" 
exit code: 1 
process error: "Unknown error" 
"[
0: akonadiserver() [0x418114]
1: akonadiserver() [0x418451]
2: /lib/x86_64-linux-gnu/libc.so.6(+0x370b0) [0x7fad4916e0b0]
3: /lib/x86_64-linux-gnu/libc.so.6(gsignal+0x37) [0x7fad4916e037]
4: /lib/x86_64-linux-gnu/libc.so.6(abort+0x148) [0x7fad49171698]
5: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x122) [0x7fad4ac215c2]
6: akonadiserver() [0x41a35b]
7: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0xb4) [0x7fad4acbb9f4]
8: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(+0x11662f) [0x7fad4acc662f]
9: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x3b) [0x7fad4accebcb]
10: akonadiserver() [0x48698a]
11: akonadiserver() [0x41b0b7]
12: akonadiserver() [0x41c035]
13: akonadiserver() [0x41d657]
14: akonadiserver() [0x411f13]
15: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf5) [0x7fad49158ea5]
16: akonadiserver() [0x4128d1]
]
" 


Test 18:  SUCCESS
--------

No current Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its current startup.

Test 19:  SUCCESS
--------

No previous Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its previous startup.


---

