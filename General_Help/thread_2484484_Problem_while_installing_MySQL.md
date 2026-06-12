---
title: "Problem while installing MySQL"
date: 2023-02-28
forum: General Help
---

### Post by lumaja on 2023-02-28
[SIZE=3]Ubuntu 22.04 LTS[/SIZE]
  
 
  [SIZE=3]While installing MySQL come to alt with this error:[/SIZE]
  
 
  [SIZE=3]luis@l-System-luisj:~$ sudo apt-get install mysql-server[/SIZE]
  [SIZE=3]Reading package lists... Done[/SIZE]
  [SIZE=3]Building dependency tree... Done[/SIZE]
  [SIZE=3]Reading state information... Done[/SIZE]
  [SIZE=3]Some packages could not be installed. This may mean that you have[/SIZE]
  [SIZE=3]requested an impossible situation or if you are using the unstable[/SIZE]
  [SIZE=3]distribution that some required packages have not yet been created[/SIZE]
  [SIZE=3]or been moved out of Incoming.[/SIZE]
  [SIZE=3]The following information may help to resolve the situation:[/SIZE]
  
 
  [SIZE=3]The following packages have unmet dependencies:[/SIZE]
   [SIZE=3]mysql-server-8.0 : Depends: mysql-server-core-8.0 (= 8.0.28-0ubuntu4) but 8.0.32-0ubuntu0.22.04.2 is to be installed[/SIZE]
  [SIZE=3]E: Unable to correct problems, you have held broken packages.[/SIZE]
  [SIZE=3]luis@l-System-luisj:~$ [/SIZE] 
  
 
  [SIZE=3]Can some one help to fix this problem[/SIZE]
  [SIZE=3]Thank you[/SIZE]

---

### Post by SeijiSensei on 2023-02-28
Run
```
sudo apt-get --fix-broken
``` 
If it reports back that the broken dependencies have been fixed, try installing mysql-server again.

If you already have a version of mysql-server on this machine, you might try removing it first before installing
```

sudo apt remove mysql-server
sudo apt install mysql-server

```

---

### Post by lumaja on 2023-03-01
[SIZE=3]Tried your suggestion but there is something wrong[/SIZE]
 [SIZE=3]luis@l-System-luisj:~$ sudo apt-get --fix-broken[/SIZE]
  [SIZE=3][sudo] password for luis: [/SIZE] 
  [SIZE=3]E: Command line option --fix-broken is not understood in combination with the other options[/SIZE]
  [SIZE=3]luis@l-System-luisj:~$ [/SIZE]

---

### Post by MAFoElffen on 2023-03-01
Try
```

sudo apt install --fix-broken

```

---

### Post by lumaja on 2023-03-01
[SIZE=3]There still some problems[/SIZE]
 [SIZE=3]luis@l-System-luisj:~$ sudo apt install --fix-broken[/SIZE]
  [SIZE=3][sudo] password for luis: [/SIZE] 
  [SIZE=3]Reading package lists... Done[/SIZE]
  [SIZE=3]Building dependency tree... Done[/SIZE]
  [SIZE=3]Reading state information... Done[/SIZE]
  [SIZE=3]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/SIZE]
  [SIZE=3]luis@l-System-luisj:~$ sudo apt remove mysql-server[/SIZE]
  [SIZE=3]Reading package lists... Done[/SIZE]
  [SIZE=3]Building dependency tree... Done[/SIZE]
  [SIZE=3]Reading state information... Done[/SIZE]
  [SIZE=3]Package 'mysql-server' is not installed, so not removed[/SIZE]
  [SIZE=3]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/SIZE]
  [SIZE=3]luis@l-System-luisj:~$ sudo apt install mysql-server[/SIZE]
  [SIZE=3]Reading package lists... Done[/SIZE]
  [SIZE=3]Building dependency tree... Done[/SIZE]
  [SIZE=3]Reading state information... Done[/SIZE]
  [SIZE=3]Some packages could not be installed. This may mean that you have[/SIZE]
  [SIZE=3]requested an impossible situation or if you are using the unstable[/SIZE]
  [SIZE=3]distribution that some required packages have not yet been created[/SIZE]
  [SIZE=3]or been moved out of Incoming.[/SIZE]
  [SIZE=3]The following information may help to resolve the situation:[/SIZE]
  
 
  [SIZE=3]The following packages have unmet dependencies:[/SIZE]
   [SIZE=3]mysql-server-8.0 : Depends: mysql-server-core-8.0 (= 8.0.28-0ubuntu4) but 8.0.32-0ubuntu0.22.04.2 is to be installed[/SIZE]
                      [SIZE=3]Recommends: libhtml-template-perl but it is not going to be installed[/SIZE]
                      [SIZE=3]Recommends: mecab-ipadic-utf8 but it is not going to be installed[/SIZE]
  [SIZE=3]E: Unable to correct problems, you have held broken packages.[/SIZE]
  [SIZE=3]luis@l-System-luisj:~$ [/SIZE]

---

### Post by ActionParsnip on 2023-03-01
What is the output of:
```

apt-cache policy mysql-server-8.0 mysql-server-core-8.0

```
Thanks

---

### Post by SeijiSensei on 2023-03-01
Have you done a full update of your system? Try that first before installing.
```
sudo apt update; sudo apt full-upgrade
```

---

