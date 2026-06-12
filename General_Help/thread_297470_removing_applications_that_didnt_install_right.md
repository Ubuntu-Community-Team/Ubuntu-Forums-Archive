---
title: "removing applications that didnt install right"
date: 2006-11-11
forum: General Help
---

### Post by pfusco on 2006-11-11
Installed a couple of apps that failed in the install procedure, now when updating, I get alot of error messages regarding the failed application (k3d)

Cant find it in add/ remove or when Ive searched for it, but when I do try to run it, it shows as needing to be completed

How do I resolve this problem

Not sure if the updates or programs Im trying to install are getting past this error

Thanks

---

### Post by bruenig on 2006-11-11
maybe a stupid question on my part, but have you tried doing
```
sudo apt-get remove whatever
```
Where whatever is the package you installed?

---

### Post by dannyboy79 on 2006-11-11
that will only remove the spps and not any config files, after the remove, then you want to do sudo aptitude purge whatprogram

---

### Post by pfusco on 2006-11-11
No, its not a stupid question. Im new to gnome and about a week new to ubuntu
thanks, Ill try that :)

oops, got this when running the remove command

dpkg: error processing k3d (--remove):
 subprocess pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 865, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 k3d
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

