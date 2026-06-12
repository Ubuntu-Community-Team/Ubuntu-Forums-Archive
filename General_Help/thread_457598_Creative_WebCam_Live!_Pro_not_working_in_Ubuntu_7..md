---
title: "Creative WebCam Live! Pro not working in Ubuntu 7.04."
date: 2007-05-28
forum: General Help
---

### Post by Programmerfromthehood on 2007-05-28
[LEFT]Hi, I just got Ubuntu Feisty Fawn about three days ago, and it's great.But I haven't got my webcam to work with Ubuntu, I know I need a driver, and I **think** I know how to install one. It's a good thing I partioned my HD to have Ubuntu and Windows on it.
The model is "WebCam Live! Pro"
And it's a usb cam. 
Thanks in advance!![/LEFT]

---

### Post by Happy_Man on 2007-05-28
Actually, I think Kopete IM would work with that. Actually, I know it works; I have the same model. :razz: Haven't found anything else that will, and 'tis a lot easier than mucking w/ drivers. *shudders*

```
sudo apt-get install kopete
```

---

### Post by Programmerfromthehood on 2007-05-28
> **Happy_Man said:**
> Actually, I think Kopete IM would work with that. Actually, I know it works; I have the same model. :razz: Haven't found anything else that will, and 'tis a lot easier than mucking w/ drivers. *shudders*

