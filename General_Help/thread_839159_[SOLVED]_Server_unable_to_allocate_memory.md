---
title: "[SOLVED] Server unable to allocate memory"
date: 2008-06-24
forum: General Help
---

### Post by apakatt on 2008-06-24
I have bought a VPS from a local provider which runs Ubuntu 6.06 LTS.
It has been running for like 100 days and there hasn't been any problems with it until just recently.

I noticed last Thursday that I was unable to log in to it via SSH. It stated something like "Unable to allocate enough memory to create fork" (sorry I can't give the exact error msg but I'm at work atm). Later that day I was able to sign in but as soon as I need to do something requiring memory it fails (like apt-get etc).

So I rebooted the server and everything was fine again but the same problem occurred later the same day. 

I don't see any strange things when I run top or ps -aux. There seems to be a lot of free memory which really bothers me. No crazy process running wild. No new software was installed (maybe a automatic update). The only thing I added to the server is Wordpress which sounds really wierd if it was the source of the problem.

The server is running Apache 2 and MySQL 5 and all the web-stuff works just fine. I have a couple of sites with some traffic and this problem doesn't seem to affect them.

Any suggestions?

---

### Post by rubicon on 2008-06-24
> **apakatt said:**
> I noticed last Thursday that I was unable to log in to it via SSH. It stated something like "Unable to allocate enough memory to create fork" (sorry I can't give the exact error msg but I'm at work atm). Later that day I was able to sign in but as soon as I need to do something requiring memory it fails (like apt-get etc).Both error messages would be quite useful to see.

> **apakatt said:**
> I don't see any strange things when I run top or ps -aux. There seems to be a lot of free memory which really bothers me. No crazy process running wild.Mind posting `ps aux` here? :)

> I have a couple of sites with some traffic and this problem doesn't seem to affect them.Is it certain?

---

### Post by apakatt on 2008-06-24
> **rubicon said:**
> Both error messages would be quite useful to see.

I'll give it to you when I get home.

> **rubicon said:**
> Mind posting `ps aux` here? :)
My VPS provider has the functionality to lend 1 GB of RAM for 1h. I'm able to log in to SSH and everything else when I do it. This is what it looks like:

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   1572   532 ?        Ss   Jun18   0:00 init [2]
root      1783  0.0  0.0   1692   492 ?        Ss   Jun18   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      1785  0.0  0.0   1572   392 ?        Ss   Jun18   0:00 /sbin/klogd -P /var/run/klogd/kmsg
root      1824  0.0  0.0   2640  1312 ?        S    Jun18   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     1904  0.2  1.5 145532 40604 ?        Sl   Jun18  21:35 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mys
root      1906  0.0  0.0   1552   496 ?        S    Jun18   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root      3154  0.0  0.0   4668  1608 ?        Ss   Jun18   0:00 /usr/lib/postfix/master
postfix   3163  0.0  0.0   4712  1648 ?        S    Jun18   0:00 qmgr -l -t fifo -u
nobody    3232  0.0  0.0   4636  1308 ?        Ss   Jun18   0:00 proftpd: (accepting connections)
root      3254  0.0  0.0   2120   840 ?        Ss   Jun18   0:00 /usr/sbin/cron
root      3312  0.0  0.1   7496  4316 ?        S    Jun18   0:17 /usr/bin/python /usr/bin/denyhosts.py --daemon -c /usr/share/denyhosts/denyhosts.cfg
root      3727  0.0  0.0   4772  1084 ?        Ss   Jun18   0:00 /usr/sbin/sshd
www-data  3951  0.0  0.6  29484 17496 ?        S    Jun19   0:45 /usr/sbin/apache2 -k start -DSSL
root      3953  0.0  0.2  19912  6112 ?        Ss   Jun18   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  3955  0.0  0.6  30884 18140 ?        S    Jun18   0:57 /usr/sbin/apache2 -k start -DSSL
www-data  5808  0.0  0.6  31424 18284 ?        S    Jun23   0:09 /usr/sbin/apache2 -k start -DSSL
syslog    7702  0.0  0.0   1768   708 ?        Ss   06:25   0:00 /sbin/syslogd -u syslog
postfix  11320  0.0  0.0   4728  1912 ?        S    Jun19   0:00 tlsmgr -l -t unix -u -c
www-data 13487  0.0  0.6  29324 16956 ?        S    Jun23   0:08 /usr/sbin/apache2 -k start -DSSL
postfix  16159  0.0  0.0   4680  1516 ?        S    14:49   0:00 pickup -l -t fifo -u -c
root     19819  0.0  0.0   7528  2360 ?        Ss   14:50   0:00 sshd: anton [priv]
anton    19877  0.0  0.0   7528  1528 ?        S    14:50   0:00 sshd: anton@pts/0
anton    19878  0.0  0.0   3252  1804 pts/0    Ss   14:50   0:00 -bash
www-data 19968  0.0  0.3  21048  8276 ?        S    13:58   0:00 /usr/sbin/apache2 -k start -DSSL
anton    20451  0.0  0.0   2196   872 pts/0    R+   14:51   0:00 ps aux
www-data 30168  0.0  0.6  29440 17308 ?        S    Jun23   0:12 /usr/sbin/apache2 -k start -DSSL
www-data 30369  0.0  0.6  29364 17004 ?        S    Jun23   0:11 /usr/sbin/apache2 -k start -DSSL
www-data 31795  0.0  0.6  29224 16640 ?        S    Jun23   0:05 /usr/sbin/apache2 -k start -DSSL
``````
top - 14:53:51 up 5 days, 22:05,  1 user,  load average: 0.01, 0.03, 0.00
Tasks:  28 total,   2 running,  26 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0% us,  0.0% sy,  0.0% ni, 100.0% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   2621440k total,   264696k used,  2356744k free,        0k buffers
Swap:        0k total,        0k used,        0k free,        0k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
24247 anton     15   0  2200 1080  856 R  0.3  0.0   0:00.01 top
    1 root      18   0  1572  532  460 S  0.0  0.0   0:00.29 init
 1783 root      25   0  1692  492  412 S  0.0  0.0   0:00.00 dd
 1785 klog      18   0  1572  392  320 S  0.0  0.0   0:00.00 klogd
 1824 root      25   0  2640 1312 1064 S  0.0  0.1   0:00.01 mysqld_safe
 1904 mysql     15   0  142m  39m 5280 S  0.0  1.5  21:35.03 mysqld
 1906 root      25   0  1552  496  432 S  0.0  0.0   0:00.00 logger
 3154 root      25   0  4668 1608 1312 S  0.0  0.1   0:00.38 master
 3163 postfix   15   0  4712 1648 1336 S  0.0  0.1   0:00.13 qmgr
 3232 nobody    18   0  4636 1308  692 S  0.0  0.0   0:00.04 proftpd
 3254 root      18   0  2120  840  684 S  0.0  0.0   0:00.10 cron
 3312 root      18   0  7496 4316 1484 S  0.0  0.2   0:17.74 denyhosts.py
 3727 root      15   0  4772 1084  788 S  0.0  0.0   0:00.05 sshd
 3951 www-data  15   0 29484  17m 5320 S  0.0  0.7   0:45.12 apache2
 3953 root      18   0 19912 6112 3620 S  0.0  0.2   0:00.70 apache2
 3955 www-data  15   0 30884  17m 5452 S  0.0  0.7   0:57.06 apache2
 5808 www-data  15   0 31424  17m 5192 S  0.0  0.7   0:09.42 apache2
 7702 syslog    18   0  1768  708  584 S  0.0  0.0   0:00.01 syslogd
