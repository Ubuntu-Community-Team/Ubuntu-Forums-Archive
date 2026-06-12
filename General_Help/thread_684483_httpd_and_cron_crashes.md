---
title: "httpd and cron crashes"
date: 2008-02-01
forum: General Help
---

### Post by maratonic on 2008-02-01
Hello distinguished gurus of the Ubuntu world, I would be immensely glad if anyone could help me...

My problem is that httpd crashes once or twice every day. As a "band aid" I set up a cron job to check every minute wether apache is running and if not, start it again. This script works, only now I discovered that cron crashes too and my script doesn't get run... The actual problem is probably  memory related but I'm  a newbie and don't know how to proceed to find out the root cause of the crashes. The server has 256 MB RAM and generally uses 200-220 according to free. At some of the crashes the [COLOR="Green"]apache error.log[/COLOR] says:

[COLOR="Green"]FATAL:  emalloc():  Unable to allocate 394104 bytes
FATAL:  emalloc():  Unable to allocate 12 bytes
[Fri Feb 01 02:49:13 2008] [notice] caught SIGTERM, shutting down[/COLOR]



In syslog I can see at what times cron stops because there are no more lines like this for a while:

Jan 28 08:54:01 rentmjol /USR/SBIN/CRON[26593]: (root) CMD (/root/watchdog.sh)

I see no pattern in the timing of cron deaths. 


I've tried logging free and ps to a [COLOR="Navy"]log file[/COLOR] at 10 minute intervals but I can't make out what might be wrong there. Here are two of the entries just before crashes, the first one corresponds to the above emalloc() error.

[COLOR="Navy"]Fri Feb  1 02:40:01 CET 2008
 02:40:01 up 6 days, 17:41,  1 user,  load average: 0.28, 0.26, 0.25
             total       used       free     shared    buffers     cached
Mem:           256        219         36          0          0          0
-/+ buffers/cache:        219         36
Swap:            0          0          0
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  1      0  37080      0      0    0    0     0     0    0   17  2  0 97  1
 0  1      0  36992      0      0    0    0     0     0    0 3274  0  0 68 31
 0  1      0  36952      0      0    0    0     0     0    0 3160  0  0 80 20
 0  1      0  36876      0      0    0    0     0     0    0 3172  0  0 78 22
 0  0      0  36592      0      0    0    0     0     0    0 3199  0  0 84 16
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.2   1848   664 ?        Ss   Jan25   0:01 init [2]
root      5683  0.0  0.2   1544   592 ?        Ds   Jan25   0:03 /sbin/syslogd
mysql     5833  0.7 16.5 149296 43296 ?        Sl   Jan25  70:45 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --us
er=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-locking --port=3306
root      6124  0.0  0.3   4824   952 ?        Ss   Jan25   0:02 /usr/sbin/sshd
root     13482  0.0  0.9   7772  2424 ?        Ss   Jan30   0:02  \_ sshd: root@pts/0
root     13504  0.0  0.6   2724  1696 pts/0    Ss+  Jan30   0:00      \_ -bash
root      7183  0.0  0.3   2168   812 ?        Ss   Jan25   0:00 /usr/sbin/xinetd -pidfile /var/run/xinetd.pid -stayalive
root      9461  0.0  3.9  27044 10340 ?        Ss   Jan31   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  9467  1.5 14.5  57180 38208 ?        S    Jan31   3:06  \_ /usr/sbin/apache2 -k start -DSSL
www-data  9513  1.5 14.5  57260 38204 ?        S    Jan31   3:11  \_ /usr/sbin/apache2 -k start -DSSL
www-data  9590  1.5 14.5  57036 38012 ?        S    Jan31   3:02  \_ /usr/sbin/apache2 -k start -DSSL
www-data 23938  1.3 14.5  57284 38176 ?        S    Jan31   2:16  \_ /usr/sbin/apache2 -k start -DSSL
www-data 29999  1.3 14.2  56424 37420 ?        S    00:04   2:06  \_ /usr/sbin/apache2 -k start -DSSL
root     11279  0.0  0.3   2092   868 ?        Ss   Jan31   0:00 /usr/sbin/cron
root     29933  0.0  0.3   2440   916 ?        S    02:40   0:00  \_ /USR/SBIN/CRON
111      29948  0.1  1.0  11224  2844 ?        D    02:40   0:00  |   \_ /usr/sbin/sendmail -i -FCronDaemon -oem root
root     29935  0.0  0.3   2440   916 ?        S    02:40   0:00  \_ /USR/SBIN/CRON
111      30232  1.0  1.0  11216  2844 ?        D    02:40   0:00  |   \_ /usr/sbin/sendmail -i -FCronDaemon -oem root
root     29937  0.0  0.3   2440   908 ?        S    02:40   0:00  \_ /USR/SBIN/CRON
root     29939  0.0  0.1   1544   468 ?        Ss   02:40   0:00  |   \_ /bin/sh -c /root/memmon.sh >> /root/memmon.txt
root     29952  0.0  0.4   2324  1056 ?        S    02:40   0:00  |       \_ /bin/bash /root/memmon.sh
root     30244  0.0  0.3   2124   856 ?        R    02:40   0:00  |           \_ ps auxf --width=200
root     29940  0.0  0.3   2440   916 ?        S    02:40   0:00  \_ /USR/SBIN/CRON
111      29951  0.1  1.0  11220  2852 ?        D    02:40   0:00      \_ /usr/sbin/sendmail -i -FCronDaemon -oem root
[/COLOR]


