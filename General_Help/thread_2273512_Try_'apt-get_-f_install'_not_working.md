---
title: "Try 'apt-get -f install' not working"
date: 2015-04-13
forum: General Help
---

### Post by laphyzz2 on 2015-04-13
Ok so tryed to install Overviewer for Minecraft however when trying to download it something has gone wrong and im now unable to install anything with out getting this message,

-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-

You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
 python-numpy : Depends: libblas3 but it is not going to be installed or
                         libblas.so.3
                Depends: liblapack3 but it is not going to be installed or
                         liblapack.so.3
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-

root@ID-Main-Server:/home/robert# apt-get install linux-image-extra-3.13.0-49-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-image-extra-3.13.0-49-generic is already the newest version.
linux-image-extra-3.13.0-49-generic set to manually installed.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-

I need some help,
Please

---

### Post by overdrank on 2015-04-13
Hi and welcome, have you try to run the command
```
sudo apt-get -f install
```

---

### Post by laphyzz2 on 2015-04-13
Did not work

apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-3.13.0-43-generic linux-image-3.13.0-49-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed
  linux-image-3.13.0-43-generic linux-image-3.13.0-49-generic
0 to upgrade, 2 to newly install, 0 to remove and 70 not to upgrade.
6 not fully installed or removed.
Need to get 0 B/67.0 MB of archives.
After this operation, 84.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 321882 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-49-generic_3.13.0-49.81_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-49-generic (3.13.0-49.81) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-49-generic_3.13.0-49.81_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.13.0-49-generic' to '/boot/vmlinuz-3.13.0-49-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
Preparing to unpack .../linux-image-3.13.0-43-generic_3.13.0-43.72_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-43-generic (3.13.0-43.72) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-43-generic_3.13.0-43.72_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-3.13.0-43-generic' to '/boot/System.map-3.13.0-43-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-49-generic_3.13.0-49.81_amd64.deb
 /var/cache/apt/archives/linux-image-3.13.0-43-generic_3.13.0-43.72_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ian-weisser on 2015-04-13
> **laphyzz2 said:**
> 0 to upgrade, 2 to newly install, 0 to remove and **70 not to upgrade**.
**6 not fully installed or removed.**


Two problems there.

> **laphyzz2 said:**
> Unpacking linux-image-3.13.0-49-generic (3.13.0-49.81) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-49-generic_3.13.0-49.81_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.13.0-49-generic' to '/boot/vmlinuz-3.13.0-49-generic.dpkg-new': **failed to write (No space left on device)**

Ah, that's the root cause.
Your partition is full.

Please post the output of the following two commands:
```
df
df -i
```

---

### Post by laphyzz2 on 2015-04-13
df:

Filesystem                             1K-blocks     Used  Available Use% Mounted on
/dev/mapper/ID--Main--Server--vg-root 1914500476 15588224 1801638192   1% /
none                                           4        0          4   0% /sys/fs/cgroup
udev                                     3906220        8    3906212   1% /dev
tmpfs                                     790088      648     789440   1% /run
none                                        5120        0       5120   0% /run/lock
none                                     3950428        0    3950428   0% /run/shm
none                                      102400        0     102400   0% /run/user
/dev/sda1                                 240972   233423          0 100% /boot

-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-

df -i:

Filesystem                               Inodes  IUsed     IFree IUse% Mounted on
/dev/mapper/ID--Main--Server--vg-root 121577472 337024 121240448    1% /
none                                     987607      2    987605    1% /sys/fs/cgroup
udev                                     976555    487    976068    1% /dev
tmpfs                                    987607    466    987141    1% /run
none                                     987607      3    987604    1% /run/lock
none                                     987607      1    987606    1% /run/shm
none                                     987607      2    987605    1% /run/user
/dev/sda1                                 62248    337     61911    1% /boot

-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-

Usage of /:   0.8% of 1.78TB

---

### Post by laphyzz2 on 2015-04-13
df:

Filesystem                             1K-blocks     Used  Available Use% Mounted on
/dev/mapper/ID--Main--Server--vg-root 1914500476 15588224 1801638192   1% /
none                                           4        0          4   0% /sys/fs/cgroup
udev                                     3906220        8    3906212   1% /dev
tmpfs                                     790088      648     789440   1% /run
none                                        5120        0       5120   0% /run/lock
none                                     3950428        0    3950428   0% /run/shm
none                                      102400        0     102400   0% /run/user
/dev/sda1                                 240972   233423          0 100% /boot

-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-

df -i:

Filesystem                               Inodes  IUsed     IFree IUse% Mounted on
/dev/mapper/ID--Main--Server--vg-root 121577472 337024 121240448    1% /
none                                     987607      2    987605    1% /sys/fs/cgroup
udev                                     976555    487    976068    1% /dev
tmpfs                                    987607    466    987141    1% /run
none                                     987607      3    987604    1% /run/lock
none                                     987607      1    987606    1% /run/shm
none                                     987607      2    987605    1% /run/user
/dev/sda1                                 62248    337     61911    1% /boot

-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-:-

Usage of /:   0.8% of 1.78TB

---

### Post by Bashing-om on 2015-04-13
laphyzz2; Yuk;

Not keeping up with the house cleaning, huh ?
per:
> 
df  ->
/dev/sda1 240972 233423 0 100% /boot

At 100% capacity, maybe there is no operational headroom to operate in, but, we can try the easier method:
What results:
```

sudo apt-get autoremove

```
failing that, we can try and invoke 'dpkg' manually, see if we can free up that disk space.

