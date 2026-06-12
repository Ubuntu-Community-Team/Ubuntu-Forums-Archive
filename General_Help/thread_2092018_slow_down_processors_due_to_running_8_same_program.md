---
title: "slow down processors due to running 8 same program in 8 core"
date: 2012-12-06
forum: General Help
---

### Post by alireza2010 on 2012-12-06
I have a  computer with 2 intel xeon 4-core processors and 2.0 GHz speed   (it means I have 8 cores on my computer). the cpu model is (Intel® Xeon® Processor E5405 (12M Cache, 2.00 GHz, 1333 MHz FSB) )

 when I  run a program it   takes about 33 seconds. but when I run 8 programs (same  programs)   simultaneously in 8 different folders, they take about 120  seconds   each. I'm so confused. what's the problem?
I use Ubuntu 11.04. I also used the CENT OS 5. but it had the same problem.
for check this problem I checked another sample FORTRAN code that does not need huge memory and I/O. My sample code is:

     ```
program testcpuspeed
implicit none
integer i,j,k
integer,parameter::n=1000000
real(8) a(n),b(n),r


do i=1,1000

    do j=1,n
        a(j)=3321.312+1.0/(float(i)+54.4545)
        b(j)=15.0-1.0/(float(i)+400.055)
    end do

    do k=1+100,n-100
        a(k)=a(k)+21.313+b(k-100)+b(k+100)
    end do

    r=dot_product(a,b)
end do

print*,r

end program testcpuspeed                      
```You can compile it with "gfortran -O3 filename.f90 -o exe"
The output will be "exe"
You can test the time with 
```
time ./exe
```for 1 core. and 
```
time ./exe  & 
time ./exe & 
time ./exe &
time ./exe & 
time ./exe  & 
time ./exe & 
time ./exe & 
time ./exe &

```for 8 cores.
In my computer it take about 13 sec for 1 core and about 50 sec for 8   cores. it means my computer uses only of 2 core effectively. when I get   top during running with 8 cores I have 8 thread with 100% capacity  which  means all 8 cores are running my programs. 

I checked it with another computer. Running this program with 1 core does not differ from 8 core alot in that computer.
you can check this program in your laptop and check the difference. the   number of "time ./exe & " should be as same as your number of your   real cores.

---

### Post by drmrgd on 2012-12-06
I'm not sure that thread processing is exactly linear (depends probably on how things are scheduled and how much time each thread takes to process).  Also, it probably depends a lot on how your program is written and how efficiently it schedules and uses the processor cores.  I would say this is not a hardware problem but either expected behavior or a less than ideal parallel processing algorithm in the program.

---

### Post by alireza2010 on 2012-12-06
> **drmrgd said:**
> I'm not sure that thread processing is exactly linear (depends probably on how things are scheduled and how much time each thread takes to process).  Also, it probably depends a lot on how your program is written and how efficiently it schedules and uses the processor cores.  I would say this is not a hardware problem but either expected behavior or a less than ideal parallel processing algorithm in the program.
Thanks for your reply. But I think the time processing in 8 same programs in 8 core should not differ a lot with a program in 1 core and should be in range of 30-40 seconds. I also checked it in another computer with different hardware. the running time did not differ a lot from 33 seconds.

---

### Post by UltimateCat on 2012-12-06
On a stable system users only install a new kernel if they need support for newer hardware or to correct a performance problem.

Not sure if that helps but I learn it from a man in Debian Testing and I thought it might help for you to know-

---

### Post by Yellow Pasque on 2012-12-07
You're probably hitting another bottleneck (RAM or I/O throughput).

---

### Post by alireza2010 on 2012-12-07
> **Temüjin said:**
> You're probably hitting another bottleneck (RAM or I/O throughput).

for check this problem I checked another sample FORTRAN code that does not need huge memory and I/O. My sample code is:

> program testcpuspeed
implicit none
integer i,j,k
integer,parameter::n=1000000
real(8) a(n),b(n),r


do i=1,1000

    do j=1,n
        a(j)=3321.312+1.0/(float(i)+54.4545)
        b(j)=15.0-1.0/(float(i)+400.055)
    end do

    do k=1+100,n-100
        a(k)=a(k)+21.313+b(k-100)+b(k+100)
    end do

    r=dot_product(a,b)
end do

print*,r

end program testcpuspeed

You can compile it with "gfortran -O3 filename.f90 -o exe"
The output will be "exe"
You can test the time with "time ./exe" for 1 core. and "time ./exe & time ./exe & time ./exe & time ./exe & time ./exe & time ./exe & time ./exe & time ./exe &" for 8 cores.
In my computer it take about 13 sec for 1 core and about 50 sec for 8 cores.
I checked it with another computer. Running with 1 core does not differ from 8 core alot in that computer.

---

### Post by alireza2010 on 2012-12-09
> **UltimateCat said:**
> On a stable system users only install a new kernel if they need support for newer hardware or to correct a performance problem.

Not sure if that helps but I learn it from a man in Debian Testing and I thought it might help for you to know-
I checked it. unfortunately it does not work.

---

### Post by tgalati4 on 2012-12-09
```
sudo apt-get install htop

htop


```

