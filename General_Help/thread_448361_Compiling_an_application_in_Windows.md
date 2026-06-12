---
title: "Compiling an application in Windows"
date: 2007-05-19
forum: General Help
---

### Post by RudolfMDLT on 2007-05-19
Hi there,

I've posted earlier on finding a security suite. I've found two. The one works on Windows aswell except I have no idea how to compile from source in windows? Any ideas?

This is the app i need to download:
[http://sourceforge.net/projects/camtown/](http://sourceforge.net/projects/camtown/)
[http://sourceforge.net/project/showfiles.php?group_id=194967&package_id=229957&release_id=503921](http://sourceforge.net/project/showfiles.php?group_id=194967&package_id=229957&release_id=503921)

Thank you very much!

---

### Post by jtraub on 2007-05-19
Try to install cygwin and compile in this environment

---

### Post by public_void on 2007-05-19
Under Cygwin gcc with link against cygwin1.dll unless the compiler option -mno-cygw is used to force gcc to link against Windows standard dlls. Maybe use  the Dev-c++ IDE which has the minGW compiler. 

After reading ./doc/setup and deployment.txt in the source download there is a Dev-c++ dev project file. And steps for building using Dev-c++.

---