[INDENT][INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by laphyzz2 on 2015-04-13
apt-get autoremove Reading package lists... Done Building dependency tree Reading state information... Done You might want to run ‘apt-get -f install’ to correct these. The following packages have unmet dependencies.  linux-image-extra-3.13.0-43-generic : Depends: linux-image-3.13.0-43-generic but it is not installed  linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not installed  linux-image-generic : Depends: linux-image-3.13.0-49-generic but it is not installed E: Unmet dependencies. Try using -f.

---

### Post by Bashing-om on 2015-04-13
laphyzz2; Well;

Not surprised . no head room .
Let's proceed to the manual method and give it a try.
Post back - Between Code Tags , PLEASE - the outputs of terminal commands:
```

uname -r
dpkg -l | grep linux-
ls -al /boot

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
to know what to purge with 'dpkg' .

[INDENT]if at 1st you do not succeed 
[INDENT][INDENT][INDENT]do something else
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by laphyzz2 on 2015-04-13
```
 unmae -r No command 'unmae' found, did you mean:  Command 'uname' from package 'coreutils' (main) unmae: command not found 
```  ```
 ii  linux-firmware                      1.127.11                         all          Firmware for Linux kernel drivers iU  linux-generic                       3.13.0.49.56                     amd64        Complete Generic Linux kernel and headers ii  linux-headers-3.13.0-33             3.13.0-33.58                     all          Header files related to Linux kernel version 3.13.0 ii  linux-headers-3.13.0-33-generic     3.13.0-33.58                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP ii  linux-headers-3.13.0-34             3.13.0-34.60                     all          Header files related to Linux kernel version 3.13.0 ii  linux-headers-3.13.0-34-generic     3.13.0-34.60                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP ii  linux-headers-3.13.0-36             3.13.0-36.63                     all          Header files related to Linux kernel version 3.13.0 ii  linux-headers-3.13.0-36-generic     3.13.0-36.63                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP ii  linux-headers-3.13.0-37             3.13.0-37.64                     all          Header files related to Linux kernel version 3.13.0 ii  linux-headers-3.13.0-37-generic     3.13.0-37.64                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP ii  linux-headers-3.13.0-39             3.13.0-39.66                     all          Header files related to Linux kernel version 3.13.0 ii  linux-headers-3.13.0-39-generic     3.13.0-39.66                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP ii  linux-headers-3.13.0-40             3.13.0-40.69                     all          Header files related to Linux kernel version 3.13.0 ii  linux-headers-3.13.0-40-generic     3.13.0-40.69                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP ii  linux-headers-3.13.0-41             3.13.0-41.70                     all          Header files related to Linux kernel version 3.13.0 ii  linux-headers-3.13.0-41-generic     3.13.0-41.70                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP ii  linux-headers-3.13.0-43             3.13.0-43.72                     all          Header files related to Linux kernel version 3.13.0 ii  linux-headers-3.13.0-43-generic     3.13.0-43.72                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP ii  linux-headers-3.13.0-44             3.13.0-44.73                     all          Header files related to Linux kernel version 3.13.0 ii  linux-headers-3.13.0-44-generic     3.13.0-44.73                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP ii  linux-headers-3.13.0-49             3.13.0-49.81                     all          Header files related to Linux kernel version 3.13.0 ii  linux-headers-3.13.0-49-generic     3.13.0-49.81                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP ii  linux-headers-generic               3.13.0.49.56                     amd64        Generic Linux kernel headers rc  linux-image-3.13.0-24-generic       3.13.0-24.47                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP rc  linux-image-3.13.0-27-generic       3.13.0-27.50                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP rc  linux-image-3.13.0-29-generic       3.13.0-29.53                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP rc  linux-image-3.13.0-30-generic       3.13.0-30.55                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP rc  linux-image-3.13.0-32-generic       3.13.0-32.57                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP ii  linux-image-3.13.0-33-generic       3.13.0-33.58                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP ii  linux-image-3.13.0-34-generic       3.13.0-34.60                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP rc  linux-image-3.13.0-35-generic       3.13.0-35.62                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP ii  linux-image-3.13.0-36-generic       3.13.0-36.63                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP ii  linux-image-3.13.0-37-generic       3.13.0-37.64                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP ii  linux-image-3.13.0-39-generic       3.13.0-39.66                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP ii  linux-image-3.13.0-40-generic       3.13.0-40.69                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP ii  linux-image-3.13.0-41-generic       3.13.0-41.70                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP ic  linux-image-3.13.0-43-generic       3.13.0-43.72                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP iF  linux-image-3.13.0-44-generic       3.13.0-44.73                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP rc  linux-image-extra-3.13.0-24-generic 3.13.0-24.47                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP rc  linux-image-extra-3.13.0-27-generic 3.13.0-27.50                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP rc  linux-image-extra-3.13.0-29-generic 3.13.0-29.53                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP rc  linux-image-extra-3.13.0-30-generic 3.13.0-30.55                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP rc  linux-image-extra-3.13.0-32-generic 3.13.0-32.57                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP ii  linux-image-extra-3.13.0-33-generic 3.13.0-33.58                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP ii  linux-image-extra-3.13.0-34-generic 3.13.0-34.60                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP rc  linux-image-extra-3.13.0-35-generic 3.13.0-35.62                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP ii  linux-image-extra-3.13.0-36-generic 3.13.0-36.63                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP ii  linux-image-extra-3.13.0-37-generic 3.13.0-37.64                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP ii  linux-image-extra-3.13.0-39-generic 3.13.0-39.66                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP ii  linux-image-extra-3.13.0-40-generic 3.13.0-40.69                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP ii  linux-image-extra-3.13.0-41-generic 3.13.0-41.70                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP rH  linux-image-extra-3.13.0-43-generic 3.13.0-43.72                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP iU  linux-image-extra-3.13.0-44-generic 3.13.0-44.73                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP rc  linux-image-extra-3.13.0-46-generic 3.13.0-46.79                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP iU  linux-image-extra-3.13.0-49-generic 3.13.0-49.81                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP iU  linux-image-generic                 3.13.0.49.56                     amd64        Generic Linux kernel image 
```  ```
 ls -al /boot total 224536 drwxr-xr-x  4 root root     3072 Apr 13 21:27 . drwxr-xr-x 23 root root     4096 Apr 13 20:54 .. -rw-r--r--  1 root root  1162712 Jul 29  2014 abi-3.13.0-33-generic -rw-r--r--  1 root root  1162712 Aug 13  2014 abi-3.13.0-34-generic -rw-r--r--  1 root root  1163858 Sep  3  2014 abi-3.13.0-36-generic -rw-r--r--  1 root root  1164489 Sep 22  2014 abi-3.13.0-37-generic -rw-r--r--  1 root root  1164547 Oct 28 14:25 abi-3.13.0-39-generic -rw-r--r--  1 root root  1164509 Nov 13 18:30 abi-3.13.0-40-generic -rw-r--r--  1 root root  1164720 Nov 25 15:34 abi-3.13.0-41-generic -rw-r--r--  1 root root  1164720 Dec 16 01:17 abi-3.13.0-44-generic -rw-r--r--  1 root root   165611 Jul 29  2014 config-3.13.0-33-generic -rw-r--r--  1 root root   165611 Aug 13  2014 config-3.13.0-34-generic -rw-r--r--  1 root root   165671 Sep  3  2014 config-3.13.0-36-generic -rw-r--r--  1 root root   165712 Sep 22  2014 config-3.13.0-37-generic -rw-r--r--  1 root root   165712 Oct 28 14:25 config-3.13.0-39-generic -rw-r--r--  1 root root   165745 Nov 13 18:30 config-3.13.0-40-generic -rw-r--r--  1 root root   165745 Nov 25 15:34 config-3.13.0-41-generic -rw-r--r--  1 root root   165748 Dec 16 01:17 config-3.13.0-44-generic drwxr-xr-x  5 root root     1024 Apr 13 20:57 grub -rw-r--r--  1 root root 20085652 Aug 12  2014 initrd.img-3.13.0-33-generic -rw-r--r--  1 root root 20085679 Aug 14  2014 initrd.img-3.13.0-34-generic -rw-r--r--  1 root root 20108251 Oct 28 13:19 initrd.img-3.13.0-36-generic -rw-r--r--  1 root root 20109817 Oct 28 13:22 initrd.img-3.13.0-37-generic -rw-r--r--  1 root root 20109475 Oct 29 06:44 initrd.img-3.13.0-39-generic -rw-r--r--  1 root root 20114942 Nov 25 06:36 initrd.img-3.13.0-40-generic -rw-r--r--  1 root root 20144934 Dec 11 07:01 initrd.img-3.13.0-41-generic -rw-r--r--  1 root root  3463278 Apr 13 20:54 initrd.img-3.13.0-46-generic drwx------  2 root root    12288 May 23  2014 lost+found -rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin -rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf -rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin -rw-------  1 root root  3381262 Jul 29  2014 System.map-3.13.0-33-generic -rw-------  1 root root  3381262 Aug 13  2014 System.map-3.13.0-34-generic -rw-------  1 root root  3386479 Sep  3  2014 System.map-3.13.0-36-generic -rw-------  1 root root  3386945 Sep 22  2014 System.map-3.13.0-37-generic -rw-------  1 root root  3386936 Oct 28 14:25 System.map-3.13.0-39-generic -rw-------  1 root root  3387231 Nov 13 18:30 System.map-3.13.0-40-generic -rw-------  1 root root  3388792 Nov 25 15:34 System.map-3.13.0-41-generic -rw-------  1 root root  3388834 Dec 16 01:17 System.map-3.13.0-44-generic -rw-------  1 root root  5798688 Jul 29  2014 vmlinuz-3.13.0-33-generic -rw-------  1 root root  5797728 Aug 13  2014 vmlinuz-3.13.0-34-generic -rw-------  1 root root  5806848 Sep  3  2014 vmlinuz-3.13.0-36-generic -rw-------  1 root root  5808832 Sep 22  2014 vmlinuz-3.13.0-37-generic -rw-------  1 root root  5808544 Oct 28 14:25 vmlinuz-3.13.0-39-generic -rw-------  1 root root  5808960 Nov 13 18:30 vmlinuz-3.13.0-40-generic -rw-------  1 root root  5814112 Nov 25 15:34 vmlinuz-3.13.0-41-generic -rw-------  1 root root  5814496 Dec 16 01:17 vmlinuz-3.13.0-44-generic 
```

---

### Post by laphyzz2 on 2015-04-13
```
 root@ID-Main-Server:/home/robert# unmae -r No command 'unmae' found, did you mean:  Command 'uname' from package 'coreutils' (main) unmae: command not found 
```  ```
 ii  linux-firmware                      1.127.11                         all          Firmware for Linux kernel drivers iU  linux-generic                       3.13.0.49.56                     amd64        Complete Generic Linux kernel and headers ii  linux-headers-3.13.0-33             3.13.0-33.58                     all          Header files related to Linux kernel version 3.13.0 ii  linux-headers-3.13.0-33-generic     3.13.0-33.58                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP ii  linux-headers-3.13.0-34             3.13.0-34.60                     all          Header files related to Linux kernel version 3.13.0 ii  linux-headers-3.13.0-34-generic     3.13.0-34.60                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP ii  linux-headers-3.13.0-36             3.13.0-36.63                     all          Header files related to Linux kernel version 3.13.0 ii  linux-headers-3.13.0-36-generic     3.13.0-36.63                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP ii  linux-headers-3.13.0-37             3.13.0-37.64                     all          Header files related to Linux kernel version 3.13.0 ii  linux-headers-3.13.0-37-generic     3.13.0-37.64                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP ii  linux-headers-3.13.0-39             3.13.0-39.66                     all          Header files related to Linux kernel version 3.13.0 ii  linux-headers-3.13.0-39-generic     3.13.0-39.66                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP ii  linux-headers-3.13.0-40             3.13.0-40.69                     all          Header files related to Linux kernel version 3.13.0 ii  linux-headers-3.13.0-40-generic     3.13.0-40.69                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP ii  linux-headers-3.13.0-41             3.13.0-41.70                     all          Header files related to Linux kernel version 3.13.0 ii  linux-headers-3.13.0-41-generic     3.13.0-41.70                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP ii  linux-headers-3.13.0-43             3.13.0-43.72                     all          Header files related to Linux kernel version 3.13.0 ii  linux-headers-3.13.0-43-generic     3.13.0-43.72                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP ii  linux-headers-3.13.0-44             3.13.0-44.73                     all          Header files related to Linux kernel version 3.13.0 ii  linux-headers-3.13.0-44-generic     3.13.0-44.73                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP ii  linux-headers-3.13.0-49             3.13.0-49.81                     all          Header files related to Linux kernel version 3.13.0 ii  linux-headers-3.13.0-49-generic     3.13.0-49.81                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP ii  linux-headers-generic               3.13.0.49.56                     amd64        Generic Linux kernel headers rc  linux-image-3.13.0-24-generic       3.13.0-24.47                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP rc  linux-image-3.13.0-27-generic       3.13.0-27.50                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP rc  linux-image-3.13.0-29-generic       3.13.0-29.53                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP rc  linux-image-3.13.0-30-generic       3.13.0-30.55                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP rc  linux-image-3.13.0-32-generic       3.13.0-32.57                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP ii  linux-image-3.13.0-33-generic       3.13.0-33.58                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP ii  linux-image-3.13.0-34-generic       3.13.0-34.60                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP rc  linux-image-3.13.0-35-generic       3.13.0-35.62                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP ii  linux-image-3.13.0-36-generic       3.13.0-36.63                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP ii  linux-image-3.13.0-37-generic       3.13.0-37.64                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP ii  linux-image-3.13.0-39-generic       3.13.0-39.66                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP ii  linux-image-3.13.0-40-generic       3.13.0-40.69                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP ii  linux-image-3.13.0-41-generic       3.13.0-41.70                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP ic  linux-image-3.13.0-43-generic       3.13.0-43.72                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP iF  linux-image-3.13.0-44-generic       3.13.0-44.73                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP rc  linux-image-extra-3.13.0-24-generic 3.13.0-24.47                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP rc  linux-image-extra-3.13.0-27-generic 3.13.0-27.50                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP rc  linux-image-extra-3.13.0-29-generic 3.13.0-29.53                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP rc  linux-image-extra-3.13.0-30-generic 3.13.0-30.55                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP rc  linux-image-extra-3.13.0-32-generic 3.13.0-32.57                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP ii  linux-image-extra-3.13.0-33-generic 3.13.0-33.58                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP ii  linux-image-extra-3.13.0-34-generic 3.13.0-34.60                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP rc  linux-image-extra-3.13.0-35-generic 3.13.0-35.62                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP ii  linux-image-extra-3.13.0-36-generic 3.13.0-36.63                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP ii  linux-image-extra-3.13.0-37-generic 3.13.0-37.64                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP ii  linux-image-extra-3.13.0-39-generic 3.13.0-39.66                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP ii  linux-image-extra-3.13.0-40-generic 3.13.0-40.69                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP ii  linux-image-extra-3.13.0-41-generic 3.13.0-41.70                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP rH  linux-image-extra-3.13.0-43-generic 3.13.0-43.72                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP iU  linux-image-extra-3.13.0-44-generic 3.13.0-44.73                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP rc  linux-image-extra-3.13.0-46-generic 3.13.0-46.79                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP iU  linux-image-extra-3.13.0-49-generic 3.13.0-49.81                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP iU  linux-image-generic                 3.13.0.49.56                     amd64        Generic Linux kernel image 
```  ```
 ls -al /boot total 224536 drwxr-xr-x  4 root root     3072 Apr 13 21:27 . drwxr-xr-x 23 root root     4096 Apr 13 20:54 .. -rw-r--r--  1 root root  1162712 Jul 29  2014 abi-3.13.0-33-generic -rw-r--r--  1 root root  1162712 Aug 13  2014 abi-3.13.0-34-generic -rw-r--r--  1 root root  1163858 Sep  3  2014 abi-3.13.0-36-generic -rw-r--r--  1 root root  1164489 Sep 22  2014 abi-3.13.0-37-generic -rw-r--r--  1 root root  1164547 Oct 28 14:25 abi-3.13.0-39-generic -rw-r--r--  1 root root  1164509 Nov 13 18:30 abi-3.13.0-40-generic -rw-r--r--  1 root root  1164720 Nov 25 15:34 abi-3.13.0-41-generic -rw-r--r--  1 root root  1164720 Dec 16 01:17 abi-3.13.0-44-generic -rw-r--r--  1 root root   165611 Jul 29  2014 config-3.13.0-33-generic -rw-r--r--  1 root root   165611 Aug 13  2014 config-3.13.0-34-generic -rw-r--r--  1 root root   165671 Sep  3  2014 config-3.13.0-36-generic -rw-r--r--  1 root root   165712 Sep 22  2014 config-3.13.0-37-generic -rw-r--r--  1 root root   165712 Oct 28 14:25 config-3.13.0-39-generic -rw-r--r--  1 root root   165745 Nov 13 18:30 config-3.13.0-40-generic -rw-r--r--  1 root root   165745 Nov 25 15:34 config-3.13.0-41-generic -rw-r--r--  1 root root   165748 Dec 16 01:17 config-3.13.0-44-generic drwxr-xr-x  5 root root     1024 Apr 13 20:57 grub -rw-r--r--  1 root root 20085652 Aug 12  2014 initrd.img-3.13.0-33-generic -rw-r--r--  1 root root 20085679 Aug 14  2014 initrd.img-3.13.0-34-generic -rw-r--r--  1 root root 20108251 Oct 28 13:19 initrd.img-3.13.0-36-generic -rw-r--r--  1 root root 20109817 Oct 28 13:22 initrd.img-3.13.0-37-generic -rw-r--r--  1 root root 20109475 Oct 29 06:44 initrd.img-3.13.0-39-generic -rw-r--r--  1 root root 20114942 Nov 25 06:36 initrd.img-3.13.0-40-generic -rw-r--r--  1 root root 20144934 Dec 11 07:01 initrd.img-3.13.0-41-generic -rw-r--r--  1 root root  3463278 Apr 13 20:54 initrd.img-3.13.0-46-generic drwx------  2 root root    12288 May 23  2014 lost+found -rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin -rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf -rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin -rw-------  1 root root  3381262 Jul 29  2014 System.map-3.13.0-33-generic -rw-------  1 root root  3381262 Aug 13  2014 System.map-3.13.0-34-generic -rw-------  1 root root  3386479 Sep  3  2014 System.map-3.13.0-36-generic -rw-------  1 root root  3386945 Sep 22  2014 System.map-3.13.0-37-generic -rw-------  1 root root  3386936 Oct 28 14:25 System.map-3.13.0-39-generic -rw-------  1 root root  3387231 Nov 13 18:30 System.map-3.13.0-40-generic -rw-------  1 root root  3388792 Nov 25 15:34 System.map-3.13.0-41-generic -rw-------  1 root root  3388834 Dec 16 01:17 System.map-3.13.0-44-generic -rw-------  1 root root  5798688 Jul 29  2014 vmlinuz-3.13.0-33-generic -rw-------  1 root root  5797728 Aug 13  2014 vmlinuz-3.13.0-34-generic -rw-------  1 root root  5806848 Sep  3  2014 vmlinuz-3.13.0-36-generic -rw-------  1 root root  5808832 Sep 22  2014 vmlinuz-3.13.0-37-generic -rw-------  1 root root  5808544 Oct 28 14:25 vmlinuz-3.13.0-39-generic -rw-------  1 root root  5808960 Nov 13 18:30 vmlinuz-3.13.0-40-generic -rw-------  1 root root  5814112 Nov 25 15:34 vmlinuz-3.13.0-41-generic -rw-------  1 root root  5814496 Dec 16 01:17 vmlinuz-3.13.0-44-generic 
```

---

### Post by Bashing-om on 2015-04-13
laphyzz2; sheeshhh ...

I correct my " uname -r "
I do not know why the outputs did not retain formatting:
should be similar:
```

sysop@1404mini:~$ uname -r
3.13.0-49-generic
sysop@1404mini:~$

```

```

3.13.0-49-generic
sysop@1404mini:~$ dpkg -l | grep linux-
ii  linux-firmware                        1.127.11                             all          Firmware for Linux kernel drivers
ii  linux-generic                         3.13.0.49.56                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-45               3.13.0-45.74                         all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic       3.13.0-45.74                         amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-46               3.13.0-46.79                         all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic       3.13.0-46.79                         amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-48               3.13.0-48.80                         all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic       3.13.0-48.80                         amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-49               3.13.0-49.81                         all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic       3.13.0-49.81                         amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                 3.13.0.49.56                         amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-45-generic         3.13.0-45.74                         amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-generic         3.13.0-46.79                         amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-48-generic         3.13.0-48.80                         amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-49-generic         3.13.0-49.81                         amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic   3.13.0-45.74                         amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic   3.13.0-46.79                         amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-48-generic   3.13.0-48.80                         amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic   3.13.0-49.81                         amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                   3.13.0.49.56                         amd64        Generic Linux kernel image
sysop@1404mini:~$ 

```

```

sysop@1404mini:~$ ls -al /boot
total 1252980
drwxr-xr-x  4 root root       4096 Apr  8 14:02 .
drwxr-xr-x 25 root root       4096 Apr 13 16:22 ..
-rw-r--r--  1 root root    1164967 Jan 13 14:12 abi-3.13.0-45-generic
-rw-r--r--  1 root root    1164852 Mar 10 15:43 abi-3.13.0-46-generic
-rw-r--r--  1 root root    1164723 Mar 12 06:52 abi-3.13.0-48-generic
-rw-r--r--  1 root root    1164723 Mar 24 15:05 abi-3.13.0-49-generic
-rw-r--r--  1 root root     165748 Jan 13 14:12 config-3.13.0-45-generic
-rw-r--r--  1 root root     165748 Mar 10 15:43 config-3.13.0-46-generic
-rw-r--r--  1 root root     165773 Mar 12 06:52 config-3.13.0-48-generic
-rw-r--r--  1 root root     165773 Mar 24 15:05 config-3.13.0-49-generic
drwxr-xr-x  5 root root       4096 Apr  8 14:02 grub
drwxr-xr-x  5 root root       4096 Jun  9  2014 grub_backup
-rw-r--r--  1 root root   19342792 Feb 19 12:16 initrd.img-3.13.0-45-generic
-rw-r--r--  1 root root   19341335 Mar 12 10:41 initrd.img-3.13.0-46-generic
-rw-r--r--  1 root root   19343618 Apr  8 13:57 initrd.img-3.13.0-48-generic
-rw-r--r--  1 root root   19341533 Apr  8 14:02 initrd.img-3.13.0-49-generic
-rw-r--r--  1 root root     176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root     178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root     178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root    3389258 Jan 13 14:12 System.map-3.13.0-45-generic
-rw-------  1 root root    3389458 Mar 10 15:43 System.map-3.13.0-46-generic
-rw-------  1 root root    3389235 Mar 12 06:52 System.map-3.13.0-48-generic
-rw-------  1 root root    3389437 Mar 24 15:05 System.map-3.13.0-49-generic
-rw-r-----  1 root root 1162936320 Jan 15 12:00 ubie1410.iso
-rw-------  1 root root    5814112 Jan 13 14:12 vmlinuz-3.13.0-45-generic
-rw-------  1 root root    5814592 Mar 10 15:43 vmlinuz-3.13.0-46-generic
-rw-------  1 root root    5815680 Mar 12 06:52 vmlinuz-3.13.0-48-generic
-rw-------  1 root root    5815264 Mar 24 15:05 vmlinuz-3.13.0-49-generic
sysop@1404mini:~$ 

```
where you can see I do need to do a bit of house cleaning my-self.

Can you try again these commands .. so they are posted in a readable format ?
And we take off where I left off.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by laphyzz2 on 2015-04-13
uname -r ```
 uname -r 3.13.0-33-generic 
```  ```
 dpkg -l | grep linux-  ii  linux-firmware                      1.127.11                         all          Firmware for Linux kernel drivers  iU  linux-generic                       3.13.0.49.56                     amd64        Complete Generic Linux kernel and headers  ii  linux-headers-3.13.0-33             3.13.0-33.58                     all          Header files related to Linux kernel version 3.13.0  ii  linux-headers-3.13.0-33-generic     3.13.0-33.58                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP  ii  linux-headers-3.13.0-34             3.13.0-34.60                     all          Header files related to Linux kernel version 3.13.0  ii  linux-headers-3.13.0-34-generic     3.13.0-34.60                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP  ii  linux-headers-3.13.0-36             3.13.0-36.63                     all          Header files related to Linux kernel version 3.13.0  ii  linux-headers-3.13.0-36-generic     3.13.0-36.63                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP  ii  linux-headers-3.13.0-37             3.13.0-37.64                     all          Header files related to Linux kernel version 3.13.0  ii  linux-headers-3.13.0-37-generic     3.13.0-37.64                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP  ii  linux-headers-3.13.0-39             3.13.0-39.66                     all          Header files related to Linux kernel version 3.13.0  ii  linux-headers-3.13.0-39-generic     3.13.0-39.66                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP  ii  linux-headers-3.13.0-40             3.13.0-40.69                     all          Header files related to Linux kernel version 3.13.0  ii  linux-headers-3.13.0-40-generic     3.13.0-40.69                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP  ii  linux-headers-3.13.0-41             3.13.0-41.70                     all          Header files related to Linux kernel version 3.13.0  ii  linux-headers-3.13.0-41-generic     3.13.0-41.70                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP  ii  linux-headers-3.13.0-43             3.13.0-43.72                     all          Header files related to Linux kernel version 3.13.0  ii  linux-headers-3.13.0-43-generic     3.13.0-43.72                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP  ii  linux-headers-3.13.0-44             3.13.0-44.73                     all          Header files related to Linux kernel version 3.13.0  ii  linux-headers-3.13.0-44-generic     3.13.0-44.73                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP  ii  linux-headers-3.13.0-49             3.13.0-49.81                     all          Header files related to Linux kernel version 3.13.0  ii  linux-headers-3.13.0-49-generic     3.13.0-49.81                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP  ii  linux-headers-generic               3.13.0.49.56                     amd64        Generic Linux kernel headers  rc  linux-image-3.13.0-24-generic       3.13.0-24.47                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP  rc  linux-image-3.13.0-27-generic       3.13.0-27.50                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP  rc  linux-image-3.13.0-29-generic       3.13.0-29.53                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP  rc  linux-image-3.13.0-30-generic       3.13.0-30.55                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP  rc  linux-image-3.13.0-32-generic       3.13.0-32.57                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP  ii  linux-image-3.13.0-33-generic       3.13.0-33.58                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP  ii  linux-image-3.13.0-34-generic       3.13.0-34.60                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP  rc  linux-image-3.13.0-35-generic       3.13.0-35.62                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP  ii  linux-image-3.13.0-36-generic       3.13.0-36.63                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP  ii  linux-image-3.13.0-37-generic       3.13.0-37.64                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP  ii  linux-image-3.13.0-39-generic       3.13.0-39.66                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP  ii  linux-image-3.13.0-40-generic       3.13.0-40.69                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP  ii  linux-image-3.13.0-41-generic       3.13.0-41.70                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP  ic  linux-image-3.13.0-43-generic       3.13.0-43.72                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP  iF  linux-image-3.13.0-44-generic       3.13.0-44.73                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP  rc  linux-image-extra-3.13.0-24-generic 3.13.0-24.47                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP  rc  linux-image-extra-3.13.0-27-generic 3.13.0-27.50                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP  rc  linux-image-extra-3.13.0-29-generic 3.13.0-29.53                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP  rc  linux-image-extra-3.13.0-30-generic 3.13.0-30.55                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP  rc  linux-image-extra-3.13.0-32-generic 3.13.0-32.57                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP  ii  linux-image-extra-3.13.0-33-generic 3.13.0-33.58                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP  ii  linux-image-extra-3.13.0-34-generic 3.13.0-34.60                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP  rc  linux-image-extra-3.13.0-35-generic 3.13.0-35.62                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP  ii  linux-image-extra-3.13.0-36-generic 3.13.0-36.63                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP  ii  linux-image-extra-3.13.0-37-generic 3.13.0-37.64                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP  ii  linux-image-extra-3.13.0-39-generic 3.13.0-39.66                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP  ii  linux-image-extra-3.13.0-40-generic 3.13.0-40.69                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP  ii  linux-image-extra-3.13.0-41-generic 3.13.0-41.70                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP  rH  linux-image-extra-3.13.0-43-generic 3.13.0-43.72                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP  iU  linux-image-extra-3.13.0-44-generic 3.13.0-44.73                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP  rc  linux-image-extra-3.13.0-46-generic 3.13.0-46.79                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP  iU  linux-image-extra-3.13.0-49-generic 3.13.0-49.81                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP  iU  linux-image-generic                 3.13.0.49.56                     amd64        Generic Linux kernel image 
```  ```
 ls -al /boot  total 224536  drwxr-xr-x  4 root root     3072 Apr 13 21:27 .  drwxr-xr-x 23 root root     4096 Apr 13 20:54 ..  -rw-r--r--  1 root root  1162712 Jul 29  2014 abi-3.13.0-33-generic  -rw-r--r--  1 root root  1162712 Aug 13  2014 abi-3.13.0-34-generic  -rw-r--r--  1 root root  1163858 Sep  3  2014 abi-3.13.0-36-generic  -rw-r--r--  1 root root  1164489 Sep 22  2014 abi-3.13.0-37-generic  -rw-r--r--  1 root root  1164547 Oct 28 14:25 abi-3.13.0-39-generic  -rw-r--r--  1 root root  1164509 Nov 13 18:30 abi-3.13.0-40-generic  -rw-r--r--  1 root root  1164720 Nov 25 15:34 abi-3.13.0-41-generic  -rw-r--r--  1 root root  1164720 Dec 16 01:17 abi-3.13.0-44-generic  -rw-r--r--  1 root root   165611 Jul 29  2014 config-3.13.0-33-generic  -rw-r--r--  1 root root   165611 Aug 13  2014 config-3.13.0-34-generic  -rw-r--r--  1 root root   165671 Sep  3  2014 config-3.13.0-36-generic  -rw-r--r--  1 root root   165712 Sep 22  2014 config-3.13.0-37-generic  -rw-r--r--  1 root root   165712 Oct 28 14:25 config-3.13.0-39-generic  -rw-r--r--  1 root root   165745 Nov 13 18:30 config-3.13.0-40-generic  -rw-r--r--  1 root root   165745 Nov 25 15:34 config-3.13.0-41-generic  -rw-r--r--  1 root root   165748 Dec 16 01:17 config-3.13.0-44-generic  drwxr-xr-x  5 root root     1024 Apr 13 20:57 grub  -rw-r--r--  1 root root 20085652 Aug 12  2014 initrd.img-3.13.0-33-generic  -rw-r--r--  1 root root 20085679 Aug 14  2014 initrd.img-3.13.0-34-generic  -rw-r--r--  1 root root 20108251 Oct 28 13:19 initrd.img-3.13.0-36-generic  -rw-r--r--  1 root root 20109817 Oct 28 13:22 initrd.img-3.13.0-37-generic  -rw-r--r--  1 root root 20109475 Oct 29 06:44 initrd.img-3.13.0-39-generic  -rw-r--r--  1 root root 20114942 Nov 25 06:36 initrd.img-3.13.0-40-generic  -rw-r--r--  1 root root 20144934 Dec 11 07:01 initrd.img-3.13.0-41-generic  -rw-r--r--  1 root root  3463278 Apr 13 20:54 initrd.img-3.13.0-46-generic  drwx------  2 root root    12288 May 23  2014 lost+found  -rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin  -rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf  -rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin  -rw-------  1 root root  3381262 Jul 29  2014 System.map-3.13.0-33-generic  -rw-------  1 root root  3381262 Aug 13  2014 System.map-3.13.0-34-generic  -rw-------  1 root root  3386479 Sep  3  2014 System.map-3.13.0-36-generic  -rw-------  1 root root  3386945 Sep 22  2014 System.map-3.13.0-37-generic  -rw-------  1 root root  3386936 Oct 28 14:25 System.map-3.13.0-39-generic  -rw-------  1 root root  3387231 Nov 13 18:30 System.map-3.13.0-40-generic  -rw-------  1 root root  3388792 Nov 25 15:34 System.map-3.13.0-41-generic  -rw-------  1 root root  3388834 Dec 16 01:17 System.map-3.13.0-44-generic  -rw-------  1 root root  5798688 Jul 29  2014 vmlinuz-3.13.0-33-generic  -rw-------  1 root root  5797728 Aug 13  2014 vmlinuz-3.13.0-34-generic  -rw-------  1 root root  5806848 Sep  3  2014 vmlinuz-3.13.0-36-generic  -rw-------  1 root root  5808832 Sep 22  2014 vmlinuz-3.13.0-37-generic  -rw-------  1 root root  5808544 Oct 28 14:25 vmlinuz-3.13.0-39-generic  -rw-------  1 root root  5808960 Nov 13 18:30 vmlinuz-3.13.0-40-generic  -rw-------  1 root root  5814112 Nov 25 15:34 vmlinuz-3.13.0-41-generic  -rw-------  1 root root  5814496 Dec 16 01:17 vmlinuz-3.13.0-44-generic  
```

---

### Post by laphyzz2 on 2015-04-13
ok I don't knwo how to stop it from doing that, I even put a new line between each line of code..

---

### Post by Bashing-om on 2015-04-13
laphyzz2; Humm  ..

I sure do not know what you are not doing to transfer the outputs;
I generally use "advanced reply" button and in the response ->
All that should be required is a simple copy/paste.
I do from the keyboard and copy/paste :
in the post I type [noparse]```
[/noparse]
and paste in the code and then terminate the code block:
[noparse]
```[/noparse].
Note that the terminating 'code' is preceeded by '/' .

Not to be difficult to work with myself, but if the requested outputs are not formatted, most impossible to work with in an attempt to minimize the probability of error. Breaking or messing up your system is the last thing I want to see happen. I desire that any instruction be exact and explicit . Double/triple checked for errors -> formatted outputs that a readily readable are required.

I personally have never experienced a problem following any of the tutorial's 3 methods.

[INDENT][INDENT][INDENT]this too we will get through
[/INDENT][/INDENT][/INDENT]

---

### Post by laphyzz2 on 2015-04-13
I've done that and it still dues it I will try once more

```

root@ID-Main-Server:/home/robert# uname -r
3.13.0-33-generic

```
```

root@ID-Main-Server:/home/robert# dpkg -l | grep linux-
ii  linux-firmware                      1.127.11                         all          Firmware for Linux kernel drivers
iU  linux-generic                       3.13.0.49.56                     amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-33             3.13.0-33.58                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-33-generic     3.13.0-33.58                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-34             3.13.0-34.60                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic     3.13.0-34.60                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-36             3.13.0-36.63                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-36-generic     3.13.0-36.63                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-37             3.13.0-37.64                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic     3.13.0-37.64                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-39             3.13.0-39.66                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic     3.13.0-39.66                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-40             3.13.0-40.69                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-40-generic     3.13.0-40.69                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-41             3.13.0-41.70                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-41-generic     3.13.0-41.70                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-43             3.13.0-43.72                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-generic     3.13.0-43.72                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-44             3.13.0-44.73                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic     3.13.0-44.73                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-49             3.13.0-49.81                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic     3.13.0-49.81                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic               3.13.0.49.56                     amd64        Generic Linux kernel headers
rc  linux-image-3.13.0-24-generic       3.13.0-24.47                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-27-generic       3.13.0-27.50                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-29-generic       3.13.0-29.53                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-30-generic       3.13.0-30.55                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-32-generic       3.13.0-32.57                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-33-generic       3.13.0-33.58                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic       3.13.0-34.60                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-35-generic       3.13.0-35.62                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic       3.13.0-36.63                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic       3.13.0-37.64                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic       3.13.0-39.66                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-40-generic       3.13.0-40.69                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-41-generic       3.13.0-41.70                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ic  linux-image-3.13.0-43-generic       3.13.0-43.72                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-3.13.0-44-generic       3.13.0-44.73                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-24-generic 3.13.0-24.47                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-27-generic 3.13.0-27.50                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-29-generic 3.13.0-29.53                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-30-generic 3.13.0-30.55                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic 3.13.0-32.57                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-33-generic 3.13.0-33.58                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic 3.13.0-34.60                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-35-generic 3.13.0-35.62                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic 3.13.0-36.63                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic 3.13.0-37.64                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic 3.13.0-39.66                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic 3.13.0-40.69                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-41-generic 3.13.0-41.70                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-43-generic 3.13.0-43.72                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-extra-3.13.0-44-generic 3.13.0-44.73                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-46-generic 3.13.0-46.79                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-extra-3.13.0-49-generic 3.13.0-49.81                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                 3.13.0.49.56                     amd64        Generic Linux kernel image

```
```

root@ID-Main-Server:/home/robert# ls -al /boot
total 224536
drwxr-xr-x  4 root root     3072 Apr 13 21:27 .
drwxr-xr-x 23 root root     4096 Apr 13 20:54 ..
-rw-r--r--  1 root root  1162712 Jul 29  2014 abi-3.13.0-33-generic
-rw-r--r--  1 root root  1162712 Aug 13  2014 abi-3.13.0-34-generic
-rw-r--r--  1 root root  1163858 Sep  3  2014 abi-3.13.0-36-generic
-rw-r--r--  1 root root  1164489 Sep 22  2014 abi-3.13.0-37-generic
-rw-r--r--  1 root root  1164547 Oct 28 14:25 abi-3.13.0-39-generic
-rw-r--r--  1 root root  1164509 Nov 13 18:30 abi-3.13.0-40-generic
-rw-r--r--  1 root root  1164720 Nov 25 15:34 abi-3.13.0-41-generic
-rw-r--r--  1 root root  1164720 Dec 16 01:17 abi-3.13.0-44-generic
-rw-r--r--  1 root root   165611 Jul 29  2014 config-3.13.0-33-generic
-rw-r--r--  1 root root   165611 Aug 13  2014 config-3.13.0-34-generic
-rw-r--r--  1 root root   165671 Sep  3  2014 config-3.13.0-36-generic
-rw-r--r--  1 root root   165712 Sep 22  2014 config-3.13.0-37-generic
-rw-r--r--  1 root root   165712 Oct 28 14:25 config-3.13.0-39-generic
-rw-r--r--  1 root root   165745 Nov 13 18:30 config-3.13.0-40-generic
-rw-r--r--  1 root root   165745 Nov 25 15:34 config-3.13.0-41-generic
-rw-r--r--  1 root root   165748 Dec 16 01:17 config-3.13.0-44-generic
drwxr-xr-x  5 root root     1024 Apr 13 20:57 grub
-rw-r--r--  1 root root 20085652 Aug 12  2014 initrd.img-3.13.0-33-generic
-rw-r--r--  1 root root 20085679 Aug 14  2014 initrd.img-3.13.0-34-generic
-rw-r--r--  1 root root 20108251 Oct 28 13:19 initrd.img-3.13.0-36-generic
-rw-r--r--  1 root root 20109817 Oct 28 13:22 initrd.img-3.13.0-37-generic
-rw-r--r--  1 root root 20109475 Oct 29 06:44 initrd.img-3.13.0-39-generic
-rw-r--r--  1 root root 20114942 Nov 25 06:36 initrd.img-3.13.0-40-generic
-rw-r--r--  1 root root 20144934 Dec 11 07:01 initrd.img-3.13.0-41-generic
-rw-r--r--  1 root root  3463278 Apr 13 20:54 initrd.img-3.13.0-46-generic
drwx------  2 root root    12288 May 23  2014 lost+found
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3381262 Jul 29  2014 System.map-3.13.0-33-generic
-rw-------  1 root root  3381262 Aug 13  2014 System.map-3.13.0-34-generic
-rw-------  1 root root  3386479 Sep  3  2014 System.map-3.13.0-36-generic
-rw-------  1 root root  3386945 Sep 22  2014 System.map-3.13.0-37-generic
-rw-------  1 root root  3386936 Oct 28 14:25 System.map-3.13.0-39-generic
-rw-------  1 root root  3387231 Nov 13 18:30 System.map-3.13.0-40-generic
-rw-------  1 root root  3388792 Nov 25 15:34 System.map-3.13.0-41-generic
-rw-------  1 root root  3388834 Dec 16 01:17 System.map-3.13.0-44-generic
-rw-------  1 root root  5798688 Jul 29  2014 vmlinuz-3.13.0-33-generic
-rw-------  1 root root  5797728 Aug 13  2014 vmlinuz-3.13.0-34-generic
-rw-------  1 root root  5806848 Sep  3  2014 vmlinuz-3.13.0-36-generic
-rw-------  1 root root  5808832 Sep 22  2014 vmlinuz-3.13.0-37-generic
-rw-------  1 root root  5808544 Oct 28 14:25 vmlinuz-3.13.0-39-generic
-rw-------  1 root root  5808960 Nov 13 18:30 vmlinuz-3.13.0-40-generic
-rw-------  1 root root  5814112 Nov 25 15:34 vmlinuz-3.13.0-41-generic
-rw-------  1 root root  5814496 Dec 16 01:17 vmlinuz-3.13.0-44-generic

```

---

### Post by Bashing-om on 2015-04-13
laphyzz2; Hey, hey;

3rd time is the charm .. This I can work with.
There are these conditions:
```

iU  linux-generic
iU  linux-image-generic

```
where the 'U' in the second field indicates "unpacked" -> so the files are not 'placed'  .. hummmm 
that I find troubling .. but laying that aside for the moment let's try and see what results:
```

sudo dpkg -P linux-headers-3.13.0-{36,37,39,40,41,43,44}
sudo dpkg -P linux-headers-3.13.0-{36,37,39,40,41,43,44}-generic
sudo dpkg -P linux-image-3.13.0-{36,37,39,40,41,43,44}-generic
sudo dpkg -P linux-image-generic-3.13.0-{36,37,39,40,41,43,44}-generic

```
copy and paste to preclude transcription errors.
See if we can get some head room before tackling the 'iU' packages. We keep the booting kernel -33 ( why oh why booting such an old old kernel ??) ..
Then we try and get the -48 kernel installed as the backup kernel for -49  once we get the -49 kernel fully installed.

but, but ... small steps
[INDENT][INDENT][INDENT]1 small step at the time
[/INDENT][/INDENT][/INDENT]

---

### Post by laphyzz2 on 2015-04-13
```

sudo dpkg -P linux-headers-3.13.0-{36,37,39,40,41,43,44}
dpkg: dependency problems prevent removal of linux-headers-3.13.0-36:
 linux-headers-3.13.0-36-generic depends on linux-headers-3.13.0-36.

dpkg: error processing package linux-headers-3.13.0-36 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.13.0-37:
 linux-headers-3.13.0-37-generic depends on linux-headers-3.13.0-37.

dpkg: error processing package linux-headers-3.13.0-37 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.13.0-39:
 linux-headers-3.13.0-39-generic depends on linux-headers-3.13.0-39.

dpkg: error processing package linux-headers-3.13.0-39 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.13.0-40:
 linux-headers-3.13.0-40-generic depends on linux-headers-3.13.0-40.

dpkg: error processing package linux-headers-3.13.0-40 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.13.0-41:
 linux-headers-3.13.0-41-generic depends on linux-headers-3.13.0-41.

dpkg: error processing package linux-headers-3.13.0-41 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.13.0-43:
 linux-headers-3.13.0-43-generic depends on linux-headers-3.13.0-43.

dpkg: error processing package linux-headers-3.13.0-43 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.13.0-44:
 linux-headers-3.13.0-44-generic depends on linux-headers-3.13.0-44.

dpkg: error processing package linux-headers-3.13.0-44 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-3.13.0-36
 linux-headers-3.13.0-37
 linux-headers-3.13.0-39
 linux-headers-3.13.0-40
 linux-headers-3.13.0-41
 linux-headers-3.13.0-43
 linux-headers-3.13.0-44

```

```

 sudo dpkg -P linux-headers-3.13.0-{36,37,39,40,41,43,44}-generic
(Reading database ... 321882 files and directories currently installed.)
Removing linux-headers-3.13.0-36-generic (3.13.0-36.63) ...
Removing linux-headers-3.13.0-37-generic (3.13.0-37.64) ...
Removing linux-headers-3.13.0-39-generic (3.13.0-39.66) ...
Removing linux-headers-3.13.0-40-generic (3.13.0-40.69) ...
Removing linux-headers-3.13.0-41-generic (3.13.0-41.70) ...
Removing linux-headers-3.13.0-43-generic (3.13.0-43.72) ...
Removing linux-headers-3.13.0-44-generic (3.13.0-44.73) ...

```

```

sudo dpkg -P linux-headers-3.13.0-{36,37,39,40,41,43,44}-generic
(Reading database ... 321882 files and directories currently installed.)
Removing linux-headers-3.13.0-36-generic (3.13.0-36.63) ...
Removing linux-headers-3.13.0-37-generic (3.13.0-37.64) ...
Removing linux-headers-3.13.0-39-generic (3.13.0-39.66) ...
Removing linux-headers-3.13.0-40-generic (3.13.0-40.69) ...
Removing linux-headers-3.13.0-41-generic (3.13.0-41.70) ...
Removing linux-headers-3.13.0-43-generic (3.13.0-43.72) ...
Removing linux-headers-3.13.0-44-generic (3.13.0-44.73) ...
root@ID-Main-Server:/home/robert# ^C
root@ID-Main-Server:/home/robert# sudo dpkg -P linux-image-3.13.0-{36,37,39,40,41,43,44}-generic
dpkg: dependency problems prevent removal of linux-image-3.13.0-36-generic:
 linux-image-extra-3.13.0-36-generic depends on linux-image-3.13.0-36-generic.

dpkg: error processing package linux-image-3.13.0-36-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-37-generic:
 linux-image-extra-3.13.0-37-generic depends on linux-image-3.13.0-37-generic.

dpkg: error processing package linux-image-3.13.0-37-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-39-generic:
 linux-image-extra-3.13.0-39-generic depends on linux-image-3.13.0-39-generic.

dpkg: error processing package linux-image-3.13.0-39-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-40-generic:
 linux-image-extra-3.13.0-40-generic depends on linux-image-3.13.0-40-generic.

dpkg: error processing package linux-image-3.13.0-40-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-41-generic:
 linux-image-extra-3.13.0-41-generic depends on linux-image-3.13.0-41-generic.

dpkg: error processing package linux-image-3.13.0-41-generic (--purge):
 dependency problems - not removing
(Reading database ... 254982 files and directories currently installed.)
Removing linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Purging configuration files for linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Removing linux-image-3.13.0-44-generic (3.13.0-44.73) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-44-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-41-generic
Found initrd image: /boot/initrd.img-3.13.0-41-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-3.13.0-44-generic (3.13.0-44.73) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic
Errors were encountered while processing:
 linux-image-3.13.0-36-generic
 linux-image-3.13.0-37-generic
 linux-image-3.13.0-39-generic
 linux-image-3.13.0-40-generic
 linux-image-3.13.0-41-generic

```

```

sudo dpkg -P linux-image-generic-3.13.0-{36,37,39,40,41,43,44}-generic
dpkg: warning: ignoring request to remove linux-image-generic-3.13.0-36-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-generic-3.13.0-37-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-generic-3.13.0-39-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-generic-3.13.0-40-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-generic-3.13.0-41-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-generic-3.13.0-43-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-generic-3.13.0-44-generic which isn't installed

```

---

### Post by ian-weisser on 2015-04-13
You have probably freed up enough space for 'sudo apt-get autoremove' (which is much easier) to finally work.
And for those 70 long delayed upgrades ('sudo apt-get upgrade').

It's a bad idea to use sudo *and* root at the same time. Try to avoid that.

---

### Post by laphyzz2 on 2015-04-13
```

sudo dpkg -P linux-headers-3.13.0-{36,37,39,40,41,43,44}
dpkg: dependency problems prevent removal of linux-headers-3.13.0-36:
 linux-headers-3.13.0-36-generic depends on linux-headers-3.13.0-36.

dpkg: error processing package linux-headers-3.13.0-36 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.13.0-37:
 linux-headers-3.13.0-37-generic depends on linux-headers-3.13.0-37.

dpkg: error processing package linux-headers-3.13.0-37 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.13.0-39:
 linux-headers-3.13.0-39-generic depends on linux-headers-3.13.0-39.

dpkg: error processing package linux-headers-3.13.0-39 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.13.0-40:
 linux-headers-3.13.0-40-generic depends on linux-headers-3.13.0-40.

dpkg: error processing package linux-headers-3.13.0-40 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.13.0-41:
 linux-headers-3.13.0-41-generic depends on linux-headers-3.13.0-41.

dpkg: error processing package linux-headers-3.13.0-41 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.13.0-43:
 linux-headers-3.13.0-43-generic depends on linux-headers-3.13.0-43.

dpkg: error processing package linux-headers-3.13.0-43 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.13.0-44:
 linux-headers-3.13.0-44-generic depends on linux-headers-3.13.0-44.

dpkg: error processing package linux-headers-3.13.0-44 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-3.13.0-36
 linux-headers-3.13.0-37
 linux-headers-3.13.0-39
 linux-headers-3.13.0-40
 linux-headers-3.13.0-41
 linux-headers-3.13.0-43
 linux-headers-3.13.0-44

```

```

 sudo dpkg -P linux-headers-3.13.0-{36,37,39,40,41,43,44}-generic
(Reading database ... 321882 files and directories currently installed.)
Removing linux-headers-3.13.0-36-generic (3.13.0-36.63) ...
Removing linux-headers-3.13.0-37-generic (3.13.0-37.64) ...
Removing linux-headers-3.13.0-39-generic (3.13.0-39.66) ...
Removing linux-headers-3.13.0-40-generic (3.13.0-40.69) ...
Removing linux-headers-3.13.0-41-generic (3.13.0-41.70) ...
Removing linux-headers-3.13.0-43-generic (3.13.0-43.72) ...
Removing linux-headers-3.13.0-44-generic (3.13.0-44.73) ...

```

```

sudo dpkg -P linux-headers-3.13.0-{36,37,39,40,41,43,44}-generic
(Reading database ... 321882 files and directories currently installed.)
Removing linux-headers-3.13.0-36-generic (3.13.0-36.63) ...
Removing linux-headers-3.13.0-37-generic (3.13.0-37.64) ...
Removing linux-headers-3.13.0-39-generic (3.13.0-39.66) ...
Removing linux-headers-3.13.0-40-generic (3.13.0-40.69) ...
Removing linux-headers-3.13.0-41-generic (3.13.0-41.70) ...
Removing linux-headers-3.13.0-43-generic (3.13.0-43.72) ...
Removing linux-headers-3.13.0-44-generic (3.13.0-44.73) ...
root@ID-Main-Server:/home/robert# ^C
root@ID-Main-Server:/home/robert# sudo dpkg -P linux-image-3.13.0-{36,37,39,40,41,43,44}-generic
dpkg: dependency problems prevent removal of linux-image-3.13.0-36-generic:
 linux-image-extra-3.13.0-36-generic depends on linux-image-3.13.0-36-generic.

dpkg: error processing package linux-image-3.13.0-36-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-37-generic:
 linux-image-extra-3.13.0-37-generic depends on linux-image-3.13.0-37-generic.

dpkg: error processing package linux-image-3.13.0-37-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-39-generic:
 linux-image-extra-3.13.0-39-generic depends on linux-image-3.13.0-39-generic.

dpkg: error processing package linux-image-3.13.0-39-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-40-generic:
 linux-image-extra-3.13.0-40-generic depends on linux-image-3.13.0-40-generic.

dpkg: error processing package linux-image-3.13.0-40-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-41-generic:
 linux-image-extra-3.13.0-41-generic depends on linux-image-3.13.0-41-generic.

dpkg: error processing package linux-image-3.13.0-41-generic (--purge):
 dependency problems - not removing
(Reading database ... 254982 files and directories currently installed.)
Removing linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Purging configuration files for linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Removing linux-image-3.13.0-44-generic (3.13.0-44.73) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-44-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-41-generic
Found initrd image: /boot/initrd.img-3.13.0-41-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-3.13.0-44-generic (3.13.0-44.73) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic
Errors were encountered while processing:
 linux-image-3.13.0-36-generic
 linux-image-3.13.0-37-generic
 linux-image-3.13.0-39-generic
 linux-image-3.13.0-40-generic
 linux-image-3.13.0-41-generic

```

```

sudo dpkg -P linux-image-generic-3.13.0-{36,37,39,40,41,43,44}-generic
dpkg: warning: ignoring request to remove linux-image-generic-3.13.0-36-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-generic-3.13.0-37-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-generic-3.13.0-39-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-generic-3.13.0-40-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-generic-3.13.0-41-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-generic-3.13.0-43-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-generic-3.13.0-44-generic which isn't installed

```

---

### Post by laphyzz2 on 2015-04-13
```

apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-43-generic : Depends: linux-image-3.13.0-43-generic but it is not installed
 linux-image-extra-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic but it is not installed
 linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.13.0-49-generic but it is not installed
E: Unmet dependencies. Try using -f.

```

```

apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-43-generic : Depends: linux-image-3.13.0-43-generic but it is not installed
 linux-image-extra-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic but it is not installed
 linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.13.0-49-generic but it is not installed
E: Unmet dependencies. Try using -f.


```

---

### Post by Bashing-om on 2015-04-13
laphyzz2; Hey !

Looking much better.
Let's get a fresh new look at things before proceeding.
show us anew:
```

df -h
dpkg -l | grep linux-

```
then we see about why the linux-image-extra-3.13.0-43-generic and -44 were not removed.
And complete the removal and old kernel ( config files) .

[INDENT][INDENT]still, small steps
[/INDENT][/INDENT]

---

### Post by laphyzz2 on 2015-04-13
```

df -h
Filesystem                             Size  Used Avail Use% Mounted on
/dev/mapper/ID--Main--Server--vg-root  1.8T   15G  1.7T   1% /
none                                   4.0K     0  4.0K   0% /sys/fs/cgroup
udev                                   3.8G   12K  3.8G   1% /dev
tmpfs                                  772M  648K  771M   1% /run
none                                   5.0M     0  5.0M   0% /run/lock
none                                   3.8G     0  3.8G   0% /run/shm
none                                   100M     0  100M   0% /run/user
/dev/sda1                              236M  218M  5.4M  98% /boot


```

```

dpkg -l | grep linux-
ii  linux-firmware                      1.127.11                         all          Firmware for Linux kernel drivers
iU  linux-generic                       3.13.0.49.56                     amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-33             3.13.0-33.58                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-33-generic     3.13.0-33.58                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-34             3.13.0-34.60                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic     3.13.0-34.60                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
pi  linux-headers-3.13.0-36             3.13.0-36.63                     all          Header files related to Linux kernel version 3.13.0
pi  linux-headers-3.13.0-37             3.13.0-37.64                     all          Header files related to Linux kernel version 3.13.0
pi  linux-headers-3.13.0-39             3.13.0-39.66                     all          Header files related to Linux kernel version 3.13.0
pi  linux-headers-3.13.0-40             3.13.0-40.69                     all          Header files related to Linux kernel version 3.13.0
pi  linux-headers-3.13.0-41             3.13.0-41.70                     all          Header files related to Linux kernel version 3.13.0
pi  linux-headers-3.13.0-43             3.13.0-43.72                     all          Header files related to Linux kernel version 3.13.0
pi  linux-headers-3.13.0-44             3.13.0-44.73                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49             3.13.0-49.81                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic     3.13.0-49.81                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic               3.13.0.49.56                     amd64        Generic Linux kernel headers
rc  linux-image-3.13.0-24-generic       3.13.0-24.47                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-27-generic       3.13.0-27.50                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-29-generic       3.13.0-29.53                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-30-generic       3.13.0-30.55                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-32-generic       3.13.0-32.57                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-33-generic       3.13.0-33.58                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic       3.13.0-34.60                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-35-generic       3.13.0-35.62                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
pi  linux-image-3.13.0-36-generic       3.13.0-36.63                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
pi  linux-image-3.13.0-37-generic       3.13.0-37.64                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
pi  linux-image-3.13.0-39-generic       3.13.0-39.66                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
pi  linux-image-3.13.0-40-generic       3.13.0-40.69                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
pi  linux-image-3.13.0-41-generic       3.13.0-41.70                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-24-generic 3.13.0-24.47                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-27-generic 3.13.0-27.50                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-29-generic 3.13.0-29.53                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-30-generic 3.13.0-30.55                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic 3.13.0-32.57                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-33-generic 3.13.0-33.58                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic 3.13.0-34.60                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-35-generic 3.13.0-35.62                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic 3.13.0-36.63                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic 3.13.0-37.64                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic 3.13.0-39.66                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic 3.13.0-40.69                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-41-generic 3.13.0-41.70                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-43-generic 3.13.0-43.72                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-extra-3.13.0-44-generic 3.13.0-44.73                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-46-generic 3.13.0-46.79                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-extra-3.13.0-49-generic 3.13.0-49.81                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                 3.13.0.49.56                     amd64        Generic Linux kernel image

```

---

### Post by Bashing-om on 2015-04-13
laphyzz2; Yuk ....

Not at all what I had anticipated or hoped for... 

What in the world is going on that the kernels are now marked as '(P)urged (i)installed,
We do want to re-install linux-generic and linux-image-generic and though we are down with capacity usage to 98%, still do not think it is enough room to try and install.
Let's poke a bit more at removing kernels, see if we can determine the why they - at large - did not completely remove (pi).

Let's poke at it and see what bites:
```

sudo apt-get purge linux-image-3.13.0-34-generic
sudo apt-get purge linux-image-extra-3.13.0-34-generic
sudo apt-get purge linux-headers-3.13.0-34-generic
sudo apt-get purge linux-headers-3.13.0-34

```
maybe now get an idea of what is not going on.

[INDENT][INDENT][INDENT]making haste
[INDENT][INDENT][INDENT]real real slow
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by laphyzz2 on 2015-04-13
This tends to happen to me, if its almost imposable to happen it happens.

```

sudo apt-get purge linux-image-3.13.0-34-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-34-generic : Depends: linux-image-3.13.0-34-generic but it is not going to be installed
 linux-image-extra-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic but it is not going to be installed
 linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

```

apt-get purge linux-image-extra-3.13.0-34-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic but it is not going to be installed
 linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

```

apt-get purge linux-headers-3.13.0-34-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic but it is not going to be installed
 linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

```

apt-get purge linux-headers-3.13.0-34
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-headers-3.13.0-34-generic : Depends: linux-headers-3.13.0-34 but it is not going to be installed
 linux-image-extra-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic but it is not going to be installed
 linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Bashing-om on 2015-04-13
laphyzz2; ermmm ...

I do not understand all I do not know about this sloppyation. Making little sense of things, getting those dependency conditions.
Let's change our focus to the -44 kernel.
We have it only  partially installed, of the 4 modules required we are missing the  linux-image module.
Let's take a gentler smaller poke at it.
```

sudo apt-get --purge remove linux-image-extra-3.13.0-44-generic

```
see if we can selectively remove this component and maybe work our way back to the -34 kernel.

[INDENT][INDENT]one of those times I wonder
[/INDENT][/INDENT]

---

### Post by laphyzz2 on 2015-04-13
```

apt-get --purge remove linux-image-extra-3.13.0-44-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ID-Main-Server:/home/robert#

```

---

### Post by Bashing-om on 2015-04-13
laphyzz2; Well ..

Looks to be a step in the right direction.
Change in focus again . let's see if we can give the package manager what it wants, and maybe the error will go away.
try:
```

sudo apt-get install --reinstall linux-image-extra-3.13.0-49
sudo apt-get install --reinstall linux-image-3.13.0-49
sudo apt-get install --reinstall linux-headers-3.13.0-49-generic
sudo apt-get install --reinstall linux-headers-3.13.0-49

```

Or see what it will now take to get them installed.

[INDENT][INDENT][INDENT]not all bad
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-04-13
laphyzz2; Another thought;

As when if the -49 kernel will not install is back to the 'iU' packages:
Try and install them - operating head room permitting.
```

sudo apt-get install --reinstall linux-generic
sudo apt-get install --reinstall linux-image-generic

```
see then if we can go back to work on all those 'pi' packages, see if we can get them off the system.

[INDENT][INDENT]beating around the tree
[INDENT][INDENT][INDENT][INDENT]trying to see the forest
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by laphyzz2 on 2015-04-14
sorry for the delay I fell a sleep

```

sudo apt-get install --reinstall linux-image-extra-3.13.0-49
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'linux-image-extra-3.13.0-49-generic' for regex 'linux-image-extra-3.13.0-49'
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic but it is not going to be installed
 linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

```

sudo apt-get install --reinstall linux-image-3.13.0-49
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'linux-image-3.13.0-49-lowlatency' for regex 'linux-image-3.13.0-49'
Note, selecting 'linux-image-3.13.0-49-generic' for regex 'linux-image-3.13.0-49'
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

```

sudo apt-get install --reinstall linux-headers-3.13.0-49-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic but it is not going to be installed
 linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

```

apt-get install --reinstall linux-headers-3.13.0-49
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic but it is not going to be installed
 linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

```

sudo apt-get install --reinstall linux-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic but it is not going to be installed
 linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

```

apt-get install --reinstall linux-image-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic but it is not going to be installed
 linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ID-Main-Server:/home/robert#

```

](*,)

