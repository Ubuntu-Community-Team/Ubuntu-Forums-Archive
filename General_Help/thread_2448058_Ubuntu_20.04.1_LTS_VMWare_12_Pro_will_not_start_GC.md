---
title: "Ubuntu 20.04.1 LTS VMWare 12 Pro will not start GCC not found"
date: 2020-07-31
forum: General Help
---

### Post by joyce-nord on 2020-07-31
The error I receive is from the VMWare Kernal Module UPdater.  The error:

 Before you can run VMware, several modules must be compiled and loaded into the running kernel. 

GCC

GNU C Compiler (gcc) version 9.3.0 was not found. If you installed it in a non-default path you can specify the path below. Otherwise refer to your distrubution's documentation for installation instructors and click Refresh to search again in default locations.

gcc --version returns

gcc (Ubuntu 9.3.0-10ubuntu2) 9.3.0
Copywright (C) 2019 Free Software Foundations, Inc. This is free software; see the source for copying conditions. There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

whereis gcc returns

gcc: /usr/bin/gcc /usr/lib/gcc /usr/share/man/man1/gcc.1.gz

When I attempt to point the VMWare Kernal Module Updater to the location /usr/bin/gcc or /usr/lib/gcc, still doesn't find it.

I have gcc, gcc-7, gcc-9, gcc-ar, gcc-ar-7, gcc-ar-9, gcc-nm, gcc-nm-7, gcc-nm-9 gcc-ranlib, gcc-ranlib-7, gcc-ranlib-9 all of which have lrwxrwxrwx permissions (so they're executable). the gc and gcore folder are -rwxr-xr-x 

How can I fix this?

---

### Post by joyce-nord on 2020-07-31
So I was able to solve my own problem after hours and hours and hours.  GCC compiler, although installed, is not compatible somehow with the kernel is what I gather.  So, vmmon and vmnet need to be recompiled based upon the kernel, but in order to do that, you need modified host modules found [https://github.com/mkubecek/vmware-host-modules/branches](https://github.com/mkubecek/vmware-host-modules/branches) which work.  The one you choose from that page will depend upon whether your are trying to get player or workstation running, and/or hwat version of player.  

At any rate, the basic steps are to download the appropriate vmware host modules into the /usr/lib/vmware/modules/source directory which requires you to access this directory as sudo. (wget or simply c/p as sudo) 

$sudo cd /usr/lib/vmware/modules/source

wget [https://github.com/mkubecek/vmware-host-modules/archive/nameversionoffile](https://github.com/mkubecek/vmware-host-modules/archive/nameversionoffile)
Extract downloaded file within that directory.

#unzip nameofdownloadedfile

switch over to the new vmmon-only directoy, run make

#cd nameofdownloadedfile/vmmon-only/

#make

#cd ../vmnet-only/

#make

#cd .. (to go back one directory)

create a directory within /lib/modules/, called misc

#mkdir /lib/modules/`uname -r`/misc (also requires sudo)

copy vmmon.o and vmnet.o to /misc

#cp vmmon.o /lib/modules/`uname -r`/misc/vmmon.ko

#cp vmnet.o /lib/modules/`uname -r`/misc/vmnet.ko


then recreate module dependencies using depmod -a

#depmod -a

restart vmware

#/etc/init.d/vmware restart

---

### Post by monkeybrain20122 on 2020-08-02
You can install different gcc and set up update alternatives to switch between them. so when you compile your modules switch to the gcc version you need (set it as the default  gcc) and when finish switch back. Have been using multiple gccs to compile different stuffs for a while

for example, if you want to set up option to use gcc-10.1.0 installed in $HOME/opt/gcc-10.1.0

```

sudo update-alternatives --install /usr/bin/gcc gcc /home/yourusername/opt/gcc-10.1.0/bin/gcc 40 --slave /usr/bin/g++ g++ /home/yourusername/opt/gcc-10.1.0/bin/g++ --slave /usr/bin/gfortran gfortran /home/yourusername/opt/gcc-10.1.0
/bin/gfortran
```

Then use this command to choose your default gcc

```
sudo update-alternatives --config gcc
```
 
See this [link]("http://charette.no-ip.com:81/programming/2011-12-24_GCCv47/") for more details and explanations.

---

