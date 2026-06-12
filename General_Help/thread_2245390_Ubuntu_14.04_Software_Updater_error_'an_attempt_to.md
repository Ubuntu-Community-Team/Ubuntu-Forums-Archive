---
title: "Ubuntu 14.04 Software Updater error 'an attempt to commit /etc changes to bzr failed'"
date: 2014-09-23
forum: General Help
---

### Post by hockeybum27 on 2014-09-23
Running Ubuntu 14.041 x64 (upgraded from 12.04) on Dell Latitude E600 series.

When I try to apply recommended updates - specifically those under 'Ubuntu base' I get the error:
(Window title: Debconf on *mymachinename*)
> An attempt to commit /etc changes to bzr failed.

You may manually resolve the issues with the uncommitted changes before continuing.

At the same time, in the details of the Software Updater window, I show

```
bzr: warning: skipping /etc/X11/core (larger than add.maximum_file_size of 20000000 bytes) 
Committing to: /etc/ [0] - Stage 1/5 
bzr: ERROR: No changes to commit. Please 'bzr add' the files you want to commit, or use --unchanged to force an empty commit. 

```

Any ideas on how to proceed would be much appreciated - happy to do the work but just not sure what 'the work' is.  For example, I'm not familiar with bzr (I know it's a version control utility used by Ubuntu for updates and such).

Thanks in advance!

---

### Post by bapoumba on 2014-09-24
May be a workaround here, post #5 :
[https://bugs.launchpad.net/ubuntu/+source/etckeeper/+bug/1058301](https://bugs.launchpad.net/ubuntu/+source/etckeeper/+bug/1058301)

---

### Post by hockeybum27 on 2014-09-26
This appears to have done the trick; specifically, I followed the advice in that thread to add the file to the non-monitor list.  It appears to have done the trick.  This  is still a bug according to launchpad, one that's been around for a couple of years :(

thanks bapoumba!

---

### Post by bapoumba on 2014-09-27
Thanks for marking your thread as solved and glad to see the workaround worked :)

---

