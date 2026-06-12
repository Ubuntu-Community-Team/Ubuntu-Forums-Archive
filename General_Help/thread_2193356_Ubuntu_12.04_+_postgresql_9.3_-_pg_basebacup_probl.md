---
title: "Ubuntu 12.04 + postgresql 9.3 - pg_basebacup problem"
date: 2013-12-12
forum: General Help
---

### Post by maciej.danielkiewi on 2013-12-12
First of all I want to say Hello everyone.

I'm trying to do postgres replication. I follow this tutorial [http://bartek.im/blog/2012/12/04/postgresql-92-streaming-primer.html#master-config](http://bartek.im/blog/2012/12/04/postgresql-92-streaming-primer.html#master-config), but when I do: ```
maciejdan@primary:~$ pg_basebackup -U postgres -D - -P -Ft | bzip2 > /var/tmp/pg_basebackup.tar.bz2
19708/19708 kB (100%), 1/1 tablespace
NOTICE:  pg_stop_backup cleanup done, waiting for required WAL segments to be archived
WARNING:  pg_stop_backup still waiting for all required WAL segments to be archived (60 seconds elapsed)
HINT:  Check that your archive_command is executing properly.  pg_stop_backup can be canceled safely, but the database backup will not be usable without all the WAL segments.
WARNING:  pg_stop_backup still waiting for all required WAL segments to be archived (120 seconds elapsed)
HINT:  Check that your archive_command is executing properly.  pg_stop_backup can be canceled safely, but the database backup will not be usable without all the WAL segments.
WARNING:  pg_stop_backup still waiting for all required WAL segments to be archived (240 seconds elapsed)
HINT:  Check that your archive_command is executing properly.  pg_stop_backup can be canceled safely, but the database backup will not be usable without all the WAL segments.
WARNING:  pg_stop_backup still waiting for all required WAL segments to be archived (480 seconds elapsed)
HINT:  Check that your archive_command is executing properly.  pg_stop_backup can be canceled safely, but the database backup will not be usable without all the WAL segments.
WARNING:  pg_stop_backup still waiting for all required WAL segments to be archived (960 seconds elapsed)
HINT:  Check that your archive_command is executing properly.  pg_stop_backup can be canceled safely, but the database backup will not be usable without all the WAL segments.
WARNING:  pg_stop_backup still waiting for all required WAL segments to be archived (1920 seconds elapsed)
HINT:  Check that your archive_command is executing properly.  pg_stop_backup can be canceled safely, but the database backup will not be usable without all the WAL segments. 
```

It's not going to stop if it's not finnish i can't  do netx step which is ```

scp /var/tmp/pg_basebackup.tar.bz2 postgres@pgslave.mysite.internal:/var/tmp/
```
because tar is broken ...

```
postgres  7055  0.0  0.0  96340  1628 ?        Ss   18:36   0:00 postgres: archiver process   failed on 000000010000000000000001
```

---

