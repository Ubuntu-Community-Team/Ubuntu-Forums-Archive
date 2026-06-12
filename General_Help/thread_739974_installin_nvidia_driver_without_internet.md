---
title: "installin nvidia driver without internet"
date: 2008-03-30
forum: General Help
---

### Post by jusbug on 2008-03-30
i'm very newbie to linux and ubuntu studio, i tried to install nvidia 169.12 but...
i looked everywhere and always poeple refer to envy utilities, but my probleme is i dont have internet connection.

here's the log file content:

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Mar 30 04:25:14 2008

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '5232'
   of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).

please guyz, what's this Xserver and how do you exit and install the driver.

please guyz, i realy need your expertise.

PS: i have 8600 GT, and no internet connection.

---

### Post by astoltz on 2008-03-30
In a nutshell, X is the program that handles the graphical interface.  To stop it, switch to a virtual console by pressing "ctrl-alt-F1".  Login with your user name and password and then run the command ```
sudo /etc/init.d/gdm stop
```You'll have to enter your password again.  After that, you can run the nvidia installer.  At the end, let the installer configure X to use the new driver.  If all goes well, the easiest thing to do is just re-boot.

---

