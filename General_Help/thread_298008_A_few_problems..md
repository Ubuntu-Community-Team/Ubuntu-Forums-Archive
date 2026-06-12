---
title: "A few problems."
date: 2006-11-12
forum: General Help
---

### Post by bhirning on 2006-11-12
I just installed Ubuntu Server Edition, 6.06 LTS.

I was able to connect it to the net and was going to edit my index page of /var/www/

when it told me that it cannot write because it was a read-only file system.
i looked at mount:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I see that it says "remount-ro"

I looked online and some people removed it without troubles, so I would try too. I  sudo nano /etc/fstab but get a line like this:


baka@onion:~$ "anycommand"
-bash: /bin/"anycommand": Input/output error

So I try a reboot, but now i am missing a lot of commands. I went from 1111 commands to :

Display all 782 possibilities? (y or n)


I have also lost: sudo, su and man. ](*,) 

baka@onion:~$ su
-bash: su: command not found
baka@onion:~$



Any ideas? 
I will try to reboot to a rescue shell tomorrow when I have access to my tower. (i am ssh into it right now)

thanks.

---

### Post by bhirning on 2006-11-12
lets see if ths helps.

```

baka@onion:~$ ps -aux
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.4   1564   528 ?        S    07:31   0:01 init [2]
root         2  0.0  0.0      0     0 ?        S    07:31   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   07:31   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    07:31   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S<   07:31   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        S<   07:31   0:00 [khelper]
root         7  0.0  0.0      0     0 ?        S<   07:31   0:00 [kthread]
root         9  0.0  0.0      0     0 ?        S<   07:31   0:00 [kblockd/0]
root        10  0.0  0.0      0     0 ?        S<   07:31   0:00 [kacpid]
root       119  0.0  0.0      0     0 ?        S    07:31   0:00 [pdflush]
root       120  0.0  0.0      0     0 ?        S    07:31   0:00 [pdflush]
root       122  0.0  0.0      0     0 ?        S<   07:31   0:00 [aio/0]
root       121  0.0  0.0      0     0 ?        S    07:31   0:00 [kswapd0]
root       710  0.0  0.0      0     0 ?        S<   07:31   0:00 [kseriod]
root      1786  0.0  0.0      0     0 ?        S<   07:31   0:00 [khubd]
root      1888  0.0  0.0      0     0 ?        S<   07:32   0:00 [kacpid-work-0]
root      1889  0.0  0.0      0     0 ?        S    07:33   0:00 [kjournald]
root      2050  0.0  0.4   2108   552 ?        S<s  07:33   0:00 /sbin/udevd --daemon
root      2829  0.0  0.0      0     0 ?        S    07:33   0:00 [shpchpd_event]
root      2919  0.0  0.0      0     0 ?        S<   07:33   0:00 [kgameportd]
syslog    3604  0.0  0.5   1764   704 ?        Ss   07:33   0:00 /sbin/syslogd -u syslog
root      3621  0.0  0.4   1684   500 ?        Ss   07:33   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      3623  0.0  1.0   2408  1332 ?        Ss   07:33   0:00 /sbin/klogd -P /var/run/klogd/kmsg
root      3663  0.0  1.0   2644  1316 ?        S    07:33   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     3727  0.0 13.6 126408 17012 ?        Sl   07:33   0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/myroot      3728  0.0  0.4   1552   504 ?        S    07:33   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root      3816  0.0  0.8   4764  1048 ?        Ss   07:34   0:00 /usr/sbin/sshd
root      3837  0.0  1.9   7524  2396 ?        Ss   07:34   0:00 sshd: baka [priv]
root      3850  0.0  0.2   1628   296 ?        Ss   07:34   0:00 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -s
daemon    3863  0.0  0.3   1804   400 ?        Ss   07:34   0:00 /usr/sbin/atd
root      3873  0.0  0.6   2120   840 ?        Ss   07:34   0:00 /usr/sbin/cron
root      3901  0.0  4.3  16880  5360 ?        Ss   07:34   0:00 /usr/sbin/apache2 -k start -DSSL
root      3921  0.0  0.3   1560   492 tty1     Ss+  07:34   0:00 /sbin/getty 38400 tty1
root      3922  0.0  0.3   1564   496 tty2     Ss+  07:34   0:00 /sbin/getty 38400 tty2
root      3923  0.0  0.3   1564   496 tty3     Ss+  07:34   0:00 /sbin/getty 38400 tty3
root      3924  0.0  0.3   1560   492 tty4     Ss+  07:34   0:00 /sbin/getty 38400 tty4
root      3925  0.0  0.3   1560   492 tty5     Ss+  07:34   0:00 /sbin/getty 38400 tty5
root      3926  0.0  0.3   1564   492 tty6     Ss+  07:34   0:00 /sbin/getty 38400 tty6
www-data  3939  0.0  2.4  17012  3072 ?        S    07:34   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  3940  0.0  2.4  17012  3072 ?        S    07:34   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  3941  0.0  2.4  17012  3072 ?        S    07:34   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  3942  0.0  2.4  17012  3072 ?        S    07:34   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  3943  0.0  2.4  17012  3072 ?        S    07:34   0:00 /usr/sbin/apache2 -k start -DSSL
baka      3944  0.0  1.2   7524  1544 ?        S    07:34   0:00 sshd: baka@pts/0
baka      3945  0.0  2.5   5492  3208 pts/0    Ss+  07:34   0:00 -bash
root      3968  0.0  1.9   7524  2396 ?        Ss   07:36   0:00 sshd: baka [priv]
baka      3970  0.0  1.2   7524  1544 ?        S    07:36   0:00 sshd: baka@pts/1
baka      3971  0.0  2.6   5508  3240 pts/1    Ss   07:36   0:05 -bash
baka      4011  0.0  0.5   2660   640 pts/1    T    07:46   0:00 cat
baka      4048  0.0  0.8   2396  1020 pts/1    R+   09:32   0:00 ps -aux

```

---

### Post by bhirning on 2006-11-13
I did a fresh install on a different hard drive and everything is running smooth! i had a feeling the hard drive was glitching.

---

