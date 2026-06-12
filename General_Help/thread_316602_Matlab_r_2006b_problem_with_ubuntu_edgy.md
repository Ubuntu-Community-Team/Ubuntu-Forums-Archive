---
title: "Matlab r 2006b problem with ubuntu edgy"
date: 2006-12-11
forum: General Help
---

### Post by weiqiang on 2006-12-11
I experienced a matlab problem after installation. After launching the matlab, if I open a new window in matlab, e.g. an editor of matlab, and close it, matlab crashes and disapppear.

Here is the "ver" output:

-------------------------------------------------------------------------------------
MATLAB Version 7.3.0.298 (R2006b)
MATLAB License Number: xxxxxx
Operating System: Linux 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Java VM Version: Java 1.5.0 with Sun Microsystems Inc. Java HotSpot(TM) Client VM mixed mode
-------------------------------------------------------------------------------------
MATLAB                                                Version 7.3        (R2006b)
Simulink                                              Version 6.5        (R2006b)
Communications Blockset                               Version 3.4        (R2006b)
Communications Toolbox                                Version 3.4        (R2006b)
Control System Toolbox                                Version 7.1        (R2006b)
Curve Fitting Toolbox                                 Version 1.1.6      (R2006b)
Database Toolbox                                      Version 3.2        (R2006b)
Distributed Computing Toolbox                         Version 3.0        (R2006b)
Extended Symbolic Math Toolbox                        Version 3.1.5      (R2006b)
Filter Design HDL Coder                               Version 1.5        (R2006b)
Filter Design Toolbox                                 Version 4.0        (R2006b)
Genetic Algorithm and Direct Search Toolbox           Version 2.0.2      (R2006b)
Image Processing Toolbox                              Version 5.3        (R2006b)
Link for ModelSim                                     Version 2.1        (R2006b)
MATLAB Builder for Java                               Version 1.0        (R2006b)
MATLAB Compiler                                       Version 4.5        (R2006b)
MATLAB Report Generator                               Version 3.1        (R2006b)
Mapping Toolbox                                       Version 2.4        (R2006b)
Model Predictive Control Toolbox                      Version 2.2.3      (R2006b)
Optimization Toolbox                                  Version 3.1        (R2006b)
RF Blockset                                           Version 1.3.1      (R2006b)
RF Toolbox                                            Version 2.0        (R2006b)
Real-Time Workshop                                    Version 6.5        (R2006b)
Real-Time Workshop Embedded Coder                     Version 4.5        (R2006b)
Signal Processing Blockset                            Version 6.4        (R2006b)
Signal Processing Toolbox                             Version 6.6        (R2006b)
Simulink Accelerator                                  Version 6.5        (R2006b)
Simulink Control Design                               Version 2.0.1      (R2006b)
Simulink Fixed Point                                  Version 5.3        (R2006b)
Simulink HDL Coder                                    Version 1.0        (R2006b)
Simulink Parameter Estimation                         Version 1.1.4      (R2006b)
Simulink Report Generator                             Version 3.1        (R2006b)
Simulink Response Optimization                        Version 3.1        (R2006b)
Simulink Verification and Validation                  Version 2.0        (R2006b)
Symbolic Math Toolbox                                 Version 3.1.5      (R2006b)
System Identification Toolbox                         Version 6.2        (R2006b)

Trademarks
------------------
MATLAB, Simulink, Stateflow, Handle Graphics, Real-Time Workshop, and xPC
TargetBox are registered trademarks of The MathWorks, Inc. Other product or
brand names are trademarks or registered trademarks of their respective holders.
>>



2) Ubuntu 6.10 \n \l
3) Linux ma 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux
4) GNU C Library development release version 2.4, by Roland McGrath et al.
5) processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.70GHz
stepping        : 6
cpu MHz         : 600.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up est tm2
bogomips        : 1197.31

---

### Post by newpants2003 on 2007-03-12
i have the same problem...
also tried 2006a, same thing. 
but 7.0 works.

if you log in as root in the recovery mode, and startx, then run matlab 2006b/a, it will works perfect.
also you can install two matlab, 2006b/a and 7.0.1. if you run the second one first, close, then run the 2006b, it will works. but you have to do it again after a reboot.

may not really help you. hope someone else can tell us how to fix it.

---

### Post by Palmstroem on 2007-03-14
Hi guys,

I have not observed crashes with Matlab 7.3 (R2006b) so far. However, I am on a 64bit machine, see output below:

>> ver
-------------------------------------------------------------------------------------
MATLAB Version 7.3.0.298 (R2006b)
MATLAB License Number: xxxxxx
Operating System: Linux 2.6.17-11-generic #2 SMP Thu Feb 1 18:03:05 UTC 2007 x86_64
Java VM Version: Java 1.5.0_04 with Sun Microsystems Inc. Java HotSpot(TM) 64-Bit Server VM mixed mode
-------------------------------------------------------------------------------------

etc. etc.

Did you have any problems with the flexlm server/client system? I am asking because it caused me a lot of trouble.

---

### Post by newpants2003 on 2007-03-14
what is that?

---

### Post by Palmstroem on 2007-03-15
> **newpants2003 said:**
> what is that?

flexlm is the license manager daemon that is used by quite a number of commercial programs, not only Matlab. Go to /etc within your Matlab directory and inspect the file license.dat.

---

### Post by newpants2003 on 2007-03-15
how to check the license.dat ?

./lmstat gave me this:

lmgrd is not running: Cannot connect to license server system. (-15,570:115 "Operation now in progress")

how to fix?

---

### Post by Palmstroem on 2007-03-16
depends on whether you are running flexlm or lmgrd as client or as server+client. If your file license.dat says

SERVER some-other-computer license-number 27000

then you are a client and the licenses are distributed by another computer on your local network. It is then necessary that you can reach, e.g. ping, this server. Quite often some firewall programs interfere with the communication on several ports which need to be established between server and client.

If your license.dat file says

SERVER your-own-computer license-number 27000

then you are server and client at the same time. You need to get lmgrd running on your computer. You can check this with

ps -A | grep lmgrd

As for me, I am running a client and had a hard time with the server because it was an ill-configured windows computer.

---

### Post by newpants2003 on 2007-03-18
i will try this when i am home. 
but this problem happen to my both pc, should be some common problem, why so hard to find any solutions??

---

