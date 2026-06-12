---
title: "Ubuntu 12.04LTS Samba works after upgrade, with errors"
date: 2014-02-10
forum: General Help
---

### Post by Old_Brewer on 2014-02-10
I upgraded from 10.04LTS to 12.04LTS.  I was asked during the upgrade a Samba question, something like, do you want to keep the original settings.  I said yes.  The log file had several Samba errors.  Whenever any standard package upgrade is done, I get a Samba error mesage.  I have attached it.  I am able to print from Ubuntu to the printers attached to the 2 Windows computers.  I can also see and  open the files on the 2 Windows computers.  I would like to cleanup the error messages.  All help will be appreciated.  Here is the most recent Samba error message:

```
installArchives() failed: dpkg: warning: parsing file '/var/lib/dpkg/status' near line 42566 package 'avg75fld':  
 error in Version string '7.5.51_a1243': invalid character in version number  
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 42567 package 'avg75fld':  
 error in Config-Version string '7.5.51_a1243': invalid character in version number  
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 46468 package 'avg75fld':  
 error in Version string '7.5.51_a1243': invalid character in version number  
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 235806 files and directories currently installed.)  
Preparing to replace libgnome-bluetooth8 3.2.2-0ubuntu5 (using .../libgnome-bluetooth8_3.2.2-0ubuntu5.1_i386.deb) ...  
Unpacking replacement libgnome-bluetooth8 ...  
Preparing to replace gnome-bluetooth 3.2.2-0ubuntu5 (using .../gnome-bluetooth_3.2.2-0ubuntu5.1_i386.deb) ...  
Unpacking replacement gnome-bluetooth ...  
Preparing to replace gir1.2-gnomebluetooth-1.0 3.2.2-0ubuntu5 (using .../gir1.2-gnomebluetooth-1.0_3.2.2-0ubuntu5.1_i386.deb) ...  
Unpacking replacement gir1.2-gnomebluetooth-1.0 ...  
Processing triggers for man-db ...  
Processing triggers for libglib2.0-0 ...  
Processing triggers for hicolor-icon-theme ...  
Processing triggers for gconf2 ...  
Processing triggers for bamfdaemon ...  
Rebuilding /usr/share/applications/bamf.index...  
Processing triggers for desktop-file-utils ...  
Processing triggers for gnome-menus ...  
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 42568 package 'avg75fld':  
 error in Version string '7.5.51_a1243': invalid character in version number  
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 42569 package 'avg75fld':  
 error in Config-Version string '7.5.51_a1243': invalid character in version number  
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...  
Unknown parameter encountered: "max log size"  
Ignoring unknown parameter "max log size"  
Unknown parameter encountered: "syslog"  
Ignoring unknown parameter "syslog"  
Unknown parameter encountered: "username map"  
Ignoring unknown parameter "username map"  
Unknown parameter encountered: "unix password sync"  
Ignoring unknown parameter "unix password sync"  
Unknown parameter encountered: "passwd program"  
Ignoring unknown parameter "passwd program"  
Unknown parameter encountered: "pam password change"  
Ignoring unknown parameter "pam password change"  
Unknown parameter encountered: "map to guest"  
Ignoring unknown parameter "map to guest"  
Unknown parameter encountered: "usershare allow guests"  
Ignoring unknown parameter "usershare allow guests"  
Unknown parameter encountered: "writable"  
Ignoring unknown parameter "writable"  
Unknown parameter encountered: "valid users"  
Ignoring unknown parameter "valid users"  
Unknown parameter encountered: "guest ok"  
Ignoring unknown parameter "guest ok"  
Unknown parameter encountered: "guest ok"  
Ignoring unknown parameter "guest ok"  
Unknown parameter encountered: "max log size"  
Ignoring unknown parameter "max log size"  
Unknown parameter encountered: "syslog"  
Ignoring unknown parameter "syslog"  
Unknown parameter encountered: "username map"  
Ignoring unknown parameter "username map"  
Unknown parameter encountered: "unix password sync"  
Ignoring unknown parameter "unix password sync"  
Unknown parameter encountered: "passwd program"  
Ignoring unknown parameter "passwd program"  
Unknown parameter encountered: "pam password change"  
Ignoring unknown parameter "pam password change"  
Unknown parameter encountered: "map to guest"  
Ignoring unknown parameter "map to guest"  
Unknown parameter encountered: "usershare allow guests"  
Ignoring unknown parameter "usershare allow guests"  
Unknown parameter encountered: "writable"  
Ignoring unknown parameter "writable"  
Unknown parameter encountered: "valid users"  
Ignoring unknown parameter "valid users"  
Unknown parameter encountered: "guest ok"  
Ignoring unknown parameter "guest ok"  
Unknown parameter encountered: "guest ok"  
Ignoring unknown parameter "guest ok"  
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied  
dpkg: error processing samba4 (--configure):  
 subprocess installed post-installation script returned error exit status 126  
No apport report written because MaxReports is reached already 
Setting up libgnome-bluetooth8 (3.2.2-0ubuntu5.1) ...  
Setting up gir1.2-gnomebluetooth-1.0 (3.2.2-0ubuntu5.1) ...  
Setting up gnome-bluetooth (3.2.2-0ubuntu5.1) ...  
Processing triggers for libc-bin ...  
ldconfig deferred processing now taking place  
Errors were encountered while processing:  
 samba4  
Error in function:   
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 42566 package 'avg75fld':  
 error in Version string '7.5.51_a1243': invalid character in version number  
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 42567 package 'avg75fld':  
 error in Config-Version string '7.5.51_a1243': invalid character in version number  
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...  
Unknown parameter encountered: "max log size"  
Ignoring unknown parameter "max log size"  
Unknown parameter encountered: "syslog"  
Ignoring unknown parameter "syslog"  
Unknown parameter encountered: "username map"  
Ignoring unknown parameter "username map"  
Unknown parameter encountered: "unix password sync"  
Ignoring unknown parameter "unix password sync"  
Unknown parameter encountered: "passwd program"  
Ignoring unknown parameter "passwd program"  
Unknown parameter encountered: "pam password change"  
Ignoring unknown parameter "pam password change"  
Unknown parameter encountered: "map to guest"  
Ignoring unknown parameter "map to guest"  
Unknown parameter encountered: "usershare allow guests"  
Ignoring unknown parameter "usershare allow guests"  
Unknown parameter encountered: "writable"  
Ignoring unknown parameter "writable"  
Unknown parameter encountered: "valid users"  
Ignoring unknown parameter "valid users"  
Unknown parameter encountered: "guest ok"  
Ignoring unknown parameter "guest ok"  
Unknown parameter encountered: "guest ok"  
Ignoring unknown parameter "guest ok"  
Unknown parameter encountered: "max log size"  
Ignoring unknown parameter "max log size"  
Unknown parameter encountered: "syslog"  
Ignoring unknown parameter "syslog"  
Unknown parameter encountered: "username map"  
Ignoring unknown parameter "username map"  
Unknown parameter encountered: "unix password sync"  
Ignoring unknown parameter "unix password sync"  
Unknown parameter encountered: "passwd program"  
Ignoring unknown parameter "passwd program"  
Unknown parameter encountered: "pam password change"  
Ignoring unknown parameter "pam password change"  
Unknown parameter encountered: "map to guest"  
Ignoring unknown parameter "map to guest"  
Unknown parameter encountered: "usershare allow guests"  
Ignoring unknown parameter "usershare allow guests"  
Unknown parameter encountered: "writable"  
Ignoring unknown parameter "writable"  
Unknown parameter encountered: "valid users"  
Ignoring unknown parameter "valid users"  
Unknown parameter encountered: "guest ok"  
Ignoring unknown parameter "guest ok"  
Unknown parameter encountered: "guest ok"  
Ignoring unknown parameter "guest ok"  
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied  
dpkg: error processing samba4 (--configure):  
 subprocess installed post-installation script returned error exit status 126
```

