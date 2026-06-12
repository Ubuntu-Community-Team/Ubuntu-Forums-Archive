---
title: "cant remove virtualbox"
date: 2007-10-17
forum: General Help
---

### Post by atlfalcons866 on 2007-10-17
hi
when i try to remove virtualbox i get this

Do you want to continue [Y/n]? y
(Reading database ... 233053 files and directories currently installed.)
Removing virtualbox-ose-modules-2.6.22-14-generic ...
 * Stopping VirtualBox kernel module vboxdrv                                    invoke-rc.d: initscript vboxdrv, action "stop" failed.
dpkg: error processing virtualbox-ose-modules-2.6.22-14-generic (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 virtualbox-ose-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by bodhi.zazen on 2007-10-17
I do not know if this will help, but you can try :

```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

---

