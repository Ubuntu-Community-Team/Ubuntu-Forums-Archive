---
title: "[SOLVED] cant install package. PLEASE HELP DONT LOOK AWAY"
date: 2008-06-25
forum: General Help
---

### Post by elidoperezmd on 2008-06-25
i know... sounds stupid but i just cant install apackage, its a driver for the web cam.

name: gspcav1-20071224.tar.gz

and this is what i have done so far:

1- Uncompressed gspcav1-20071224.tar.gz to the desktop, and know i have the folder gspcav1-20071224

2- in the terminal i wrote cd gspcav1-20071224, and im in the folder

3- i wrote ./configure and what i get is this:
bash: ./configure: No such file or directory

4- i wrote make and this is what i get:
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/elido/Desktop/gspcav1-20071224 CC=cc modules
make: *** /lib/modules/2.6.24-16-rt/build: No such file or directory.  Stop.
make: *** [default] Error 2

5- i wrote sudo make install and i get:
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1

6- i wrote et
sudo check install and i gsudo: checkinstall: command not found




What am i doing wrong? thanks for all the help here

---

### Post by spiderbatdad on 2008-06-25
Is there a readme or install file in the folder to tell you how to install it? Is there a file called installer.sh?

Not all source packages install he same way. If there are no configure or make files, those commands wont work. Sometimes you run automake...you should find some documentation with the package.

---

### Post by Habbit on 2008-06-25
In order to compile kernel modules, you need to have the sources, or at the very least the headers, for your running kernel. If you have a stock Ubuntu kernel, run ```
sudo apt-get install linux-headers-generic
``` If you run Ubuntu server, just switch "generic" for "server". Same goes for other kernels in the repositories (rt, xen, openvz...)

---

### Post by elidoperezmd on 2008-06-26
> **Habbit said:**
> In order to compile kernel modules, you need to have the sources, or at the very least the headers, for your running kernel. If you have a stock Ubuntu kernel, run ```
sudo apt-get install linux-headers-generic
``` If you run Ubuntu server, just switch "generic" for "server". Same goes for other kernels in the repositories (rt, xen, openvz...)

linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


any other ideas?

---

### Post by mempman on 2008-06-26
> **elidoperezmd said:**
> i know... sounds stupid but i just cant install apackage, its a driver for the web cam.

name: gspcav1-20071224.tar.gz

and this is what i have done so far:

1- Uncompressed gspcav1-20071224.tar.gz to the desktop, and know i have the folder gspcav1-20071224

2- in the terminal i wrote cd gspcav1-20071224, and im in the folder

3- i wrote ./configure and what i get is this:
bash: ./configure: No such file or directory

4- i wrote make and this is what i get:
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/elido/Desktop/gspcav1-20071224 CC=cc modules
make: *** /lib/modules/2.6.24-16-rt/build: No such file or directory.  Stop.
make: *** [default] Error 2

5- i wrote sudo make install and i get:
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1

6- i wrote et
sudo check install and i gsudo: checkinstall: command not found




What am i doing wrong? thanks for all the help here



Installing program via configure, make, make istall is not guaranteed to work 100% of the time.  For your case it didn't work because there isn't a "configure" file.

The correct way to go about it is to read the README or the INSTALL file, which will tell you the install instructions.

---

### Post by jimv on 2008-06-26
Just for kicks, what's the output of:

uname -r

---

### Post by mempman on 2008-06-26
> **elidoperezmd said:**
> linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


any other ideas?


```

sudo apt-get install build-essentials
sudo apt-get install linux-headers-generic

```

build essentials has all the necessary, basic header files along with make and other useful, basic tools.

---

### Post by elidoperezmd on 2008-06-26
im reading the read me file now

 FATAL you need to install the Kernel Source for your running kernel


how i install this and how to know the running version

---

### Post by Habbit on 2008-06-26
How to know the running version: `uname -r'

It's very strange that the module requires you to install the SOURCES for the running kernel: most modules should only depend on its HEADERS. You can try installing the "module-assistant" program (in the repositories) and running "module-assistant prepare", which will download all files required for building modules and set up the /usr/src/linux symlink to the running kernel source/headers tree.

If you absolutely need to download the sources for the running kernel, try installing the "linux-source" package.

---

### Post by jaypmcwilliams on 2009-10-24
> **mempman said:**
> ```

sudo apt-get install build-essentials
sudo apt-get install linux-headers-generic

```

build essentials has all the necessary, basic header files along with make and other useful, basic tools.




it's build-essential in ubuntu intrepid. :) & it still doesn't work. same results as above useing instructions " ./gspca_build , MAKE , (Which requires sudo make) , Sudo make install. STILL GET- install: cannot stat `gspca.ko': No such file or directory....

---

