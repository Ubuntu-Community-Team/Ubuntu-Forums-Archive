---
title: "Xilinx ISE Webpack"
date: 2007-02-25
forum: General Help
---

### Post by hvymtlsteve on 2007-02-25
Hi guys, 
I intend to start using the Xilinx ISE WebPack software to study VHDL synthesis and program FPGA boards. If possible I would like to be able to run this on my Ubuntu Linux machine here at home. The site says it's supported for Redhat Enterprise 3 and 4, but is it still possible (or likely) that it would work on Ubuntu?

If it turns out that it won't work for some reason, I may have to crack and reconfigure my computer to dual boot with Windows XP :( Or I can just put the software on my old laptop, I suppose. It would be nice to be able to do everything I need on the 
Probably my main reason for switching to Linux (aside from Microsoft being the devil) is that it is much simpler for writing programs to interface with my electronic devices.. I do not want to have to deal with the Win32 API or Active X controls for serial communications, ya know? Reading and writing ttyS0 or ttyUSB0 is much easier. 

If there's anyone out there who knows this Xilinx software, please let me know what you think... 
Steve

---

### Post by hvymtlsteve on 2007-02-25
Hmm so I tried installing this software but when I ran the setup executable I just got a bus error. I guess I might not be able to do this...

---

### Post by hvymtlsteve on 2007-02-26
Here's an update for anyone who's interested. 
For whatever reason I was just kind of unable to get the installer for the newest version, 9.2i, to run at all because of that bus error thing. 

I decided to give 8.2i a shot instead. When I downloaded this directly from Xilinx's website, (with either web install or single file download) I always got a checksum error when I tried to run the installer shell script. 
On Google I found some old mirror site, however, that has both the Web Install and single file download of 8.2.. it's just very slow to download (got 100kB/second as opposed to about 1MB/s from Xilinx.com). The Web Install would run, but couldn't get the files it was looking for or something.. so I had to download the single file version, which is over a gig. 
This actually worked, and installed the program for me. 
If anyone wants it, the site is:
[http://tg.x-net.hu/files/xilinx/](http://tg.x-net.hu/files/xilinx/)

Sweet deal. 


Steve

---

### Post by lognok on 2007-03-18
Just installed ISE WebPACK 9.1i on my Feisty Herd5 using the webinstall without any problems.
Haven't tried to program an actual device yet, but I'll get the chance next week.
Also tried the webupdate to update to SP2, but ran out of space on my hd ](*,) since I've only got 10GB on that partition.
When Feisty beta arrives, I'll give it a bigger partition and try again.

---

### Post by fca_neo on 2007-03-23
hey, I'm trying to do the same thing.

I have a Xilinx spartan board and I installed the ISE Webpack 9.1i just fine but i cannot get the drivers installed correctly.

The software works just fine but when I try to program the board it says that the windrvr module is not loaded and that I should reinstall it. I reinstalled it many times using the webpack and the driver installer from the xilinx website but I cannot get it to work. 

It always says there is an error. 

