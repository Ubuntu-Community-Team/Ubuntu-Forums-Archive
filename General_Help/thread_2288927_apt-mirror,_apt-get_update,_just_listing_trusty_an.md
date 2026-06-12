---
title: "apt-mirror, apt-get update, just listing trusty and nothing else"
date: 2015-07-30
forum: General Help
---

### Post by claw-o on 2015-07-30
Ran apt-mirror and got over 150+GB mirrored, no errors.
But when I change all the sources on the client, it only looks a trusty, no trusty-updates, etc.

Am I missing something?

```

[root@vacsld02ubuntu ~]# more /etc/apt/mirror.list
set base_path         /var/spool/apt-mirror
set mirror_path       $base_path/mirror
set skel_path         $base_path/skel
set var_path          $base_path/var
set postmirror_script $var_path/postmirror.sh
set defaultarch       amd64
set run_postmirror    0
set nthreads          20
set _tilde            0
set _autoclean        1


deb http://ca.archive.ubuntu.com/ubuntu trusty main restricted universe multiverse
deb http://ca.archive.ubuntu.com/ubuntu trusty-security main restricted universe multiverse
deb http://ca.archive.ubuntu.com/ubuntu trusty-updates main restricted universe multiverse
deb http://ca.archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse


deb-i386 http://ca.archive.ubuntu.com/ubuntu trusty main restricted universe multiverse
deb-i386 http://ca.archive.ubuntu.com/ubuntu trusty-security main restricted universe multiverse
deb-i386 http://ca.archive.ubuntu.com/ubuntu trusty-updates main restricted universe multiverse
deb-i386 http://ca.archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse


deb-src http://ca.archive.ubuntu.com/ubuntu trusty main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu trusty-security main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu trusty-updates main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse


clean http://ca.archive.ubuntu.com/ubuntu

```

```

[root@vacsld02ubuntu ~]# apt-mirror
Downloading 468 index files using 20 threads...
Begin time: Thu Jul 30 14:44:40 2015
[20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]... 
End time: Thu Jul 30 14:44:49 2015


Processing translation indexes: [TTTTTTTT]


Downloading 213 translation files using 20 threads...
Begin time: Thu Jul 30 14:44:49 2015
[20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]... 
End time: Thu Jul 30 14:44:52 2015


Processing indexes: [SSSSPPPPPPPP]


0 bytes will be downloaded into archive.
Downloading 0 archive files using 0 threads...
Begin time: Thu Jul 30 14:54:55 2015
[0]... 
End time: Thu Jul 30 14:54:55 2015


0 bytes in 0 files and 0 directories will be freed...
[root@vacsld02ubuntu ~]# 

```


```

root@VACSLL50697:~# more /etc/apt/sources.list
deb http://vacsld02ubuntu/ubuntu/ trusty main restricted
deb-src http://vacsld02ubuntu/ubuntu/ trusty main restricted
deb http://vacsld02ubuntu/ubuntu/ trusty-updates main restricted
deb-src http://vacsld02ubuntu/ubuntu/ trusty-updates main restricted
deb http://vacsld02ubuntu/ubuntu/ trusty universe
deb-src http://vacsld02ubuntu/ubuntu/ trusty universe
deb http://vacsld02ubuntu/ubuntu/ trusty-updates universe
deb-src http://vacsld02ubuntu/ubuntu/ trusty-updates universe
deb http://vacsld02ubuntu/ubuntu/ trusty multiverse
deb-src http://vacsld02ubuntu/ubuntu/ trusty multiverse
deb http://vacsld02ubuntu/ubuntu/ trusty-updates multiverse
deb-src http://vacsld02ubuntu/ubuntu/ trusty-updates multiverse
deb http://vacsld02ubuntu/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://vacsld02ubuntu/ubuntu/ trusty-backports main restricted universe multiverse
deb http://vacsld02ubuntu/ubuntu trusty-security main restricted
deb-src http://vacsld02ubuntu/ubuntu trusty-security main restricted
deb http://vacsld02ubuntu/ubuntu trusty-security universe
deb-src http://vacsld02ubuntu/ubuntu trusty-security universe
deb http://vacsld02ubuntu/ubuntu trusty-security multiverse
deb-src http://vacsld02ubuntu/ubuntu trusty-security multiverse

```

```

root@VACSLL50697:~# apt-get update
Apt-Spacewalk: Updating sources.list
Ign http://vacsld02ubuntu trusty InRelease
Hit http://vacsld02ubuntu trusty Release.gpg
Hit http://vacsld02ubuntu trusty Release
Hit http://vacsld02ubuntu trusty/main Sources
Hit http://vacsld02ubuntu trusty/restricted Sources
Hit http://vacsld02ubuntu trusty/universe Sources
Hit http://vacsld02ubuntu trusty/multiverse Sources
Hit http://vacsld02ubuntu trusty/main amd64 Packages
Hit http://vacsld02ubuntu trusty/restricted amd64 Packages
Hit http://vacsld02ubuntu trusty/universe amd64 Packages
Hit http://vacsld02ubuntu trusty/multiverse amd64 Packages
Hit http://vacsld02ubuntu trusty/main i386 Packages
Hit http://vacsld02ubuntu trusty/restricted i386 Packages
Hit http://vacsld02ubuntu trusty/universe i386 Packages
Hit http://vacsld02ubuntu trusty/multiverse i386 Packages
Hit http://vacsld02ubuntu trusty/main Translation-en
Hit http://vacsld02ubuntu trusty/multiverse Translation-en
Hit http://vacsld02ubuntu trusty/restricted Translation-en
Hit http://vacsld02ubuntu trusty/universe Translation-en
Ign http://vacsld02ubuntu trusty/main Translation-en_US
Reading package lists... Done 

```

---

