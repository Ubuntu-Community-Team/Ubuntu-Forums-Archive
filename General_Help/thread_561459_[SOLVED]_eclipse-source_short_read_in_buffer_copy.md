---
title: "[SOLVED] eclipse-source short read in buffer_copy"
date: 2007-09-27
forum: General Help
---

### Post by shanem on 2007-09-27
Hi,

I am getting a strange error when trying to install eclipse-source, see below. Can anyone help?

sss

sss@sss-laptop:~$ sudo apt-get install eclipse-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  eclipse-source
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B/30.0MB of archives.
After unpacking 36.7MB of additional disk space will be used.
(Reading database ... 107181 files and directories currently installed.)
Unpacking eclipse-source (from .../eclipse-source_3.2.2-0ubuntu3_i386.deb) ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/eclipse-source_3.2.2-0ubuntu3_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/eclipse/plugins/org.eclipse.jdt.source_3.2.2.r322_v20070104-R4CR0Znkvtfjv9-/src/org.eclipse.jdt.ui_3.2.2.r322_v20070124/src.zip')
Errors were encountered while processing:
 /var/cache/apt/archives/eclipse-source_3.2.2-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

sss@sss-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6              7052464   2718208   3976012  41% /
varrun                  192956       104    192852   1% /var/run
varlock                 192956         0    192956   0% /var/lock
procbususb              192956       112    192844   1% /proc/bus/usb
udev                    192956       112    192844   1% /dev
devshm                  192956         0    192956   0% /dev/shm
lrm                     192956     33788    159168  18% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1              4803400   4303152    500248  90% /media/sda1
/dev/sda3              4610652   3822716    787936  83% /media/sda3
/dev/sda7              2120280   1285198    835082  61% /media/sda7

---

### Post by shanem on 2007-09-27
apt-get clean fixed the problem.

---

