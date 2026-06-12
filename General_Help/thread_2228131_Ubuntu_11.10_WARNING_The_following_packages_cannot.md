---
title: "Ubuntu 11.10 WARNING: The following packages cannot be authenticated!"
date: 2014-06-05
forum: General Help
---

### Post by kgordon-0 on 2014-06-05
Most packages provide this warning:

[EMAIL="root@kgwebsite:/"]root@kgwebsite:/[/EMAIL]# apt-get install exim4
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  exim4
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,872 B of archives.
After this operation, 61.4 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  exim4
Install these packages without verification [y/N]? y
Err [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) oneiric-updates/main exim4 all 4.76-2ubuntu1.1
  404  Not Found
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security/main exim4 all 4.76-2ubuntu1.1
  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/exim4/exim4_4.76-2ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/e/exim4/exim4_4.76-2ubuntu1.1_all.deb)  404  Not Found [IP: 91.189.91.13 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


I have tried: "apt-get update or try with --fix-missing" and key...
Tried [http://ubuntuforums.org/showthread.php?t=304430](http://ubuntuforums.org/showthread.php?t=304430) apt-get update -o Acquire::http::No-Cache=True
There are lots of threads. Any advice would be much appreciated.

---

### Post by Frogs Hair on 2014-06-05
Hello and Welcome 

11.10 is no longer supported and the repositories closed. Consider installing 12.04 or 14.04.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by kgordon-0 on 2014-06-05
Can I use **do**-***release***-***upgrade***?

---

### Post by 3rdalbum on 2014-06-06
You can try it if you want, but I don't think it will work on an unsupported Ubuntu.

---