--------------------
The second one doesn't have a corresponding memory allocation problem in the apache error log:

[COLOR="Navy"]Wed Jan 30 12:50:01 CET 2008
 12:50:01 up 5 days,  3:51,  0 users,  load average: 0.79, 0.40, 0.25
             total       used       free     shared    buffers     cached
Mem:           256        211         44          0          0          0
-/+ buffers/cache:        211         44
Swap:            0          0          0
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  1      0  46064      0      0    0    0     0     0    0   12  2  0 97  1
 1  0      0  45824      0      0    0    0     0     0    0 2976 24  1 75  0
 0  0      0  46736      0      0    0    0     0     0    0 8812 16  1 82  0
 0  0      0  46780      0      0    0    0     0     0    0 1633  2  0 98  0
 0  0      0  46708      0      0    0    0     0     0    0 1683  0  0 100  0
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.2   1848   664 ?        Ss   Jan25   0:01 init [2]
root      5683  0.0  0.2   1544   592 ?        Ss   Jan25   0:02 /sbin/syslogd
mysql     5833  0.7 16.5 148964 43340 ?        Sl   Jan25  57:06 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --us
er=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-locking --port=3306
root      6124  0.0  0.3   4824   976 ?        Ss   Jan25   0:01 /usr/sbin/sshd
root      7183  0.0  0.3   2168   828 ?        Ss   Jan25   0:00 /usr/sbin/xinetd -pidfile /var/run/xinetd.pid -stayalive
root      5313  0.0  0.3   2092   868 ?        Ss   Jan29   0:00 /usr/sbin/cron
root     24413  0.0  0.3   2440   908 ?        S    12:50   0:00  \_ /USR/SBIN/CRON
root     24415  0.0  0.1   1544   468 ?        Ss   12:50   0:00      \_ /bin/sh -c /root/memmon.sh >> /root/memmon.txt
root     24420  0.0  0.4   2324  1056 ?        S    12:50   0:00          \_ /bin/bash /root/memmon.sh
root     24530  0.0  0.3   2124   852 ?        R    12:50   0:00              \_ ps auxf --width=200
root     30638  0.0  3.9  27044 10340 ?        Ss   00:22   0:00 /usr/sbin/apache2 -k start -DSSL
www-data 13487  5.3 14.4  57020 37984 ?        S    12:24   1:21  \_ /usr/sbin/apache2 -k start -DSSL
www-data 21711  3.5 14.4  56848 37896 ?        S    12:41   0:18  \_ /usr/sbin/apache2 -k start -DSSL
www-data 21721  2.8 14.3  56784 37636 ?        S    12:41   0:15  \_ /usr/sbin/apache2 -k start -DSSL
www-data 21729  4.7 14.4  56976 37904 ?        S    12:41   0:24  \_ /usr/sbin/apache2 -k start -DSSL
www-data 24282 11.6 13.9  57020 36476 ?        S    12:49   0:04  \_ /usr/sbin/apache2 -k start -DSSL
root     24469  0.3  1.1  11212  3116 ?        Ss   12:50   0:00 /usr/sbin/exim4 -Mc 1JKBS5-0006Lw-9u
mail     24471  0.0  0.5  11212  1540 ?        D    12:50   0:00  \_ /usr/sbin/exim4 -Mc 1JKBS5-0006Lw-9u
[/COLOR]


