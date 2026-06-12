---
title: "What does this aptitude text in the terminal mean?"
date: 2006-10-27
forum: General Help
---

### Post by Schammy on 2006-10-27
I'm trying to install webmin and having trouble.  I had it installed via a downloaded file yesterday -- it was the 1.2 version.  I was having trouble with configuring it so I try to install the 1.3 version.  I successfully did that via aptitude but I couldn't connect to the webmin server.

I figured I should use the "aptitude purge" command to get rid of webmin completely.  I ran that command and then tried to reinstall webmin via the comand below and it didn't work.  

Anyone know what's going on here?  Did I screw things up by installing webmin 1.2 via a downloaded .tar and then install webmin 1.3 via an "aptitude install" comand?

whoami
steve
steve@steve-ubuntu:~$ sudo aptitude install webmin
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for webmin
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
steve@steve-ubuntu:~$

Any help is greatly appreciated!

---

### Post by Schammy on 2006-10-27
I thought it might be helpful to show you all of the webmin files and folders on my system.  I see both both 1.2 and 1.3 versions on my system.```
/usr/local/webmin/webmin-1.210
/usr/local/webmin/webmin-1.210/cluster-webmin
/usr/local/webmin/webmin-1.210/mscstyle3/webminlog
/usr/local/webmin/webmin-1.300/webminlog
/usr/local/webmin/webmin-1.300/caldera/webminlog
/usr/local/webmin
/usr/local/webmin/webmin-1.300
/usr/local/webmin/webmin-1.210/caldera/cluster-webmin
/usr/local/webmin/webmin-1.210/mscstyle3/webmin
/usr/local/webmin/webmin-1.300/caldera/webmin
/usr/local/webmin/webmin-1.210/webminlog
/usr/local/webmin/webmin-1.210/webmin
/usr/share/webmin
/usr/local/webmin/webmin-1.300/webmin
/usr/local/webmin/webmin-1.210/caldera/webmin
/usr/local/webmin/webmin-1.210/caldera/webminlog
/usr/local/webmin/webmin-1.300/caldera/cluster-webmin
/usr/local/webmin/webmin-1.300/mscstyle3/webminlog
/usr/local/webmin/webmin-1.300/mscstyle3/webmin
/usr/local/webmin/webmin-1.300/cluster-webmin
/usr/local/webmin/webmin-1.300/Webmin
/usr/local/webmin/webmin-1.300/blue-theme/webmin
/usr/local/webmin/webmin-1.300/blue-theme/webminlog
/usr/local/webmin/webmin-1.300/status/images/webmin.gif
/usr/local/webmin/webmin-1.210/images/webmin.gif
/usr/local/webmin/webmin-1.300/caldera/images/webmin-header.gif
/usr/local/webmin/webmin-1.210/caldera/images/webmin-header.gif
/usr/local/webmin/webmin-1.210/status/images/webmin.gif
/usr/local/webmin/webmin-1.300/cluster-software/status/images/webmin.gif
/usr/local/webmin/webmin-1.300/images/webmin.gif
/usr/local/webmin/webmin-1.210/mscstyle3/images/cats_over/webmin.jpg
/usr/local/webmin/webmin-1.300/mscstyle3/images/cats_over/webmin.jpg
/usr/local/webmin/webmin-1.210/mscstyle3/images/cats/webmin.jpg
/usr/local/webmin/webmin-1.210/mscstyle3/images/top_bar/webmin_logo.jpg
/usr/local/webmin/webmin-1.300/mscstyle3/images/top_bar/webmin_logo.jpg
/usr/local/webmin/webmin-1.300/mscstyle3/images/cats/webmin.jpg
/usr/local/webmin/webmin-1.210/cluster-webmin/cluster-webmin-lib.pl
/usr/local/webmin/webmin-1.210/webmin/webmin-lib.pl
/usr/local/webmin/webmin-1.210/lpadmin/webmin-driver.pl
/usr/local/webmin/webmin-1.300/webminlog/webminlog-lib.pl
/usr/local/webmin/webmin-1.300/status/webmin-monitor.pl
/usr/local/webmin/webmin-1.300/webmin/webmin-lib.pl
/usr/local/webmin/webmin-1.300/lpadmin/webmin-driver.pl
/usr/local/webmin/webmin-1.210/status/webmin-monitor.pl
/usr/local/webmin/webmin-1.210/webminlog/webminlog-lib.pl
/usr/local/webmin/webmin-1.300/cluster-software/status/webmin-monitor.pl
/usr/local/webmin/webmin-1.300/cluster-webmin/cluster-webmin-lib.pl
/usr/local/webmin/webmin-1.210/rbac/webmin_auth_attr
/usr/local/webmin/webmin-1.300/status/WEBMIN-STATUS-MIB.txt
/etc/vsftpd.conf.webmin.bak
/usr/local/webmin/webmin-1.210/webmin-daemon
/usr/local/webmin/webmin-1.210/webmin-gentoo-init
/usr/local/webmin/webmin-1.210/webmin-pam
/usr/local/webmin/webmin-1.300/webmin-daemon
/usr/local/webmin/webmin-1.300/webmin-pam
/usr/local/webmin/webmin-1.300/webmin-gentoo-init
/usr/local/webmin/webmin-1.210/status/WEBMIN-STATUS-MIB.txt
/usr/local/webmin/webmin-1.300/cluster-software/status/WEBMIN-STATUS-MIB.txt
/usr/local/webmin/webmin-1.300/rbac/webmin_auth_attr
/usr/local/webmin/webmin-1.210/mscstyle3/images/webmin_icon.png
/usr/local/webmin/webmin-1.300/mscstyle3/images/webmin_icon.png
/usr/local/webmin/webmin-1.210/webmin-caldera-init
/usr/local/webmin/webmin-1.210/webmin-init
/usr/local/webmin/webmin-1.300/webmin-init
/usr/local/webmin/webmin-1.300/webmin-caldera-init
/usr/local/webmin/webmin-1.210.tar.gz
/usr/local/webmin/webmin-1.210/images/webmin.xpm
/usr/local/webmin/webmin-1.210/images/webmin-mini.xpm
/usr/local/webmin/webmin-1.300/images/webmin-mini.xpm
/usr/local/webmin/webmin-1.300/images/webmin.xpm
```

---

### Post by matthewstory on 2006-10-27
the package may not be called webmin:

aptitude search webmin

to see if it has another name.

---

