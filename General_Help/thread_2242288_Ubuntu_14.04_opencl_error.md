---
title: "Ubuntu 14.04 opencl error"
date: 2014-08-31
forum: General Help
---

### Post by Tony T on 2014-08-31
Ubuntu 14.04 opencl error

Please help with this error, I don't know where to start. I get this error 
whenever I try to install or remove software packages:


Setting up opencl-devel (1.2-4.4.0.117) ...
warning: `/usr/include/CL' exists and not a symlink; alternative `opencl-headers' will not be installed.
dpkg: error processing package opencl-devel (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 opencl-devel
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Tony T on 2014-09-01
Fixed by doing:

sudo dpkg --remove  opencl-devel

---

