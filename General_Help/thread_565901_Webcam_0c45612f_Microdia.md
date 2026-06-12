---
title: "Webcam 0c45:612f Microdia"
date: 2007-10-02
forum: General Help
---

### Post by danieldocki on 2007-10-02
I'am use Ubuntu 7.04

> 
daniel@casa:~$ lsusb
Bus 005 Device 001: ID 0000:0000 
Bus 002 Device 003: ID 0c45:612f Microdia
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 001: ID 0000:0000 
Bus 003 Device 001: ID 0000:0000 
Bus 004 Device 001: ID 0000:0000 
daniel@casa:~$



I'am edit spca5xx.c and add

Line 789: {USB_DEVICE(0x0c45, 0x612f)}, /* Microdia.*/
Line 5124: case 0x612f:

All de fine, here?
I Can't make and make install

    > root@casa:/home/daniel/Desktop/spca5xx-v4l1goodbye# sudo su
    root@casa :/home/daniel/Desktop/spca5xx-v4l1goodbye# make
       Building SPCA5XX driver for 2.5/2.6 kernel.
       Remember: you must have read/write access to your kernel source tree.
    make -C /lib/modules/`uname -r`/build SUBDIRS=/home/daniel/Desktop/spca5xx-v4l1goodbye CC=cc modules
    make[1]: Entrando no diretório `/usr/src/linux-headers-2.6.20-16-generic'
      CC [M]  /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.o
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:39:26: error: linux/config.h: Arquivo ou diretório inexistente
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function 'spca50x_init_isoc':
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:1624: warning: assignment from incompatible pointer type
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function 'spca5xx_open':
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2395: warning: implicit declaration of function 'video_devdata'
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2395: warning: initialization makes pointer from integer without a cast
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2400: warning: implicit declaration of function 'video_get_drvdata'
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2400: warning: initialization makes pointer from integer without a cast
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function 'spca5xx_close':
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2490: warning: initialization makes pointer from integer without a cast
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function 'spca5xx_do_ioctl':
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2550: warning: initialization makes pointer from integer without a cast
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function 'spca5xx_ioctl':
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3094: warning: implicit declaration of function 'video_usercopy'
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function 'spca5xx_read':
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3113: warning: initialization makes pointer from integer without a cast
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function 'spca5xx_mmap':
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3212: warning: initialization makes pointer from integer without a cast
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: At top level:
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3264: error: variable 'spca50x_template' has initializer but incomplete type
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: error: unknown field 'owner' specified in initializer
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: warning: excess elements in struct initializer
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: warning: (near initialization for 'spca50x_template')
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: error: unknown field 'name' specified in initializer
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: warning: excess elements in struct initializer
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: warning: (near initialization for 'spca50x_template')
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: error: unknown field 'type' specified in initializer
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: warning: excess elements in struct initializer
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: warning: (near initialization for 'spca50x_template')
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: error: unknown field 'hardware' specified in initializer
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: warning: excess elements in struct initializer
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: warning: (near initialization for 'spca50x_template')
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3269: error: unknown field 'fops' specified in initializer
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3269: warning: excess elements in struct initializer
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3269: warning: (near initialization for 'spca50x_template')
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3271: error: unknown field 'release' specified in initializer
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3271: error: 'video_device_release' undeclared here (not in a function)
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3271: warning: excess elements in struct initializer
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3271: warning: (near initialization for 'spca50x_template')
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3273: error: unknown field 'minor' specified in initializer
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3273: warning: excess elements in struct initializer
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3273: warning: (near initialization for 'spca50x_template')
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function 'cd_to_spca50x':
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3341: warning: implicit declaration of function 'to_video_device'
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3341: warning: initialization makes pointer from integer without a cast
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3342: warning: return makes pointer from integer without a cast
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function 'spca50x_create_sysfs':
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3451: warning: implicit declaration of function 'video_device_create_file'
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function 'spca5xx_probe':
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5511: warning: implicit declaration of function 'video_device_alloc'
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5511: warning: assignment makes pointer from integer without a cast
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5514: error: invalid application of 'sizeof' to incomplete type 'struct video_device'
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5514: error: invalid application of 'sizeof' to incomplete type 'struct video_device'
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5514: error: invalid application of 'sizeof' to incomplete type 'struct video_device'
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5516: error: dereferencing pointer to incomplete type
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5518: warning: implicit declaration of function 'video_set_drvdata'
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5523: warning: implicit declaration of function 'video_register_device'
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5523: error: 'VFL_TYPE_GRABBER' undeclared (first use in this function)
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5523: error: (Each undeclared identifier is reported only once
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5523: error: for each function it appears in.)
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5552: error: dereferencing pointer to incomplete type
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5553: warning: implicit declaration of function 'video_device_release'
    /home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5555: warning: implicit declaration of function 'video_unregister_device'
    make[2]: ** [/home/daniel/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.o] Erro 1
    make[1]: ** [_module_/home/daniel/Desktop/spca5xx-v4l1goodbye] Erro 2
    make[1]: Saindo do diretório `/usr/src/linux- headers-2.6.20-16-generic'
    make: ** [default] Erro 2
    root@casa:/home/daniel/Desktop/spca5xx-v4l1goodbye# 

---

### Post by xarroyo on 2007-10-02
Read this Thread... maybe it helps!

[http://ubuntuforums.org/showthread.php?t=530727](http://ubuntuforums.org/showthread.php?t=530727)

---

### Post by waldeck on 2008-05-08
> **xarroyo said:**
> Read this Thread... maybe it helps!

[http://ubuntuforums.org/showthread.php?t=530727](http://ubuntuforums.org/showthread.php?t=530727)

Unfortunately it does not. It seems that this camera is presently unsupported on linux. For one thing, the gspca (formerly spca5xx) driver *does not* support it. That camera is built around the SN110 and ICM105 chipset and the gspca driver knows both, though. Perhaps it will be a very small step to making it work. I have contacted the developer a long time ago but got no answer.

Waldeck

Edit: simply editing the gspca driver as suggested above *will not* help because it still does not know what to do with that information. It seems that some tables and a bit more code is required. I might have the knowledge to put it together, but unfortunately lack the time. :(

---

