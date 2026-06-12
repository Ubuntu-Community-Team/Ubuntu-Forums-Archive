---
title: "/dev/sda5 keeps filling up are they logs?"
date: 2012-11-30
forum: General Help
---

### Post by dinonet on 2012-11-30
Hello, can someone kindly check out why this keeps filling up?

/dev/sda5               233335     90446    130441  41% /boot

I'm guessing it's log files but is that the only thing? I couldn't boot up last time it filled up and I had to delete logs. I don't understand alot of the files and dir? in this list. Any feedback on what is safe to delete and why some weird directories are in there like unattended-upgrades, dist-upgrade?

Sorry if this is a little messy.

[SIZE="1"]
-rw-rw----  1 root      utmp      0 2012-11-01 06:54 btmp
-rw-rw----  1 root      utmp      0 2012-10-01 06:44 btmp.1
drwxr-xr-x  2 root      root   4096 2012-11-01 06:54 ConsoleKit
drwxr-xr-x  2 root      root   4096 2012-09-28 06:56 cups
-rw-r-----  1 syslog    adm   13218 2012-11-30 09:04 daemon.log
drwxr-xr-x  2 root      root   4096 2012-09-26 16:50 dbconfig-common
-rw-r-----  1 syslog    adm    6417 2012-11-30 09:04 debug
-rw-r-----  1 syslog    adm    6417 2012-10-22 11:41 debug.1
drwxr-xr-x  4 root      root   4096 2012-10-20 09:47 dist-upgrade
-rw-r-----  1 root      adm   28913 2012-11-30 09:00 dmesg
-rw-r-----  1 root      adm   29222 2012-10-22 11:41 dmesg.0
-rw-r--r--  1 root      root  65583 2012-11-30 09:10 dpkg.log
-rw-r--r--  1 root      root   2894 2012-10-27 06:49 dpkg.log.1
-rw-r--r--  1 root      root  24048 2012-08-10 15:55 faillog
drwxr-xr-x  2 root      root   4096 2009-06-12 15:24 fsck
drwxrwx--T  2 root      gdm    4096 2012-11-30 09:04 gdm
drwxr-xr-x  3 root      root   4096 2011-11-05 20:11 installer
-rw-r-----  1 syslog    adm   41883 2012-11-30 09:04 kern.log
drwxr-xr-x  2 landscape root   4096 2009-06-12 15:49 landscape
-rw-rw-r--  1 root      utmp 292584 2012-11-30 09:05 lastlog
-rw-r-----  1 syslog    adm       0 2012-11-30 09:00 lpr.log
-rw-r-----  1 syslog    adm       0 2012-11-30 09:00 mail.err
-rw-r-----  1 syslog    adm       0 2012-11-30 09:00 mail.info
-rw-r-----  1 syslog    adm       0 2012-11-30 09:00 mail.log
-rw-r-----  1 syslog    adm       0 2012-11-30 09:00 mail.warn
-rw-r-----  1 syslog    adm   37390 2012-11-30 09:47 messages
-rw-r-----  1 syslog    adm    1288 2012-11-25 06:48 messages.1
-rw-r-----  1 syslog    adm     603 2012-11-18 06:54 messages.2.gz
-rw-r-----  1 syslog    adm     678 2012-11-11 06:52 messages.3.gz
-rw-r-----  1 syslog    adm     569 2012-11-04 06:54 messages.4.gz
drwxr-s---  2 mysql     adm    4096 2012-03-12 06:41 mysql
-rw-r-----  1 mysql     adm       0 2012-11-05 15:57 mysql.err
-rw-r-----  1 mysql     adm       0 2012-11-30 06:48 mysql.log
-rw-r-----  1 mysql     adm      20 2012-11-29 06:32 mysql.log.1.gz
-rw-r-----  1 mysql     adm      20 2012-11-28 06:53 mysql.log.2.gz
-rw-r-----  1 mysql     adm      20 2012-11-27 06:36 mysql.log.3.gz
-rw-r-----  1 mysql     adm      20 2012-11-26 06:33 mysql.log.4.gz
-rw-r-----  1 mysql     adm      20 2012-11-25 06:48 mysql.log.5.gz
-rw-r-----  1 mysql     adm      20 2012-11-24 06:41 mysql.log.6.gz
-rw-r-----  1 mysql     adm      20 2012-11-23 06:42 mysql.log.7.gz
drwxr-sr-x  2 news      news   4096 2009-06-12 15:26 news
-rw-r--r--  1 root      root      0 2012-11-05 15:57 pycentral.log
drwxr-x---  3 root      adm    4096 2012-11-04 06:54 samba
-rw-r-----  1 syslog    adm   59305 2012-11-30 09:47 syslog
-rw-r-----  1 syslog    adm   14306 2012-11-30 06:39 syslog.1
-rw-r-----  1 syslog    adm    1351 2012-11-29 06:25 syslog.2.gz
-rw-r-----  1 syslog    adm    1468 2012-11-28 06:39 syslog.3.gz
-rw-r-----  1 syslog    adm    1167 2012-11-27 06:25 syslog.4.gz
-rw-r-----  1 syslog    adm    1389 2012-11-26 06:25 syslog.5.gz
-rw-r-----  1 syslog    adm    1416 2012-11-25 06:47 syslog.6.gz
-rw-r-----  1 syslog    adm    1494 2012-11-24 06:39 syslog.7.gz
-rw-r--r--  1 root      root 144917 2012-11-30 09:00 udev
-rw-r-----  1 syslog    adm       0 2012-11-30 09:00 ufw.log
drwxr-xr-x  2 root      root  20480 2012-11-30 06:42 unattended-upgrades
-rw-r-----  1 syslog    adm     396 2012-11-30 09:47 user.log
-rw-r-----  1 root      adm       0 2012-11-25 06:48 vsftpd.log
-rw-r-----  1 root      adm  143440 2012-11-22 11:00 vsftpd.log.1
-rw-r-----  1 root      adm    5409 2012-11-17 14:44 vsftpd.log.2
-rw-r-----  1 root      adm    3887 2012-11-10 14:34 vsftpd.log.3
-rw-r-----  1 root      adm    9602 2012-11-03 09:35 vsftpd.log.4
-rw-rw-r--  1 root      utmp  24576 2012-11-30 09:05 wtmp
-rw-rw-r--  1 root      utmp  61440 2012-10-31 17:24 wtmp.1
-rw-r--r--  1 root      root   8168 2012-11-30 09:04 Xorg.0.log
-rw-r--r--  1 root      root   8168 2012-11-30 09:04 Xorg.0.log.old
-rw-r--r--  1 root      root   8168 2012-11-30 09:04 Xorg.1.log
-rw-r--r--  1 root      root   8168 2012-11-30 09:04 Xorg.2.log
-rw-r--r--  1 root      root   8168 2012-11-30 09:04 Xorg.3.log
-rw-r--r--  1 root      root   8168 2012-11-30 09:04 Xorg.3.log.old
-rw-r--r--  1 root      root   8168 2012-11-30 09:04 Xorg.4.log
-rw-r--r--  1 root      root   8168 2012-11-30 09:04 Xorg.5.log[/SIZE]

