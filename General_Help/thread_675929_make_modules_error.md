---
title: "make modules error"
date: 2008-01-23
forum: General Help
---

### Post by ugm6hr on 2008-01-23
I have a kernel level driver for a new DVB USB card.  I have the driver for it.

In trying to compile the driver module, I have edited menuconfig (sudo make menuconfig) to include the driver, but I cannot make the modules

```
xxx@zzz:/usr/src/linux-headers-2.6.22-14-generic$ sudo make modules
[sudo] password for xxx:
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[1]: *** No rule to make target `arch/i386/kernel/asm-offsets.c', needed by `arch/i386/kernel/asm-offsets.s'. Stop.
make: *** [prepare0] Error 2

```

Where would it look for the rule to make the first file?

I have included the readme for info (step d is the problem):
```
	Step a. copy all files to linux kernel 2.6.21.4 source code in drivers/media/dvb/dvb-usb



	Step b. add the following lines to Makefile in dvb-usb or you can refereence ex_Makefile.

dvb-usb-rtl2831u-objs = math_mpi.o foundation.o demod_rtl2830.o tuner_demod_io.o tuner_mxl5005s.o mt_spuravoid.o \

	mt_userdef.o mt2060_basic.o tuner.o MT2060Tuner.o rtd2830.o rtd2830u.o

obj-$(CONFIG_DVB_USB_RTL2831U) += dvb-usb-rtl2831u.o



	Step c. add the following lines to Kconfig in dvb-usb or you can refereence ex_Kconfig.	

config DVB_USB_RTL2831U

	tristate "Realtek RTL2831U DVB-T USB2.0 support"

	depends on DVB_USB

	help

	  Realtek RTL2831U DVB-T driver.



	Step d.

		1. Choose the required modules, In KERNEL_DIR,

   		% make menuconfig

	

		Device Drivers  --->

			Multimedia devices  ---> 

			    Digital Video Broadcasting Devices  --->  

				[*] DVB For Linux 

				<M>   DVB Core Support

				...................

				<M>   Support for various USB DVB devices----->

					.................................

					<M>   Realtek RTL2831U DVB-T USB2.0 support





   		% make modules

   		% make modules_install





		2. Installation

   		% modprobe dvb-usb-rtl2831u

   		

   		3. check 

   		%lsmod | grep dvb

   		 dvb_usb_rtl2831u

   		 dvb_usb

   		 dvb_core

   		 dvb_pll

   		 i2c_core
```

---

### Post by ugm6hr on 2008-01-23
Obviously I didn't appreciate that you *do* have to recompile the whole kernel to get this to work.

So adding the linux-source package did it with a bit of help: [http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way](http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way)

It's compiling now - fingers crossed!

EDIT: Success?  Don't know yet.  Have to check if it actually works with DVB now!

EDIT2: I wrote the original edit in a hurry so that I wouldn't forget.  I have now tidied it up and merged info from the various sections.

I have compiled a custom kernel from a default Ubuntu 7.10 installation as follows:

Install following packages from Synaptic / apt-get:
build-essential fakeroot kernel-package libncurses5-dev
linux-source-2.6.22 (referred to below as linux-source-<version>)

```
sudo adduser <my_username> src
```
Logout & log back in
```
cd /usr/src
tar xjvf linux-source-<version>.tar.bz2
ln -s linux-source-<version> linux

```

Extract and copy all driver files to /usr/src/linux/drivers/media/dvb/dvb-usb

Add the following lines to Makefile in /usr/src/linux/drivers/media/dvb/dvb-usb:

```
dvb-usb-rtl2831u-objs = math_mpi.o foundation.o demod_rtl2830.o tuner_demod_io.o tuner_mxl5005s.o mt_spuravoid.o \
	mt_userdef.o mt2060_basic.o tuner.o MT2060Tuner.o rtd2830.o rtd2830u.o
obj-$(CONFIG_DVB_USB_RTL2831U) += dvb-usb-rtl2831u.o
```

Add the following lines to Kconfig in /usr/src/linux/drivers/media/dvb/dvb-usb: 	

```
config DVB_USB_RTL2831U
	tristate "Realtek RTL2831U DVB-T USB2.0 support"
	depends on DVB_USB
	help
	  Realtek RTL2831U DVB-T driver.

```

```
cd /usr/src/linux
make menuconfig
```

Use arrow keys to navigate, Enter to select submenu and Y to choose options (mark with * or M to activate as below):
```
		Device Drivers  --->
			Multimedia devices  ---> 
				[*] DVB For Linux 
				[*]   Load and attach frontend modules as needed
				[*]   DVB/ATSC adapters --->
					<M>   Support for various USB DVB devices
					.......
					<M>   Realtek RTL2831U DVB-T USB2.0 support (new)