```
carlos@Neb:~/Documents/FPGA/install_drivers$ sudo ./install_drivers
Password:
--Kernel version = 2.6.17-11-generic.
--Arch = i686.
--Installer version = 1029
--User has root permission.
--File /lib/modules/misc/install_windrvr6 does not exist.
--Installing windrvr6---------------------------------------------
loading cache ./config.cache
checking for cpu architecture... i386
checking for WinDriver root directory... /home/carlos/Documents/FPGA/install_drivers/linux_drivers/windriver32
checking for linux kernel source... found at /lib/modules/2.6.17-11-generic/build
checking for lib directory... /usr/lib
checking which directories to include... -I/lib/modules/2.6.17-11-generic/build/include -I/lib/modules/2.6.17-11-generic/build/include/asm/mach-default
checking linux kernel version... 2.6.17-11-generic
checking for modules installation directory... /lib/modules/2.6.17-11-generic/kernel/drivers/misc
checking for gcc kernel version... 4
checking output directory... LINUX.2.6.17-11-generic.i386
checking target... LINUX.2.6.17-11-generic.i386/windrvr6.ko
checking for usb support... yes
checking for regparm kernel option... 1
checking for right linked object... windrvr_gcc_v3_regparm.a
checking for modpost location... /lib/modules/2.6.17-11-generic/build/scripts/mod/modpost
checking for udev support... no
creating ./config.status
creating makefile
rm -f core LINUX.2.6.17-11-generic.i386/windrvr6.ko LINUX.2.6.17-11-generic.i386/*
cc -c -O2 -Wall -DLINUX -D__KERNEL__ -DMODULE -DWINDRIVER_KERNEL  -DLINUX_USB_SUPPORT -mpreferred-stack-boundary=2 -mregparm=3 -nostdinc -iwithprefix include -Wstrict-prototypes -Wno-trigraphs             -fno-common -pipe -O -I/lib/modules/2.6.17-11-generic/build/include -I/lib/modules/2.6.17-11-generic/build/include/asm/mach-default -I/home/carlos/Documents/FPGA/install_drivers/linux_drivers/windriver32/include -I/home/carlos/Documents/FPGA/install_drivers/linux_drivers/windriver32 -fno-strict-aliasing -D"KBUILD_STR(s)=#s" -D"KBUILD_MODNAME=KBUILD_STR(windrvr6)" -D"KBUILD_BASENAME=KBUILD_STR(windrvr6)" -c -o LINUX.2.6.17-11-generic.i386/linux_wrappers.o linux_wrappers.c
cc -c -O2 -Wall -DLINUX -D__KERNEL__ -DMODULE -DWINDRIVER_KERNEL  -DLINUX_USB_SUPPORT -mpreferred-stack-boundary=2 -mregparm=3 -nostdinc -iwithprefix include -Wstrict-prototypes -Wno-trigraphs             -fno-common -pipe -O -I/lib/modules/2.6.17-11-generic/build/include -I/lib/modules/2.6.17-11-generic/build/include/asm/mach-default -I/home/carlos/Documents/FPGA/install_drivers/linux_drivers/windriver32/include -I/home/carlos/Documents/FPGA/install_drivers/linux_drivers/windriver32 -fno-strict-aliasing -D"KBUILD_STR(s)=#s" -D"KBUILD_MODNAME=KBUILD_STR(windrvr6)" -D"KBUILD_BASENAME=KBUILD_STR(windrvr6)" -c -o LINUX.2.6.17-11-generic.i386/wdusb_linux.o wdusb_linux.c
ld -m elf_i386 -r -o LINUX.2.6.17-11-generic.i386/windrvr6.o LINUX.2.6.17-11-generic.i386/linux_wrappers.o LINUX.2.6.17-11-generic.i386/wdusb_linux.o windrvr_gcc_v3_regparm.a
/lib/modules/2.6.17-11-generic/build/scripts/mod/modpost LINUX.2.6.17-11-generic.i386/windrvr6.o
cc -c -O2 -Wall -DLINUX -D__KERNEL__ -DMODULE -DWINDRIVER_KERNEL  -DLINUX_USB_SUPPORT -mpreferred-stack-boundary=2 -mregparm=3 -nostdinc -iwithprefix include -Wstrict-prototypes -Wno-trigraphs             -fno-common -pipe -O -I/lib/modules/2.6.17-11-generic/build/include -I/lib/modules/2.6.17-11-generic/build/include/asm/mach-default -I/home/carlos/Documents/FPGA/install_drivers/linux_drivers/windriver32/include -I/home/carlos/Documents/FPGA/install_drivers/linux_drivers/windriver32 -fno-strict-aliasing -D"KBUILD_STR(s)=#s" -D"KBUILD_MODNAME=KBUILD_STR(windrvr6)" -D"KBUILD_BASENAME=KBUILD_STR(windrvr6)" -c -o LINUX.2.6.17-11-generic.i386/windrvr6.mod.o LINUX.2.6.17-11-generic.i386/windrvr6.mod.c
In file included from /lib/modules/2.6.17-11-generic/build/include/asm/thread_info.h:16,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/thread_info.h:21,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/capability.h:45,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/sched.h:44,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/module.h:9,
                 from LINUX.2.6.17-11-generic.i386/windrvr6.mod.c:1:
/lib/modules/2.6.17-11-generic/build/include/asm/processor.h:76: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/lib/modules/2.6.17-11-generic/build/include/asm/processor.h:76: error: requested alignment is not a constant
In file included from /lib/modules/2.6.17-11-generic/build/include/linux/sched.h:49,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/module.h:9,
                 from LINUX.2.6.17-11-generic.i386/windrvr6.mod.c:1:
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:210:31: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:210:31: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:210:31: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:210:31: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:210:31: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:210:31: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:210:31: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:210:31: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:210:31: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:210:31: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:210:31: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:210:31: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:210:31: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:210:31: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:210:31: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:210:31: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:254:46: error: division by zero in #if
In file included from /lib/modules/2.6.17-11-generic/build/include/linux/sched.h:49,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/module.h:9,
                 from LINUX.2.6.17-11-generic.i386/windrvr6.mod.c:1:
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_msecs’:
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:259: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:259: error: (Each undeclared identifier is reported only once
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:259: error: for each function it appears in.)
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:265:46: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_usecs’:
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:270: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:278:46: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h: In function ‘msecs_to_jiffies’:
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:283: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:291:46: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h: In function ‘usecs_to_jiffies’:
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:296: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h: In function ‘timespec_to_jiffies’:
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:315: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:321: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_timespec’:
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:334: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h: In function ‘timeval_to_jiffies’:
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:356: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:360: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_timeval’:
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:372: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:385:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:385:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:385:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:385:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:385:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:385:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:385:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:385:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:385:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:385:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:385:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:385:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:385:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:385:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:385:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:385:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_clock_t’:
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:386: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h: In function ‘clock_t_to_jiffies’:
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:397: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:416:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:416:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:416:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:416:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:416:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:416:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:416:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:416:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:416:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:416:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:416:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:416:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:416:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:416:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:416:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:416:6: error: division by zero in #if
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h: In function ‘jiffies_64_to_clock_t’:
/lib/modules/2.6.17-11-generic/build/include/linux/jiffies.h:417: error: ‘CONFIG_HZ’ undeclared (first use in this function)
In file included from /lib/modules/2.6.17-11-generic/build/include/linux/module.h:22,
                 from LINUX.2.6.17-11-generic.i386/windrvr6.mod.c:1:
/lib/modules/2.6.17-11-generic/build/include/asm/module.h:60:2: error: #error unknown processor family
LINUX.2.6.17-11-generic.i386/windrvr6.mod.c: At top level:
LINUX.2.6.17-11-generic.i386/windrvr6.mod.c:5: error: expected ‘,’ or ‘;’ before ‘MODULE_PROC_FAMILY’
LINUX.2.6.17-11-generic.i386/windrvr6.mod.c:8: error: variable ‘__this_module’ has initializer but incomplete type
LINUX.2.6.17-11-generic.i386/windrvr6.mod.c:9: error: unknown field ‘name’ specified in initializer
LINUX.2.6.17-11-generic.i386/windrvr6.mod.c:9: warning: excess elements in struct initializer
LINUX.2.6.17-11-generic.i386/windrvr6.mod.c:9: warning: (near initialization for ‘__this_module’)
LINUX.2.6.17-11-generic.i386/windrvr6.mod.c:10: error: unknown field ‘init’ specified in initializer
LINUX.2.6.17-11-generic.i386/windrvr6.mod.c:10: warning: excess elements in struct initializer
LINUX.2.6.17-11-generic.i386/windrvr6.mod.c:10: warning: (near initialization for ‘__this_module’)
make: *** [modpost] Error 1
--make windrvr rc = 2
--install_windrvr6 rc = 2
--Installing USB drivers------------------------------------------
--Using udev.
--File /usr/share/xusbdfwu.hex exists.
--File /usr/share/xusbdfwu.hex version = 1025
--File xusbdfwu.hex exists.
--File xusbdfwu.hex version = 1025
--File xusbdfwu.hex is already updated.
--File /etc/udev/rules.d/xusbdfwu.rules exists.
--File /etc/udev/rules.d/xusbdfwu.rules version = 0001
--File xusbdfwu.rules exists.
--File xusbdfwu.rules version = 0001
--File xusbdfwu.rules is already updated.
--File /sbin/fxload exists.
--install_pcusb rc =  0
--Module windrvr6 is not running.
--Module xpc4drvr is not running.
--Note: By default, the file permission of /dev/windrvr6 is enabled for the root user only
  and must be changed to allow access to other users.


```

