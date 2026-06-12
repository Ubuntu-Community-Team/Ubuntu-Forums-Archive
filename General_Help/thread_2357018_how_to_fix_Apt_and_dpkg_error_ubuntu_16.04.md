---
title: "how to fix Apt and dpkg error? ubuntu 16.04"
date: 2017-03-29
forum: General Help
---

### Post by evelyn.bonbon on 2017-03-29
i have ubuntu 16.04 and i cannot install applications (anything).
it always says:

```
dpkg: error processing package apt (--configure):
 package apt is not ready for configuration
 cannot configure (current status 'half-installed')
Errors were encountered while processing:
 apt
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

how to solve this? i tried googling and all the article to do 
```
sudo apt-get install -f
```
or remove the package name. but i can install anything so no package name installed.

here my result for apt-get install -f
```
bonbon@bonbon:~$ sudo apt-get install -f
[sudo] password for bonbon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 439 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1.052 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: error processing package apt (--configure):
 package apt is not ready for configuration
 cannot configure (current status 'half-installed')
Errors were encountered while processing:
 apt
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

what should i do? help.

Ps: ubuntu 16.04 is my first Linux. Thank you

---

### Post by ajgreeny on 2017-03-29
Is this a new problem on a system that has been working or have you never been able to use apt, apt-get or dpkg?
If the problem has suddenly occurred what were you doing when you first encountered it; what were you trying to install or upgrade?

What does command ```
dpkg -s apt dpkg
``` show as output, if anything?
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by lazyoga on 2017-05-01
> **ajgreeny said:**
> Is this a new problem on a system that has been working or have you never been able to use apt, apt-get or dpkg?
If the problem has suddenly occurred what were you doing when you first encountered it; what were you trying to install or upgrade?

What does command ```
dpkg -s apt dpkg
``` show as output, if anything?
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

I got the same error after the interrupted/failed installation of a local language pack. I did the same through the graphical installer.

Here is what it throws when I execute the **dpkg -s apt dpkg**:

