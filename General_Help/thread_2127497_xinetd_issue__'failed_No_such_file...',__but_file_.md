---
title: "xinetd issue : 'failed: No such file...',  but file exists"
date: 2013-03-20
forum: General Help
---

### Post by ultimomiglio on 2013-03-20
Hi, i'm new to in the community and i hope to find help.

It is a xinetd issue : xinetd won't find a file that exists.

The storyboard :

```
ubuntu@ip-10-204-237-44:/etc/xinetd cat /etc/issue
Ubuntu 11.10 



```

```
ubuntu@ip-10-204-237-44:/etc/xinetd uname -r
3.0.0-23-virtual



```

```
ubuntu@ip-10-204-237-44:/etc/xinetd xinetd -version
xinetd Version 2.3.14 libwrap loadavg



```


```
ubuntu@ip-10-204-237-44:/etc/xinetd more /etc/xinetd.conf
# Simple configuration file for xinetd
#
# Some defaults, and include /etc/xinetd.d/


defaults
{


# Please note that you need a log_type line to be able to use log_on_success
# and log_on_failure. The default is the following :
# log_type = SYSLOG daemon info
instances = 60
log_type = SYSLOG authpriv
log_on_success = HOST PID
log_on_failure = HOST
cps = 25 30
}






includedir /etc/xinetd.d



```

```
ubuntu@ip-10-204-237-44:/etc/xinetd  ls -la
total 32
drwxr-xr-x  2 root root 4096 2013-03-19 15:04 .
drwxr-xr-x 85 root root 4096 2013-03-20 06:55 ..
-rw-r--r--  1 root root  798 2013-03-19 15:18 chargen
-rw-r--r--  1 root root  660 2010-12-06 21:32 daytime
-rw-r--r--  1 root root  549 2010-12-06 21:32 discard
-rw-r--r--  1 root root  580 2010-12-06 21:32 echo
-rw-r--r--  1 root root  299 2013-03-20 11:07 fastagi
-rw-r--r--  1 root root  727 2010-12-06 21:32 time



```

```
ubuntu@ip-10-204-237-44:/etc/xinetd. more fastagi
# default: off
# description: fastagi is a remote AGI interface


service fastagi
{
        socket_type = stream
        user = ubuntu
        group = ubuntu
        groups = yes
        server = /home/ubuntu/phpagi/phpagi-fastagi.php
        wait = no
        protocol = tcp
        disable = no
}



```

```
ubuntu@ip-10-204-237-44:/etc/xinetd ls -la /home/ubuntu/phpagi/
total 152
drwxrwxr-x 4 ubuntu ubuntu  4096 2013-03-19 16:30 .
drwxr-xr-x 8 ubuntu ubuntu  4096 2013-03-19 20:44 ..
drwxrwxr-x 6 ubuntu ubuntu  4096 2010-09-30 09:54 api-docs
-rw-rw-r-- 1 ubuntu ubuntu   541 2013-03-19 18:58 a_sample.php
-rw-rw-r-- 1 ubuntu ubuntu 24389 2010-09-30 09:54 COPYING
-rwxrwxrwx 1 ubuntu ubuntu     0 2013-03-19 16:30 data.txt
drwxrwxr-x 2 ubuntu ubuntu  4096 2010-09-30 09:54 docs
-rwxrwxr-x 1 ubuntu ubuntu   239 2010-09-30 09:54 mkdocs.php
-rw-rw-r-- 1 ubuntu ubuntu 25079 2010-09-30 09:54 phpagi-asmanager.php
-rwxrwxrwx 1 ubuntu ubuntu  2324 2013-03-20 10:15 phpagi-fastagi.php
-rw-rw-r-- 1 ubuntu ubuntu 67704 2013-03-19 20:50 phpagi.php
-rw-rw-r-- 1 ubuntu ubuntu  1641 2010-09-30 09:54 README



```

start xinetd :

```

ubuntu@ip-10-204-237-44:/etc/xinetd sudo xinetd -d
Service defaults
        Instances = 60
        CPS = max conn:25 wait:30
        Bind = All addresses.
        Only from: All sites
        No access: No blocked sites
        Logging to syslog. Facility = authpriv, level = info
        Log_on_success flags = HOST PID
        Log_on_failure flags = HOST


Service configuration: fastagi
        id = fastagi
        flags = IPv4
        socket_type = stream
        Protocol (name,number) = (tcp,6)
        port = 4573
        wait = no
        user = 1000
        group = 1000
        Groups = yes
        PER_SOURCE = -1
        Bind = All addresses.
        Server = /home/ubuntu/phpagi/phpagi-fastagi.php
        Server argv = phpagi-fastagi.php
        Only from: All sites
        No access: No blocked sites
        Logging to syslog. Facility = authpriv, level = info
        Log_on_success flags = HOST PID
        Log_on_failure flags = HOST


13/3/20@11:51:19: DEBUG: 12135 {cnf_start_********** Started service: fastagi
13/3/20@11:51:19: DEBUG: 12135 {cnf_start_********** mask_max = 6, services_started = 1
13/3/20@11:51:19: NOTICE: 12135 {main} xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
13/3/20@11:51:19: NOTICE: 12135 {main} Started working: 1 available service
13/3/20@11:51:19: DEBUG: 12135 {main_loop} active_services = 1



```

client request

```

13/3/20@11:52:07: DEBUG: 12135 {main_loop} select returned 1
13/3/20@11:52:07: DEBUG: 12135 {server_start} Starting service fastagi
13/3/20@11:52:07: DEBUG: 12135 {main_loop} active_services = 1
13/3/20@11:52:07: DEBUG: 12136 {exec_server} duping 7
13/3/20@11:52:07: ERROR: 12136 {exec_server} execv( /home/ubuntu/phpagi/phpagi-fastagi.php ) failed: No such file or directory (errno = 2)
13/3/20@11:52:07: DEBUG: 12135 {main_loop} active_services = 1
13/3/20@11:52:07: DEBUG: 12135 {main_loop} select returned 1
13/3/20@11:52:07: DEBUG: 12135 {check_pipe} Got signal 17 (Child exited)
13/3/20@11:52:07: DEBUG: 12135 {child_exit} waitpid returned = 12136
13/3/20@11:52:07: DEBUG: 12135 {server_end} fastagi server 12136 exited
13/3/20@11:52:07: INFO: 12135 {conn_free} freeing connection
13/3/20@11:52:07: DEBUG: 12135 {child_exit} waitpid returned = -1
13/3/20@11:52:07: DEBUG: 12135 {main_loop} active_services = 1



```

As you see xineted don't find a file that exists.

Any idea?

---

### Post by goodvibes on 2013-03-21
Does first line in /home/ubuntu/phpagi/phpagi-fastagi.php point to a php that does not exist?

---

