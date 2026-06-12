---
title: "Issue with initramfs."
date: 2022-02-25
forum: General Help
---

### Post by pavloos on 2022-02-25
Hi, I can not upgrade nor autoremove old kernels due to the issue with initramfs. It keeps returning me the following


```
pawel@V5-591G:~$ sudo apt-get --purge autoremoveReading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 67 not to upgrade.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-5.13.0-30-generic (5.13.0-30.33~20.04.1) ...
Setting up initramfs-tools (0.136ubuntu6.6) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for linux-image-5.13.0-30-generic (5.13.0-30.33~20.04.1) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.13.0-30-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.13.0-30-generic
I: The initramfs will attempt to resume from /dev/dm-1
I: (/dev/mapper/system-swap)
I: Set the RESUME variable to override this.
Error 24 : Write error : cannot write compressed block 
E: mkinitramfs failure cpio 141 lz4 -9 -l 24
update-initramfs: failed for /boot/initrd.img-5.13.0-30-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-5.13.0-30-generic (--configure):
 installed linux-image-5.13.0-30-generic package post-installation script subprocess returned error exit status 1
Processing triggers for initramfs-tools (0.136ubuntu6.6) ...
update-initramfs: Generating /boot/initrd.img-5.13.0-28-generic
I: The initramfs will attempt to resume from /dev/dm-1
I: (/dev/mapper/system-swap)
I: Set the RESUME variable to override this.
Error 24 : Write error : cannot write compressed block 
E: mkinitramfs failure cpio 141 lz4 -9 -l 24
update-initramfs: failed for /boot/initrd.img-5.13.0-28-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 installed initramfs-tools package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-5.13.0-30-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


I tried updateing/removing via Synaptic and it returns the same


```
E: initramfs-tools: installed initramfs-tools package post-installation script subprocess returned error exit status 1E: linux-image-5.13.0-30-generic: installed linux-image-5.13.0-30-generic package post-installation script subprocess returned error exit status 1
```


Can anyone help mw with this issue? I have encrypred boot partition. I run Ubuntu 20.04.4 LTS

---

### Post by Bashing-om on 2022-02-25
pavloos; Yukkie :(

Not much yet to work with,

Let's see what we can discover.

Disk space ? - while I would expect the kernel to say so will not hurt to check and see what we have:
```

df -h

```

And what is the state of the installed kernels:
```

uname -r
dpkg -l | grep linux-

