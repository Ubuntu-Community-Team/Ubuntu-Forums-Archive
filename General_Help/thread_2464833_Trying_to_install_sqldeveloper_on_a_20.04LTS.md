---
title: "Trying to install sqldeveloper on a 20.04LTS"
date: 2021-07-13
forum: General Help
---

### Post by draak2 on 2021-07-13
Hi,

Trying to install Oracle's SQLDeveloper package, which ends up with a brick wall called 'debhelper'.

Here is the output for the console:
```
sudo apt install sqldeveloper-package -o Debug::pkgProblemResolver=true -o Debug::Acquire::http=true
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Starting pkgProblemResolver with broken count: 1
Starting 2 pkgProblemResolver with broken count: 1
Investigating (0) libtool:amd64 < none -> 2.4.6-14 @un uN Ib >
Broken libtool:amd64 Depends on libc6-dev:amd64 < none | 2.31-0ubuntu9.2 @un uH >
  Considering libc6-dev:amd64 2 as a solution to libtool:amd64 1
  Holding Back libtool:amd64 rather than change libc6-dev:amd64
Broken libtool:amd64 Depends on libc-dev:amd64 < none @un H >
  Considering libc6-dev:amd64 2 as a solution to libtool:amd64 1
  Holding Back libtool:amd64 rather than change libc-dev:amd64
  Or group keep for libtool:amd64
Investigating (1) dh-autoreconf:amd64 < none -> 19 @un uN Ib >
Broken dh-autoreconf:amd64 Depends on libtool:amd64 < none | 2.4.6-14 @un uH > (>= 2.4.2)
  Considering libtool:amd64 1 as a solution to dh-autoreconf:amd64 2
  Holding Back dh-autoreconf:amd64 rather than change libtool:amd64
Investigating (2) debhelper:amd64 < none -> 12.10ubuntu1 @un uN Ib >
Broken debhelper:amd64 Depends on dh-autoreconf:amd64 < none | 19 @un uH > (>= 17~)
  Considering dh-autoreconf:amd64 2 as a solution to debhelper:amd64 2
  Holding Back debhelper:amd64 rather than change dh-autoreconf:amd64
Investigating (2) dh-exec:amd64 < none -> 0.23.2 @un uN Ib >
Broken dh-exec:amd64 Depends on debhelper:amd64 < none | 12.10ubuntu1 @un uH > (>= 9.20151004~)
  Considering debhelper:amd64 2 as a solution to dh-exec:amd64 -1
  Holding Back dh-exec:amd64 rather than change debhelper:amd64
Investigating (3) sqldeveloper-package:amd64 < none -> 0.5.4 @un puN Ib >
Broken sqldeveloper-package:amd64 Depends on dh-exec:amd64 < none | 0.23.2 @un uH >
  Considering dh-exec:amd64 -1 as a solution to sqldeveloper-package:amd64 9999
    Reinst Failed early because of libc6:amd64
    Reinst Failed because of libc6-dev:amd64
    Reinst Failed because of libc6-dev:amd64
    Reinst Failed because of libtool:amd64
    Reinst Failed because of dh-autoreconf:amd64
    Reinst Failed because of debhelper:amd64
  Considering dh-exec:i386 -1 as a solution to sqldeveloper-package:amd64 9999
  Re-Instated gcc-10-base:i386
  Re-Instated libgcc-s1:i386
  Re-Instated libcrypt1:i386
  Re-Instated libc6:i386
  Re-Instated libpipeline1:i386
  Re-Instated perl-base:i386
  Re-Instated libbz2-1.0:i386
  Re-Instated libdb5.3:i386
  Re-Instated libgdbm6:i386
  Re-Instated libgdbm-compat4:i386
  Re-Instated zlib1g:i386
  Re-Instated libperl5.30:i386
  Re-Instated perl:i386
    Reinst Failed because of debhelper:amd64
Investigating (3) perl-base:amd64 < 5.30.0-9ubuntu0.2 @ii mK Ib >
Broken perl-base:amd64 Conflicts on perl-base:i386 < none -> 5.30.0-9ubuntu0.2 @un uN Ib >
  Considering perl-base:i386 4999 as a solution to perl-base:amd64 5497
  Added perl-base:i386 to the remove list
  Conflicts//Breaks against version 5.30.0-9build1 for perl-base but that is not InstVer, ignoring
  Fixing perl-base:amd64 via keep of perl-base:i386
Investigating (3) perl:amd64 < 5.30.0-9ubuntu0.2 @ii mK Ib >
Broken perl:amd64 Conflicts on perl:i386 < none -> 5.30.0-9ubuntu0.2 @un uN Ib >
  Considering perl:i386 -1 as a solution to perl:amd64 340
  Added perl:i386 to the remove list
  Conflicts//Breaks against version 5.30.0-9build1 for perl but that is not InstVer, ignoring
  Fixing perl:amd64 via keep of perl:i386
Investigating (3) libc6:i386 < none -> 2.31-0ubuntu9.2 @un uN Ib >
Broken libc6:i386 Breaks on libc6:amd64 < 2.31-0ubuntu9.3 @ii mK Ib > (!= 2.31-0ubuntu9.2)
  Considering libc6:amd64 14126 as a solution to libc6:i386 0
  Holding Back libc6:i386 rather than change libc6:amd64
Investigating (3) libpipeline1:i386 < none -> 1.5.2-2build1 @un uN Ib >
Broken libpipeline1:i386 Depends on libc6:i386 < none | 2.31-0ubuntu9.2 @un uH > (>= 2.28)
  Considering libc6:i386 0 as a solution to libpipeline1:i386 0
  Holding Back libpipeline1:i386 rather than change libc6:i386
Investigating (4) sqldeveloper-package:amd64 < none -> 0.5.4 @un puN Ib >
Broken sqldeveloper-package:amd64 Depends on dh-exec:amd64 < none | 0.23.2 @un uH >
  Considering dh-exec:amd64 -1 as a solution to sqldeveloper-package:amd64 9999
  Considering dh-exec:i386 -1 as a solution to sqldeveloper-package:amd64 9999
Investigating (4) libdb5.3:i386 < none -> 5.3.28+dfsg1-0.6ubuntu2 @un uN Ib >
Broken libdb5.3:i386 Depends on libc6:i386 < none | 2.31-0ubuntu9.2 @un uH > (>= 2.28)
  Considering libc6:i386 0 as a solution to libdb5.3:i386 0
  Holding Back libdb5.3:i386 rather than change libc6:i386
Investigating (4) libgcc-s1:i386 < none -> 10.3.0-1ubuntu1~20.04 @un uN Ib >
Broken libgcc-s1:i386 Depends on libc6:i386 < none | 2.31-0ubuntu9.2 @un uH > (>= 2.2.4)
  Considering libc6:i386 0 as a solution to libgcc-s1:i386 0
  Holding Back libgcc-s1:i386 rather than change libc6:i386
Investigating (4) libgdbm6:i386 < none -> 1.18.1-5 @un uN Ib >
Broken libgdbm6:i386 Depends on libc6:i386 < none | 2.31-0ubuntu9.2 @un uH > (>= 2.28)
  Considering libc6:i386 0 as a solution to libgdbm6:i386 0
  Holding Back libgdbm6:i386 rather than change libc6:i386
Investigating (4) libgdbm-compat4:i386 < none -> 1.18.1-5 @un uN Ib >
Broken libgdbm-compat4:i386 Depends on libc6:i386 < none | 2.31-0ubuntu9.2 @un uH > (>= 2.7)
  Considering libc6:i386 0 as a solution to libgdbm-compat4:i386 0
  Holding Back libgdbm-compat4:i386 rather than change libc6:i386
Investigating (4) libbz2-1.0:i386 < none -> 1.0.8-2 @un uN Ib >
Broken libbz2-1.0:i386 Depends on libc6:i386 < none | 2.31-0ubuntu9.2 @un uH > (>= 2.4)
  Considering libc6:i386 0 as a solution to libbz2-1.0:i386 0
  Holding Back libbz2-1.0:i386 rather than change libc6:i386
Investigating (4) zlib1g:i386 < none -> 1:1.2.11.dfsg-2ubuntu1.2 @un uN Ib >
Broken zlib1g:i386 Depends on libc6:i386 < none | 2.31-0ubuntu9.2 @un uH > (>= 2.4)
  Considering libc6:i386 0 as a solution to zlib1g:i386 0
  Holding Back zlib1g:i386 rather than change libc6:i386
Investigating (4) libcrypt1:i386 < none -> 1:4.4.10-10ubuntu4 @un uN Ib >
Broken libcrypt1:i386 Depends on libc6:i386 < none | 2.31-0ubuntu9.2 @un uH > (>= 2.25)
  Considering libc6:i386 0 as a solution to libcrypt1:i386 0
  Holding Back libcrypt1:i386 rather than change libc6:i386
Investigating (4) libperl5.30:i386 < none -> 5.30.0-9ubuntu0.2 @un uN Ib >
Broken libperl5.30:i386 Depends on libbz2-1.0:i386 < none | 1.0.8-2 @un uH >
  Considering libbz2-1.0:i386 0 as a solution to libperl5.30:i386 0
  Holding Back libperl5.30:i386 rather than change libbz2-1.0:i386
Investigating (5) sqldeveloper-package:amd64 < none -> 0.5.4 @un puN Ib >
Broken sqldeveloper-package:amd64 Depends on dh-exec:amd64 < none | 0.23.2 @un uH >
  Considering dh-exec:amd64 -1 as a solution to sqldeveloper-package:amd64 9999
  Considering dh-exec:i386 -1 as a solution to sqldeveloper-package:amd64 9999
Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 sqldeveloper-package : Depends: dh-exec
E: Unable to correct problems, you have held broken packages.


```

