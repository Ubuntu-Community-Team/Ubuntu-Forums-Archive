---
title: "Getting System Errors"
date: 2015-02-01
forum: General Help
---

### Post by nainsurvolte on 2015-02-01
I am getting system errors at boot up, not alwasy but often. Checking in the logs, it seem to come from my Graphic card. It is an Asus 8400GS. Not that it causes any issue, but I would like to solve it and make sure it does not become an issue at one point in time.

From the /var/crash I have this file: nvidia-331.0.crash

```
ProblemType: PackageDKMSBuildLog:
 DKMS make.log for nvidia-331-331.113 for kernel 3.13.0-45-generic (x86_64)
 Sun Feb  1 12:48:02 EST 2015
 NVIDIA: calling KBUILD...
 make[1]: Entering directory `/usr/src/linux-headers-3.13.0-45-generic'
 test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
     echo >&2;                            \
     echo >&2 "  ERROR: Kernel configuration is invalid.";        \
     echo >&2 "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
     echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
     echo >&2 ;                            \
     /bin/false)
 mkdir -p /var/lib/dkms/nvidia-331/331.113/build/.tmp_versions ; rm -f /var/lib/dkms/nvidia-331/331.113/build/.tmp_versions/*
 make -f scripts/Makefile.build obj=/var/lib/dkms/nvidia-331/331.113/build
   cc -Wp,-MD,/var/lib/dkms/nvidia-331/331.113/build/.nv.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.13.0-45-generic/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.13.0-45-generic/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.13.0-45-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-mmx -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -fno-var-tracking-assignments -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -Werror=implicit-int -Werror=strict-prototypes -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/var/lib/dkms/nvidia-331/331.113/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.113\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia-331/331.113/build/.tmp_nv.o /var/lib/dkms/nvidia-331/331.113/build/nv.c
 In file included from include/uapi/linux/stddef.h:1:0,
                  from include/linux/stddef.h:4,
                  from /usr/src/linux-headers-3.13.0-45-generic/include/uapi/linux/posix_types.h:4,
                  from include/uapi/linux/types.h:13,
                  from include/linux/types.h:5,
                  from include/uapi/linux/capability.h:16,
                  from include/linux/capability.h:15,
                  from include/linux/sched.h:13,
                  from include/linux/utsname.h:5,
                  from /var/lib/dkms/nvidia-331/331.113/build/nv-linux.h:44,
                  from /var/lib/dkms/nvidia-331/331.113/build/nv.c:13:
 /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/uaccess.h: In function \u2018copy_from_user\u2019:
 /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/uaccess.h:612:26: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (likely(sz < 0 || sz >= n))
                           ^
 include/linux/compiler.h:152:40: note: in definition of macro \u2018likely\u2019
  # define likely(x) __builtin_expect(!!(x), 1)
                                         ^
 /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/uaccess.h: In function \u2018copy_to_user\u2019:
 /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/uaccess.h:630:26: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (likely(sz < 0 || sz >= n))
                           ^
 include/linux/compiler.h:152:40: note: in definition of macro \u2018likely\u2019
  # define likely(x) __builtin_expect(!!(x), 1)
                                         ^
 mv: cannot stat \u2018/var/lib/dkms/nvidia-331/331.113/build/.tmp_nv.o\u2019: No such file or directory
 make[2]: *** [/var/lib/dkms/nvidia-331/331.113/build/nv.o] Error 1
 make[1]: *** [_module_/var/lib/dkms/nvidia-331/331.113/build] Error 2
 make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-45-generic'
 NVIDIA: left KBUILD.
 nvidia.ko failed to build!
 make: *** [nvidia.ko] Error 1
DKMSKernelVersion: 3.13.0-45-generic
Date: Sun Feb  1 12:49:07 2015
Package: nvidia-331
PackageVersion: 331.113-0ubuntu0.0.4
SourcePackage: nvidia-graphics-drivers-331
Title: nvidia-331 331.113-0ubuntu0.0.4: nvidia-331 kernel module failed to build 
```

and from the apport.log

```

ERROR: apport (pid 2827) Sun Feb  1 14:34:33 2015: called for pid 2822, signal 11, core limit 0
ERROR: apport (pid 2827) Sun Feb  1 14:34:33 2015: executable: /usr/bin/xfsettingsd (command line "xfsettingsd")
ERROR: apport (pid 2827) Sun Feb  1 14:34:33 2015: executable version is blacklisted, ignoring

```

Thanks

---

### Post by java_java_and_more_java on 2015-02-02
Exactly same problem with 14.04 when updating

**$ lspci | grep VGA**
01:00.0 VGA compatible controller: NVIDIA Corporation GK208 [GeForce GT 640 Rev. 2] (rev a1)

---

### Post by ibjsb4 on 2015-02-02
Do you have 'dkms' installed?

---

### Post by nainsurvolte on 2015-02-02
Yes, it was installed and at the last version.

It did show me that I had package to remove, and in the terminal window, some log information did contain nvidia-331...

```

depmod....


DKMS: uninstall completed.
dkms: removing: nvidia-331 331.113 (3.13.0-32-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  nvidia-331
Version: 331.113
Kernel:  3.13.0-32-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


nvidia_331.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-32-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

```

I`ll reboot when I can and see if this helped...

---

### Post by ibjsb4 on 2015-02-02
I'm having trouble understanding whats going on.

Did you remove the 331 driver?  How?

Please post
```
lspci  -mm | grep VGA && dpkg -l | grep nvidia
```

---

### Post by nainsurvolte on 2015-02-03
Sorry for the confusion... While checking if dkms was installed, it was mentioned that some packages were not needed anymore. So I simply did a "*apt-get autoremove*" and the text in my previous post was one of those packages. Since it had the mention nvidia-331, I was hoping it was the culprit.

I rebooted this morning and I am not getting the system error (which does not mean it is fixed), but the trace in the kern.log is still there (ref first post).

Here is what I get with your command line

```

02:00.0 "VGA compatible controller" "NVIDIA Corporation" "G98 [GeForce 8400 GS Rev. 2]" -ra1 "ASUSTeK Computer Inc." "Device 8266"
ii  nvidia-331                                                  331.113-0ubuntu0.0.4                     amd64        NVIDIA binary driver - version 331.113
ii  nvidia-331-uvm                                              331.113-0ubuntu0.0.4                     amd64        NVIDIA Unified Memory kernel module
ii  nvidia-libopencl1-331                                       331.113-0ubuntu0.0.4                     amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                       331.113-0ubuntu0.0.4                     amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                                0.6.2                                    amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             331.20-0ubuntu8                          amd64        Tool for configuring the NVIDIA graphics driver

```

---

### Post by ibjsb4 on 2015-02-03
Ok, see what happens.

Apport will at times hang on an old crash.  Its a good idea to reset it.  Remove the /var/crash/ file(s) to reset.

---

### Post by nainsurvolte on 2015-02-10
Ok, I deleted the crash file a while ago but only did a reboot this morning.

I don`t get a crash file anymore but still get this entry in the *kern.log* file.

```
Feb 10 07:08:10 TV-server kernel: [  102.071747] ------------[ cut here ]------------
Feb 10 07:08:10 TV-server kernel: [  102.071756] WARNING: CPU: 0 PID: 1568 at /build/buildd/linux-3.13.0/arch/x86/mm/ioremap.c:102 __ioremap_caller+0x374/0x380()
Feb 10 07:08:10 TV-server kernel: [  102.071773] Modules linked in: binfmt_misc nvidia(POX) serio_raw edac_core edac_mce_amd i2c_viapro k8temp btrfs drm shpchp raid6_pq asus_atk0110 libcrc32c xor mac_hid lp parport pata_acpi hid_generic usbhid hid psmouse via_rhine pata_via sata_via sata_sil sata_sil24 r8169 mii
Feb 10 07:08:10 TV-server kernel: [  102.071776] CPU: 0 PID: 1568 Comm: Xorg Tainted: P           OX 3.13.0-45-generic #74-Ubuntu
Feb 10 07:08:10 TV-server kernel: [  102.071777] Hardware name: System manufacturer System Product Name/A8V-VM SE, BIOS 0702    05/21/2007
Feb 10 07:08:10 TV-server kernel: [  102.071780]  0000000000000009 ffff8800685937d0 ffffffff81720eb6 0000000000000000
Feb 10 07:08:10 TV-server kernel: [  102.071782]  ffff880068593808 ffffffff810677cd ffffea0000002740 000000000000009d
Feb 10 07:08:10 TV-server kernel: [  102.071784]  000000000009d000 000000000000009d 0000000000001000 ffff880068593818
Feb 10 07:08:10 TV-server kernel: [  102.071785] Call Trace:
Feb 10 07:08:10 TV-server kernel: [  102.071790]  [<ffffffff81720eb6>] dump_stack+0x45/0x56
Feb 10 07:08:10 TV-server kernel: [  102.071793]  [<ffffffff810677cd>] warn_slowpath_common+0x7d/0xa0
Feb 10 07:08:10 TV-server kernel: [  102.071795]  [<ffffffff810678aa>] warn_slowpath_null+0x1a/0x20
Feb 10 07:08:10 TV-server kernel: [  102.071798]  [<ffffffff81056ba4>] __ioremap_caller+0x374/0x380
Feb 10 07:08:10 TV-server kernel: [  102.071994]  [<ffffffffa07b7f2d>] ? os_map_kernel_space+0xad/0xe0 [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.071996]  [<ffffffff81056be4>] ioremap_cache+0x14/0x20
Feb 10 07:08:10 TV-server kernel: [  102.072000]  [<ffffffffa07b7f2d>] os_map_kernel_space+0xad/0xe0 [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.072190]  [<ffffffffa0786050>] _nv013372rm+0x76/0x92 [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.072371]  [<ffffffffa02851b6>] ? _nv008801rm+0x9e/0x149 [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.072455]  [<ffffffffa0285344>] ? _nv013023rm+0xe3/0x123 [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.072540]  [<ffffffffa0285980>] ? _nv013054rm+0xc3/0x121 [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.072627]  [<ffffffffa02810b5>] ? _nv013033rm+0xac/0x3c2 [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.072710]  [<ffffffffa0281472>] ? _nv013056rm+0xa7/0x17e [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.072794]  [<ffffffffa0281599>] ? _nv013032rm+0x50/0x5d [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.072880]  [<ffffffffa0286dfe>] ? _nv013012rm+0x792/0x9d4 [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.072976]  [<ffffffffa07942b5>] ? _nv011353rm+0x10a/0x404 [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.073069]  [<ffffffffa0794255>] ? _nv011353rm+0xaa/0x404 [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.073167]  [<ffffffffa02cb352>] ? _nv000976rm+0xf0/0x134d [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.073265]  [<ffffffffa02caf1c>] ? _nv001657rm+0x1e6/0x3a7 [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.073426]  [<ffffffffa05933d0>] ? _nv008722rm+0x437d/0x6431 [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.073510]  [<ffffffffa0260384>] ? _nv009097rm+0x25/0x4f [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.073602]  [<ffffffffa0794028>] ? _nv013443rm+0xa80/0xc03 [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.073696]  [<ffffffffa0794eca>] ? _nv000813rm+0x3f1/0x631 [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.073790]  [<ffffffffa078d7a2>] ? rm_init_adapter+0x73/0xf6 [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.073883]  [<ffffffffa07ae98a>] ? nvidia_open+0x1fa/0x930 [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.073974]  [<ffffffffa07b9e79>] ? nvidia_frontend_open+0x49/0xa0 [nvidia]
Feb 10 07:08:10 TV-server kernel: [  102.073978]  [<ffffffff811c257f>] ? chrdev_open+0x9f/0x1d0
Feb 10 07:08:10 TV-server kernel: [  102.073980]  [<ffffffff811bb0b3>] ? do_dentry_open+0x233/0x2e0
Feb 10 07:08:10 TV-server kernel: [  102.073982]  [<ffffffff811c24e0>] ? cdev_put+0x30/0x30
Feb 10 07:08:10 TV-server kernel: [  102.073984]  [<ffffffff811bb3e9>] ? vfs_open+0x49/0x50
Feb 10 07:08:10 TV-server kernel: [  102.073987]  [<ffffffff811cc704>] ? do_last+0x564/0x1230
Feb 10 07:08:10 TV-server kernel: [  102.073990]  [<ffffffff811ca7a1>] ? link_path_walk+0x71/0x870
Feb 10 07:08:10 TV-server kernel: [  102.073992]  [<ffffffff81314d2b>] ? apparmor_file_alloc_security+0x5b/0x180
Feb 10 07:08:10 TV-server kernel: [  102.073996]  [<ffffffff811cd48b>] ? path_openat+0xbb/0x650
Feb 10 07:08:10 TV-server kernel: [  102.073999]  [<ffffffff812d6f2e>] ? security_inode_alloc+0x1e/0x20
Feb 10 07:08:10 TV-server kernel: [  102.074002]  [<ffffffff811e3c88>] ? simple_xattr_get+0x68/0xb0
Feb 10 07:08:10 TV-server kernel: [  102.074005]  [<ffffffff811ce88a>] ? do_filp_open+0x3a/0x90
Feb 10 07:08:10 TV-server kernel: [  102.074009]  [<ffffffff811db717>] ? __alloc_fd+0xa7/0x130
Feb 10 07:08:10 TV-server kernel: [  102.074012]  [<ffffffff811bcf09>] ? do_sys_open+0x129/0x280
Feb 10 07:08:10 TV-server kernel: [  102.074014]  [<ffffffff811dd8c4>] ? mntput+0x24/0x40
Feb 10 07:08:10 TV-server kernel: [  102.074016]  [<ffffffff811c786e>] ? path_put+0x1e/0x30
Feb 10 07:08:10 TV-server kernel: [  102.074019]  [<ffffffff811bd07e>] ? SyS_open+0x1e/0x20
Feb 10 07:08:10 TV-server kernel: [  102.074021]  [<ffffffff8173196d>] ? system_call_fastpath+0x1a/0x1f
Feb 10 07:08:10 TV-server kernel: [  102.074024] ---[ end trace 1fdbeac7a525cb26 ]---
```

Should I care about that, or should I consider the problem solved. Seems to still refer to nvidia stuff.

---

