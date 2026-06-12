---
title: "command-line question (number of bits)"
date: 2016-04-11
forum: General Help
---

### Post by wog on 2016-04-11
From the command line, is there a command for finding out how many bits my system uses? Is it a 32-bit machine / OS or is it a 64-bit machine / OS?

Thanks in advance!
Jamz

---

### Post by papibe on 2016-04-11
Hi wog.

To know what your current system is running:
```
uname -i
```
To find out what your hardware supports:
```
lscpu
```
Hope it helps. Let us know if that answer your question.
Regards.

---

### Post by wog on 2016-04-11
~$ uname -i
i686

Okay, Im not sure what this tells me. 

~$ lscpu
Architecture:          i686
CPU op-mode(s):        32-bit
Byte Order:            Little Endian
CPU(s):                1
On-line CPU(s) list:   0
Thread(s) per core:    1
Core(s) per socket:    1
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 13
Model name:            Intel(R) Pentium(R) M processor 1.70GHz
Stepping:              8
CPU MHz:               600.000
CPU max MHz:           1700.0000
CPU min MHz:           600.0000
BogoMIPS:              1196.94

Okay, does this mean the machine is 32-bit, or does it mean that the OS is 32-bit?
I know 32-bit was the standard type of Linux a few years ago, but I think the standard is now 64-bit. Im just trying to figure out if the machine is actually 64-bit, but the 32-bit version of Linux was what was installed... or maybe Im just being hopeful. :)

I *think* it means the machine has just a single core. Is that right?

Im starting to understand why this laptop bogs down from time to time.

---

### Post by QIII on 2016-04-11
You are running a 32 bit OS on a 32 bit CPU.

i686 is 32 bit architecture, but it had an "improved/updated" Intel instruction set that had to be specifically programmed to to get any benefit.  However, it would run a run-of-the-mill 32 bit operating system -- like your current Ubuntu.

Yes, it is a single core CPU, capable of only one thread and it does not run at a particularly high frequency.

---

### Post by wog on 2016-04-12
Thank you for nurse-maiding me through that. I very much appreciate it.

---

