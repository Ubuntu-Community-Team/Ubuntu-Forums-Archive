---
title: "Syslog missing and logwatch issues"
date: 2015-06-26
forum: General Help
---

### Post by MACscr on 2015-06-26
EDIT: I say logwatch a bunch, but really meant logrotate. Doh

im running ubuntu 8gb flash drives, so not much space. Also to save the storage from premature death, im logging mostly to a central logging server, but also have local logging to a tmpfs mount. Now this environment has been in development for quite awhile and i havent looked at it for a long time either. Just noticed that there is no syslog file on any of them. lol. I do have fstab to mount things correctly, so i would hope that would be early enough. Maybe not?

Plus my cron.daily for logwatch emails me the following error (shouldnt these work by default?): 

```
/etc/cron.daily/logrotate:error: skipping "/var/log/aptitude" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/dpkg.log" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/alternatives.log" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/lfd.log" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/ppp-connect-errors" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/syslog" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/mail.info" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/mail.warn" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/mail.err" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/mail.log" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/daemon.log" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/kern.log" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/auth.log" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/user.log" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/lpr.log" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/cron.log" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/rsyslog.log" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/debug" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/messages" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/ufw.log" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/wtmp" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
error: skipping "/var/log/btmp" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
run-parts: /etc/cron.daily/logrotate exited with return code 1
```

Though are my perms/ownership really wrong?

```
root@stor1:/var/log# ls -lah
total 656K
drwxrwxrwt  5 root   root    240 Jun 25 06:34 .
drwxr-xr-x 12 root   root   4.0K Jul 16  2014 ..
drwxr-xr-x  2 root   root     80 Jun 25 02:37 apt
-rw-r--r--  1 root   root    676 Jun 25 01:52 boot.log
-rw-r--r--  1 root   adm     82K Jun 25 01:51 dmesg
-rw-r--r--  1 root   root      0 Jun 25 01:51 dmesg.0
-rw-r--r--  1 root   root    15K Jun 26 06:49 dpkg.log
-rw-------  1 root   root   2.9K Jun 26 07:00 lfd.log
drwxr-x---  2 puppet puppet   40 Jun 25 01:52 puppet
-rw-r--r--  1 root   root   401K Jun 25 01:48 udev
drwxr-xr-x  2 root   root     80 Jun 26 06:45 unattended-upgrades
-rw-r-----  1 root   adm    138K Jun 26 07:47 uptrack.log
```

---

### Post by dino99 on 2015-06-26
Looks like you have made some tweaks disturbing the default ubuntu ones. Here is my output for comparing

```
/var/log > ls -lah
total 7,3M
drwxrwxr-x 16 root              syslog 4,0K juin  26 06:53 ./
drwxr-xr-x 13 root              root   4,0K août  30  2014 ../
-rw-r--r--  1 root              root   8,4K juin  26 12:45 alternatives.log
drwxr-xr-x  2 root              root   4,0K déc.   1  2014 apparmor/
-rw-r-----  1 root              adm       0 juin  24 07:03 apport.log
-rw-r-----  1 root              adm     388 juin  23 22:42 apport.log.1
-rw-r-----  1 root              adm     267 juin  22 11:18 apport.log.2.gz
-rw-r-----  1 root              adm     212 juin  19 07:30 apport.log.3.gz
drwxr-xr-x  2 root              root   4,0K juin   1 07:18 apt/
-rw-r-----  1 syslog            adm     91K juin  26 16:30 auth.log
-rw-r-----  1 syslog            adm     96K juin  21 08:44 auth.log.1
-rw-r-----  1 syslog            adm    1,2K juin  14 08:04 auth.log.2.gz
-rw-r--r--  1 root              root    12K juin  26 06:44 boot.log
-rw-------  1 root              utmp      0 juin  14 07:59 btmp
drwxr-xr-x  2 root              root   4,0K juin  26 06:53 cups/
drwxr-xr-x  4 root              root   4,0K sept.  6  2014 dist-upgrade/
-rw-r--r--  1 root              root   503K juin  26 13:40 dpkg.log
-rw-r--r--  1 root              root   3,8K juin  23 22:37 fontconfig.log
drwxr-xr-x  2 root              root   4,0K août  30  2014 fsck/
drwx--x--x  2 root              gdm    4,0K mai   23 08:16 gdm/
-rw-r--r--  1 root              root   1,4K juin  26 06:44 gpu-manager.log
drwxr-xr-x  3 root              root   4,0K août  30  2014 hp/
drwxr-xr-x  3 root              root   4,0K oct.   8  2014 installer/
-rw-r-----  1 syslog            adm    1,4M juin  26 16:27 kern.log
-rw-r-----  1 syslog            adm    1,6M juin  21 08:40 kern.log.1
-rw-r-----  1 syslog            adm     16K juin  14 08:00 kern.log.2.gz
drwxr-xr-x  2 root              root   4,0K juin  26 06:44 lightdm/
drwxr-x---  2 privoxy           adm    4,0K juin  21 08:44 privoxy/
drwxr-x---  3 root              adm    4,0K juin  21 08:44 samba/
drwx------  2 speech-dispatcher root   4,0K mai   16  2014 speech-dispatcher/
-rw-r-----  1 syslog            adm    272K juin  26 16:46 syslog
-rw-r-----  1 syslog            adm    903K juin  26 06:53 syslog.1
-rw-r-----  1 syslog            adm    142K juin  25 05:46 syslog.2.gz
-rw-r-----  1 syslog            adm    135K juin  24 07:03 syslog.3.gz
-rw-r-----  1 syslog            adm    122K juin  23 06:27 syslog.4.gz
-rw-r-----  1 syslog            adm     59K juin  22 06:19 syslog.5.gz
-rw-r-----  1 syslog            adm     93K juin  21 08:44 syslog.6.gz
-rw-r-----  1 syslog            adm     93K juin  20 06:57 syslog.7.gz
-rw-r-----  1 syslog            adm    616K juin  26 16:27 ufw.log
-rw-r-----  1 syslog            adm    965K juin  20 17:05 ufw.log.1
-rw-r-----  1 syslog            adm     357 juin  13 09:28 ufw.log.2.gz
drwxr-x---  2 root              adm    4,0K août  30  2014 unattended-upgrades/
drwxr-xr-x  2 root              root   4,0K mars  23 15:39 upstart/
-rw-rw-r--  1 root              utmp    63K juin  26 16:53 wtmp
-rw-r--r--  1 root              root    25K juin  26 13:33 Xorg.0.log
-rw-r--r--  1 root              root    47K juin  25 18:00 Xorg.0.log.old
```


maybe also glance at the missed 'recommended' packages list inside 'synaptic' you have removed by accident

---

