---
title: "Conflicts with apt-get and K-3D"
date: 2007-05-11
forum: General Help
---

### Post by TheMatt on 2007-05-11
When I first installed Kubuntu, I was browsing around at all the apps. I had downloaded K-3D (package name is 'k3d') and played around with it a little. However, lately, it has been causing problems with apt-get.

This is the error I get when I try and upgrade my packages (there are a lot that need to be upgraded).
```
sudo apt-get upgrade
```
```
update-python-modules: error: /usr/share/python-support/k3d.dirs does not exist
dpkg: error processing /var/cache/apt/archives/k3d_0.6.6.0.ds1-1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 879, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 542, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/k3d_0.6.6.0.ds1-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

When I first did the upgrade, I had to fix some dependency problems.
```
sudo apt-get -f install
```

For some reason, I can't do anything with this program, not even uninstall it now. I'm not sure what to do. :confused: 

Thanks in advance. :)

---