---

### Post by lingpanda on 2014-02-11
Looks like you installed Samba4 versus Samba3 and it's complaining about the parameters set in smb.conf file. This should be located in /usr/local/samba/etc/.

---

### Post by Old_Brewer on 2014-02-11
Hello Lingpanda
I have a question.  Should Ubuntu 12.04 use Samba3 and not Samba 4?  I'm guessing the Samba 4 was either on the old Ubuntu 10.04, or got automatically installed with 12.04.  
I just got done removing Samba 4, shutting down the computer.  Starting it up, and installing Samba 4.

Also there seems to be only these smb.conf files:

```
# find . -name  "*smb.conf*" -print |pg                   
./var/lib/ucf/cache/:etc:samba:smb.conf
./etc/samba/smb.conf.orig
./etc/samba/smb.conf
./etc/samba/smb.conf.ucf-dist
./usr/share/samba/smb.conf
./usr/share/samba/setup/provision.smb.conf.member
./usr/share/samba/setup/provision.smb.conf.dc
./usr/share/samba/setup/provision.smb.conf.standalone
./usr/share/doc/nautilus-share/examples/smb.conf
./usr/share/man/man5/smb.conf.5.gz

Here is the error message after installing Samba 4:

installArchives() failed: Preconfiguring packages ...
/tmp/samba4.config.142653: 1: /tmp/samba4.config.142653: samba-tool: not found
/tmp/samba4.config.142653: 1: /tmp/samba4.config.142653: samba-tool: not found
Preconfiguring packages ...
/tmp/samba4.config.143193: 1: /tmp/samba4.config.143193: samba-tool: not found
/tmp/samba4.config.143193: 1: /tmp/samba4.config.143193: samba-tool: not found
Preconfiguring packages ...
/tmp/samba4.config.143733: 1: /tmp/samba4.config.143733: samba-tool: not found
/tmp/samba4.config.143733: 1: /tmp/samba4.config.143733: samba-tool: not found
Preconfiguring packages ...
/tmp/samba4.config.149003: 1: /tmp/samba4.config.149003: samba-tool: not found
/tmp/samba4.config.149003: 1: /tmp/samba4.config.149003: samba-tool: not found
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 42425 package 'avg75fld':
 error in Version string '7.5.51_a1243': invalid character in version number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 42426 package 'avg75fld':
 error in Config-Version string '7.5.51_a1243': invalid character in version number
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 46468 package 'avg75fld':
 error in Version string '7.5.51_a1243': invalid character in version number
Selecting previously unselected package libhdb9-heimdal.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 234870 files and directories currently installed.)
Unpacking libhdb9-heimdal (from .../libhdb9-heimdal_1.6~git20120311.dfsg.1-2ubuntu0.1_i386.deb) ...
Selecting previously unselected package libsamba-util0.
Unpacking libsamba-util0 (from .../libsamba-util0_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package libndr0.
Unpacking libndr0 (from .../libndr0_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package libndr-standard0.
Unpacking libndr-standard0 (from .../libndr-standard0_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package libsamba-hostconfig0.
Unpacking libsamba-hostconfig0 (from .../libsamba-hostconfig0_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package libsamba-credentials0.
Unpacking libsamba-credentials0 (from .../libsamba-credentials0_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package libsamdb0.
Unpacking libsamdb0 (from .../libsamdb0_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package libgensec0.
Unpacking libgensec0 (from .../libgensec0_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package libsmbclient-raw0.
Unpacking libsmbclient-raw0 (from .../libsmbclient-raw0_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package python-talloc.
Unpacking python-talloc (from .../python-talloc_2.0.7-3_i386.deb) ...
Selecting previously unselected package libdcerpc0.
Unpacking libdcerpc0 (from .../libdcerpc0_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package libregistry0.
Unpacking libregistry0 (from .../libregistry0_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package libdcerpc-server0.
Unpacking libdcerpc-server0 (from .../libdcerpc-server0_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package libsamba-policy0.
Unpacking libsamba-policy0 (from .../libsamba-policy0_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package python-ldb.
Unpacking python-ldb (from .../python-ldb_1%3a1.1.4-1_i386.deb) ...
Selecting previously unselected package libkdc2-heimdal.
Unpacking libkdc2-heimdal (from .../libkdc2-heimdal_1.6~git20120311.dfsg.1-2ubuntu0.1_i386.deb) ...
Selecting previously unselected package attr.
Unpacking attr (from .../attr_1%3a2.4.46-5ubuntu1_i386.deb) ...
Selecting previously unselected package bind9utils.
Unpacking bind9utils (from .../bind9utils_1%3a9.8.1.dfsg.P1-4ubuntu0.8_i386.deb) ...
Selecting previously unselected package bind9.
Unpacking bind9 (from .../bind9_1%3a9.8.1.dfsg.P1-4ubuntu0.8_i386.deb) ...
Selecting previously unselected package python-dnspython.
Unpacking python-dnspython (from .../python-dnspython_1.9.4-0ubuntu3_all.deb) ...
Selecting previously unselected package python-tdb.
Unpacking python-tdb (from .../python-tdb_1.2.9-4_i386.deb) ...
Selecting previously unselected package python-samba.
Unpacking python-samba (from .../python-samba_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package samba-dsdb-modules.
Unpacking samba-dsdb-modules (from .../samba-dsdb-modules_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package samba4-common-bin.
Unpacking samba4-common-bin (from .../samba4-common-bin_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package samba4.
Unpacking samba4 (from .../samba4_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 42539 package 'avg75fld':
 error in Version string '7.5.51_a1243': invalid character in version number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 42540 package 'avg75fld':
 error in Config-Version string '7.5.51_a1243': invalid character in version number
Setting up libhdb9-heimdal (1.6~git20120311.dfsg.1-2ubuntu0.1) ...
Setting up libsamba-util0 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up libndr0 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up libndr-standard0 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up libsamba-hostconfig0 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up libsamba-credentials0 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up libsamdb0 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up libgensec0 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up libsmbclient-raw0 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up python-talloc (2.0.7-3) ...
Setting up libdcerpc0 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up libregistry0 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up libdcerpc-server0 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up libsamba-policy0 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up python-ldb (1:1.1.4-1) ...
Setting up libkdc2-heimdal (1.6~git20120311.dfsg.1-2ubuntu0.1) ...
Setting up attr (1:2.4.46-5ubuntu1) ...
Setting up bind9utils (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
Setting up bind9 (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
 * Starting domain name service... bind9
   ...done.
Setting up python-dnspython (1.9.4-0ubuntu3) ...
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42539 package 'avg75fld':
 error in Version string '7.5.51_a1243': invalid character in version number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42540 package 'avg75fld':
 error in Config-Version string '7.5.51_a1243': invalid character in version number
Setting up python-tdb (1.2.9-4) ...
Setting up python-samba (4.0.0~alpha18.dfsg1-4ubuntu2) ...
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42539 package 'avg75fld':
 error in Version string '7.5.51_a1243': invalid character in version number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42540 package 'avg75fld':
 error in Config-Version string '7.5.51_a1243': invalid character in version number
Setting up samba-dsdb-modules (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up samba4-common-bin (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "username map"
Ignoring unknown parameter "username map"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
Unknown parameter encountered: "valid users"
Ignoring unknown parameter "valid users"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "username map"
Ignoring unknown parameter "username map"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
Unknown parameter encountered: "valid users"
Ignoring unknown parameter "valid users"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
No apport report written because MaxReports is reached already
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 samba4
Error in function: 
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 42530 package 'avg75fld':
 error in Version string '7.5.51_a1243': invalid character in version number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 42531 package 'avg75fld':
 error in Config-Version string '7.5.51_a1243': invalid character in version number
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "username map"
Ignoring unknown parameter "username map"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
Unknown parameter encountered: "valid users"
Ignoring unknown parameter "valid users"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "username map"
Ignoring unknown parameter "username map"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
Unknown parameter encountered: "valid users"
Ignoring unknown parameter "valid users"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
```