Do you have any clue of how can i fix it. I only want the parallel port to work. BTW I use Kubuntu 6.10 and I'm very new to Linux.

If I don't find a solution soon enough I will have to install windows in dual boot :( .

---

### Post by bbhome on 2007-05-15
So I just got the Xilinx ISE 9.1i tools working on Ubuntu 7.04 Festy Fawn (2.6.20-15-generic).  The tricky part was getting the parallel IV cable working.  I have not tested the USB programming cable.  There is good information on the web that helped me.  You may have to read the following links to understand some of the steps I list below.

[http://gentoo-wiki.com/HOWTO_Xilinx](http://gentoo-wiki.com/HOWTO_Xilinx)
[http://gentoo-wiki.com/Talk:HOWTO_Xilinx](http://gentoo-wiki.com/Talk:HOWTO_Xilinx)
[http://www.freelabs.com/~whitis/electronics/fpga/xilinx_install_deb3.1.html](http://www.freelabs.com/~whitis/electronics/fpga/xilinx_install_deb3.1.html)

Here are the steps I did

0) installed ISE9.1i tools.

1) Downloaded and extracted
   install_drivers.tar.gz  (from Xilinx answer record #22648)
   WD811LN.tgz  (from jungo)

2) Linked the jungo drivers into install_drivers
   mv install_drivers/linux_drivers/windriver32/windrvr
install_drivers/linux_drivers/windriver32/windrvr_orig
   ln -s WinDriver/redist
install_drivers/linux_drivers/windriver32/windrvr

3) Changed /bin/sh to point to /bin/bash instead of /bin/dash
   sudo rm /bin/sh
   sudo ln -s /bin/bash /bin/sh

4) Set CC to gcc-3.3 compiler (not sure if this is necessary)
   export CC=/usr/bin/gcc-3.3   

5) Get header sources and fxload
   sudo apt-get install linux-headers-2.6.20-15-generic
   sudo apt-get install fxload

6) Update line 544 of ...windriver32/windrvr/linux_wrapper.c to
   bh->data = *((atomic_long_t *)data);

7) Run Xilinx install_drivers script
   sudo ./install_drivers

8) Make windrvr6 world accessable
   sudo chmod 666 /dev/windrvr6

9) modified /etc/rc.local to be
   /lib/modules/2.6.20-15-generic/kernel/drivers/misc/install_windrvr6
windrvr6 no
   /lib/modules/2.6.20-15-generic/kernel/drivers/misc/install_xpc4drvr
   chmod 666 /dev/windrvr6
   exit 0

--Brandon

---

### Post by macson_g on 2007-05-19
Please note that to compile the windrv driver, you have to have configured sources linked in /lib/modules/.../source

---

