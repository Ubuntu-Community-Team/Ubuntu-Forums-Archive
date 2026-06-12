---
title: "apt-get &amp; vsftpd"
date: 2013-03-20
forum: General Help
---

### Post by ndusr on 2013-03-20
I have inherited a system with Ubuntu 8.04, and I'm working with vsftpd.  I'm having a problem with it and I want to be sure I have the latest version.  Here's what I see:
```
ndusr@ftp:~$ dpkg -s vsftpdPackage: vsftpd
Status: install ok installed
Priority: extra
Section: net
Installed-Size: 396
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 2.0.6-1ubuntu1.2
Provides: ftp-server
Depends: adduser, libc6 (>= 2.4), libcap1, libpam-modules, libpam0g (>= 0.99.7.1), libssl0.9.8 (>= 0.9.8f-1), libwrap0, lsb-base (>= 1.3-9ubuntu3), netbase, ssl-cert (>= 1.0-11ubuntu1), sysv-rc (>= 2.86.ds1-14.1ubuntu2), update-inetd
Recommends: logrotate
Conflicts: ftp-server
Conffiles:
 /etc/init.d/vsftpd c66e30cd4415701071de757f39e5cc24
 /etc/pam.d/vsftpd 6153c5fb6ac31f73553f0a02feaaab3b
 /etc/logrotate.d/vsftpd d1db1f8a362fad77f4f28b2a67443764
 /etc/vsftpd.conf 71e44babc55664dec72fb1e6118557ce
 /etc/ftpusers 839f3157aad792bafbbdcd932a95a345
Description: The Very Secure FTP Daemon
 A lightweight, efficient FTP server written from the ground up with
 security in mind.
 .
 vsftpd supports both anonymous and non-anonymous FTP, PAM authentication,
 bandwidth limiting, and the Linux sendfile() facility.
Original-Maintainer: Matej Vela <vela@debian.org>

```

This says to me I have version 2.0.6 (!?) - I know the latest is >3.  I've tried `apt-get update && apt-get upgrade`, but it doesn't appear to touch vsftpd.  Maybe my sources aren't getting updated?

Any help would be appreciated.

---

### Post by dabl on 2013-03-20
There is a total disconnect between running version 8.04 and wanting the latest version of anything.   =;

Support for 8.04 desktop ended [**[color=green]12 May 2011[/color]**](https://wiki.ubuntu.com/Releases).  So your system does not have the libraries and dependencies required to support the latest version of any packages.  According to my 12.10 system, the currently available version of vsftpd from the standard repos is 

```
don@ubuntu:~$ sudo apt-cache policy vsftpd
vsftpd:
  Installed: (none)
  Candidate: 2.3.5-3ubuntu1
  Version table:
     2.3.5-3ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
```

You are going to have to do a version upgrade (actually several version upgrades) of your system before you can get a newer version of vsftpd.  Instructions to upgrade the version are [**[color=green]here[/color]**](https://help.ubuntu.com/community/UpgradeNotes).

---

### Post by gordintoronto on 2013-03-20
You could get the latest version from here: [https://security.appspot.com/vsftpd.html#download](https://security.appspot.com/vsftpd.html#download)

However, it might not work on a version of Linux which will be five years old in a couple of weeks.

If the computer has sufficient specs, you could download and install Ubuntu 12.04 LTS, or Kubuntu, Lubuntu, Xubuntu. The current Ubuntu really would like to have 1 GB of memory, Lubuntu should be fine with 512 MB. Old CPUs are generally OK, not enough memory is a deal breaker.

There have been several security updates since support was dropped for 8.04, so it's not a good idea to continue using it.

---

