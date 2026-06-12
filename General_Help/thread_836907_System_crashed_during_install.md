---
title: "System crashed during install"
date: 2008-06-22
forum: General Help
---

### Post by henrismail on 2008-06-22
I was installing updates on my computer when my computer crashed, and upon boot up it said low graphics only or something. Know my screen resloution is low and it wouldnt alow me to change and when running synaptic it says

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

when runing dpkg --configure -a under sudo it says 
```

dpkg: parse error, in file `/var/lib/dpkg/updates/0013' near line 17 package `apache2':
 EOF after field name `'
```

Please help, thank you in advance.

---

### Post by PmDematagoda on 2008-06-22
Can you post the output of:-
```
cat /var/lib/dpkg/updates/0013
```

---

### Post by henrismail on 2008-06-22
sure 
```
Package: apache2
Status: install ok unpacked
Priority: optional
Section: web
Installed-Size: 100
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Version: 2.2.8-1ubuntu0.2
Config-Version: 2.2.8-1
Depends: apache2-mpm-worker (>= 2.2.8-1ubuntu0.2) | apache2-mpm-prefork (>= 2.2.8-1ubuntu0.2) | apache2-mpm-event (>= 2.2.8-1ubuntu0.2)
Description: Next generation, scalable, extendable web server
 Apache v2 is the next generation of the omnipresent Apache web server. This
 version - a total rewrite - introduces many new improvements, such as
 threading, a new API, IPv6 support, request/response filtering, and more.
Homepage: http://httpd.apache.org/
Original-Maintainer: Debian Apache Maintainers <debian-apache@lists.debian.org>

```

---

### Post by PmDematagoda on 2008-06-22
Well, there doesn't seem to be anything wrong, but try and delete it, but first make a backup of it with(the below command will move it, so no need to remove it):-
```
sudo mv /var/lib/dpkg/updates/0013 ~/0013.bak
```
then try executing:-
```
sudo dpkg --configure -a
```
again.

---

### Post by henrismail on 2008-06-22
OK after that 
```
dpkg: parse error, in file `/var/lib/dpkg/updates/0014' near line 17 package `apache2':
 EOF after field name `'

```

---

### Post by PmDematagoda on 2008-06-22
Post the output of:-
```
ls /var/lib/dpkg/updates/
```

---

### Post by henrismail on 2008-06-22
That gives 
```

henri@henri-desktop:~$ ls /var/lib/dpkg/updates/
0000  0003  0006  0009  0012  0016  0019  0022  0025  0028  0031  0034  0037
0001  0004  0007  0010  0014  0017  0020  0023  0026  0029  0032  0035  tmp.i
0002  0005  0008  0011  0015  0018  0021  0024  0027  0030  0033  0036

```

---