```
Exit (multiple times) and select Yes to save kernel config on final exit

```
cd /usr/src/linux
fakeroot make-kpkg clean
fakeroot make-kpkg --append-to-version=-dvb kernel_image --initrd binary

```

Then install the new kernel image that has just been created (example below):
```
cd /usr/src
sudo dpkg -i linux-image-2.6.22.9-dvb_2.6.22.9-dvb-10.00.Custom_i386.deb
```

Then reboot into new kernel (select from Grub)
If it doesn't work, you should just be able to reboot and select your usual kernel (and maybe try again!)

This should load the driver after the reboot into the custom -dvb kernel:
```
modprobe dvb-usb-rtl2831u
```
If it works, you can load the driver module at boot by adding *dvb-usb-rtl2831u* to the bottom of:
```
gksudo gedit /etc/modules
```

Problems:
Restricted Drivers don't work - So, wifi needs to be manually configured.
No sound drivers installed (oops)
Not sure whether it even works yet!

---

### Post by tiwag on 2008-01-24
> **ugm6hr said:**
> Problems:
Restricted Drivers don't work - So, wifi needs to be manually configured.
No sound drivers installed (oops)
...

see here "Rebuilding linux-restricted-modules''
[https://help.ubuntu.com/community/Kernel/Compile#head-4591a640f1ecb03492f49521d7c055cba2845ca1](https://help.ubuntu.com/community/Kernel/Compile#head-4591a640f1ecb03492f49521d7c055cba2845ca1)

good luck, i'm trying too

---

### Post by ugm6hr on 2008-01-24
More for my own benefit than others (sorry) - here is how I got sound to work with my **custom kernel** on Acer5051AWXMi (not necessary for standard Ubuntu kernel).

As above, but on make menuconfig:
Find device drivers -> sound -> Intel Sound - mark as modular

I have also installed madwifi manually ([http://madwifi.org/wiki](http://madwifi.org/wiki) - look for download) rather than recompiling Restricted Drivers:
Install package *madwifi-tools* from Synaptic

Install the custom compiled linux-headers package (I just double-clicked it in /usr/src to do it through GDebi)

```
cd ~/madwifi-0.9.3.3 (if this is where it is downloaded, for example)
sudo make clean
sudo make
sudo make install
sudo modprobe ath_pci
```

Assuming that worked (look for ath_pci in *lsmod* output), just add *ath_pci* to the bottom of etc/modules.

Haven't actually connected to a wifi access point yet to confirm, but don't see why it shouldn't work.

Now I just need to check whether wifi and the DVB card work!  The modules seem to have compiled properly, and lsmod lists them now.  Fingers crossed again!

---

### Post by ugm6hr on 2008-01-26
OK. First test seems promising...

Wifi OK.

USB DVB-T - device light turns on when I open Kaffeine.

It detects the DVB device.  It claims the device can autoscan...

Now I just need to take it somewhere with a decent Freeview signal to try it out (it doesn't pick up any channels in Windows either in my current location).

Should report back tommorrow with results (hopefully positive?)

---

### Post by tiwag on 2008-01-27
i could build the drivers too with building a new kernel,
but did not install this kernel until now on my laptop,
because i can't experiment i need it running stable...

now i'm searching for a way, how i can build the drivers as kernel-modules
and integrate them to the existing kernel.

i don't want a custom kernel with ubuntu, because i've choosen ubuntu
in order not have to maintain my kernel and system all the time ...

brgds, tiwag

---

### Post by ugm6hr on 2008-01-27
> **tiwag said:**
> now i'm searching for a way, how i can build the drivers as kernel-modules
and integrate them to the existing kernel.

I did wonder about that initially (as you can see from my original post in this thread).

Perhaps someone else could help with this?

Is there a way to compile a kernel-module that is not referenced in the original compiled (Ubuntu) kernel, and get it working?  Something akin to the way the "restricted driver" modules are installed was my thought process - although presumably the Ubuntu kernel must reference them....

So - in summary - can a new kenel module driver be "patched" on to the existing Ubuntu kernel without losing the Ubuntu supported kernel?

---

### Post by ugm6hr on 2008-01-27
I started this thread to ask about a problem with compiling, which I have done now (albeit with a custom kernel).

I've gone back to the thread in Multimedia to continue the discussion re: why it's not working now :(

[http://ubuntuforums.org/showthread.php?p=4216590#post4216590](http://ubuntuforums.org/showthread.php?p=4216590#post4216590)

---

