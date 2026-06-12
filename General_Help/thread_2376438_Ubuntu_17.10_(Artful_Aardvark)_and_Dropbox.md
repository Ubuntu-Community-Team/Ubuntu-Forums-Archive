---
title: "Ubuntu 17.10 (Artful Aardvark) and Dropbox"
date: 2017-11-02
forum: General Help
---

### Post by puntigilio on 2017-11-02
Long time Ubuntu user and very long long time linux user (from Yggdrasil, somebody remember it ?).

I'm using Ubuntu 17.10 (Artful Aardvark) with Gnome on my MacMini (6,1, late 2012, Intel® Core™ i5-3210M CPU @ 2.50GHz × 4, RAM 10 GB, HD 500 GB) with refind.

Dropbox icon in the panel is working erratically, and only if you install Topicon Plus extension. Ubuntu Appindicators is not enough.

When the icon is present is very small and right clicking does not show the Dropbox menu.

When the icon disappears I launch this script:

===============================================
#!/bin/bash
dropbox stop
env XDG_CURRENT_DESKTOP=Gnome dropbox start -i
===============================================

and the icon returns.

After launching the script the terminal shows:

sandro@macmini:~$ ./restart_dropbox 
Dropbox daemon stopped.
Starting Dropbox...dropbox: locating interpreter
dropbox: logging to /tmp/dropbox-antifreeze-MgSa9I
dropbox: initializing
dropbox: running python 2.7.11
dropbox: setting program path '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/dropbox'
dropbox: setting home path '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29'
dropbox: setting python path '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29:/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/python-packages-27.zip'
dropbox: python initialized
dropbox: running dropbox
dropbox: setting args
dropbox: applying overrides
dropbox: running main script
dropbox: load fq extension '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/cryptography.hazmat.bindings._constant_time.so'
dropbox: load fq extension '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/cryptography.hazmat.bindings._openssl.so'
dropbox: load fq extension '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/cryptography.hazmat.bindings._padding.so'
dropbox: load fq extension '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/psutil._psutil_linux.so'
dropbox: load fq extension '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/psutil._psutil_posix.so'
dropbox: load fq extension '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/linuxffi.pthread._linuxffi_pthread.so'
dropbox: load fq extension '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/tornado.speedups.so'
dropbox: load fq extension '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/cpuid.compiled._cpuid.so'
dropbox: load fq extension '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/linuxffi.resolv.compiled._linuxffi_resolv.so'
dropbox: load fq extension '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/posixffi.libc._posixffi_libc.so'
dropbox: load fq extension '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/librsyncffi.compiled._librsyncffi.so'
dropbox: load fq extension '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/linuxffi.sys.compiled._linuxffi_sys.so'
dropbox: load fq extension '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/PyQt5.QtWebKit.so'
dropbox: load fq extension '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/PyQt5.QtCore.so'
dropbox: load fq extension '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/PyQt5.QtNetwork.so'
dropbox: load fq extension '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/PyQt5.QtGui.so'
dropbox: load fq extension '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/PyQt5.QtWebKitWidgets.so'
dropbox: load fq extension '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/PyQt5.QtWidgets.so'
dropbox: load fq extension '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/PyQt5.QtPrintSupport.so'
dropbox: load fq extension '/home/sandro/.dropbox-dist/dropbox-lnx.x86_64-37.4.29/PyQt5.QtDBus.so'
Done!


There is something that I can do ?


Apart from this, Ubuntu Gnome is improving (though not yet refined as Unity :))

Thank you

Sandro

---

### Post by puntigilio on 2017-11-02
Addendum:

If in the script the line 
env XDG_CURRENT_DESKTOP=Gnome dropbox start -i
is changed in
env XDG_CURRENT_DESKTOP=Unity dropbox start -i

right click works !

---

