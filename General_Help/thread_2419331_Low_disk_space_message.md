---
title: "Low disk space message"
date: 2019-05-20
forum: General Help
---

### Post by KieranFitzgerald on 2019-05-20
Ubuntu 16.04 LTS 64 bit
I get this message every time I turn on the computer, see attachment.
Any recommendations as to what I should do?
Thanks

---

### Post by Impavidus on 2019-05-20
Let's see how much space is used in /var:```
df -h
```One possibility is an overflowing log file:```
ls -l /var/log
```Most people don't have a separate partition for /var, but it's OK if you have.

---

### Post by KieranFitzgerald on 2019-05-20
Here are the results of the commands

kieran@Kierans-Desktop:~$ df -h
```

Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           390M  6.3M  383M   2% /run
/dev/sda2        26G  6.9G   18G  29% /
/dev/sda3        15G  5.3G  9.0G  37% /usr
tmpfs           1.9G  7.5M  1.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sda1       487M   38M  449M   8% /boot/efi
/dev/sdb1       3.7G  3.5G     0 100% /var
/dev/loop3       90M   90M     0 100% /snap/core/6673
/dev/loop5       22M   22M     0 100% /snap/chromium-ffmpeg/13
/dev/loop8      210M  210M     0 100% /snap/firefox/203
/dev/loop2      210M  210M     0 100% /snap/firefox/212
/dev/loop0       92M   92M     0 100% /snap/core/6531
/dev/loop1      151M  151M     0 100% /snap/opera/36
/dev/loop4      151M  151M     0 100% /snap/opera/35
/dev/loop6      210M  210M     0 100% /snap/firefox/198
/dev/loop7      151M  151M     0 100% /snap/opera/37
/dev/loop9       90M   90M     0 100% /snap/core/6818
/dev/sdb3       716G  188G  493G  28% /home
tmpfs           390M   60K  390M   1% /run/user/1000


