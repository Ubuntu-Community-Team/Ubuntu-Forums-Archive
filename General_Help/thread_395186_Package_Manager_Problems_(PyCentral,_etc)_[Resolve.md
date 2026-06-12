---
title: "Package Manager Problems (PyCentral, etc) [Resolved]"
date: 2007-03-27
forum: General Help
---

### Post by NickPresta on 2007-03-27
```
$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages will be upgraded:
  python-uno
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
18 not fully installed or removed.
Need to get 0B/220kB of archives.
After unpacking, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 116035 files and directories currently installed.)
Preparing to replace python-uno 2.0.4-0ubuntu4 (using .../python-uno_2.0.4-0ubuntu5_i386.deb) ...
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
dpkg: error processing /var/cache/apt/archives/python-uno_2.0.4-0ubuntu5_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python-uno_2.0.4-0ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Apt now seems broken. I would appreciate some help.
If you need more information, just ask.

Thank you.


**EDIT:** *sigh* Forgive me. I need to use Google more. 
Solution here: [http://www.ubuntuforums.org/showpost.php?p=1916251](http://www.ubuntuforums.org/showpost.php?p=1916251)

---

