---
title: "/usr/src/linux/include/linux/version.h missing in zen  kernel to build NVIDIA module"
date: 2008-07-04
forum: General Help
---

### Post by deepclutch on 2008-07-04
[FONT=Tahoma][SIZE=3]** Please help me resolve this problem: **
I have been trying to compile latest NVIDIA 177.13 module for my stock kernel 2.6.26-rc8-zen1-x0-core2-smp2 for Debian.the nvidia installer fails with below error for every work arounds [IMG]http://forums.gentoo.org/images/smiles/icon_sad.gif[/IMG] I have linux-header ,linux-source all installed for the current kernel version. 

```

ERROR: The kernel header file '/usr/src/linux/include/linux/version.h' does not exist.  The most likely reason for this is that the kernel source files  in '/usr/src/linux' have not been configured. 

ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at [www.nvidia.com]("http://www.nvidia.com/").

``` Please point to me ,which file needs to be symlinked for **version.h.  **

Thanks :D[/SIZE][/FONT]

---

### Post by deepclutch on 2008-07-04
thanks. 
 
well ,I am on Debian.It comes with a linux-image-2.6.26-rc8-zen1-x0-core2-smp2 .deb package and a linux-headers-2.6.26-rc8-zen1-x0-core2-smp2 .deb package both I have installed. 
 
Now ,mostly Nvidia should compile with both of this installed.but in this case ,the nvidia installer is complaining that version.h is missing :( . 
 
 :roll:

---