---

### Post by wildmanne39 on 2014-02-11
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by lingpanda on 2014-02-12
First what exactly are you using Samba for? Are you using it to create file shares and a printer server? The Samba4 version you are installing is very old. Samba4 is used primarily for Active Directory but can be used as a file and printer server as well. /etc/samba/smb.conf is the default file location for Samba3.

---

### Post by Old_Brewer on 2014-02-13
I am using Samba to use files on 2 Windows computers.  I am also using Samba to print to printers attached to these Windows computers.
Here is some info about the most recent smb.conf file:
```
root@joebelle-laptop:/etc/samba# ls -l /etc/samba
total 60
-rw-r--r-- 1 root root     0 Feb  6 20:59 dhcp.conf
-rw-r--r-- 1 root root     8 Oct  4  2007 gdbcommands
-rw-r--r-- 1 root root 12444 Feb  3 12:56 smb.conf
-rw-r--r-- 1 root root 12413 Jul  2  2011 smb.conf.orig
-rw-r--r-- 1 root root 12461 Feb  3 12:56 smb.conf.ucf-dist
-rw-r--r-- 1 root root    25 Jul  2  2011 smbusers
drwxr-xr-x 2 root root  4096 Apr 13  2012 tls
root@joebelle-laptop:/etc/samba# 
root@joebelle-laptop:/etc/samba# 
root@joebelle-laptop:/etc/samba# cat -vet smb.conf
#$
# Sample configuration file for the Samba suite for Debian GNU/Linux.$
#$
#$
# This is the main Samba configuration file. You should read the$
# smb.conf(5) manual page in order to understand the options listed$
# here. Samba has a huge number of configurable options most of which $
# are not shown in this example$
#$
# Some options that are often worth tuning have been included as$
# commented-out examples in this file.$
#  - When such options are commented with ";", the proposed setting$
#    differs from the default Samba behaviour$
#  - When commented with "#", the proposed setting is the default$
#    behaviour of Samba but the option is considered important$
#    enough to be mentioned here$
#$
# NOTE: Whenever you modify this file you should run the command$
# "testparm" to check that you have not made any basic syntactic $
# errors. $
# A well-established practice is to name the original file$
# "smb.conf.master" and create the "real" config file with$
# testparm -s smb.conf.master >smb.conf$
# This minimizes the size of the really used smb.conf file$
# which, according to the Samba Team, impacts performance$
# However, use this with caution if your smb.conf file contains nested$
# "include" statements. See Debian bug #483187 for a case$
# where using a master file is not a good idea.$
#$
$
#======================= Global Settings =======================$
$
[global]$
$
## Browsing/Identification ###$
$
# Change this to the workgroup/NT-domain name your Samba server will part of$
   workgroup = MSHOME$
$
# server string is the equivalent of the NT Description field$
   server string = %h server (Samba, Ubuntu)$
$
# Windows Internet Name Serving Support Section:$
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server$
wins support = yes$
$
# WINS Server - Tells the NMBD components of Samba to be a WINS Client$
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both$
;   wins server = w.x.y.z$
$
# This will prevent nmbd to search for NetBIOS names through DNS.$
   dns proxy = no$
$
# What naming service and in what order should we use to resolve host names$
# to IP addresses$
;   name resolve order = lmhosts host wins bcast$
$
#### Networking ####$
$
# The specific set of interfaces / networks to bind to$
# This can be either the interface name or an IP address/netmask;$
# interface names are normally preferred$
;   interfaces = 127.0.0.0/8 eth0$
$
# Only bind to the named interfaces and/or networks; you must use the$
# 'interfaces' option above to use this.$
# It is recommended that you enable this feature if your Samba machine is$
# not protected by a firewall or is a firewall itself.  However, this$
# option cannot handle dynamic or non-broadcast interfaces correctly.$
;   bind interfaces only = yes$
$
$
$
#### Debugging/Accounting ####$
$
# This tells Samba to use a separate log file for each machine$
# that connects$
   log file = /var/log/samba/log.%m$
$
# Cap the size of the individual log files (in KiB).$
   max log size = 1000$
$
# If you want Samba to only log through syslog then set the following$
# parameter to 'yes'.$
#   syslog only = no$
$
# We want Samba to log a minimum amount of information to syslog. Everything$
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log$
# through syslog you should set the following parameter to something higher.$
   syslog = 0$
$
# Do something sensible when Samba crashes: mail the admin a backtrace$
   panic action = /usr/share/samba/panic-action %d$
$
$
####### Authentication #######$
$
# "security = user" is always a good idea. This will require a Unix account$
# in this server for every user accessing the server. See$
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html$
# in the samba-doc package for details.$
security = user$
username map = /etc/samba/smbusers$
$
# You may wish to use password encryption.  See the section on$
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.$
   encrypt passwords = true$
$
# If you are using encrypted passwords, Samba will need to know what$
# password database type you are using.  $
   passdb backend = tdbsam$
$
   obey pam restrictions = yes$
$
# This boolean parameter controls whether Samba attempts to sync the Unix$
# password with the SMB password when the encrypted SMB password in the$
# passdb is changed.$
   unix password sync = yes$
$
# For Unix password sync to work on a Debian GNU/Linux system, the following$
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for$
# sending the correct chat script for the passwd program in Debian Sarge).$
   passwd program = /usr/bin/passwd %u$
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .$
$
# This boolean controls whether PAM will be used for password changes$
# when requested by an SMB client instead of the program listed in$
# 'passwd program'. The default is 'no'.$
   pam password change = yes$
$
# This option controls how unsuccessful authentication attempts are mapped $
# to anonymous connections$
   map to guest = bad user$
$
########## Domains ###########$
$
# Is this machine able to authenticate users. Both PDC and BDC$
# must have this setting enabled. If you are the BDC you must$
# change the 'domain master' setting to no$
#$
;   domain logons = yes$
#$
# The following setting only takes effect if 'domain logons' is set$
# It specifies the location of the user's profile directory$
# from the client point of view)$
# The following required a [profiles] share to be setup on the$
# samba server (see below)$
;   logon path = \\%N\profiles\%U$
# Another common choice is storing the profile in the user's home directory$
# (this is Samba's default)$
#   logon path = \\%N\%U\profile$
$
# The following setting only takes effect if 'domain logons' is set$
# It specifies the location of a user's home directory (from the client$
# point of view)$
;   logon drive = H:$
#   logon home = \\%N\%U$
$
# The following setting only takes effect if 'domain logons' is set$
# It specifies the script to run during logon. The script must be stored$
# in the [netlogon] share$
# NOTE: Must be store in 'DOS' file format convention$
;   logon script = logon.cmd$
$
# This allows Unix users to be created on the domain controller via the SAMR$
# RPC pipe.  The example command creates a user account with a disabled Unix$
# password; please adapt to your needs$
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u$
$
# This allows machine accounts to be created on the domain controller via the $
# SAMR RPC pipe.  $
# The following assumes a "machines" group exists on the system$
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u$
$
# This allows Unix groups to be created on the domain controller via the SAMR$
# RPC pipe.  $
; add group script = /usr/sbin/addgroup --force-badname %g$
$
########## Printing ##########$
$
# If you want to automatically load your printer list rather$
# than setting them up individually then you'll need this$
#   load printers = yes$
$
# lpr(ng) printing. You may wish to override the location of the$
# printcap file$
;   printing = bsd$
;   printcap name = /etc/printcap$
$
# CUPS printing.  See also the cupsaddsmb(8) manpage in the$
# cupsys-client package.$
;   printing = cups$
;   printcap name = cups$
$
############ Misc ############$
$
# Using the following line enables you to customise your configuration$
# on a per machine basis. The %m gets replaced with the netbios name$
# of the machine that is connecting$
;   include = /home/samba/etc/smb.conf.%m$
$
# Most people will find that this option gives better performance.$
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html$
# for details$
# You may want to add the following on a Linux system:$
#         SO_RCVBUF=8192 SO_SNDBUF=8192$
#   socket options = TCP_NODELAY$
$
# The following parameter is useful only if you have the linpopup package$
# installed. The samba maintainer and the linpopup maintainer are$
# working to ease installation and configuration of linpopup and samba.$
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &$
$
# Domain Master specifies Samba to be the Domain Master Browser. If this$
# machine will be configured as a BDC (a secondary logon server), you$
# must set this to 'no'; otherwise, the default behavior is recommended.$
#   domain master = auto$
$
# Some defaults for winbind (make sure you're not using the ranges$
# for something else.)$
;   idmap uid = 10000-20000$
;   idmap gid = 10000-20000$
;   template shell = /bin/bash$
$
# The following was the default behaviour in sarge,$
# but samba upstream reverted the default because it might induce$
# performance issues in large organizations.$
# See Debian bug #368251 for some of the consequences of *not*$
# having this setting and smb.conf(5) for details.$
;   winbind enum groups = yes$
;   winbind enum users = yes$
$
# Setup usershare options to enable non-root users to share folders$
# with the net usershare command.$
$
# Maximum number of usershare. 0 (default) means that usershare is disabled.$
;   usershare max shares = 100$
$
# Allow users who've been granted usershare privileges to create$
# public shares, not just authenticated ones$
   usershare allow guests = yes$
$
#======================= Share Definitions =======================$
$
# Un-comment the following (and tweak the other settings below to suit)$
# to enable the default home directory shares.  This will share each$
# user's home directory as \\server\username$
[homes]$
comment = Home Directories$
browseable = yes$
$
# By default, the home directories are exported read-only. Change the$
# next parameter to 'no' if you want to be able to write to them.$
;   read only = no$
$
writable = yes$
$
# File creation mask is set to 0700 for security reasons. If you want to$
# create files with group=rw permissions, set next parameter to 0775.$
;   create mask = 0700$
$
# Directory creation mask is set to 0700 for security reasons. If you want to$
# create dirs. with group=rw permissions, set next parameter to 0775.$
;   directory mask = 0700$
$
# By default, \\server\username shares can be connected to by anyone$
# with access to the samba server.  Un-comment the following parameter$
# to make sure that only "username" can connect to \\server\username$
# This might need tweaking when using external authentication schemes$
valid users = %S$
$
# Un-comment the following and create the netlogon directory for Domain Logons$
# (you need to configure Samba to act as a domain controller too.)$
;[netlogon]$
;   comment = Network Logon Service$
;   path = /home/samba/netlogon$
;   guest ok = yes$
;   read only = yes$
;   share modes = no$
$
# Un-comment the following and create the profiles directory to store$
# users profiles (see the "logon path" option above)$
# (you need to configure Samba to act as a domain controller too.)$
# The path below should be writable by all users so that their$
# profile directory may be created the first time they log on$
;[profiles]$
;   comment = Users profiles$
;   path = /home/samba/profiles$
;   guest ok = no$
;   browseable = no$
;   create mask = 0600$
;   directory mask = 0700$
$
[printers]$
   comment = All Printers$
   browseable = no$
   path = /var/spool/samba$
   printable = yes$
   guest ok = no$
   read only = yes$
   create mask = 0700$
$
# Windows clients look for this share name as a source of downloadable$
# printer drivers$
[print$]$
   comment = Printer Drivers$
   path = /var/lib/samba/printers$
   browseable = yes$
   read only = yes$
   guest ok = no$
# Uncomment to allow remote administration of Windows print drivers.$
# You may need to replace 'lpadmin' with the name of the group your$
# admin users are members of.$
# Please note that you also need to set appropriate Unix permissions$
# to the drivers directory for these users to have write rights in it$
;   write list = root, @lpadmin$
$
# A sample share for sharing your CD-ROM with others.$
;[cdrom]$
;   comment = Samba server's CD-ROM$
;   read only = yes$
;   locking = no$
;   path = /cdrom$
;   guest ok = yes$
$
# The next two parameters show how to auto-mount a CD-ROM when the$
#^Icdrom share is accesed. For this to work /etc/fstab must contain$
#^Ian entry like this:$
#$
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0$
#$
# The CD-ROM gets unmounted automatically after the connection to the$
#$
# If you don't want to use auto-mounting/unmounting make sure the CD$
#^Iis mounted on /cdrom$
#$
;   preexec = /bin/mount /cdrom$
;   postexec = /bin/umount /cdrom$
$
root@joebelle-laptop:/etc/samba# 
```