```

[INDENT]if the kernel is not happy ,,,,
[INDENT][INDENT][INDENT]no one is happy
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pavloos on 2022-02-26
Hello,

thank you for your willingness to look into it. So:

```
pawel@V5-591G:~$ df -h
Filesystem               Size  Used Avail Use% Mounted on
udev                     7,7G     0  7,7G   0% /dev
tmpfs                    1,6G  2,4M  1,6G   1% /run
/dev/mapper/system-root   35G   31G  2,4G  93% /
tmpfs                    7,8G  142M  7,7G   2% /dev/shm
tmpfs                    5,0M  4,0K  5,0M   1% /run/lock
tmpfs                    7,8G     0  7,8G   0% /sys/fs/cgroup
/dev/loop0               128K  128K     0 100% /snap/acrordrdc/62
/dev/loop2               187M  187M     0 100% /snap/audacity/934
/dev/loop1               128K  128K     0 100% /snap/acrordrdc/53
/dev/loop3                56M   56M     0 100% /snap/core18/2253
/dev/loop4               128K  128K     0 100% /snap/bare/5
/dev/loop6                56M   56M     0 100% /snap/core18/2284
/dev/loop7               111M  111M     0 100% /snap/core/12725
/dev/loop8               278M  278M     0 100% /snap/gimp/380
/dev/loop9               165M  165M     0 100% /snap/gnome-3-28-1804/161
/dev/loop10              304M  304M     0 100% /snap/wine-platform-5-stable/16
/dev/loop11              163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop12              392M  392M     0 100% /snap/gimp/383
/dev/loop13              219M  219M     0 100% /snap/gnome-3-34-1804/72
/dev/loop14               63M   63M     0 100% /snap/okular/108
/dev/loop15              304M  304M     0 100% /snap/wine-platform-5-stable/18
/dev/loop16              248M  248M     0 100% /snap/gnome-3-38-2004/87
/dev/loop17              190M  190M     0 100% /snap/inkscape/9866
/dev/loop18              3,0M  3,0M     0 100% /snap/ksnip/386
/dev/loop19              151M  151M     0 100% /snap/okular/109
/dev/loop20              274M  274M     0 100% /snap/wps-office-multilang/1
/dev/loop21              256K  256K     0 100% /snap/gtk2-common-themes/13
/dev/loop22              320M  320M     0 100% /snap/kde-frameworks-5-qt-5-15-3-core20/7
/dev/loop23               55M   55M     0 100% /snap/snap-store/558
/dev/loop24              170M  170M     0 100% /snap/digikam/50
/dev/loop25              347M  347M     0 100% /snap/wine-platform-runtime/286
/dev/loop26               66M   66M     0 100% /snap/gtk-common-themes/1515
/dev/loop27               83M   83M     0 100% /snap/scrcpy/371
/dev/loop28              600M  600M     0 100% /snap/scummvm/5639
/dev/loop29               62M   62M     0 100% /snap/core20/1328
/dev/loop30              425M  425M     0 100% /snap/kde-frameworks-5-qt-5-15-3-core20/8
/dev/loop31              323M  323M     0 100% /snap/wine-platform-6-stable/8
/dev/loop32               62M   62M     0 100% /snap/core20/1361
/dev/loop33              145M  145M     0 100% /snap/notepadqq/855
/dev/loop34               44M   44M     0 100% /snap/snapd/14978
/dev/loop35              187M  187M     0 100% /snap/inkscape/9711
/dev/loop36               66M   66M     0 100% /snap/gtk-common-themes/1519
/dev/loop37              324M  324M     0 100% /snap/kde-frameworks-5-qt-5-15-core20/14
/dev/loop38              168M  168M     0 100% /snap/spotify/56
/dev/loop39              249M  249M     0 100% /snap/gnome-3-38-2004/99
/dev/loop40              112M  112M     0 100% /snap/shutter/27
/dev/loop41               51M   51M     0 100% /snap/snap-store/547
/dev/loop42              3,0M  3,0M     0 100% /snap/ksnip/407
/dev/loop43              323M  323M     0 100% /snap/wine-platform-6-stable/14
/dev/loop44              600M  600M     0 100% /snap/scummvm/5694
/dev/loop45              347M  347M     0 100% /snap/wine-platform-runtime/285
/dev/loop46              261M  261M     0 100% /snap/kde-frameworks-5-core18/32
/dev/loop47               83M   83M     0 100% /snap/scrcpy/364
/dev/loop48              219M  219M     0 100% /snap/gnome-3-34-1804/77
/dev/loop49              169M  169M     0 100% /snap/spotify/57
/dev/loop50              135M  135M     0 100% /snap/skype/197
/dev/loop51              135M  135M     0 100% /snap/skype/200
/dev/loop52              291M  291M     0 100% /snap/kde-frameworks-5-qt-5-14-core18/4
/dev/loop53              171M  171M     0 100% /snap/digikam/51
/dev/mapper/system-home  169G  141G   20G  88% /home
/dev/sda1                235G  146G   77G  66% /mnt/24d8e4bc-b711-4c2e-acb8-81e4a6cc6c72
/dev/sdb1                472M  363M   85M  82% /boot
tmpfs                    1,6G   32K  1,6G   1% /run/user/125
tmpfs                    1,6G  5,4M  1,6G   1% /run/user/1000
/dev/loop54              187M  187M     0 100% /snap/audacity/971