### Post by MAFoElffen on 2023-03-02
From what I see for jammy:
```

mafoelffen@Mikes-B460M:~$ apt-cache policy mysql-server
mysql-server:
  Installed: (none)
  Candidate: 8.0.32-0ubuntu0.22.04.2
  Version table:
     8.0.32-0ubuntu0.22.04.2 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main i386 Packages
     8.0.32-0buntu0.22.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages
     8.0.28-0ubuntu4 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu jammy/main i386 Packages

```
The install candidate is 8.0.32-0ubuntu4, but somehow his was trying to install 8.0.28-0ubuntu4?
[quote=lamaja]
The following packages have unmet dependencies:
mysql-server-8.0 : Depends: mysql-server-core-8.0 (= 8.0.28-0ubuntu4) but 8.0.32-0ubuntu0.22.04.2 is to be installed
[/quote]
He said release is Ubuntu 22.04...

What happens if he pushes the 'specific' version:
```

sudo apt install mysqlserver=8.0.32-0ubuntu0.22.04.2

```
This is what I get in a dry run:
```

mafoelffen@Mikes-B460M:~$ sudo apt-get install --dry-run mysql-server=8.0.32-0ubuntu0.22.04.2
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  libcgi-fast-perl libcgi-pm-perl libevent-pthreads-2.1-7 libfcgi-bin
  libfcgi-perl libfcgi0ldbl libhtml-template-perl libmecab2 libprotobuf-lite23
  mecab-ipadic mecab-ipadic-utf8 mecab-utils mysql-client-8.0
  mysql-client-core-8.0 mysql-common mysql-server-8.0 mysql-server-core-8.0
Suggested packages:
  libipc-sharedcache-perl mailx tinyca
The following NEW packages will be installed:
  libcgi-fast-perl libcgi-pm-perl libevent-pthreads-2.1-7 libfcgi-bin
  libfcgi-perl libfcgi0ldbl libhtml-template-perl libmecab2 libprotobuf-lite23
  mecab-ipadic mecab-ipadic-utf8 mecab-utils mysql-client-8.0
  mysql-client-core-8.0 mysql-common mysql-server mysql-server-8.0
  mysql-server-core-8.0
0 upgraded, 18 newly installed, 0 to remove and 58 not upgraded.
Inst mysql-common (5.8+1.0.8 Ubuntu:22.04/jammy [all])
Inst mysql-client-core-8.0 (8.0.32-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Inst mysql-client-8.0 (8.0.32-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Inst libevent-pthreads-2.1-7 (2.1.12-stable-1build3 Ubuntu:22.04/jammy [amd64])
Inst libmecab2 (0.996-14build9 Ubuntu:22.04/jammy [amd64])
Inst libprotobuf-lite23 (3.12.4-1ubuntu7 Ubuntu:22.04/jammy [amd64])
Inst mysql-server-core-8.0 (8.0.32-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf mysql-common (5.8+1.0.8 Ubuntu:22.04/jammy [all])
Inst mysql-server-8.0 (8.0.32-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Inst libcgi-pm-perl (4.54-1 Ubuntu:22.04/jammy [all])
Inst libfcgi0ldbl (2.4.2-2build2 Ubuntu:22.04/jammy [amd64])
Inst libfcgi-perl (0.82+ds-1build1 Ubuntu:22.04/jammy [amd64])
Inst libcgi-fast-perl (1:2.15-1 Ubuntu:22.04/jammy [all])
Inst libfcgi-bin (2.4.2-2build2 Ubuntu:22.04/jammy [amd64])
Inst libhtml-template-perl (2.97-1.1 Ubuntu:22.04/jammy [all])
Inst mecab-utils (0.996-14build9 Ubuntu:22.04/jammy [amd64])
Inst mecab-ipadic (2.7.0-20070801+main-3 Ubuntu:22.04/jammy [all])
Inst mecab-ipadic-utf8 (2.7.0-20070801+main-3 Ubuntu:22.04/jammy [all])
Inst mysql-server (8.0.32-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [all])
Conf mysql-client-core-8.0 (8.0.32-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf mysql-client-8.0 (8.0.32-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf libevent-pthreads-2.1-7 (2.1.12-stable-1build3 Ubuntu:22.04/jammy [amd64])
Conf libmecab2 (0.996-14build9 Ubuntu:22.04/jammy [amd64])
Conf libprotobuf-lite23 (3.12.4-1ubuntu7 Ubuntu:22.04/jammy [amd64])
Conf mysql-server-core-8.0 (8.0.32-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf mysql-server-8.0 (8.0.32-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf libcgi-pm-perl (4.54-1 Ubuntu:22.04/jammy [all])
Conf libfcgi0ldbl (2.4.2-2build2 Ubuntu:22.04/jammy [amd64])
Conf libfcgi-perl (0.82+ds-1build1 Ubuntu:22.04/jammy [amd64])
Conf libcgi-fast-perl (1:2.15-1 Ubuntu:22.04/jammy [all])
Conf libfcgi-bin (2.4.2-2build2 Ubuntu:22.04/jammy [amd64])
Conf libhtml-template-perl (2.97-1.1 Ubuntu:22.04/jammy [all])
Conf mecab-utils (0.996-14build9 Ubuntu:22.04/jammy [amd64])
Conf mecab-ipadic (2.7.0-20070801+main-3 Ubuntu:22.04/jammy [all])
Conf mecab-ipadic-utf8 (2.7.0-20070801+main-3 Ubuntu:22.04/jammy [all])
Conf mysql-server (8.0.32-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [all])

```
Make sure he is updated to current before he tries that. That should work.

---