Here is the output from testparm:
```
root@joebelle-laptop:/etc/samba# testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    workgroup = MSHOME
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    wins support = Yes
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[homes]
    comment = Home Directories
    valid users = %S
    read only = No

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
root@joebelle-laptop:/etc/samba# 

```

---

### Post by lingpanda on 2014-02-13
I would completely remove Samba4 and not reinstall it. Stick with Samba3 for your needs. It looks like Samba3 has been replaced by Samba4 in the repositories Since 10.04 to 12.04.

---

### Post by bab1 on 2014-02-13
> **lingpanda said:**
> I would completely remove Samba4 and not reinstall it. Stick with Samba3 for your needs. It looks like Samba3 has been replaced by Samba4 in the repositories Since 10.04 to 12.04.

The Samba package (Samba v3.6) is available in the latest versions of Ubuntu (13.10 and 14.04).  The package name is *Samba*.  Samba4 is packaged as *samba4*.

See here for the [samba3 package]("http://packages.ubuntu.com/saucy-updates/samba") (samba by name).  

This is the [Samba4 package]("http://packages.ubuntu.com/saucy/samba4") (samba4 by name).

+1 for the advice to the OP to use Samba3.  In most home and small business there is no real need for a AD style domain that is deployed by Samba4.

---

### Post by Old_Brewer on 2014-02-13
Thanks Lingpanda & bab1
Sounds like great advise.  Do you have any tips on if I just uninstall Samba4, or do i have to unstall any of the addons?
This is what "Ubuntu Software Center" shows as installed:

```
SMB/CIFS file, NT domain and active directory server (version 4)
Samba 4 common files used by both the server and the client
Samba host configuration library
```

---

### Post by bab1 on 2014-02-13
> **Old_Brewer said:**
> Thanks Lingpanda & bab1
Sounds like great advise.  Do you have any tips on if I just uninstall Samba4, or do i have to unstall any of the addons?
This is what "Ubuntu Software Center" shows as installed:

```
SMB/CIFS file, NT domain and active directory server (version 4)
Samba 4 common files used by both the server and the client
Samba host configuration library
```

The simplest way to remove the package *samba4 * is to use the command line```

sudo apt-get purge samba4
```...I would then cleanup the trash that might be left behind with this```
sudo apt-get autoremove
```

If you are interested in seeing what you are removing you can add the -s switch fist like this```

sudo apt-get -s purge samba4

sudo apt-get autoremove

```

---

### Post by Old_Brewer on 2014-02-13
> **bab1 said:**
> The simplest way to remove the package *samba4 * is to use the command line```

sudo apt-get purge samba4
```...I would then cleanup the trash that might be left behind with this```
sudo apt-get autoremove
```

If you are interested in seeing what you are removing you can add the -s switch fist like this```

sudo apt-get -s purge samba4

sudo apt-get autoremove

```

