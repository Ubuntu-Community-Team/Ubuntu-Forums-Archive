---
title: "Python Dependency Issue"
date: 2006-11-04
forum: General Help
---

### Post by Burgresso on 2006-11-04
I think I have dependency problems with Python but I'm not sure what to do. I'm not sure how to fix dependency issues.

When I run system updates I often get this error message:
E: python-setuptools: subprocess post-installation script returned error exit status 1
E: python-kid: dependency problems - leaving unconfigured

If I try "sudo aptitude install python-kid" I get
```

me@mycomputer:~$ sudo aptitude install python-kid
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  automatix2 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up python-setuptools (0.6c3-1ubuntu4) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/setuptools.pth
pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/setuptools.pth
dpkg: error processing python-setuptools (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-kid:
 python-kid depends on python-setuptools (>= 0.6b3-1); however:
  Package python-setuptools is not configured yet.
dpkg: error processing python-kid (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-setuptools
 python-kid
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python-setuptools (0.6c3-1ubuntu4) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/setuptools.pth
pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/setuptools.pth
dpkg: error processing python-setuptools (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-kid:
 python-kid depends on python-setuptools (>= 0.6b3-1); however:
  Package python-setuptools is not configured yet.
dpkg: error processing python-kid (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-setuptools
 python-kid
me@mycomputer:~$ 

```

What should I do to fix this dependency issue?

Thanks so much,

burgresso

---

### Post by Burgresso on 2006-11-04
I've think I got this fixed...

sudo aptitude remove python-setuptools

Then I reinstalled em'. Looks good so far...:)

I think I'm good with this issue.

---

