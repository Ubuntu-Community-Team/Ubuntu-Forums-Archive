---
title: "Repeated output with apt-cache show"
date: 2013-12-23
forum: General Help
---

### Post by vasa1 on 2013-12-23
When I run
**apt-cache show nginx**
I get
```
Package: nginx
Priority: optional
Section: universe/web
Installed-Size: 90
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Kartik Mistry <kartik@debian.org>
Architecture: all
Version: 1.4.1-3ubuntu1
Depends: nginx-full | nginx-light
Filename: pool/universe/n/nginx/nginx_1.4.1-3ubuntu1_all.deb
Size: 5854
MD5sum: ac2892b64e0ceb6b4a02b4371ab9559c
SHA1: 33eac40815bb96a58b001902b9cc4f7bfb866cd3
SHA256: 4ecacf3682e7ec4903cb8dcb752c9a3d3fa80811447dfc6a23e803c460bc663e
Description-en: small, powerful, scalable web/proxy server
 Nginx ("engine X") is a high-performance web and reverse proxy server
 created by Igor Sysoev. It can be used both as a standalone web server
 and as a proxy to reduce the load on back-end HTTP or mail servers.
 .
 This is a dependency package to install either nginx-full (by default) or
  nginx-light.
Description-md5: 19a4ea43e33eae4a46abf8a78966deb5
Homepage: http://nginx.net
Description-md5: 19a4ea43e33eae4a46abf8a78966deb5
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```but it's printed *twice*. The same happens with **apt-cache show firefox**.

Other ones work fine: **apt-cache show** with geany or gedit or medit or google-chrome-stable give the data just once (as expected).

Does anyone else see the same?

This is on 13.10.

---

### Post by bapoumba on 2013-12-23
Just tested with firefox, yes, it outputs twice ..
Edit1 : ```
dpkg --print-avail firefox
``` has only one output.
Edit2 : [http://lists.debian.org/deity/2001/04/msg00038.html](http://lists.debian.org/deity/2001/04/msg00038.html). Old thread but Matt Zimmerman says : "Note that both erlang and erlang-base appear twice (apparently because they exist both in non-US and in the main archive)" so I guess it could be normal :)

---

### Post by deadflowr on 2013-12-23
How many are listed when you run
apt-cache policy "package" ?

---

### Post by vasa1 on 2013-12-23
> **deadflowr said:**
> How many are listed when you run
apt-cache policy "package" ?
The double ones show two and the single ones show one:
```
[09:57 PM] ~ $ apt-cache policy nginx
nginx:
  Installed: (none)
  Candidate: 1.4.1-3ubuntu1.1
  Version table:
     1.4.1-3ubuntu1.1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy-updates/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu/ saucy-security/universe amd64 Packages
     1.4.1-3ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
[09:57 PM] ~ $ apt-cache policy firefox
firefox:
  Installed: (none)
  Candidate: 26.0+build2-0ubuntu0.13.10.2
  Version table:
     26.0+build2-0ubuntu0.13.10.2 0
        500 http://archive.ubuntu.com/ubuntu/ saucy-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu/ saucy-security/main amd64 Packages
     24.0+build1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main amd64 Packages
[09:57 PM] ~ $ apt-cache policy geany
geany:
  Installed: 1.23.1+dfsg-1
  Candidate: 1.23.1+dfsg-1
  Version table:
 *** 1.23.1+dfsg-1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
        100 /var/lib/dpkg/status
[09:57 PM] ~ $ apt-cache policy gedit
gedit:
  Installed: (none)
  Candidate: 3.8.3-0ubuntu3
  Version table:
     3.8.3-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main amd64 Packages

```
Don't quite know what to say but it's nice that it's *not just me* :)

---

### Post by vasa1 on 2013-12-23
> **bapoumba said:**
> Just tested with firefox, yes, it outputs twice ..
Edit1 : ```
dpkg --print-avail firefox
``` has only one output.
Edit2 : [http://lists.debian.org/deity/2001/04/msg00038.html](http://lists.debian.org/deity/2001/04/msg00038.html). Old thread but Matt Zimmerman says : "Note that both erlang and erlang-base appear twice (apparently because they exist both in non-US and in the main archive)" so I guess it could be normal :)
Yes, in the present case, they're in saucy-updates and in saucy-security.

I thought I had messed up something because I'm learning a bit about Bash and maybe some command I entered did something weird when I wasn't looking ;)

---

### Post by bapoumba on 2013-12-23
> **vasa1 said:**
> Yes, in the present case, they're in saucy-updates and in saucy-security.

I thought I had messed up something because I'm learning a bit about Bash and maybe some command I entered did something weird when I wasn't looking ;)

Eheh, I do not think you have messed up anything, or we have both :)

---