---

### Post by dino99 on 2015-04-14
when things are going wrong, its time thinking to clean the room:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by ian-weisser on 2015-04-14
Have you run apt-get autoremove yet? Good time for it.

> **laphyzz2 said:**
>  linux-image-extra-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic but it is not going to be installed

The -44 kernel was removed from the repositories when it was superseded. Your system will never be able to install it. 
Try: apt-get autoremove linux-image-extra-3.13.0-44-generic linux-image-3.13.0-44-generic


> **laphyzz2 said:**
>  linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed

Try: apt-get install --reinstall linux-image-3.13.0-49-generic linux-image-generic

---

### Post by laphyzz2 on 2015-04-14
```

root@ID-Main-Server:/home/robert# apt-get clean
root@ID-Main-Server:/home/robert#

```

```

root@ID-Main-Server:/home/robert# apt-get autoclean
Reading package lists... Done
Building dependency tree
Reading state information... Done
root@ID-Main-Server:/home/robert#

```

```

root@ID-Main-Server:/home/robert# apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-43-generic : Depends: linux-image-3.13.0-43-generic but it is not installed
 linux-image-extra-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic but it is not installed
 linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.13.0-49-generic but it is not installed
E: Unmet dependencies. Try using -f.
root@ID-Main-Server:/home/robert#

```