Thanks for the detailed instructions.  I'll get it done, probably tomorrow.  I'll let you know how it goes.
Thanks

---

### Post by bab1 on 2014-02-13
> **Old_Brewer said:**
> Thanks for the detailed instructions.  I'll get it done, probably tomorrow.  I'll let you know how it goes.
Thanks

Then if you want to manually install Samba v3.6 you can do this```

sudo apt-get install samba

```

At that point we will be ready to configure a share.  It can be done via the GUI (Nautilus) if what you are sharing is in your home directory or via the smb.conf file if the share is outside of that file system.

---

### Post by Old_Brewer on 2014-02-17
Hi bab1
I refreshed my screen, but did not log back into ubuntuforms.  I missed the additional, most recent info.  Here is what I did:
> &#65279;root@joebelle-laptop:~# apt-get purge samba4 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
The following packages were automatically installed and are no longer required: 
  libguess1 audacious libbinio1ldbl libaudclient2 libresid-builder0c2a 
  libtagc0 audacious-plugins-data libbs2b0 libcddb2 audacious-plugins kdesudo 
  libcue1 python-urwid dkms libmowgli2 libfluidsynth1 libaudcore1 libsidplay2 
  libdb4.8 update-manager-kde libgnome-desktop-2-17 acroread-common libpisync1 
