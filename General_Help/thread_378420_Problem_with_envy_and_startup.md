---
title: "Problem with envy and startup"
date: 2007-03-07
forum: General Help
---

### Post by pentium on 2007-03-07
I recently had to reinstall ubuntu and that meant I lost the envy nvidia driver.
After the reinstall, I downloaded the latest debian packae and went envy -t with sudo.
I then downloaded the driver and right when it begins to build it complains about missing files and the install fails. Did I forget something?

Also, I use gkrellm to watch my system and before the reinstall I had it set to startup on login. Right now I have forgotteb what I did to make it autoload and making it run as a startup sesson still resfuses to make it run.
Any help here too?

---

### Post by taurus on 2007-03-07
Do you remember what files are missing when you try to install a driver for your graphic card?

To start a program when you log in, add it to System -> Preferences -> Sessions -> Startup Programs.

---

### Post by pentium on 2007-03-07
Here's the readout (or at least part of it)
```
install: cannot stat `NVIDIA-Linux-x86-1.0-7184-pkg0/usr/include/GL/glxext.h': No such file or directory
make: *** [install] Error 1
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
rm: cannot remove `/usr/src/nvidia-kernel*.deb': No such file or directory
Getting source for kernel version: 2.6.15-28-386
Kernel headers available in /usr/src/linux

Done!

Updated infos about 69 packages
The source tarball could not be found!
Package nvidia-kernel-source not installed?
Running "m-a -f get nvidia-kernel-source" may help.
find: /usr/src/modules: No such file or directory
rm: cannot remove `*.deb': No such file or directory
rm: cannot remove `*.changes': No such file or directory
rm: cannot remove `*.asc': No such file or directory
rm: cannot remove `/usr/share/envy/*.deb': No such file or directory
rm: cannot remove `/usr/share/envy/*.asc': No such file or directory
rm: cannot remove `/usr/share/envy/*.changes': No such file or directory
rm: cannot remove `/usr/share/envy/nvidia-graphics-drivers/debian/files': No such file or directory
rm: cannot remove `/usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx.postinst.debhelper': No such file or directory
rm: cannot remove `/usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx.postrm.debhelper': No such file or directory
rm: cannot remove `/usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx.prerm.debhelper': No such file or directory
rm: cannot remove `/usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx.substvars': No such file or directory
rm: cannot remove `/usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx.substvars.bak': No such file or directory

```

> To start a program when you log in, add it to System -> Preferences -> Sessions -> Startup Programs.
I did do that and it still won't start at login.

---

### Post by pentium on 2007-03-08
Anyone?
My system is useless without the proper driver.

---

### Post by tseliot on 2007-03-10
Try the latest release of Envy (envy_0.9.1-0ubuntu2):
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by pentium on 2007-03-10
I tried bot the latest and the lod one and both failed to work.
I think I sent you an email with more detail.

---

### Post by tseliot on 2007-03-11
There's no need to reinstall Ubuntu every time the Xserver crashes.

Boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "nv" driver. Press ENTER whenever you don't know the answer to a question.

Then save the Xserver log somewhere:
type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Then reboot:
```
reboot
```

On next reboot the Xserver should work fine

Then I would like you to post 
a) Envy's log:
```
/var/log/envy-installer.log
```

b) the Xorg.0.log which you will find in your home folder

---

### Post by pentium on 2007-03-12
> a) Envy's log:
Does not exist!
However, there is Nvidia-installer.log:
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Mar  9 18:05:19 2007

option status:
  license pre-accepted    : true
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : false
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : true
  silent                  : true
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
  X install prefix        : /usr/lib/xorg/modules
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : /usr/src/linux-headers-2.6.15-28-386
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : none
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using built-in stream user interface
-> License accepted by command line option.
-> Not probing for precompiled kernel interfaces.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Using the kernel source path '/usr/src/linux-headers-2.6.15-28-386' as
   specified by the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/linux-headers-2.6.15-28-386'
-> Kernel output path: '/usr/src/linux-headers-2.6.15-28-386'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv.o nv-vm.o os-
   agp.o os-interface.o os-registry.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -rf .tmp_versions
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/usr/src/linux-headers-2.6.1
   5-28-386 SYSOUT=/usr/src/linux-headers-2.6.15-28-386'...
   
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /usr/src/linux-headers-2.6.15-28-386 SUBDIRS
   =/tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv modules
   mkdir -p /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.tmp_ver
   sions
   make -f scripts/Makefile.build obj=/tmp/selfgz13197/NVIDIA-Linux-x86-1.0-718
   4-pkg1/usr/src/nv
   echo \#define NV_COMPILER \"`cc -v 2>&1 | tail -n 1`\" > /tmp/selfgz13197/NV
   IDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/nv_compiler.h
     cc -Wp,-MD,/tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.3/include -D__KERNEL
   __ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-proto
   types -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -O2    
   -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-un
   it-at-a-time -march=i486 -Iinclude/asm-i386/mach-default -Wdeclaration-after
   -statement -Wno-pointer-sign -I/tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pk
   g1/usr/src/nv
    -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparent
   heses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common -MD   -Wsign-c
   ompare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE
    -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV_MAJO
   R_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7184  -DNV_UNIX   -DNV_LINU
   X   -DNV_INT64_OK   -DNVCPU_X86      -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_S
   TRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -
   DNV_PM_MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_P
   RESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_
   4_PRESENT  -DMODULE -DKBUILD_BASENAME=nv -DKBUILD_MODNAME=nvidia -c -o /tmp/
   selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz1
   3197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:77,
                    from include/linux/kernel.h:15,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv-linux.h:46,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv.c:14:
   include/asm/bitops.h: In function ‘find_first_bit’:
   include/asm/bitops.h:326: warning: comparison between signed and unsigned
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv-linux.h:47,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:485,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv-linux.h:71,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv.c:14:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:253: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.nv-
   vm.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.3/include -D__KER
   NEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pr
   ototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -O2 
      -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno
   -unit-at-a-time -march=i486 -Iinclude/asm-i386/mach-default -Wdeclaration-af
   ter-statement -Wno-pointer-sign -I/tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184
   -pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-sub
   scripts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-commo
   n -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__K
   ERNEL__ -DMODULE  -DNTRM -D_GNU_SOUR
   CE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV_MAJOR_VERSION=1 -DNV_MI
   NOR_VERSION=0 -DNV_PATCHLEVEL=7184  -DNV_UNIX   -DNV_LINUX   -DNV_INT64_OK  
   -DNVCPU_X86      -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULT
   IPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_PM_MESSAGE_T_PRE
   SENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_REMAP_PF
   N_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE 
   -DKBUILD_BASENAME=nv_vm -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz13197/NVIDI
   A-Linux-x86-1.0-7184-pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz13197/NVIDIA-Li
   nux-x86-1.0-7184-pkg1/usr/src/nv/nv-vm.c
   In file included from include/linux/bitops.h:77,
                    from include/linux/kernel.h:15,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv-linux.h:46,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/asm/bitops.h: In function ‘find_first_bit’:
   include/asm/bitops.h:326: warning: comparison between signed and unsigned
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv-linux.h:47,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:485,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv-linux.h:71,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:253: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.os-
   agp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.3/include -D__KE
   RNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-p
   rototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -O2
       -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fn
   o-unit-at-a-time -march=i486 -Iinclude/asm-i386/mach-default -Wdeclaration-a
   fter-statement -Wno-pointer-sign -I/tmp/selfgz13197/NVIDIA-Linux-x86-1.0-718
   4-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-su
   bscripts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-comm
   on -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__
   KERNEL__ -DMODULE  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -
   DMODULE  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7184  -DN
   V_UNIX   -DNV_LINUX   -DNV_INT64_OK   -DNVCPU_X86      -UDEBUG -U_DEBUG -DND
   EBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULT
   IPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_PM_MESSAGE_T_PRE
   SENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_REMAP_PF
   N_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE 
   -DKBUILD_BASENAME=os_agp -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz13197/NVID
   IA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.tmp_os-agp.o /tmp/selfgz13197/NVIDIA-
   Linux-x86-1.0-7184-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/bitops.h:77,
                    from include/linux/kernel.h:15,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv-linux.h:46,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/asm/bitops.h: In function ‘find_first_bit’:
   include/asm/bitops.h:326: warning: comparison between signed and unsigned
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv-linux.h:47,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:485,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv-linux.h:71,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:253: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.os-
   interface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.3/include 
   -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wst
   rict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestandi
   ng -O2     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundar
   y=2 -fno-unit-at-a-time -march=i486 -Iinclude/asm-i386/mach-default -Wdeclar
   ation-after-statement -Wno-pointer-sign -I/tmp/selfgz13197/NVIDIA-Linux-x86-
   1.0-7184-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -W
   char-subscripts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -O -f
   no-common -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAM
   ES -D__KERNEL__ -DMODULE  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KER
   NEL__ -DMODULE  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=71
   84  -DNV_UNIX   -DNV_LINUX   -DNV_INT64_OK   -DNVCPU_X86      -UDEBUG -U_DEB
   UG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DN
   V_PCI_GET_CLASS_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRES
   ENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAG
   E_ATTR_PRESENT -DNV_VMAP_4_PRESENT
     -DMODULE -DKBUILD_BASENAME=os_interface -DKBUILD_MODNAME=nvidia -c -o /tmp
   /selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.tmp_os-interface.o /
   tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/bitops.h:77,
                    from include/linux/kernel.h:15,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv-linux.h:46,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/asm/bitops.h: In function ‘find_first_bit’:
   include/asm/bitops.h:326: warning: comparison between signed and unsigned
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv-linux.h:47,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:485,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv-linux.h:71,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:253: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.os-
   registry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.3/include -
   D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstr
   ict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestandin
   g -O2     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary
   =2 -fno-unit-at-a-time -mar
   ch=i486 -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-p
   ointer-sign -I/tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv -Wa
   ll -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparenthese
   s -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common -MD   -Wsign-compa
   re -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -D
   NTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV_MAJOR_V
   ERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7184  -DNV_UNIX   -DNV_LINUX  
   -DNV_INT64_OK   -DNVCPU_X86      -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUC
   T_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_
   PM_MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESE
   NT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PR
   ESENT  -DMODULE -DKBUILD_BASENAME=os_registry -DKBUILD_MODNAME=nvidia -c -o 
   /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.tmp_os-registry.
   o /tmp/selfgz13197/NVIDIA-Linux-x86
   -1.0-7184-pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/bitops.h:77,
                    from include/linux/kernel.h:15,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv-linux.h:46,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/os-registry.c:14:
   include/asm/bitops.h: In function ‘find_first_bit’:
   include/asm/bitops.h:326: warning: comparison between signed and unsigned
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv-linux.h:47,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/os-registry.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:485,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/nv-linux.h:71,
                    from /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
   c/nv/os-registry.c:14:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:253: warning: wrong type argument to increment
     ld -m elf_i386 -m elf_i386  -r -o /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-71
   84-pkg1/usr/src/nv/nvidia.o /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/
   usr/src/nv/nv-kernel.o /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/s
   rc/nv/nv.o /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/nv-vm.
   o /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/os-agp.o /tmp/s
   elfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/os-interface.o /tmp/sel
   fgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/os-registry.o
     Building modules, stage 2.
   make -rR -f /usr/src/linux-headers-2.6.15-28-386/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.15-28-386/Module.s
   ymvers /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/nvidia.o
   Warning: could not find /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/
   src/nv/.nv-kernel.o.cmd for /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/
   usr/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.nvi
   dia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.3/include -D
   __KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding
   -O2     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2
   -fno-unit-at-a-time -march=i486 -Iinclude/asm-i386/mach-default -Wdeclaratio
   n-after-statement -Wno-pointer-sign    -DKBUILD_BASENAME=nvidia -DKBUILD_MOD
   NAME=nvidia -DMODULE -c -o /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/u
   sr/src/nv/nvidia.mod.o /tmp/selfgz13197/NVIDIA-Linux-x86-1.
   0-7184-pkg1/usr/src/nv/nvidia.mod.c
     ld -m elf_i386 -m elf_i386 -r -o /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-718
   4-pkg1/usr/src/nv/nvidia.ko /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/
   usr/src/nv/nvidia.o /tmp/selfgz13197/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/
   nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
-> Kernel messages:
   [17179602.492000] lo: Disabled Privacy Extensions
   [17179602.492000] IPv6 over IPv4 tunneling driver
   [17179609.792000] ACPI: Power Button (FF) [PWRF]
   [17179609.792000] ACPI: Sleep Button (CM) [SBTN]
   [17179609.992000] ibm_acpi: ec object not found
   [17179610.044000] pcc_acpi: loading...
   [17179612.560000] eth0: no IPv6 routers present
   [17179621.132000] ppdev: user-space parallel port driver
   [17179621.748000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
   [17179621.748000] apm: overridden by ACPI.
   [17179622.508000] NET: Registered protocol family 5
   [17179667.308000] Bluetooth: Core ver 2.8
   [17179667.308000] NET: Registered protocol family 31
   [17179667.308000] Bluetooth: HCI device and connection manager initialized
   [17179667.308000] Bluetooth: HCI socket layer initialized
   [17179667.364000] Bluetooth: L2CAP ver 2.8
   [17179667.364000] Bluetooth: L2CAP socket layer initialized
   [17179667.368000] Bluetooth: RFCOMM socket layer initialized
   [17179667.368000] Bluetooth: RFCOMM TTY layer initialized
   [17179667.368000] Bluetooth: RFCOMM ver 1.7
   [17261858.076000] nvidia: module license 'NVIDIA' taints kernel.
   [17261858.092000] **** SET: Misaligned resource pointer: d6e919a2 Type 07
   Len 0
   [17261858.092000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
   [17261858.092000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI
   11 (level, low) -> IRQ 11
   [17261858.092000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-7184 
   Tue Aug  1 18:38:58 PDT 2006
-> Installing both new and classic TLS OpenGL libraries.
-> Searching for conflicting X files:
-> done.
-> Searching for conflicting OpenGL files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86' (1.0-7184):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
-> done.
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
-> done.
-> Runtime sanity check passed.
-> Installation of the NVIDIA Accelerated Graphics Driver for Linux-x86
   (version: 1.0-7184) is now complete.  Please update your XF86Config or
   xorg.conf file as appropriate; see the file
   /usr/share/doc/NVIDIA_GLX-1.0/README for details.

```

---

### Post by pentium on 2007-03-12
> the Xorg.0.log which you will find in your home folder
```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux Ubuntu 2.6.15-28-386 #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar  9 22:39:06 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,1130 card 0000,0000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1131 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 8086,4541 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 8086,4541 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2443 card 8086,4541 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2445 card 8086,4541 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0150 card 107d,2842 rev a4 class 03,00,00 hdr 00
(II) PCI: 02:08:0: chip 8086,2449 card 8086,3013 rev 01 class 02,00,00 hdr 00
(II) PCI: 02:0a:0: chip 109e,036e card 0070,13eb rev 11 class 04,00,00 hdr 80
(II) PCI: 02:0a:1: chip 109e,0878 card 0070,13eb rev 11 class 04,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfc900000 - 0xfe9fffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe4600000 - 0xf46fffff (0x10100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xf4700000 - 0xf47fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV15 [GeForce2 GTS/Pro] rev 164, Mem @ 0xfd000000/24, 0xe8000000/27, BIOS @ 0xfe9f0000/16
(--) PCI: (2:10:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xf47fe000/12
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[1] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[2] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[3] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[4] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[5] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[6] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[8] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[9] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[10] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[11] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[12] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[1] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[2] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[3] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[4] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[5] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[6] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[8] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[9] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[10] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[11] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[12] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[5] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[8] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[9] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[10] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[14] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[16] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[17] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[18] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7184
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 GT, GeForce 6800 GT,
	GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000, GeForce 6800 GS,
	GeForce 6800, GeForce 6800 LE, GeForce 6800 XT, GeForce Go 6800,
	GeForce Go 6800 Ultra, Quadro FX Go1400, Quadro FX 3450/4000 SDI,
	Quadro FX 1400, GeForce 6600 GT, GeForce 6600, GeForce 6600 LE,
	GeForce 6600 VE, GeForce Go 6600, GeForce 6610 XL,
	GeForce Go 6600 TE/6200 TE, GeForce 6700 XL, GeForce Go 6600,
	GeForce Go 6600 GT, Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 7800 GTX, GeForce 7800 GTX, GeForce 7800 GT, GeForce 7800 GS,
	GeForce 7800 SLI, GeForce Go 7800, GeForce Go 7800 GTX,
	Quadro FX 4500, GeForce 7300 LE, GeForce Go 7200, GeForce Go 7300,
	GeForce Go 7400, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	Quadro FX 350, GeForce 7300 GS, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, Quadro FX 550M, GeForce Go 7900 GS,
	GeForce Go 7900 GTX, Quadro FX 2500M, Quadro FX 1500M, GeForce 6150,
	GeForce 6150 LE, GeForce 6100, GeForce Go 6150, GeForce Go 6100
(II) Primary Device is: PCI 01:00:0
(--) Chipset GeForce2 GTS found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[5] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[8] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[9] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[10] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[14] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[16] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[17] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[18] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[5] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[8] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[9] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[10] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[17] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[19] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[20] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce2 GTS"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xE8000000
(--) NV(0): MMIO registers at 0xFD000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules/libi2c.so
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): HW is currently programmed for CRT
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 32768 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Generic Monitor: Using hsync range of 28.00-51.00 kHz
(II) NV(0): Generic Monitor: Using vrefresh range of 43.00-60.00 Hz
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (vrefresh out of range)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (vrefresh out of range)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (vrefresh out of range)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (vrefresh out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (vrefresh out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "832x624" (vrefresh out of range)
(II) NV(0): Not using default mode "416x312" (vrefresh out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (hsync out of range)
(II) NV(0): Not using default mode "720x450" (hsync out of range)
(II) NV(0): Not using default mode "1600x1024" (hsync out of range)
(II) NV(0): Not using default mode "800x512" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NV(0): Not using default mode "1152x768" (width too large for virtual size)
(--) NV(0): Virtual size is 1024x768 (pitch 1024)
(**) NV(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) NV(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) NV(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) NV(0):  Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) NV(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"   12.60  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(==) NV(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[7] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[8] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[9] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[10] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[19] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[21] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[22] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[25] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled

```

---

### Post by pentium on 2007-03-24
You know I still have not gotten the driver installed properly.
Has anyone figured the problem out yet?

---

### Post by pentium on 2007-03-30
I'm still without the proper and blender will not run without it.
Your latest version won't even allow me to install the driver and gives me an error box with no information.

EDIT: Oh I see why. You have dropped support for dapper temporarly.

---

### Post by tseliot on 2007-04-13
Can you attach the complete /var/log/envy-installer.log ?

---

### Post by pentium on 2007-04-13
> Can you attach the complete /var/log/envy-installer.log ?
I tried to do that before but envy's log was not created for some twisted reason,
I tried the instructions again to get the log but it still didn't appear.

---