```

root@ID-Main-Server:/home/robert# apt-get update
Ign http://gb.archive.ubuntu.com trusty InRelease
Ign http://gb.archive.ubuntu.com trusty-updates InRelease
Ign http://gb.archive.ubuntu.com trusty-backports InRelease
Hit http://gb.archive.ubuntu.com trusty Release.gpg
Get:1 http://gb.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Hit http://gb.archive.ubuntu.com trusty-backports Release.gpg
Hit http://gb.archive.ubuntu.com trusty Release
Get:2 http://gb.archive.ubuntu.com trusty-updates Release [63.5 kB]
Hit http://gb.archive.ubuntu.com trusty-backports Release
Hit http://gb.archive.ubuntu.com trusty/main Sources
Hit http://gb.archive.ubuntu.com trusty/restricted Sources
Hit http://gb.archive.ubuntu.com trusty/universe Sources
Hit http://gb.archive.ubuntu.com trusty/multiverse Sources
Hit http://gb.archive.ubuntu.com trusty/main amd64 Packages
Hit http://gb.archive.ubuntu.com trusty/restricted amd64 Packages
Ign http://overviewer.org ./ InRelease
Hit http://gb.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://gb.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com trusty/main i386 Packages
Hit http://gb.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://overviewer.org ./ Release.gpg
Hit http://gb.archive.ubuntu.com trusty/universe i386 Packages
Hit http://gb.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com trusty/main Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/main Translation-en
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://overviewer.org ./ Release
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en
Get:3 http://gb.archive.ubuntu.com trusty-updates/main Sources [192 kB]
Get:4 http://gb.archive.ubuntu.com trusty-updates/restricted Sources [2,564 B]
Get:5 http://gb.archive.ubuntu.com trusty-updates/universe Sources [108 kB]
Hit http://overviewer.org ./ Packages
Get:6 http://gb.archive.ubuntu.com trusty-updates/multiverse Sources [4,765 B]
Get:7 http://gb.archive.ubuntu.com trusty-updates/main amd64 Packages [497 kB]
Get:8 http://gb.archive.ubuntu.com trusty-updates/restricted amd64 Packages [9,238 B]
Get:9 http://gb.archive.ubuntu.com trusty-updates/universe amd64 Packages [263 kB]
Ign http://security.ubuntu.com trusty-security InRelease
Get:10 http://gb.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11.7 kB]
Get:11 http://gb.archive.ubuntu.com trusty-updates/main i386 Packages [486 kB]
Get:12 http://gb.archive.ubuntu.com trusty-updates/restricted i386 Packages [9,256 B]
Get:13 http://gb.archive.ubuntu.com trusty-updates/universe i386 Packages [265 kB]
Get:14 http://gb.archive.ubuntu.com trusty-updates/multiverse i386 Packages [11.9 kB]
Hit http://gb.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://gb.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://gb.archive.ubuntu.com trusty-backports/main Sources
Hit http://gb.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://gb.archive.ubuntu.com trusty-backports/universe Sources
Hit http://gb.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://gb.archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://gb.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Get:15 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Hit http://gb.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://gb.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://gb.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://gb.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://gb.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com trusty-backports/universe Translation-en
Get:16 http://security.ubuntu.com trusty-security Release [63.5 kB]
Ign http://overviewer.org ./ Translation-en_GB
Ign http://overviewer.org ./ Translation-en
Get:17 http://security.ubuntu.com trusty-security/main Sources [77.9 kB]
Get:18 http://security.ubuntu.com trusty-security/restricted Sources [2,061 B]
Get:19 http://security.ubuntu.com trusty-security/universe Sources [19.5 kB]
Get:20 http://security.ubuntu.com trusty-security/multiverse Sources [1,905 B]
Get:21 http://security.ubuntu.com trusty-security/main amd64 Packages [256 kB]
Get:22 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8,875 B]
Get:23 http://security.ubuntu.com trusty-security/universe amd64 Packages [92.0 kB]
Get:24 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,459 B]
Get:25 http://security.ubuntu.com trusty-security/main i386 Packages [246 kB]
Get:26 http://security.ubuntu.com trusty-security/restricted i386 Packages [8,846 B]
Get:27 http://security.ubuntu.com trusty-security/universe i386 Packages [91.9 kB]
Get:28 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,628 B]
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Fetched 2,803 kB in 18s (149 kB/s)
Reading package lists... Done

```