Use 'apt-get autoremove' to remove them. 
The following packages will be REMOVED: 
  samba4* 
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded. 
1 not fully installed or removed. 
After this operation, 11.2 MB disk space will be freed. 
Do you want to continue [Y/n]? y 
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 42530 package 'avg75fld': 
 error in Version string '7.5.51_a1243': invalid character in version number 
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 42531 package 'avg75fld': 
 error in Config-Version string '7.5.51_a1243': invalid character in version number 
(Reading database ... 235803 files and directories currently installed.) 
Removing samba4 ... 
samba4 stop/waiting 
Purging configuration files for samba4 ... 
Processing triggers for ureadahead ... 
ureadahead will be reprofiled on next reboot 
Processing triggers for man-db ... 
root@joebelle-laptop:~#  
root@joebelle-laptop:~#  
root@joebelle-laptop:~# apt-get autoremove 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
The following packages will be REMOVED: 
  acroread-common audacious audacious-plugins audacious-plugins-data dkms kdesudo libaudclient2 libaudcore1 libbinio1ldbl libbs2b0 
  libcddb2 libcue1 libdb4.8 libfluidsynth1 libgnome-desktop-2-17 libguess1 libmowgli2 libpisync1 libresid-builder0c2a libsidplay2 
  libtagc0 python-urwid update-manager-kde 
0 upgraded, 0 newly installed, 23 to remove and 0 not upgraded. 
After this operation, 12.8 MB disk space will be freed. 
Do you want to continue [Y/n]? y 
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 42500 package 'avg75fld': 
 error in Version string '7.5.51_a1243': invalid character in version number 
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 42501 package 'avg75fld': 
 error in Config-Version string '7.5.51_a1243': invalid character in version number 
(Reading database ... 235661 files and directories currently installed.) 
Removing acroread-common ... 
Removing audacious ... 
Removing audacious-plugins ... 
Removing audacious-plugins-data ... 
Removing dkms ... 
Removing update-manager-kde ... 
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42500 package 'avg75fld': 
 error in Version string '7.5.51_a1243': invalid character in version number 
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42501 package 'avg75fld': 
 error in Config-Version string '7.5.51_a1243': invalid character in version number 
Removing kdesudo ... 
update-alternatives: using /usr/lib/kde4/libexec/kdesu-distrib/kdesu to provide /usr/lib/kde4/libexec/kdesu (kdesu) in auto mode. 
Removing libaudclient2 ... 
Removing libaudcore1 ... 
Removing libbinio1ldbl ... 
Removing libbs2b0 ... 
Removing libcddb2 ... 
Removing libcue1 ... 
Removing libdb4.8 ... 
Removing libfluidsynth1 ... 
Removing libgnome-desktop-2-17 ... 
Removing libguess1 ... 
Removing libmowgli2 ... 
Removing libpisync1 ... 
Removing libresid-builder0c2a ... 
Removing libsidplay2 ... 
Removing libtagc0 ... 
Removing python-urwid ... 
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42500 package 'avg75fld': 
 error in Version string '7.5.51_a1243': invalid character in version number 
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42501 package 'avg75fld': 
 error in Config-Version string '7.5.51_a1243': invalid character in version number 
Processing triggers for man-db ... 
Processing triggers for menu ... 
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42500 package 'avg75fld': 
 error in Version string '7.5.51_a1243': invalid character in version number 
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42501 package 'avg75fld': 
 error in Config-Version string '7.5.51_a1243': invalid character in version number 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
