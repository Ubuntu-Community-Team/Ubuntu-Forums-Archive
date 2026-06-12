---
title: "After upgrade to  to 3.13.0-35-generic  Kernel rts5138 module no longer works"
date: 2014-09-14
forum: General Help
---

### Post by pouldney on 2014-09-14
I have an Aspire-XC-605 desktop with a ID 0bda:0129 Realtek Semiconductor Corporation 
    SD card reader.
             I was using rts5139 module which worked.However after upgrade to 3.13.0-35-generic  Kernel
     in ubuntu 12.04  it no longer works I am not able to compile the module
           Here is the result of make command

$ make
sed "s/RTSX_MK_TIME/`date +%y.%m.%d.%H.%M`/" timestamp.in > timestamp.h
cp -f define.release define.h
make -C /lib/modules/3.13.0-35-generic/build/ SUBDIRS=/home/george/Temp/rts5139-old modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-35-generic'
  CC [M]  /home/george/Temp/rts5139-old/rts51x_transport.o
  CC [M]  /home/george/Temp/rts5139-old/rts51x_common.o
  CC [M]  /home/george/Temp/rts5139-old/rts51x_scsi.o
  CC [M]  /home/george/Temp/rts5139-old/rts51x_fop.o
  CC [M]  /home/george/Temp/rts5139-old/rts51x.o
/home/george/Temp/rts5139-old/rts51x.c:88:2: error: unknown field ‘proc_info’ specified in initializer
/home/george/Temp/rts5139-old/rts51x.c:88:2: warning: initialization from incompatible pointer type [enabled by default]
/home/george/Temp/rts5139-old/rts51x.c:88:2: warning: (near initialization for ‘rts51x_host_template.proc_dir’) [enabled by default]
make[2]: *** [/home/george/Temp/rts5139-old/rts51x.o] Error 1
make[1]: *** [_module_/home/george/Temp/rts5139-old] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-35-generic'
make: *** [default] Error 2

   Any ideas on why it would compile on previous kernels bot not on 3.13.0-35   ?

---

### Post by pouldney on 2014-09-25
After upgrade to 3.13.0-36-generic
   It now works

---