After this problem began I've tried added the following line to [COLOR="DarkRed"]apache2.conf[/COLOR]:
<IfModule worker.c>
[COLOR="DarkRed"]ThreadStackSize 1000000  # said to improve apache memory efficiency[/COLOR]

---

### Post by maratonic on 2008-02-01
Ok, trying again with PRE tag to hopefully get better formatting...


[FONT="Courier New"][HTML]<pre>
the first one corresponds to the above emalloc() error


Fri Feb  1 02:40:01 CET 2008
 02:40:01 up 6 days, 17:41,  1 user,  load average: 0.28, 0.26, 0.25
             total       used       free     shared    buffers     cached
Mem:           256        219         36          0          0          0
-/+ buffers/cache:        219         36
Swap:            0          0          0
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  1      0  37080      0      0    0    0     0     0    0   17  2  0 97  1
 0  1      0  36992      0      0    0    0     0     0    0 3274  0  0 68 31
 0  1      0  36952      0      0    0    0     0     0    0 3160  0  0 80 20
 0  1      0  36876      0      0    0    0     0     0    0 3172  0  0 78 22
 0  0      0  36592      0      0    0    0     0     0    0 3199  0  0 84 16
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.2   1848   664 ?        Ss   Jan25   0:01 init [2]
root      5683  0.0  0.2   1544   592 ?        Ds   Jan25   0:03 /sbin/syslogd
mysql     5833  0.7 16.5 149296 43296 ?        Sl   Jan25  70:45 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --us
er=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-locking --port=3306
root      6124  0.0  0.3   4824   952 ?        Ss   Jan25   0:02 /usr/sbin/sshd
root     13482  0.0  0.9   7772  2424 ?        Ss   Jan30   0:02  \_ sshd: root@pts/0
root     13504  0.0  0.6   2724  1696 pts/0    Ss+  Jan30   0:00      \_ -bash
root      7183  0.0  0.3   2168   812 ?        Ss   Jan25   0:00 /usr/sbin/xinetd -pidfile /var/run/xinetd.pid -stayalive
root      9461  0.0  3.9  27044 10340 ?        Ss   Jan31   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  9467  1.5 14.5  57180 38208 ?        S    Jan31   3:06  \_ /usr/sbin/apache2 -k start -DSSL
www-data  9513  1.5 14.5  57260 38204 ?        S    Jan31   3:11  \_ /usr/sbin/apache2 -k start -DSSL
www-data  9590  1.5 14.5  57036 38012 ?        S    Jan31   3:02  \_ /usr/sbin/apache2 -k start -DSSL
www-data 23938  1.3 14.5  57284 38176 ?        S    Jan31   2:16  \_ /usr/sbin/apache2 -k start -DSSL
www-data 29999  1.3 14.2  56424 37420 ?        S    00:04   2:06  \_ /usr/sbin/apache2 -k start -DSSL
root     11279  0.0  0.3   2092   868 ?        Ss   Jan31   0:00 /usr/sbin/cron
root     29933  0.0  0.3   2440   916 ?        S    02:40   0:00  \_ /USR/SBIN/CRON
111      29948  0.1  1.0  11224  2844 ?        D    02:40   0:00  |   \_ /usr/sbin/sendmail -i -FCronDaemon -oem root
root     29935  0.0  0.3   2440   916 ?        S    02:40   0:00  \_ /USR/SBIN/CRON
111      30232  1.0  1.0  11216  2844 ?        D    02:40   0:00  |   \_ /usr/sbin/sendmail -i -FCronDaemon -oem root
root     29937  0.0  0.3   2440   908 ?        S    02:40   0:00  \_ /USR/SBIN/CRON
root     29939  0.0  0.1   1544   468 ?        Ss   02:40   0:00  |   \_ /bin/sh -c /root/memmon.sh >> /root/memmon.txt
root     29952  0.0  0.4   2324  1056 ?        S    02:40   0:00  |       \_ /bin/bash /root/memmon.sh
root     30244  0.0  0.3   2124   856 ?        R    02:40   0:00  |           \_ ps auxf --width=200
root     29940  0.0  0.3   2440   916 ?        S    02:40   0:00  \_ /USR/SBIN/CRON
111      29951  0.1  1.0  11220  2852 ?        D    02:40   0:00      \_ /usr/sbin/sendmail -i -FCronDaemon -oem root





