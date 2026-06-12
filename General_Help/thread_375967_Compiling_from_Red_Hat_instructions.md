---
title: "Compiling from Red Hat instructions"
date: 2007-03-04
forum: General Help
---

### Post by Redeyes_Gambit on 2007-03-04
}{i,

I have a driver module I'm trying to compile for a RAID card, and though it comes with instructions, they're all in red-hat-ees. I have tried numerous things and really could use a little old-fashioned Ubuntu community help here.

The instructions read something like this:

                      Promise SATAII-150/300 Series Linux Driver
              ----------------------------------------------------

Support List
============

The following Promise SATAII150/300 series adapters and Linux operating systems are
compatible with the drivers in this release:

Chipset		Adapter Name
--------	------------
PDC40518	Promise SATAII150 TX4
PDC20575	Promise SATAII150 TX2plus
PDC20579	Promise SATAII150 579
PDC40718	Promise SATA300 TX4
PDC20775	Promise SATA300 TX2plus
PDC20779	Promise SATA300 779

OS		kernel version
--		--------------
Red Hat EL4 AS	kernel 2.6.9-5
SuSE Pro 9.2	kernel 2.6.8-24
N/A		kernel 2.6.x	(kernel compiled by yourself)


File List
=========

File Name	Description
---------	-----------
pdc-ulsata2.c	Promise SATAII150/300 Series Linux Driver 
pdc-ulsata2.h	header file of pdc-ulsata2.c
Makefile	Makefile of linux driver
README		this README
cam/		directory of Common Access Module (CAM). 
		needed by pdc-ulsata2.c


Prerequisties
=============

A develop environment is required to compile SATAII150/300 Linux driver. The easiest
way is to choose develop toolkit when installing linux. 

1. kernel source code
   (PS: Please make sure you have linux kernel source code at ("/usr/src/linux").
   	For Linux Kernel 2.6 like FedoraCore, it may be installed by rpm command with packaged source.
        And we recommend the user to refer the Linux's USERGUIDE that you have, 
        if you have any questions about kernel source code.)
   ex: Under the OS of Fedora Core 3
       #rpm -i kernel-2.6.9-1.667.src.rpm
       #rpmbuild -bp --target=i686 /usr/src/redhat/SPECS/kernel-2.6.9.spec
       #mv /usr/src/redhat/BUILD/kernel-2.6.9/linux-2.6.9 /usr/src
       #rpmbuild --rmsource --rmspec /usr/src/redhat/SPECS/kernel-2.6.9.spec
       #cd /usr/src
       #ln -s linux-2.6.9 linux	 
       #cd linux  
       #make mrproper
       #cp configs/kernel-2.6.9-i686.config .config
       #vi Makefile(Modify EXTRAVERSION=-prep to =-1.667)
       #make menuconfig
       #make
2. gcc compiler


Building and Installation
=========================
You can easily build/install driver according to the following steps:

Step 1. Set the proper ulsata2 binary 

	make clean

Step 2. Build driver binary file.

	make DRIVER_SRC_DIR=`pwd`

Step 3. Install the driver module.

     #cp -f ulsata2.ko 
        /lib/modules/<kernel_version>/kernel/drivers/scsi/ulsata2.ko

Step 4. Remove the module of sata_promise.ko(if it is necessary)

     #rmmod sata_promise.ko	

Step 5. Load the driver module.

     #insmod ulsata2.ko
     
PS: Makefile script can receive parameters from command line, so if you want to build drive according to specific settings, such as build driver automaticly. 
    Please refer to Makefile script itself or contact to the author.

Anyway, like I said, it's all in hat-ees. I'm trying to compile this module on an Ubuntu 6.06 LTS server, so I won't have access to any graphical tools. Any help would be appreciated.

---

### Post by PriceChild on 2007-03-04
Well the instructions should be basically the same...

You will want to```
sudo apt-get install build-essential linux-headers
```first to get the tools required.

---

### Post by Redeyes_Gambit on 2007-03-04
K-o, did that already. What I don't understand is the whole rpmbuild part.

---

### Post by PriceChild on 2007-03-04
> **Redeyes_Gambit said:**
> K-o, did that already. What I don't understand is the whole rpmbuild part.Use my command above to grab the headers and you "shouldn't" need to do any of that section.

---

### Post by Redeyes_Gambit on 2007-03-04
Really??! Well that's too easy :P . Back in a flash, gotta try out the rest of the instructions...

---

### Post by Redeyes_Gambit on 2007-03-04
Should I symlink to the linux headers?

---

### Post by PriceChild on 2007-03-04
It "should" already be done.. I'm not sure. If it needs it then do it :)

---

### Post by Redeyes_Gambit on 2007-03-04
Alright, well I have a whole slew of scrolling errors when I try "make DRIVER_SRC_DIR=`pwd`"

Most of it looks like:

error: field name not in record or union initializer
warning: excess elements in scalar initializer
warning: data definition has no type or storage class
error:/usr/src/linux/drivers/scsi/scsi_module.c: no such files or directory
Make[2]: *** [/home/ubuntu/ut_mod/pdc-ulsata2.o] error 1
make[1]: *** [_module_/home/ubuntu/ut_mod/] error 2
make[1]: Leaving directory '/usr/src/linux-headers-2.6.15-26-server'
Make: *** [default] Error 2

Lol, it seems as though I have no idea what I'm doing ;)

---

### Post by Redeyes_Gambit on 2007-03-04
Anybody know what I'm doing wrong?

---

### Post by Redeyes_Gambit on 2007-03-05
Anybody?

---

### Post by NeoTaoistTechnoPagan on 2007-07-16
I'm having the same issue here.

Working on it tonight and will post what I get done.

---

