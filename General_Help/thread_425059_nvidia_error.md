---
title: "nvidia error"
date: 2007-04-27
forum: General Help
---

### Post by adza on 2007-04-27
hi, i was wondering if anyone has seen this before? When trying to launch diablo through wine, the following appears...

Error: API mismatch: the NVIDIA kernel module has the version 1.0-9755, but
this client has the version 1.0-9631.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
Error: API mismatch: the NVIDIA kernel module has the version 1.0-9755, but
this client has the version 1.0-9631.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy

now, i've tried installing the latest nvidia drivers, it won't let me proceed due to X server running.. how do i disable and get to command line? this would also help... arrrrhhh NVIDIA!!!


*********Fixed - NVIDIA latest drivers installed... found way of stopping x server... /etc/init.d/gdm stop (stops gnome desktop), then [ALT+F2] to log in to terminal... ran NVIDIA.run file from there... sweet! then /etc/init.d/gdm start to restart x server *************

---

### Post by Pox on 2007-04-27
For the future, instead of using the Nvidia .RUN files, it's easier through apt-get:

the packages nvidia-glx-new and linux-restricted-modules-2.6.20-15-386 should work perfectly.

---

### Post by adza on 2007-04-28
ummm... i have rebooted my machine this morning, to only what could be described as a critical level1 incident.. hehe... It seems the new NVIDIA driver installed yesterday (while working when restarted Xserver) has failed completely, Xserver is broken and i can't boot past the command prompt... My question is thus... how on earth do i remove a package installed as a .run (ie this proprietary driver).. I guess my only hope to fix this is to remove all traces of nvidia drivers from the system, the sudo apt-get install nvidia-glx-new again.. at least (while giving me a kernel error) these allowed the xserver to run... i'm typing this from windows as i speak, which is making me violently ill... could someone please help!!! 

p.s. any other suggestions on fixing the currently installed (but broken) NVIDIA driver would also be greatly appreciated... :confused:

---

### Post by Pox on 2007-04-28
OK, I'll run you through how I fixed this recently... my Nvidia driver broke during the feisty upgrade and I had to do a complete purge.

From a TTY terminal:

```

sh NVIDIA-Linux-x86-1.0-9XXX-pkg1.run --uninstall; #put the right number in there
sudo apt-get remove nvidia-glx-new nvidia-glx linux-restricted-modules-2.6.20-15-386;
mkdir ~/libGL_bu/; #directory to move old libGL to
sudo mv /usr/lib/libGL* ~/libGL_bu/;
sudo apt-get install nvidia-glx-new linux-restricted-modules-2.6.20-15-386;
sudo reboot;

```

That _should_ do it IIRC.

---

### Post by adza on 2007-04-28
Pox,

 Thanks!! this is exactly what i need to do... as for 'from a TTY term' heheh that won't be a problem, it's all i can get to!! haha ... will let you know :)

---

### Post by adza on 2007-04-28
aahhh... no good unfortunately... didn't fix the issue.. i've got two points that are killing me here..

 1) linux-restricted-modules-2.6.20-15-386 doesn't exist... (also i'm running AMD64, shouldn't i get a 64 bit version?)
2) GPU Kernel module version 1.0-7184 whereas X server module version 1.0-9755 (this was the error i was trying to fix yesterday..... )

?:confused: ?  any more tips?

---

### Post by adza on 2007-04-28
**bump** i'm going nuts here!! please help :) anyone!!

---

