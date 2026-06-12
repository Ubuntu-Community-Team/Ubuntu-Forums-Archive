---
title: "Xilinx ISE 14.7 on Ubuntu 15.10"
date: 2016-01-14
forum: General Help
---

### Post by eric108 on 2016-01-14
Hello everyone,

Im having a problem with Xilinx ISE specifically iMPACT. The ISE interface appears to work correctly and I can build a bit file however when I try to setup a cable using impact it instantly crashes and in terminal I get the error:

Release 14.7 - iMPACT P.20131013 (lin64)
Copyright (c) 1995-2013 Xilinx, Inc.  All rights reserved.
INFO:iMPACT - Initial Project Directory: '/home/eric/Downloads/'
INFO:iMPACT - Initial Current Working Directory:
   '/opt/Xilinx/14.7/ISE_DS/ISE/bin/lin64'
INFO:iMPACT - Selected Project Directory: '/home/eric/Downloads/'
INFO:iMPACT - Selected Current Working Directory:
   '/opt/Xilinx/14.7/ISE_DS/ISE/bin/lin64'
_impact4: pthread_mutex_unlock.c:87: __pthread_mutex_unlock_usercnt: Assertion `type == PTHREAD_MUTEX_ERRORCHECK_NP' failed.

Out of curiosity I decided to find out what libraries are required for their impact program using ldd:

 eric@Serval-WS:/opt/Xilinx/14.7/ISE_DS/ISE/bin/lin64$ ldd impact
    linux-vdso.so.1 =>  (0x00007ffd35f97000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f2051896000)
    **libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0** (0x00007f2051678000)
    libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f20512f5000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f2050fed000)
    libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f2050dd6000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f2050a0b000)
    /lib64/ld-linux-x86-64.so.2 (0x000055da1b955000)

I would suspect there is something different with the highlighted library in this version of Ubuntu because the Xilinx tools work properly on my 32-bit installation:

Xilinx ISE 14.7 -- 32 BIT
iMPACT          --  32 BIT
Ubuntu 14.04LTS -- 32 BIT

if anybody has any ideas how to get this working on my 64-BIT ubuntu installation I would greatly appreciate it as I have spent hours trying to find a solution (but most google results are far outdated circa 2011)

---

### Post by eric108 on 2016-01-15
simple half way solution.... run a windows 7 virtual machine... run windows version of Xilinx ISE... devices and JTAG magically work

---

### Post by soulcmdc on 2016-01-15
I seem to be having a similar problem with the Vivado tools on Ubuntu 15.10 as well.
This also shows up in the Digilent utilities, for example:

# dadutil enum
dadutil: pthread_mutex_unlock.c:87: __pthread_mutex_unlock_usercnt: Assertion `type == PTHREAD_MUTEX_ERRORCHECK_NP' failed.
[1]    6268 abort (core dumped)  dadutil enum

I'm pretty stumped on this one - this is running on a Thinkpad T450, and I have a Macbook also running Ubuntu 15.10 that seems to work fine without this error. Libraries loaded appear to be the same.

---

### Post by eric108 on 2016-01-18
It looks like your error is slightly different than mine... If your T450 is running an intel broadwell chip look at this link:

[https://bugs.launchpad.net/ubuntu/+source/intel-microcode/+bug/1509764](https://bugs.launchpad.net/ubuntu/+source/intel-microcode/+bug/1509764)

My machine is running a skylake architecture so unfortunately the above fix does not work for me..

---

