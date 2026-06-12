---
title: "Wayland much slower than x11"
date: 2017-10-28
forum: General Help
---

### Post by corradoventu on 2017-10-28
On my PC:
System:    Host: corrado-artful-p3 Kernel: 4.13.0-16-generic x86_64
           bits: 64 gcc: 7.2.0
           Desktop: Gnome 3.26.1 (Gtk 3.22.24-0ubuntu1) Distro: Ubuntu 17.10
Machine:   Device: desktop Mobo: ASRock model: H110M-G/M.2 serial: N/A
           UEFI: American Megatrends v: P1.10 date: 05/11/2017
CPU:       Dual core Intel Core i3-7100 (-HT-MCP-) 
           arch: Skylake rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 15648
           clock speeds: max: 3900 MHz 1: 3900 MHz 2: 3900 MHz 3: 3900 MHz
           4: 3900 MHz
Graphics:  Card: Intel HD Graphics 630 bus-ID: 00:02.0 
           Display Server: wayland (X.Org 1.19.5 ) driver: i915
           Resolution: 1920x1080@59.96hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2)
           version: 4.5 Mesa 17.2.2 Direct Render: Yes

Wayland is much slower than x11:
GTKperf gives times 6.9-7.3 while x1 gives 1.9-2.2
Hardinfo GPU Drawing gives 6900-7300 while x11 9900-10100

Should I open a bug? Against Wayland? ubuntu-bug Xwayland ? or ubuntu-bug gdm-wayland-session ?
Thanks

In attacment: output from inxi and GTKperf

---

