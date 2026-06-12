---
title: "LibreOffice Writer 5.1.2: please test this"
date: 2016-05-16
forum: General Help
---

### Post by vasa1 on 2016-05-16
Warning: keep a terminal window ready to run *pkill soffice*!

I would like to know how the following works for you ***only*** if 
[LIST]
[*]you're on 16.04 (any official flavor)
[*]have the version of LibreOffice being offered in the Software Center (1:5.1.2-0ubuntu1), not one that's older or newer.
[*]have the default kernel (4.4.0-22-generic)
[/LIST]

1. Make a Writer file by entering
```
1
2
3
4
5
6
7
8
9
10
```and then copying that until you have 500 lines.

2. Save the file as *test1.odt* and close Writer and any other Libreoffice process. *pgrep soffice* should come up blank.

3. cd to the folder containing *test1.odt* and run```
SAL_USE_VCLPLUGIN=gtk libreoffice --writer test1.odt
```This should launch Writer as a ***gtk2*** application and open *test1.odt* without too much of an issue.

4. Now toggle between *Normal* and *Web* by clicking on *View* in the menu bar and selecting the appropriate viewing mode. 
[LIST]
[*]While you're toggling, there shouldn't be much of a delay in the repagination process and you can monitor that in the lower left corner of the status bar.
[*]There shouldn't be much CPU usage either (if you can monitor that).
[/LIST]

5. Quit LibreOffice and check with *pgrep soffice*.

6. Now keep a terminal window open ready to run *pkill soffice* and open another terminal window to the folder containing *test1.odt* and run ```
libreoffice --writer test1.odt
```This should cause LibreOffice Writer to open as a ***gtk3*** application.

At this point, I would like to know 
[LIST]
[*]if *test1.odt* opens as quickly as it did when Writer was opened in gtk2 mode
[*]if the document is immediately responsive to selecting lines, moving the text cursor (insertion bar) around, etc
[*]whether you can toggle as easily between *Normal* view and *Web* view as when *test1.odt* was opened in *gtk2* mode.
[*]whether repagination takes a significant time and there's a usability lag
[/LIST]

In my case, when I run LibreOffice Writer in gtk3 mode (which is the default mode) and open *test1.odt* **_in Web view_**, the LibreOffice window can become unresponsive for at least one minute, %CPU usage goes up to >60% and the laptop's temperature rises to > 60 Celsius. Opening the same file in Normal view is _not_ a problem.

My laptop is a Dell Inspiron 1545 Core2Duo, 4GB RAM, integrated graphics (= no GPU) bought in 2009.

```
07:55 PM ~ $ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Model name:            Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz
Stepping:              10
CPU MHz:               2000.000
CPU max MHz:           2000.0000
CPU min MHz:           1200.0000
BogoMIPS:              3989.90
L1d cache:             32K
L1i cache:             32K
L2 cache:              2048K
NUMA node0 CPU(s):     0,1
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm
07:55 PM ~ $ 
```

and```
07:55 PM ~ $ grep -i chipset /var/log/Xorg.0.log
[    40.291] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
[    40.292] (II) VESA: driver for VESA chipsets: vesa
[    40.636] (--) intel(0): Integrated Graphics Chipset: Intel(R) GM45
07:57 PM ~ $ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
07:57 PM ~ $ 
```

Can others please test and post their experience?

There's [another thread]("http://ubuntuforums.org/showthread.php?t=2322879") around but neither of the posters there are in a position to upload their documents for others to test :(

---

### Post by Impavidus on 2016-05-16
I just checked on Xubuntu 16.04, upgraded from 14.10 via all interim releases, all packages the latest version from the official Ubuntu repos (which means the versions you mentioned). Libreoffice remains responsive at all times. No significant delays. I've got an HP Probook 4530s with Intel Core i5 CPU, integrated graphics and 8GB memory.

---

### Post by vasa1 on 2016-05-16
> **Impavidus said:**
> I just checked on Xubuntu 16.04, upgraded from 14.10 via all interim releases, all packages the latest version from the official Ubuntu repos (which means the versions you mentioned). Libreoffice remains responsive at all times. No significant delays. I've got an HP Probook 4530s with Intel Core i5 CPU, integrated graphics and 8GB memory.

Thanks! Do you know if you have a GPU as part of the integrated graphics? My hardware knowledge isn't much :(