root@joebelle-laptop:~#  
root@joebelle-laptop:~#  
root@joebelle-laptop:~# 

I'm not sure what is left of all of the Samba packages.  I did this:
> root@joebelle-laptop:~# dpkg -l | grep "samba"
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42423 package 'avg75fld':
 error in Version string '7.5.51_a1243': invalid character in version number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42424 package 'avg75fld':
 error in Config-Version string '7.5.51_a1243': invalid character in version number
ii  libsamba-credentials0                         4.0.0~alpha18.dfsg1-4ubuntu2                          Samba Credentials management library
ii  libsamba-hostconfig0                          4.0.0~alpha18.dfsg1-4ubuntu2                          Samba host configuration library
ii  libsamba-policy0                              4.0.0~alpha18.dfsg1-4ubuntu2                          Samba policy management
ii  libsamba-util0                                4.0.0~alpha18.dfsg1-4ubuntu2                          Samba utility function library
ii  python-samba                                  4.0.0~alpha18.dfsg1-4ubuntu2                          Python bindings for Samba
ii  samba                                         2:3.6.3-2ubuntu2.9                                    SMB/CIFS file, print, and login server for Unix
ii  samba-common                                  2:3.6.3-2ubuntu2.9                                    common files used by both the Samba server and client
ii  samba-common-bin                              2:3.6.3-2ubuntu2.9                                    common files used by both the Samba server and client
ii  samba-dsdb-modules                            4.0.0~alpha18.dfsg1-4ubuntu2                          Samba Directory Services Database
ii  samba4-common-bin                             4.0.0~alpha18.dfsg1-4ubuntu2                          Samba 4 common files used by both the server and the client
root@joebelle-laptop:~# 

I can print, and see files on the windows computers.
Do you think I need to do anything else?  I have not done this:  sudo apt-get install samba
Thanks

---

### Post by bab1 on 2014-02-17
> **Old_Brewer said:**
> Hi bab1
...

I'm not sure what is left of all of the Samba packages.  I did this:
```
root@joebelle-laptop:~# dpkg -l | grep "samba"
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42423 package 'avg75fld':
error in Version string '7.5.51_a1243': invalid character in version number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42424 package 'avg75fld':
error in Config-Version string '7.5.51_a1243': invalid character in version number
ii libsamba-credentials0 4.0.0~alpha18.dfsg1-4ubuntu2 Samba Credentials management library
ii libsamba-hostconfig0 4.0.0~alpha18.dfsg1-4ubuntu2 Samba host configuration library
ii libsamba-policy0 4.0.0~alpha18.dfsg1-4ubuntu2 Samba policy management
ii libsamba-util0 4.0.0~alpha18.dfsg1-4ubuntu2 Samba utility function library
ii python-samba 4.0.0~alpha18.dfsg1-4ubuntu2 Python bindings for Samba
[COLOR="#FF0000"]ii samba 2:3.6.3-2ubuntu2.9 SMB/CIFS file, print, and login server for Unix
ii samba-common 2:3.6.3-2ubuntu2.9 common files used by both the Samba server and client
ii samba-common-bin 2:3.6.3-2ubuntu2.9 common files used by both the Samba server and client[/COLOR]
ii samba-dsdb-modules 4.0.0~alpha18.dfsg1-4ubuntu2 Samba Directory Services Database
ii samba4-common-bin 4.0.0~alpha18.dfsg1-4ubuntu2 Samba 4 common files used by both the server and the client
root@joebelle-laptop:~# 
```
I can print, and see files on the windows computers.
Do you think I need to do anything else?  I have not done this:  sudo apt-get install samba
Thanks
Most of what is left are files that could be manually removed or need editing.  But there is no reason to do that.  It is just digital dust.  :D

However the items in red above are the Samba3 components you do need ( and are using right now).

I'd just leave everything alone if it is all working correctly at this point.

---

### Post by Old_Brewer on 2014-02-17
Thanks for all of your help.
Another issue seems to have surfaced.  I have a red triangle at the top of the screen near the shutdown icon.  When I check for updates, I get this information about what I think are old repositories that are no longer functional.  I'm not sure if it because of the old Samba version, or if it is just coincidental.  Here is what I am getting, do you have any suggestions?  Thanks
```
W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by bab1 on 2014-02-17
> **Old_Brewer said:**
> Thanks for all of your help.
Another issue seems to have surfaced.  I have a red triangle at the top of the screen near the shutdown icon.  When I check for updates, I get this information about what I think are old repositories that are no longer functional.  I'm not sure if it because of the old Samba version, or if it is just coincidental.  Here is what I am getting, do you have any suggestions?  Thanks
```
W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```
These don't look to have anything to do with Samba v3.  They are old backports for Gutsy (7.10) like you said,  Since those repos are closed and moved you will never get any updates.  Those lines should be removed.  You can remove them using Synaptic I believe.

---

### Post by Old_Brewer on 2014-02-17
OK  I'll do some checking and take care of what I hope is the last issue.
Thanks again for all of your help.  I'll mark the thread solved \\:D/

---