### Post by mc4man on 2017-10-28
Maybe try some add. benchmarks
[http://www.phoronix-test-suite.com/?k=downloads](http://www.phoronix-test-suite.com/?k=downloads)

---

### Post by corradoventu on 2017-10-28
I downloaded  Phoronix Test Suite   but i have an error installing a test

```
corrado@corrado-artful-p3:~$ phoronix-test-suite install pts/glmark2

The following dependencies are needed and will be installed: 

- freeglut3-dev
- libpng-dev
- libjpeg-dev
- mesa-utils
- unzip
- apt-file

This process may take several minutes.
[sudo] password for corrado: 
dpkg-preconfigure: unable to re-open stdin: No such file or directory
Reading package lists...
Building dependency tree...
Reading state information...
unzip is already the newest version (6.0-21ubuntu1).
mesa-utils is already the newest version (8.3.0-5).
mesa-utils set to manually installed.

......

Phoronix Test Suite v7.4.0

    To Install:    pts/glmark2-1.1.0

    Determining File Requirements ................................................................................................................
    Searching Download Caches ....................................................................................................................

    1 Test To Install
        1 File To Download [7.49MB]
        59MB Of Disk Space Is Needed

    pts/glmark2-1.1.0:
        Test Installation 1 of 1
        1 File Needed [7.49 MB]
        Downloading: glmark2-20170617.tar.gz                                                                                              [7.49MB]
        Downloading ..............................................................................................................................
        Installation Size: 59 MB
        Installing Test @ 20:04:15
            The installer exited with a non-zero exit status.
            ERROR: Missing Command:
            LOG: ~/.phoronix-test-suite/installed-tests/pts/glmark2-1.1.0/install-failed.log


corrado@corrado-artful-p3:~$
```

---

### Post by mc4man on 2017-10-28
does that log show anything?
Seemed to install ok here (though had an ambiguous message?
```
$  phoronix-test-suite install pts/glmark2
......
The following dependencies are needed and will be installed: 

- freeglut3-dev
- mesa-utils
- unzip
- apt-file
This process may take several minutes.
[sudo] password for doug: 
....
The system-wide cache is empty. You may want to run 'apt-file update'
as root to update the cache.
    To Install:    pts/glmark2-1.1.0

    Determining File Requirements ......................................................................................
    Searching Download Caches ..........................................................................................

    1 Test To Install
        1 File To Download [7.49MB]
        59MB Of Disk Space Is Needed

    pts/glmark2-1.1.0:
        Test Installation 1 of 1
        1 File Needed [7.49 MB]
        Downloading: glmark2-20170617.tar.gz                                                                    [7.49MB]
        Downloading ....................................................................................................
        Installation Size: 59 MB
        Installing Test @ 15:30:24
[COLOR="#FF0000"]sh: 1: cannot create 1: Permission denied[/COLOR] 
```

```
~$ phoronix-test-suite install pts/glmark2

Phoronix Test Suite v7.4.0

    Installed:     pts/glmark2-1.1.0
```

(- am doing in an xorg session if that matters??

---

### Post by mc4man on 2017-10-28
Here's some - 
[https://www.phoronix.com/scan.php?page=article&item=fedora-27-beta&num=1](https://www.phoronix.com/scan.php?page=article&item=fedora-27-beta&num=1)
[https://www.phoronix.com/scan.php?page=article&item=gnome-326-x11way&num=1](https://www.phoronix.com/scan.php?page=article&item=gnome-326-x11way&num=1) ( notice Unigine has issue with wayland

---

### Post by corradoventu on 2017-10-30
with phoronix-test-suite i have 
```
pts/etlegacy on x11: Average: 68.00 Frames Per Second
pts/etlegacy on wayland: Average: 46.13 Frames Per Second

pts/glmark2 on x11: Average: 264 Score
pts/glmark2 on wayland: Average: 271 Score

but running pts/glmark2 on x11 i see

  OPERATING SYSTEM:   Ubuntu 17.10
    Kernel:           4.13.0-16-generic (x86_64)
    Desktop:          GNOME Shell 3.26.1
    [COLOR="#FF0000"]Display Server:   Wayland[/COLOR]
    Compiler:         GCC 7.2.0

    Would you like to save these test results (Y/n): y

......

Current Description: Intel Core i3-7100 testing with a ASRock H110M-G/M.2 and Intel HD 630 3072MB on Ubuntu 17.10 via the Phoronix Test Suite.


GLmark2 276:
    pts/glmark2-1.1.0 [Resolution: 1920 x 1080]
    Test 1 of 1
    Estimated Trial Run Count:    1
    Estimated Time To Completion: 6 Minutes [07:59 CET]
        Started Run 1 @ 07:54:19

    Resolution: 1920 x 1080:
        268

    Average: 268 Score

    OpenBenchmarking.org Dynamic Comparison: 
    Score > Higher Is Better
    oggi30ott .. 268  |=========
    Test ....... 2504 |=======================================================================================
    Result Reference: [http://openbenchmarking.org/result/1709104-TR-TEST1175605](http://openbenchmarking.org/result/1709104-TR-TEST1175605)

    Do you want to view the results in your web browser (Y/n): n
    Would you like to upload the results to OpenBenchmarking.org (Y/n): n

corrado@corrado-artful-p3:~$ inxi -Gx
Graphics:  Card: Intel HD Graphics 630 bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.5 ) driver: i915
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2)
           version: 4.5 Mesa 17.2.2 Direct Render: Yes
```

---

### Post by Chanath on 2017-10-30
@[COLOR=#000000]corradoventu

Do you have Wayland on Ubuntu 18.04?

I don't appear to have it. The Ubuntu (Default) session says it is X11.[/COLOR]

---

### Post by slickymaster on 2017-10-30
*Thread moved to **General Help**.*

---

### Post by vasa1 on 2017-10-30
> **Chanath said:**
> @[COLOR=#000000]corradoventu

Do you have Wayland on Ubuntu 18.04?

I don't appear to have it. The Ubuntu (Default) session says it is X11.[/COLOR]

This thread is about 17.10. Let's please keep it that way. Thanks.

---

### Post by slickymaster on 2017-10-30
@corradoventu:

Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting output. Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The use of code tags makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by corradoventu on 2017-10-30
I have wayland and x11 on Artful 17.10 as you may see from inxi output. Inxi says x11 but pts/glmark2 says wayland.

---