```
Package: apt
Status: install ok installed
Priority: important
Section: admin
Installed-Size: 3309
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 1.2.20
Replaces: bash-completion (<< 1:2.1-4.2+fakesync1), manpages-it (<< 2.80-4~), manpages-pl (<< 20060617-3~), openjdk-6-jdk (<< 6b24-1.11-0ubuntu1~), sun-java5-jdk (>> 0), sun-java6-jdk (>> 0)
Depends: libapt-pkg5.0 (>= 1.2.20), libc6 (>= 2.15), libgcc1 (>= 1:4.2), libstdc++6 (>= 5.2), init-system-helpers (>= 1.18~), ubuntu-keyring, gpgv | gpgv2, gnupg | gnupg2, adduser
Suggests: aptitude | synaptic | wajig, dpkg-dev (>= 1.17.2), apt-doc, python-apt
Breaks: apt-utils (<< 1.1.3), manpages-it (<< 2.80-4~), manpages-pl (<< 20060617-3~), openjdk-6-jdk (<< 6b24-1.11-0ubuntu1~), sun-java5-jdk (>> 0), sun-java6-jdk (>> 0)
Conffiles:
 /etc/apt/apt.conf.d/01-vendor-ubuntu 5232396660502461fc834c0a1229dbe4
 /etc/apt/apt.conf.d/01autoremove 0b1391c01d75f95fa4ea5ac01219b515
 /etc/cron.daily/apt-compat bc4a71cbcaeed4179f25d798257fa980
 /etc/kernel/postinst.d/apt-auto-removal 8ad76ae4492b54f0dcbf18c79429dfab
 /etc/logrotate.d/apt 179f2ed4f85cbaca12fa3d69c2a4a1c3
Description: commandline package manager
 This package provides commandline tools for searching and
 managing as well as querying information about packages
 as a low-level access to all features of the libapt-pkg library.
 .
 These include:
  * apt-get for retrieval of packages and information about them
    from authenticated sources and for installation, upgrade and
    removal of packages together with their dependencies
  * apt-cache for querying available information about installed
    as well as installable packages
  * apt-cdrom to use removable media as a source for packages
  * apt-config as an interface to the configuration settings
  * apt-key as an interface to manage authentication keys
Original-Maintainer: APT Development Team <deity@lists.debian.org>

Package: dpkg
Essential: yes
Status: install ok installed
Priority: required
Section: admin
Installed-Size: 6704
Origin: debian
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Bugs: debbugs://bugs.debian.org
Architecture: i386
Multi-Arch: foreign
Version: 1.18.4ubuntu1.2
Replaces: manpages-it (<< 2.80-4)
Pre-Depends: libbz2-1.0, libc6 (>= 2.11), liblzma5 (>= 5.1.1alpha+20120614), libselinux1 (>= 2.3), zlib1g (>= 1:1.1.4), tar (>= 1.23)
Suggests: apt
Breaks: apt (<< 0.7.7~), apt-cudf (<< 3.3~beta1-3~), aptitude (<< 0.4.7-1~), auctex (<< 11.87-3+deb8u1~), ccache (<< 3.1.10-1~), cups (<< 1.7.5-10~), dbus (<< 1.8.12-1ubuntu6~), debian-security-support (<< 2014.10.26~), distcc (<< 3.1-6.1~), doc-base (<< 0.10.5~), dpkg-dev (<< 1.15.8), fontconfig (<< 2.11.1-0ubuntu5~), fusionforge-plugin-mediawiki (<< 5.3.2+20141104-3~), gap-core (<< 4r7p5-2~), gitweb (<< 1:2.1.4-2.1~), grace (<< 1:5.1.24-3~), gxine (<< 0.5.908-3.1~), hoogle (<< 4.2.33-4~), icecc (<< 1.0.1-2~), install-info (<< 5.1.dfsg.1-3~), libapache2-mod-php5 (<< 5.6.4+dfsg-3~), libapache2-mod-php5filter (<< 5.6.4+dfsg-3~), libdpkg-perl (<< 1.15.8), libjs-protoaculous (<< 5~), man-db (<< 2.6.3-6~), mcollective (<< 2.6.0+dfsg-2.1~), php5-fpm (<< 5.6.4+dfsg-3~), pypy (<< 2.4.0+dfsg-3~), readahead-fedora (<< 2:1.5.6-5.2~), software-center (<< 13.10-0ubuntu9~), ufw (<< 0.35-0ubuntu2~), ureadahead (<< 0.100.0-17~), wordpress (<< 4.1+dfsg-1~), xfonts-traditional (<< 1.7~), xine-ui (<< 0.99.9-1.2~)
Conflicts: ada-reference-manual (<< 20021112web-4~), asn1-mode (<< 2.7-7~), bogosort (<< 0.4.2-3~), cl-yacc (<< 0.3-3~), cpp-4.1-doc (<< 4.1.2.nf2-4~), cpp-4.2-doc (<< 4.2.4.nf1-4~), gcc-4.1-doc (<< 4.1.2.nf2-4~), gcc-4.2-doc (<< 4.2.4.nf1-4~), gcj-4.1-doc (<< 4.1.2.nf2-4~), gcj-4.2-doc (<< 4.2.4.nf1-4~), gfortran-4.1-doc (<< 4.1.2.nf2-4~), gfortran-4.2-doc (<< 4.2.4.nf1-4~), ggz-docs (<< 0.0.14.1-2~), glame (<< 2.0.1-6~), gnat-4.1-doc (<< 4.1.2.nf2-4~), gnat-4.2-doc (<< 4.2.4.nf1-4~), gtalk (<< 0.99.10-16~), libalogg-dev (<< 1.3.7-2~), libgtk1.2-doc (<< 1.2.10-19~), libnettle-dev (<< 2~), liborbit-dev (<< 0.5.17-12~), libreadline5-dev (<< 5.2-8~), librep-doc (<< 0.90~), mmucl (<< 1.5.2-3~), nxml-mode (<< 20041004-9~), octave3.0-info (<< 1:3.0.5-7+rm), octave3.2-info (<< 3.2.4-12+rm), polgen-doc (<< 1.3-3+rm), r6rs-doc (<< 1.0-2~), serveez-doc (<< 0.1.5-3~), slat (<< 2.0-6~), texlive-base-bin-doc (<< 2007.dfsg.2-9~), ttcn-el (<< 0.6.9-2~), ulog-acctd (<< 0.4.3-3~), xconq-doc (<< 7.4.1-5~), zenirc (<< 2.112.dfsg-1~)
Conffiles:
 /etc/alternatives/README 69c4ba7f08363e998e0f2e244a04f881
 /etc/cron.daily/dpkg b8065b6bfc248caba501c3f5bb508e66
 /etc/dpkg/dpkg.cfg f4413ffb515f8f753624ae3bb365b81b
 /etc/logrotate.d/dpkg 782ea5ae536f67ff51dc8c3e2eeb4cf9
Description: Debian package management system
 This package provides the low-level infrastructure for handling the
 installation and removal of Debian software packages.
 .
 For Debian package development tools, install dpkg-dev.
Homepage: https://wiki.debian.org/Teams/Dpkg
Original-Maintainer: Dpkg Developers <debian-dpkg@lists.debian.org>

```

Any suggestion/solution would be appreciated. Thanks in advance.

---

