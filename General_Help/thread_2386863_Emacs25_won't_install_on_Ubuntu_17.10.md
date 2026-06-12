---
title: "Emacs25 won't install on Ubuntu 17.10"
date: 2018-03-11
forum: General Help
---

### Post by multios on 2018-03-11
This is a new installation. Only thing done after installation, was the automatic upgrading of system.
When trying to install emacs, here is what I got:
```
Setting up emacs25 (25.2+1-6) ...
Install emacsen-common for emacs25
emacsen-common: Handling install of emacsen flavor emacs25
emacs25: error while loading shared libraries: libotf.so.0: cannot open shared object file: No such file or directory
ERROR: install script from emacsen-common package failed
dpkg: error processing package emacs25 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 emacs25
E: Sub-process /usr/bin/dpkg returned an error code (1)


$ sudo apt install libotf0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libotf0 is already the newest version (0.9.13-3build1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
```

Solved somewhat.
Found out via irc that this is a bug and has been reported

---