```

root@ID-Main-Server:/home/robert# apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-41 linux-headers-3.13.0-44
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.13.0-43-generic linux-image-3.13.0-44-generic
  linux-image-3.13.0-49-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
  linux-headers-3.13.0-43-generic linux-headers-3.13.0-44-generic
The following NEW packages will be installed
  linux-image-3.13.0-43-generic linux-image-3.13.0-44-generic
  linux-image-3.13.0-49-generic
0 to upgrade, 3 to newly install, 0 to remove and 73 not to upgrade.
5 not fully installed or removed.
Need to get 82.1 MB of archives.
After this operation, 126 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.13.0-49-generic amd64 3.13.0-49.83 [15.1 MB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.13.0-43-generic amd64 3.13.0-43.72 [15.1 MB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-extra-3.13.0-43-generic amd64 3.13.0-43.72 [36.7 MB]
Get:4 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.13.0-44-generic amd64 3.13.0-44.73 [15.1 MB]
Fetched 82.1 MB in 24s (3,315 kB/s)
(Reading database ... 254232 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-49-generic_3.13.0-49.83_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-49-generic (3.13.0-49.83) ...
Selecting previously unselected package linux-image-3.13.0-43-generic.
Preparing to unpack .../linux-image-3.13.0-43-generic_3.13.0-43.72_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-43-generic (3.13.0-43.72) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-43-generic_3.13.0-43.72_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-3.13.0-43-generic' to '/boot/System.map-3.13.0-43-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Selecting previously unselected package linux-image-3.13.0-44-generic.
Preparing to unpack .../linux-image-3.13.0-44-generic_3.13.0-44.73_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-44-generic (3.13.0-44.73) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-44-generic_3.13.0-44.73_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-3.13.0-44-generic' to '/boot/System.map-3.13.0-44-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-43-generic_3.13.0-43.72_amd64.deb
 /var/cache/apt/archives/linux-image-3.13.0-44-generic_3.13.0-44.73_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

root@ID-Main-Server:/home/robert# dpkg --configure -a
Setting up linux-image-3.13.0-49-generic (3.13.0-49.83) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-49-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-49-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-49-generic.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-49-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-49-generic; however:
  Package linux-image-3.13.0-49-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-44-generic:
 linux-image-extra-3.13.0-44-generic depends on linux-image-3.13.0-44-generic; however:
  Package linux-image-3.13.0-44-generic is not installed.

dpkg: error processing package linux-image-extra-3.13.0-44-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.49.56); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-49-generic:
 linux-image-extra-3.13.0-49-generic depends on linux-image-3.13.0-49-generic; however:
  Package linux-image-3.13.0-49-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-49-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.13.0-49-generic
 linux-image-generic
 linux-image-extra-3.13.0-44-generic
 linux-generic
 linux-image-extra-3.13.0-49-generic

```

---

### Post by laphyzz2 on 2015-04-14
```

root@ID-Main-Server:/home/robert# apt-get autoremove linux-image-extra-3.13.0-44-generic linux-image-3.13.0-44-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'linux-image-3.13.0-44-generic' is not installed, so not removed
The following packages will be REMOVED
  linux-headers-3.13.0-41 linux-headers-3.13.0-44
  linux-image-3.13.0-41-generic linux-image-extra-3.13.0-41-generic
  linux-image-extra-3.13.0-43-generic linux-image-extra-3.13.0-44-generic
0 to upgrade, 0 to newly install, 6 to remove and 73 not to upgrade.
6 not fully installed or removed.
After this operation, 625 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 254983 files and directories currently installed.)
Removing linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-43-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
grep: /boot/config-3.13.0-43-generic: No such file or directory
WARNING: missing /lib/modules/3.13.0-43-generic
Device driver support needs thus be built-in linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-43-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_NnhQyg/lib/modules/3.13.0-43-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_NnhQyg/lib/modules/3.13.0-43-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-41-generic
Found initrd image: /boot/initrd.img-3.13.0-41-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Removing linux-image-extra-3.13.0-44-generic (3.13.0-44.73) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-44-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-44-generic
grep: /boot/config-3.13.0-44-generic: No such file or directory
WARNING: missing /lib/modules/3.13.0-44-generic
Device driver support needs thus be built-in linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-44-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_jPMHUG/lib/modules/3.13.0-44-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_jPMHUG/lib/modules/3.13.0-44-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-41-generic
Found initrd image: /boot/initrd.img-3.13.0-41-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Removing linux-headers-3.13.0-41 (3.13.0-41.70) ...
Removing linux-headers-3.13.0-44 (3.13.0-44.73) ...
Removing linux-image-extra-3.13.0-41-generic (3.13.0-41.70) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-41-generic /boot/vmlinuz-3.13.0-41-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-41-generic /boot/vmlinuz-3.13.0-41-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-41-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-41-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-41-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-41-generic (3.13.0-41.70) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-41-generic /boot/vmlinuz-3.13.0-41-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-41-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-41-generic /boot/vmlinuz-3.13.0-41-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
The link /initrd.img is a damaged link
Removing symbolic link initrd.img
 you may need to re-run your boot loader[grub]
Errors were encountered while processing:
 linux-image-extra-3.13.0-41-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

root@ID-Main-Server:/home/robert# apt-get install --reinstall linux-image-3.13.0-49-generic linux-image-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED
  linux-image-extra-3.13.0-41-generic
0 to upgrade, 0 to newly install, 2 reinstalled, 1 to remove and 73 not to upgrade.
5 not fully installed or removed.
After this operation, 152 MB disk space will be freed.
Do you want to continue? [Y/n] y
E: Internal Error, No file name for linux-image-3.13.0-49-generic:amd

```

---

### Post by ian-weisser on 2015-04-14
> **laphyzz2 said:**
> gzip: stdout: No space left on device

Try autoremove. You have not freed enough space yet.

---

### Post by laphyzz2 on 2015-04-14
```

root@ID-Main-Server:/home/robert# apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED
  linux-image-extra-3.13.0-41-generic
0 to upgrade, 0 to newly install, 1 to remove and 73 not to upgrade.
5 not fully installed or removed.
After this operation, 152 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 215591 files and directories currently installed.)
Removing linux-image-extra-3.13.0-41-generic (3.13.0-41.70) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-41-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-41-generic /boot/vmlinuz-3.13.0-41-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-41-generic /boot/vmlinuz-3.13.0-41-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-41-generic
grep: /boot/config-3.13.0-41-generic: No such file or directory
WARNING: missing /lib/modules/3.13.0-41-generic
Device driver support needs thus be built-in linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-41-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_wQToDo/lib/modules/3.13.0-41-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_wQToDo/lib/modules/3.13.0-41-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-41-generic /boot/vmlinuz-3.13.0-41-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-41-generic /boot/vmlinuz-3.13.0-41-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-3.13.0-49-generic (3.13.0-49.83) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
vmlinuz(/boot/vmlinuz-3.13.0-49-generic
) points to /boot/vmlinuz-3.13.0-49-generic
 (/boot/vmlinuz-3.13.0-49-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.13.0-49-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-extra-3.13.0-49-generic (3.13.0-49.81) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-49-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-49-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-49-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-3.13.0-49-generic; however:
  Package linux-image-extra-3.13.0-49-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.49.56); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                Errors were encountered while processing:
 linux-image-extra-3.13.0-49-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by ian-weisser on 2015-04-14
> **ian-weisser said:**
> You have probably freed up enough space for 'sudo apt-get autoremove' (which is much easier) to finally work.
And for those 70 long delayed upgrades ('sudo apt-get upgrade').

I was wrong. You have not freed up enough space yet.
Go back to Bashing-om's method of using dpkg.

Use 'dpkg -l | grep linux' to find the packages you need to remove.
Use dpkg -r <packagename> to remove them.
Do NOT remove any packages that your current running kernel is using. The only way to fix that is to reinstall.
If dpkg complains the you are removing a dependency, leaving a different package orphaned, remove that different package too.

You now have enough experience with dpkg, and reading the output, that you should be able to make some progress.

---

### Post by laphyzz2 on 2015-04-14
```

root@ID-Main-Server:/home/robert# dpkg -l | grep linux
ii  libselinux1:amd64                   2.2.2-1ubuntu0.1                 amd64        SELinux runtime shared libraries
ii  libv4l-0:amd64                      1.0.1-1                          amd64        Collection of video4linux support libraries
ii  libv4lconvert0:amd64                1.0.1-1                          amd64        Video4linux frame format conversion library
ii  linux-firmware                      1.127.11                         all          Firmware for Linux kernel drivers
iU  linux-generic                       3.13.0.49.56                     amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-33             3.13.0-33.58                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-33-generic     3.13.0-33.58                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-34             3.13.0-34.60                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic     3.13.0-34.60                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
pi  linux-headers-3.13.0-36             3.13.0-36.63                     all          Header files related to Linux kernel version 3.13.0
pi  linux-headers-3.13.0-37             3.13.0-37.64                     all          Header files related to Linux kernel version 3.13.0
pi  linux-headers-3.13.0-39             3.13.0-39.66                     all          Header files related to Linux kernel version 3.13.0
pi  linux-headers-3.13.0-40             3.13.0-40.69                     all          Header files related to Linux kernel version 3.13.0
pi  linux-headers-3.13.0-43             3.13.0-43.72                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49             3.13.0-49.81                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic     3.13.0-49.81                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic               3.13.0.49.56                     amd64        Generic Linux kernel headers
rc  linux-image-3.13.0-24-generic       3.13.0-24.47                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-27-generic       3.13.0-27.50                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-29-generic       3.13.0-29.53                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-30-generic       3.13.0-30.55                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-32-generic       3.13.0-32.57                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-33-generic       3.13.0-33.58                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic       3.13.0-34.60                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-35-generic       3.13.0-35.62                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
pi  linux-image-3.13.0-36-generic       3.13.0-36.63                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
pi  linux-image-3.13.0-37-generic       3.13.0-37.64                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
pi  linux-image-3.13.0-39-generic       3.13.0-39.66                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
pi  linux-image-3.13.0-40-generic       3.13.0-40.69                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-41-generic       3.13.0-41.70                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-49-generic       3.13.0-49.83                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-24-generic 3.13.0-24.47                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-27-generic 3.13.0-27.50                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-29-generic 3.13.0-29.53                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-30-generic 3.13.0-30.55                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic 3.13.0-32.57                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-33-generic 3.13.0-33.58                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic 3.13.0-34.60                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-35-generic 3.13.0-35.62                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic 3.13.0-36.63                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic 3.13.0-37.64                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic 3.13.0-39.66                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic 3.13.0-40.69                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-41-generic 3.13.0-41.70                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-43-generic 3.13.0-43.72                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-44-generic 3.13.0-44.73                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-46-generic 3.13.0-46.79                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-extra-3.13.0-49-generic 3.13.0-49.81                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                 3.13.0.49.56                     amd64        Generic Linux kernel image
ii  util-linux                          2.20.1-5.1ubuntu20.4             amd64        Miscellaneous system utilities

```

As for 
```
dpkg -r <packagename>
```
I may have from this learned a lot, I also have more experience at breaking things and I can't risk it with this server so I would really appreciate the help

---

### Post by Impavidus on 2015-04-14
> **Bashing-om said:**
> 
What in the world is going on that the kernels are now marked as '(P)urged (i)installed,

Quite simple, actually. The dpkg commands suggested back in post #17 were in principle correct (except for one), but given in the wrong order. **linux-headers-blahblah** has to be uninstalled *after* **linux-headers-blahblah-generic**, and the same for **linux-image-blahblah-generic** and **linux-image-[COLOR=#ff0000]extra[/COLOR]-blahblah-generic**. So two of the dpkg commands only marked the packages to be purged, without actually uninstalling them. Reshuffling the commands and skipping the one that had worked gives```
sudo dpkg -P linux-image-extra-3.13.0-{36,37,39,40,41,43,44}-generic
sudo dpkg -P linux-image-3.13.0-{36,37,39,40,41,43,44}-generic
sudo dpkg -P linux-headers-3.13.0-{36,37,39,40,41,43,44}
```

---

### Post by laphyzz2 on 2015-04-14
```

root@ID-Main-Server:/home/robert# dpkg -P linux-image-extra-3.13.0-{36,37,39,40,41,43,44}-generic
(Reading database ... 215591 files and directories currently installed.)
Removing linux-image-extra-3.13.0-36-generic (3.13.0-36.63) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-36-generic /boot/vmlinuz-3.13.0-36-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-36-generic /boot/vmlinuz-3.13.0-36-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.13.0-36-generic (3.13.0-36.63) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-36-generic /boot/vmlinuz-3.13.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-36-generic /boot/vmlinuz-3.13.0-36-generic
Removing linux-image-extra-3.13.0-37-generic (3.13.0-37.64) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.13.0-37-generic (3.13.0-37.64) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
Removing linux-image-extra-3.13.0-39-generic (3.13.0-39.66) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-39-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.13.0-39-generic (3.13.0-39.66) ...
Removing linux-image-extra-3.13.0-40-generic (3.13.0-40.69) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-40-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.13.0-40-generic (3.13.0-40.69) ...
Removing linux-image-extra-3.13.0-41-generic (3.13.0-41.70) ...
Purging configuration files for linux-image-extra-3.13.0-41-generic (3.13.0-41.70) ...
Removing linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
Purging configuration files for linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
Removing linux-image-extra-3.13.0-44-generic (3.13.0-44.73) ...
Purging configuration files for linux-image-extra-3.13.0-44-generic (3.13.0-44.73) ...

```

```

