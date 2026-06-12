---
title: "udev update error on Ubuntu Server 12.04"
date: 2014-03-31
forum: General Help
---

### Post by Skynan on 2014-03-31
I was updating my packages with apt-get upgrade and ran into a problem.

Setting up udev (175-0ubuntu9.5) ...
invoke-rc.d: unknown initscript, /etc/init.d/udev not found.
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)

As I'm not completely sure what udev actually does I'm being careful incase it will mess something up.
What can I do to resolve this error?

---

### Post by Skynan on 2014-03-31
I've found that /etc/init.d/udev links to /lib/init/upstart-job which doesn't exist.
What should I do next?

---

### Post by slickymaster on 2014-03-31
A non-existent **/lib/init/upstart-job** file would be the reason you got the "unknown initscript, /etc/init.d/udev not found" error.

You could try _reinstalling_ or _dpkg-reconfigure_-ing the upstart package.

---

### Post by Skynan on 2014-03-31
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 312 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://ubuntu.mirrors.ovh.net/ftp.ubuntu.com/ubuntu/](http://ubuntu.mirrors.ovh.net/ftp.ubuntu.com/ubuntu/) precise-updates/main                                                                                                                                                              upstart amd64 1.5-0ubuntu7.2 [312 kB]
Fetched 312 kB in 0s (0 B/s)
(Reading database ... 25611 files and directories currently installed.)
Preparing to replace upstart 1.5-0ubuntu7.2 (using .../upstart_1.5-0ubuntu7.2_am                                                                                                                                                             d64.deb) ...
Unpacking replacement upstart ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up upstart (1.5-0ubuntu7.2) ...
Setting up udev (175-0ubuntu9.5) ...
udev stop/waiting
udev start/running, process 19093
Removing 'diversion of /sbin/udevadm to /sbin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...


Looks like that did it! Thank you so much!

---

### Post by slickymaster on 2014-03-31
Just glad you got it fixed and running.

---

