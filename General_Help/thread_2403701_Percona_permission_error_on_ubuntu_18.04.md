---
title: "Percona permission error on ubuntu 18.04"
date: 2018-10-15
forum: General Help
---

### Post by vruler on 2018-10-15
Hi,

I'm having a permission issue on ubuntu 18 when changing datadir for percona.

I copied the permissions from /var/lib/mysql to /media/mavacorp/nvme1/mysql/ but I'm getting "Errcode: 13 - Permission denied". Tried chown and chmod(even 777) but still getting the permission error. Server is working fine if the datadir is set to the default /var/lib/mysql/ but I have a small ssd so I'm trying to move it to a different ssd(mounted at /media/mavacorp/nvme1/mysql/).

Any advice is welcomed, starting to pull my hair with this :(.

```
oct 15 13:16:53 mavacorp-System-Product-Name mysqld[43616]: mysqld: Can't change dir to '/media/mavacorp/nvme1/mysql/' (Errcode: 13 - Permission denied)oct 15 13:16:53 mavacorp-System-Product-Name mysqld[43616]: 2018-10-15T10:16:53.779288Z 0 [Warning] Changed limits: max_open_files: 1024 (requested 5000)
oct 15 13:16:53 mavacorp-System-Product-Name mysqld[43616]: 2018-10-15T10:16:53.779467Z 0 [Warning] Changed limits: table_open_cache: 431 (requested 2000)
oct 15 13:16:53 mavacorp-System-Product-Name mysqld[43616]: 2018-10-15T10:16:53.918279Z 0 [Warning] 'NO_ZERO_DATE', 'NO_ZERO_IN_DATE' and 'ERROR_FOR_DIVISION_BY_ZERO' sql mode
oct 15 13:16:53 mavacorp-System-Product-Name mysqld[43616]: 2018-10-15T10:16:53.918296Z 0 [Warning] 'NO_AUTO_CREATE_USER' sql mode was not set.
oct 15 13:16:53 mavacorp-System-Product-Name mysqld[43616]: 2018-10-15T10:16:53.918335Z 0 [Warning] Can't create test file /media/mavacorp/nvme1/mysql/mavacorp-System-Product-
oct 15 13:16:53 mavacorp-System-Product-Name mysqld[43616]: 2018-10-15T10:16:53.918350Z 0 [Note] /usr/sbin/mysqld (mysqld 5.7.23-23) starting as process 43618 ...
oct 15 13:16:53 mavacorp-System-Product-Name mysqld[43616]: 2018-10-15T10:16:53.919822Z 0 [Warning] Can't create test file /media/mavacorp/nvme1/mysql/mavacorp-System-Product-
oct 15 13:16:53 mavacorp-System-Product-Name mysqld[43616]: 2018-10-15T10:16:53.919830Z 0 [Warning] Can't create test file /media/mavacorp/nvme1/mysql/mavacorp-System-Product-
oct 15 13:16:53 mavacorp-System-Product-Name mysqld[43616]: 2018-10-15T10:16:53.920116Z 0 [ERROR] failed to set datadir to /media/mavacorp/nvme1/mysql/
oct 15 13:16:53 mavacorp-System-Product-Name mysqld[43616]: 2018-10-15T10:16:53.920123Z 0 [ERROR] Aborting
oct 15 13:16:53 mavacorp-System-Product-Name mysqld[43616]: 2018-10-15T10:16:53.920140Z 0 [Note] Binlog end
oct 15 13:16:53 mavacorp-System-Product-Name mysqld[43616]: 2018-10-15T10:16:53.920173Z 0 [Note] /usr/sbin/mysqld: Shutdown complete
oct 15 13:16:53 mavacorp-System-Product-Name mysqld[43616]: Initialization of mysqld failed: 0
oct 15 13:16:53 mavacorp-System-Product-Name systemd[1]: mysql.service: Control process exited, code=exited status=1
oct 15 13:16:53 mavacorp-System-Product-Name systemd[1]: mysql.service: Failed with result 'exit-code'.
oct 15 13:16:53 mavacorp-System-Product-Name systemd[1]: Failed to start Percona Server.

```

---

### Post by TheFu on 2018-10-15
What are the actual permissions for 

```
 mysqld: Can't change dir to '/media/mavacorp/nvme1/mysql/' (Errcode: 13 - Permission denied)
```

Show the output for** ls -al **from the directory up the chain. Please use code tags.  I suppose there is a single command that would know how to do that, but I'd just run these commands:
```
ls -al /media
ls -al /media/mavacorp
ls -al /media/mavacorp/nvme1
ls -al /media/mavacorp/nvme1/mysql

```
Permissions, ownership, groups, any ACLs are important.

---

### Post by vruler on 2018-10-15
@[COLOR=#000000]TheFu
[/COLOR]Here is the output for each command.

```

mavacorp@mavacorp-System-Product-Name:~$ ls -al /mediatotal 12
drwxr-xr-x   3 root root 4096 oct  9 23:27 .
drwxr-xr-x  24 root root 4096 oct 13 19:39 ..
drwxr-x---+  4 root root 4096 oct 13 20:10 mavacorp

```

```

mavacorp@mavacorp-System-Product-Name:~$ ls -al /media/mavacorp
total 16
drwxr-x---+ 4 root     root     4096 oct 13 20:10 .
drwxr-xr-x  3 root     root     4096 oct  9 23:27 ..
drwxrwxrwx  6 mysql    mysql    4096 oct 13 19:48 nvme1
drwx------  4 mavacorp mavacorp 4096 oct 13 17:37 nvme2

```

```

mavacorp@mavacorp-System-Product-Name:~$ ls -al /media/mavacorp/nvme1total 36
drwxrwxrwx  6 mysql mysql  4096 oct 13 19:48 .
drwxr-x---+ 4 root  root   4096 oct 13 20:10 ..
drwxrwxrwx  2 mysql mysql  4096 oct 13 17:37 asdad
drwxrwxrwx  2 mysql mysql 16384 oct 13 17:35 lost+found
drwxrwxrwx  6 mysql mysql  4096 oct 13 19:44 mysql
drwxrwxrwx  2 mysql mysql  4096 oct 13 17:50 tmp

```

```

mavacorp@mavacorp-System-Product-Name:~$ ls -al /media/mavacorp/nvme1/mysql
total 110664
drwxrwxrwx 6 mysql mysql     4096 oct 13 19:44 .
drwxrwxrwx 6 mysql mysql     4096 oct 13 19:48 ..
-rwxrwxrwx 1 mysql mysql       56 oct 13 19:36 auto.cnf
-rwxrwxrwx 1 mysql mysql     1680 oct 13 19:36 ca-key.pem
-rwxrwxrwx 1 mysql mysql     1120 oct 13 19:36 ca.pem
-rwxrwxrwx 1 mysql mysql     1120 oct 13 19:36 client-cert.pem
-rwxrwxrwx 1 mysql mysql     1672 oct 13 19:36 client-key.pem
drwxrwxrwx 2 mysql mysql     4096 oct 13 19:42 facem_untest
-rwxrwxrwx 1 mysql mysql      345 oct 13 19:44 ib_buffer_pool
-rwxrwxrwx 1 mysql mysql 12582912 oct 13 19:44 ibdata1
-rwxrwxrwx 1 mysql mysql 50331648 oct 13 19:44 ib_logfile0
-rwxrwxrwx 1 mysql mysql 50331648 oct 13 19:36 ib_logfile1
drwxrwxrwx 2 mysql mysql     4096 oct 13 19:36 mysql
drwxrwxrwx 2 mysql mysql     4096 oct 13 19:36 performance_schema
-rwxrwxrwx 1 mysql mysql     1680 oct 13 19:36 private_key.pem
-rwxrwxrwx 1 mysql mysql      452 oct 13 19:36 public_key.pem
-rwxrwxrwx 1 mysql mysql     1120 oct 13 19:36 server-cert.pem
-rwxrwxrwx 1 mysql mysql     1680 oct 13 19:36 server-key.pem
drwxrwxrwx 2 mysql mysql    12288 oct 13 19:36 sys

```

---

### Post by TheFu on 2018-10-15
Do you see the issue?
```
drwxr-x---+  4 root root 4096 oct 13 20:10 mavacorp
```
Only root has access to any files below that level.
```
sudo chmod o+rx /media/mavacorp
```
will fix it.  Also, using 777 should never happen. Bad habit. 755 or 775 would be the most permissive permissions used.

---

### Post by vruler on 2018-10-15
Thanks man, you are a lifesaver. I set 777 our of desperation, I'll change it to 755 and see what else I can do later for security, the issue was getting it to work first.

---

### Post by TheFu on 2018-10-15
It does appear that directory has some ACLs added. Take a look at those.  Oops. My mistake. It isn't ACLs, it is the +t permission.  Eh. leave it or not. doesn't matter, but if you didn't manually mount this storage and are using gvfs to control the mount, just know it will be slow.  It is best to avoid mounts under /media/ since those are handled is a poor performance way.  Use the fstab or autofs for mounting if you want the best performance.

If this is solved, please use the "thread tools" button near the top to mark it that way.  It helps the community.

---

### Post by vruler on 2018-10-15
It's mounted using fstab. Is it still an issue if it's mounted with fstab but in media? 
I'll set it as solved, thanks again.

---

### Post by TheFu on 2018-10-15
> **vruler said:**
> It's mounted using fstab. Is it still an issue if it's mounted with fstab but in media? 
I'll set it as solved, thanks again.

There are different opinions about using /media/ for manual mounts.  I fall on the "no way, no how" side.  I've seen programs make terrible mistakes because they assumed a directory area was only used 1 way.  Easy to avoid those issues - don't use /media/ for manual mounts.

---

