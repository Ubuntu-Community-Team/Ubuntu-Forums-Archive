---
title: "Problem with Google Chrome"
date: 2014-12-25
forum: General Help
---

### Post by milen2 on 2014-12-25
Hello. I accidentally deleted the "google" folder in "opt" and Google Chrome stopped working. So I tried removing it and this appeared. How can I reinstall it ?
```
 davion100@milen:~$  sudo apt-get remove google-chrome-stableReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gstreamer-0.10 rsync
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  google-chrome-stable
0 upgraded, 0 newly installed, 1 to remove and 328 not upgraded.
1 not fully installed or removed.
After this operation, 183 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 127670 files and directories currently installed.)
Removing google-chrome-stable ...
xdg-icon-resource: size argument must be numeric
Try 'xdg-icon-resource --help' for more information.
dpkg: error processing google-chrome-stable (--remove):
 subprocess installed pre-removal script returned error exit status 1
xdg-icon-resource: size argument must be numeric
Try 'xdg-icon-resource --help' for more information.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 google-chrome-stable
E: Sub-process /usr/bin/dpkg returned an error code (1)
davion100@milen:~$ 

```

---

### Post by monkeybrain20122 on 2014-12-25
Well you need sudo to delete it, how could it be 'accidental'??!! Anyway, it is easist just to reinstall Chrome. Since when you installed the first time it has set up a repository in your system, you can just reinstall with synaptic or the software centre. Since all your bookmarks and settings are stored in your /home they are not affected by removing the folder in /opt and reinstalling. Everything will be restored to where it was when you reinstall Chrome.

---

