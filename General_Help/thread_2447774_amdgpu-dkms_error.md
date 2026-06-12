---
title: "amdgpu-dkms error"
date: 2020-07-25
forum: General Help
---

### Post by backspin on 2020-07-25
Just performed another package upgrade and noticed a a dkms error, and was wondering what it takes to fix it?

Appears amdgpu-dkms was removed and re-installed what looks like the same version (see below) however later on the error is "nux-headers-5.7.10-050710-generic".  The current kernel on this machine is 5.7.10. 

Any thoughts on how I get around this?  Do I need to install a 5.6 kernel? 

Setting up amdgpu-dkms (1:5.6.0.13-1089974) ...
Removing old amdgpu-5.6.0.13-1089974 DKMS files...

------------------------------
Deleting module version: 5.6.0.13-1089974
completely from the DKMS tree.
------------------------------
Done.
Loading new amdgpu-5.6.0.13-1089974 DKMS files...
Building for 5.7.10-050710-generic
Building for architecture x86_64
Building initial module for 5.7.10-050710-generic
ERROR (dkms apport): kernel package nux-headers-5.7.10-050710-generic is not supported
Error! Bad return status for module build on kernel: 5li.7.10-050710-generic (x86_64)
Consult /var/lib/dkms/amdgpu/5.6.0.13-1089974/build/make.log for more information.
dpkg: error processing package amdgpu-dkms (--configure):
 installed amdgpu-dkms package post-installation script subprocess returned error exit status 10
Setting up python3-pil:amd64 (7.0.0-4ubuntu0.1) ...
dpkg: dependency problems prevent configuration of amdgpu:
 amdgpu depends on amdgpu-dkms (= 1:5.6.0.13-1089974); however:
  Package amdgpu-dkms is not configured yet.

dpkg: error processing package amdgpu (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-control-center-data (1:3.36.4-0ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Setting up libpulse-mainloop-glib0:amd64 (1:13.99.1-1ubuntu3.5) ...

---

### Post by backspin on 2020-07-25
Yup, that appears to be the issue... Installed kernel 5.6.0 and removed 5.7.10 and it installed just fine.

I was also able to install the amdgpu 20.20 without any errors as well.

---

### Post by Yellow Pasque on 2020-07-25
amdgpu 20.20 is probably not compatible with kernel 5.7
There's not much you can do about that except look for a patch.

---

### Post by GhX6GZMB on 2020-07-25
I'm a bit confused: the newest kernel I'm running is 5.4.0-42-generic on 20.04 LTS. Are you running development kernels?

---

