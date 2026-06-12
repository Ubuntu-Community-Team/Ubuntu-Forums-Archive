---
title: "Removing unneeded packages (Problem with python-gst0.10)"
date: 2007-02-10
forum: General Help
---

### Post by NickPresta on 2007-02-10
At one point, I installed python-gst0.10 for what ever reason. I don't need it anymore, apparently, but when I try to remove it, I get:

```
$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-gst0.10
The following packages will be REMOVED:
  python-gst0.10
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
Need to get 0B of archives.
After unpacking, 1409kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 114462 files and directories currently installed.)
Removing python-gst0.10 ...
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
dpkg: error processing python-gst0.10 (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 python-gst0.10
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any idea how to go about fixing this or what I should be searching for?

---

### Post by NickPresta on 2007-02-10
Subtle Bump. >_>

---

### Post by durand on 2007-02-23
.wysiwyg { background-attachment: scroll; background-repeat: repeat; background-position: 0% 0%; background-color: #ffffff; background-image: none; color: #666666; font-family: "Verdana [microsoft]", "Lucida [B&h]", "Arial [monotype]", "Helvetica [Adobe]", "Arial [monotype]"; font-style: normal; font-variant: normal; font-weight: 400; font-size: 10pt; line-height: normal } p { margin: 0px; }got the same annoying error here. problems with other packages as well so im not sure whether it is a problem with the python-gst package

---

### Post by NickPresta on 2007-03-12
Another bump.

I've tried aptitude (which fixed broken packages) but that didn't work either (so I installed some of the packages that aptitude removed) and no luck even still.

Any help in fooling APT into thinking python-gst0.10 is removed (I can delete the package from /usr/share/pycentral/python-gst0.10 and /usr/share/doc/python-gst0.10)?
I see:
```

/var/lib/dpkg/info/python-gst0.10.postinst
/var/lib/dpkg/info/python-gst0.10.list
/var/lib/dpkg/info/python-gst0.10.prerm
/var/lib/dpkg/info/python-gst0.10.md5sums

```

Is there anything specific I should do with those?

---

