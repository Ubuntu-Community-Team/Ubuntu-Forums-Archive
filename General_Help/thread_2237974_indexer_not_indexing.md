---
title: "indexer not indexing"
date: 2014-08-05
forum: General Help
---

### Post by betlog-hax on 2014-08-05
baloo/akonadi are not completely indexing my system.
I can search for something I am actually looking at, and yet no search results appear.
Searches will often yield results from one of my drives but not find something on on another drive. Albeit they are all USB3 drives, but permanently mounted via fstab.

The only place I can see obvious problems are by:
Running akonaditray, opening the Akonadi Server configuration, and hitting "Test" I get the errors posted below.
But I have no idea how to diagnose or fix this error, or if it's even related to the fact that I get some search results, but not others.

I'm sure there is a simple way to rebuild the database or force indexing of a specific structure, but system settings offerings are far too simplistic. Even trying to google for command line syntax is made impossible by the sheer quantity of whining by people wanting to disable indexing.

Assistance greatly appreciated.


PS: why is there no existing forum tag for "kubuntu 14.04"  or "baloo"?


> Akonadi Server Self-Test Report
===============================

Test 1:  SUCCESS
--------

Database driver found.
Details: The QtSQL driver 'QMYSQL' is required by your current Akonadi server configuration and was found on your system.

File content of '/home/user/.config/akonadi/akonadiserverrc':
[%General]
Driver=QMYSQL

[QMYSQL]
Name=akonadi
Host=
Options="UNIX_SOCKET=/tmp/akonadi-user.iLipuv/mysql.socket"
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
Details: MySQL server found: 140805 17:01:51 [Warning] Using unique option prefix key_buffer instead of key_buffer_size is deprecated and will be removed in a future release. Please use the full name instead.
/usr/sbin/mysqld  Ver 5.5.38-0ubuntu0.14.04.1 for debian-linux-gnu on x86_64 ((Ubuntu))


Test 5:  SUCCESS
--------

MySQL server log contains no errors.
Details: The MySQL server log file &apos;<a href='/home/user/.local/share/akonadi/db_data/mysql.err'>/home/user/.local/share/akonadi/db_data/mysql.err</a>&apos; does not contain any errors or warnings.

File content of '/home/user/.local/share/akonadi/db_data/mysql.err':
140805 16:44:57 [Note] Plugin 'FEDERATED' is disabled.
140805 16:44:57 InnoDB: The InnoDB memory heap is disabled
140805 16:44:57 InnoDB: Mutexes and rw_locks use GCC atomic builtins
140805 16:44:57 InnoDB: Compressed tables use zlib 1.2.8
140805 16:44:57 InnoDB: Using Linux native AIO
140805 16:44:57 InnoDB: Initializing buffer pool, size = 80.0M
140805 16:44:57 InnoDB: Completed initialization of buffer pool
140805 16:44:57 InnoDB: highest supported file format is Barracuda.
140805 16:44:58  InnoDB: Waiting for the background threads to start
140805 16:44:59 InnoDB: 5.5.38 started; log sequence number 47598933
140805 16:44:59 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.5.38-0ubuntu0.14.04.1'  socket: '/tmp/akonadi-user.iLipuv/mysql.socket'  port: 0  (Ubuntu)


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
# Deprecated in MySQL >= 5.6.3
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
table_open_cache=200

# How many threads the server should cache for reuse (default:0)
thread_cache_size=3

# wait 365d before dropping the DB connection (default:8h)
wait_timeout=31536000

# We use InnoDB, so don't let MyISAM eat up memory
key_buffer_size=16K

[client]
default-character-set=utf8


Test 7:  SKIP
--------

MySQL server custom configuration not available.
Details: The custom configuration for the MySQL server was not found but is optional.

Test 8:  SUCCESS
--------

MySQL server configuration is usable.
Details: The MySQL server configuration was found at <a href='/home/user/.local/share/akonadi/mysql.conf'>/home/user/.local/share/akonadi/mysql.conf</a> and is readable.

