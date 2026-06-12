---
title: "Installing nVidia driver in Ubuntu Studio"
date: 2007-05-28
forum: General Help
---

### Post by Shardsofmetal on 2007-05-28
I'm trying to install the nVidia driver, and I'm now stuck. The installer wants to build the driver against the kernel I'm using. I'm using UbuntuStudio with the low-latency kernel. I have installed linux-source, but don't know if that's the package I need. Here is the content of my nvidia-installer.log file:
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue May 22 17:17:21 2007

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
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

If I have installed the correct package, where would the kernel source path be? If I haven't installed the correct package, what is the correct package? Thanks

---

### Post by energiya on 2007-05-28
Well, it asks for the kernel source. 

linux-source? Wasn't it kernel-source?

See first what kernel you are using with "uname -r" and install the exact kernel source. It should be located in /usr/src/linux-2.6.x.x. If you can find it there try making
```

sudo ln -s /usr/src/linux-2.6.x.x /usr/src/linux

```
Another thing to try would be to
```

sudo cp /boot/.config-2.6.x.x /usr/src/linux-2.6.x.x
cd /usr/src/linux-2.6.x.x
sudo make menuconfig

```
Nothing else I can think off.

If you are 100% sure you have the correct kernel source call the nVidia installer with
> 
--kernel-source-path=full_path_to_kernel

command line option.

---

### Post by kiwidoc66 on 2007-05-28
Not sure if this answers your question but when I upgraded from Feisty to Studio, the X server failed to start.  I eventually worked out that it was the nvidia drivers missing some dependencies.  By removing the nvidia drivers from feisty, then installing studio, then enabling the nvidia drivers, everything worked.  I think it's because of an additional package required by the studio low-latency kernel **linux-restricted-modules-2.6.20-15-lowlatency**

---

### Post by aldenhg on 2007-05-29
Have you tried just installing the vanilla nvidia-glx driver? I don't know what version Ubuntu Studio is based off of, but you could always try ```
sudo apt-get install nvidia-glx
or
sudo apt-get install nvidia-glx-new
or 
sudo apt-get install nvidia-glx-legacy
```
based on the age of your card.

---

### Post by bobp0303 on 2007-06-02
My studio installs and runs, but no video after the startup splash screen -- I was able to log in 'blind', but the screen remained completely blank. -- will try adding the nvidia drivers per the above post from the recovery boot option.

---

