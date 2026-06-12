---
title: "Attempting to compile driver module"
date: 2007-02-21
forum: General Help
---

### Post by Redeyes_Gambit on 2007-02-21
Well, as the title says, I am attempting to compile a driver module from source code. Lol, note the word "attempting" :) .

So far I have been up, down, left, right inside out, and upside down trying to get this thing to work without success. Thus I come here.

The driver I am trying to compile is for a Promise SATA300 TX2 plus (fake) RAID card. The source code is available of the promise site along with a rather sparse "guide." I'll give you the most pertinent snippet here just so you know what the goal is ;) :

Prerequisites
=============

A develop environment is required to compile SATAII150/300 Linux driver. The easiest
way is to choose develop toolkit when installing Linux. 

1. kernel source code
   (PS: Please make sure you have Linux kernel source code at ("/usr/src/linux").
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

----------------------------------------------------------------------------------------------------------------------------------

Ok, now for the information about my system. I am trying to compile this on an Ubuntu Server 6.06 distribution. The OS is on a 1 gig drive and installed without issue. I have downloaded the the kernel source code via apt-get install kernel-source if I am not mistaken. When I attempt to compile the driver by typing "make DRIVER_SRC_DIR=`pwd`"  I get the following error:

Make: *** /usr/src/linux SUBDIRS=`pwd` modules
Make: *** /usr/src/linux: No such file or directory. Stop.
Make: *** [default] error 2

Do I have to compile the kernel? Do I leave it uncompiled? Do I symlink?

Any help would be appreciated.

---

### Post by maher on 2007-02-22
Hi
Try dowloading the linux-headers package 

```

sudo apt-get install linux-headers-$(uname -r)

```


then recompile your module 
if it still doesn't compile, try to create a symbolic link:

```

cd /usr/src/
ln -s linux-headers-$(uname -r) linux

```

---

### Post by Redeyes_Gambit on 2007-02-22
Ok, I already have the headers. Trying symlink...

---

### Post by Redeyes_Gambit on 2007-02-22
Closer! I don't get the error about no Linux directory any more. However, I DO get about three dozen other errors :-P .

Of the ones I can see (would someone please tell me how to scroll up in a pure text console lol) There are errors like:

/home/ubuntu/ut_mod/pdc-ulsata.c:3302: error: feild name not in record or union initializer
/home/ubuntu/ut_mod/pdc-ulsata.c:3302: Warning: excess elements in scalar initializer.
/home/ubuntu/ut_mod/pdc-ulsata.c:3302: error: (near initialization for driver_template)
/home/ubuntu/ut_mod/pdc-ulsata.c:3302: warning: data definition has no type or storage class
/home/ubuntu/ut_mod/pdc-ulsata.c:3302: error: /usr/src/linux/drivers/scsi/scsi_module.c: No such file or directory

make[2]: *** [/home/ubuntu/ut_mod/pdc-ulsata2.o] Error 1
make[1]: *** [_module_/home/ubuntu/ut_mod] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-server'
make: *** [default] Error 2

Dependancy issue?

---

### Post by Redeyes_Gambit on 2007-02-23
Are you sure I am supposed to be compiling this against the kernel headers and not the kernel itself? I'm unfamiliar with redhat but the example given in the instructions looks like I'm supposed to compile against the kernel.

I duno, I'm still new to compiling. Help would be appreciated ;)

---

### Post by punx45 on 2007-02-23
i don't know if you can scroll back on a console, but try piping the output of make to a file, or check to see if there is an error log for make.

---

### Post by Redeyes_Gambit on 2007-02-23
Lol, 'fraid I don't know how to do either of those. Where would I probably find such a log, and/or how would I pipe the output of make to a file?

---

### Post by punx45 on 2007-02-24
my bad..   not sure where to find a log for make.   but piping is pretty easy.

basically to redirect any output from any command you do:

```
command blargh blah blah > filename
```

the '>' takes all the messages that would have been printed to the screen and puts them in the file named filename.   so if you did it with make, all the crazy scrolling text that you normally see will be written to a file rather than flashing by incomprehensibly fast.   because of this the console may appear frozen, because make still takes some time to complete, but there is no text whizzing by to show that it is working.  when it is done you will see your command prompt (user@host:~$) return.

thats one type of pipe.  there are more, but i will leave them to learn on your own as you please.

---

### Post by Redeyes_Gambit on 2007-02-24
Oooo, ok. Shweet. That'l come in handy :) . Many thanks! I just love it when you get more than the standard "do (long list of stuff) and it will work... Maybe."

Come tomorrow (or maybe the day after depending on how much homework I have to get done) I'll try and get that driver compiled with a piped output so we can see what's what.

---

