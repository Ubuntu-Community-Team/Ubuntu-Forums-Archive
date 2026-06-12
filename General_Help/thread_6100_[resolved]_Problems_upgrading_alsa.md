---
title: "[resolved] Problems upgrading alsa"
date: 2004-11-24
forum: General Help
---

### Post by sebast on 2004-11-24
Hi,

Sorry for the (resolved) and (not resolved), I clicked on the wrong button, sorry for posting in to places (general and installation), I didn't saw the installation forum at first. Lots of mistakes for just one post, lol

I just installed Ubuntu 4.10.

My sound card as a Audigy Ls so it doesn't work with the version of alsa installed in Ubuntu. So, I decided to install alsa 1.0.7.

I installed GCC 3.3.4 and the linux kernel 2.6.8 sources with synaptic because I tought it would be usefull. I just installed them doing nothing else with them.

On the alsa web site, I downloaded the driver version 1.0.7. I ran into a couple of problems trying to install it. This is the copy of the text of my terminal when I tried to install it:

[INDENT]sebb@ubuntu:~ $ cd /usr/src
sebb@ubuntu:/usr/src $ sudo mkdir alsa
Password:
sebb@ubuntu:/usr/src $ cd alsa
sebb@ubuntu:/usr/src/alsa $ sudo cp /home/sebb/alsa-driver-1.0.7.tar.bz2 /usr/src/alsa
sebb@ubuntu:/usr/src/alsa $ sudo bunzip2 alsa-driver-1.0.7.tar.bz2
sebb@ubuntu:/usr/src/alsa $ sudo tar -xf alsa-driver-1.0.7.tar
sebb@ubuntu:/usr/src/alsa $ cd alsa-driver-1.0.7
sebb@ubuntu:/usr/src/alsa/alsa-driver-1.0.7 $ ls
acinclude.m4  cvscompile  isa               README         test
aclocal.m4    doc         kbuild            Rules.make     TODO
acore         drivers     Makefile          scripts        toplevel.config
alsa-kernel   FAQ         Makefile.conf.in  snddevices     toplevel.config.in
arm           hal2        modules           snddevices.in  usb
CARDS-STATUS  i2c         parisc            sound          utils
configure     include     pci               sparc          version
configure.in  INSTALL     pcmcia            support        version.in
COPYING       install-sh  ppc               synth          WARNING
sebb@ubuntu:/usr/src/alsa/alsa-driver-1.0.7 $ ./configure --help
./configure: line 88: conf13330.sh: Permission denied
./configure: line 89: conf13330.sh: Permission denied
chmod: failed to get attributes of `conf13330.sh': No such file or directory
./configure: line 201: conf13330.file: Permission denied
`configure' configures this package to adapt to many kinds of systems.

Usage: ./configure [OPTION]... [VAR=VALUE]...

To assign environment variables (e.g., CC, CFLAGS...), specify them as
VAR=VALUE.  See below for descriptions of some of the useful variables.

Defaults for the options are specified in brackets.

