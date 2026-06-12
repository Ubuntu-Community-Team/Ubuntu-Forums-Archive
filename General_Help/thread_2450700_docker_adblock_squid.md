---
title: "docker adblock squid"
date: 2020-09-18
forum: General Help
---

### Post by walk3rwhite on 2020-09-18
Hy. I want to run squid-adblock server on my Ubuntu 20.04.1 LTS machine. ([https://github.com/andrassebo/squid-adblock)]("https://github.com/andrassebo/squid-adblock")
My Ubuntu runs on a proxmox server and docker is installed: 
root@ubu:~# docker --version
Docker version 19.03.13, build 4484c46d9d

I have no clue how this can be done with docker.
according to readme i simply run ./start-squid.sh.

Don't work:
root@ubu:/opt/squid/scripts# ./start-squid.sh
touch: cannot touch '/var/log/squid/access.log': No such file or directory
chown: cannot access '/var/cache/squid': No such file or directory
chown: cannot access '/var/log/squid': No such file or directory
chmod: cannot access '/etc/periodic/daily/access-log-rotate': No such file or directory
./start-squid.sh: line 8: crond: command not found
./start-squid.sh: line 10: /usr/sbin/squid: No such file or directory
./start-squid.sh: line 11: /usr/sbin/squid: No such file or directory

Squid needs to be installed before i think but then it calls:

./start-squid.sh: line 8: crond: command not found
WARNING: Cannot write log file: /var/log/squid/cache.log
/var/log/squid/cache.log: Permission denied
         messages will be sent to 'stderr'.
2020/09/19 00:12:32| Created PID file (/var/run/squid.pid)
WARNING: Cannot write log file: /var/log/squid/cache.log
/var/log/squid/cache.log: Permission denied
         messages will be sent to 'stderr'.
2020/09/19 00:12:32 kid1| Set Current Directory to /var/spool/squid
2020/09/19 00:12:32 kid1| Creating missing swap directories
2020/09/19 00:12:32 kid1| No cache_dir stores are configured.
2020/09/19 00:12:32| Removing PID file (/var/run/squid.pid)
WARNING: Cannot write log file: /var/log/squid/cache.log
/var/log/squid/cache.log: Permission denied
         messages will be sent to 'stderr'.

no cache initialised, 
then i initialise it over webmin and then this shows up when i execute start:

root@ubu:/opt/squid/scripts# ./start-squid.sh
chown: cannot access '/var/cache/squid': No such file or directory
chmod: cannot access '/etc/periodic/daily/access-log-rotate': No such file or directory
./start-squid.sh: line 8: crond: command not found
2020/09/19 00:15:45| Created PID file (/var/run/squid.pid)
2020/09/19 00:15:45 kid1| Set Current Directory to /var/spool/squid
2020/09/19 00:15:45 kid1| Creating missing swap directories
2020/09/19 00:15:45 kid1| /var/spool/squid exists
2020/09/19 00:15:45 kid1| /var/spool/squid/00 exists
2020/09/19 00:15:45 kid1| Making directories in /var/spool/squid/00
2020/09/19 00:15:45 kid1| /var/spool/squid/01 exists
2020/09/19 00:15:45 kid1| Making directories in /var/spool/squid/01
2020/09/19 00:15:45 kid1| /var/spool/squid/02 exists
2020/09/19 00:15:45 kid1| Making directories in /var/spool/squid/02
2020/09/19 00:15:45 kid1| /var/spool/squid/03 exists
2020/09/19 00:15:45 kid1| Making directories in /var/spool/squid/03
2020/09/19 00:15:45 kid1| /var/spool/squid/04 exists
2020/09/19 00:15:45 kid1| Making directories in /var/spool/squid/04
root@ubu:/opt/squid/scripts# 2020/09/19 00:15:45 kid1| /var/spool/squid/05 exists
2020/09/19 00:15:45 kid1| Making directories in /var/spool/squid/05
2020/09/19 00:15:45 kid1| /var/spool/squid/06 exists
2020/09/19 00:15:45 kid1| Making directories in /var/spool/squid/06
2020/09/19 00:15:45 kid1| /var/spool/squid/07 exists
2020/09/19 00:15:45 kid1| Making directories in /var/spool/squid/07
2020/09/19 00:15:45 kid1| /var/spool/squid/08 exists
2020/09/19 00:15:45 kid1| Making directories in /var/spool/squid/08
2020/09/19 00:15:45 kid1| /var/spool/squid/09 exists
2020/09/19 00:15:45 kid1| Making directories in /var/spool/squid/09
2020/09/19 00:15:45 kid1| /var/spool/squid/0A exists
2020/09/19 00:15:45 kid1| Making directories in /var/spool/squid/0A
2020/09/19 00:15:45 kid1| /var/spool/squid/0B exists
2020/09/19 00:15:45 kid1| Making directories in /var/spool/squid/0B
2020/09/19 00:15:45 kid1| /var/spool/squid/0C exists
2020/09/19 00:15:45 kid1| Making directories in /var/spool/squid/0C
2020/09/19 00:15:45 kid1| /var/spool/squid/0D exists
2020/09/19 00:15:45 kid1| Making directories in /var/spool/squid/0D
2020/09/19 00:15:45 kid1| /var/spool/squid/0E exists
2020/09/19 00:15:45 kid1| Making directories in /var/spool/squid/0E
2020/09/19 00:15:45 kid1| /var/spool/squid/0F exists
2020/09/19 00:15:45 kid1| Making directories in /var/spool/squid/0F
2020/09/19 00:15:45| Removing PID file (/var/run/squid.pid)

That's it.
Can someone tell me how this code can be executed correctly?

---

