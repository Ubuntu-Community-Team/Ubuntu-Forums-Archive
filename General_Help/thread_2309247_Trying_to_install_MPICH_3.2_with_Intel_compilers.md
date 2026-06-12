---
title: "Trying to install MPICH 3.2 with Intel compilers"
date: 2016-01-08
forum: General Help
---

### Post by Chris_Laskaris on 2016-01-08
As the title says, I am trying to install MPICH 3.2 with Intel compilers.

I am using a fresh install of Ubuntu 14.04 LTS. I have successfully installed g++ and the Intel C++ and Fortran compilers. I have activated the Fortran compiler with the command:

```
source /opt/intel/bin/ifortvars.sh ia32
```

The Intel compilers seem to be working fine:

```
laskaris@ubuntu:~$ ifort --version
ifort (IFORT) 16.0.1 20151021
Copyright (C) 1985-2015 Intel Corporation.  All rights reserved.

laskaris@ubuntu:~$ icc --version
icc (ICC) 16.0.1 20151021
Copyright (C) 1985-2015 Intel Corporation.  All rights reserved.
```

I then try to configure MPICH, specifying the compilers I wish to use. But I get an error message:

```
laskaris@ubuntu:~/mpich-3.2$ ./configure CC=icc FC=ifort F77=ifort
Configuring MPICH version 3.2 with  'CC=icc' 'FC=ifort' 'F77=ifort'
Running on system: Linux ubuntu 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:18:00 UTC 2015 i686 athlon i686 GNU/Linux
checking whether the C compiler works... no
configure: error: in `/home/laskaris/mpich-3.2':
configure: error: C compiler cannot create executables
See `config.log' for more details
```

The config.log file says:

```
icc: command not found
```

How can this be, given that the console command icc --version shows a version and seems to be working just fine? What could the problem be?

Thanks for your help!

---

### Post by steeldriver on 2016-01-08
I'd try giving the absolute path i.e. 'CC=/opt/intel/icc' or whatever

---

### Post by Chris_Laskaris on 2016-01-09
> **steeldriver said:**
> I'd try giving the absolute path i.e. 'CC=/opt/intel/icc' or whatever

Thank you, that worked. This command did the trick:

```
./configure CC=/opt/intel/compilers_and_libraries_2016.1.150/linux/bin/ia32/icc FC=/opt/intel/compilers_and_libraries_2016.1.150/linux/bin/ia32/ifort F77=/opt/intel/compilers_and_libraries_2016.1.150/linux/bin/ia32/ifort
```

---

