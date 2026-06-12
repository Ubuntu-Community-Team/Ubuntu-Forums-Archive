---
title: "mysql failed to start on m.2 SSD (Samsung XP941)"
date: 2015-05-11
forum: General Help
---

### Post by jorge8 on 2015-05-11
Help!  I've moved my local mysql database to a Samsung XP941 m.2 SSD drive, but doing this has caused mysql to stop working. When I enter the command "sudo service mysql start", I get a response saying that the operation failed.  The mysql error log says  "Can't start server : Bind on unix socket: Permission denied," even though I've set all the necessary permissions (chown -R mysql:mysql mysql, chmod -R 755 mysql).  I've also disabled and uninstalled apparmor, so I doubt that's the cause of the problem.

 I'm hoping someone out there can help!  Here's my setup:

SanDisk SSD for root directory "/"
Samsung XP941 m.2 SSD for my home directory ("/home")

I've created a folder for mysql in "/home/storage/mysql"
I've disabled and un-installed apparmor (I will re-install this once I get mysql running in the /home folder)

I tried starting mysql using the command: sudo service mysql start

The strange thing is that mysql starts fine if I move mysqld to any folder outside the m.2 drive.
- I've tried moving the mysql directory to "/mysql" and it works fine.
- I've also tested the home folder itself (in case it's a configuration  issue) by unmounting the m.2 drive, and copying the mysql directory to  /home/storage/mysql (from /var/lib/mysql_backup).  This works just fine  when /home/storage/mysql is on the sandisk drive!  But when I stop  mysql, re-mount the Samsung m.2 drive to /home, and re-copy the mysql  directory to /home/storage/mysql (from /var/lib/mysql_backup), mysql  goes back to not wanting to start up!

Does anyone have any ideas on what I should do to get the mysql database  running on the m.2 drive?  Am I missing any configurations?  Thanks in  advance for your help!

I've reconfigured my /etc/mysql/my.cnf file to as follows (removed comments for previty):
```

[client]
port            = 3306
socket          = /home/storage/mysql/mysqld.sock

[mysqld_safe]
/home/storage/mysql/mysqld.sock
nice            = 0

[mysqld]
user            = mysql
pid-file        = /home/storage/mysql/mysqld.pid
socket          = /home/storage/mysql/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /home/storage/mysql
tmpdir          = /tmp
lc-messages-dir = /usr/share/mysql
skip-external-locking

bind-address            = 127.0.0.1
key_buffer              = 16M
max_allowed_packet      = 16M
thread_stack            = 192K
thread_cache_size       = 8
myisam-recover         = BACKUP
query_cache_limit       = 1M
query_cache_size        = 16M
log_error = /var/log/mysql/error.log

[mysqldump]
quick
quote-names
max_allowed_packet      = 16M

[isamchk]
key_buffer              = 16M

!includedir /etc/mysql/conf.d/

```

Here's the log output when starting from /home/storage/mysql using the Sandisk SSD (only the Sandisk SSD is mounted, at "/")
```
150511 11:27:48 [Warning] Using unique option prefix myisam-recover instead of myisam-recover-options is deprecated and will be removed in a future release. Please use the full name instead.
150511 11:27:48 [Note] Plugin 'FEDERATED' is disabled.
150511 11:27:48 InnoDB: The InnoDB memory heap is disabled
150511 11:27:48 InnoDB: Mutexes and rw_locks use GCC atomic builtins
150511 11:27:48 InnoDB: Compressed tables use zlib 1.2.8
150511 11:27:48 InnoDB: Using Linux native AIO
150511 11:27:48 InnoDB: Initializing buffer pool, size = 128.0M
150511 11:27:48 InnoDB: Completed initialization of buffer pool
150511 11:27:48 InnoDB: highest supported file format is Barracuda.
150511 11:27:48  InnoDB: Waiting for the background threads to start
150511 11:27:49 InnoDB: 5.5.43 started; log sequence number 4717007614
150511 11:27:49 [Note] Server hostname (bind-address): '127.0.0.1'; port: 3306
150511 11:27:49 [Note]   - '127.0.0.1' resolves to '127.0.0.1';
150511 11:27:49 [Note] Server socket created on IP: '127.0.0.1'.
150511 11:27:49 [Note] Event Scheduler: Loaded 0 events
150511 11:27:49 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.5.43-0ubuntu0.14.10.1'  socket: '/home/storage/mysql/mysqld.sock'  port: 3306  (Ubuntu)
```