root@ID-Main-Server:/home/robert# dpkg -P linux-image-3.13.0-{36,37,39,40,41,43,44}-generic
(Reading database ... 199915 files and directories currently installed.)
Removing linux-image-3.13.0-36-generic (3.13.0-36.63) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-36-generic /boot/vmlinuz-3.13.0-36-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-36-generic /boot/vmlinuz-3.13.0-36-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.13.0-36-generic (3.13.0-36.63) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-36-generic /boot/vmlinuz-3.13.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-36-generic /boot/vmlinuz-3.13.0-36-generic
Removing linux-image-3.13.0-37-generic (3.13.0-37.64) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.13.0-37-generic (3.13.0-37.64) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
Removing linux-image-3.13.0-39-generic (3.13.0-39.66) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-39-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.13.0-39-generic (3.13.0-39.66) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
Removing linux-image-3.13.0-40-generic (3.13.0-40.69) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-40-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.13.0-40-generic (3.13.0-40.69) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
Removing linux-image-3.13.0-41-generic (3.13.0-41.70) ...
Purging configuration files for linux-image-3.13.0-41-generic (3.13.0-41.70) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-41-generic /boot/vmlinuz-3.13.0-41-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-41-generic /boot/vmlinuz-3.13.0-41-generic
dpkg: warning: ignoring request to remove linux-image-3.13.0-43-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-3.13.0-44-generic which isn't installed

```

```

root@ID-Main-Server:/home/robert# dpkg -P linux-headers-3.13.0-{36,37,39,40,41,43,44}
(Reading database ... 196315 files and directories currently installed.)
Removing linux-headers-3.13.0-36 (3.13.0-36.63) ...
Removing linux-headers-3.13.0-37 (3.13.0-37.64) ...
Removing linux-headers-3.13.0-39 (3.13.0-39.66) ...
Removing linux-headers-3.13.0-40 (3.13.0-40.69) ...
dpkg: warning: ignoring request to remove linux-headers-3.13.0-41 which isn't installed
Removing linux-headers-3.13.0-43 (3.13.0-43.72) ...
dpkg: warning: ignoring request to remove linux-headers-3.13.0-44 which isn't installed

```

---

### Post by Impavidus on 2015-04-14
That seems to have uninstalled some old kernels. Now let's try and configure those packages and see where we get then.
```
sudo dpkg --configure -a
dpkg -l | grep "linux-"
df -h
```

---

### Post by laphyzz2 on 2015-04-14
```

root@ID-Main-Server:/home/robert# sudo dpkg --configure -a
Setting up linux-image-extra-3.13.0-49-generic (3.13.0-49.81) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-generic (3.13.0.49.56) ...
Setting up linux-generic (3.13.0.49.56) ...

```

```

root@ID-Main-Server:/home/robert# dpkg -l | grep "linux-"
ii  linux-firmware                      1.127.11                         all          Firmware for Linux kernel drivers
ii  linux-generic                       3.13.0.49.56                     amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-33             3.13.0-33.58                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-33-generic     3.13.0-33.58                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-34             3.13.0-34.60                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic     3.13.0-34.60                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-49             3.13.0-49.81                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic     3.13.0-49.81                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic               3.13.0.49.56                     amd64        Generic Linux kernel headers
rc  linux-image-3.13.0-24-generic       3.13.0-24.47                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-27-generic       3.13.0-27.50                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-29-generic       3.13.0-29.53                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-30-generic       3.13.0-30.55                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-32-generic       3.13.0-32.57                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-33-generic       3.13.0-33.58                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic       3.13.0-34.60                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-35-generic       3.13.0-35.62                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-49-generic       3.13.0-49.83                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-24-generic 3.13.0-24.47                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-27-generic 3.13.0-27.50                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-29-generic 3.13.0-29.53                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-30-generic 3.13.0-30.55                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic 3.13.0-32.57                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-33-generic 3.13.0-33.58                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic 3.13.0-34.60                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-35-generic 3.13.0-35.62                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-46-generic 3.13.0-46.79                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic 3.13.0-49.81                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                 3.13.0.49.56                     amd64        Generic Linux kernel image


```

```

root@ID-Main-Server:/home/robert# df -h
Filesystem                             Size  Used Avail Use% Mounted on
/dev/mapper/ID--Main--Server--vg-root  1.8T   14G  1.7T   1% /
none                                   4.0K     0  4.0K   0% /sys/fs/cgroup
udev                                   3.8G   12K  3.8G   1% /dev
tmpfs                                  772M  656K  771M   1% /run
none                                   5.0M     0  5.0M   0% /run/lock
none                                   3.8G     0  3.8G   0% /run/shm
none                                   100M     0  100M   0% /run/user
/dev/sda1                              236M  111M  113M  50% /boot


```

---

### Post by Impavidus on 2015-04-14
Looking good now. You should be able to reboot into the 3.13.0-49 kernel.```
uname -r
``` will tell whether you succeed in booting that. Then it's time for some additional cleanup. Keep kernel 3.13.0-33 for a while, as we know it's good.
```
sudo apt-get purge linux-image{,-extra}-3.13.0-{24,27,29,30,32,34,35}-generic
sudo apt-get purge linux-image-extra-3.13.0-46-generic
sudo apt-get purge linux-headers-3.13.0-34{,-generic}
```Finally get the latest updates installed and your system should be as new.```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by laphyzz2 on 2015-04-14
```

root@ID-Main-Server:/home/robert# uname -r
3.13.0-49-generic

```

```

root@ID-Main-Server:/home/robert# sudo apt-get purge linux-image{,-extra}-3.13.0- {24,27,29,30,32,34,35}-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED
  linux-image-3.13.0-24-generic* linux-image-3.13.0-27-generic*
  linux-image-3.13.0-29-generic* linux-image-3.13.0-30-generic*
  linux-image-3.13.0-32-generic* linux-image-3.13.0-34-generic*
  linux-image-3.13.0-35-generic* linux-image-extra-3.13.0-24-generic*
  linux-image-extra-3.13.0-27-generic* linux-image-extra-3.13.0-29-generic*
  linux-image-extra-3.13.0-30-generic* linux-image-extra-3.13.0-32-generic*
  linux-image-extra-3.13.0-34-generic* linux-image-extra-3.13.0-35-generic*
0 to upgrade, 0 to newly install, 14 to remove and 73 not to upgrade.
After this operation, 194 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 120061 files and directories currently installed.)
Removing linux-image-3.13.0-24-generic (3.13.0-24.47) ...
Purging configuration files for linux-image-3.13.0-24-generic (3.13.0-24.47) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-24-generic /boot /vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-24-generic /boot/ vmlinuz-3.13.0-24-generic
Removing linux-image-3.13.0-27-generic (3.13.0-27.50) ...
Purging configuration files for linux-image-3.13.0-27-generic (3.13.0-27.50) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-27-generic /boot /vmlinuz-3.13.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-27-generic /boot/ vmlinuz-3.13.0-27-generic
Removing linux-image-3.13.0-29-generic (3.13.0-29.53) ...
Purging configuration files for linux-image-3.13.0-29-generic (3.13.0-29.53) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-29-generic /boot /vmlinuz-3.13.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-29-generic /boot/ vmlinuz-3.13.0-29-generic
Removing linux-image-3.13.0-30-generic (3.13.0-30.55) ...
Purging configuration files for linux-image-3.13.0-30-generic (3.13.0-30.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-30-generic /boot /vmlinuz-3.13.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-30-generic /boot/ vmlinuz-3.13.0-30-generic
Removing linux-image-3.13.0-32-generic (3.13.0-32.57) ...
Purging configuration files for linux-image-3.13.0-32-generic (3.13.0-32.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-32-generic /boot /vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-32-generic /boot/ vmlinuz-3.13.0-32-generic
Removing linux-image-extra-3.13.0-34-generic (3.13.0-34.60) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-34-generic /boot /vmlinuz-3.13.0-34-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-34-generic /boot/ vmlinuz-3.13.0-34-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.13.0-34-generic (3.13.0-34.60 ) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-34-generic /boot /vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-34-generic /boot/ vmlinuz-3.13.0-34-generic
Removing linux-image-3.13.0-34-generic (3.13.0-34.60) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-34-generic /boot /vmlinuz-3.13.0-34-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-34-generic /boot/ vmlinuz-3.13.0-34-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.13.0-34-generic (3.13.0-34.60) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-34-generic /boot /vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-34-generic /boot/ vmlinuz-3.13.0-34-generic
Removing linux-image-3.13.0-35-generic (3.13.0-35.62) ...
Purging configuration files for linux-image-3.13.0-35-generic (3.13.0-35.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-35-generic /boot /vmlinuz-3.13.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-35-generic /boot/ vmlinuz-3.13.0-35-generic
Removing linux-image-extra-3.13.0-24-generic (3.13.0-24.47) ...
Purging configuration files for linux-image-extra-3.13.0-24-generic (3.13.0-24.47 ) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-24-generic /boot /vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-24-generic /boot  vmlinuz-3.13.0-24-generic
Removing linux-image-extra-3.13.0-27-generic (3.13.0-27.50) ...
Purging configuration files for linux-image-extra-3.13.0-27-generic (3.13.0-27.5  ) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-27-generic /boo  /vmlinuz-3.13.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-27-generic /boot  vmlinuz-3.13.0-27-generic
Removing linux-image-extra-3.13.0-29-generic (3.13.0-29.53) ...
Purging configuration files for linux-image-extra-3.13.0-29-generic (3.13.0-29.5  ) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-29-generic /boo  /vmlinuz-3.13.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-29-generic /boot  vmlinuz-3.13.0-29-generic
Removing linux-image-extra-3.13.0-30-generic (3.13.0-30.55) ...
Purging configuration files for linux-image-extra-3.13.0-30-generic (3.13.0-30.5  ) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-30-generic /boo  /vmlinuz-3.13.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-30-generic /boot  vmlinuz-3.13.0-30-generic
Removing linux-image-extra-3.13.0-32-generic (3.13.0-32.57) ...
Purging configuration files for linux-image-extra-3.13.0-32-generic (3.13.0-32.5  ) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-32-generic /boo  /vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-32-generic /boot  vmlinuz-3.13.0-32-generic
Removing linux-image-extra-3.13.0-35-generic (3.13.0-35.62) ...
Purging configuration files for linux-image-extra-3.13.0-35-generic (3.13.0-35.6  ) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-35-generic /boo  /vmlinuz-3.13.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-35-generic /boot  vmlinuz-3.13.0-35-generic

```

```

root@ID-Main-Server:/home/robert# sudo apt-get purge linux-image-extra-3.13.0-46-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED
  linux-image-extra-3.13.0-46-generic*
0 to upgrade, 0 to newly install, 1 to remove and 73 not to upgrade.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 115246 files and directories currently installed.)
Removing linux-image-extra-3.13.0-46-generic (3.13.0-46.79) ...
Purging configuration files for linux-image-extra-3.13.0-46-generic (3.13.0-46.79) ...


```

```

root@ID-Main-Server:/home/robert# sudo apt-get purge linux-image-extra-3.13.0-46-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED
  linux-image-extra-3.13.0-46-generic*
0 to upgrade, 0 to newly install, 1 to remove and 73 not to upgrade.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 115246 files and directories currently installed.)
Removing linux-image-extra-3.13.0-46-generic (3.13.0-46.79) ...
Purging configuration files for linux-image-extra-3.13.0-46-generic (3.13.0-46.79) ...
root@ID-Main-Server:/home/robert# ^C
root@ID-Main-Server:/home/robert#
root@ID-Main-Server:/home/robert# sudo apt-get purge linux-headers-3.13.0-34{,-generic}
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED
  linux-headers-3.13.0-34* linux-headers-3.13.0-34-generic*
0 to upgrade, 0 to newly install, 2 to remove and 73 not to upgrade.
After this operation, 76.6 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 115246 files and directories currently installed.)
Removing linux-headers-3.13.0-34-generic (3.13.0-34.60) ...
Removing linux-headers-3.13.0-34 (3.13.0-34.60) ...


```

```

root@ID-Main-Server:/home/robert# sudo apt-get purge linux-headers-3.13.0-34{,-generic}
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED
  linux-headers-3.13.0-34* linux-headers-3.13.0-34-generic*
0 to upgrade, 0 to newly install, 2 to remove and 73 not to upgrade.
After this operation, 76.6 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 115246 files and directories currently installed.)
Removing linux-headers-3.13.0-34-generic (3.13.0-34.60) ...
Removing linux-headers-3.13.0-34 (3.13.0-34.60) ...
root@ID-Main-Server:/home/robert# ^C
root@ID-Main-Server:/home/robert# sudo apt-get update
Ign http://gb.archive.ubuntu.com trusty InRelease
Ign http://gb.archive.ubuntu.com trusty-updates InRelease
Ign http://gb.archive.ubuntu.com trusty-backports InRelease
Hit http://gb.archive.ubuntu.com trusty Release.gpg
Get:1 http://gb.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Get:2 http://gb.archive.ubuntu.com trusty-backports Release.gpg [933 B]
Hit http://gb.archive.ubuntu.com trusty Release
Get:3 http://gb.archive.ubuntu.com trusty-updates Release [63.5 kB]
Ign http://security.ubuntu.com trusty-security InRelease
Get:4 http://gb.archive.ubuntu.com trusty-backports Release [63.5 kB]
Get:5 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Hit http://gb.archive.ubuntu.com trusty/main Sources
Get:6 http://security.ubuntu.com trusty-security Release [63.5 kB]
Hit http://gb.archive.ubuntu.com trusty/restricted Sources
Ign http://overviewer.org ./ InRelease
Hit http://gb.archive.ubuntu.com trusty/universe Sources
Hit http://gb.archive.ubuntu.com trusty/multiverse Sources
Hit http://gb.archive.ubuntu.com trusty/main amd64 Packages
Hit http://gb.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://gb.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com trusty/main i386 Packages
Hit http://overviewer.org ./ Release.gpg
Hit http://gb.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://gb.archive.ubuntu.com trusty/universe i386 Packages
Hit http://gb.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://overviewer.org ./ Release
Hit http://gb.archive.ubuntu.com trusty/main Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/main Translation-en
Get:7 http://security.ubuntu.com trusty-security/main Sources [78.5 kB]
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en
Get:8 http://gb.archive.ubuntu.com trusty-updates/main Sources [192 kB]
Hit http://overviewer.org ./ Packages
Get:9 http://security.ubuntu.com trusty-security/restricted Sources [2,061 B]
Get:10 http://security.ubuntu.com trusty-security/universe Sources [19.5 kB]
Get:11 http://gb.archive.ubuntu.com trusty-updates/restricted Sources [2,564 B]
Get:12 http://gb.archive.ubuntu.com trusty-updates/universe Sources [108 kB]
Get:13 http://security.ubuntu.com trusty-security/multiverse Sources [1,905 B]
Get:14 http://security.ubuntu.com trusty-security/main amd64 Packages [258 kB]
Get:15 http://gb.archive.ubuntu.com trusty-updates/multiverse Sources [4,765 B]
Get:16 http://gb.archive.ubuntu.com trusty-updates/main amd64 Packages [497 kB]
Get:17 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8,875 B]
Get:18 http://security.ubuntu.com trusty-security/universe amd64 Packages [92.5 kB]
Get:19 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,459 B]
Get:20 http://security.ubuntu.com trusty-security/main i386 Packages [248 kB]
Get:21 http://gb.archive.ubuntu.com trusty-updates/restricted amd64 Packages [9,238 B]
Get:22 http://security.ubuntu.com trusty-security/restricted i386 Packages [8,846 B]
Get:23 http://gb.archive.ubuntu.com trusty-updates/universe amd64 Packages [263 kB]
Get:24 http://security.ubuntu.com trusty-security/universe i386 Packages [92.5 kB]
Ign http://overviewer.org ./ Translation-en_GB
Get:25 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,628 B]
Ign http://overviewer.org ./ Translation-en
Get:26 http://security.ubuntu.com trusty-security/main Translation-en [131 kB]
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Get:27 http://gb.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11.7 kB]
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Get:28 http://gb.archive.ubuntu.com trusty-updates/main i386 Packages [486 kB]
Get:29 http://security.ubuntu.com trusty-security/universe Translation-en [51.4 kB]
Get:30 http://gb.archive.ubuntu.com trusty-updates/restricted i386 Packages [9,256 B]
Get:31 http://gb.archive.ubuntu.com trusty-updates/universe i386 Packages [265 kB]
Get:32 http://gb.archive.ubuntu.com trusty-updates/multiverse i386 Packages [11.9 kB]
Hit http://gb.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://gb.archive.ubuntu.com trusty-updates/universe Translation-en
Get:33 http://gb.archive.ubuntu.com trusty-backports/main Sources [5,298 B]
Get:34 http://gb.archive.ubuntu.com trusty-backports/restricted Sources [28 B]
Get:35 http://gb.archive.ubuntu.com trusty-backports/universe Sources [24.4 kB]
Get:36 http://gb.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:37 http://gb.archive.ubuntu.com trusty-backports/main amd64 Packages [5,536 B]
Get:38 http://gb.archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:39 http://gb.archive.ubuntu.com trusty-backports/universe amd64 Packages [27.9 kB]
Get:40 http://gb.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,245 B]
Get:41 http://gb.archive.ubuntu.com trusty-backports/main i386 Packages [5,550 B]
Get:42 http://gb.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:43 http://gb.archive.ubuntu.com trusty-backports/universe i386 Packages [27.9 kB]
Get:44 http://gb.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,249 B]
Hit http://gb.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en
Get:45 http://gb.archive.ubuntu.com trusty-backports/universe Translation-en [25.1 kB]
Fetched 3,180 kB in 3s (807 kB/s)
Reading package lists... Done

```