```

kieran@Kierans-Desktop:~$ ls -l /var/log
```
total 2692
-rw-r--r-- 1 root              root   1505 May 16 10:25 alternatives.log
-rw-r--r-- 1 root              root   1408 Apr 12 09:24 alternatives.log.1
-rw-r--r-- 1 root              root   4978 Mar 23 16:28 alternatives.log.2.gz
-rw-r----- 1 root              adm       0 May 17 23:19 apport.log
-rw-r----- 1 root              adm     524 May 13 19:29 apport.log.1
-rw-r----- 1 root              adm     363 May 12 12:50 apport.log.2.gz
-rw-r----- 1 root              adm     258 May  8 12:39 apport.log.3.gz
-rw-r----- 1 root              adm     275 May  5 11:38 apport.log.4.gz
-rw-r----- 1 root              adm     274 Apr 23 10:31 apport.log.5.gz
-rw-r----- 1 root              adm     258 Apr 19 10:28 apport.log.6.gz
-rw-r----- 1 root              adm     258 Apr 16 21:26 apport.log.7.gz
drwxr-xr-x 2 root              root   4096 May  1 09:36 apt
-rw-r----- 1 syslog            adm       0 May 20 12:17 auth.log
-rw-r----- 1 syslog            adm   54559 May 20 09:52 auth.log.1
-rw-r----- 1 syslog            adm    4356 May 12 10:28 auth.log.2.gz
-rw-r----- 1 syslog            adm    5029 May  5 09:43 auth.log.3.gz
-rw-r----- 1 syslog            adm    4512 Apr 28 09:32 auth.log.4.gz
-rw-r--r-- 1 root              root      0 May 20 09:47 boot.log
drwxr-xr-x 5 root              root   4096 Mar  9 11:14 boot-repair
-rw-r--r-- 1 root              root  57457 Jul 31  2018 bootstrap.log
-rw------- 1 root              utmp      0 May  1 09:36 btmp
-rw------- 1 root              utmp   1152 Apr 20 17:37 btmp.1
drwxr-xr-x 2 root              root   4096 May 20 09:52 cups
drwxr-xr-x 2 root              root   4096 Apr  9  2018 dist-upgrade
-rw-r----- 1 root              adm      31 Jul 31  2018 dmesg
-rw-r--r-- 1 root              root 110770 May 16 10:27 dpkg.log
-rw-r--r-- 1 root              root 133109 Apr 30 18:10 dpkg.log.1
-rw-r--r-- 1 root              root 156264 Mar 29 15:36 dpkg.log.2.gz
-rw-r--r-- 1 root              root  32032 Mar 23 16:28 faillog
-rw-r--r-- 1 root              root   4036 Mar 10 21:50 fontconfig.log
drwxr-xr-x 2 root              root   4096 Jul 31  2018 fsck
-rw-r--r-- 1 root              root   1890 May 20 09:47 gpu-manager.log
drwxr-xr-x 3 root              root   4096 Jul 31  2018 hp
drwxrwxr-x 2 root              root   4096 Mar  7 18:01 installer
-rw-r----- 1 syslog            adm       0 May 20 09:52 kern.log
-rw-r----- 1 syslog            adm  798720 May 20 09:48 kern.log.1
-rw-r----- 1 syslog            adm  184189 May 12 10:26 kern.log.2.gz
-rw-r----- 1 syslog            adm  226246 May  5 09:41 kern.log.3.gz
-rw-r----- 1 syslog            adm  227019 Apr 28 09:29 kern.log.4.gz
-rw-rw-r-- 1 root              utmp 292292 Mar 23 16:28 lastlog
drwxr-xr-x 2 root              root   4096 May 20 09:52 lightdm
-rw-r--r-- 1 root              root     55 May 20 09:47 prime-offload.log
-rw-r--r-- 1 root              root     30 May 20 09:47 prime-supported.log
drwx------ 2 speech-dispatcher root   4096 Feb 18  2016 speech-dispatcher
-rw-r----- 1 syslog            adm       0 May 20 12:25 syslog
-rw-r----- 1 syslog            adm    4096 May 20 09:52 syslog.1
-rw-r----- 1 syslog            adm     659 May 19 09:16 syslog.2.gz
-rw-r----- 1 syslog            adm   37267 May 17 09:39 syslog.3.gz
-rw-r----- 1 syslog            adm   50264 May 16 10:25 syslog.4.gz
-rw-r----- 1 syslog            adm   55356 May 15 10:16 syslog.5.gz
-rw-r----- 1 syslog            adm   73783 May 14 10:11 syslog.6.gz
-rw-r----- 1 syslog            adm   76168 May 13 09:53 syslog.7.gz
drwxr-x--- 2 root              adm    4096 May  1 09:36 unattended-upgrades
drwxr-xr-x 2 root              root   4096 May 19  2016 upstart
-rw-r--r-- 1 root              root    140 Mar  9 13:32 vbox-setup.log
-rw-r--r-- 1 root              root    140 Mar  9 13:06 vbox-setup.log.1
-rw-r--r-- 1 root              root    140 Mar  9 12:57 vbox-setup.log.2
-rw-rw-r-- 1 root              utmp  59136 May 20 09:47 wtmp
-rw-rw-r-- 1 root              utmp 112896 May  1 09:31 wtmp.1
-rw-r--r-- 1 root              root  32435 May 20 09:48 Xorg.0.log
-rw-r--r-- 1 root              root  33295 May 19 20:36 Xorg.0.log.old

```

---

### Post by Peter_van_Loenhout on 2019-05-20
You can remove old logging to reclaim a little bit of diskspace: rm -rf /var/log/*.gz
See if this frees up some diskspace:
  apt-get autoclean
  apt-get clean
  apt-get autoremove

That could be a start.

---

### Post by Impavidus on 2019-05-20
3.9GB may be a bit tight for /var. I currently use 1.9GB, so it may work. Now you see the disadvantage of using multiple partitions: there's plenty of space left on the root partition, but not on /var. If you'd kept it on the same partition, you wouldn't have this problem. Maybe your sda is an SSD and you wanted to keep your /var on an HDD to increase life of your SSD?

Try to dig a bit deeper to find what's consuming that space:```
sudo du -sk /var/* | sort -n
```

---

