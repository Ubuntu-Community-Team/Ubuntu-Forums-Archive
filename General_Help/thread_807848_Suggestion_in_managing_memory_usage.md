---
title: "Suggestion in managing memory usage"
date: 2008-05-26
forum: General Help
---

### Post by ikkubus on 2008-05-26
Hi,

I have a filehosting server (4gb ram, 2.x gh dualcore)and i noticed that my server is slowing down every time i upload a file. then eventually the server can't display any web page.

I also check memory consumption. this is the result of #free

```
 
             total       used       free     shared    buffers     cached
Mem:       4025660    2940172    1085488          0     157468    2423548
-/+ buffers/cache:     359156    3666504
Swap:      2104504          0    2104504


```

is it normal? do i need to change something to optimize my server? like whats the best partition? swap? etc... anything that will help optimize servers performance. 
thanks

---

### Post by kerry_s on 2008-05-26
that looks fine, it's not a memory problem.

more info on the way the server is set up might help us help you.

---

### Post by ikkubus on 2008-05-26
```

             total       used       free     shared    buffers     cached
Mem:       4025660    3495992     529668          0     165972    2952436
-/+ buffers/cache:     377584    3648076
Swap:      2104504          0    2104504

```

this is my mem after 12 hrs..

is it ok to restart apache daily? Because whenever i restart apache mem usage is back to normal. Is there another way to "refresh memory"?  

here are some changes that i made:

**php.ini**
> timeout 0
upload max size 100mb

**.htaccess**
> php_value upload_max_filesize 100M
php_value post_max_size 100M
LimitRequestBody 0

thanks for your reply :)

---

### Post by ikkubus on 2008-05-27
after 18 hrs 21 hrs..
server memory is::
```

             total       used       free     shared    buffers     cached
Mem:       4025660    3985280      40380          0     168544    2992424
-/+ buffers/cache:     824312    3201348
Swap:      2104504          0    2104504


```

is there any way to free used memory?

---

### Post by sdennie on 2008-05-27
In your first post, the actual memory used is only 350M and in the last it's only 825M.  You are *FAR* from using swap in either post.  I don't know much about apache but, in both cases, your memory usage is perfectly fine.  When the machine gets to the state where it's no longer displaying pages, run top to see if anything is amiss.

---

### Post by sdennie on 2008-05-27
Thinking about this a bit more.  Depending on how your server is hosted, you simply may not have enough bandwidth to both upload files and do anything else network related.  I've seen similar behavior in P2P applications when upload rates aren't being limited.  (This is especially likely if your server is hosted on a conventional ADSL or cable connection).

---

### Post by ikkubus on 2008-05-27
im freaking out coz now i dont have much traffic... and servers mem is all used up. what if i have heavy traffic? maybe server wont last long...

one more thing i dont know what process eats the memory. i tried using top command but theres nothing there. CPU and mem usage are 0.0

---

### Post by sdennie on 2008-05-27
I haven't seen any evidence that you've posted to suggest that you are having memory problems.  I have no way to say this for sure but, if you don't have enough outbound bandwidth, a few users downloading large files may saturate your link to the point where it can no longer reliably serve pages.

---

### Post by ikkubus on 2008-05-27
hows this? 64mb free memory out of 4gb mem? i think its not normal. considering that there are only about 10 people online. and 
 

