---
title: "JRE dependencies"
date: 2012-11-25
forum: General Help
---

### Post by tech7 on 2012-11-25
I've been trying to install the newer version of netbeans php ide.  However, the jre is not installed and when I try to install it, I get the following message:

```

The following packages have unmet dependencies:

openjdk-6-jre: Depends: openjdk-6-jre-headless (>= 6b24-1.11.1-4ubuntu2) but 6b24-1.11.1-4ubuntu2 is to be installed
               Depends: libjpeg8 (>= 8c) but 8c-2ubuntu7 is to be installed
               Depends: libpulse0 (>= 1:0.99.1) but 1:1.1-0ubuntu15.1 is to be installed



```

I cannot locate the packages in synaptic, software center, or via apt-get in terminal.  

Does anybody have any useful tips for ideas for getting JRE 6 or 7 to install?

---

### Post by rai4shu2 on 2012-11-26
Okay, so you're using 12.04? And you just want "netbeans"?

```
$ apt-cache show netbeans
Package: netbeans
Priority: optional
Section: universe/java
Installed-Size: 1918
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Java Maintainers <pkg-java-maintainers@lists.alioth.debian.org>
Architecture: all
Version: 7.0.1+dfsg1-4
Replaces: netbeans-ide, netbeans5.5
Provides: netbeans-ide
Depends: libnb-platform13-java (>= 7.0), openjdk-6-jdk | java6-sdk | java7-sdk, libnb-ide14-java (= 7.0.1+dfsg1-4), libnb-java5-java (= 7.0.1+dfsg1-4), libnb-apisupport3-java (= 7.0.1+dfsg1-4)
Conflicts: netbeans-ide, netbeans5.5
Filename: pool/universe/n/netbeans/netbeans_7.0.1+dfsg1-4_all.deb
Size: 897978
MD5sum: 7c3f56be71f23d3fc70d0da76a33b552
SHA1: 6695e4511fb28c7dfa7f78816691d0096a300f36
SHA256: b7c94b59e9a2659efb7a4caf7bb59ea85a95d22ae4f92fc7f8a0c15775e26513
Description-en: Extensible Java IDE
 Integrated Development Environment for software developers. It supports
 development of desktop, enterprise, web, and mobile applications. Package
 includes the Base IDE, Java Development Tools and Plug-in Development Tools.
 Support for PHP, Ruby, C/C++, Java EE and others can be added.
Homepage: http://netbeans.org/
Description-md5: 26e2554fdd9aea3a39bf374f2f9703d0
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
```

---

