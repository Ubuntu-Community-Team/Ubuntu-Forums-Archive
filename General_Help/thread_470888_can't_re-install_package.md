---
title: "can't re-install package"
date: 2007-06-11
forum: General Help
---

### Post by jrcal on 2007-06-11
I had a broken installation of the netatalk AFP server package, which would neither remove nor reinstall.  Finally, I was able to remove it by running commands from a forum thread I can no longer find, something like:

$ sudo echo "..........
$ sudo apt-get remove netatalk

I even purged it with

$ sudo dpkg -P --force-all netatalk.  

All seemed good until I tried to re-install it, after apparently being purged, getting the error:

Setting up netatalk (2.0.3-5) ...
hostname: Unknown host
invoke-rc.d: initscript netatalk, action "start" failed.
dpkg: error processing netatalk (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 netatalk
E: Sub-process /usr/bin/dpkg returned an error code (1)


Trying to install, remove, purge now always gives me the that same error line:

invoke-rc.d: initscript netatalk, action "start" failed.

Even weirder, apt-get even gave me that netatalk initscript error when I tried to install a totally different package, netcat!!  That has since gone away, but I'm not sure how I did it. 

I've even tried removing all traces of netatalk from /var/lib/dpkg/status  and restarting, but attempting to reinstall gives me the same errors.   I have tried all this as root, of course.  

help!  any help greatly appreciated!!

---

### Post by jrcal on 2007-06-11
I found the command that allows me to apt-get remove netatalk successfully:

# echo "exit 0" > /etc/init.d/netatalk

even if I follow with a purge, then delete all reference to netatalk in var/lib/dpkg/status, the restart and try to reinstall, I still get the initscript failed error!!

---

