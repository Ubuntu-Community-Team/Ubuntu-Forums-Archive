---
title: "sumo-0.14.0 on ubuntu 10.10 make error undefined reference to libxercesc_3_0"
date: 2014-02-19
forum: General Help
---

### Post by dommer87 on 2014-02-19
[FONT=arial]Hi all! [/FONT][FONT=arial]i need to install sumo-0.14.0 on ubuntu10.10, i can't use newer release since i need to install iTetris platform that works only for ubuntu10.10. i have stricly followed the guidelines but still i can't install SUMO.
 
I did the following: 
[/FONT][FONT=arial][COLOR=#333333]
sudo apt-get install autoconf automake libtool[/COLOR][/FONT][COLOR=#333333][FONT=Ubuntu][FONT=arial]sudo apt-get install g++[/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=arial]download xerces-c-3.0.1.tar.gz -> unzip -> ./configure -> make -> make install[/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=arial]sudo apt-get install libgdal1-dev proj libxerces-c2-dev[/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=arial]sudo apt-get install libfox-1.6-dev libgl1-mesa-dev libglu1-mesa-dev[/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=arial]in the sumo folder i did:[/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=arial]replace LIB_GDAL="gdal" to LIB_GDAL="gdal1.6.0" in the configure.ac file[/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=arial]autoreconf --force --install[/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=arial]sudo ./configure --with-fox-libraries=/usr/lib --with-fox-includes=/usr/include/fox-1.6 --with-gdal-libraries=/usr/lib --with-gdal-includes=/usr/include/gdal --with-proj-libraries=/usr --with-xerces=/usr/local/lib -&#8211;with-xerces-includes=/usr/local/include/xercesc[/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=arial]sudo make


After doing sudo make i get the following error:[/FONT][/FONT][/COLOR]
[B][FONT=arial]SUMOSAXAttributesImpl_Xerces.cpp:(.text+0x1149): undefined reference to xercesc_3_0::XMLString::release(unsigned short, xercesc_3_0::MemoryManager*)'collect2: ld returned 1 exit status
make[3]: *** [netgen] Error 1
make[3]: Leaving directory /home/dommer/Scrivania/itetris/iTETRIS_Platform_0.2.0/sumo-0.14.0/src/netgen
[/FONT][/B][B][FONT=arial]make[2]: *** [all-recursive] Error 1make[2]: Leaving directory /home/dommer/Scrivania/itetris/iTETRIS_Platform_0.2.0/sumo-0.14.0/src
[/FONT][/B][B][FONT=arial]make[1]: *** [all] Error 2
[/FONT][/B][B][FONT=arial]make[1]: Leaving directory /home/dommer/Scrivania/itetris/iTETRIS_Platform_0.2.0/sumo-0.14.0/src
[/FONT][/B][B][FONT=arial]make: *** [all-recursive] Error 1 
[/FONT][/B][FONT=arial]
Browsing the web and the 10.10.10 Community this is a common error but i haven't found any solution or at least a solution that fits for me. It looks a problem of library bindings but i don't know how to solve. A professor who installed this software few years ago told me that he managed to install Sumo "downgrading" the compiler and other "tools" but unfortunately he doesn't remember exactly.
[/FONT][FONT=arial]
Can you tell me please which are the versions of libtool, autoconf, g++, xerces, libfox, proj and gdal and the other important tools to be installed?
 [/FONT][FONT=arial]What should i do to make the installation work?
[/FONT][FONT=arial]
Thanks very much![/FONT]

---

