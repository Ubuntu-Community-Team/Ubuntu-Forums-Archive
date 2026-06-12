---
title: "How to fix a badly broken package?"
date: 2008-01-12
forum: General Help
---

### Post by charlieg on 2008-01-12
I'm having a lot of trouble (an unbootable system) and I can't really do anything with apt because it won't get past the package powernowd that seems to be in a very sorry state.

Anybody got any recommendations of how to fix this?

```
root@localhost:/# dpkg -r --force-all powernowd
(Reading database ... 181499 files and directories currently installed.)
Removing powernowd ...
invoke-rc.d: initscript powernowd, action "stop" failed.
dpkg: error processing powernowd (--remove):
 subprocess pre-removal script returned error exit status 1
invoke-rc.d: initscript powernowd, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 powernowd

root@localhost:/# dpkg -P powernowd
(Reading database ... 181499 files and directories currently installed.)
Removing powernowd ...
invoke-rc.d: initscript powernowd, action "stop" failed.
dpkg: error processing powernowd (--purge):
 subprocess pre-removal script returned error exit status 1
invoke-rc.d: initscript powernowd, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 powernowd

root@localhost:/# dpkg --configure powernowd
Setting up powernowd (0.97-2ubuntu2) ...
invoke-rc.d: initscript powernowd, action "start" failed.
dpkg: error processing powernowd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 powernowd
```

---

### Post by dcstar on 2008-01-12
> **charlieg said:**
> I'm having a lot of trouble (an unbootable system) and I can't really do anything with apt because it won't get past the package powernowd that seems to be in a very sorry state.

Anybody got any recommendations of how to fix this?


Delete the package, delete any cached copy of it and the download and reinstall it.

---

### Post by charlieg on 2008-01-14
Ok, thanks for the tip.

In the end I did this - which is dangerous, btw, for any casual readers:

```
find / -name powernowd* -exec rm {} \;
```

(Needs to be done as su)

Seemed to make more progress.  We'll see, I'm doing all this in a chrooted environment so there were configure issues related to that (since /proc etc isn't set up) when I did a subsuquent aptitude upgrade.

I'll report back if there's anything else to report after I boot in.  (Nothing to report being 'success!')

---

### Post by charlieg on 2008-01-14
In the end a few more steps were required, found here:
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/hppa/linux-upgrade.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/hppa/linux-upgrade.html)

Basically for several of the packages to configure in the chroot environment, I needed to mount /proc and /sys using the following commands:

```
root@localhost:/# mount -t proc proc /proc
root@localhost:/# mount -t sysfs sysfs /sys
```

After that it all worked.  Still not booted it yet but, hopefully, it should boot successfully this time as everything is supposedly installed correctly!

---

### Post by charlieg on 2008-02-11
Just in case anybody is reading - at some point in the last 2 weeks a Hardy Heron update fixed the booting issue.  So my Hardy install now works!  Yay! :D

---