---

### Post by QLee on 2016-05-16
Hello vasa1,
On a desktop with a low power "Bay Trail" Atom CPU and 8G memory with Intel integrated graphics only. [Edit] upgraded 16.04 just before test.

Both tests were responsive enough that I wouldn't have noticed a difference if I hadn't been looking for one. The gtk3 mode seemed sightly less responsive but it also seemed to use a bit less CPU [Edit](both were under 15%) during the test. Both worked so well that I'm not sure there was enough difference to actually call it a difference or perhaps other things happening in the background that might have caused a slight delay or a few extra cpu cycles. I certainly did not see anything like the lag you mentioned. They just switched back and forth pretty smoothly.

HTH

---

### Post by vasa1 on 2016-05-16
> **QLee said:**
> Hello vasa1,
On a desktop with a low power "Bay Trail" Atom CPU and 8G memory with Intel integrated graphics only. [Edit] upgraded 16.04 just before test.

Both tests were responsive enough that I wouldn't have noticed a difference if I hadn't been looking for one. The gtk3 mode seemed sightly less responsive but it also seemed to use a bit less CPU [Edit](both were under 15%) during the test. Both worked so well that I'm not sure there was enough difference to actually call it a difference or perhaps other things happening in the background that might have caused a slight delay or a few extra cpu cycles. I certainly did not see anything like the lag you mentioned. They just switched back and forth pretty smoothly.

HTH
Thanks, QLee! It's interesting that the gtk3 mode seemed to use *less* CPU. I suspect gtk3 + newer hardware makes for more efficiency.

---

### Post by QLee on 2016-05-16
> **vasa1 said:**
> Thanks, QLee! It's interesting that the gtk3 mode seemed to use *less* CPU. I suspect gtk3 + newer hardware makes for more efficiency.

Yes, this should be the intention in upgraded software.  ;-) Don't put too much on my one time test, as I said, I wasn't monitoring carefully if anything else might have skewed my observations. And, it was only in the neighbourhood of 5% or less for a brief moment.

[Edit] I should mention that I'm not sure a document with 500 lines and only 500 characters is comparable to what is in the other thread, which is a "real" document with diagrams and such. Maybe you should have the other poster try this simple test that you posed if they don't want to supply an example.

---

### Post by bapoumba on 2016-05-16
No difference as far as responsiveness.
4- transiently uses about 40%CPU (under 10 sec, then resumes to normal very low numbers) when going from normal to web view, not the other way around
6- same
```
bapoumba@bapoumba-Mate1604:~/Desktop$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 42
Model name:            Intel(R) Core(TM) i7-2760QM CPU @ 2.40GHz
Stepping:              7
CPU MHz:               2399.998
BogoMIPS:              4799.99
Hypervisor vendor:     KVM
Virtualization type:   full
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              6144K
NUMA node0 CPU(s):     0,1
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx rdtscp lm constant_tsc rep_good nopl xtopology nonstop_tsc pni pclmulqdq ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx hypervisor lahf_lm

```
```
bapoumba@bapoumba-Mate1604:~/Desktop$ grep -i chipset /var/log/Xorg.0.log
[    32.526] (II) VESA: driver for VESA chipsets: vesa
bapoumba@bapoumba-Mate1604:~/Desktop$ lspci | grep VGA
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter

```
This is ubuntu-mate 16.04 up to date in a VM (MacOS host), 3GB mem (out of 8).

---

### Post by vasa1 on 2016-05-16
> **QLee said:**
> ...
[Edit] I should mention that I'm not sure a document with 500 lines and only 500 characters is comparable to what is in the other thread, which is a "real" document with diagrams and such. Maybe you should have the other poster try this simple test that you posed if they don't want to supply an example.

There are two users there! I've pointed to this thread. Let's see.

> **bapoumba said:**
> No difference as far as responsiveness.
4- transiently uses about 40%CPU (under 10 sec, then resumes to normal very low numbers) when going from normal to web view, not the other way around
6- same
```
...
Model name:            Intel(R) Core(TM) i7-2760QM CPU @ 2.40GHz
...
```
...
Well, impavidus with *i5* and bapoumba with *i7* and QLee with *Bay Trail*. The messages seem to point to getting a new laptop!

---