```


The next one:
```
pawel@V5-591G:~$ uname -r5.13.0-28-generic
```

And the last one:
```
pawel@V5-591G:~$ dpkg -l | grep linux-ii  binutils-x86-64-linux-gnu                     2.34-6ubuntu1.3                            amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                                    4.5ubuntu3.7                               all          Linux image base package
iF  linux-firmware                                1.187.26                                   all          Firmware for Linux kernel drivers
ii  linux-generic-hwe-20.04                       5.13.0.30.33~20.04.17                      amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.11.0-44-generic               5.11.0-44.48~20.04.2                       amd64        Linux kernel headers for version 5.11.0 on 64 bit x86 SMP
ii  linux-headers-5.13.0-28-generic               5.13.0-28.31~20.04.1                       amd64        Linux kernel headers for version 5.13.0 on 64 bit x86 SMP
ii  linux-headers-5.13.0-30-generic               5.13.0-30.33~20.04.1                       amd64        Linux kernel headers for version 5.13.0 on 64 bit x86 SMP
ii  linux-headers-5.8.0-63-generic                5.8.0-63.71~20.04.1                        amd64        Linux kernel headers for version 5.8.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-20.04               5.13.0.30.33~20.04.17                      amd64        Generic Linux kernel headers
ii  linux-hwe-5.11-headers-5.11.0-44              5.11.0-44.48~20.04.2                       all          Header files related to Linux kernel version 5.11.0
ii  linux-hwe-5.13-headers-5.13.0-28              5.13.0-28.31~20.04.1                       all          Header files related to Linux kernel version 5.13.0
ii  linux-hwe-5.13-headers-5.13.0-30              5.13.0-30.33~20.04.1                       all          Header files related to Linux kernel version 5.13.0
ii  linux-hwe-5.8-headers-5.8.0-63                5.8.0-63.71~20.04.1                        all          Header files related to Linux kernel version 5.8.0
rc  linux-image-5.11.0-25-generic                 5.11.0-25.27~20.04.1                       amd64        Signed kernel image generic
rc  linux-image-5.11.0-27-generic                 5.11.0-27.29~20.04.1                       amd64        Signed kernel image generic
rc  linux-image-5.11.0-34-generic                 5.11.0-34.36~20.04.1                       amd64        Signed kernel image generic
rc  linux-image-5.11.0-36-generic                 5.11.0-36.40~20.04.1                       amd64        Signed kernel image generic
rc  linux-image-5.11.0-37-generic                 5.11.0-37.41~20.04.2                       amd64        Signed kernel image generic
rc  linux-image-5.11.0-38-generic                 5.11.0-38.42~20.04.1                       amd64        Signed kernel image generic
rc  linux-image-5.11.0-40-generic                 5.11.0-40.44~20.04.2                       amd64        Signed kernel image generic
rc  linux-image-5.11.0-41-generic                 5.11.0-41.45~20.04.1                       amd64        Signed kernel image generic
rc  linux-image-5.11.0-43-generic                 5.11.0-43.47~20.04.2                       amd64        Signed kernel image generic
ii  linux-image-5.11.0-44-generic                 5.11.0-44.48~20.04.2                       amd64        Signed kernel image generic
ii  linux-image-5.13.0-28-generic                 5.13.0-28.31~20.04.1                       amd64        Signed kernel image generic
iF  linux-image-5.13.0-30-generic                 5.13.0-30.33~20.04.1                       amd64        Signed kernel image generic
rc  linux-image-5.4.0-42-generic                  5.4.0-42.46                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-45-generic                  5.4.0-45.49                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-47-generic                  5.4.0-47.51                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-48-generic                  5.4.0-48.52                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-52-generic                  5.4.0-52.57                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-53-generic                  5.4.0-53.59                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-54-generic                  5.4.0-54.60                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-56-generic                  5.4.0-56.62                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-58-generic                  5.4.0-58.64                                amd64        Signed kernel image generic
rc  linux-image-5.8.0-38-generic                  5.8.0-38.43~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.8.0-41-generic                  5.8.0-41.46~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.8.0-43-generic                  5.8.0-43.49~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.8.0-44-generic                  5.8.0-44.50~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.8.0-45-generic                  5.8.0-45.51~20.04.1+1                      amd64        Signed kernel image generic
rc  linux-image-5.8.0-48-generic                  5.8.0-48.54~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.8.0-50-generic                  5.8.0-50.56~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.8.0-53-generic                  5.8.0-53.60~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.8.0-55-generic                  5.8.0-55.62~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.8.0-59-generic                  5.8.0-59.66~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.8.0-63-generic                  5.8.0-63.71~20.04.1                        amd64        Signed kernel image generic
ii  linux-image-generic-hwe-20.04                 5.13.0.30.33~20.04.17                      amd64        Generic Linux kernel image
rc  linux-image-unsigned-5.8.0-36-generic         5.8.0-36.40~20.04.1                        amd64        Linux kernel image for version 5.8.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                          5.4.0-100.113                              amd64        Linux Kernel Headers for development
rc  linux-modules-5.11.0-25-generic               5.11.0-25.27~20.04.1                       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-5.11.0-27-generic               5.11.0-27.29~20.04.1                       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-5.11.0-34-generic               5.11.0-34.36~20.04.1                       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-5.11.0-36-generic               5.11.0-36.40~20.04.1                       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-5.11.0-37-generic               5.11.0-37.41~20.04.2                       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-5.11.0-38-generic               5.11.0-38.42~20.04.1                       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-5.11.0-40-generic               5.11.0-40.44~20.04.2                       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-5.11.0-41-generic               5.11.0-41.45~20.04.1                       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-5.11.0-43-generic               5.11.0-43.47~20.04.2                       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
ii  linux-modules-5.11.0-44-generic               5.11.0-44.48~20.04.2                       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
ii  linux-modules-5.13.0-28-generic               5.13.0-28.31~20.04.1                       amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
ii  linux-modules-5.13.0-30-generic               5.13.0-30.33~20.04.1                       amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-42-generic                5.4.0-42.46                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-45-generic                5.4.0-45.49                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-47-generic                5.4.0-47.51                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-48-generic                5.4.0-48.52                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-52-generic                5.4.0-52.57                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-53-generic                5.4.0-53.59                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-54-generic                5.4.0-54.60                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-56-generic                5.4.0-56.62                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-58-generic                5.4.0-58.64                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-59-generic                5.4.0-59.65                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.8.0-38-generic                5.8.0-38.43~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-5.8.0-41-generic                5.8.0-41.46~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-5.8.0-43-generic                5.8.0-43.49~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-5.8.0-44-generic                5.8.0-44.50~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-5.8.0-45-generic                5.8.0-45.51~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-5.8.0-48-generic                5.8.0-48.54~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-5.8.0-50-generic                5.8.0-50.56~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-5.8.0-53-generic                5.8.0-53.60~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-5.8.0-55-generic                5.8.0-55.62~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-5.8.0-59-generic                5.8.0-59.66~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.11.0-25-generic         5.11.0-25.27~20.04.1                       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.11.0-27-generic         5.11.0-27.29~20.04.1                       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.11.0-34-generic         5.11.0-34.36~20.04.1                       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.11.0-36-generic         5.11.0-36.40~20.04.1                       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.11.0-37-generic         5.11.0-37.41~20.04.2                       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.11.0-38-generic         5.11.0-38.42~20.04.1                       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.11.0-40-generic         5.11.0-40.44~20.04.2                       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.11.0-41-generic         5.11.0-41.45~20.04.1                       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.11.0-43-generic         5.11.0-43.47~20.04.2                       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.11.0-44-generic         5.11.0-44.48~20.04.2                       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.13.0-28-generic         5.13.0-28.31~20.04.1                       amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.13.0-30-generic         5.13.0-30.33~20.04.1                       amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-42-generic          5.4.0-42.46                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-45-generic          5.4.0-45.49                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-47-generic          5.4.0-47.51                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-48-generic          5.4.0-48.52                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-52-generic          5.4.0-52.57                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-53-generic          5.4.0-53.59                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-54-generic          5.4.0-54.60                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-56-generic          5.4.0-56.62                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-58-generic          5.4.0-58.64                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-59-generic          5.4.0-59.65                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.8.0-36-generic          5.8.0-36.40~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.8.0-38-generic          5.8.0-38.43~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.8.0-41-generic          5.8.0-41.46~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.8.0-43-generic          5.8.0-43.49~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.8.0-44-generic          5.8.0-44.50~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.8.0-45-generic          5.8.0-45.51~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.8.0-48-generic          5.8.0-48.54~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.8.0-50-generic          5.8.0-50.56~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.8.0-53-generic          5.8.0-53.60~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.8.0-55-generic          5.8.0-55.62~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.8.0-59-generic          5.8.0-59.66~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.8.0-63-generic          5.8.0-63.71~20.04.1                        amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5                       all          base package for ALSA and OSS sound systems
ii  syslinux-common                               3:6.04~git20190206.bf6db5b4+dfsg1-2        all          collection of bootloaders (common)
ii  syslinux-legacy                               2:3.63+dfsg-2ubuntu9                       amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Bashing-om on 2022-02-26
pavloos; Hey hey -