---

### Post by dannyboy79 on 2012-11-30
show me whats at the end of your kern.log and or syslog by issuing the following command
```
tail /var/log/syslog
```
OR
```
tail /var/log/kern.log
```

I am guessing you have some error that keeps repeating and filling up your log files/hard drive space. ALso, you could change your logrotate.conf so it doesn't keep as many backups of log files and also makes them a max file size. Here's a thread where I helped someone else. 
[http://ubuntuforums.org/showthread.php?t=2084168&highlight=logrotate](http://ubuntuforums.org/showthread.php?t=2084168&highlight=logrotate)

---

### Post by dinonet on 2012-11-30
> **dannyboy79 said:**
> show me whats at the end of your kern.log and or syslog by issuing the following command
```
tail /var/log/syslog
```
OR
```
tail /var/log/kern.log
```


Here's what they say on both

lamer@pao:/var$ tail /var/log/kern.log
Nov 30 09:00:28 pao kernel: [   22.652470] __ratelimit: 6 callbacks suppressed
Nov 30 09:00:28 pao kernel: [   22.652492] type=1505 audit(1354284028.190:14):  operation="profile_load" pid=652 name="/usr/lib/cups/backend/cups-pdf"
Nov 30 09:00:28 pao kernel: [   22.655036] type=1505 audit(1354284028.190:15):  operation="profile_load" pid=652 name="/usr/sbin/cupsd"
Nov 30 09:00:28 pao kernel: [   23.081948] type=1505 audit(1354284028.687:16):  operation="profile_load" pid=727 name="/usr/sbin/mysqld"
Nov 30 09:00:28 pao kernel: [   23.092210] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
Nov 30 09:00:28 pao kernel: [   23.161247] type=1505 audit(1354284028.687:17):  operation="profile_load" pid=730 name="/usr/sbin/named"
Nov 30 09:00:29 pao kernel: [   23.663096] type=1505 audit(1354284029.189:18):  operation="profile_load" pid=732 name="/usr/sbin/tcpdump"
Nov 30 09:04:08 pao kernel: [   29.571620] type=1505 audit(1354284248.493:19):  operation="profile_replace" pid=922 name="/usr/sbin/mysqld"
Nov 30 09:04:12 pao kernel: [   33.252063] eth1: no IPv6 routers present
Nov 30 09:04:16 pao kernel: [   37.179833] ppdev: user-space parallel port driver

lamer@pao:/var$ tail /var/log/syslog
Nov 30 09:06:41 pao sudo: pam_sm_authenticate: /home/lamer is already mounted
Nov 30 09:09:03 pao CRON[4235]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Nov 30 09:17:01 pao CRON[8439]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 09:39:01 pao CRON[17496]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Nov 30 09:47:32 pao sudo: pam_sm_authenticate: Called
Nov 30 09:47:32 pao sudo: pam_sm_authenticate: username = [lamer]
Nov 30 09:47:32 pao sudo: pam_sm_authenticate: /home/lamer is already mounted
Nov 30 10:09:01 pao CRON[30340]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Nov 30 10:17:01 pao CRON[1200]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 10:39:01 pao CRON[10154]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)


