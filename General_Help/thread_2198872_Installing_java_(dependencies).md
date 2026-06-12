---
title: "Installing java (dependencies)"
date: 2014-01-11
forum: General Help
---

### Post by iRbeastware on 2014-01-11
Hello, I am stuck with a java install




root@rf-System-Product-Name:/home/rf/Desktop# rpm -ivh java.rpm
rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
error: Failed dependencies:
    /bin/basename is needed by jre-1.7.0_45-fcs.x86_64
    /bin/cat is needed by jre-1.7.0_45-fcs.x86_64
    /bin/cp is needed by jre-1.7.0_45-fcs.x86_64
    /bin/gawk is needed by jre-1.7.0_45-fcs.x86_64
    /bin/grep is needed by jre-1.7.0_45-fcs.x86_64
    /bin/ln is needed by jre-1.7.0_45-fcs.x86_64
    /bin/ls is needed by jre-1.7.0_45-fcs.x86_64
    /bin/mkdir is needed by jre-1.7.0_45-fcs.x86_64
    /bin/mv is needed by jre-1.7.0_45-fcs.x86_64
    /bin/pwd is needed by jre-1.7.0_45-fcs.x86_64
    /bin/rm is needed by jre-1.7.0_45-fcs.x86_64
    /bin/sed is needed by jre-1.7.0_45-fcs.x86_64
    /bin/sort is needed by jre-1.7.0_45-fcs.x86_64
    /bin/touch is needed by jre-1.7.0_45-fcs.x86_64
    /usr/bin/cut is needed by jre-1.7.0_45-fcs.x86_64
    /usr/bin/dirname is needed by jre-1.7.0_45-fcs.x86_64
    /usr/bin/expr is needed by jre-1.7.0_45-fcs.x86_64
    /usr/bin/find is needed by jre-1.7.0_45-fcs.x86_64
    /usr/bin/tail is needed by jre-1.7.0_45-fcs.x86_64
    /usr/bin/tr is needed by jre-1.7.0_45-fcs.x86_64
    /usr/bin/wc is needed by jre-1.7.0_45-fcs.x86_64
    /bin/sh is needed by jre-1.7.0_45-fcs.x86_64

I updated the rpms after by using apt-get upgrade rpm (I think). it's my first day on linux, but hey I love it so far.

Would appreciate if any experienced guys could advise me on what I should be doing to install java successfully.

---

### Post by monkeybrain20122 on 2014-01-11
rpm?? What are you talking about? What is your OS?

In Ubuntu you just install java from the package manager and the Debian/Ubuntu equivalent to rpm command is dpkg. You must be reading some instructions for redhat/fedora Linux.

---

### Post by claracc on 2014-01-11
Are you using ubuntu?, if so, the executable files are .deb not .rpm.

For installing oracle java, the best way is using webup8 repository, you will also receive automatic updates.

Please, see this link: [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html) with step by step instructions to install oracle java.

---

### Post by iRbeastware on 2014-01-11
Thank you very much, I installed it so fast. Thanks!

---

### Post by claracc on 2014-01-11
You are very welcome.

Please, mark the thread as solved with thread tools.

Thanks

---

