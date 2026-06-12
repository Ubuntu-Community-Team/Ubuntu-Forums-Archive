---
title: "X is not starting any more for segmentation fault"
date: 2014-01-20
forum: General Help
---

### Post by uqbar on 2014-01-20
Since a few days the X part of my Kubuntu desktop is failing to start.
This is what I see in /var/log/Xorg.0.log:```
...
[  3235.155]    ABI class: X.Org ANSI C Emulation, version 0.4
[  3235.155] (II) glamor: OpenGL accelerated X.org driver based.
[  3235.173] (EE) 
[  3235.173] (EE) Backtrace:
[  3235.174] (EE) 0: /usr/bin/X (xorg_backtrace+0x3d) [0x7f5e6c442fdd]
[  3235.174] (EE) 1: /usr/bin/X (0x7f5e6c2a0000+0x1a6d49) [0x7f5e6c446d49]
[  3235.174] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f5e6b3a1000+0xfbb0) [0x7f5e6b3b0bb0]
[  3235.174] (EE) 
[  3235.174] (EE) Segmentation fault at address 0x0
[  3235.174] (EE) 
Fatal server error:
[  3235.174] (EE) Caught signal 11 (Segmentation fault). Server aborting
[  3235.174] (EE) 
[  3235.174] (EE) 
Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
[  3235.174] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  3235.174] (EE) 
[  3235.179] (EE) Server terminated with error (1). Closing log file.
```My system is:
```
Distributor ID: Ubuntu
Description:    Ubuntu 13.10
Release:        13.10
Codename:       saucy
```Architecture is x86_64 anx Xorg -version reports:```
X.Org X Server 1.14.5
Release Date: 2013-12-12
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
Current Operating System: Linux Feynman 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:17:04 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-3.11.0-15-generic root=/dev/mapper/vg_feynman-lv_root ro quiet splash vt.handoff=7
Build Date: 17 December 2013  10:06:15AM
xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.30.2
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
```.
I have tried to reinstall libc6, libc6-amd64 (bacause of libpthread), xorg and xserver-xorg.
No way.
I would like not to reinstall the whole (K)ubuntu system.
Any hint?
Thanks in advance.

---

### Post by Bashing-om on 2014-01-20
uqbar; Hi !

An error reported in  /var/log/Xorg.0.log may be indicative of a problem with the graphics driver.

What results if you attempt to boot the operating system from the "recovery" console ?
As this means will force the use of a onboard graphics driver.

[INDENT][INDENT]a perspective
[INDENT][INDENT][INDENT]from an alternate vantage point
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by uqbar on 2014-01-21
In the recovery boot mode there is nothing useful.
I can reinstall packages, but I could do that from the normal CLI.
If only I knew what's wrong...

---

### Post by Bashing-om on 2014-01-21
uqbar; Like this,

If you are able to boot to the GUI desk top from the recovery console, even with degraded graphics, that pretty well points to a graphics driver issue.

What one might do in that case is to remove the driver that is currently loaded and (re)install a driver (?) 

Then
[INDENT]it ain't nothing
[INDENT][INDENT][INDENT]but a thing
[/INDENT][/INDENT][/INDENT][/INDENT]

---