Configuration:
  -h, --help              display this help and exit
      --help=short        display options specific to this package
      --help=recursive    display the short help of all the included packages
  -V, --version           display version information and exit
  -q, --quiet, --silent   do not print `checking...' messages
      --cache-file=FILE   cache test results in FILE [disabled]
  -C, --config-cache      alias for `--cache-file=config.cache'
  -n, --no-create         do not create output files
      --srcdir=DIR        find the sources in DIR [configure dir or `..']

Installation directories:
  --prefix=PREFIX         install architecture-independent files in PREFIX
                          [/usr]
  --exec-prefix=EPREFIX   install architecture-dependent files in EPREFIX
                          [PREFIX]

By default, `make install' will install all the files in
`/usr/bin', `/usr/lib' etc.  You can specify
an installation prefix other than `/usr' using `--prefix',
for instance `--prefix=$HOME'.

For better control, use the options below.

Fine tuning of the installation directories:
  --bindir=DIR           user executables [EPREFIX/bin]
  --sbindir=DIR          system admin executables [EPREFIX/sbin]
  --libexecdir=DIR       program executables [EPREFIX/libexec]
  --datadir=DIR          read-only architecture-independent data [PREFIX/share]
  --sysconfdir=DIR       read-only single-machine data [PREFIX/etc]
  --sharedstatedir=DIR   modifiable architecture-independent data [PREFIX/com]
  --localstatedir=DIR    modifiable single-machine data [PREFIX/var]
  --libdir=DIR           object code libraries [EPREFIX/lib]
  --includedir=DIR       C header files [PREFIX/include]
  --oldincludedir=DIR    C header files for non-gcc [/usr/include]
  --infodir=DIR          info documentation [PREFIX/info]
  --mandir=DIR           man documentation [PREFIX/man]

Optional Features:
  --disable-FEATURE       do not include FEATURE (same as --enable-FEATURE=no)
  --enable-FEATURE[=ARG]  include FEATURE [ARG=yes]
  --enable-verbose-printk  enables verbose printk (file + line number)

Optional Packages:
  --with-PACKAGE[=ARG]    use PACKAGE [ARG=yes]
  --without-PACKAGE       do not use PACKAGE (same as --with-PACKAGE=no)
  --with-cross=dir        give the cross-compile prefix
  --with-kernel=dir       give the directory with kernel sources
                          [/usr/src/linux]
  --with-build=dir        give the directory with kernel build tree
  --with-redhat=no,yes,auto  specify Red Hat kernel build
  --with-suse=no,yes,auto  specify SUSE kernel build
  --with-moddir=/path     give the path for the alsa driver kernel modules
                          [/lib/modules/<KVER>/misc]
  --with-debug=level      give the debug level (none,basic,full,detect)
  --with-isapnp=yes,no,auto  driver will (not) be compiled with ISA PnP support
  --with-sequencer=yes,no  driver will (not) be compiled with sequencer support
  --with-oss=no,yes       driver will (not) be compiled with OSS/Free emulation
  --with-pcmcia=kernel,external   support kernel PCMCIA driver or external PCMCIA driver
  --with-pcmcia-root=dir  specify the root directory of external PCMCIA source-tree
  --with-asihpk=dir       specify the AudioScience HPK source code tree
  --with-cards=<list>     compile driver for cards in <list>;
                          cards may be separated with commas;
                          'all' compiles all drivers;
                          Possible cards are:
                          seq-dummy, dummy, virmidi, mtpav, serial-u16550,
                          mpu401, serialmidi, loopback, portman2x4,
                          ad1816a, ad1848, cs4231, cs4232, cs4236, es968,
                          es1688, es18xx, gusclassic, gusextreme, gusmax,
                          interwave, interwave-stb, opti92x-ad1848,
                          opti92x-cs4231, opti93x, sb8, sb16, sbawe,
                          wavefront, als100, azt2320, cmi8330, dt019x,
                          opl3sa2, sgalaxy, sscape, pc98-cs4232,
                          msnd-pinnacle, ali5451, atiixp, atiixp-modem,
                          au8810, au8820, au8830, azt3328, bt87x, cs46xx,
                          cs4281, emu10k1, korg1212, mixart, nm256, rme32,
                          rme96, rme9652, hdsp, trident, ymfpci, als4000,
                          cmipci, ens1370, ens1371, es1938, es1968,
                          maestro3, fm801, fm801-tea575x, ice1712, ice1724,
                          intel8x0, intel8x0m, sonicvibes, via82xx, vx222,
                          pdplus, hdspm, emu10k1x, audigyls, azx,
                          via82xx-modem, asihpi, powermac, sa11xx-uda1341,
                          usb-audio, usb-usx2y, vxpocket, vxp440,
                          pdaudiocf, sun-amd7930, sun-cs4231, harmony
                          Possible additional options are:
                          sb16-csp, bt87x-overclock, cs46xx-new-dsp

Some influential environment variables:
  CC          C compiler command
  CFLAGS      C compiler flags
  LDFLAGS     linker flags, e.g. -L<lib dir> if you have libraries in a
              nonstandard directory <lib dir>
  CPPFLAGS    C/C++ preprocessor flags, e.g. -I<include dir> if you have
              headers in a nonstandard directory <include dir>
  CPP         C preprocessor

Use these variables to override the choices made by `configure' or to help
it to find libraries and programs with nonstandard names/locations.

sebb@ubuntu:/usr/src/alsa/alsa-driver-1.0.7 $ sudo ./configure --with-cards=audigyls --with-sequencer=yes;make;make install
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/alsa/alsa-driver-1.0.7
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel version... 0.0.0
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 3.3.4 (Debian 1:3.3.4-9ubuntu5)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... "no"
checking for existing ALSA module... "no"
checking for Red Hat kernel... "auto"
checking for Red Hat kernel... "no"
checking for SUSE kernel... "auto"
checking for SUSE kernel... "no"
checking to modify of kernel linux/kmod.h... "yes"
cat: /usr/src/linux/include/linux/kmod.h: No such file or directory
checking for kernel linux/compiler.h... "no"
Creating a dummy <linux/compiler.h>...
checking for kernel linux/pm.h... "no"
Creating a dummy <linux/pm.h>...
checking for kernel linux/spinlock.h... "no"
Creating a dummy <linux/spinlock.h>...
checking for kernel linux/irq.h... "no"
Creating a dummy <linux/irq.h>...
checking for kernel linux/threads.h... "no"
Creating a dummy <linux/threads.h>...
checking for kernel linux/rwsem.h... "no"
Creating a dummy <linux/rwsem.h>...
checking for kernel linux/gameport.h... "no"
Creating a dummy <linux/gameport.h>...
checking for kernel linux/devfs_fs_kernel.h... "no"
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... "no"
Creating a dummy <linux/highmem.h>...
checking for kernel linux/workqueue.h... "no"
checking for kernel linux/dma-mapping.h... "no"
checking for kernel asm/hw_irq.h... "no"
Creating a dummy <asm/hw_irq.h>...
checking for kernel linux/device.h... "no"
checking for kernel linux/jiffies.h... "no"
checking for kernel linux/compat.h... "no"
checking for kernel linux/adb.h... "no"
Creating <linux/adb.h>...
checking for kernel linux/cuda.h... "no"
Creating <linux/cuda.h>...
checking for kernel linux/pmu.h... "no"
Creating <linux/pmu.h>...
checking for kernel linux/moduleparam.h... "no"
checking for kernel linux/syscalls.h... "no"
checking for exported symbol dump_stack... grep: /usr/src/linux/kernel/ksyms.c: No such file or directory
"no"
checking for kernel module symbol versions... "no"
checking for PCI support in kernel... "no"
checking for I2C driver in kernel... unknown
checking for SGI/MIPS (HAL2) architecture... "no"
checking for directory to store kernel modules... /lib/modules/0.0.0/misc
checking for verbose printk... on
checking for debug level... none
checking for processor type... "unknown"
checking for SMP... "no"
checking for ISA PnP driver in kernel... no
checking for PnP driver in kernel... no
checking for ISA PnP support... yes
checking for strlcpy... "no"
checking for snprintf... "no"
checking for scnprintf... "no"
checking for sscanf... "no"
checking for vmalloc_to_page... "no"
checking for old kmod... "yes"
checking for PDE... "no"
checking for pci_set_consistent_dma_mask... "no"
checking for tty->count is the atomic type... "no"
checking for remap_pfn_range... "no"
checking for new remap_page_range... "no"
checking for kcalloc... "no"
checking for saved_config_space in pci_dev... "no"
checking for acpi_register_gsi... "no"
checking for old kill_fasync... "no"
checking for dma_addr_t... "no"
checking for MUTEX macros... "no"
Symlinking <linux/isapnp.h>...
checking for driver version... 1.0.7
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for RTC callback support in kernel... "no"
checking for Procfs support... "no"
checking for USB support... "no"
checking for USB module support... "no"
checking for kernel PCMCIA
checking for PCMCIA support... "no"
checking for PCMCIA module support... "no"
checking for PC9800 support in kernel... "no"
checking for parallel port support... "no"
checking for parallel port module support... "no"
checking for which soundcards to compile driver for... configure: error: Unsupported soundcard audigyls
make all-deps
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.7'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.7'

Please, run the configure script as first...

rm -f /snd*.*o /persist.o /isapnp.o
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.7/acore'
Makefile:6: /usr/src/alsa/alsa-driver-1.0.7/Makefile.conf: No such file or directory
make[1]: *** No rule to make target `/usr/src/alsa/alsa-driver-1.0.7/Makefile.conf'.  Stop.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.7/acore'
make: *** [install-modules] Error 1
sebb@ubuntu:/usr/src/alsa/alsa-driver-1.0.7 $
[/INDENT]

Wishing someone will be able to solve my problem.

---

