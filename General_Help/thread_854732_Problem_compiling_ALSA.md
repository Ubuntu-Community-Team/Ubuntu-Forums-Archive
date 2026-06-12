---
title: "Problem compiling ALSA"
date: 2008-07-09
forum: General Help
---

### Post by Insomniac18 on 2008-07-09
My Ubuntu system has no sound. I looked up my soundcard, a SIGMATEL STAC 92XX C-Major HD Audio and found that many others can't get sound working either.


I decided to get ALSA to attempt to get it working. But I'm having problems compiling it.

I downloaded the tarball for version 1.0.16 and ran "./configure"
The output:
```
paras@Eugene:~/Desktop/alsa-driver-1.0.16$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/paras/Desktop/alsa-driver-1.0.16
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.24-19-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.24-19-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... no
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for CONFIG_EXPERIMENTAL... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... yes
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/latency.h... yes
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... yes
checking for kernel linux/seq_file.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.24-19-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i586
checking for i386 machine type... default
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... no
checking for video_get_drvdata... yes
checking for V4L1 layer... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver version... 1.0.16
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... yes
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... yes
checking for nested class_device... yes
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for PnP suspend/resume... yes
checking for new unlocked/compat_ioctl... yes
checking for x86-compatible PC... yes
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
checking for which soundcards to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged

```

Then I ran "make"
Output:
```
make dep
make[1]: Entering directory `/home/paras/Desktop/alsa-driver-1.0.16'
make[2]: Entering directory `/home/paras/Desktop/alsa-driver-1.0.16/acore'
copying file alsa-kernel/core/hwdep.c
/home/paras/Desktop/alsa-driver-1.0.16/utils/patch-alsa: 24: patch: not found
make[2]: *** [hwdep.c] Error 1
make[2]: Leaving directory `/home/paras/Desktop/alsa-driver-1.0.16/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/paras/Desktop/alsa-driver-1.0.16'
make: *** [include/sndversions.h] Error 2

```

There is an error there, and I have no idea how to get it working! Help is greatly appreciated.

---

### Post by ramjet_1953 on 2008-07-09
Apart from sorting out dependencies, have you installed the [COLOR="Blue"]build-essential package?[/COLOR]

This is required, if you want to compile.

[COLOR="Red"]sudo apt-get install build-essential[/COLOR]

Also I would install the [COLOR="Blue"]checkinstall[/COLOR] package

[COLOR="Red"]sudo apt-get install checkinstall[/COLOR]

Now all you need to do is to learn how to use these utilities.
I would suggest that you run through a few tutorials that can be googled for, [COLOR="#ff0000"]before[/COLOR] going any further.

When satisfying dependencies, remember that if a particular package is required, you will almist certainly need to also install the [COLOR="Blue"].dev[/COLOR] package associated with it also.

I can't help but think that at this early stage of your learning with 'NIX, you may have bitten-off a bit more than you can chew.

Also, the alsa packages are already availble in Synaptic.

Just go to S[COLOR="#0000ff"]ystem>Administaration[/COLOR] and when the window opens, click on the [COLOR="#0000ff"]search[/COLOR] button and enter alsa.

It will come back with the available alsa packages.

You probably only need install the [COLOR="#0000ff"]alsa-base[/COLOR] package.

Regards,
Roger :cool:

---

### Post by Insomniac18 on 2008-07-10
Thanks so much for the help, but unfortunately I still can't get this damn sound card working. I googled it, but I just couldn't understand the solutions. 

I also feel like an idiot for compiling this when it's available in the repo's -_-

Thanks again. I might just search a bit more for this sound card.

---

### Post by Insomniac18 on 2008-07-10
Thanks so much for the help, but unfortunately I still can't get this damn sound card working. I googled it, but I just couldn't understand the solutions. 

I also feel like an idiot for compiling this when it's available in the repo's -_-

Thanks again. I might just search a bit more for this sound card.

---

