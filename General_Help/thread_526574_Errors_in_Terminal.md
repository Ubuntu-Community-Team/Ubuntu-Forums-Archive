---
title: "Errors in Terminal"
date: 2007-08-15
forum: General Help
---

### Post by ModularMike on 2007-08-15
I am trying to get my WUSB54GSC Linksys wireless adapter to work and I found step by step instructions in the WiFi Docs of the Ubuntu community. I came across these errors while doing step 5 "Make driver with the make command"

```
make
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/mike/RT73_Linux_STA_Drv1.0.3.6/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/mike/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o
/home/mike/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:65:42: error: invalid suffix "c0026" on integer constant
/home/mike/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:163: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘->’ token
/home/mike/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:213:2: error: #endif without #if
/home/mike/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c: In function ‘usb_rtusb_probe’:
/home/mike/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2088: warning: unused variable ‘device’
make[2]: *** [/home/mike/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/mike/RT73_Linux_STA_Drv1.0.3.6/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [all] Error 2

```

Can anyone help me out? I'm new to linux and just trying to get my wireless adapter to work.

---

### Post by ModularMike on 2007-08-15
The only time I went into the rtmp_main.c file was to edit something to try to fix the error but I was still getting the same errors before I edited the file.

---

### Post by kikin568 on 2007-12-01
Every time I try to install app by terminal comands this is the result, if I try with Synaptic, the same hapen:

kikin@kikin-pc:~$ sudo apt-get install ktorrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libgmp3c2
Suggested packages:
  php5-cli
The following NEW packages will be installed:
  ktorrent libgmp3c2
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 3200kB of archives.
After unpacking 10.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) gutsy/main libgmp3c2 2:4.2.1+dfsg-5ubuntu4
  Could not connect to cr.archive.ubuntu.com:80 (163.178.101.17). - connect (111 Connection refused)
Err [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) gutsy/main ktorrent 2.2.1-0ubuntu3
  Could not connect to cr.archive.ubuntu.com:80 (163.178.101.17). - connect (111 Connection refused)
Failed to fetch [http://cr.archive.ubuntu.com/ubuntu/pool/main/g/gmp/libgmp3c2_4.2.1+dfsg-5ubuntu4_i386.deb](http://cr.archive.ubuntu.com/ubuntu/pool/main/g/gmp/libgmp3c2_4.2.1+dfsg-5ubuntu4_i386.deb)  Could not connect to cr.archive.ubuntu.com:80 (163.178.101.17). - connect (111 Connection refused)
Failed to fetch [http://cr.archive.ubuntu.com/ubuntu/pool/main/k/ktorrent/ktorrent_2.2.1-0ubuntu3_i386.deb](http://cr.archive.ubuntu.com/ubuntu/pool/main/k/ktorrent/ktorrent_2.2.1-0ubuntu3_i386.deb)  Could not connect to cr.archive.ubuntu.com:80 (163.178.101.17). - connect (111 Connection refused)

What can I do, 
Please help.
Thanks.

---

