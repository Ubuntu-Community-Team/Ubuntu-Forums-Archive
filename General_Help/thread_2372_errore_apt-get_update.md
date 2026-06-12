---
title: "errore apt-get update"
date: 2004-10-27
forum: General Help
---

### Post by emamarro on 2004-10-27
i always get this error...what can i do?
thank you
ciaoo

root@ubuntu:/home/ema # apt-get update
Err [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages
  Temporary failure resolving 'ftp.nerim.net'
Err [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Packages
  Temporary failure resolving 'security.ubuntu.com'
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Release [102B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Packages
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Release [108B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Sources
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Release [104B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Sources
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Release [110B]
Get:5 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Release
Ign [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Packages
  Temporary failure resolving 'archive.ubuntu.com'
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Packages [483kB]
99% [6 Packages gzip 0] [Waiting for headers]                          68B/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Packages
  Sub-process gzip returned an error code (1)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Pac

---

### Post by Rancoras on 2004-10-27
First glance looks like you have some DNS problems.  Can you browse web sites ok?

---

### Post by jdong on 2004-10-27
Not just DNS, your computer seems to be downloading corrupt files (input not in gzip format!)

Are you behind a corporate network or proxy, by any chance?

---

### Post by emamarro on 2004-10-28
by firefox i can  normally browsing web even if i close it and reopen it i have to restart connection by pon. 
I must say i had troubles to set dsl connection as i found on an italian forum, ubuntu is using a file ppp same in sid which was giving problems overwriting  DNS in resolv.conf  This has been fixed in sid and i was suggested to update ppp and pppoeconf using unstable repository.Unfortunately i was never able to do this as explained in the thread:-((

the connection is a normal dsl no proxy,never problem on libranet 2.8.1 kernel 2.4.
thanks& ciaoo

---