I am relatively new to both linux and ubuntu in general, so my attempts to figure things out ended up quite fast.

I've tried installing 'alien', but at some point I get the same root cause:
```
sudo apt install alien -o Debug::pkgProblemResolver=true -o Debug::Acquire::http=true
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Starting pkgProblemResolver with broken count: 1
Starting 2 pkgProblemResolver with broken count: 1
Investigating (0) libtool:amd64 < none -> 2.4.6-14 @un uN Ib >
Broken libtool:amd64 Depends on libc6-dev:amd64 < none | 2.31-0ubuntu9.2 @un uH >
  Considering libc6-dev:amd64 2 as a solution to libtool:amd64 1
  Holding Back libtool:amd64 rather than change libc6-dev:amd64
Broken libtool:amd64 Depends on libc-dev:amd64 < none @un H >
  Considering libc6-dev:amd64 2 as a solution to libtool:amd64 1
  Holding Back libtool:amd64 rather than change libc-dev:amd64
  Or group keep for libtool:amd64
Investigating (1) dh-autoreconf:amd64 < none -> 19 @un uN Ib >
Broken dh-autoreconf:amd64 Depends on libtool:amd64 < none | 2.4.6-14 @un uH > (>= 2.4.2)
  Considering libtool:amd64 1 as a solution to dh-autoreconf:amd64 2
  Holding Back dh-autoreconf:amd64 rather than change libtool:amd64
Investigating (2) debhelper:amd64 < none -> 12.10ubuntu1 @un uN Ib >
Broken debhelper:amd64 Depends on dh-autoreconf:amd64 < none | 19 @un uH > (>= 17~)
  Considering dh-autoreconf:amd64 2 as a solution to debhelper:amd64 2
  Holding Back debhelper:amd64 rather than change dh-autoreconf:amd64
Investigating (3) alien:amd64 < none -> 8.95 @un puN Ib >
Broken alien:amd64 Depends on debhelper:amd64 < none | 12.10ubuntu1 @un uH > (>= 7)
  Considering debhelper:amd64 2 as a solution to alien:amd64 9999
    Reinst Failed early because of libc6:amd64
    Reinst Failed because of libc6-dev:amd64
    Reinst Failed because of libc6-dev:amd64
    Reinst Failed because of libtool:amd64
    Reinst Failed because of dh-autoreconf:amd64
Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 alien : Depends: debhelper (>= 7) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

