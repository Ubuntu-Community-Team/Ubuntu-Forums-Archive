---
title: "mysqld taking to long to shutdown?"
date: 2017-03-09
forum: General Help
---

### Post by shamsat on 2017-03-09
In ubuntu 16.10 mysqld is taking to long about 10 minutes to shutdown this is the message when shutting down the ubuntu:
```

[***] A stop job is running for Mysql Community Server (1 3 s / 10 min 9 s)

```
The stop watch (1 3 s /10 min 9 s) is running until reach the 10 min and 9 s then ubuntu is shutting down after few more jobs.
this is the /va/log/mysql/error.log file:

```
2017-03-09T07:15:54.955435Z 0 [Note] Giving 0 client threads a chance to die gracefully
2017-03-09T07:15:54.996949Z 0 [Note] Shutting down slave threads
2017-03-09T07:15:55.017438Z 0 [Note] Forcefully disconnecting 0 remaining clients
2017-03-09T07:15:55.069346Z 0 [Note] Event Scheduler: Purging the queue. 0 events
2017-03-09T07:15:55.173737Z 0 [Note] Binlog end
2017-03-09T07:16:00.349341Z 0 [Note] Shutting down plugin 'auth_socket'
2017-03-09T07:16:00.378778Z 0 [Note] Shutting down plugin 'ngram'
2017-03-09T07:16:00.668207Z 0 [Note] Shutting down plugin 'partition'
2017-03-09T07:16:00.668233Z 0 [Note] Shutting down plugin 'BLACKHOLE'
2017-03-09T07:16:00.809994Z 0 [Note] Shutting down plugin 'ARCHIVE'
2017-03-09T07:16:00.810040Z 0 [Note] Shutting down plugin 'PERFORMANCE_SCHEMA'
2017-03-09T07:16:01.030184Z 0 [Note] Shutting down plugin 'MRG_MYISAM'
2017-03-09T07:16:01.030243Z 0 [Note] Shutting down plugin 'MyISAM'
2017-03-09T07:16:01.158664Z 0 [Note] Shutting down plugin 'INNODB_SYS_VIRTUAL'
2017-03-09T07:16:01.168735Z 0 [Note] Shutting down plugin 'INNODB_SYS_DATAFILES'
2017-03-09T07:16:01.168756Z 0 [Note] Shutting down plugin 'INNODB_SYS_TABLESPACES'
2017-03-09T07:16:01.168764Z 0 [Note] Shutting down plugin 'INNODB_SYS_FOREIGN_COLS'
2017-03-09T07:16:01.168772Z 0 [Note] Shutting down plugin 'INNODB_SYS_FOREIGN'
2017-03-09T07:16:01.168779Z 0 [Note] Shutting down plugin 'INNODB_SYS_FIELDS'
2017-03-09T07:16:01.168786Z 0 [Note] Shutting down plugin 'INNODB_SYS_COLUMNS'
2017-03-09T07:16:01.168793Z 0 [Note] Shutting down plugin 'INNODB_SYS_INDEXES'
2017-03-09T07:16:01.168800Z 0 [Note] Shutting down plugin 'INNODB_SYS_TABLESTATS'
2017-03-09T07:16:01.168807Z 0 [Note] Shutting down plugin 'INNODB_SYS_TABLES'
2017-03-09T07:16:01.168814Z 0 [Note] Shutting down plugin 'INNODB_FT_INDEX_TABLE'
2017-03-09T07:16:01.168821Z 0 [Note] Shutting down plugin 'INNODB_FT_INDEX_CACHE'
2017-03-09T07:16:01.168828Z 0 [Note] Shutting down plugin 'INNODB_FT_CONFIG'
2017-03-09T07:16:01.168835Z 0 [Note] Shutting down plugin 'INNODB_FT_BEING_DELETED'
2017-03-09T07:16:01.168842Z 0 [Note] Shutting down plugin 'INNODB_FT_DELETED'
2017-03-09T07:16:01.168849Z 0 [Note] Shutting down plugin 'INNODB_FT_DEFAULT_STOPWORD'
2017-03-09T07:16:01.168856Z 0 [Note] Shutting down plugin 'INNODB_METRICS'
2017-03-09T07:16:01.168863Z 0 [Note] Shutting down plugin 'INNODB_TEMP_TABLE_INFO'
2017-03-09T07:16:01.168870Z 0 [Note] Shutting down plugin 'INNODB_BUFFER_POOL_STATS'
2017-03-09T07:16:01.168877Z 0 [Note] Shutting down plugin 'INNODB_BUFFER_PAGE_LRU'
2017-03-09T07:16:01.168884Z 0 [Note] Shutting down plugin 'INNODB_BUFFER_PAGE'
2017-03-09T07:16:01.168891Z 0 [Note] Shutting down plugin 'INNODB_CMP_PER_INDEX_RESET'
2017-03-09T07:16:01.168898Z 0 [Note] Shutting down plugin 'INNODB_CMP_PER_INDEX'
2017-03-09T07:16:01.168905Z 0 [Note] Shutting down plugin 'INNODB_CMPMEM_RESET'
2017-03-09T07:16:01.168911Z 0 [Note] Shutting down plugin 'INNODB_CMPMEM'
2017-03-09T07:16:01.168918Z 0 [Note] Shutting down plugin 'INNODB_CMP_RESET'
2017-03-09T07:16:01.168925Z 0 [Note] Shutting down plugin 'INNODB_CMP'
2017-03-09T07:16:01.168933Z 0 [Note] Shutting down plugin 'INNODB_LOCK_WAITS'
2017-03-09T07:16:01.168939Z 0 [Note] Shutting down plugin 'INNODB_LOCKS'
2017-03-09T07:16:01.168946Z 0 [Note] Shutting down plugin 'INNODB_TRX'
2017-03-09T07:16:01.168954Z 0 [Note] Shutting down plugin 'InnoDB'
2017-03-09T07:16:01.396676Z 0 [Note] InnoDB: FTS optimize thread exiting.
2017-03-09T07:16:01.512793Z 0 [Note] InnoDB: Starting shutdown...
2017-03-09T07:16:02.021556Z 0 [Note] InnoDB: Dumping buffer pool(s) to /var/lib/mysql/ib_buffer_pool
2017-03-09T07:16:02.047812Z 0 [Note] InnoDB: Buffer pool(s) dump completed at 170309 11:46:02
2017-03-09T07:17:03.359381Z 0 [Note] InnoDB: Waiting for page_cleaner to finish flushing of buffer pool
2017-03-09T07:18:03.594049Z 0 [Note] InnoDB: Waiting for page_cleaner to finish flushing of buffer pool
2017-03-09T07:19:03.828362Z 0 [Note] InnoDB: Waiting for page_cleaner to finish flushing of buffer pool
2017-03-09T07:20:04.064051Z 0 [Note] InnoDB: Waiting for page_cleaner to finish flushing of buffer pool
2017-03-09T07:21:04.299627Z 0 [Note] InnoDB: Waiting for page_cleaner to finish flushing of buffer pool
2017-03-09T07:22:04.537886Z 0 [Note] InnoDB: Waiting for page_cleaner to finish flushing of buffer pool
2017-03-09T07:23:04.776052Z 0 [Note] InnoDB: Waiting for page_cleaner to finish flushing of buffer pool
2017-03-09T07:24:05.013906Z 0 [Note] InnoDB: Waiting for page_cleaner to finish flushing of buffer pool
2017-03-09T07:25:05.251676Z 0 [Note] InnoDB: Waiting for page_cleaner to finish flushing of buffer pool
2017-03-09T07:28:55.152018Z 0 [Warning] Changed limits: max_open_files: 1024 (requested 5000)
2017-03-09T07:28:55.152229Z 0 [Warning] Changed limits: table_open_cache: 431 (requested 2000)
2017-03-09T07:28:55.561026Z 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).
2017-03-09T07:28:55.771260Z 0 [Note] /usr/sbin/mysqld (mysqld 5.7.17-0ubuntu0.16.10.1) starting as process 1444 ...
2017-03-09T07:28:56.702602Z 0 [Note] InnoDB: PUNCH HOLE support available
2017-03-09T07:28:56.702684Z 0 [Note] InnoDB: Mutexes and rw_locks use GCC atomic builtins
2017-03-09T07:28:56.702706Z 0 [Note] InnoDB: Uses event mutexes
2017-03-09T07:28:56.702729Z 0 [Note] InnoDB: GCC builtin __atomic_thread_fence() is used for memory barrier
2017-03-09T07:28:56.702747Z 0 [Note] InnoDB: Compressed tables use zlib 1.2.8
2017-03-09T07:28:56.702764Z 0 [Note] InnoDB: Using Linux native AIO
2017-03-09T07:28:56.724512Z 0 [Note] InnoDB: Number of pools: 1
2017-03-09T07:28:56.810177Z 0 [Note] InnoDB: Using CPU crc32 instructions
2017-03-09T07:28:56.826230Z 0 [Note] InnoDB: Initializing buffer pool, total size = 128M, instances = 1, chunk size = 128M
2017-03-09T07:28:56.942605Z 0 [Note] InnoDB: Completed initialization of buffer pool
2017-03-09T07:28:57.019407Z 0 [Note] InnoDB: If the mysqld execution user is authorized, page cleaner thread priority can be changed. See the man page of setpriority().
2017-03-09T07:28:58.022144Z 0 [Note] InnoDB: Highest supported file format is Barracuda.
2017-03-09T07:28:58.385216Z 0 [Note] InnoDB: Log scan progressed past the checkpoint lsn 4398541
2017-03-09T07:28:58.385293Z 0 [Note] InnoDB: Doing recovery: scanned up to log sequence number 4398550
2017-03-09T07:28:58.385935Z 0 [Note] InnoDB: Doing recovery: scanned up to log sequence number 4398550
2017-03-09T07:28:58.385961Z 0 [Note] InnoDB: Database was not shutdown normally!
2017-03-09T07:28:58.385980Z 0 [Note] InnoDB: Starting crash recovery.
2017-03-09T07:29:01.996450Z 0 [Note] InnoDB: Removed temporary tablespace data file: "ibtmp1"
2017-03-09T07:29:01.996544Z 0 [Note] InnoDB: Creating shared tablespace for temporary tables
2017-03-09T07:29:01.996778Z 0 [Note] InnoDB: Setting file './ibtmp1' size to 12 MB. Physically writing the file full; Please wait ...
2017-03-09T07:29:02.377522Z 0 [Note] InnoDB: File './ibtmp1' size is now 12 MB.
2017-03-09T07:29:02.381652Z 0 [Note] InnoDB: 96 redo rollback segment(s) found. 96 redo rollback segment(s) are active.
2017-03-09T07:29:02.381753Z 0 [Note] InnoDB: 32 non-redo rollback segment(s) are active.
2017-03-09T07:29:02.383476Z 0 [Note] InnoDB: Waiting for purge to start
2017-03-09T07:29:02.433833Z 0 [Note] InnoDB: page_cleaner: 1000ms intended loop took 5414ms. The settings might not be optimal. (flushed=0 and evicted=0, during the time.)
2017-03-09T07:29:02.433931Z 0 [Note] InnoDB: 5.7.17 started; log sequence number 4398550
2017-03-09T07:29:02.435179Z 0 [Note] InnoDB: Loading buffer pool(s) from /var/lib/mysql/ib_buffer_pool
2017-03-09T07:29:02.472782Z 0 [Note] Plugin 'FEDERATED' is disabled.
2017-03-09T07:29:02.875885Z 0 [Note] InnoDB: Buffer pool(s) load completed at 170309 11:59:02
2017-03-09T07:29:03.093417Z 0 [Warning] Failed to set up SSL because of the following SSL library error: SSL context is not usable without certificate and private key
2017-03-09T07:29:03.093503Z 0 [Note] Server hostname (bind-address): '127.0.0.1'; port: 3306
2017-03-09T07:29:03.093538Z 0 [Note]   - '127.0.0.1' resolves to '127.0.0.1';
2017-03-09T07:29:03.093634Z 0 [Note] Server socket created on IP: '127.0.0.1'.
2017-03-09T07:29:04.150683Z 0 [Note] Event Scheduler: Loaded 0 events
2017-03-09T07:29:04.151104Z 0 [Note] Executing 'SELECT * FROM INFORMATION_SCHEMA.TABLES;' to get a list of tables using the deprecated partition engine. You may use the startup option '--disable-partition-engine-check' to skip this check. 
2017-03-09T07:29:04.151150Z 0 [Note] Beginning of list of non-natively partitioned tables
2017-03-09T07:29:04.703557Z 0 [Note] End of list of non-natively partitioned tables
2017-03-09T07:29:04.703683Z 0 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.7.1
```

---

