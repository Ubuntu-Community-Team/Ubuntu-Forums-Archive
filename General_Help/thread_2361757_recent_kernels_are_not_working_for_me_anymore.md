---
title: "recent kernels are not working for me anymore"
date: 2017-05-20
forum: General Help
---

### Post by ELMIT on 2017-05-20
kernels 4.2.0-78 and 4.2.0-77 are giving me troubles.

I use 2 monitors. Starting with the above kernels I get only ONE monitor and the login fails with a flash of the screen. No idea why.

If I use in Grub an older kernel 4.2.0-75 it works.

Usually each kernel results in a bigger size than before, look at my boot directory:

```
/boot$ ls -l
total 316328
-rw-r--r-- 1 root root  1313029 Mar 16  2016 abi-4.2.0-35-generic
-rw-r--r-- 1 root root  1245659 Mar 24 23:20 abi-4.4.0-71-generic
-rw-r--r-- 1 root root  1245659 Apr  1 01:14 abi-4.4.0-72-generic
-rw-r--r-- 1 root root  1246246 Apr 20 20:02 abi-4.4.0-75-generic
-rw-r--r-- 1 root root  1246313 Apr 26 18:30 abi-4.4.0-77-generic
-rw-r--r-- 1 root root  1246312 Apr 28 02:24 abi-4.4.0-78-generic
-rw-r--r-- 1 root root   184888 Mar 16  2016 config-4.2.0-35-generic
-rw-r--r-- 1 root root   190236 Mar 24 23:20 config-4.4.0-71-generic
-rw-r--r-- 1 root root   190236 Apr  1 01:14 config-4.4.0-72-generic
-rw-r--r-- 1 root root   190214 Apr 20 20:02 config-4.4.0-75-generic
-rw-r--r-- 1 root root   190355 Apr 26 18:30 config-4.4.0-77-generic
-rw-r--r-- 1 root root   190355 Apr 28 02:24 config-4.4.0-78-generic
drwxr-xr-x 5 root root     4096 May 20 15:58 grub
-rw-r--r-- 1 root root 35418181 May 20 14:53 initrd.img-4.2.0-35-generic
-rw-r--r-- 1 root root 45634262 May 20 14:53 initrd.img-4.4.0-71-generic
-rw-r--r-- 1 root root 45632172 May 20 14:53 initrd.img-4.4.0-72-generic
-rw-r--r-- 1 root root 45634127 May 20 14:53 initrd.img-4.4.0-75-generic
-rw-r--r-- 1 root root 38415590 May 20 14:52 initrd.img-4.4.0-77-generic
-rw-r--r-- 1 root root 38464697 May 20 15:58 initrd.img-4.4.0-78-generic
-rw-r--r-- 1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw------- 1 root root  3745312 Mar 16  2016 System.map-4.2.0-35-generic
-rw------- 1 root root  3882277 Mar 24 23:20 System.map-4.4.0-71-generic
-rw------- 1 root root  3882277 Apr  1 01:14 System.map-4.4.0-72-generic
-rw------- 1 root root  3883390 Apr 20 20:02 System.map-4.4.0-75-generic
-rw------- 1 root root  3883390 Apr 26 18:30 System.map-4.4.0-77-generic
-rw------- 1 root root  3882872 Apr 28 02:24 System.map-4.4.0-78-generic
-rw------- 1 root root  6829104 Mar 16  2016 vmlinuz-4.2.0-35-generic
-rw------- 1 root root  7083344 Mar 24 23:20 vmlinuz-4.4.0-71-generic
-rw------- 1 root root  7083248 Apr  1 01:14 vmlinuz-4.4.0-72-generic
-rw------- 1 root root  7081872 Apr 20 20:02 vmlinuz-4.4.0-75-generic
-rw------- 1 root root  7081808 Apr 26 18:30 vmlinuz-4.4.0-77-generic
-rw------- 1 root root  7089552 Apr 28 02:24 vmlinuz-4.4.0-78-generic

```

