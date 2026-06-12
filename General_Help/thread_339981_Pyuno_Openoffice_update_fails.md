---
title: "Pyuno Openoffice update fails"
date: 2007-01-16
forum: General Help
---

### Post by nexxus on 2007-01-16
Hi,

Edgy had really not been a very nice experience. Apt keeps giving me the same error. Please help, I'm desperate now, I don't want to have to redo the whole install, it's taken me a couple of weeks to get everything to where I want it.

The apt output:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python-uno
The following packages will be upgraded:
  python-uno
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/220kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 123491 files and directories currently installed.)
Preparing to replace python-uno 2.0.4-0ubuntu2 (using .../python-uno_2.0.4-0ubuntu4_i386.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 935, in run
    pkg.remove(runtimes, remove_script_files=True)
  File "/usr/bin/pycentral", line 693, in remove
    default_runtime.remove_byte_code(self.private_files)
AttributeError: 'NoneType' object has no attribute 'remove_byte_code'
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 935, in run
    pkg.remove(runtimes, remove_script_files=True)
  File "/usr/bin/pycentral", line 693, in remove
    default_runtime.remove_byte_code(self.private_files)
AttributeError: 'NoneType' object has no attribute 'remove_byte_code'
dpkg: error processing /var/cache/apt/archives/python-uno_2.0.4-0ubuntu4_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python-uno_2.0.4-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by nexxus on 2007-01-16
Managed to fix it by hacking the python code, 2nd time I've had to do that, looks like my python install is cracked.

---

### Post by jaiwithani on 2007-01-19
Same problem here. What's the hack? (I have Python 2.4 and 2.5 installed, which I suppose might be part of the problem. I recall hearing people having the same problem on the dapper-edgy upgrade).

---