> **dannyboy79 said:**
> I am guessing you have some error that keeps repeating and filling up your log files/hard drive space. ALso, you could change your logrotate.conf so it doesn't keep as many backups of log files and also makes them a max file size. Here's a thread where I helped someone else. 
[http://ubuntuforums.org/showthread.php?t=2084168&highlight=logrotate](http://ubuntuforums.org/showthread.php?t=2084168&highlight=logrotate)

Thanks for this. I really need to figure out how to set this up.

---

### Post by Wim Sturkenboom on 2012-11-30
/boot does not contain log files. It contains kernels and old kernels will stay in there; so after every kernel update, it will grow a bit.

There are some articles on the web (and possibly threads with solutions on ubuntuforums) how to get rid of them properly.

PS
please use code tags ( [noparse]```
 and 
```[/noparse] ) when posting commands and terminal output

---

### Post by steeldriver on 2012-11-30
I was about to post the same - see this thread for suggestions for cleaning up /boot

[http://ubuntuforums.org/showthread.php?t=1798699](http://ubuntuforums.org/showthread.php?t=1798699)

---

### Post by dinonet on 2012-11-30
Ohh ok so the /boot issue has nothing to do with the log files in /var/log? I guess I should look at taking care of both. By looking at this is my ubuntu server install messed up? What are all these "none" drives?

```

lamer@pao:/var/log$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/pao-root  37494312   3987228  31602444  12% /
none                    110548       208    110340   1% /dev
none                    115176         4    115172   1% /dev/shm
none                    115176       304    114872   1% /var/run
none                    115176         0    115176   0% /var/lock
none                    115176         0    115176   0% /lib/init/rw
none                  37494312   3987228  31602444  12% /var/lib/ureadahead/debugfs
/dev/sda5               233335     90446    130441  41% /boot
/home/lamer/.Private  37494312   3987228  31602444  12% /home/lamer

```

---

### Post by dannyboy79 on 2012-11-30
I didn't notice you were worried about /boot/ since you posted all those log files.

how big is your /boot partition? it's only 41% full, which is no big deal. see here on how to remove old kernels: [http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

the none locations are creating by the OS, I can't explain why though. they're fine.

---

### Post by dinonet on 2012-11-30
> **dannyboy79 said:**
> I didn't notice you were worried about /boot/ since you posted all those log files.

how big is your /boot partition? it's only 41% full, which is no big deal. see here on how to remove old kernels: [http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

the none locations are creating by the OS, I can't explain why though. they're fine.

At first I thought it was a log file issue. Shows how much I need to learn even though I've had this server set up for a while now. I don't know why all those kernels were saved. I don't recall upgrading the kernel that many times! I checked a few places and they suggested running this:

```

dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge

```

Not that I like to just run commands without knowing for sure what they do but apparently it removed all the prior and unused kernels.

I will still look into how to manage this log file directory though.

Thanks for all your help.

---

### Post by dino99 on 2012-11-30
using a server is not install then forget  :)

log files are usefull if you watch them to know about possible issues; and you still can set your preferences if you does not care about some logs (logrotate/whoopsie/zeitgeist)

---

### Post by Wim Sturkenboom on 2012-11-30
First of all, from your df output it does not look that you have anything to worry about at this stage.

> **dinonet said:**
> I don't know why all those kernels were saved. I don't recall upgrading the kernel that many times!
Old kernels are saved as a fallback, e.g. in case something that you are using is not compatible with the newer kernel. So you can fall back to the older kernel.

> **dinonet said:**
> 
I will still look into how to manage this log file directory though.
Older logs are the compressed one in your log directory; if you no longer need them, you can delete them.

---

