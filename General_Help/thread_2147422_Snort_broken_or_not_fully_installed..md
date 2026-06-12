---
title: "Snort broken or not fully installed."
date: 2013-05-21
forum: General Help
---

### Post by OtagoHarbour on 2013-05-21
I am using Ubuntu 11.10 Gnome.

I uninstalled snort in order to install a more recent version.  The new installation initially failed because the system would not let be rm or modify /var/log/snort even as root.

```
sudo chattr -i /var/log/snort/*
```

enabled me to remove the contents of /var/log/snort although the i attribute did not appear to have been set.

However ```
sudo chattr -i /var/log/snort
```

did not allow me to remove /var/log/snort itself although only the e attribute was set.

Subsequently

```

 sudo apt-get install snort

```

resulted in

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  snort-doc
The following NEW packages will be installed:
  snort
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/473 kB of archives.
After this operation, 1,339 kB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 402348 files and directories currently installed.)
Unpacking snort (from .../snort_2.8.5.2-9.1_i386.deb) ...
usermod: no changes
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up snort (2.8.5.2-9.1) ...
 * Stopping Network Intrusion Detection System  snort                                                             *  - No running snort instance found
 * Starting Network Intrusion Detection System  snort                                                     [fail] 
invoke-rc.d: initscript snort, action "start" failed.
dpkg: error processing snort (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 snort
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Subsequently,

```

sudo snort -d -l ./log -c snort.conf

```

resulted in

```

ERROR: Unable to open rules file "snort.conf": No such file or directory.

```

```

sudo snort -d -l ./log -c /etc/snort/snort.conf

```

resulted in

```

ERROR: /etc/snort/snort.conf(45) Unknown rule type: ipvar.
Fatal Error, Quitting..

```

Subsequently

```

sudo dpkg-reconfigure snort

```

```

/usr/sbin/dpkg-reconfigure: snort is broken or not fully installed

```

```

sudo apt-get purge snort snort-common

```

resulted in

```

rm: cannot remove `/var/log/snort': Operation not permitted
dpkg: error processing snort (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 snort
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I was able to change ownership of /var/log/snort so now I get

```

ls -ld /var/log/snort
drwxrws--- 2 root adm 4096 2013-05-20 23:22 /var/log/snort
rmdir /var/log/snort
rmdir: failed to remove `/var/log/snort': Permission denied
peter@peter-Inspiron-620:/var/log$ sudo rmdir /var/log/snort
rmdir: failed to remove `/var/log/snort': Operation not permitted
peter@peter-Inspiron-620:/var/log$ 

```

---

