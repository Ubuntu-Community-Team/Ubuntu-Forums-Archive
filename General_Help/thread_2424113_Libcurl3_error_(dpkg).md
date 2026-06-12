---
title: "Libcurl3 error (dpkg)"
date: 2019-08-03
forum: General Help
---

### Post by extremeomen213 on 2019-08-03
Hi All,

New to Linux (been using it for a few days) managed to do some simple commands on the terminal however after encountering the below error I seem to have hit a brick wall, hoping someone here might be able to help with this would be greatly appreciated.

p.s have tried updating, full upgrade, auto remove etc from the sudo apt commands.

~$ sudo apt-get full-upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libcurl3-gnutls
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/184 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 227122 files and directories currently installed.)
Preparing to unpack .../libcurl3-gnutls_7.47.0-1ubuntu2.13_amd64.deb ...
dpkg: error processing archive /var/cache/apt/archives/libcurl3-gnutls_7.47.0-1ubuntu2.13_amd64.deb (--unpack):
 read error in '/var/lib/dpkg/info/libcurl3-gnutls:amd64.triggers': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libcurl3-gnutls_7.47.0-1ubuntu2.13_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by oldos2er on 2019-08-03
Try clearing the cache? ```
sudo apt clean
```

---

### Post by extremeomen213 on 2019-08-03
doesn't seem to work either, simply returns back to a new line without doing anything

---

### Post by extremeomen213 on 2019-08-03
dpkg error wont allow the install, also tried purging the file but that produces the same error.

~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libcurl3-gnutls
The following packages will be upgraded:
  libcurl3-gnutls
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 184 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 [http://im.archive.ubuntu.com/ubuntu](http://im.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libcurl3-gnutls amd64 7.47.0-1ubuntu2.13 [184 kB]
Fetched 184 kB in 0s (658 kB/s)         
(Reading database ... 227122 files and directories currently installed.)
Preparing to unpack .../libcurl3-gnutls_7.47.0-1ubuntu2.13_amd64.deb ...
dpkg: error processing archive /var/cache/apt/archives/libcurl3-gnutls_7.47.0-1ubuntu2.13_amd64.deb (--unpack):
 read error in '/var/lib/dpkg/info/libcurl3-gnutls:amd64.triggers': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libcurl3-gnutls_7.47.0-1ubuntu2.13_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by oldos2er on 2019-08-04
You may need to fsck the partition; there's some info on fsck and input/output errors in this thread: [https://ubuntuforums.org/showthread.php?t=2344963](https://ubuntuforums.org/showthread.php?t=2344963)

---