Making progress :D

We have:
> 
[color=red]iF[/color]  linux-image-5.13.0-30-generic

inpish release :D
where the kernel is installed (i) BUT the status (F) is "halF-conf"-igured.

How about we start with cleaning up the cruft (rc) where the package has been (r)emoved, but (c)onfig files remain,
```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```

Next is to see if the package manager will heal its self - keep this as simple as possible :D
```

sudo apt update
sudo apt full-upgrade
sudo dpkg --configure -a

```
see if that latest linux-image-5.13.0-30-generic will complete installation.

while we are poking about:
"iF  linux-firmware"
will also require some TLC

[INDENT]how these go is
[INDENT][INDENT]what we do next
[/INDENT][/INDENT][/INDENT]

---

### Post by pavloos on 2022-02-27
HI,

possible something in the code is a good thing but it still end with informing me that errors were encountered. Below what I receive

```
pawel@V5-591G:~$ dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P[sudo] password for pawel: 
(Reading database ... 335877 files and directories currently installed.)
Purging configuration files for hplip-gui (3.20.3+dfsg0-2) ...
Purging configuration files for libnvidia-compute-450:amd64 (460.80-0ubuntu0.20.04.2) ...
Purging configuration files for libnvidia-compute-460:amd64 (460.91.03-0ubuntu0.20.04.1) ...
Purging configuration files for libnvidia-compute-495:amd64 (510.47.03-0ubuntu0.20.04.1) ...
Purging configuration files for libsane-hpaio:amd64 (3.20.3+dfsg0-2) ...
dpkg: warning: while removing libsane-hpaio:amd64, directory '/usr/share/hplip' not empty so not removed
Purging configuration files for linux-image-5.11.0-25-generic (5.11.0-25.27~20.04.1) ...
Purging configuration files for linux-image-5.11.0-27-generic (5.11.0-27.29~20.04.1) ...
Purging configuration files for linux-image-5.11.0-34-generic (5.11.0-34.36~20.04.1) ...
Purging configuration files for linux-image-5.11.0-36-generic (5.11.0-36.40~20.04.1) ...
Purging configuration files for linux-image-5.11.0-37-generic (5.11.0-37.41~20.04.2) ...
Purging configuration files for linux-image-5.11.0-38-generic (5.11.0-38.42~20.04.1) ...
Purging configuration files for linux-image-5.11.0-40-generic (5.11.0-40.44~20.04.2) ...
Purging configuration files for linux-image-5.11.0-41-generic (5.11.0-41.45~20.04.1) ...
Purging configuration files for linux-image-5.11.0-43-generic (5.11.0-43.47~20.04.2) ...
Purging configuration files for linux-image-5.4.0-42-generic (5.4.0-42.46) ...
Purging configuration files for linux-image-5.4.0-45-generic (5.4.0-45.49) ...
Purging configuration files for linux-image-5.4.0-47-generic (5.4.0-47.51) ...
Purging configuration files for linux-image-5.4.0-48-generic (5.4.0-48.52) ...
Purging configuration files for linux-image-5.4.0-52-generic (5.4.0-52.57) ...
Purging configuration files for linux-image-5.4.0-53-generic (5.4.0-53.59) ...
Purging configuration files for linux-image-5.4.0-54-generic (5.4.0-54.60) ...
Purging configuration files for linux-image-5.4.0-56-generic (5.4.0-56.62) ...
Purging configuration files for linux-image-5.4.0-58-generic (5.4.0-58.64) ...
Purging configuration files for linux-image-5.8.0-38-generic (5.8.0-38.43~20.04.1) ...
rmdir: failed to remove '/lib/modules/5.8.0-38-generic': Directory not empty
Purging configuration files for linux-image-5.8.0-41-generic (5.8.0-41.46~20.04.1) ...
rmdir: failed to remove '/lib/modules/5.8.0-41-generic': Directory not empty
Purging configuration files for linux-image-5.8.0-43-generic (5.8.0-43.49~20.04.1) ...
rmdir: failed to remove '/lib/modules/5.8.0-43-generic': Directory not empty
Purging configuration files for linux-image-5.8.0-44-generic (5.8.0-44.50~20.04.1) ...
rmdir: failed to remove '/lib/modules/5.8.0-44-generic': Directory not empty
Purging configuration files for linux-image-5.8.0-45-generic (5.8.0-45.51~20.04.1+1) ...
rmdir: failed to remove '/lib/modules/5.8.0-45-generic': Directory not empty
Purging configuration files for linux-image-5.8.0-48-generic (5.8.0-48.54~20.04.1) ...
rmdir: failed to remove '/lib/modules/5.8.0-48-generic': Directory not empty
Purging configuration files for linux-image-5.8.0-50-generic (5.8.0-50.56~20.04.1) ...
rmdir: failed to remove '/lib/modules/5.8.0-50-generic': Directory not empty
Purging configuration files for linux-image-5.8.0-53-generic (5.8.0-53.60~20.04.1) ...
rmdir: failed to remove '/lib/modules/5.8.0-53-generic': Directory not empty
Purging configuration files for linux-image-5.8.0-55-generic (5.8.0-55.62~20.04.1) ...
rmdir: failed to remove '/lib/modules/5.8.0-55-generic': Directory not empty
Purging configuration files for linux-image-5.8.0-59-generic (5.8.0-59.66~20.04.1) ...
rmdir: failed to remove '/lib/modules/5.8.0-59-generic': Directory not empty
Purging configuration files for linux-image-5.8.0-63-generic (5.8.0-63.71~20.04.1) ...
rmdir: failed to remove '/lib/modules/5.8.0-63-generic': Directory not empty
Purging configuration files for linux-image-unsigned-5.8.0-36-generic (5.8.0-36.40~20.04.1) ...
rmdir: failed to remove '/lib/modules/5.8.0-36-generic': Directory not empty
Purging configuration files for linux-modules-5.11.0-25-generic (5.11.0-25.27~20.04.1) ...
Purging configuration files for linux-modules-5.11.0-27-generic (5.11.0-27.29~20.04.1) ...
Purging configuration files for linux-modules-5.11.0-34-generic (5.11.0-34.36~20.04.1) ...
Purging configuration files for linux-modules-5.11.0-36-generic (5.11.0-36.40~20.04.1) ...
Purging configuration files for linux-modules-5.11.0-37-generic (5.11.0-37.41~20.04.2) ...
Purging configuration files for linux-modules-5.11.0-38-generic (5.11.0-38.42~20.04.1) ...
Purging configuration files for linux-modules-5.11.0-40-generic (5.11.0-40.44~20.04.2) ...
Purging configuration files for linux-modules-5.11.0-41-generic (5.11.0-41.45~20.04.1) ...
Purging configuration files for linux-modules-5.11.0-43-generic (5.11.0-43.47~20.04.2) ...
Purging configuration files for linux-modules-5.4.0-42-generic (5.4.0-42.46) ...
Purging configuration files for linux-modules-5.4.0-45-generic (5.4.0-45.49) ...
Purging configuration files for linux-modules-5.4.0-47-generic (5.4.0-47.51) ...
Purging configuration files for linux-modules-5.4.0-48-generic (5.4.0-48.52) ...
Purging configuration files for linux-modules-5.4.0-52-generic (5.4.0-52.57) ...
Purging configuration files for linux-modules-5.4.0-53-generic (5.4.0-53.59) ...
Purging configuration files for linux-modules-5.4.0-54-generic (5.4.0-54.60) ...
Purging configuration files for linux-modules-5.4.0-56-generic (5.4.0-56.62) ...
Purging configuration files for linux-modules-5.4.0-58-generic (5.4.0-58.64) ...
Purging configuration files for linux-modules-5.4.0-59-generic (5.4.0-59.65) ...
Purging configuration files for linux-modules-5.8.0-38-generic (5.8.0-38.43~20.04.1) ...
Purging configuration files for linux-modules-5.8.0-41-generic (5.8.0-41.46~20.04.1) ...
dpkg: warning: while removing linux-modules-5.8.0-41-generic, directory '/lib/modules/5.8.0-41-generic' not empty so not removed
Purging configuration files for linux-modules-5.8.0-43-generic (5.8.0-43.49~20.04.1) ...
Purging configuration files for linux-modules-5.8.0-44-generic (5.8.0-44.50~20.04.1) ...
Purging configuration files for linux-modules-5.8.0-45-generic (5.8.0-45.51~20.04.1) ...
Purging configuration files for linux-modules-5.8.0-48-generic (5.8.0-48.54~20.04.1) ...
Purging configuration files for linux-modules-5.8.0-50-generic (5.8.0-50.56~20.04.1) ...
Purging configuration files for linux-modules-5.8.0-53-generic (5.8.0-53.60~20.04.1) ...
Purging configuration files for linux-modules-5.8.0-55-generic (5.8.0-55.62~20.04.1) ...
dpkg: warning: while removing linux-modules-5.8.0-55-generic, directory '/lib/modules/5.8.0-55-generic' not empty so not removed
Purging configuration files for linux-modules-5.8.0-59-generic (5.8.0-59.66~20.04.1) ...
dpkg: warning: while removing linux-modules-5.8.0-59-generic, directory '/lib/modules/5.8.0-59-generic' not empty so not removed
Purging configuration files for linux-modules-extra-5.11.0-25-generic (5.11.0-25.27~20.04.1) ...
Purging configuration files for linux-modules-extra-5.11.0-27-generic (5.11.0-27.29~20.04.1) ...
Purging configuration files for linux-modules-extra-5.11.0-34-generic (5.11.0-34.36~20.04.1) ...
Purging configuration files for linux-modules-extra-5.11.0-36-generic (5.11.0-36.40~20.04.1) ...
Purging configuration files for linux-modules-extra-5.11.0-37-generic (5.11.0-37.41~20.04.2) ...
Purging configuration files for linux-modules-extra-5.11.0-38-generic (5.11.0-38.42~20.04.1) ...
Purging configuration files for linux-modules-extra-5.11.0-40-generic (5.11.0-40.44~20.04.2) ...
Purging configuration files for linux-modules-extra-5.11.0-41-generic (5.11.0-41.45~20.04.1) ...
Purging configuration files for linux-modules-extra-5.11.0-43-generic (5.11.0-43.47~20.04.2) ...
Purging configuration files for linux-modules-extra-5.4.0-42-generic (5.4.0-42.46) ...
Purging configuration files for linux-modules-extra-5.4.0-45-generic (5.4.0-45.49) ...
Purging configuration files for linux-modules-extra-5.4.0-47-generic (5.4.0-47.51) ...
Purging configuration files for linux-modules-extra-5.4.0-48-generic (5.4.0-48.52) ...
Purging configuration files for linux-modules-extra-5.4.0-52-generic (5.4.0-52.57) ...
Purging configuration files for linux-modules-extra-5.4.0-53-generic (5.4.0-53.59) ...
Purging configuration files for linux-modules-extra-5.4.0-54-generic (5.4.0-54.60) ...
Purging configuration files for linux-modules-extra-5.4.0-56-generic (5.4.0-56.62) ...
Purging configuration files for linux-modules-extra-5.4.0-58-generic (5.4.0-58.64) ...
Purging configuration files for linux-modules-extra-5.4.0-59-generic (5.4.0-59.65) ...
Purging configuration files for linux-modules-extra-5.8.0-36-generic (5.8.0-36.40~20.04.1) ...
Purging configuration files for linux-modules-extra-5.8.0-38-generic (5.8.0-38.43~20.04.1) ...
Purging configuration files for linux-modules-extra-5.8.0-41-generic (5.8.0-41.46~20.04.1) ...
Purging configuration files for linux-modules-extra-5.8.0-43-generic (5.8.0-43.49~20.04.1) ...
Purging configuration files for linux-modules-extra-5.8.0-44-generic (5.8.0-44.50~20.04.1) ...
Purging configuration files for linux-modules-extra-5.8.0-45-generic (5.8.0-45.51~20.04.1) ...
Purging configuration files for linux-modules-extra-5.8.0-48-generic (5.8.0-48.54~20.04.1) ...
Purging configuration files for linux-modules-extra-5.8.0-50-generic (5.8.0-50.56~20.04.1) ...
Purging configuration files for linux-modules-extra-5.8.0-53-generic (5.8.0-53.60~20.04.1) ...
Purging configuration files for linux-modules-extra-5.8.0-55-generic (5.8.0-55.62~20.04.1) ...
Purging configuration files for linux-modules-extra-5.8.0-59-generic (5.8.0-59.66~20.04.1) ...
Purging configuration files for linux-modules-extra-5.8.0-63-generic (5.8.0-63.71~20.04.1) ...
Purging configuration files for nautilus-dropbox (2019.02.14-1ubuntu1) ...
Purging configuration files for nvidia-compute-utils-460 (460.91.03-0ubuntu0.20.04.1) ...
userdel: user nvidia-persistenced is currently used by process 1779
Purging configuration files for nvidia-dkms-460 (460.91.03-0ubuntu0.20.04.1) ...
update-initramfs: deferring update (trigger activated)
Purging configuration files for nvidia-kernel-common-460 (460.91.03-0ubuntu0.20.04.1) ...
update-initramfs: deferring update (trigger activated)
Purging configuration files for ubuntu-tweak (0.8.7-1~trusty2) ...
Purging configuration files for virtualbox (6.1.10-dfsg-1~ubuntu1.20.04.1) ...
Purging configuration files for virtualbox-qt (6.1.10-dfsg-1~ubuntu1.20.04.1) ...
Processing triggers for dbus (1.12.16-2ubuntu2.1) ...
Processing triggers for systemd (245.4-4ubuntu3.15) ...

```