11320 postfix   18   0  4728 1912 1584 S  0.0  0.1   0:00.01 tlsmgr
13487 www-data  16   0 29324  16m 4952 S  0.0  0.6   0:08.79 apache2
16159 postfix   18   0  4680 1516 1236 S  0.0  0.1   0:00.00 pickup
19819 root      16   0  7528 2360 1960 S  0.0  0.1   0:00.03 sshd
19877 anton     15   0  7684 1544 1124 R  0.0  0.1   0:00.00 sshd
19878 anton     16   0  3252 1804 1184 S  0.0  0.1   0:00.00 bash
19968 www-data  16   0 21048 8276 4592 S  0.0  0.3   0:00.24 apache2
30168 www-data  15   0 29440  16m 5192 S  0.0  0.7   0:12.87 apache2
30369 www-data  15   0 29364  16m 4964 S  0.0  0.6   0:11.75 apache2
31795 www-data  15   0 29224  16m 4800 S  0.0  0.6   0:05.65 apache2
``````
             total       used       free     shared    buffers     cached
Mem:          2560        258       2301          0          0          0
-/+ buffers/cache:        258       2301
Swap:            0          0          0

```> **rubicon said:**
> Is it certain?

Yes, all server functionality fails like sending e-mail via mutt etc but all web pages runs smoothly as usual.

---

### Post by rubicon on 2008-06-24
Nothing seems wrong to me, but one thing: do you really have no swap memory or is it just because of virtualization? Also, what does your ISP's support team says about this problem? Sorry, I can't tell anything more useful now... 

Subscribed to this thread, maybe I'll get more ideas when you post those error messages :)

---

### Post by apakatt on 2008-06-25
Okey, I've found the problem.
I logged in to it today and everything looks fine:
```
             total       used       free     shared    buffers     cached
Mem:           512        239        272          0          0          0
-/+ buffers/cache:        239        272
Swap:            0          0          0
```

But I started looking at my contract and I noticed that I didn't actually have 512 RAM but 256 which was doubled up to 512 when the server had extra free memory that no one used (burst).

So I'll just have to buy new memory (or do some memory tweaking). :)

---

### Post by apakatt on 2008-06-25
Argh, there seems to be some kind of problem anyway. Don't know if it's still memory related to the previous post.

```
anton@downpenguin:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           512        232        279          0          0          0
-/+ buffers/cache:        232        279
Swap:            0          0          0
anton@downpenguin:~$ sudo aptitude install php5-cli
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  php5-cli
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
FATAL -> Failed to fork.
```

---

### Post by rubicon on 2008-06-25
That's odd. There's no obvious reason to fail at fork() unless your ISP has strictly limited number of processes on VPSes and it have already reached the limit.

Googled this page: [http://lists.tagcommons.org/pipermail/apt-rpm-laiskiainen.org/2006-June/000418.html](http://lists.tagcommons.org/pipermail/apt-rpm-laiskiainen.org/2006-June/000418.html) 
*panu* tells quite right thing, 
> 
a system that fails to fork new processes 
under normal conditions sounds seriously ill to me.


---

### Post by apakatt on 2008-06-26
Todays error message:
```
anton@downpenguin:~$ free -
             total       used       free     shared    buffers     cached
Mem:        524288     254228     270060          0          0          0
-/+ buffers/cache:     254228     270060
Swap:            0          0          0
anton@downpenguin:~$ sudo aptitude install zsh
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Uncaught exception: Not enough resources to create thread
```I havn't got a decent reply from my VPS-provider regarding this issue but it seems to be related to the memory. It seems as I've only got 256 MB to play with even though it looks like I have 512MB

--- EDIT ---
I just noticed the problem. I had a fairly big archive in a MySQL database and the PHP-page that fetched all the rows from different tables got a little crazy. After limiting the SQL-query in the code the memory usage was a lot smaller. So I fixed the code and bought more memory. :)

---

