---
title: "creating a Makefile"
date: 2007-10-02
forum: General Help
---

### Post by ats1080s on 2007-10-02
my problem here is the DeLorme Earthmate LT 20.  i found a "fix" for it but once it gets to compiling the files i get nothing to do for "default"  here is the directions, can anyone see anything wrong?



The solution involves recompiling the module, which stopped working for the LT-20 after a patch introduced into the 2.6.19 tree. The patch I'm assuming fixed some issue with other devices which use the same driver, so be careful.

To get it to work I did the following:

1)installed the linux source tree:
sudo apt-get install linux-source-2.6.XX <- replace XX with your running kernel version, for me: 20.
cd /usr/src
tar -xvf linux-source-2.6.XX.bz2

2)Copied the files cypress_m8.h and cypress_m8.c from /usr/src/linux-source-2.6.XX/drivers/usb/serial/
to /usr/src/modules/

3)Changed dirs to /usr/src/modules,
created /usr/src/Makefile with the standard module creation 2.6 stuff:

obj-m := cypress_m8.o
KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)
default:
        $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

4) Commented out line 408 from cypress_m8.c, which should read:
   cypress_set_dead(port);
(anyway, if it isn't line 408 for you, it should be in the following if statement in function cypress_serial_control, which, after being commented out should look like this:
if (retval != 5) {
                err("%s - failed to retrieve serial line settings - %d", __FUNCTION__, retval);
                /*cypress_set_dead(port); // fix for LT-20*/
                return retval;
            } else ...

5) ran make

6) finally installed the new modules:
install -m 644 cypress_m8.ko /lib/modules/`uname -r`/kernel/drivers/cypress_m8.ko
depmod -a

7) tested with
cat /dev/ttyUSB0
all good -> lots out NMEA output.

Hope I didn't forget anything important, Good luck.

---

### Post by amp_man on 2007-10-02
Okay, try this instead (I wasn't able to get it to build either):

1) Do not move the files, just edit it inside the kernel source as specified above

2) do "cp /boot/config-`uname -r` /usr/src/linux-source-2.6.<XX>/.config", that should copy the running kernel config into the source

3) type "make && make module && sudo make install && sudo make modules_install", that will install the "new" kernel

4) run "sudo update-grub" to find the new kernel. It may overwrite the stock ubuntu kernel, or it may just install it as a new one. Either way it should be the top of the list when you reboot

5) reboot and give it a whirl

Hope it works!

---

### Post by ats1080s on 2007-10-03
doing this created a kernel panic.  [ 0.820000] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)  im going to do a fresh install and try it again, i was doing a lot of tinkering with the kernel files.

---

### Post by amp_man on 2007-10-03
Oops, forgot to mention that you also need to compile in support for your filesystem and IDE controller, that was completely my bad. Sorry.l

---

### Post by ats1080s on 2007-10-03
how do you go about doing that?

---

