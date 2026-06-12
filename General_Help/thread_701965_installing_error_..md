---
title: "installing error ."
date: 2008-02-19
forum: General Help
---

### Post by hamzamusa on 2008-02-19
Hi i tried to install many software , but since i add some developer tools packages " python " the system stuck first cause wxpython version for many application which i removed  . and now i can't install many stuff as KDE , Xine , cause i got a strange error message that appears :

```
Setting up libxine1-ffmpeg (1.1.10-1~gutsy1) ...
rmdir: /usr/share/doc/libxine1-ffmpeg: Directory not empty
dpkg: error processing libxine1-ffmpeg (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libxine1-misc-plugins (1.1.10-1~gutsy1) ...
rmdir: /usr/share/doc/libxine1-misc-plugins: Directory not empty
dpkg: error processing libxine1-misc-plugins (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libxine1-plugins:
 libxine1-plugins depends on libxine1-ffmpeg (>= 1.1.10-1~gutsy1); however:
  Package libxine1-ffmpeg is not configured yet.
 libxine1-plugins depends on libxine1-misc-plugins (>= 1.1.10-1~gutsy1); however:
  Package libxine1-misc-plugins is not configured yet.
dpkg: error processing libxine1-plugins (--configure):
 dependency problems - leaving unconfigured
Setting up libxine1-x (1.1.10-1~gutsy1) ...
rmdir: /usr/share/doc/libxine1-x: Directory not empty
dpkg: error processing libxine1-x (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libxine1-console (1.1.10-1~gutsy1) ...
rmdir: /usr/share/doc/libxine1-console: Directory not empty
dpkg: error processing libxine1-console (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxine1-plugins (= 1.1.10-1~gutsy1) | libxine1-misc-plugins (= 1.1.10-1~gutsy1); however:
  Package libxine1-plugins is not configured yet.
  Package libxine1-misc-plugins is not configured yet.
 libxine1 depends on libxine1-x (= 1.1.10-1~gutsy1); however:
  Package libxine1-x is not configured yet.
 libxine1 depends on libxine1-console (= 1.1.10-1~gutsy1); however:
  Package libxine1-console is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xine-ui:
 xine-ui depends on libxine1 (>= 1.1.4); however:
  Package libxine1 is not configured yet.
 xine-ui depends on libxine1-ffmpeg; however:
  Package libxine1-ffmpeg is not configured yet.
dpkg: error processing xine-ui (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
Errors were encountered while processing:
 libxine1-ffmpeg
 libxine1-misc-plugins
 libxine1-plugins
 libxine1-x
 libxine1-console
 libxine1
 xine-ui
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried to locate the broken and orphanage packages and removed them , but the error keeps coming !!!

how to fix this error ?

---

