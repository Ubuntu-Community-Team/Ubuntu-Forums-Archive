---
title: "apt install -f and dist-upgrade  tries to compile kernel headers/recompile failure"
date: 2024-10-25
forum: General Help
---

### Post by ubupro97 on 2024-10-25
[INDENT] 		Currently on Noble 24.04.1

 	Code:
 	[FONT=monospace][COLOR=#000000]uname -a
Linux pc.localdomain 6.8.0-35-generic #35-Ubuntu SMP PREEMPT_DYNAMIC Mon May 20 15:51:52 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux[/COLOR]
[/FONT] 
I haven't dist-upgrade and autoremoved old kernel packages for a  while, currently linux headers installed include one for 5.15 and:

 	Code:
 	 
linux-headers-6.8.0-35
linux-headers-6.8.0-44
linux-headers-6.8.0-45 (linux image is installed but not booted)
linux-headers-6.8.0-47 (linux image is installed but not booted) 
Kernel images -45 and -47 didn't boot last I checked, probably  related to the headers missing, or the headers won't compile on the  wrong kernel version.
I want to upgrade to 24.10; is it possible to test the Oracular kernel and install that before performing the upgrade?

Here's the compilation error:

[https://dpaste.com/HH258WRM4.txt](https://dpaste.com/HH258WRM4.txt)

Or in brief:

 	Code:
 	Setting up linux-headers-6.8.0-44-generic (6.8.0-44.44) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.8.0-44-generic
...
Running the pre_build script:
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables...
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether the compiler supports GNU C... yes
checking whether gcc accepts -g... yes
checking for gcc option to enable C11 features... none needed
checking how to run the C preprocessor... gcc -E
checking kernel source directory... /usr/src/linux-headers-6.8.0-44-generic
checking kernel build directory... /usr/src/linux-headers-6.8.0-44-generic
checking kernel source version... 6.8.0-44-generic
checking kernel file name for module symbols... Module.symvers
checking for linux/bits.h... yes
checking for linux/io-64-nonatomic-lo-hi.h... yes
checking for asm/set_memory.h... yes
checking for asm/fpu/api.h... yes
checking for linux/compiler_attributes.h... yes
checking for linux/fence-array.h... no
checking for linux/dma-resv.h... yes
checking for linux/mmap_lock.h... yes
checking for linux/pci-p2pdma.h... yes
checking for linux/dma-attrs.h... no
checking for linux/dma-buf-map.h... no
checking for linux/iosys-map.h... yes
checking for linux/stdarg.h... yes
checking for linux/dma-fence-chain.h... yes
checking for linux/xarray.h... yes
checking for linux/container_of.h... yes
checking for linux/cc_platform.h... yes
checking for linux/processor.h... yes
checking for linux/dma-map-ops.h... yes
checking for linux/apple-gmux.h... yes
checking for linux/device/class.h... yes
checking for linux/build_bug.h... yes
checking for linux/acpi_amd_wbrf.h... yes
checking for linux/units.h... yes
checking for drm/drm_backport.h... no
checking for drm/amdgpu_pciid.h... no
checking for drm/drm_probe_helper.h... yes
checking for drm/drmP.h... no
checking for drm/task_barrier.h... yes
checking for drm/drm_managed.h... yes
checking for drm/amd_asic_type.h... yes
checking for drm/drm_aperture.h... yes
checking for drm/dp/drm_dp_helper.h... no
checking for drm/dp/drm_dp_mst_helper.h... no
...
checking for nproc... (cached) yes    # [245 instances]
...
checking for module configuration... done
configure: creating ./config.status
config.status: creating config/config.h

Building module:
Cleaning build area...(bad exit status: 2)
. /tmp/amd.74HlkDs3/.env && make -j8 KERNELRELEASE=6.8.0-44-generic TTM_NAME=amdttm SCHED_NAME=amd-sched -C /lib/modules/6.8.0-44-generic/build M=/tmp/amd.74HlkDs3.......................................................(bad exit status: 2)
Error! Bad return status for module build on kernel: 6.8.0-44-generic (x86_64) 
 	[/INDENT]

---

### Post by ubupro97 on 2024-10-25
I'm having a battle with the editor and keep losing my posts, hence the formatting died.

---

### Post by ubupro97 on 2024-10-29
bump

---

### Post by ubupro97 on 2024-10-31
bump

---

### Post by ubupro97 on 2024-11-01
post closed, I'll make a new one

---