--------------------
The second one doesn't have a corresponding memory allocation problem in the apache error log:






Wed Jan 30 12:50:01 CET 2008
 12:50:01 up 5 days,  3:51,  0 users,  load average: 0.79, 0.40, 0.25
             total       used       free     shared    buffers     cached
Mem:           256        211         44          0          0          0
-/+ buffers/cache:        211         44
Swap:            0          0          0
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  1      0  46064      0      0    0    0     0     0    0   12  2  0 97  1
 1  0      0  45824      0      0    0    0     0     0    0 2976 24  1 75  0
 0  0      0  46736      0      0    0    0     0     0    0 8812 16  1 82  0
 0  0      0  46780      0      0    0    0     0     0    0 1633  2  0 98  0
 0  0      0  46708      0      0    0    0     0     0    0 1683  0  0 100  0
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.2   1848   664 ?        Ss   Jan25   0:01 init [2]
root      5683  0.0  0.2   1544   592 ?        Ss   Jan25   0:02 /sbin/syslogd
mysql     5833  0.7 16.5 148964 43340 ?        Sl   Jan25  57:06 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --us
er=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-locking --port=3306
root      6124  0.0  0.3   4824   976 ?        Ss   Jan25   0:01 /usr/sbin/sshd
root      7183  0.0  0.3   2168   828 ?        Ss   Jan25   0:00 /usr/sbin/xinetd -pidfile /var/run/xinetd.pid -stayalive
root      5313  0.0  0.3   2092   868 ?        Ss   Jan29   0:00 /usr/sbin/cron
root     24413  0.0  0.3   2440   908 ?        S    12:50   0:00  \_ /USR/SBIN/CRON
root     24415  0.0  0.1   1544   468 ?        Ss   12:50   0:00      \_ /bin/sh -c /root/memmon.sh >> /root/memmon.txt
root     24420  0.0  0.4   2324  1056 ?        S    12:50   0:00          \_ /bin/bash /root/memmon.sh
root     24530  0.0  0.3   2124   852 ?        R    12:50   0:00              \_ ps auxf --width=200
root     30638  0.0  3.9  27044 10340 ?        Ss   00:22   0:00 /usr/sbin/apache2 -k start -DSSL
www-data 13487  5.3 14.4  57020 37984 ?        S    12:24   1:21  \_ /usr/sbin/apache2 -k start -DSSL
www-data 21711  3.5 14.4  56848 37896 ?        S    12:41   0:18  \_ /usr/sbin/apache2 -k start -DSSL
www-data 21721  2.8 14.3  56784 37636 ?        S    12:41   0:15  \_ /usr/sbin/apache2 -k start -DSSL
www-data 21729  4.7 14.4  56976 37904 ?        S    12:41   0:24  \_ /usr/sbin/apache2 -k start -DSSL
www-data 24282 11.6 13.9  57020 36476 ?        S    12:49   0:04  \_ /usr/sbin/apache2 -k start -DSSL
root     24469  0.3  1.1  11212  3116 ?        Ss   12:50   0:00 /usr/sbin/exim4 -Mc 1JKBS5-0006Lw-9u
mail     24471  0.0  0.5  11212  1540 ?        D    12:50   0:00  \_ /usr/sbin/exim4 -Mc 1JKBS5-0006Lw-9u

</pre>

[/HTML][/FONT]

---

### Post by maratonic on 2008-02-05
Now it seems I found another clue in this puzzle: I've been logged on to the server remotely via putty (an SSH terminal) since thursday and apparently cron and httpd have managed to stay more or less alive since then. They HAVE crashed though, while a colleague has been working with the server, so the problem persists. 

Maybe I should mention that it's a Drupal multi-site installation we're running and it may be that the original config (apache2.config) isn't optimal for that when you have only 256 MB of RAM. Any suggestions for improving performance?

---

