---
title: "Linux Kernel Issue"
date: 2020-09-10
forum: General Help
---

### Post by mpmckinnon on 2020-09-10
Hi there I am not sure were to post this question I am hoping someone can help me here. When I try to do an update now I get this error message "[FONT=monospace][COLOR=#000000]E: The package linux-modules-5.8.7-050807-generic needs to be reinstalled, but I can't f[/COLOR]ind an archive for it." I would like to be able to fix this issue. Thank you for your guys help with this. :-)
[/FONT]

---

### Post by deadflowr on 2020-09-10
Outside of possibly a development version package 5.8 is only available from the Ubuntu kernel mainline packages.
So should be able to grab it from here: [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.8.7/]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.8.7/")

---

### Post by speartip on 2020-09-10
You'll need to give more info as to what version Ubuntu you're on, & where you got that Kernel from. You seem to be on the 5.8 series kernel, were 20.04 ships with the 5.4 kernel.

---

### Post by mpmckinnon on 2020-09-10
Thank you for getting back I am using Kubuntu 20.04 and downloaded it orginally from [COLOR=var(--black-800)][FONT=Consolas]uktools-upgrade.[/FONT][/COLOR]

---

### Post by deadflowr on 2020-09-10
Okay, so looking at uktools it can do updates and removals of development mainline testing kernels.
[https://github.com/usbkey9/uktools]("https://github.com/usbkey9/uktools")
I wonder what kernel you are on currently:
see
```
uname -a
```
also what kernels are installed 
see
```
dpkg -l linux-*
```
note that this command should be run in a maximize or full screen as the output actually gets cropped out in windows mode.

---

### Post by mpmckinnon on 2020-09-11
[FONT=monospace][COLOR=#000000]Linux TheOneAndOnly 5.9.0-050900rc4-generic #202009070130 SMP Mon Sep 7 01:35:52 UTC 202[/COLOR]
0 x86_64 x86_64 x86_64 GNU/Linux

```
[/FONT][FONT=monospace][COLOR=#000000]esired=Unknown/Install/Remove/Purge/Hold[/COLOR]
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                         Version                      Architect[COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
+++-============================================-============================-=========[COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
ii  linux-base                                   4.5ubuntu3.1                 all      [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
un  linux-doc                                    <none>                       <none>   [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
un  linux-doc-5.9.0                              <none>                       <none>   [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
ii  linux-firmware                               1.187.3                      all      [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
un  linux-firmware-raspi2                        <none>                       <none>   [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
un  linux-firmware-snapdragon                    <none>                       <none>   [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
un  linux-headers                                <none>                       <none>   [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
un  linux-headers-3.0                            <none>                       <none>   [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
ii  linux-headers-5.8.7-050807                   5.8.7-050807.202009051031    all      [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
ii  linux-headers-5.8.7-050807-generic           5.8.7-050807.202009051031    amd64    [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
ii  linux-headers-5.8.8-050808                   5.8.8-050808.202009091435    all      [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
ii  linux-headers-5.8.8-050808-generic           5.8.8-050808.202009091435    amd64    [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
ii  linux-headers-5.9.0-050900rc2                5.9.0-050900rc2.202008232232 all      [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
ii  linux-headers-5.9.0-050900rc2-generic        5.9.0-050900rc2.202008232232 amd64    [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
ii  linux-headers-5.9.0-050900rc3                5.9.0-050900rc3.202008302030 all      [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
ii  linux-headers-5.9.0-050900rc3-generic        5.9.0-050900rc3.202008302030 amd64    [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
ii  linux-headers-5.9.0-050900rc4                5.9.0-050900rc4.202009070130 all      [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
ii  linux-headers-5.9.0-050900rc4-generic        5.9.0-050900rc4.202009070130 amd64    [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
un  linux-headers-686-pae                        <none>                       <none>   [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
un  linux-headers-amd64                          <none>                       <none>   [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
un  linux-headers-generic                        <none>                       <none>   [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
un  linux-image                                  <none>                       <none>   [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
un  linux-image-5.8.7-050807-generic             <none>                       <none>   [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
un  linux-image-5.8.8-050808-generic             <none>                       <none>   [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
un  linux-image-5.9.0-050900rc2-generic          <none>                       <none>   [COLOR=#ffffff]>[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#ffffff]lines 1-30[/COLOR][COLOR=#000000]...skipping...[/COLOR]
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                         Version                      Architecture Description
+++-============================================-============================-============-==============================================================
ii  linux-base                                   4.5ubuntu3.1                 all          Linux image base package
un  linux-doc                                    <none>                       <none>       (no description available)
un  linux-doc-5.9.0                              <none>                       <none>       (no description available)
ii  linux-firmware                               1.187.3                      all          Firmware for Linux kernel drivers
un  linux-firmware-raspi2                        <none>                       <none>       (no description available)
un  linux-firmware-snapdragon                    <none>                       <none>       (no description available)
un  linux-headers                                <none>                       <none>       (no description available)
un  linux-headers-3.0                            <none>                       <none>       (no description available)
ii  linux-headers-5.8.7-050807                   5.8.7-050807.202009051031    all          Header files related to Linux kernel version 5.8.7
ii  linux-headers-5.8.7-050807-generic           5.8.7-050807.202009051031    amd64        Linux kernel headers for version 5.8.7 on 64 bit x86 SMP
ii  linux-headers-5.8.8-050808                   5.8.8-050808.202009091435    all          Header files related to Linux kernel version 5.8.8
ii  linux-headers-5.8.8-050808-generic           5.8.8-050808.202009091435    amd64        Linux kernel headers for version 5.8.8 on 64 bit x86 SMP
ii  linux-headers-5.9.0-050900rc2                5.9.0-050900rc2.202008232232 all          Header files related to Linux kernel version 5.9.0
ii  linux-headers-5.9.0-050900rc2-generic        5.9.0-050900rc2.202008232232 amd64        Linux kernel headers for version 5.9.0 on 64 bit x86 SMP
ii  linux-headers-5.9.0-050900rc3                5.9.0-050900rc3.202008302030 all          Header files related to Linux kernel version 5.9.0
ii  linux-headers-5.9.0-050900rc3-generic        5.9.0-050900rc3.202008302030 amd64        Linux kernel headers for version 5.9.0 on 64 bit x86 SMP
ii  linux-headers-5.9.0-050900rc4                5.9.0-050900rc4.202009070130 all          Header files related to Linux kernel version 5.9.0
ii  linux-headers-5.9.0-050900rc4-generic        5.9.0-050900rc4.202009070130 amd64        Linux kernel headers for version 5.9.0 on 64 bit x86 SMP
un  linux-headers-686-pae                        <none>                       <none>       (no description available)
un  linux-headers-amd64                          <none>                       <none>       (no description available)
un  linux-headers-generic                        <none>                       <none>       (no description available)
un  linux-image                                  <none>                       <none>       (no description available)
un  linux-image-5.8.7-050807-generic             <none>                       <none>       (no description available)
un  linux-image-5.8.8-050808-generic             <none>                       <none>       (no description available)
un  linux-image-5.9.0-050900rc2-generic          <none>                       <none>       (no description available)
un  linux-image-5.9.0-050900rc3-generic          <none>                       <none>       (no description available)
un  linux-image-5.9.0-050900rc4-generic          <none>                       <none>       (no description available)
iU  linux-image-unsigned-5.8.7-050807-generic    5.8.7-050807.202009051031    amd64        Linux kernel image for version 5.8.7 on 64 bit x86 SMP
ii  linux-image-unsigned-5.8.8-050808-generic    5.8.8-050808.202009091435    amd64        Linux kernel image for version 5.8.8 on 64 bit x86 SMP
ii  linux-image-unsigned-5.9.0-050900rc2-generic 5.9.0-050900rc2.202008232232 amd64        Linux kernel image for version 5.9.0 on 64 bit x86 SMP
ii  linux-image-unsigned-5.9.0-050900rc3-generic 5.9.0-050900rc3.202008302030 amd64        Linux kernel image for version 5.9.0 on 64 bit x86 SMP
ii  linux-image-unsigned-5.9.0-050900rc4-generic 5.9.0-050900rc4.202009070130 amd64        Linux kernel image for version 5.9.0 on 64 bit x86 SMP
un  linux-initramfs-tool                         <none>                       <none>       (no description available)
un  linux-kernel-headers                         <none>                       <none>       (no description available)
un  linux-kernel-log-daemon                      <none>                       <none>       (no description available)
ii  linux-libc-dev:amd64                         5.4.0-47.51                  amd64        Linux Kernel Headers for development
iHR linux-modules-5.8.7-050807-generic           5.8.7-050807.202009051031    amd64        (no description available)
ii  linux-modules-5.8.8-050808-generic           5.8.8-050808.202009091435    amd64        Linux kernel extra modules for version 5.8.8 on 64 bit x86 SMP
ii  linux-modules-5.9.0-050900rc2-generic        5.9.0-050900rc2.202008232232 amd64        Linux kernel extra modules for version 5.9.0 on 64 bit x86 SMP
ii  linux-modules-5.9.0-050900rc3-generic        5.9.0-050900rc3.202008302030 amd64        Linux kernel extra modules for version 5.9.0 on 64 bit x86 SMP
ii  linux-modules-5.9.0-050900rc4-generic        5.9.0-050900rc4.202009070130 amd64        Linux kernel extra modules for version 5.9.0 on 64 bit x86 SMP
un  linux-restricted-common                      <none>                       <none>       (no description available)
ii  linux-sound-base                             1.0.25+dfsg-0ubuntu5         all          base package for ALSA and OSS sound systems
un  linux-source-5.8.7                           <none>                       <none>       (no description available)
un  linux-source-5.8.8                           <none>                       <none>       (no description available)
un  linux-source-5.9.0                           <none>                       <none>       (no description available)
un  linux-tools                                  <none>                       <none>       (no description available)

[/FONT][FONT=monospace]
[/FONT]
```

---

### Post by deadflowr on 2020-09-11
So have you tried grabbing the package from the mainline archives I linked to?
I would try a reinstall first, if possible.
otherwise removal can be quite a task.
See:[https://askubuntu.com/questions/148715/how-to-fix-package-is-in-a-very-bad-inconsistent-state-error]("https://askubuntu.com/questions/148715/how-to-fix-package-is-in-a-very-bad-inconsistent-state-error")

FWIW, to be clear you want this package: linux-modules-5.8.7-050807-generic

---

