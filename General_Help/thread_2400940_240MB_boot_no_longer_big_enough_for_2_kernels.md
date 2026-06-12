---
title: "240MB /boot no longer big enough for 2 kernels?"
date: 2018-09-11
forum: General Help
---

### Post by sremick on 2018-09-11
So back before I was wiser, I set up my system with the recommended 240MB /boot partition and also used full-disk encryption. Over time, managing the manual removal of old kernels has worked out ok and I've followed the rule to always keep 2 kernels.

Now I'm face with having *just* 2 kernels and *still* not being able to update. 

Error:
> **Not Enough Free Space**
The upgrade needs a total of 139 M free space on disk '/boot'. Please free at least an additional 1,971 k of disk space on '/boot'


Relevant info:

```
$ df
Filesystem              1K-blocks      Used Available Use% Mounted on
udev                     16407528         0  16407528   0% /dev
tmpfs                     3287892      1608   3286284   1% /run
/dev/mapper/it--vg-root 428101800 147761156 258571224  37% /
tmpfs                    16439456    115576  16323880   1% /dev/shm
tmpfs                        5120         8      5112   1% /run/lock
tmpfs                    16439456         0  16439456   0% /sys/fs/cgroup
/dev/sda1                  240972     94867    133664  42% /boot
```

```
/boot$ ls -l
total 85905
-rw-r--r-- 1 root root  1537455 Aug 10 13:22 abi-4.15.0-32-generic
-rw-r--r-- 1 root root  1537455 Aug 15 08:50 abi-4.15.0-33-generic
-rw-r--r-- 1 root root   216860 Aug 10 13:22 config-4.15.0-32-generic
-rw-r--r-- 1 root root   216905 Aug 15 08:50 config-4.15.0-33-generic
drwxr-xr-x 5 root root     1024 Sep 11 08:32 grub
-rw-r--r-- 1 root root 58920077 Sep  9 15:32 initrd.img-4.15.0-33-generic
drwx------ 2 root root    12288 Aug 25  2015 lost+found
-rw-r--r-- 1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-r--r-- 1 root root        0 Aug 10 13:22 retpoline-4.15.0-32-generic
-rw-r--r-- 1 root root        0 Aug 15 08:50 retpoline-4.15.0-33-generic
-rw------- 1 root root  4042389 Aug 10 13:22 System.map-4.15.0-32-generic
-rw------- 1 root root  4042247 Aug 15 08:50 System.map-4.15.0-33-generic
-rw------- 1 root root  8263536 Aug 10 13:22 vmlinuz-4.15.0-32-generic
-rw------- 1 root root  8265464 Aug 15 08:57 vmlinuz-4.15.0-33-generic
```

```
$ dpkg -l linux-image*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                           Version                      Architecture                 Description
+++-==============================================-============================-============================-==================================================================================================
un  linux-image                                    <none>                       <none>                       (no description available)
un  linux-image-3.0                                <none>                       <none>                       (no description available)
rc  linux-image-3.19.0-15-generic                  3.19.0-15.15                 amd64                        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-26-generic                  3.19.0-26.28                 amd64                        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
un  linux-image-4.15.0-32-generic                  <none>                       <none>                       (no description available)
ii  linux-image-4.15.0-33-generic                  4.15.0-33.36                 amd64                        Signed kernel image generic
rc  linux-image-4.2.0-19-generic                   4.2.0-19.23                  amd64                        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-36-generic                   4.2.0-36.42                  amd64                        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-45-generic                   4.4.0-45.66                  amd64                        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-53-generic                   4.4.0-53.74                  amd64                        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-15-generic            3.19.0-15.15                 amd64                        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-26-generic            3.19.0-26.28                 amd64                        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-19-generic             4.2.0-19.23                  amd64                        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-36-generic             4.2.0-36.42                  amd64                        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-45-generic             4.4.0-45.66                  amd64                        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-53-generic             4.4.0-53.74                  amd64                        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                            4.15.0.33.35                 amd64                        Generic Linux kernel image
ii  linux-image-unsigned-4.15.0-32-generic         4.15.0-32.35                 amd64                        Linux kernel image for version 4.15.0 on 64 bit x86 SMP
un  linux-image-unsigned-4.15.0-33-generic         <none>                       <none>                       (no description available)

```

What can be done? Obviously even buying a larger hard drive and moving things over with a larger /boot on the destination drive is no trivial thing given the full disk encryption.

---

### Post by Dennis N on 2018-09-12
Some of the removed kernels still have configuration files. These have line in your dpkg output starting with 'rc'. You can remove those config files by purge option:
Example:
**sudo apt purge linux-image-3.19.0-15-generic**
There are 12 of those.  That should free some space from /boot if the configuration files are still there. 

On my system:

```
dmn@Roxanne:/boot$ ls -l | grep config
-rw-r--r-- 1 root root   216860 Aug 10 10:22 config-4.15.0-32-generic
-rw-r--r-- 1 root root   216905 Aug 15 05:50 config-4.15.0-33-generic
-rw-r--r-- 1 root root   216905 Aug 27 07:45 config-4.15.0-34-generic

```
about 200K per kernel.

---

### Post by sremick on 2018-09-12
> **Dennis N said:**
> Some of the removed kernels still have configuration files. These have line in your dpkg output starting with 'rc'. You can remove those config files by purge option:
Example:
**sudo apt purge linux-image-3.19.0-15-generic**
There are 12 of those.  That should free some space from /boot if the configuration files are still there. 
Well I don't think the config files were still there but I ran that command anyway on all the "rc" listings. Unfortunately it still says I need to free up 1.971MB.

I still don't get why the standard 240MB isn't big enough for 2 kernels. Why am I the only one experiencing this?

```
$ ls -l
total 85905
-rw-r--r-- 1 root root  1537455 Aug 10 13:22 abi-4.15.0-32-generic
-rw-r--r-- 1 root root  1537455 Aug 15 08:50 abi-4.15.0-33-generic
-rw-r--r-- 1 root root   216860 Aug 10 13:22 config-4.15.0-32-generic
-rw-r--r-- 1 root root   216905 Aug 15 08:50 config-4.15.0-33-generic
drwxr-xr-x 5 root root     1024 Sep 11 08:32 grub
-rw-r--r-- 1 root root 58920077 Sep  9 15:32 initrd.img-4.15.0-33-generic
drwx------ 2 root root    12288 Aug 25  2015 lost+found
-rw-r--r-- 1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-r--r-- 1 root root        0 Aug 10 13:22 retpoline-4.15.0-32-generic
-rw-r--r-- 1 root root        0 Aug 15 08:50 retpoline-4.15.0-33-generic
-rw------- 1 root root  4042389 Aug 10 13:22 System.map-4.15.0-32-generic
-rw------- 1 root root  4042247 Aug 15 08:50 System.map-4.15.0-33-generic
-rw------- 1 root root  8263536 Aug 10 13:22 vmlinuz-4.15.0-32-generic
-rw------- 1 root root  8265464 Aug 15 08:57 vmlinuz-4.15.0-33-generic
```

```
$ sudo du
12    ./lost+found
2068    ./grub/i386-pc
2354    ./grub/fonts
127    ./grub/locale
6913    ./grub
92818    .

```

---

### Post by Dennis N on 2018-09-13
Assuming a new kernel is going to be installed, if I were in your situation I would just remove (purge) the -32 kernel packages before starting the upgrade. Then it should install the new one OK and leave you again with two kernels.

---

