---
title: "GE Webcam Driver Install Help"
date: 2008-05-14
forum: General Help
---

### Post by Fordkiller on 2008-05-14
imm having a problem with my cam here and im not sure how to fix it at this point i have searched all the forums and i can't find a fix for it anywhere 

i have looked for the dev/video0 and thats missing and also i can't seen to find a linux driver for it at all 

i went into the symaptic package manager and install everything i could find for a web cam but still nothing  


this is the info i have on it 

GE HO98064 model number of the cam 

from the dmesg

[25231.622471] usb 2-1: new full speed USB device using uhci_hcd and address 4


from  the lsusb 

Bus 002 Device 004: ID 05a9:8519 OmniVision Technologies, Inc. 

now im not sure where to go with this so any help would be great thanks a lot

---

### Post by linuxwizard on 2008-05-14
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by Fordkiller on 2008-05-15
Hi linuxwizard i saw that you had posted that in another thread for someone having a problem like this with a different webcam and i have tryed it and i just get the bouncing logo so i tryed to change the setting and the cam is not found at all.... im lost at this point thanks for the input and all the help to get this working

---

### Post by linuxwizard on 2008-05-15
Your webcam > GE (Target) EasyCam PC Camera Pro HO98064 > is listed as working but it is showing 2 different sensors not sure which one is yours > [http://alpha.dyndns.org/ov511/cameras.html](http://alpha.dyndns.org/ov511/cameras.html)

---

### Post by Fordkiller on 2008-05-15
Thanks linuxwizard for the post back i went and got the info and read the read me and tryed to make the file and i keep getting errors. i changed the make file to the linux source but still get errors.. sorry im still learning this and trying. this is the log of the errors im getting

```
root@fordkiller-laptop:/home/fordkiller/Desktop/ov51x-1.65-1.12-mark# make install
make -C /lib/modules/2.6.24-16-generic/build M=/home/fordkiller/Desktop/ov51x-1.65-1.12-mark modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.o
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:42:26: error: linux/config.h: No such file or directory
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:207: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:209: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:211: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:213: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:216: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:220: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:223: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:227: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:229: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:231: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:234: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:236: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:239: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:242: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:244: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:246: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:248: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:250: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:252: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:254: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:256: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:258: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:260: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:262: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:264: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:267: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:270: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:272: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:274: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:276: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:278: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:280: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:282: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:285: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:288: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:290: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:292: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:294: error: expected ‘)’ before string constant
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c: In function ‘ov51x_init_isoc’:
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:5449: warning: assignment from incompatible pointer type
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c: In function ‘ov51x_v4l1_open’:
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:5705: error: implicit declaration of function ‘video_devdata’
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:5705: warning: initialization makes pointer from integer without a cast
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:5707: error: implicit declaration of function ‘video_get_drvdata’
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:5707: warning: initialization makes pointer from integer without a cast
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c: In function ‘ov51x_v4l1_close’:
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:5784: warning: initialization makes pointer from integer without a cast
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c: In function ‘ov51x_v4l1_ioctl_internal’:
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:5842: warning: initialization makes pointer from integer without a cast
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6246: error: dereferencing pointer to incomplete type
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c: In function ‘ov51x_v4l1_ioctl’:
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6358: warning: initialization makes pointer from integer without a cast
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6364: error: implicit declaration of function ‘video_usercopy’
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c: In function ‘ov51x_v4l1_read’:
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6384: warning: initialization makes pointer from integer without a cast
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c: In function ‘ov51x_v4l1_mmap’:
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6554: warning: initialization makes pointer from integer without a cast
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c: At top level:
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6625: error: variable ‘vdev_template’ has initializer but incomplete type
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6626: error: unknown field ‘owner’ specified in initializer
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6626: warning: excess elements in struct initializer
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6626: warning: (near initialization for ‘vdev_template’)
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6627: error: unknown field ‘name’ specified in initializer
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6627: warning: excess elements in struct initializer
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6627: warning: (near initialization for ‘vdev_template’)
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6628: error: unknown field ‘type’ specified in initializer
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6628: warning: excess elements in struct initializer
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6628: warning: (near initialization for ‘vdev_template’)
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6629: error: unknown field ‘hardware’ specified in initializer
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6629: error: ‘VID_HARDWARE_OV511’ undeclared here (not in a function)
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6629: warning: excess elements in struct initializer
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6629: warning: (near initialization for ‘vdev_template’)
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6630: error: unknown field ‘fops’ specified in initializer
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6630: warning: excess elements in struct initializer
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6630: warning: (near initialization for ‘vdev_template’)
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6632: error: unknown field ‘release’ specified in initializer
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6632: error: ‘video_device_release’ undeclared here (not in a function)
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6632: warning: excess elements in struct initializer
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6632: warning: (near initialization for ‘vdev_template’)
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6634: error: unknown field ‘minor’ specified in initializer
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6634: warning: excess elements in struct initializer
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:6634: warning: (near initialization for ‘vdev_template’)
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c: In function ‘ov51x_probe’:
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:8298: error: implicit declaration of function ‘video_device_alloc’
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:8298: warning: assignment makes pointer from integer without a cast
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:8302: error: dereferencing pointer to incomplete type
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:8302: error: dereferencing pointer to incomplete type
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:8302: error: dereferencing pointer to incomplete type
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:8304: error: dereferencing pointer to incomplete type
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:8306: error: implicit declaration of function ‘video_set_drvdata’
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:8314: error: implicit declaration of function ‘video_register_device’
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:8314: error: ‘VFL_TYPE_GRABBER’ undeclared (first use in this function)
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:8314: error: (Each undeclared identifier is reported only once
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:8314: error: for each function it appears in.)
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:8321: error: dereferencing pointer to incomplete type
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:8331: error: dereferencing pointer to incomplete type
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:8354: error: dereferencing pointer to incomplete type
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:8355: error: implicit declaration of function ‘video_device_release’
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:8357: error: implicit declaration of function ‘video_unregister_device’
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c: At top level:
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:8464: error: unknown field ‘owner’ specified in initializer
/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.c:8464: warning: initialization from incompatible pointer type
make[2]: *** [/home/fordkiller/Desktop/ov51x-1.65-1.12-mark/ov51x.o] Error 1
make[1]: *** [_module_/home/fordkiller/Desktop/ov51x-1.65-1.12-mark] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [all] Error 2

```

```
OVCAM_KVER := $(shell uname -r)
OVCAM_MAJMIN := $(shell echo $(OVCAM_KVER) | cut -d . -f 1-2)

# -------------------------- 2.4 KERNEL SUPPORT -------------------------------
ifeq ($(OVCAM_MAJMIN),2.4)

#################################### OPTIONS ##################################
# Change this to /usr/include if you get header file errors
INCLUDEDIR = /usr/include

CFLAGS = -D__KERNEL__ -DMODULE -DOUTSIDE_KERNEL -O2 -Wall -Wstrict-prototypes \
	-fomit-frame-pointer -I$(INCLUDEDIR)

CC = gcc

MODULES = ov51x.o ov511_decomp.o ov518_decomp.o

INSTALL_PATH_2.2   = /lib/modules/`uname -r`/usb/
INSTALL_PATH_2.4   = /lib/modules/`uname -r`/kernel/drivers/usb/
INSTALL_PATH_2.4RH = /lib/modules/`uname -r`/kernel/drivers/usb/ov511/
INSTALL_PATH_2.5   = /lib/modules/`uname -r`/kernel/drivers/usb/media/

#################################### TARGETS ##################################

# Make with standard options for cameras and video capture. No tuner support.
all: $(MODULES)

install:
	@echo 'You must specify an appropriate install command for your kernel:'
	@echo '   make install-2.2'
	@echo '   make install-2.4'
	@echo '   make install-2.4rh  (for RedHat kernels 2.4.9-31 thru 2.4.18)'
	@echo '   make install-2.5'

# Install on a 2.2 system
install-2.2: all
	$(MAKE) _do_install _INSTALL_PATH_="$(INSTALL_PATH_2.2)"

# Install on a 2.4 system
install-2.4: all
	$(MAKE) _do_install _INSTALL_PATH_="$(INSTALL_PATH_2.4)"

# Install on a RedHat 2.4.9-31 - 2.4.18 system
install-2.4rh: all
	$(MAKE) _do_install _INSTALL_PATH_="$(INSTALL_PATH_2.4RH)"

# Install on a 2.5 system
install-2.5: all
	$(MAKE) _do_install _INSTALL_PATH_="$(INSTALL_PATH_2.5)"

clean:
	rm -f *.o *~ core *.i

#################################### RULES ####################################

_do_install:
	install $(MODULES) $(_INSTALL_PATH_)
	/sbin/depmod -ae

ov51x.o: ov51x.c ov51x.h
	$(CC) -c $(CFLAGS) -DEXPORT_SYMTAB ov51x.c

ov511_decomp.o: ov511_decomp.c ov51x.h
	$(CC) -c $(CFLAGS) ov511_decomp.c

ov518_decomp.o: ov518_decomp.c ov51x.h
	$(CC) -c $(CFLAGS) ov518_decomp.c

endif  # End kernel version test
# -------------------------- 2.6 KERNEL SUPPORT -------------------------------
ifeq ($(OVCAM_MAJMIN),2.6)

ifneq ($(KERNELRELEASE),)
#
# Make rules for use from within 2.6 kbuild system
#
obj-m	+= ov51x.o ov511_decomp.o ov518_decomp.o

else  # We were called from command line

KDIR	:= /lib/modules/$(shell uname -r)/build
PWD	:= $(shell pwd)
all:
	$(MAKE) -C $(KDIR) M=$(PWD) modules

install: all
	$(MAKE) -C $(KDIR) M=$(PWD) modules_install

clean:
	$(MAKE) -C $(KDIR) M=$(PWD) clean
endif

endif  # End kernel version test
```

---

