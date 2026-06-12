---
title: "gnome video arcade help"
date: 2008-01-29
forum: General Help
---

### Post by onewill on 2008-01-29
Was trying to compile gva and got this message

> william@illest-comp:~$ cd /home/william/Desktop/gnome-video-arcade-0.5.5
william@illest-comp:~/Desktop/gnome-video-arcade-0.5.5$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... yes
checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.10) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

william@illest-comp:~/Desktop/gnome-video-arcade-0.5.5$ 


I'm almost positive that my gtk was up to date. Not quite sure where to go from here.:confused:

---

### Post by mfbarnes on 2008-03-14
You probably need to install libgtk2.0-dev, which contains the development files necessary for building.

---