```
sudo apt-get install kopete
```Nope, installed it and still not working.:(

---

### Post by Programmerfromthehood on 2007-05-29
I also did this:
```

sudo apt-get install gcc
wget http://mxhaard.free.fr/spca50x/Download/oldrelease/spcaview-20050701.tar.gz
tar -xzf sp*.gz
rm sp*.gz
cd sp*
make
sudo make install
sudo modprobe videodev
sudo modprobe spca5xx
sudo apt-get install camorama
camorama &
cd
sudo rm -R spca*

```
Installed and everything, but still didn't work. Just got this:
```

james@Saito:~$ wget http://mxhaard.free.fr/spca50x/Download/oldrelease/spcaview-20050701.tar.gz
--03:10:20--  http://mxhaard.free.fr/spca50x/Download/oldrelease/spcaview-20050701.tar.gz
           => `spcaview-20050701.tar.gz'
Resolving mxhaard.free.fr... 212.27.63.150
Connecting to mxhaard.free.fr|212.27.63.150|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 90,967 (89K) [application/x-gzip]

100%[====================================>] 90,967       111.48K/s             

03:10:21 (111.29 KB/s) - `spcaview-20050701.tar.gz' saved [90967/90967]

james@Saito:~$ tar -xzf sp*.gz
james@Saito:~$ rm sp*.gz
james@Saito:~$ cd sp*
james@Saito:~/spca5xx-v4l1goodbye$ make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/james/spca5xx-v4l1goodbye CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.o
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:39:26: error: linux/config.h: No such file or directory
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca50x_init_isoc’:
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:1623: warning: assignment from incompatible pointer type
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_open’:
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2394: warning: implicit declaration of function ‘video_devdata’
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2394: warning: initialization makes pointer from integer without a cast
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2399: warning: implicit declaration of function ‘video_get_drvdata’
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2399: warning: initialization makes pointer from integer without a cast
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_close’:
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2489: warning: initialization makes pointer from integer without a cast
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_do_ioctl’:
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2549: warning: initialization makes pointer from integer without a cast
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_ioctl’:
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3093: warning: implicit declaration of function ‘video_usercopy’
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_read’:
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3112: warning: initialization makes pointer from integer without a cast
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_mmap’:
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3211: warning: initialization makes pointer from integer without a cast
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: At top level:
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3263: error: variable ‘spca50x_template’ has initializer but incomplete type
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3264: error: unknown field ‘owner’ specified in initializer
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3264: warning: excess elements in struct initializer
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3264: warning: (near initialization for ‘spca50x_template’)
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: error: unknown field ‘name’ specified in initializer
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: warning: excess elements in struct initializer
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: warning: (near initialization for ‘spca50x_template’)
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: error: unknown field ‘type’ specified in initializer
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: warning: excess elements in struct initializer
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: warning: (near initialization for ‘spca50x_template’)
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: error: unknown field ‘hardware’ specified in initializer
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: warning: excess elements in struct initializer
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: warning: (near initialization for ‘spca50x_template’)
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: error: unknown field ‘fops’ specified in initializer
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: warning: excess elements in struct initializer
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: warning: (near initialization for ‘spca50x_template’)
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: error: unknown field ‘release’ specified in initializer
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: error: ‘video_device_release’ undeclared here (not in a function)
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: warning: excess elements in struct initializer
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: warning: (near initialization for ‘spca50x_template’)
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3272: error: unknown field ‘minor’ specified in initializer
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3272: warning: excess elements in struct initializer
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3272: warning: (near initialization for ‘spca50x_template’)
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘cd_to_spca50x’:
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3340: warning: implicit declaration of function ‘to_video_device’
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3340: warning: initialization makes pointer from integer without a cast
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3341: warning: return makes pointer from integer without a cast
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca50x_create_sysfs’:
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3450: warning: implicit declaration of function ‘video_device_create_file’
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_probe’:
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5509: warning: implicit declaration of function ‘video_device_alloc’
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5509: warning: assignment makes pointer from integer without a cast
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5512: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5512: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5512: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5514: error: dereferencing pointer to incomplete type
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5516: warning: implicit declaration of function ‘video_set_drvdata’
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: warning: implicit declaration of function ‘video_register_device’
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: error: ‘VFL_TYPE_GRABBER’ undeclared (first use in this function)
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: error: (Each undeclared identifier is reported only once
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: error: for each function it appears in.)
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5550: error: dereferencing pointer to incomplete type
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5551: warning: implicit declaration of function ‘video_device_release’
/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5553: warning: implicit declaration of function ‘video_unregister_device’
make[2]: *** [/home/james/spca5xx-v4l1goodbye/drivers/usb/spca5xx.o] Error 1
make[1]: *** [_module_/home/james/spca5xx-v4l1goodbye] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [default] Error 2
james@Saito:~/spca5xx-v4l1goodbye$ sudo make install
make: `install' is up to date.
james@Saito:~/spca5xx-v4l1goodbye$ sudo modprobe videodev
james@Saito:~/spca5xx-v4l1goodbye$ sudo modprobe spca5xx
FATAL: Module spca5xx not found.

```
So, can I try anythig else?

---

### Post by helgi on 2007-06-02
I have the same camera/problem. I've been trying to install this spca5xx driver without success just like you.
It would be grate if somebody could help. Thanx.

---

### Post by Zowie on 2007-06-05
Hi. I had a similar problem and had to change the include line in the spca5xx.c file. 
Where it says "#include <linux/config.h>" change it to "#include <linux/configfs.h>"

Now it compiles in Feisty.

Hope it helps

---

### Post by dimas869 on 2007-07-13
there is a driver that works for this webcam which is ov51x
check here for details [http://www.rastageeks.org/ov51x-jpeg...gHackedInstall](http://www.rastageeks.org/ov51x-jpeg...gHackedInstall) 
cheers:)

---

### Post by yorkie on 2007-07-13
Hi
Have a look at this thread
[https://help.ubuntu.com/community/Spca5xx](https://help.ubuntu.com/community/Spca5xx)
Hope it helps

---

### Post by subaruwrx on 2007-07-22
So has anybody got it to work yet?

Did you use the spca5 or ov51x driver?

---

### Post by dimas869 on 2007-07-22
> **subaruwrx said:**
> So has anybody got it to work yet?

Did you use the spca5 or ov51x driver?

hello subaruwrx,
this camera is working for me but with ov51x driver
works good on aMSN (substitute of microsoft messenger), Xwatv and Ekiga.
good luck!

---

### Post by subaruwrx on 2007-07-22
> **dimas869 said:**
> hello subaruwrx,
this camera is working for me but with ov51x driver
works good on aMSN (substitute of microsoft messenger), Xwatv and Ekiga.
good luck!

Hi,

I read through the web site but got a bit confused with the drivers and installations. 

Ok I have a clean installed Ubuntu now. I just need to download the source driver ([http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.2.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.2.tar.gz)), compile and install it? 

Whats with the debian module package, videodev etc? Do I need to perform those steps?

Thanks.

---

### Post by vixmusic01 on 2008-03-13
Hi all,

I bought a Creative Live! cam because I read that Creative cams were working

[http://alpha.dyndns.org/ov511/cameras.html](http://alpha.dyndns.org/ov511/cameras.html)

Are there any cameras that work reliably?

I tried camorama, but it "could not connect to the video device (/dev/video0) check connection"

Any help?

Victoria

---

