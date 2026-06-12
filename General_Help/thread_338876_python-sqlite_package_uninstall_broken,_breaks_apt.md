---
title: "python-sqlite package uninstall broken, breaks apt too"
date: 2007-01-15
forum: General Help
---

### Post by nexxus on 2007-01-15
I tried to install python-sqlite via apt and it didn't quite work out so I got the code, compiled & installed, all fine. But I think the failed install has messed up somehow.

Apt tries to remove it every time I run Synaptic and that tries to run some python script which fails with the ffg traceback:

```
Removing python-sqlite ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 930, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 195, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 120, in default_version
    _default_version = link = os.readlink('/usr/bin/python')
OSError: [Errno 22] Invalid argument: '/usr/bin/python'
dpkg: error processing python-sqlite (--remove):
 subprocess pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 861, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 195, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 120, in default_version
    _default_version = link = os.readlink('/usr/bin/python')
OSError: [Errno 22] Invalid argument: '/usr/bin/python'
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-sqlite
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas, it's really annoying the hell out of me.

---

### Post by nexxus on 2007-01-15
*bumpity*

Any ideas? Desperate here.

---

