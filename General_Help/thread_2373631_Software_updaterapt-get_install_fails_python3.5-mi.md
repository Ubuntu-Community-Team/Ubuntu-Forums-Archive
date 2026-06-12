---
title: "Software updater/apt-get install fails: python3.5-minimal"
date: 2017-10-08
forum: General Help
---

### Post by iqdesigner on 2017-10-08
Hi,

I use 16.04 LTS. The popup appeared with the software updater (1 and 1/2 weeks ago as I remember) and I hit to install. The installer failed, and since then I cannot update.

With sudo apt-get install or sudo apt-get -f install I get:

```

$ sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-92 linux-headers-4.4.0-92-generic linux-image-4.4.0-92-generic linux-image-extra-4.4.0-92-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up python3.5-minimal (3.5.2-2ubuntu0~16.04.3) ...
Traceback (most recent call last):
  File "/usr/lib/python3.5/py_compile.py", line 186, in <module>
    sys.exit(main())
  File "/usr/lib/python3.5/py_compile.py", line 178, in main
    compile(filename, doraise=True)
  File "/usr/lib/python3.5/py_compile.py", line 143, in compile
    importlib._bootstrap_external._write_atomic(cfile, bytecode, mode)
  File "<frozen importlib._bootstrap_external>", line 106, in _write_atomic
NotADirectoryError: [Errno 20] Not a directory: '/usr/lib/python3.5/encodings/__pycache__/cp1258.cpython-35.pyc.140578933493296'
dpkg: error processing package python3.5-minimal (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python3.5:
 python3.5 depends on python3.5-minimal (= 3.5.2-2ubuntu0~16.04.3); however:
  Package python3.5-minimal is not configured yet.

dpkg: error processing package python3.5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 python3.5-minimal
 python3.5
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What I should do?

Thanks

---

### Post by ajgreeny on 2017-10-08
Try command ```
sudo dpkg --configure -a
sudo apt-get install -f
``` to try to correct any broken packages if you have any (it appears not but it is harmless if you have none) and then finish configuring the package **python3.5-minimal** which appears from the error not yet configured.

---

### Post by iqdesigner on 2017-10-10
> **ajgreeny said:**
> Try command ```
sudo dpkg --configure -a
sudo apt-get install -f
``` to try to correct any broken packages if you have any (it appears not but it is harmless if you have none) and then finish configuring the package **python3.5-minimal** which appears from the error not yet configured.

Hi ajgreeny,

The configure command is failing with same error:

```
$ sudo dpkg --configure -a
Setting up python3.5-minimal (3.5.2-2ubuntu0~16.04.3) ...
Traceback (most recent call last):
  File "/usr/lib/python3.5/py_compile.py", line 186, in <module>
    sys.exit(main())
  File "/usr/lib/python3.5/py_compile.py", line 178, in main
    compile(filename, doraise=True)
  File "/usr/lib/python3.5/py_compile.py", line 143, in compile
    importlib._bootstrap_external._write_atomic(cfile, bytecode, mode)
  File "<frozen importlib._bootstrap_external>", line 106, in _write_atomic
NotADirectoryError: [Errno 20] Not a directory: '/usr/lib/python3.5/encodings/__pycache__/cp1258.cpython-35.pyc.140087527460400'
dpkg: error processing package python3.5-minimal (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python3.5:
 python3.5 depends on python3.5-minimal (= 3.5.2-2ubuntu0~16.04.3); however:
  Package python3.5-minimal is not configured yet.

dpkg: error processing package python3.5 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python3.5-minimal
 python3.5


```

Very mysterious error, just by updating with the normal process

Thanks

---

