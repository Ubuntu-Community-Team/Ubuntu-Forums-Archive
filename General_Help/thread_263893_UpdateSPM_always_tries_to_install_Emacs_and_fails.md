---
title: "Update/SPM always tries to install Emacs and fails"
date: 2006-09-23
forum: General Help
---

### Post by jslmsca on 2006-09-23
I'm not sure exactly which forum this issue is best suited for.

I was trying to get a more colourful version of Emacs installed but failed.  I eventually was able to get back to the default version but now, Add/Remove Programs, Synaptic Package Manager and the automatic Updates always tries to install Emacs and fails.  The default version of Emacs still works (thankfully!) and whatever else needs to be installed seems to install safely.  However, I'd like to remove the following errors from happening every time but I'm not sure where to look.  An install script somewhere?

Thanks in advance.

emacs-install emacs21
install/dictionaries-common: Byte-compiling for emacsen flavour emacs21
cp: cannot stat `/usr/share/emacs/site-lisp/dictionaries-common/debian-ispell.el': No such file or directory
emacs-install: /usr/lib/emacsen-common/packages/install/dictionaries-common emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 2.
dpkg: error processing emacs21 (--configure):
 subprocess post-installation script returned error exit status 1

.
.
.

Errors were encountered while processing:
 emacs21
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Setting up emacs21 (21.4a-3ubuntu2) ...
emacs-install emacs21
install/dictionaries-common: Byte-compiling for emacsen flavour emacs21
cp: cannot stat `/usr/share/emacs/site-lisp/dictionaries-common/debian-ispell.el': No such file or directory
emacs-install: /usr/lib/emacsen-common/packages/install/dictionaries-common emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 2.
dpkg: error processing emacs21 (--configure):
 subprocess post-installation script returned error exit status 1

---

### Post by jslmsca on 2006-09-23
I tried the following:

laptop:~$ sudo apt-get remove emacs21
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  emacs21
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 6050kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 78461 files and directories currently installed.)
Removing emacs21 ...
emacs-remove emacs21
emacsen-common: Handling removal of emacsen flavor emacs21
emacsen-common: purging byte-compiled files for emacs21
remove/dictionaries-common: Purging byte-compiled files for flavour emacs21


I then needed to re-install Emacs and used the simple Add/Remove program interface.  The errors are still there.

---

### Post by jslmsca on 2006-09-24
bump... My only unresolved issue with Ubuntu at the moment...

---

### Post by jslmsca on 2006-09-27
bump

---