---

### Post by TheFu on 2017-05-20
You need to look at the logs for any messages.

---

### Post by ELMIT on 2017-05-20
what should I look for in which log file?  I tried syslog (grep "16:29:" - that was kernel *79 and grep "16:30:" - that was kernel *75)

Since there is a date/time stamp I cannot run diff to see the difference. How can I narrow that down?

---

### Post by ajgreeny on 2017-05-20
You have a lot of unnecessary kernels sitting around in your system which you really should get rid of.

The easiest way would be to try ```
sudo apt -s autoremove --purge
``` as a start to simulate what would be removed before actually doing anything, and if all looks OK just remove the **-s** option and run it again.

However, you will then be left only with the kernels that you say are giving you problems, so let's see if there are any extra packages related to kernels that are missing ; this has recently been a problem in xenial and could be yours as well.
Run command ```
dpkg -l linux-image* linux-headers*
```to see exactly what you have currently installed and we can move on from there.

---

### Post by deadflowr on 2017-05-20
> I use 2 monitors. Starting with the above kernels I get only ONE monitor and the login fails with a flash of the screen. No idea why.

If I use in Grub an older kernel 4.2.0-75 it works.

You mean the 4.4.0-75 kernel. (you have no 4.2..0-75 kernel, only the 4.2.0-31 kernel.)

What's the gpu, and did you need to add any additional drivers for it?l

---

### Post by ELMIT on 2017-09-20
I am still on that problem

```
sudo apt -s autoremove --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

dpkg -l linux-image* linux-headers*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-================================================================================================
un  linux-headers                                 <none>                      <none>                      (no description available)
un  linux-headers-2.6-686                         <none>                      <none>                      (no description available)
un  linux-headers-2.6-amd64                       <none>                      <none>                      (no description available)
un  linux-headers-3.0                             <none>                      <none>                      (no description available)
ii  linux-headers-4.4.0-75                        4.4.0-75.96                 all                         Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-75-generic                4.4.0-75.96                 amd64                       Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
un  linux-headers-4.4.0-83-generic                <none>                      <none>                      (no description available)
un  linux-headers-4.4.0-87-generic                <none>                      <none>                      (no description available)
un  linux-headers-4.4.0-89-generic                <none>                      <none>                      (no description available)
ii  linux-headers-4.4.0-93                        4.4.0-93.116                all                         Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-93-generic                4.4.0-93.116                amd64                       Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-96                        4.4.0-96.119                all                         Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-96-generic                4.4.0-96.119                amd64                       Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
un  linux-headers-686-pae                         <none>                      <none>                      (no description available)
un  linux-headers-amd64                           <none>                      <none>                      (no description available)
ii  linux-headers-generic                         4.4.0.96.101                amd64                       Generic Linux kernel headers
un  linux-headers-generic-pae                     <none>                      <none>                      (no description available)
un  linux-image                                   <none>                      <none>                      (no description available)
ii  linux-image-4.4.0-75-generic                  4.4.0-75.96                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-83-generic                  4.4.0-83.106                amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-87-generic                  4.4.0-87.110                amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-89-generic                  4.4.0-89.112                amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-93-generic                  4.4.0-93.116                amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-96-generic                  4.4.0-96.119                amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-75-generic            4.4.0-75.96                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-83-generic            4.4.0-83.106                amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-87-generic            4.4.0-87.110                amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-89-generic            4.4.0-89.112                amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-93-generic            4.4.0-93.116                amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-96-generic            4.4.0-96.119                amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-virtual                     4.4.0.96.101                amd64                       Transitional package.
ii  linux-image-generic                           4.4.0.96.101                amd64                       Generic Linux kernel image

```

[IMG]http://home.elmit.biz/Ubuntu/Software%20&%20Updates_608.png[/IMG]

---

