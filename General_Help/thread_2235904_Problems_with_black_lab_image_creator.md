---
title: "Problems with black lab image creator"
date: 2014-07-23
forum: General Help
---

### Post by webmanoffesto on 2014-07-23
Today I downloaded and attempted to install black-lab-image-creator-1.3.deb on my Ubuntu 14 machine. 
I got the error message 
"The Package is of bad quality:
The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organisation who provided this package file and include the details beneath."

Apparently the problem is "wrong-file-owner-uid-or-gid"

```
"Lintian check results for /home/tom/Downloads/black-lab-image-creator-1.3.deb:
E: BlackLabImageCreator: bad-package-name 
E: BlackLabImageCreator: package-not-lowercase 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid etc/ 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid etc/blacklabimager.conf 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid etc/blacklabimager/ 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid etc/blacklabimager/blacklabimager.version 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid etc/blacklabimager/customisolinux/ 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid etc/blacklabimager/isolinux/ 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid etc/blacklabimager/isolinux/isolinux.cfg.vesamenu 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid etc/blacklabimager/isolinux/splash.png 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid etc/blacklabimager/plymouth/ 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid etc/blacklabimager/plymouth/blacklablinux-theme/ 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid etc/blacklabimager/plymouth/blacklablinux-theme/blacklabimager-theme.plymouth 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid etc/blacklabimager/plymouth/blacklablinux-theme/blacklabimager-theme.script 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid etc/blacklabimager/plymouth/blacklablinux-theme/blacklablinux.png 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid etc/blacklabimager/plymouth/blacklablinux-theme/progress_bar.png 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid etc/blacklabimager/plymouth/blacklablinux-theme/progress_box.png 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid etc/blacklabimager/preseed/ 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid etc/blacklabimager/preseed/custom.seed 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid etc/blacklabimager/remastersys.version~ 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid usr/ 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid usr/bin/ 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid usr/bin/BlackLabImager 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid usr/bin/blacklabimager-skelcopy 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid usr/share/ 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid usr/share/applications/ 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid usr/share/doc/ 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid usr/share/doc/BlackLabImager/ 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid usr/share/doc/BlackLabImager/README 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid usr/share/doc/BlackLabImager/README~ 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid usr/share/doc/BlackLabImager/changelog.Debian.gz 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid usr/share/doc/BlackLabImager/copyright 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid usr/share/doc/BlackLabImager/copyright~ 1000/1000 
E: BlackLabImageCreator: wrong-file-owner-uid-or-gid usr/share/man/ 1000/1000
```"

---

### Post by Bucky Ball on 2014-07-23
*Post move to own thread.*

---