Here's the log output when starting from /home/storage/mysql using the Samsung m.2 SSD (mounted at "/home"):
```
150511 11:25:25 [Warning] Using unique option prefix myisam-recover instead of myisam-recover-options is deprecated and will be removed in a future release. Please use the full name instead.
150511 11:25:25 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Table 'plugin' is read only
150511 11:25:25 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
150511 11:25:25 InnoDB: The InnoDB memory heap is disabled
150511 11:25:25 InnoDB: Mutexes and rw_locks use GCC atomic builtins
150511 11:25:25 InnoDB: Compressed tables use zlib 1.2.8
150511 11:25:25 InnoDB: Using Linux native AIO
150511 11:25:25 InnoDB: Initializing buffer pool, size = 128.0M
150511 11:25:25 InnoDB: Completed initialization of buffer pool
150511 11:25:25 InnoDB: highest supported file format is Barracuda.
150511 11:25:25  InnoDB: Waiting for the background threads to start
150511 11:25:26 InnoDB: 5.5.43 started; log sequence number 4717007614
150511 11:25:26 [Note] Server hostname (bind-address): '127.0.0.1'; port: 3306
150511 11:25:26 [Note]   - '127.0.0.1' resolves to '127.0.0.1';
150511 11:25:26 [Note] Server socket created on IP: '127.0.0.1'.
150511 11:25:26 [ERROR] Can't start server : Bind on unix socket: Permission denied
150511 11:25:26 [ERROR] Do you already have another mysqld server running on socket: /home/storage/mysql/mysqld.sock ?
150511 11:25:26 [ERROR] Aborting

150511 11:25:26  InnoDB: Starting shutdown...
150511 11:25:27  InnoDB: Shutdown completed; log sequence number 4717007614
150511 11:25:27 [Note] /usr/sbin/mysqld: Shutdown complete
```


Here's my /etc/fstab configuration (edited to not include my hd UUIDs).  The Samsung m.2 SSD is /dev/sdb:
```
UUID=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=XXXX-XXXX  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX none            swap    sw              0       0

/dev/sdb        /home   ext4    defaults        0       2

```

Here's my apparmor configuration for /etc/apparmor.d/usr.sbin.mysqld (including this for completion, even though apparmor is currently not loaded or running):
```
# vim:syntax=apparmor
# Last Modified: Tue Jun 19 17:37:30 2007
#include <tunables/global>

/usr/sbin/mysqld {
  #include <abstractions/base>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>
  #include <abstractions/mysql>
  #include <abstractions/winbind>

  capability dac_override,
  capability sys_resource,
  capability setgid,
  capability setuid,

  network tcp,

  /etc/hosts.allow r,
  /etc/hosts.deny r,

  /etc/mysql/*.pem r,
  /etc/mysql/conf.d/ r,
  /etc/mysql/conf.d/* r,
  /etc/mysql/*.cnf r,
  /usr/lib/mysql/plugin/ r,
  /usr/lib/mysql/plugin/*.so* mr,
  /usr/sbin/mysqld mr,
  /usr/share/mysql/** r,
  /var/log/mysql.log rw,
  /var/log/mysql.err rw,
  /var/lib/mysql/ r,
  /var/lib/mysql/** rwk,
  /home/storage/mysql/ rwk,
  /home/storage/mysql/** rwk,
  /var/log/mysql/ r,
  /var/log/mysql/* rw,
  /{,var/}run/mysqld/mysqld.pid rw,
  /{,var/}run/mysqld/mysqld.sock w,
  /run/mysqld/mysqld.pid rw,
  /run/mysqld/mysqld.sock w,

  /sys/devices/system/cpu/ r,

  # Site-specific additions and overrides. See local/README for details.
  #include <local/usr.sbin.mysqld>
}
```

---

### Post by SeijiSensei on 2015-05-12
By default, MySQL expects to find its databases in /var/lib/mysql.  If you want to move that elsewhere, copy the files to the other location and use a symbolic link:
```

sudo service mysql stop
sudo rsync -av /var/lib/mysql /path/to/some/directory
cd /var/lib
sudo mv mysql mysql.bak
ln -s /path/to/some/directory/mysql .
sudo service mysql start

```

That new directory must be owned by user mysql and group mysql.  
```
ls -l /var/lib | grep mysql
drwxr-xr-x 4 mysql         mysql         4096 May  7 11:50 mysql

```

---

### Post by jorge8 on 2015-05-12
SeijiSensei, thanks for your reply.  In the process of making the symlink I realized that my /home directory had permissions 700!  I've changed the permissions to 755 and all works fine now. :)

I'm not sure, but I think the OS must be mounting my m.2 SSD with the 700 permissions, because unmounting the drive exposes the original /home folder with the original permissions.  I'll have to look deeper into this... but at least I got it working now!

---

