---
title: "Spotify client doesn't start"
date: 2015-08-20
forum: General Help
---

### Post by checoimg on 2015-08-20
I installed Spotify from the repositories and the program doesn't start. When I try to run from the terminal it shows this message : 

spotify: error while loading shared libraries: libgcrypt.so.11: cannot open shared object file: No such file or directory

---

### Post by checoimg on 2015-08-20
Sorry just remembered this not official repos

---

### Post by Toz on 2015-08-20
> **checoimg said:**
> Sorry just remembered this not official repos

Where did you get spotify from?

What version of ubuntu are you running? 32-bit or 64-bit?

Is libgcrypt installed? If so, which version:
```
apt-cache policy libgcrypt
```

If you're running a later version of Ubuntu (15.04 or later), libgcrypt was updated to version 2.0 and spotify requires version 1.1. The fix in this case can be found [here](http://thehumble.ninja/2015/04/21/installing-spotify-in-ubuntu-15-04/).

---

### Post by checoimg on 2015-08-21
I'm on Ubuntu 15.04 64 bit.

 "aptitude search libgcrypt" shows the following output :

v   libgcrypt-dev                   -                                           
v   libgcrypt-dev:i386              -                                           
p   libgcrypt11-dev                 - transitional libgcrypt11-dev package      
i   libgcrypt20                     - LGPL Crypto library - runtime library     
i A libgcrypt20:i386                - LGPL Crypto library - runtime library     
p   libgcrypt20-dbg                 - LGPL Crypto library - debugger files      
p   libgcrypt20-dbg:i386            - LGPL Crypto library - debugger files      
p   libgcrypt20-dev                 - LGPL Crypto library - development files   
p   libgcrypt20-dev:i386            - LGPL Crypto library - development files   
p   libgcrypt20-doc                 - LGPL Crypto library - documentation


"apt-cache policy libgcrypt" gives :

N: Unable to locate package libgcrypt

"apt-cache policy libgcrypt20" shows :

libgcrypt20:
  Installed: 1.6.2-4ubuntu2
  Candidate: 1.6.2-4ubuntu2
  Version table:
 *** 1.6.2-4ubuntu2 0
        500 [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) vivid/main amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by checoimg on 2015-08-21
The fix worked!! :D, I'll leave the fix here

```
$ wget http://security.ubuntu.com/ubuntu/pool/main/libg/libgcrypt11/libgcrypt11_1.5.4-2ubuntu1.1_amd64.deb
$ sudo dpkg -i libgcrypt11_1.5.4-2ubuntu1.1_amd64.deb
```

---

### Post by mollie4168 on 2015-11-11
I'm having the same problem with Spotify not starting.  Here's my output from running the above in terminal: 

[HTML]tracy@tracy:~$ spotify
spotify: error while loading shared libraries: libgcrypt.so.11: cannot open shared object file: No such file or directory
tracy@tracy:~$ apt-cache policy libcrypt
N: Unable to locate package libcrypt
tracy@tracy:~$ wget http://security.ubuntu.com/ubuntu/pool/main/libg/libgcrypt11/libgcrypt11_1.5.4-2ubuntu1.1_amd64.deb
--2015-11-11 17:33:49--  http://security.ubuntu.com/ubuntu/pool/main/libg/libgcrypt11/libgcrypt11_1.5.4-2ubuntu1.1_amd64.deb
Resolving security.ubuntu.com (security.ubuntu.com)... 2001:67c:1562::17, 2001:67c:1360:8c01::18, 2001:67c:1562::13, ...
Connecting to security.ubuntu.com (security.ubuntu.com)|2001:67c:1562::17|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2015-11-11 17:33:49 ERROR 404: Not Found.[/HTML]

---

### Post by vincentertainment on 2016-01-05
I got the same error as Molly. I'm running 15.10

---

### Post by ian-weisser on 2016-01-06
libgcrypt11 was superseded by libgcrypt20 from the Ubuntu repositories during 14.04. Replaced in Debian, too.

```
$ rmadison libgcrypt11
 libgcrypt11 | 1.5.0-3          | precise          | source, amd64, armel, armhf, i386, powerpc
 libgcrypt11 | 1.5.0-3ubuntu0.4 | precise-security | source, amd64, armel, armhf, i386, powerpc
 libgcrypt11 | 1.5.0-3ubuntu0.4 | precise-updates  | source, amd64, armel, armhf, i386, powerpc
 libgcrypt11 | 1.5.3-2ubuntu4   | trusty           | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 libgcrypt11 | 1.5.3-2ubuntu4.2 | trusty-security  | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 libgcrypt11 | 1.5.3-2ubuntu4.2 | trusty-updates   | source, amd64, arm64, armhf, i386, powerpc, ppc64el
```

I don't know where you got that Spotify client from, but go back there and tell them to stop living in the past. You need a verion that uses libgcrypt20.

---

### Post by jim_deadlock on 2016-01-06
I just go to [https://play.spotify.com/browse](https://play.spotify.com/browse) it's much less hassle.

---

