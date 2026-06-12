---
title: "Need a hand fixing some broken packages"
date: 2012-12-05
forum: General Help
---

### Post by TheForumTroll on 2012-12-05
**Solved:**

/lib/init/upstart-job somehow was missing. According to the dates it happened way back in april (like what, 7-8 monthes ago?) and the server has been rebooted since. No idea how this didn't break everything.

The fix is to reinstall upstart:

```

sudo aptitude reinstall upstart

```

That's it!

Thanks to [kmathern in the Debian forum]("http://forums.debian.net/viewtopic.php?f=5&t=89494&p=464177#p464177").


------------------------------------
 
I got some broken packages that I can't seem to fix, so here's hoping someone can help me out :o

This is what i get:

```

server:~$ sudo aptitude install -f
The following partially installed packages will be configured:
  dbus resolvconf udev
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up resolvconf (1.63ubuntu16) ...
invoke-rc.d: unknown initscript, /etc/init.d/resolvconf not found.
dpkg: error processing resolvconf (--configure):
 subprocess installed post-installation script returned error exit status 100
No apport report written because MaxReports is reached already
                                                              Setting up udev (175-0ubuntu9.2) ...
invoke-rc.d: unknown initscript, /etc/init.d/udev not found.
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 100
No apport report written because MaxReports is reached already
                                                              Setting up dbus (1.4.18-1ubuntu1.3) ...
invoke-rc.d: unknown initscript, /etc/init.d/dbus not found.
dpkg: error processing dbus (--configure):
 subprocess installed post-installation script returned error exit status 100
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 resolvconf
 udev
 dbus
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up resolvconf (1.63ubuntu16) ...
invoke-rc.d: unknown initscript, /etc/init.d/resolvconf not found.
dpkg: error processing resolvconf (--configure):
 subprocess installed post-installation script returned error exit status 100
Setting up udev (175-0ubuntu9.2) ...
invoke-rc.d: unknown initscript, /etc/init.d/udev not found.
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 resolvconf
 udev


```

I must admit that I have no idea when this happened as it is a headless server that I seldom log into and it has been upgraded between Ubuntu versions once or twice as far as I remember, so that might be when they showed up(?).

---

### Post by zvacet on 2012-12-06
Try with 

```
sudo dpkg --configure -a
```

---

### Post by TheForumTroll on 2012-12-06
Sadly, that doesn't help:

```

Setting up resolvconf (1.63ubuntu16) ...
invoke-rc.d: unknown initscript, /etc/init.d/resolvconf not found.
dpkg: error processing resolvconf (--configure):
 subprocess installed post-installation script returned error exit status 100
Setting up udev (175-0ubuntu9.2) ...
invoke-rc.d: unknown initscript, /etc/init.d/udev not found.
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 resolvconf
 udev


```

Looks like some init scripts are broken, but I have no idea how to fix them. Removing (remove or purge) and installing again does nothing.

---

### Post by TheForumTroll on 2012-12-06
Think someone found the problem for me. I'll update later.

---

### Post by zvacet on 2012-12-06
Let us know how do you fix it.It will help others.Tnx!

---

