---
title: "Unable to remove lighttpd"
date: 2008-01-12
forum: General Help
---

### Post by schutzy on 2008-01-12
Hi.

I am having great difficulties in removing lighttpd.

Here is the full text-

root@warthog:/var/lib/dpkg/info# apt-get remove lighttpd
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
 lighttpd
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 848kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 87805 files and directories currently installed.)
Removing lighttpd ...
* Stopping web server lighttpd                                                                                                                       [fail]
invoke-rc.d: initscript lighttpd, action "stop" failed.
dpkg: error processing lighttpd (--remove):
subprocess pre-removal script returned error exit status 1
* Starting web server lighttpd                                                                                                                       [ ok ]
Errors were encountered while processing:
lighttpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@warthog:/var/lib/dpkg/info# dpkg --purge lighttpd
(Reading database ... 87805 files and directories currently installed.)
Removing lighttpd ...
* Stopping web server lighttpd                                                                                                                       [fail]
invoke-rc.d: initscript lighttpd, action "stop" failed.
dpkg: error processing lighttpd (--purge):
subprocess pre-removal script returned error exit status 1
* Starting web server lighttpd                                                                                                                       [ ok ]
Errors were encountered while processing:
lighttpd


Any help will be deeply appreciated!

Thanks!

---

### Post by tgalati4 on 2008-01-13
Try killing the server manually:

>top

Get the process id (PID) of the lighttpd

>sudo kill -9 PID

Then

>sudo apt-get remove lighttpd

If that fails, then boot into the rescue shell and try deleting it with a minimal boot.

---

