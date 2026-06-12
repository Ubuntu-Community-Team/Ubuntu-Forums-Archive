---
title: "Problem installing Garfield on Ubuntu 14.04 LTS 64 bit"
date: 2017-05-17
forum: General Help
---

### Post by arnabbanerjee on 2017-05-17
Hi Everybody,

I am trying to install Garfield on my laptop which consists of Ubuntu 14.04 LTS 64 bit.

But at one step I got an error as follows:

```
arnab@arnab-Inspiron-3542:~/Work/Garfield$ make garfield-9
fcasplit garfield-9.f
 FCASPLIT executing.
             Input file : garfield-9.f
           Shell script : garfield-9.shfca
              Make file : garfield-9.mkfca
        Fortran    name : gfortran  
        Fortran options : -c -g -O2 -fno-automatic  
             CC    name : gcc  
             CC options : -c -g -O2  
      Assembler    name : as  
      Assembler options :   
 106804 lines written for   459 decks
     27 trailing comment lines ignored.
fcasplit garfadd-9.f
 FCASPLIT executing.
             Input file : garfadd-9.f
           Shell script : garfadd-9.shfca
              Make file : garfadd-9.mkfca
        Fortran    name : gfortran  
        Fortran options : -c -g -O2 -fno-automatic  
             CC    name : gcc  
             CC options : -c -g -O2  
      Assembler    name : as  
      Assembler options :   
At line 786 of file /build/buildd/cernlib-20061220+dfsg3/src/patchy/fcasplit.F (unit = 11, file = '')
Fortran runtime error: File 'garfadd-9.f' does not exist
make: *** [main-9.f] Error 2
arnab@arnab-Inspiron-3542:~/Work/Garfield$ 
```

Can anybody help? 

Thanks in advance.

Arnab

---

### Post by Xian on 2017-05-17
This may be helpful .... good luck. 

[https://ubuntuforums.org/showthread.php?t=1636834&p=11976536#post11976536](https://ubuntuforums.org/showthread.php?t=1636834&p=11976536#post11976536)

---

### Post by gordintoronto on 2017-05-17
It wouldn't hurt to say what garfield is or does, since Googling garfield will produce lots of links to comic strips.

---

### Post by arnabbanerjee on 2017-05-18
Dear Xian,

I had tried the same steps that you have been suggesting through the link. But that does not work. So please tell me is there any other way?

Thanks
Arnab

---

### Post by arnabbanerjee on 2017-05-19
Hi everrybody,

I am still trying to install Garfield in my laptop. At present stage the error is something like below:

```
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgsl.so: undefined reference to `cblas_chemv'
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgsl.so: undefined reference to `cblas_dnrm2'
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgsl.so: undefined reference to `cblas_drotm'
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgsl.so: undefined reference to `cblas_icamax'
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgsl.so: undefined reference to `cblas_zgemv'
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgsl.so: undefined reference to `cblas_zhemm'
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgsl.so: undefined reference to `cblas_cgemv'
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgsl.so: undefined reference to `cblas_ssyr2'
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgsl.so: undefined reference to `cblas_strsv'
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgsl.so: undefined reference to `cblas_dscal'
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgsl.so: undefined reference to `cblas_dgemm'
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgsl.so: undefined reference to `cblas_srotmg'
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgsl.so: undefined reference to `cblas_dtrsm'
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgsl.so: undefined reference to `cblas_ccopy'
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgsl.so: undefined reference to `cblas_zsyrk'
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgsl.so: undefined reference to `cblas_cswap'
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgsl.so: undefined reference to `cblas_daxpy'
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgsl.so: undefined reference to `cblas_csyrk'
collect2: error: ld returned 1 exit status
make: *** [garfield-9] Error 1
```

Can anybody help? I am attaching the makefile that I am using. 

Thanks,
Arnab

---

### Post by mörgæs on 2017-05-19
> **gordintoronto said:**
> It wouldn't hurt to say what garfield is or does, since Googling garfield will produce lots of links to comic strips.

Yes, please do. I have never heard of a program with that name.

If [this]("https://github.com/GarfieldLinux/garfield") is the one it looks like an abandoned project.

---

### Post by dragonfly41 on 2017-05-19
The clue is "Fortran" in post #1 ..

[https://ubuntuforums.org/showthread.php?t=1636834&page=4&p=11976536#post11976536](https://ubuntuforums.org/showthread.php?t=1636834&page=4&p=11976536#post11976536)

see post #38 in that thread ..

And more here .. [http://lambda.phys.tohoku.ac.jp/~kobayash/seminar/files/cern/garfield.pdf](http://lambda.phys.tohoku.ac.jp/~kobayash/seminar/files/cern/garfield.pdf)

Is Garfield expecting 32bit OS architecture?

> I am trying to install Garfield on my laptop which consists of Ubuntu 14.04 LTS 64 bit.

Perhaps it might install in a 32bit VM in Virtual Box?

---

