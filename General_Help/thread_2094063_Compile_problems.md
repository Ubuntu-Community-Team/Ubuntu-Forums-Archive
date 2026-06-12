---
title: "Compile problems"
date: 2012-12-12
forum: General Help
---

### Post by fyredraken on 2012-12-12
Hello

I am trying to install Asterisk and Zaptel using this guide ([http://expectus.hubpages.com/hub/How-to-Install-Asterisk-on-Ubuntu-Setting-up-Asterisk-PBX](http://expectus.hubpages.com/hub/How-to-Install-Asterisk-on-Ubuntu-Setting-up-Asterisk-PBX)) with updated packages from asterisk.  I am having a compile error with zaptel that I'm not sure how to fix (asterisk and zaptel are not in the repositories).  I am using Using Server 12.04 with desktop package installed.

My compile output is (for configure and make):
```
root@PbxBox:/usr/src/zaptel-1.4.12.1# ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for GNU make... make
checking for grep... /bin/grep
checking for sh... /bin/bash
checking for ln... /bin/ln
checking for wget... /usr/bin/wget
checking for grep that handles long lines and -e... (cached) /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for initscr in -lcurses... yes
checking curses.h usability... yes
checking curses.h presence... yes
checking for curses.h... yes
checking for initscr in -lncurses... yes
checking for curses.h... (cached) yes
checking for newtBell in -lnewt... yes
checking newt.h usability... yes
checking newt.h presence... yes
checking for newt.h... yes
checking for usb_init in -lusb... no
configure: creating ./config.status
config.status: creating build_tools/menuselect-deps
config.status: creating makeopts
config.status: creating build_tools/make_firmware_object
configure: *** Zaptel build successfully configured ***
root@PbxBox:/usr/src/zaptel-1.4.12.1# make
make[1]: Entering directory `/usr/src/zaptel-1.4.12.1/menuselect'
make[2]: Entering directory `/usr/src/zaptel-1.4.12.1/menuselect'
make[2]: `menuselect' is up to date.
make[2]: Leaving directory `/usr/src/zaptel-1.4.12.1/menuselect'
make[1]: Leaving directory `/usr/src/zaptel-1.4.12.1/menuselect'
make[1]: Entering directory `/usr/src/zaptel-1.4.12.1'
make[2]: Entering directory `/usr/src/zaptel-1.4.12.1/menuselect'
make[3]: Entering directory `/usr/src/zaptel-1.4.12.1/menuselect'
make[3]: `menuselect' is up to date.
make[3]: Leaving directory `/usr/src/zaptel-1.4.12.1/menuselect'
make[2]: Leaving directory `/usr/src/zaptel-1.4.12.1/menuselect'
make -C /lib/modules/3.2.0-34-generic-pae/build ARCH=i386 SUBDIRS=/usr/src/zaptel-1.4.12.1/kernel HOTPLUG_FIRMWARE=yes KBUILD_OBJ_M="pciradio.o tor2.o torisa.o wcfxo.o wct1xxp.o wctdm.o wcte11xp.o wcusb.o zaptel.o ztd-eth.o ztd-loc.o ztdummy.o ztdynamic.o zttranscode.o wct4xxp/ wctc4xxp/ xpp/ wctdm24xxp/ wcte12xp/" modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-34-generic-pae'
  CC [M]  /usr/src/zaptel-1.4.12.1/kernel/pciradio.o
In file included from /usr/src/zaptel-1.4.12.1/kernel/zaptel.h:39:0,
                 from /usr/src/zaptel-1.4.12.1/kernel/pciradio.c:56:
/usr/src/zaptel-1.4.12.1/kernel/zconfig.h:26:28: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
make[3]: *** [/usr/src/zaptel-1.4.12.1/kernel/pciradio.o] Error 1
make[2]: *** [_module_/usr/src/zaptel-1.4.12.1/kernel] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-34-generic-pae'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/zaptel-1.4.12.1'
make: *** [all] Error 2

```

I'm not sure what I need to do, would someone guide me in the right direction please?

---

### Post by drmrgd on 2012-12-12
Looks like the system might be missing autoconf.  Try installing that and automake while you're at it, and then compiling again:

```
sudo apt-get install automake autoconf
```

---

### Post by fyredraken on 2012-12-12
I have the current automake and autoconf installed

autoconf is already the newest version.
automake is already the newest version.

---

### Post by sandyd on 2012-12-12
zaptel is obsolete, see dahdi

---

