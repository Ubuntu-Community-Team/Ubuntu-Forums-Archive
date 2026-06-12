---
title: "Installation (kindof) Fails"
date: 2015-09-13
forum: General Help
---

### Post by cranerja on 2015-09-13
I was installing i-Nex when I recieved the error "E: Sub-process /usr/bin/dpkg returned an error code (1)". I was still able to use the program after this error code. Purging the program and reinstalling does not remove the error. When I run "dpkg --configure -a" I get:
```
Setting up i-nex (7.4.0+bzr887+20150112~ubuntu14.04.1) ...dpkg: error processing package i-nex (--configure):
 subprocess installed post-installation script returned error exit status 6
Processing triggers for menu (2.1.46ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 i-nex

```
Because I can still run upgrades, it has not really affected me but It does cause issues with the GUI updater. Is there any solution for this?
Ubuntu 14.04.

---

### Post by v3.xx on 2015-09-14
Try running an update in terminal and see what errors you get.

---

### Post by cranerja on 2015-09-14
> **v3.xx said:**
> Try running an update in terminal and see what errors you get.
It completes but I get the  "E: Sub-process /usr/bin/dpkg returned an error code (1)" message.

---

### Post by v3.xx on 2015-09-15
Check out this thread, may hit on something

[http://ubuntuforums.org/showthread.php?t=1642173](http://ubuntuforums.org/showthread.php?t=1642173)

---