```

root@ID-Main-Server:/home/robert# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  apache2 apache2-bin apache2-data apport bsdutils gnupg gpgv gvfs gvfs-common
  gvfs-daemons gvfs-libs language-pack-en language-pack-en-base
  libasn1-8-heimdal libcups2 libgcrypt11 libgl1-mesa-dri libgl1-mesa-glx
  libglapi-mesa libgnutls-openssl27 libgnutls26 libgssapi3-heimdal libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libgudev-1.0-0 libhcrypto4-heimdal
  libheimbase1-heimdal libheimntlm0-heimdal libhx509-5-heimdal libicu52
  libkrb5-26-heimdal libmount1 libnuma1 libpam-systemd libpolkit-agent-1-0
  libpolkit-backend-1-0 libpolkit-gobject-1-0 libpulse0 libroken18-heimdal
  libssl1.0.0 libsystemd-daemon0 libsystemd-login0 libtasn1-6 libtiff5
  libwind0-heimdal libxext6 libxfixes3 libxi6 libxrender1
  linux-headers-3.13.0-49 linux-headers-3.13.0-49-generic
  linux-image-extra-3.13.0-49-generic multiarch-support ntpdate openssl
  policykit-1 python-requests python-urllib3 python3-apport
  python3-distupgrade python3-problem-report python3-software-properties
  rsyslog software-properties-common sudo systemd-services tzdata tzdata-java
  ubuntu-release-upgrader-core unattended-upgrades uuid-runtime x11-common
73 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 67.9 MB of archives.
After this operation, 394 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main bsdutils amd64 1:2.20.1-5.1ubuntu20.4 [33.8 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libmount1 amd64 2.20.1-5.1ubuntu20.4 [60.2 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libgcrypt11 amd64 1.5.3-2ubuntu4.2 [239 kB]
Get:4 http://security.ubuntu.com/ubuntu/ trusty-security/main python3-problem-report all 2.14.1-0ubuntu3.9 [9,190 B]
Get:5 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libtasn1-6 amd64 3.4-3ubuntu0.2 [43.6 kB]
Get:6 http://security.ubuntu.com/ubuntu/ trusty-security/main python3-apport all 2.14.1-0ubuntu3.9 [75.1 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libgnutls-openssl27 amd64 2.12.23-12ubuntu2.2 [18.3 kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libgnutls26 amd64 2.12.23-12ubuntu2.2 [393 kB]
Get:9 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libssl1.0.0 amd64 1.0.1f-1ubuntu2.11 [827 kB]
Get:10 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main ntpdate amd64 1:4.2.6.p5+dfsg-3ubuntu2.14.04.3 [56.3 kB]
Get:11 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libroken18-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1.1 [40.0 kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libasn1-8-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1.1 [161 kB]
Get:13 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libhcrypto4-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1.1 [83.9 kB]
Get:14 http://security.ubuntu.com/ubuntu/ trusty-security/main apport all 2.14.1-0ubuntu3.9 [179 kB]
Get:15 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libheimbase1-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1.1 [28.9 kB]
Get:16 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libwind0-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1.1 [47.8 kB]
Get:17 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libhx509-5-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1.1 [104 kB]
Get:18 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libkrb5-26-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1.1 [196 kB]
Get:19 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libheimntlm0-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1.1 [15.2 kB]
Get:20 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libgssapi3-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1.1 [89.8 kB]
Get:21 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libnuma1 amd64 2.0.9~rc5-1ubuntu3 [20.3 kB]
Get:22 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libpam-systemd amd64 204-5ubuntu20.11 [25.5 kB]
Get:23 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main systemd-services amd64 204-5ubuntu20.11 [197 kB]
Get:24 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libsystemd-daemon0 amd64 204-5ubuntu20.11 [9,726 B]
Get:25 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libsystemd-login0 amd64 204-5ubuntu20.11 [26.8 kB]
Get:26 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libpolkit-gobject-1-0 amd64 0.105-4ubuntu2.14.04.1 [34.8 kB]
Get:27 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libxext6 amd64 2:1.3.2-1ubuntu0.0.14.04.1 [28.8 kB]
Get:28 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main language-pack-en all 1:14.04+20150219 [1,828 B]
Get:29 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main language-pack-en-base all 1:14.04+20150219 [472 kB]
Get:30 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libcups2 amd64 1.7.2-0ubuntu1.5 [179 kB]
Get:31 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libgl1-mesa-dri amd64 10.1.3-0ubuntu0.4 [4,568 kB]
Get:32 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libgl1-mesa-glx amd64 10.1.3-0ubuntu0.4 [114 kB]
Get:33 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libglapi-mesa amd64 10.1.3-0ubuntu0.4 [21.4 kB]
Get:34 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libxfixes3 amd64 1:5.0.1-1ubuntu1.1 [10.4 kB]
Get:35 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libgtk2.0-common all 2.24.23-0ubuntu1.2 [121 kB]
Get:36 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libgtk2.0-bin amd64 2.24.23-0ubuntu1.2 [9,798 B]
Get:37 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libxi6 amd64 2:1.7.1.901-1ubuntu1.1 [27.9 kB]
Get:38 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libxrender1 amd64 1:0.9.8-1build0.14.04.1 [17.9 kB]
Get:39 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libgtk2.0-0 amd64 2.24.23-0ubuntu1.2 [1,739 kB]
Get:40 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libgudev-1.0-0 amd64 1:204-5ubuntu20.11 [14.1 kB]
Get:41 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libicu52 amd64 52.1-3ubuntu0.2 [6,751 kB]
Get:42 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libpolkit-agent-1-0 amd64 0.105-4ubuntu2.14.04.1 [14.9 kB]
Get:43 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libpolkit-backend-1-0 amd64 0.105-4ubuntu2.14.04.1 [34.6 kB]
Get:44 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libpulse0 amd64 1:4.0-0ubuntu11.1 [225 kB]
Get:45 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libtiff5 amd64 4.0.3-7ubuntu0.3 [143 kB]
Get:46 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main gpgv amd64 1.4.16-1ubuntu2.3 [161 kB]
Get:47 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main gnupg amd64 1.4.16-1ubuntu2.3 [611 kB]
Get:48 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main multiarch-support amd64 2.19-0ubuntu6.6 [4,486 B]
Get:49 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main tzdata-java all 2015b-0ubuntu0.14.04 [70.1 kB]
Get:50 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main tzdata all 2015b-0ubuntu0.14.04 [172 kB]
Get:51 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main rsyslog amd64 7.4.4-1ubuntu2.5 [355 kB]
Get:52 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main sudo amd64 1.8.9p5-1ubuntu1.1 [343 kB]
Get:53 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main openssl amd64 1.0.1f-1ubuntu2.11 [488 kB]
Get:54 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main ubuntu-release-upgrader-core all 1:0.220.7 [23.1 kB]
Get:55 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-distupgrade all 1:0.220.7 [104 kB]
Get:56 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main uuid-runtime amd64 2.20.1-5.1ubuntu20.4 [12.3 kB]
Get:57 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main apache2 amd64 2.4.7-1ubuntu4.4 [87.4 kB]
Get:58 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main apache2-bin amd64 2.4.7-1ubuntu4.4 [843 kB]
Get:59 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main apache2-data all 2.4.7-1ubuntu4.4 [160 kB]
Get:60 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main gvfs amd64 1.20.3-0ubuntu1 [89.5 kB]
Get:61 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main gvfs-daemons amd64 1.20.3-0ubuntu1 [109 kB]
Get:62 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main gvfs-libs amd64 1.20.3-0ubuntu1 [106 kB]
Get:63 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main gvfs-common all 1.20.3-0ubuntu1 [42.4 kB]
Get:64 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-49 all 3.13.0-49.83 [8,878 kB]
Get:65 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-49-generic amd64 3.13.0-49.83 [699 kB]
Get:66 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-extra-3.13.0-49-generic amd64 3.13.0-49.83 [36.8 MB]
Get:67 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main policykit-1 amd64 0.105-4ubuntu2.14.04.1 [51.3 kB]
Get:68 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main python-urllib3 all 1.7.1-1ubuntu0.1 [39.3 kB]
Get:69 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main python-requests all 2.2.1-1ubuntu0.2 [43.0 kB]
Get:70 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main software-properties-common all 0.92.37.3 [9,376 B]
Get:71 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main unattended-upgrades all 0.82.1ubuntu2.2 [25.4 kB]
Get:72 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-software-properties all 0.92.37.3 [19.1 kB]
Get:73 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main x11-common all 1:7.7+1ubuntu8.1 [49.5 kB]
Fetched 67.9 MB in 6s (10.2 MB/s)
Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 90450 files and directories currently installed.)
Preparing to unpack .../bsdutils_1%3a2.20.1-5.1ubuntu20.4_amd64.deb ...
Unpacking bsdutils (1:2.20.1-5.1ubuntu20.4) over (1:2.20.1-5.1ubuntu20.3) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up bsdutils (1:2.20.1-5.1ubuntu20.4) ...
(Reading database ... 90450 files and directories currently installed.)
Preparing to unpack .../libmount1_2.20.1-5.1ubuntu20.4_amd64.deb ...
Unpacking libmount1:amd64 (2.20.1-5.1ubuntu20.4) over (2.20.1-5.1ubuntu20.3) ...
Setting up libmount1:amd64 (2.20.1-5.1ubuntu20.4) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
(Reading database ... 90450 files and directories currently installed.)
Preparing to unpack .../libgcrypt11_1.5.3-2ubuntu4.2_amd64.deb ...
Unpacking libgcrypt11:amd64 (1.5.3-2ubuntu4.2) over (1.5.3-2ubuntu4.1) ...
Preparing to unpack .../libtasn1-6_3.4-3ubuntu0.2_amd64.deb ...
Unpacking libtasn1-6:amd64 (3.4-3ubuntu0.2) over (3.4-3ubuntu0.1) ...
Preparing to unpack .../libgnutls-openssl27_2.12.23-12ubuntu2.2_amd64.deb ...
Unpacking libgnutls-openssl27:amd64 (2.12.23-12ubuntu2.2) over (2.12.23-12ubuntu2.1) ...
Preparing to unpack .../libgnutls26_2.12.23-12ubuntu2.2_amd64.deb ...
Unpacking libgnutls26:amd64 (2.12.23-12ubuntu2.2) over (2.12.23-12ubuntu2.1) ...
Preparing to unpack .../libssl1.0.0_1.0.1f-1ubuntu2.11_amd64.deb ...
Unpacking libssl1.0.0:amd64 (1.0.1f-1ubuntu2.11) over (1.0.1f-1ubuntu2.8) ...
Preparing to unpack .../ntpdate_1%3a4.2.6.p5+dfsg-3ubuntu2.14.04.3_amd64.deb ...
Unpacking ntpdate (1:4.2.6.p5+dfsg-3ubuntu2.14.04.3) over (1:4.2.6.p5+dfsg-3ubuntu2.14.04.2) ...
Preparing to unpack .../libroken18-heimdal_1.6~git20131207+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libroken18-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) over (1.6~git20131207+dfsg-1ubuntu1) ...
Preparing to unpack .../libasn1-8-heimdal_1.6~git20131207+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libasn1-8-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) over (1.6~git20131207+dfsg-1ubuntu1) ...
Preparing to unpack .../libhcrypto4-heimdal_1.6~git20131207+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libhcrypto4-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) over (1.6~git20131207+dfsg-1ubuntu1) ...
Preparing to unpack .../libheimbase1-heimdal_1.6~git20131207+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libheimbase1-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) over (1.6~git20131207+dfsg-1ubuntu1) ...
Preparing to unpack .../libwind0-heimdal_1.6~git20131207+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libwind0-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) over (1.6~git20131207+dfsg-1ubuntu1) ...
Preparing to unpack .../libhx509-5-heimdal_1.6~git20131207+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libhx509-5-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) over (1.6~git20131207+dfsg-1ubuntu1) ...
Preparing to unpack .../libkrb5-26-heimdal_1.6~git20131207+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libkrb5-26-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) over (1.6~git20131207+dfsg-1ubuntu1) ...
Preparing to unpack .../libheimntlm0-heimdal_1.6~git20131207+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libheimntlm0-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) over (1.6~git20131207+dfsg-1ubuntu1) ...
Preparing to unpack .../libgssapi3-heimdal_1.6~git20131207+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libgssapi3-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) over (1.6~git20131207+dfsg-1ubuntu1) ...
Preparing to unpack .../libnuma1_2.0.9~rc5-1ubuntu3_amd64.deb ...
Unpacking libnuma1:amd64 (2.0.9~rc5-1ubuntu3) over (2.0.9~rc5-1ubuntu2) ...
Preparing to unpack .../libpam-systemd_204-5ubuntu20.11_amd64.deb ...
systemd-logind stop/waiting
Unpacking libpam-systemd:amd64 (204-5ubuntu20.11) over (204-5ubuntu20.9) ...
Preparing to unpack .../systemd-services_204-5ubuntu20.11_amd64.deb ...
Unpacking systemd-services (204-5ubuntu20.11) over (204-5ubuntu20.9) ...
Preparing to unpack .../libsystemd-daemon0_204-5ubuntu20.11_amd64.deb ...
Unpacking libsystemd-daemon0:amd64 (204-5ubuntu20.11) over (204-5ubuntu20.9) ...
Preparing to unpack .../libsystemd-login0_204-5ubuntu20.11_amd64.deb ...
Unpacking libsystemd-login0:amd64 (204-5ubuntu20.11) over (204-5ubuntu20.9) ...
Preparing to unpack .../libpolkit-gobject-1-0_0.105-4ubuntu2.14.04.1_amd64.deb ...
Unpacking libpolkit-gobject-1-0:amd64 (0.105-4ubuntu2.14.04.1) over (0.105-4ubuntu2) ...
Preparing to unpack .../libxext6_2%3a1.3.2-1ubuntu0.0.14.04.1_amd64.deb ...
Unpacking libxext6:amd64 (2:1.3.2-1ubuntu0.0.14.04.1) over (2:1.3.2-1) ...
Preparing to unpack .../language-pack-en_1%3a14.04+20150219_all.deb ...
Unpacking language-pack-en (1:14.04+20150219) over (1:14.04+20141110) ...
Preparing to unpack .../language-pack-en-base_1%3a14.04+20150219_all.deb ...
Unpacking language-pack-en-base (1:14.04+20150219) over (1:14.04+20140707) ...
Preparing to unpack .../libcups2_1.7.2-0ubuntu1.5_amd64.deb ...
Unpacking libcups2:amd64 (1.7.2-0ubuntu1.5) over (1.7.2-0ubuntu1.2) ...
Preparing to unpack .../libgl1-mesa-dri_10.1.3-0ubuntu0.4_amd64.deb ...
Unpacking libgl1-mesa-dri:amd64 (10.1.3-0ubuntu0.4) over (10.1.3-0ubuntu0.3) ...
Preparing to unpack .../libgl1-mesa-glx_10.1.3-0ubuntu0.4_amd64.deb ...
Unpacking libgl1-mesa-glx:amd64 (10.1.3-0ubuntu0.4) over (10.1.3-0ubuntu0.3) ...
Preparing to unpack .../libglapi-mesa_10.1.3-0ubuntu0.4_amd64.deb ...
Unpacking libglapi-mesa:amd64 (10.1.3-0ubuntu0.4) over (10.1.3-0ubuntu0.3) ...
Preparing to unpack .../libxfixes3_1%3a5.0.1-1ubuntu1.1_amd64.deb ...
Unpacking libxfixes3:amd64 (1:5.0.1-1ubuntu1.1) over (1:5.0.1-1ubuntu1) ...
Preparing to unpack .../libgtk2.0-common_2.24.23-0ubuntu1.2_all.deb ...
Unpacking libgtk2.0-common (2.24.23-0ubuntu1.2) over (2.24.23-0ubuntu1.1) ...
Preparing to unpack .../libgtk2.0-bin_2.24.23-0ubuntu1.2_amd64.deb ...
Unpacking libgtk2.0-bin (2.24.23-0ubuntu1.2) over (2.24.23-0ubuntu1.1) ...
Preparing to unpack .../libxi6_2%3a1.7.1.901-1ubuntu1.1_amd64.deb ...
Unpacking libxi6:amd64 (2:1.7.1.901-1ubuntu1.1) over (2:1.7.1.901-1ubuntu1) ...
Preparing to unpack .../libxrender1_1%3a0.9.8-1build0.14.04.1_amd64.deb ...
Unpacking libxrender1:amd64 (1:0.9.8-1build0.14.04.1) over (1:0.9.8-1) ...
Preparing to unpack .../libgtk2.0-0_2.24.23-0ubuntu1.2_amd64.deb ...
Unpacking libgtk2.0-0:amd64 (2.24.23-0ubuntu1.2) over (2.24.23-0ubuntu1.1) ...
Preparing to unpack .../libgudev-1.0-0_1%3a204-5ubuntu20.11_amd64.deb ...
Unpacking libgudev-1.0-0:amd64 (1:204-5ubuntu20.11) over (1:204-5ubuntu20.9) ...
Preparing to unpack .../libicu52_52.1-3ubuntu0.2_amd64.deb ...
Unpacking libicu52:amd64 (52.1-3ubuntu0.2) over (52.1-3) ...
Preparing to unpack .../libpolkit-agent-1-0_0.105-4ubuntu2.14.04.1_amd64.deb ...
Unpacking libpolkit-agent-1-0:amd64 (0.105-4ubuntu2.14.04.1) over (0.105-4ubuntu2) ...
Preparing to unpack .../libpolkit-backend-1-0_0.105-4ubuntu2.14.04.1_amd64.deb ...
Unpacking libpolkit-backend-1-0:amd64 (0.105-4ubuntu2.14.04.1) over (0.105-4ubuntu2) ...
Preparing to unpack .../libpulse0_1%3a4.0-0ubuntu11.1_amd64.deb ...
Unpacking libpulse0:amd64 (1:4.0-0ubuntu11.1) over (1:4.0-0ubuntu11) ...
Preparing to unpack .../libtiff5_4.0.3-7ubuntu0.3_amd64.deb ...
Unpacking libtiff5:amd64 (4.0.3-7ubuntu0.3) over (4.0.3-7ubuntu0.1) ...
Preparing to unpack .../gpgv_1.4.16-1ubuntu2.3_amd64.deb ...
Unpacking gpgv (1.4.16-1ubuntu2.3) over (1.4.16-1ubuntu2.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Setting up gpgv (1.4.16-1ubuntu2.3) ...
(Reading database ... 90448 files and directories currently installed.)
Preparing to unpack .../gnupg_1.4.16-1ubuntu2.3_amd64.deb ...
Unpacking gnupg (1.4.16-1ubuntu2.3) over (1.4.16-1ubuntu2.1) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up gnupg (1.4.16-1ubuntu2.3) ...
(Reading database ... 90448 files and directories currently installed.)
Preparing to unpack .../multiarch-support_2.19-0ubuntu6.6_amd64.deb ...
Unpacking multiarch-support (2.19-0ubuntu6.6) over (2.19-0ubuntu6.5) ...
Setting up multiarch-support (2.19-0ubuntu6.6) ...
(Reading database ... 90448 files and directories currently installed.)
Preparing to unpack .../tzdata-java_2015b-0ubuntu0.14.04_all.deb ...
Unpacking tzdata-java (2015b-0ubuntu0.14.04) over (2015a-0ubuntu0.14.04) ...
Preparing to unpack .../tzdata_2015b-0ubuntu0.14.04_all.deb ...
Unpacking tzdata (2015b-0ubuntu0.14.04) over (2015a-0ubuntu0.14.04) ...
Setting up tzdata (2015b-0ubuntu0.14.04) ...

Current default time zone: 'Europe/London'
Local time is now:      Tue Apr 14 15:06:24 BST 2015.
Universal Time is now:  Tue Apr 14 14:06:24 UTC 2015.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

(Reading database ... 90444 files and directories currently installed.)
Preparing to unpack .../rsyslog_7.4.4-1ubuntu2.5_amd64.deb ...
Unpacking rsyslog (7.4.4-1ubuntu2.5) over (7.4.4-1ubuntu2.3) ...
Preparing to unpack .../sudo_1.8.9p5-1ubuntu1.1_amd64.deb ...
Unpacking sudo (1.8.9p5-1ubuntu1.1) over (1.8.9p5-1ubuntu1) ...
Preparing to unpack .../openssl_1.0.1f-1ubuntu2.11_amd64.deb ...
Unpacking openssl (1.0.1f-1ubuntu2.11) over (1.0.1f-1ubuntu2.8) ...
Preparing to unpack .../ubuntu-release-upgrader-core_1%3a0.220.7_all.deb ...
Unpacking ubuntu-release-upgrader-core (1:0.220.7) over (1:0.220.6) ...
Preparing to unpack .../python3-distupgrade_1%3a0.220.7_all.deb ...
Unpacking python3-distupgrade (1:0.220.7) over (1:0.220.6) ...
Preparing to unpack .../uuid-runtime_2.20.1-5.1ubuntu20.4_amd64.deb ...
Unpacking uuid-runtime (2.20.1-5.1ubuntu20.4) over (2.20.1-5.1ubuntu20.3) ...
Preparing to unpack .../apache2_2.4.7-1ubuntu4.4_amd64.deb ...
Unpacking apache2 (2.4.7-1ubuntu4.4) over (2.4.7-1ubuntu4.1) ...
Preparing to unpack .../apache2-bin_2.4.7-1ubuntu4.4_amd64.deb ...
Unpacking apache2-bin (2.4.7-1ubuntu4.4) over (2.4.7-1ubuntu4.1) ...
Preparing to unpack .../apache2-data_2.4.7-1ubuntu4.4_all.deb ...
Unpacking apache2-data (2.4.7-1ubuntu4.4) over (2.4.7-1ubuntu4.1) ...
Preparing to unpack .../python3-problem-report_2.14.1-0ubuntu3.9_all.deb ...
Unpacking python3-problem-report (2.14.1-0ubuntu3.9) over (2.14.1-0ubuntu3.6) ...
Preparing to unpack .../python3-apport_2.14.1-0ubuntu3.9_all.deb ...
Unpacking python3-apport (2.14.1-0ubuntu3.9) over (2.14.1-0ubuntu3.6) ...
Preparing to unpack .../apport_2.14.1-0ubuntu3.9_all.deb ...
apport stop/waiting
Unpacking apport (2.14.1-0ubuntu3.9) over (2.14.1-0ubuntu3.6) ...
Preparing to unpack .../gvfs_1.20.3-0ubuntu1_amd64.deb ...
Unpacking gvfs:amd64 (1.20.3-0ubuntu1) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../gvfs-daemons_1.20.3-0ubuntu1_amd64.deb ...
Unpacking gvfs-daemons (1.20.3-0ubuntu1) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../gvfs-libs_1.20.3-0ubuntu1_amd64.deb ...
Unpacking gvfs-libs:amd64 (1.20.3-0ubuntu1) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../gvfs-common_1.20.3-0ubuntu1_all.deb ...
Unpacking gvfs-common (1.20.3-0ubuntu1) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../linux-headers-3.13.0-49_3.13.0-49.83_all.deb ...
Unpacking linux-headers-3.13.0-49 (3.13.0-49.83) over (3.13.0-49.81) ...
Preparing to unpack .../linux-headers-3.13.0-49-generic_3.13.0-49.83_amd64.deb ...
Unpacking linux-headers-3.13.0-49-generic (3.13.0-49.83) over (3.13.0-49.81) ...
Preparing to unpack .../linux-image-extra-3.13.0-49-generic_3.13.0-49.83_amd64.deb ...
Unpacking linux-image-extra-3.13.0-49-generic (3.13.0-49.83) over (3.13.0-49.81) ...
Preparing to unpack .../policykit-1_0.105-4ubuntu2.14.04.1_amd64.deb ...
Unpacking policykit-1 (0.105-4ubuntu2.14.04.1) over (0.105-4ubuntu2) ...
Preparing to unpack .../python-urllib3_1.7.1-1ubuntu0.1_all.deb ...
Unpacking python-urllib3 (1.7.1-1ubuntu0.1) over (1.7.1-1build1) ...
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.2_all.deb ...
Unpacking python-requests (2.2.1-1ubuntu0.2) over (2.2.1-1ubuntu0.1) ...
Preparing to unpack .../software-properties-common_0.92.37.3_all.deb ...
Unpacking software-properties-common (0.92.37.3) over (0.92.37.2) ...
Preparing to unpack .../unattended-upgrades_0.82.1ubuntu2.2_all.deb ...
Unpacking unattended-upgrades (0.82.1ubuntu2.2) over (0.82.1ubuntu2) ...
Preparing to unpack .../python3-software-properties_0.92.37.3_all.deb ...
Unpacking python3-software-properties (0.92.37.3) over (0.92.37.2) ...
Preparing to unpack .../x11-common_1%3a7.7+1ubuntu8.1_all.deb ...
Unpacking x11-common (1:7.7+1ubuntu8.1) over (1:7.7+1ubuntu8) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ufw (0.34~rc-0ubuntu2) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
Setting up libgcrypt11:amd64 (1.5.3-2ubuntu4.2) ...
Setting up libtasn1-6:amd64 (3.4-3ubuntu0.2) ...
Setting up libgnutls26:amd64 (2.12.23-12ubuntu2.2) ...
Setting up libgnutls-openssl27:amd64 (2.12.23-12ubuntu2.2) ...
Setting up libssl1.0.0:amd64 (1.0.1f-1ubuntu2.11) ...
Setting up ntpdate (1:4.2.6.p5+dfsg-3ubuntu2.14.04.3) ...
Setting up libroken18-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Setting up libasn1-8-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Setting up libhcrypto4-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Setting up libheimbase1-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Setting up libwind0-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Setting up libhx509-5-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Setting up libkrb5-26-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Setting up libheimntlm0-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Setting up libgssapi3-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Setting up libnuma1:amd64 (2.0.9~rc5-1ubuntu3) ...
Setting up libsystemd-daemon0:amd64 (204-5ubuntu20.11) ...
Setting up systemd-services (204-5ubuntu20.11) ...
Setting up libpam-systemd:amd64 (204-5ubuntu20.11) ...
systemd-logind start/running, process 6660
Setting up libsystemd-login0:amd64 (204-5ubuntu20.11) ...
Setting up libpolkit-gobject-1-0:amd64 (0.105-4ubuntu2.14.04.1) ...
Setting up libxext6:amd64 (2:1.3.2-1ubuntu0.0.14.04.1) ...
Setting up libcups2:amd64 (1.7.2-0ubuntu1.5) ...
Setting up libgl1-mesa-dri:amd64 (10.1.3-0ubuntu0.4) ...
Setting up libglapi-mesa:amd64 (10.1.3-0ubuntu0.4) ...
Setting up libxfixes3:amd64 (1:5.0.1-1ubuntu1.1) ...
Setting up libgl1-mesa-glx:amd64 (10.1.3-0ubuntu0.4) ...
Setting up libgtk2.0-common (2.24.23-0ubuntu1.2) ...
Setting up libxi6:amd64 (2:1.7.1.901-1ubuntu1.1) ...
Setting up libxrender1:amd64 (1:0.9.8-1build0.14.04.1) ...
Setting up libgtk2.0-0:amd64 (2.24.23-0ubuntu1.2) ...
Setting up libgtk2.0-bin (2.24.23-0ubuntu1.2) ...
Setting up libgudev-1.0-0:amd64 (1:204-5ubuntu20.11) ...
Setting up libicu52:amd64 (52.1-3ubuntu0.2) ...
Setting up libpolkit-agent-1-0:amd64 (0.105-4ubuntu2.14.04.1) ...
Setting up libpolkit-backend-1-0:amd64 (0.105-4ubuntu2.14.04.1) ...
Setting up libpulse0:amd64 (1:4.0-0ubuntu11.1) ...
Setting up libtiff5:amd64 (4.0.3-7ubuntu0.3) ...
Setting up tzdata-java (2015b-0ubuntu0.14.04) ...
Setting up rsyslog (7.4.4-1ubuntu2.5) ...
The user `syslog' is already a member of `adm'.
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
rsyslog stop/waiting
rsyslog start/running, process 6880
Setting up sudo (1.8.9p5-1ubuntu1.1) ...
Setting up openssl (1.0.1f-1ubuntu2.11) ...
Setting up python3-distupgrade (1:0.220.7) ...
Setting up ubuntu-release-upgrader-core (1:0.220.7) ...
Setting up uuid-runtime (2.20.1-5.1ubuntu20.4) ...
Setting up apache2-bin (2.4.7-1ubuntu4.4) ...
Setting up apache2-data (2.4.7-1ubuntu4.4) ...
Setting up apache2 (2.4.7-1ubuntu4.4) ...
 * Restarting web server apache2                                                  AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
                                                                           [ OK ]