Watch your CPU's fill up in htop and if you get blue bars, that could indicate IOWaits and other system bottlenecks.  Because L1 and L2 cache is sometimes shared between processors, it's possible that your code doesn't scale well with multiple processors.  Although you would think 8x processors would give you 8x computing power for a particular job, but depending on coding, that may not be the case.

Multicore optimization is part art and part science and testing is worth 1,000 expert opinions.

Part of the problem is you are using "time" and that requires pulsing the system clock.  There is only one system clock so every increment of "time" interrupts all processing.  A better metric would be to include some low-level  timing code to print out your job time after each job is finished.

There are several websites and documents written on instrumentation and profiling code.  Some profiling can be done with kernel switches (and a custom-instrumented kernel), others can be done with debugging/profiling compilers, or you can include time calculations in the code itself.  Each metric will be slightly different, but you are looking for relative improvements in code speed.

I use cpuburn (sudo apt-get install cpuburn) to load up my processors on a new build:

```
burnP6 &
burnP6 &
burnP6 &
.
.
.

```

Run htop in another terminal to watch your processors get loaded.

There are lots of benchmarks to be found in:

apt-cache search phoronix
phoronix-test-suite - a comprehensive testing and benchmarking platform
sudo apt-get install phoronix-test-suite
man phoronix-test-suite

---

### Post by alireza2010 on 2012-12-10
11

---

### Post by Yellow Pasque on 2012-12-10
I have an AMD tri-core. It took 8 seconds for 1 core and about 15 seconds when all 3 cores were loaded. htop behavior was as expected. What kind of Xeons do you have? It's possible you're running into a bottleneck from the FSB: [http://en.wikipedia.org/wiki/Pentium_d#Implementation](http://en.wikipedia.org/wiki/Pentium_d#Implementation).

```
$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 4
model name	: AMD Phenom(tm) II X3 720 Processor
stepping	: 2
microcode	: 0x10000db
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 3
core id		: 0
cpu cores	: 3
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save
bogomips	: 5599.96
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 4
model name	: AMD Phenom(tm) II X3 720 Processor
stepping	: 2
microcode	: 0x10000db
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 3
core id		: 1
cpu cores	: 3
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save
bogomips	: 5599.96
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 2
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 4
model name	: AMD Phenom(tm) II X3 720 Processor
stepping	: 2
microcode	: 0x10000db
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 3
core id		: 2
cpu cores	: 3
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save
bogomips	: 5599.96
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

$ time ./fortprog &

real	0m8.423s
user	0m8.251s
sys	0m0.036s

$ time ./fortprog &
[1] 18637
$ time ./fortprog &
[2] 18639
$ time ./fortprog &
[3] 18641
$    50586805392.047012     

real	0m15.554s
user	0m15.165s
sys	0m0.014s
   50586805392.047012     

real	0m16.577s
user	0m15.514s
sys	0m0.079s
   50586805392.047012     

real	0m17.062s
user	0m15.016s
sys	0m0.092s



```

---

### Post by lisati on 2012-12-10
Threads merged.

Please do not start multiple threads for the same support request, it dilutes the community's ability to help.

---

### Post by Pjotr123 on 2012-12-11
Try installing the latest microcode for your CPU:
[https://sites.google.com/site/easylinuxtipsproject/microcode](https://sites.google.com/site/easylinuxtipsproject/microcode)

It might help, and certainly won't do any harm....

---

### Post by alireza2010 on 2012-12-11
> **Temüjin said:**
> I have an AMD tri-core. It took 8 seconds for 1 core and about 15 seconds when all 3 cores were loaded. htop behavior was as expected. What kind of Xeons do you have? It's possible you're running into a bottleneck from the FSB: [http://en.wikipedia.org/wiki/Pentium_d#Implementation](http://en.wikipedia.org/wiki/Pentium_d#Implementation).

```
$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 4
model name	: AMD Phenom(tm) II X3 720 Processor
stepping	: 2
microcode	: 0x10000db
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 3
core id		: 0
cpu cores	: 3
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save
bogomips	: 5599.96
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 4
model name	: AMD Phenom(tm) II X3 720 Processor
stepping	: 2
microcode	: 0x10000db
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 3
core id		: 1
cpu cores	: 3
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save
bogomips	: 5599.96
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 2
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 4
model name	: AMD Phenom(tm) II X3 720 Processor
stepping	: 2
microcode	: 0x10000db
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 3
core id		: 2
cpu cores	: 3
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save
bogomips	: 5599.96
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

$ time ./fortprog &

real	0m8.423s
user	0m8.251s
sys	0m0.036s

$ time ./fortprog &
[1] 18637
$ time ./fortprog &
[2] 18639
$ time ./fortprog &
[3] 18641
$    50586805392.047012     

real	0m15.554s
user	0m15.165s
sys	0m0.014s
   50586805392.047012     

real	0m16.577s
user	0m15.514s
sys	0m0.079s
   50586805392.047012     

real	0m17.062s
user	0m15.016s
sys	0m0.092s



```
my cpu model is Intel® Xeon® Processor E5405 (12M Cache, 2.00 GHz, 1333 MHz FSB). perhaps you are right. what should I do now?

---