```

             total       used       free     shared    buffers     cached
Mem:       4025660    3379972     645688          0     142184    2821752
-/+ buffers/cache:     416036    3609624
Swap:      2104504          0    2104504

```
[B]
this are the running processes 
[/B]
```

 ps -ef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 May25 ?        00:00:00 /sbin/init
root         2     0  0 May25 ?        00:00:00 [kthreadd]
root         3     2  0 May25 ?        00:00:00 [migration/0]
root         4     2  0 May25 ?        00:00:00 [ksoftirqd/0]
root         5     2  0 May25 ?        00:00:00 [watchdog/0]
root         6     2  0 May25 ?        00:00:00 [migration/1]
root         7     2  0 May25 ?        00:00:00 [ksoftirqd/1]
root         8     2  0 May25 ?        00:00:00 [watchdog/1]
root         9     2  0 May25 ?        00:00:00 [events/0]
root        10     2  0 May25 ?        00:00:00 [events/1]
root        11     2  0 May25 ?        00:00:00 [khelper]
root        44     2  0 May25 ?        00:00:00 [kblockd/0]
root        45     2  0 May25 ?        00:00:00 [kblockd/1]
root        48     2  0 May25 ?        00:00:00 [kacpid]
root        49     2  0 May25 ?        00:00:00 [kacpi_notify]
root       128     2  0 May25 ?        00:00:00 [kseriod]
root       178     2  0 May25 ?        00:00:00 [pdflush]
root       179     2  0 May25 ?        00:00:05 [pdflush]
root       180     2  0 May25 ?        00:00:00 [kswapd0]
root       223     2  0 May25 ?        00:00:00 [aio/0]
root       224     2  0 May25 ?        00:00:00 [aio/1]
root      1158     2  0 May25 ?        00:00:00 [xfslogd/0]
root      1159     2  0 May25 ?        00:00:00 [xfslogd/1]
root      1160     2  0 May25 ?        00:00:00 [xfsdatad/0]
root      1161     2  0 May25 ?        00:00:00 [xfsdatad/1]
root      1164     2  0 May25 ?        00:00:00 [xfs_mru_cache]
root      1203     2  0 May25 ?        00:00:00 [ata/0]
root      1204     2  0 May25 ?        00:00:00 [ata/1]
root      1205     2  0 May25 ?        00:00:00 [ata_aux]
root      1235     2  0 May25 ?        00:00:00 [scsi_eh_0]
root      1237     2  0 May25 ?        00:00:00 [scsi_eh_1]
root      1239     2  0 May25 ?        00:00:00 [scsi_eh_2]
root      1241     2  0 May25 ?        00:00:00 [scsi_eh_3]
root      1352     2  0 May25 ?        00:00:00 [ksnapd]
root      1709     2  0 May25 ?        00:00:00 [ksuspend_usbd]
root      1712     2  0 May25 ?        00:00:00 [khubd]
root      2730     2  0 May25 ?        00:00:09 [kjournald]
root      2891     1  0 May25 ?        00:00:00 /sbin/udevd --daemon
root      4451     1  0 May25 tty4     00:00:00 /sbin/getty 38400 tty4
root      4452     1  0 May25 tty5     00:00:00 /sbin/getty 38400 tty5
root      4454     1  0 May25 tty2     00:00:00 /sbin/getty 38400 tty2
root      4457     1  0 May25 tty3     00:00:00 /sbin/getty 38400 tty3
root      4458     1  0 May25 tty6     00:00:00 /sbin/getty 38400 tty6
root      4523     2  0 May25 ?        00:00:00 [kondemand/0]
root      4524     2  0 May25 ?        00:00:00 [kondemand/1]
syslog    4582     1  0 May25 ?        00:00:00 /sbin/syslogd -u syslog
root      4603     1  0 May25 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4605     1  0 May25 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmsg
root      4626     1  0 May25 ?        00:00:00 /usr/sbin/sshd
root      4684     1  0 May25 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql     4726  4684  0 May25 ?        00:00:57 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locki
root      4727  4684  0 May25 ?        00:00:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root      4795     1  0 May25 ?        00:00:00 /usr/sbin/courierlogger -pid=/var/run/courier/authdaemon/pid -start /usr/lib/courier/courier-authlib/authdaemond
root      4796  4795  0 May25 ?        00:00:00 /usr/lib/courier/courier-authlib/authdaemond
root      4906  4796  0 May25 ?        00:00:00 /usr/lib/courier/courier-authlib/authdaemond
root      4907  4796  0 May25 ?        00:00:00 /usr/lib/courier/courier-authlib/authdaemond
root      4908  4796  0 May25 ?        00:00:00 /usr/lib/courier/courier-authlib/authdaemond
root      4909  4796  0 May25 ?        00:00:00 /usr/lib/courier/courier-authlib/authdaemond
root      4910  4796  0 May25 ?        00:00:00 /usr/lib/courier/courier-authlib/authdaemond
root      5015     1  0 May25 ?        00:00:00 /usr/sbin/saslauthd -a pam -c -m /var/spool/postfix/var/run/saslauthd -r -n 5
root      5016  5015  0 May25 ?        00:00:00 /usr/sbin/saslauthd -a pam -c -m /var/spool/postfix/var/run/saslauthd -r -n 5
root      5017  5015  0 May25 ?        00:00:00 /usr/sbin/saslauthd -a pam -c -m /var/spool/postfix/var/run/saslauthd -r -n 5
root      5019  5015  0 May25 ?        00:00:00 /usr/sbin/saslauthd -a pam -c -m /var/spool/postfix/var/run/saslauthd -r -n 5
root      5020  5015  0 May25 ?        00:00:00 /usr/sbin/saslauthd -a pam -c -m /var/spool/postfix/var/run/saslauthd -r -n 5
root      5127     1  0 May25 tty1     00:00:00 /sbin/getty 38400 tty1
root     14551     1  0 May25 ?        00:00:07 /usr/sbin/apache2 -k start
root     19746     1  0 May26 ?        00:00:00 /usr/sbin/cron
proftpd  19869     1  0 May26 ?        00:00:00 proftpd: (accepting connections)
root     22747     1  0 May26 ?        00:00:00 /usr/lib/postfix/master
postfix  22750 22747  0 May26 ?        00:00:00 qmgr -l -t fifo -u
postfix  22779 22747  0 May26 ?        00:00:00 tlsmgr -l -t unix -u -c
root     23561     1  0 May25 ?        00:00:00 /usr/sbin/courierlogger -pid=/var/run/courier/pop3d.pid -start -name=pop3d /usr/sbin/couriertcpd -maxprocs=40 -maxperip=4 -nodnsl
root     23562 23561  0 May25 ?        00:00:00 /usr/sbin/couriertcpd -maxprocs=40 -maxperip=4 -nodnslookup -noidentlookup -address=0 110 /usr/lib/courier/courier/courierpop3log
root     23616     1  0 May25 ?        00:00:00 /usr/sbin/courierlogger -pid=/var/run/courier/pop3d-ssl.pid -start -name=pop3d-ssl /usr/sbin/couriertcpd -address=0 -maxprocs=40
root     23617 23616  0 May25 ?        00:00:00 /usr/sbin/couriertcpd -address=0 -maxprocs=40 -maxperip=4 -nodnslookup -noidentlookup 995 /usr/bin/couriertls -server -tcpd /usr/
root     23651     1  0 May25 ?        00:00:00 /usr/sbin/courierlogger -pid=/var/run/courier/imapd.pid -start -name=imapd /usr/sbin/couriertcpd -address=0 -maxprocs=40 -maxperi
root     23652 23651  0 May25 ?        00:00:00 /usr/sbin/couriertcpd -address=0 -maxprocs=40 -maxperip=20 -nodnslookup -noidentlookup 143 /usr/lib/courier/courier/imaplogin /us
root     23698     1  0 May25 ?        00:00:00 /usr/sbin/courierlogger -pid=/var/run/courier/imapd-ssl.pid -start -name=imapd-ssl /usr/sbin/couriertcpd -address=0 -maxprocs=40
root     23699 23698  0 May25 ?        00:00:00 /usr/sbin/couriertcpd -address=0 -maxprocs=40 -maxperip=20 -nodnslookup -noidentlookup 993 /usr/bin/couriertls -server -tcpd /usr
root     27962  4626  0 04:33 ?        00:00:00 sshd: root@pts/0
root     27964 27962  0 04:33 pts/0    00:00:00 -bash
www-data 29299 14551  0 07:13 ?        00:00:00 /usr/sbin/apache2 -k start
root     29456  4626  0 07:36 ?        00:00:00 sshd: root@pts/1
root     29467 29456  0 07:37 pts/1    00:00:00 -bash
www-data 29510 14551  0 07:41 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 29685 14551  0 08:00 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 29850 14551  0 08:28 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30184 14551  0 09:00 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30198 14551  0 09:01 ?        00:00:00 /usr/sbin/apache2 -k start
postfix  30273 22747  0 09:14 ?        00:00:00 pickup -l -t fifo -u -c
root     30366     1  0 09:20 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30372 30366  0 09:20 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30373 30366  0 09:20 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30376 30366  0 09:20 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30378 30366  0 09:20 ?        00:00:01 /usr/sbin/apache2 -k start
www-data 30468 30366  0 09:24 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30470 30366  0 09:24 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30471 30366  0 09:25 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30473 30366  0 09:25 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30482 30366  0 09:27 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30498 30366  0 09:28 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30499 30366  0 09:28 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30501 30366  0 09:29 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30502 30366  0 09:29 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30503 30366  0 09:29 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30504 30366  0 09:29 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30505 30366  0 09:29 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30513 30366  0 09:29 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30517 30366  0 09:30 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30520 30366  0 09:30 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30526 30366  0 09:30 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30528 30366  0 09:30 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30529 30366  0 09:30 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30534 30366  0 09:31 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30535 30366  0 09:31 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30536 30366  0 09:31 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30537 30366  0 09:31 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30538 30366  0 09:31 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30539 30366  0 09:31 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30540 30366  0 09:31 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30542 30366  0 09:31 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30543 30366  0 09:31 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30544 30366  0 09:31 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30545 30366  0 09:31 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30546 30366  0 09:32 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30548 30366  0 09:32 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 30549 30366  0 09:32 ?        00:00:00 /usr/sbin/apache2 -k start
root     30550 29467  0 09:33 pts/1    00:00:00 ps -ef


```

