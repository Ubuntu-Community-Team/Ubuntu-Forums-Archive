---
title: "Problem Reinstalling Compiz"
date: 2008-05-01
forum: General Help
---

### Post by toallpointswest on 2008-05-01
I had to uninstall compiz-git ([from this thread]("http://ubuntuforums.org/showthread.php?t=763829")) from my system (it didn't work well with ATI's drivers) and when attempting to reinstall the compiz that shipped with Hardy I receive this error. 

```
###@####:~/Downloads$ sudo apt-get -f install
[sudo] password for ####:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  x11proto-resource-dev pymacs emacs21-common python-mode
  compizconfig-backend-gconf python-pyrex pyrex-mode libwnck-dev
  libmetacity-dev emacsen-common emacs21-bin-common gitweb emacs21
  libgnome-window-settings-dev compiz-fusion-plugins-extra xaw3dg libxres-dev
  compiz-fusion-plugins-main compiz-gnome liblockfile1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up compizconfig-settings-manager (0.7.4-0ubuntu2) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing compizconfig-settings-manager (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 compizconfig-settings-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
```

Any suggestions? Oddly enough ccsm launches fine. 
Thanks!

---

### Post by Zorael on 2008-05-01
What errors do you get when you try to uninstall it?
```
$ sudo aptitude purge ~ncompiz ~nemerald ~nlibdeco
```

---

### Post by toallpointswest on 2008-05-03
None, processed smoothly.

---

### Post by Zorael on 2008-05-03
So, does it work now? I'm confused. Else try this, as well.
```
$ sudo dpkg --purge compizconfig-settings-manager
```

---