```
pawel@V5-591G:~$ sudo apt update
Hit:1 http://ppa.launchpad.net/linrunner/tlp/ubuntu focal InRelease
Hit:2 http://pl.archive.ubuntu.com/ubuntu focal InRelease                                                                                                                                      
Hit:3 http://pl.archive.ubuntu.com/ubuntu focal-updates InRelease                                                                                                                              
Ign:4 http://linux.dropbox.com/ubuntu disco InRelease                                                                                                                                          
Get:5 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]                                                                        
Hit:6 http://pl.archive.ubuntu.com/ubuntu focal-backports InRelease                                                                                                     
Hit:7 http://dl.google.com/linux/chrome/deb stable InRelease                                                                                                            
Hit:8 http://linux.dropbox.com/ubuntu disco Release                                                                                                 
Ign:9 http://repo.vivaldi.com/stable/deb stable InRelease                                                                     
Hit:10 http://repo.vivaldi.com/stable/deb stable Release                                                
Get:11 https://dl.winehq.org/wine-builds/ubuntu focal InRelease [8&#8239;041 B]                               
Get:14 https://dl.winehq.org/wine-builds/ubuntu focal/main i386 Packages [314 kB]
Get:15 http://security.ubuntu.com/ubuntu focal-security/main amd64 DEP-11 Metadata [40,7 kB]
Get:16 http://security.ubuntu.com/ubuntu focal-security/universe amd64 DEP-11 Metadata [66,3 kB]
Get:17 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 DEP-11 Metadata [2&#8239;464 B]
Get:18 https://dl.winehq.org/wine-builds/ubuntu focal/main amd64 Packages [312 kB]                                                                                                                                
Fetched 858 kB in 11s (79,1 kB/s)                                                                                                                                                                                 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up-to-date.
```

