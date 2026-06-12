---
title: "dpkg-buildpackage fails with JAVA_HOME error"
date: 2016-03-08
forum: General Help
---

### Post by mike_d2 on 2016-03-08
This is an OVH ubuntu 14.04 server, and I am trying to build the Bytemine Manager, which is a debian package that requires being built with dpkg-buildpackage. I have installed all the dependencies: ant, ant-optional, build-essential, dpkg-dev, and OpenJDK 64 bit server (build 24.95-b01) and set my JAVA_HOME directory in /etc/environments to /usr/lib/jvm/java-7-openjdk-amd64 which is what I thought the correct path was. Every time I try to call dpkg-buildpackage I get an error stating:
```
dpkg-buildpackage: source package bytemine-manager
dpkg-buildpackage: source version 2.3.1
dpkg-buildpackage: source distribution stable
dpkg-buildpackage: source changed by Daniel Rauer <rauer@bytemine.net>
dpkg-buildpackage: host architecture amd64
 dpkg-source --before-build bytemine-manager-master
 debian/rules clean
test -x debian/rules
You must specify a valid JAVA_HOME or JAVACMD!
make: *** [testsanity] Error 1
dpkg-buildpackage: error: debian/rules clean gave error exit status 2
rm: cannot remove ‘bytemine-manager.jar’: No such file or directory

```

---

