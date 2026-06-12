---
title: "Removing nvidia-glx"
date: 2007-04-21
forum: General Help
---

### Post by Mau on 2007-04-21
I cannot remove nvidia-glx (I want to install nvidia-glx-new to get direct rendering), but I keep getting an error:

```
carl@virltron:~$ sudo apt-get remove nvidia-glx
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  nvidia-glx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 15.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 161090 files and directories currently installed.)
Removing nvidia-glx ...
rm: cannot remove `/usr/lib/libGL.so': No such file or directory
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1.2' with
  different file `/usr/lib/nvidia/libGL.so.1.2.xlibmesa', not allowed
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

How can I do this?

---

### Post by pseudonym on 2007-04-21
Try using the '--purge' option (which is always good to do anyway) -

sudo apt-get --purge remove nvidia-glx

---

### Post by duncDescent on 2008-04-06
Hi, I'm having the same problem in that i cannot remove Nvidia-glx.

After trying a purge I get the following error:

The following packages were automatically installed and are no longer required:
  debhelper libpthread-stubs0 libgl1-mesa-dev po-debconf intltool-debian
  x11proto-kb-dev mesa-common-dev xtrans-dev gettext x11proto-input-dev
  libxcb-xlib0-dev libglu1-mesa-dev libxau-dev html2text libx11-dev
  libxcb1-dev x11proto-core-dev dpatch libxdmcp-dev libpthread-stubs0-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  nvidia-glx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 22.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 102062 files and directories currently installed.)
Removing nvidia-glx ...
dpkg-divert: error checking `/usr/lib32/libGL.so.1': No such file or directory
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)
duncan@duncan-desktop:~$  


Cant remove/or purge via packet installer as I get:

There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages.


Running Kubuntu 8.04 with a Nvidia8500GT card.

---

### Post by hellfeuer on 2008-04-24
I had a similar problem.

Does /usr/lib32 exist? If it doesn't, just do a mkdir /usr/lib32 and try again

---

### Post by aboutblank on 2008-04-26
> **hellfeuer said:**
> I had a similar problem.

Does /usr/lib32 exist? If it doesn't, just do a mkdir /usr/lib32 and try again

Thanks. This worked for me!

---

### Post by rotalever on 2008-04-26
I had an error similar to that of the thread starter. I was using nvidia-glx-new, but nvidia-glx configurations were still installed. I could not remove them, because I got the error. The following helped me:
```

sudo dpkg --purge nvidia-glx-new
sudo dpkg --purge nvidia-glx
sudo apt-get install nvidia-glx-new

```

---

### Post by Gorromog on 2008-07-19
mkdir: cannot create directory `/usr/lib32': Permission denied

this is the error message i get while trying to make that directory. Any help?

---

### Post by hellfeuer on 2008-07-19
use sudo

sudo mkdir /usr/lib32

---