```
pawel@V5-591G:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-image-5.13.0-30-generic (5.13.0-30.33~20.04.1) ...
I: /boot/initrd.img is now a symlink to initrd.img-5.13.0-30-generic
Setting up initramfs-tools (0.136ubuntu6.7) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-firmware (1.187.26) ...
update-initramfs: Generating /boot/initrd.img-5.13.0-28-generic
I: The initramfs will attempt to resume from /dev/dm-1
I: (/dev/mapper/system-swap)
I: Set the RESUME variable to override this.
Error 24 : Write error : cannot write compressed block 
E: mkinitramfs failure cpio 141 lz4 -9 -l 24
update-initramfs: failed for /boot/initrd.img-5.13.0-28-generic with 1.
dpkg: error processing package linux-firmware (--configure):
 installed linux-firmware package post-installation script subprocess returned error exit status 1
Processing triggers for linux-image-5.13.0-30-generic (5.13.0-30.33~20.04.1) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.13.0-30-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.13.0-30-generic
I: The initramfs will attempt to resume from /dev/dm-1
I: (/dev/mapper/system-swap)
I: Set the RESUME variable to override this.
Error 24 : Write error : cannot write compressed block 
E: mkinitramfs failure cpio 141 lz4 -9 -l 24
update-initramfs: failed for /boot/initrd.img-5.13.0-30-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-5.13.0-30-generic (--configure):
 installed linux-image-5.13.0-30-generic package post-installation script subprocess returned error exit status 1
Processing triggers for initramfs-tools (0.136ubuntu6.7) ...
update-initramfs: Generating /boot/initrd.img-5.13.0-28-generic
I: The initramfs will attempt to resume from /dev/dm-1
I: (/dev/mapper/system-swap)
I: Set the RESUME variable to override this.
Error 24 : Write error : cannot write compressed block 
E: mkinitramfs failure cpio 141 lz4 -9 -l 24
update-initramfs: failed for /boot/initrd.img-5.13.0-28-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 installed initramfs-tools package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-firmware
 linux-image-5.13.0-30-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```
