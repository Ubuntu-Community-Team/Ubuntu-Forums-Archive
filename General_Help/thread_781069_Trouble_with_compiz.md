---
title: "Trouble with compiz"
date: 2008-05-04
forum: General Help
---

### Post by dtcheney on 2008-05-04
Hey everyone. I am new to linux and am having trouble with compiz. I am running ubuntu 8.04. When I enable the desktop cube and close advanced settings, nothing happens. When I log back in, it is disabled. I keep getting error messages after I try to download anything. Here is what I get:

Setting up compizconfig-settings-manager (0.7.4-0ubuntu2) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing compizconfig-settings-manager (--configure):
 subprocess post-installation script returned error exit status 1
Setting up fusion-icon (0.0.0+git20071028-2ubuntu2) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing fusion-icon (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 compizconfig-settings-manager
 fusion-icon
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please let me know what you think.

---

### Post by dtcheney on 2008-05-04
here is what i get when i run compiz --replace:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5955 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present.

---

### Post by Zorael on 2008-05-04
```
$ sudo aptitude purge compizconfig-settings-manager fusion-icon
$ sudo dpkg --purge compizconfig-settings-manager
$ sudo dpkg --purge fusion-icon
$ sudo aptitude install compizconfig-settings-manager fusion-icon
```

As for Compiz being disabled, after entering the above commands fusion-icon should hopefully work, so add it to Sessions to make it load upon login.

Alternatively, look in your menus for Visual Effects and enable stuff there.

---

### Post by dtcheney on 2008-05-04
Thanks. Everything seems to be working fine now. Most everything has an example picture beside it and works. Some though, do not. They look like they won't work, but I haven't tried them either. Thanks again though.

---