Setting up python3-problem-report (2.14.1-0ubuntu3.9) ...
Setting up python3-apport (2.14.1-0ubuntu3.9) ...
Setting up apport (2.14.1-0ubuntu3.9) ...
apport start/running
Setting up gvfs-common (1.20.3-0ubuntu1) ...
Setting up gvfs-libs:amd64 (1.20.3-0ubuntu1) ...
Setting up gvfs-daemons (1.20.3-0ubuntu1) ...
Setting up gvfs:amd64 (1.20.3-0ubuntu1) ...
Setting up linux-headers-3.13.0-49 (3.13.0-49.83) ...
Setting up linux-headers-3.13.0-49-generic (3.13.0-49.83) ...
Setting up linux-image-extra-3.13.0-49-generic (3.13.0-49.83) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up policykit-1 (0.105-4ubuntu2.14.04.1) ...
Setting up python-urllib3 (1.7.1-1ubuntu0.1) ...
Setting up python-requests (2.2.1-1ubuntu0.2) ...
Setting up unattended-upgrades (0.82.1ubuntu2.2) ...
Setting up python3-software-properties (0.92.37.3) ...
Setting up software-properties-common (0.92.37.3) ...
Setting up x11-common (1:7.7+1ubuntu8.1) ...
 * Setting up X socket directories...                                      [ OK ]
Setting up language-pack-en (1:14.04+20150219) ...
Setting up language-pack-en-base (1:14.04+20150219) ...
Generating locales...
  en_AG.UTF-8... up-to-date
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZM.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...


```

---

### Post by laphyzz2 on 2015-04-14
Thank you to everyone, my system seems to be working again and the program I wanted to install has installed with out a hich.

You are all amazing

---

### Post by Impavidus on 2015-04-14
Glad we could help. Just remember to uninstall old kernels before the /boot partition gets full.

---

### Post by Bashing-om on 2015-04-14
laphyzz2; Great !

And yes that thought that the order of operations was critical to remove kernels had occurred to me .. I am well pleased to have my miss-thought corrected. -Hard marked for future reference ( Impavidus, thanks so much for the instruction) .

Last but not least is a bit of final clean up:
```

dpkg -l | grep linux-

```
I expect in that output to be several packages marked 'rc' - where 'r' is removed and 'c' is config files remain:
 While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package with the following command to purge all removed but not yet purged packages .
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

All should now be finer than a frog's hair;

[INDENT][INDENT]we move on to our next adventure
[/INDENT][/INDENT]

---

### Post by bnmohler on 2015-04-15
man thats awesome it worked out. i have a similar issue only it started kinda strange. i have been cleaning my boot and it still has room on it it... but still i get the No space left on device error when trying to run an update. any chance i am missing something obvious. i practically ran through all the lines you guys did on the other machine.

```

bret@DESKTOP:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-4.0.0-rc7+
grep: /boot/config-4.0.0-rc7+: No such file or directory

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.0.0-rc7+ with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

bret@DESKTOP:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-4.0.0-rc7+
grep: /boot/config-4.0.0-rc7+: No such file or directory

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.0.0-rc7+ with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

bret@DESKTOP:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  102G   30G   68G  31% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         3.9G  8.0K  3.9G   1% /dev
tmpfs                        789M  1.5M  787M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         3.9G   15M  3.9G   1% /run/shm
none                         100M   44K  100M   1% /run/user
/dev/sda1                    236M   46M  179M  21% /boot
/home/bret/.Private          102G   30G   68G  31% /home/bret

```

```

bret@DESKTOP:~$ uname -r
3.13.0-49-generic

```

```

bret@DESKTOP:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.11                                            all          Firmware for Linux kernel drivers
ii  linux-generic                                         3.13.0.49.56                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-49                               3.13.0-49.83                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                       3.13.0-49.83                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.49.56                                        amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-49-generic                         3.13.0-49.83                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.49.56                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-49.83                                        amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

```

bret@DESKTOP:~$ dpkg -l "linux-image*"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                             Version               Architecture          Description
+++-================================-=====================-=====================-======================================================================
un  linux-image                      <none>                <none>                (no description available)
un  linux-image-3.0                  <none>                <none>                (no description available)
ii  linux-image-3.13.0-49-generic    3.13.0-49.83          amd64                 Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-49-gene 3.13.0-49.83          amd64                 Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic              3.13.0.49.56          amd64                 Generic Linux kernel image

```

with a reported 21% used i dont see how i am getting an error. when i watch the /boot folder from the UI file browser i see the initrd.img-4.0.0-rc7+ appear and then when the error happens it goes away. i dont have anything in my trash bin either. !?!? im stumpped this time around. i have been able to purge a few other times in the past with no issues :/

---

### Post by Bashing-om on 2015-04-16
bnmohler; Hello .

Ungood:

This:
> 
update-initramfs: failed for /boot/initrd.img-4.0.0-rc7+ with 1.

says you are messing about with the proposed release of 15.04

this:
> 
gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1

says you are trashing ram .. maybe running out of ram ?? 
-----------------------
This will be better handled in the ubuntu+1 sub forum.
Those guys who do the 15.04 testing may find this of great interest.

this I think
[INDENT][INDENT][INDENT]right time
[INDENT][INDENT][INDENT]right place -> ubuuntu+1
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bnmohler on 2015-04-16
umm yikes?

not quite sure how that would be as i take the updates directly through the software updater.

as far as ram i have 8gb in the system with only 1.5 being used by the system. so def not running out of ram.

thanks for the info and i will see about getting this over to their eyes. i really hope this install is not hosed... i got everything how i want it so starting over would be annoying.

ill keep you posted

---