pawel@V5-591G:~$ sudo dpkg --configure -a
Setting up linux-image-5.13.0-30-generic (5.13.0-30.33~20.04.1) ...
Setting up initramfs-tools (0.136ubuntu6.7) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-firmware (1.187.26) ...
update-initramfs: Generating /boot/initrd.img-5.13.0-28-generic
I: The initramfs will attempt to resume from /dev/dm-1
I: (/dev/mapper/system-swap)
I: Set the RESUME variable to override this.
Error 24 : Write error : cannot write compressed block 
E: mkinitramfs failure cpio 141 lz4 -9 -l 24
update-initramfs: failed for /boot/initrd.img-5.13.0-28-generic with 1.
dpkg: error processing package linux-firmware (--configure):
 installed linux-firmware package post-installation script subprocess returned error exit status 1
Processing triggers for linux-image-5.13.0-30-generic (5.13.0-30.33~20.04.1) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.13.0-30-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.13.0-30-generic
I: The initramfs will attempt to resume from /dev/dm-1
I: (/dev/mapper/system-swap)
I: Set the RESUME variable to override this.
Error 24 : Write error : cannot write compressed block 
E: mkinitramfs failure cpio 141 lz4 -9 -l 24
update-initramfs: failed for /boot/initrd.img-5.13.0-30-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-5.13.0-30-generic (--configure):
 installed linux-image-5.13.0-30-generic package post-installation script subprocess returned error exit status 1