File content of '/home/user/.local/share/akonadi/mysql.conf':
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
# Deprecated in MySQL >= 5.6.3
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
table_open_cache=200

# How many threads the server should cache for reuse (default:0)
thread_cache_size=3

# wait 365d before dropping the DB connection (default:8h)
wait_timeout=31536000

# We use InnoDB, so don't let MyISAM eat up memory
key_buffer_size=16K

[client]
default-character-set=utf8


Test 9:  SUCCESS
--------

akonadictl found and usable
Details: The program '/usr/bin/akonadictl' to control the Akonadi server was found and could be executed successfully.
Result:
Akonadi 1.12.1


Test 10:  SUCCESS
--------

Akonadi control process registered at D-Bus.
Details: The Akonadi control process is registered at D-Bus which typically indicates it is operational.

Test 11:  SUCCESS
--------

Akonadi server process registered at D-Bus.
Details: The Akonadi server process is registered at D-Bus which typically indicates it is operational.

Test 12:  SKIP
--------

Protocol version check not possible.
Details: Without a connection to the server it is not possible to check if the protocol version meets the requirements.

Test 13:  SUCCESS
--------

Resource agents found.
Details: At least one resource agent has been found.

Directory listing of '/usr/share/akonadi/agents':
akonadibalooindexingagent.desktop
akonadinepomukfeederagent.desktop
akonotesresource.desktop
archivemailagent.desktop
birthdaysresource.desktop
contactsresource.desktop
davgroupwareresource.desktop
facebookresource.desktop
folderarchiveagent.desktop
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
kolabproxyresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
maildispatcheragent.desktop
mailfilteragent.desktop
mboxresource.desktop
migrationagent.desktop
mixedmaildirresource.desktop
mtdummyresource.desktop
newmailnotifieragent.desktop
nntpresource.desktop
notesagent.desktop
notesresource.desktop
openxchangeresource.desktop
pop3resource.desktop
sendlateragent.desktop
vcarddirresource.desktop
vcardresource.desktop

Environment variable XDG_DATA_DIRS is set to '/usr/share:/usr/share/kde-plasma:/usr/local/share/:/usr/share/'

Test 14:  SUCCESS
--------

No current Akonadi server error log found.
Details: The Akonadi server did not report any errors during its current startup.

Test 15:  ERROR
--------

Previous Akonadi server error log found.
Details: The Akonadi server reported errors during its previous startup. The log can be found in <a href='/home/user/.local/share/akonadi/akonadiserver.error.old'>/home/user/.local/share/akonadi/akonadiserver.error.old</a>.

File content of '/home/user/.local/share/akonadi/akonadiserver.error.old':
Control process died, committing suicide! 


Test 16:  ERROR
--------

Current Akonadi control error log found.
Details: The Akonadi control process reported errors during its current startup. The log can be found in <a href='/home/user/.local/share/akonadi/akonadi_control.error'>/home/user/.local/share/akonadi/akonadi_control.error</a>.

File content of '/home/user/.local/share/akonadi/akonadi_control.error':
Executable "akonadi_nepomuk_feeder" for agent "akonadi_nepomuk_feeder" could not be found! 
Executable "akonadi_folderarchive_agent" for agent "akonadi_folderarchive_agent" could not be found! 
QString AgentManager::agentInstanceType(const QString&) Agent instance with identifier "akonadi_contacts_resource_1" does not exist 


Test 17:  ERROR
--------

Previous Akonadi control error log found.
Details: The Akonadi control process reported errors during its previous startup. The log can be found in <a href='/home/user/.local/share/akonadi/akonadi_control.error.old'>/home/user/.local/share/akonadi/akonadi_control.error.old</a>.

File content of '/home/user/.local/share/akonadi/akonadi_control.error.old':
Executable "akonadi_nepomuk_feeder" for agent "akonadi_nepomuk_feeder" could not be found! 
Executable "akonadi_folderarchive_agent" for agent "akonadi_folderarchive_agent" could not be found! 
QString AgentManager::agentInstanceType(const QString&) Agent instance with identifier "akonadi_contacts_resource_1" does not exist 



---

