---
title: "Moblock won't uninstall"
date: 2008-04-24
forum: General Help
---

### Post by Boffy on 2008-04-24
I've been trying moblock but it blocked everything! So I stopped it manually then tried to uninstall it but it won't let me. I get this output:

```
sudo apt-get --purge remove moblock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnfnetlink0 libnetfilter-queue1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  moblock*
0 upgraded, 0 newly installed, 1 to remove and 129 not upgraded.
1 not fully installed or removed.
After this operation, 274kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 125701 files and directories currently installed.)
Removing moblock ...
 * Stopping MoBlock moblock                                                                                           [fail] 
invoke-rc.d: initscript moblock, action "stop" failed.
dpkg: error processing moblock (--purge):
 subprocess pre-removal script returned error exit status 3
 * Starting MoBlock moblock                                                                                           [fail] 
invoke-rc.d: initscript moblock, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 moblock
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How do I get rid of it or install it so it works?

---

### Post by ryanhaigh on 2008-04-24
You could try stopping the app from running youself using something like 
```
sudo /etc/init.d/moblock stop
``` or boot into recovery mode (hopefully it won't start in this mode) and then retry the command you used above.

---

### Post by jre on 2008-04-30
If you still have problems uninstalling MoBlock then please post your version (dpkg --list moblock) and have a look at /var/log/moblock-control.log.

---