---

### Post by sdennie on 2008-05-27
That says you are only using 416M of memory.  The +/- buffers/cache line is the interesting one.  The cache isn't memory used by your applications but instead memory the kernel is keeping around to avoid having to read it from disk again.  You are only using 10% of your memory. :)

---

### Post by ikkubus on 2008-05-27
> **vor said:**
> That says you are only using 416M of memory.  The +/- buffers/cache line is the interesting one.  The cache isn't memory used by your applications but instead memory the kernel is keeping around to avoid having to read it from disk again.  You are only using 10% of your memory. :)



```

                                     
          total       used       free     shared    buffers     cached
Mem:       4025660    3379972     645688          0     142184    2821752
-/+ buffers/cache:     416036    3609624
Swap:      2104504          0    2104504


```

under free column is the available memory right?
and under used column is the used memory. right?

---

### Post by sdennie on 2008-05-27
Yes, the free column displays the free memory.  However, it's the second row that tells you how much you, the user, is actually using.  Again, in the above post, you are using 416M.  When free memory is compute with cached memory included, it generally (and hopefully) seems almost completely used because the cache ideally occupies all the unused memory (a good thing).  However, when your applications actually need the memory that the cache is occupying, the kernel gladly drops stuff from the cache to make room for you applications.  You are *not* running low on memory.  Far from it.

