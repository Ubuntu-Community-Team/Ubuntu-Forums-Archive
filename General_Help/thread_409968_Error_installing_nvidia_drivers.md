---
title: "Error installing nvidia drivers"
date: 2007-04-15
forum: General Help
---

### Post by GettinBetter on 2007-04-15
Hi all, I'm newbie on Ubuntu, and yesterday when I tried to install the nvidia drivers to my geforce 4 mx 440 following this tutorial: [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
but when I'm on step 7) of Method 2 the installer gives me an error and I can't install it

[HTML]nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Apr 15 11:06:00 2007

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
  kernel source path      : /usr/src/linux-headers-2.6.17-11-generic
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: Unable to find the development tool `cc` in your path; please make sure
       that you have the package 'gcc' installed.  If gcc is installed on your
       system, then please check that `cc` is in your PATH.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
[/HTML]

I don't know if this is important, but I'm trying install the 1.0-9631 driver on a geforce 4 mx 440

thanks for your help :)

---

### Post by Rospo Zoppo on 2007-04-15
I think you can use Envy [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by GettinBetter on 2007-04-15
it worked, thanks Rospo Zoppo ;)

---

### Post by Rospo Zoppo on 2007-04-15
Np :D

---

