---
title: "trying to fix broken count with java"
date: 2015-01-30
forum: General Help
---

### Post by brigz on 2015-01-30
im not sure how to fix the problem, tied using apt-get/install, still not working, it came up with an install prompt and i typed yes and got this.


(Reading database ... 171554 files and directories currently installed.)
Preparing to unpack .../openjdk-7-jre-headless_7u75-2.5.4-1~trusty1_amd64.deb ...
Unpacking openjdk-7-jre-headless:amd64 (7u75-2.5.4-1~trusty1) over (7u71-2.5.3-0ubuntu0.14.04.1) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/openjdk-7-jre-headless_7u75-2.5.4-1~trusty1_amd64.deb (--unpack):
 cannot copy extracted data for './usr/lib/jvm/java-7-openjdk-amd64/jre/lib/rt.jar' to '/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/rt.jar.dpkg-new': unexpected end of file or stream
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Xanthius on 2015-01-30
First of all, the "headless" tag is mainly for linux installations without a graphical environment and only work in a shell (a.k.a servers). 

If you want to do these things more simpler, try opening up the ubuntu software center from the dash and search for java.
There you can choose between the Open JDK 6 and 7.

If you want the Oracle Java 8 version, you need to do this from the terminal.
[http://askubuntu.com/questions/464755/how-to-install-openjdk-8-on-14-04-lts](http://askubuntu.com/questions/464755/how-to-install-openjdk-8-on-14-04-lts)

---

### Post by Impavidus on 2015-01-31
I assume the openjdk-7-jre-headless package is pulled in as a dependency of higher level java packages.

It appears you have a corrupt download. Try clearing the cache```
sudo apt-get clear
```and try again.

---

