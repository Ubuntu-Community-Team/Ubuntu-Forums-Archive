---
title: "X-chm + Gnochm uninstall causes mime-type / GLib-CRITICAL problems"
date: 2007-01-15
forum: General Help
---

### Post by hannanjf on 2007-01-15
I have had gnochm installed on my edgy system (2.6.17-10-generic #2 SMP i686) for a while now without confronting any problems. The latter arrived when I installed x-chm as well. At this point, I can't recall if/what error I got at first, but I proceeded to try to uninstall gnochm and get the following:

```
jacob@localhost:~$ sudo aptitude remove gnochm
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REMOVED:
  gnochm
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 717kB will be freed.
Writing extended state information... Done
(Reading database ... 95889 files and directories currently installed.)
Removing gnochm ...
***
* Updating MIME database in /usr/share/mime...
Wrote 481 strings at 20 - 27f8
Wrote aliases at 27f8 - 29ac
Wrote parents at 29ac - 337c
Wrote literal globs at 337c - 33e0
Wrote suffix globs at 33e0 - 6768
Wrote full globs at 6768 - 678c
Wrote magic at 678c - be18
Wrote namespace list at be18 - be28
***

(update-desktop-database:13792): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnochm (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 gnochm
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
jacob@localhost:~$
```

I now get this whether I have x-chm installed or not.

I've filed a bug against gnochm (probably not the right place) here:
[https://launchpad.net/ubuntu/+source/gnochm/+bug/78592](https://launchpad.net/ubuntu/+source/gnochm/+bug/78592)

---

### Post by hannanjf on 2007-01-16
bump.

---

### Post by hannanjf on 2007-01-16
Problem solved.

Turns out that this problem is the result of a corrupted .desktop file, as described here:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=396439](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=396439)

As pointed out in the bug report, there is no easy way of finding out which of the files is corrupted.  I was able to do so by looking at the /usr/share/applications directory and subdirectories with nautilus.  I noticed one of the screensaver .desktop files wasn't using the "binary" icon that all the others were, so I backed it up, moved it, and re-ran aptitude.  This time, I had no errors.  In order to recreate an uncorrupted .desktop file, I ran:

```
sudo aptitude reinstall gnome-screensaver screensaver-default-images xscreensaver-data xscreensaver-gl
```

... and refreshed nautilus.  And there it was, with the proper icon.

I am not sure if the icon thing is a generalizable means of detecting corrupted .desktop files, or not, however.

---

