---
title: "Need Help Installing Audio Driver"
date: 2008-01-05
forum: General Help
---

### Post by Shadowgaze on 2008-01-05
I'm having trouble getting my audio driver to work.  I followed the instructions that came with the driver on the mother board cd.  It is a ASUS P4C800/P4P800 Series motherboard

Here is the instructions
Quick install
=============

1) You must have full configured source for the Linux kernel which you
   want to use for the ALSA drivers. Note that ALSA drivers are part
   of the kernel, so there is necessary to resolve all symbol dependencies
   between the used kernel and ALSA driver code. Partly installed kernels
   (for example from distributor makers) can be unuseable for this action.
2) You must turn on sound support (soundcore module).
3) Run './configure' script.
   If you have ISA Plug & Play soundcard, use --with-isapnp=yes switch.
   If you want sequencer support, use --with-sequencer=yes switch.
   If you do not want OSS/Free emulation, use --with-oss=no switch.
   If you want turn on debug mode use --with-debug=full switch.
   If you want debug soundcard detection try --with-debug=detect switch.
   If you have kernel source code in another directory than /usr/src/linux,
   use --with-kernel=<kernel_directory>.
   Example: ./configure --with-isapnp=yes --with-debug=full
4) Run 'make install'.
5) Run the './snddevices' script to create new sound devices in /dev directory.
   Skip this step, if you have a kernel with the DEVFS support.
6) Edit your /etc/modules.conf (see the kmod support section below).
7) Run 'modprobe snd-xxxx' where xxxx is the name of your card.
   Note: If you have a ISA PnP soundcard you need to first run the isapnp
         program from isapnptools package to initialize your
         soundcard. You can also use the native ISA PnP support by
         using the --with-isapnp=yes configuration switch, in which
	 case you do not need the isapnptools package.


This is what I get.

shadowgaze@think-brick:~$ cd /home/shadowgaze/Desktop/alsa-driver-0.9.6
shadowgaze@think-brick:~/Desktop/alsa-driver-0.9.6$ ./configure
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables

---

### Post by eggdeng on 2008-01-05
Do ```
sudo apt-get install build-essential 
```then try again.

---

### Post by Shadowgaze on 2008-01-05
Thanks.  Thats one big hurdle down.  This is what I have now though.

shadowgaze@think-brick:~/Desktop/alsa-driver-0.9.6$ ./configure
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for executable suffix... 
checking for object suffix... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for ranlib... ranlib
checking for a BSD compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for gcc option to accept ANSI C... none needed
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/shadowgaze/Desktop/alsa-driver-0.9.6
checking cross compile... 
checking for directory with kernel source... /usr/src/linux
checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
shadowgaze@think-brick:~/Desktop/alsa-driver-0.9.6$ 

Any advice?

---

### Post by eggdeng on 2008-01-07
```
sudo apt-get install linux-kernel-headers
```
should do it.

---

### Post by Shadowgaze on 2008-01-07
Unfortunately, that didn't do it.

shadowgaze@think-brick:~$ sudo apt-get install linux-kernel-headers
[sudo] password for shadowgaze:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-kernel-headers is a virtual package provided by:
  linux-libc-dev 2.6.22-14.47
You should explicitly select one to install.
E: Package linux-kernel-headers has no installation candidate
shadowgaze@think-brick:~$ cd /usr/src/linux-headers-2.6.22-14/drivers/alsa-driver-0.9.6
shadowgaze@think-brick:/usr/src/linux-headers-2.6.22-14/drivers/alsa-driver-0.9.6$ ./configure
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for executable suffix... 
checking for object suffix... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for ranlib... ranlib
checking for a BSD compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for gcc option to accept ANSI C... none needed
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/linux-headers-2.6.22-14/drivers/alsa-driver-0.9.6
checking cross compile... 
checking for directory with kernel source... /usr/src/linux
checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
shadowgaze@think-brick:/usr/src/linux-headers-2.6.22-14/drivers/alsa-driver-0.9.6$

---

### Post by eggdeng on 2008-01-07
One more try
```
apt-get install kernel-package linux-headers-$(uname -r)
```
If apt suggests any more packages, sudo apt-get install them too.

---

### Post by Shadowgaze on 2008-01-08
Thanks for your help.  Audio is up and running.

---