---

### Post by ikkubus on 2008-05-27
oh i see. i didnt mind the 2nd row.. tsk tsk tsk...

anyway dou you have any idea why my server is slowing down?
if its not a memory problem.. what could be the possible problem?

this is my server: DS 5000
you can look the specs of it here:
[http://www.hetzner.de/rootserver_en.html](http://www.hetzner.de/rootserver_en.html)


you mention about outbound traffic.. i dont know much about it. please take a look at servers specs. thanks vor

---

### Post by sdennie on 2008-05-27
> **ikkubus said:**
> you mention about outbound traffic.. i dont know much about it. please take a look at servers specs. thanks vor

As I said, I don't know much about apache but, based on the first few posts, it looks like you are trying to host some largish files.  If too many people are downloading those files, it could saturate your outbound bandwidth and prevent your machine from reliably send ACK packets.  This is an especially common problem using P2P without limiting your upload speed while on a common home broadband connection.  If you are hosting a server at home and allowing people to pound it with long and continuous downloads (and, you'd only need a few people connected to do this), you'd likely face the same problem.  Via apache, I have no idea how you'd go about fixing the problem.

---

### Post by ikkubus on 2008-05-27
ok then, thanks vor for your quick reply. iguess ihave to do more research about filehosting and apache configuration thanks

---

