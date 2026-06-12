---
title: "Dropbox headache"
date: 2019-12-31
forum: General Help
---

### Post by zkab on 2019-12-31
I switched from xubuntu (xfce) to ubuntu (gnome) just to test.
Tried to install Dropbox but only to got ...
Could not start Dropbox daemon.
Make sure your computer meets the minimum requirements.

In xubuntu installation went without problems ... how come ubuntu/gnome have problems.
Is there a solution?

Happy New Year to All of You !!!

---

### Post by howefield on 2019-12-31
"ubuntu/gnome" don't have problems with Dropbox as a rule.

Possibly an unsupported file system ?

[https://help.dropbox.com/installs-integrations/desktop/system-requirements](https://help.dropbox.com/installs-integrations/desktop/system-requirements)

---

### Post by zkab on 2019-12-31
Made a plain installation of ubuntu 18.04 LTE 
My file system is ext4 ... here is my fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme1n1p2 during installation
UUID=a1c403f4-9558-4ec0-8b1d-3bc612d8878c /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme1n1p1 during installation
UUID=B142-3135  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
UUID=46b4e179-b5b4-4c25-8d97-4ed5c95f177e   /home               ext4    errors=remount-ro 0       1

Is there a possibility to see some log file for DBox installation to check what went wrong?

---

### Post by zkab on 2019-12-31
I have also Glibc 2.19 or later which is also a requirement.
||/ Name                         Version             Architecture        Description
+++-============================-===================-===================-=============================================================
ii  libc6:amd64                  2.27-3ubuntu1       amd64               GNU C Library: Shared libraries

---

### Post by zkab on 2020-01-01
Apparently I have installed Dropbox ...

||/ Name                         Version             Architecture        Description
+++-============================-===================-===================-=============================================================
ii  dropbox                      2019.02.14          amd64               cloud synchronization engine - CLI and Nautilus extension


When giving 'dropbox start' I get this ...

```
Starting Dropbox...dropbox: locating interpreter
dropbox: logging to /tmp/dropbox-antifreeze-ZwPbjd
dropbox: initializing
dropbox: initializing python 3.7.5
dropbox: setting program path '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/dropbox'
dropbox: setting python path '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138:/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/python-packages.zip'
dropbox: python initialized
dropbox: running dropbox
dropbox: setting args
dropbox: applying overrides
dropbox: running main script
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/cryptography.hazmat.bindings._constant_time.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/cryptography.hazmat.bindings._openssl.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/cryptography.hazmat.bindings._padding.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/psutil._psutil_linux.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/psutil._psutil_posix.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/linuxffi.pthread._linuxffi_pthread.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/cpuid.compiled._cpuid.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/apex._apex.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/tornado.speedups.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/linuxffi.resolv.compiled._linuxffi_resolv.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/librsyncffi.compiled._librsyncffi.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/linuxffi.sys.compiled._linuxffi_sys.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/posixffi.libc._posixffi_libc.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/linuxffi.gnu.compiled._linuxffi_gnu.cpython-37m-x86_64-linux-gnu.so'
Traceback (most recent call last):
  File "dropbox/client/main.pyc", line 7979, in main
  File "dropbox/client/main.pyc", line 7903, in main_startup
  File "dropbox/client/main.pyc", line 952, in __init__
  File "dropbox/sync_engine_boundary/factory.pyc", line 147, in make_default_file_system
  File "dropbox/sync_engine_boundary/factory.pyc", line 99, in __init__
  File "dropbox/sync_engine_boundary/factory.pyc", line 118, in _initialize_classes
  File "dropbox/sync_engine/nucleus/classic_client/sync_engine.pyc", line 278, in <module>
  File "dropbox/sync_engine/nucleus/classic_client/thin_adapter/in_proc.pyc", line 98, in <module>
  File "dropbox/sync_engine/nucleus/classic_client/wrapped_thin_client.pyc", line 26, in <module>
  File "dropbox/sync_engine/nucleus/thin_client/client.pyc", line 28, in <module>
  File "dropbox/foundation/metrics/amp/remote_sink.pyc", line 10, in <module>
ImportError: libatomic.so.1: cannot open shared object file: No such file or directory
!! dropbox: fatal python exception:
['Traceback (most recent call last):\n', '  File "dropbox/client/main.pyc", line 7979, in main\n', '  File "dropbox/client/main.pyc", line 7903, in main_startup\n', '  File "dropbox/client/main.pyc", line 952, in __init__\n', '  File "dropbox/sync_engine_boundary/factory.pyc", line 147, in make_default_file_system\n', '  File "dropbox/sync_engine_boundary/factory.pyc", line 99, in __init__\n', '  File "dropbox/sync_engine_boundary/factory.pyc", line 118, in _initialize_classes\n', '  File "dropbox/sync_engine/nucleus/classic_client/sync_engine.pyc", line 278, in <module>\n', '  File "dropbox/sync_engine/nucleus/classic_client/thin_adapter/in_proc.pyc", line 98, in <module>\n', '  File "dropbox/sync_engine/nucleus/classic_client/wrapped_thin_client.pyc", line 26, in <module>\n', '  File "dropbox/sync_engine/nucleus/thin_client/client.pyc", line 28, in <module>\n', '  File "dropbox/foundation/metrics/amp/remote_sink.pyc", line 10, in <module>\n', 'ImportError: libatomic.so.1: cannot open shared object file: No such file or directory\n'] (error 3)

The Dropbox daemon is not installed!
Run "dropbox start -i" to install the daemon

```

When I give the command 'dropbox start -i' I get following

```
Starting Dropbox...dropbox: locating interpreter
dropbox: logging to /tmp/dropbox-antifreeze-GgdKE1
dropbox: initializing
dropbox: initializing python 3.7.5
dropbox: setting program path '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/dropbox'
dropbox: setting python path '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138:/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/python-packages.zip'
dropbox: python initialized
dropbox: running dropbox
dropbox: setting args
dropbox: applying overrides
dropbox: running main script
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/cryptography.hazmat.bindings._constant_time.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/cryptography.hazmat.bindings._openssl.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/cryptography.hazmat.bindings._padding.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/psutil._psutil_linux.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/psutil._psutil_posix.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/linuxffi.pthread._linuxffi_pthread.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/cpuid.compiled._cpuid.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/apex._apex.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/tornado.speedups.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/linuxffi.resolv.compiled._linuxffi_resolv.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/librsyncffi.compiled._librsyncffi.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/linuxffi.sys.compiled._linuxffi_sys.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/posixffi.libc._posixffi_libc.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/forsete/.dropbox-dist/dropbox-lnx.x86_64-87.4.138/linuxffi.gnu.compiled._linuxffi_gnu.cpython-37m-x86_64-linux-gnu.so'
Traceback (most recent call last):
  File "dropbox/client/main.pyc", line 7979, in main
  File "dropbox/client/main.pyc", line 7903, in main_startup
  File "dropbox/client/main.pyc", line 952, in __init__
  File "dropbox/sync_engine_boundary/factory.pyc", line 147, in make_default_file_system
  File "dropbox/sync_engine_boundary/factory.pyc", line 99, in __init__
  File "dropbox/sync_engine_boundary/factory.pyc", line 118, in _initialize_classes
  File "dropbox/sync_engine/nucleus/classic_client/sync_engine.pyc", line 278, in <module>
  File "dropbox/sync_engine/nucleus/classic_client/thin_adapter/in_proc.pyc", line 98, in <module>
  File "dropbox/sync_engine/nucleus/classic_client/wrapped_thin_client.pyc", line 26, in <module>
  File "dropbox/sync_engine/nucleus/thin_client/client.pyc", line 28, in <module>
  File "dropbox/foundation/metrics/amp/remote_sink.pyc", line 10, in <module>
ImportError: libatomic.so.1: cannot open shared object file: No such file or directory
!! dropbox: fatal python exception:
['Traceback (most recent call last):\n', '  File "dropbox/client/main.pyc", line 7979, in main\n', '  File "dropbox/client/main.pyc", line 7903, in main_startup\n', '  File "dropbox/client/main.pyc", line 952, in __init__\n', '  File "dropbox/sync_engine_boundary/factory.pyc", line 147, in make_default_file_system\n', '  File "dropbox/sync_engine_boundary/factory.pyc", line 99, in __init__\n', '  File "dropbox/sync_engine_boundary/factory.pyc", line 118, in _initialize_classes\n', '  File "dropbox/sync_engine/nucleus/classic_client/sync_engine.pyc", line 278, in <module>\n', '  File "dropbox/sync_engine/nucleus/classic_client/thin_adapter/in_proc.pyc", line 98, in <module>\n', '  File "dropbox/sync_engine/nucleus/classic_client/wrapped_thin_client.pyc", line 26, in <module>\n', '  File "dropbox/sync_engine/nucleus/thin_client/client.pyc", line 28, in <module>\n', '  File "dropbox/foundation/metrics/amp/remote_sink.pyc", line 10, in <module>\n', 'ImportError: libatomic.so.1: cannot open shared object file: No such file or directory\n'] (error 3)

```

So how do I fix this?

---

### Post by maglin2 on 2020-01-01
Possibly this?
[https://askubuntu.com/questions/1192704/i-cant-install-dropbox-client-cannont-open-libatomic-so-1?noredirect=1](https://askubuntu.com/questions/1192704/i-cant-install-dropbox-client-cannont-open-libatomic-so-1?noredirect=1)

---

### Post by zkab on 2020-01-01
Solved the problem ...
[https://github.com/cui-unige/outils-formels-modelisation-2018/issues/39](https://github.com/cui-unige/outils-formels-modelisation-2018/issues/39)

---

### Post by zkab on 2020-01-01
Thanks for your help ...

---

### Post by zkab on 2020-01-01
Also the link said ... NOTE: This library is installed with Google Chrome, so if you had have the browser installed in your system you wouldn't have seen the issue.
But I had Chrome install and but 'libatomic1' was not install ... did it manually
Now it works OK

---