### Post by Impavidus on 2016-05-17
> **vasa1 said:**
> Thanks! Do you know if you have a GPU as part of the integrated graphics? My hardware knowledge isn't much :(

Integrated graphics only, no separate GPU. I didn't mention I'm on a 64 bit system, but I think you already guessed that.

Maybe noteworthy, libreoffice complains that it cannot find a Java Runtime Environment, which is logical, as I haven't installed it.

---

### Post by vasa1 on 2016-05-17
> **Impavidus said:**
> Integrated graphics only, no separate GPU. I didn't mention I'm on a 64 bit system, but I think you already guessed that.

Maybe noteworthy, libreoffice complains that it cannot find a Java Runtime Environment, which is logical, as I haven't installed it.
Mine is 64-bit as well. I too don't need and so haven't installed JRE. Maybe I should have mentioned that.

Re. graphics, I'm not really clear about the concept but maybe one could have a GPU and still have integrated graphics. I think my low-end Dell laptop just doesn't have a GPU.

Someone had suggested seeing what Firefox has to say in the *Graphics* section under *Help > Troubleshooting*:```
Graphics
--------

Adapter Description: Intel Open Source Technology Center -- Mesa DRI Mobile IntelÂ® GM45 Express Chipset
Asynchronous Pan/Zoom: none
Device ID: Mesa DRI Mobile Intel® GM45 Express Chipset
Driver Version: 2.1 Mesa 11.2.0
**GPU Accelerated Windows: _0_/1 Basic (OMTC)**
Supports Hardware H264 Decoding: No;
Vendor ID: Intel Open Source Technology Center
WebGL Renderer: Intel Open Source Technology Center -- Mesa DRI Mobile IntelÂ® GM45 Express Chipset
windowLayerManagerRemote: true
AzureCanvasBackend: cairo
AzureContentBackend: cairo
AzureFallbackCanvasBackend: none
AzureSkiaAccelerated: 0
CairoUseXRender: 1

```In **GPU Accelerated Windows: _0_/1 Basic (OMTC)**, the _0_ is supposed to mean no GPU.

---

### Post by kagashe on 2016-05-17
Tested on my Lenovo G50-45
CPU1 usage jumps to 100% in Web view in both gtk2 and gtk3 mode and responsiveness is ok.

```
$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            22
Model:                 48
Model name:            AMD E1-6010 APU with AMD Radeon R2 Graphics
Stepping:              1
CPU MHz:               1000.000
CPU max MHz:           1350.0000
CPU min MHz:           1000.0000
BogoMIPS:              2694.97
Virtualization:        AMD-V
L1d cache:             32K
L1i cache:             32K
L2 cache:              1024K
NUMA node0 CPU(s):     0,1
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf eagerfpu pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt topoext perfctr_nb bpext perfctr_l2 hw_pstate vmmcall bmi1 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale flushbyasid decodeassists pausefilter pfthreshold
```

```
$ grep -i chipset /var/log/Xorg.0.log
[    34.346] (II) RADEON: Driver for ATI Radeon chipsets:
[    34.364] (II) VESA: driver for VESA chipsets: vesa
[    34.371] (--) RADEON(0): Chipset: "MULLINS" (ChipID = 0x9853)
```

Kamalakar

---

### Post by vasa1 on 2016-05-17
> **kagashe said:**
> Tested on my Lenovo G50-45
CPU1 usage jumps to 100% in Web view in both gtk2 and gtk3 mode and responsiveness is ok.
...
Kamalakar
Thanks for testing :) Can you say for how long CPU1 was at 100% in Web view? I'm guessing not more than a few seconds?

---

### Post by kagashe on 2016-05-17
> **vasa1 said:**
> Thanks for testing :) Can you say for how long CPU1 was at 100% in Web view? I'm guessing not more than a few seconds?

Yes. I am attaching a screenshot

Kamalakar

---

### Post by vasa1 on 2016-05-23
One more file for testing. This too works for me in gtk2 mode in Normal layout but bogs down in gtk3 mode:

[https://wiki.documentfoundation.org/images/f/f3/GS50-GettingStartedLO.odt](https://wiki.documentfoundation.org/images/f/f3/GS50-GettingStartedLO.odt)

(Also posted in johnsd's thread [here]("http://ubuntuforums.org/showthread.php?t=2322879&p=13493448#post13493448").)

---