Processing triggers for initramfs-tools (0.136ubuntu6.7) ...
update-initramfs: Generating /boot/initrd.img-5.13.0-28-generic
I: The initramfs will attempt to resume from /dev/dm-1
I: (/dev/mapper/system-swap)
I: Set the RESUME variable to override this.
Error 24 : Write error : cannot write compressed block 
E: mkinitramfs failure cpio 141 lz4 -9 -l 24
update-initramfs: failed for /boot/initrd.img-5.13.0-28-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 installed initramfs-tools package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-firmware
 linux-image-5.13.0-30-generic
 initramfs-tools

```

Best,
Pawel

---

### Post by Bashing-om on 2022-02-27
pavloos; Oh Boy -

Let's go deeper.

Looking at "initramfs-tools" :
```

apt show initramfs-tools

```

seems a good candidate that affects installs.

What results with terminal command:
```

sudo apt install --reinstall initramfs-tools

```

[INDENT]a poke to give some guidance
[/INDENT]

---

### Post by Impavidus on 2022-02-28
> **pavloos said:**
> Hello,

thank you for your willingness to look into it. So:

```
pawel@V5-591G:~$ df -h
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/system-root   35G   31G  2,4G  93% /
/dev/mapper/system-home  169G  141G   20G  88% /home
/dev/sdb1                472M  363M   85M  82% /boot

```


Your filesystem is almost full. Root, home and boot, but the issue is most likely boot. Try removing the 5.11 kernel first:```
sudo dpkg --purge linux-modules-extra-5.11.0-44-generic linux-modules-5.11.0-44-generic linux-image-5.11.0-44-generic
```Using the dpkg command here instead of the higher level apt command as apt may insist on installing the 5.13.0-30 kernel first, which will fail.

BTW, if you have a separate home partition, getting 31GB in your root partition is a lot. It may have to do with the large number of snaps you have installed.

---

### Post by MAFoElffen on 2022-02-28
That's what I see also. Especially for it trying to do a kernel update, trying to generate an intramfs with only 85M free in a limited sized boot partition... 
```

ls -l /boot

```

Yes...
initrd.img-<version>-generic, about 66MB
System.map=<version>-generic, about 6MB
vmlinuz-<version>-generic, about 11MB
config-<version<-generic, about 0.25MB

That's roughly 84MB with just those, after the compression of those files.

---

### Post by pavloos on 2022-03-01
Thank you for your help. The issue was indeed low space on /boot and I managed to fix it with your suggestions.

At first, trying purge 5.11 with the suggested command returned 
```
pawel@V5-591G:~$ sudo dpkg --purge linux-modules-extra-5.11.0-44-generic linux-modules-5.11.0-44-generic linux-image-5.11.0-44-genericdpkg: error: dpkg frontend lock is locked by another process
```

But I get rid of it using good old Synaptic.

---

### Post by Impavidus on 2022-03-01
The issue is likely to return at the next kernel upgrade. Try and make your /boot partition a bit larger, just a few 100MB extra, although you haven't much room to shrink the other partitions. Maybe it's time to remove some junk.

---

