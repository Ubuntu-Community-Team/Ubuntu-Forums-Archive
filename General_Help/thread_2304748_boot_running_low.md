---
title: "boot running low"
date: 2015-11-29
forum: General Help
---

### Post by ewuntu on 2015-11-29
Trusty Tahr  getting a warning "volume at 9.8MB. Suggested fix is to remove unused progs. or move to another partition".
Have no unused progs. Do not know how to move anything from one part. to another.
Someone suggested uninstalling unused kernels via CLI  sudo apt-get remove linux  and hit Tab twice. This should list all kernels on the PC.
Nothing happens.
Any help greatly appreciated, Thank you.

---

### Post by Bashing-om on 2015-11-29
ewuntu; Hello;

What returns from terminal command :
```

sudo apt-get autoremove

```

Does this remove those old kernels ?

Else; well, we do it the manual way .

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2015-11-29
> **ewuntu said:**
> Someone suggested uninstalling unused kernels via CLI  sudo apt-get remove linux  and hit Tab twice. This should list all kernels on the PC.
No, telling the system to *remove* the 'linux' metapackage will not instead *list* all the kernel packages on your system.
Perhaps you should not trust that 'someone' with your data. They are not your friend.

The first step is to determine the nature of the problem.
Please show us the complete output of the following two commands:
```
df
df -i
```

---

### Post by ewuntu on 2015-11-29
autoremove does nothing
 tried sudo apt-get clean nothing also

---

### Post by Bashing-om on 2015-11-29
ewuntu; Well .....

Then, we best be looking.
As Ian advises:
```

df -h
df -i
dpkg -l | grep linux

```
between code tags please :
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


see
[INDENT][INDENT]what we see
[/INDENT][/INDENT]

---

### Post by ewuntu on 2015-11-29
```
qrt67@qrt67-System-Product-Name:~$ df
Filesystem                  1K-blocks     Used Available Use% Mounted on
/dev/mapper/ubuntu--vg-root  74415288 11861204  58750948  17% /
none                                4        0         4   0% /sys/fs/cgroup
udev                          1007692        4   1007688   1% /dev
tmpfs                          204780     1332    203448   1% /run
none                             5120        0      5120   0% /run/lock
none                          1023880     6252   1017628   1% /run/shm
none                           102400       48    102352   1% /run/user
/dev/sda1                      240972   218991      9540  96% /boot
/home/qrt67/.Private         74415288 11861204  58750948  17% /home/qrt67

qrt67@qrt67-System-Product-Name:~$ df -i
Filesystem                   Inodes  IUsed   IFree IUse% Mounted on
/dev/mapper/ubuntu--vg-root 4734976 368996 4365980    8% /
none                         255970      2  255968    1% /sys/fs/cgroup
udev                         251923    492  251431    1% /dev
tmpfs                        255970    542  255428    1% /run
none                         255970      4  255966    1% /run/lock
none                         255970     29  255941    1% /run/shm
none                         255970     28  255942    1% /run/user
/dev/sda1                     62248    322   61926    1% /boot
/home/qrt67/.Private        4734976 368996 4365980    8% /home/qrt67
```

---

### Post by ewuntu on 2015-11-29
re code tags
sorry about that but the # symbol does not appear in the quick reply box

---

### Post by Bashing-om on 2015-11-29
ewuntul Heym hey ...


Never mind ya got the code tags ! Thanks .
---------------
edit your post and add the code tags ... if you read as much code in a day as we do, it makes a huge difference,
And when you get as tired as we get from hours in front of code ... sure helps to have a format we can readily  read.

[INDENT][INDENT]I make enough mistakes on my own
[INDENT][INDENT][INDENT]I do not need help to make them
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

-------------------
OK .. we do know it is /boot that is hurting :
> 
/dev/sda1                      240972   218991      9540  96% /boot

with 96% useage.

Now we need to see what is taking up the space ... most likely old kernels .
```

dpkg -l | grep linux-

```
as a short cut to what we may do.

ain't nothing but a thing

---

### Post by QIII on 2015-11-29
If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by ewuntu on 2015-11-29
```
qrt67@qrt67-System-Product-Name:~$ df
Filesystem                  1K-blocks     Used Available Use% Mounted on
/dev/mapper/ubuntu--vg-root  74415288 11861832  58750320  17% /
none                                4        0         4   0% /sys/fs/cgroup
udev                          1007692        4   1007688   1% /dev
tmpfs                          204780     1332    203448   1% /run
none                             5120        0      5120   0% /run/lock
none                          1023880     9156   1014724   1% /run/shm
none                           102400       48    102352   1% /run/user
/dev/sda1                      240972   218991      9540  96% /boot
/home/qrt67/.Private         74415288 11861832  58750320  17% /home/qrt67
```

---

### Post by ewuntu on 2015-11-29
```

qrt67@qrt67-System-Product-Name:~$ df
Filesystem                  1K-blocks     Used Available Use% Mounted on
/dev/mapper/ubuntu--vg-root  74415288 11861832  58750320  17% /
none                                4        0         4   0% /sys/fs/cgroup
udev                          1007692        4   1007688   1% /dev
tmpfs                          204780     1332    203448   1% /run
none                             5120        0      5120   0% /run/lock
none                          1023880     9156   1014724   1% /run/shm
none                           102400       48    102352   1% /run/user
/dev/sda1                      240972   218991      9540  96% /boot
/home/qrt67/.Private         74415288 11861832  58750320  17% /home/qrt67

```

```

qrt67@qrt67-System-Product-Name:~$ df -i
Filesystem                   Inodes  IUsed   IFree IUse% Mounted on
/dev/mapper/ubuntu--vg-root 4734976 369003 4365973    8% /
none                         255970      2  255968    1% /sys/fs/cgroup
udev                         251923    492  251431    1% /dev
tmpfs                        255970    542  255428    1% /run
none                         255970      4  255966    1% /run/lock
none                         255970     33  255937    1% /run/shm
none                         255970     28  255942    1% /run/user
/dev/sda1                     62248    322   61926    1% /boot
/home/qrt67/.Private        4734976 369003 4365973    8% /home/qrt67

```

---

### Post by ewuntu on 2015-11-29
```

qrt67@qrt67-System-Product-Name:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root   71G   12G   57G  17% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         985M  4.0K  985M   1% /dev
tmpfs                        200M  1.4M  199M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                        1000M   11M  990M   2% /run/shm
none                         100M   48K  100M   1% /run/user
/dev/sda1                    236M  214M  9.4M  96% /boot
/home/qrt67/.Private          71G   12G   57G  17% /home/qrt67

```

```

qrt67@qrt67-System-Product-Name:~$ df -i
Filesystem                   Inodes  IUsed   IFree IUse% Mounted on
/dev/mapper/ubuntu--vg-root 4734976 369003 4365973    8% /
none                         255970      2  255968    1% /sys/fs/cgroup
udev                         251923    492  251431    1% /dev
tmpfs                        255970    542  255428    1% /run
none                         255970      4  255966    1% /run/lock
none                         255970     31  255939    1% /run/shm
none                         255970     28  255942    1% /run/user
/dev/sda1                     62248    322   61926    1% /boot
/home/qrt67/.Private        4734976 369003 4365973    8% /home/qrt67

```

```

qrt67@qrt67-System-Product-Name:~$ dpkg -l | grep linux
ii  libselinux1:amd64                                     2.2.2-1ubuntu0.1                                    amd64        SELinux runtime shared libraries
ii  libselinux1:i386                                      2.2.2-1ubuntu0.1                                    i386         SELinux runtime shared libraries
ii  libv4l-0:amd64                                        1.0.1-1                                             amd64        Collection of video4linux support libraries
ii  libv4l-0:i386                                         1.0.1-1                                             i386         Collection of video4linux support libraries
ii  libv4lconvert0:amd64                                  1.0.1-1                                             amd64        Video4linux frame format conversion library
ii  libv4lconvert0:i386                                   1.0.1-1                                             i386         Video4linux frame format conversion library
ii  linux-firmware                                        1.127.18                                            all          Firmware for Linux kernel drivers
iU  linux-generic-lts-vivid                               3.19.0.33.20                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.19.0-26                               3.19.0-26.28~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-26-generic                       3.19.0-26.28~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-28                               3.19.0-28.30~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-28-generic                       3.19.0-28.30~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-30                               3.19.0-30.34~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-30-generic                       3.19.0-30.34~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-31                               3.19.0-31.36~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-31-generic                       3.19.0-31.36~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-33                               3.19.0-33.38~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-33-generic                       3.19.0-33.38~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-vivid                       3.19.0.33.20                                        amd64        Generic Linux kernel headers
rc  linux-image-3.19.0-25-generic                         3.19.0-25.26~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-26-generic                         3.19.0-26.28~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-28-generic                         3.19.0-28.30~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-30-generic                         3.19.0-30.34~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-generic                         3.19.0-31.36~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-33-generic                         3.19.0-33.38~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-25-generic                   3.19.0-25.26~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-26-generic                   3.19.0-26.28~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-28-generic                   3.19.0-28.30~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-30-generic                   3.19.0-30.34~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-31-generic                   3.19.0-31.36~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
iF  linux-image-extra-3.19.0-33-generic                   3.19.0-33.38~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
iU  linux-image-generic-lts-vivid                         3.19.0.33.20                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-68.111                                       amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
rc  playonlinux                                           4.2.2-1                                             all          front-end for Wine
ii  pptp-linux                                            1.7.2-7                                             amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                              3:4.05+dfsg-6+deb8u1                                amd64        collection of boot loaders
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                            2.20.1-5.1ubuntu20.7                                amd64        Miscellaneous system utilities

```

---

### Post by Bashing-om on 2015-11-29
ewuntu; OK;

We have a good clue why "autoremove" fails:
> 
iU  linux-generic-lts-vivid 

where the 'iU' means desired is (i)nstalled BUT the U says it is (U)ninstalled. We will take care of that little detail later.
Next before we clean this up, we need to know the kernel that you are presently booting - We MUST not remove this one.
show us:
```

uname -r

```

Then I think
[INDENT][INDENT]we are ready
[INDENT][INDENT][INDENT]to go to work
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ewuntu on 2015-11-29
```

qrt67@qrt67-System-Product-Name:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.18                                            all          Firmware for Linux kernel drivers
iU  linux-generic-lts-vivid                               3.19.0.33.20                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.19.0-26                               3.19.0-26.28~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-26-generic                       3.19.0-26.28~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-28                               3.19.0-28.30~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-28-generic                       3.19.0-28.30~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-30                               3.19.0-30.34~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-30-generic                       3.19.0-30.34~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-31                               3.19.0-31.36~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-31-generic                       3.19.0-31.36~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-33                               3.19.0-33.38~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-33-generic                       3.19.0-33.38~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-vivid                       3.19.0.33.20                                        amd64        Generic Linux kernel headers
rc  linux-image-3.19.0-25-generic                         3.19.0-25.26~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-26-generic                         3.19.0-26.28~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-28-generic                         3.19.0-28.30~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-30-generic                         3.19.0-30.34~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-generic                         3.19.0-31.36~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-33-generic                         3.19.0-33.38~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-25-generic                   3.19.0-25.26~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-26-generic                   3.19.0-26.28~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-28-generic                   3.19.0-28.30~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-30-generic                   3.19.0-30.34~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-31-generic                   3.19.0-31.36~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
iF  linux-image-extra-3.19.0-33-generic                   3.19.0-33.38~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
iU  linux-image-generic-lts-vivid                         3.19.0.33.20                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-68.111                                       amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by ewuntu on 2015-11-29
```

qrt67@qrt67-System-Product-Name:~$ uname -r
3.19.0-33-generic

```

---

### Post by Bashing-om on 2015-11-29
ewuntu; Yes ...

We have enough to work with.
However, I am tired and my eyes are crossing. Rather than make an error in my instruction I am calling it a end to this session and we take this back up on my morrow.

[INDENT][INDENT]to err is human
[INDENT][INDENT][INDENT]but I can really foul things up
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-11-30
ewuntu; Morning ...

Back and much refreshed .
Here we go.

Run terminal commands:
```

sudo dpkg -P linux-image-3.19.0-{25,26,28,30}-generic
sudo dpkg -P linux-headers-3.19.0-{26,28,30-generic
sudo dpkg -P linux-headers-3.19.0-{26,28,30}
sudo dpkg -P linux-image-extra-3.19.0-{25,26,28,30}-generic

```
to remove the old kernels.

If hat goes well, we then (RE-)install linux-generic-lts-vivid  and linux-image-generic-lts-vivid.
Then verify our work that all is well.

[INDENT][INDENT][INDENT]we can do this
[/INDENT][/INDENT][/INDENT]

---

### Post by ewuntu on 2015-11-30
How are doing?
This is all received. The CLI stopped before completing.
```

 qrt67@qrt67-System-Product-Name:~$ sudo dpkg -P linux-image-3.19.0-{25,26,28,30}-generic[sudo] password for qrt67: 
dpkg: warning: ignoring request to remove linux-image-3.19.0-25-generic which isn't installed
(Reading database ... 321127 files and directories currently installed.)
Removing linux-image-3.19.0-26-generic (3.19.0-26.28~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
dkms: removing: ndiswrapper 1.59 (3.19.0-26-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  ndiswrapper
Version: 1.59
Kernel:  3.19.0-26-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


ndiswrapper.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-33-generic
Found initrd image: /boot/initrd.img-3.19.0-33-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.19.0-26-generic (3.19.0-26.28~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
Removing linux-image-3.19.0-28-generic (3.19.0-28.30~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
dkms: removing: ndiswrapper 1.59 (3.19.0-28-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  ndiswrapper
Version: 1.59
Kernel:  3.19.0-28-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


ndiswrapper.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-28-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-33-generic
Found initrd image: /boot/initrd.img-3.19.0-33-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.19.0-28-generic (3.19.0-28.30~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
Removing linux-image-3.19.0-30-generic (3.19.0-30.34~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
dkms: removing: ndiswrapper 1.59 (3.19.0-30-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  ndiswrapper
Version: 1.59
Kernel:  3.19.0-30-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


ndiswrapper.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-30-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-33-generic
Found initrd image: /boot/initrd.img-3.19.0-33-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.19.0-30-generic (3.19.0-30.34~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
qrt67@qrt67-System-Product-Name:~$ qrt67@qrt67-System-Product-Name:~$ sudo dpkg -P linux-image-3.19.0-{25,26,28,30}-generic
qrt67@qrt67-System-Product-Name:~$: command not found
qrt67@qrt67-System-Product-Name:~$ [sudo] password for qrt67: 
[sudo]: command not found
qrt67@qrt67-System-Product-Name:~$ dpkg: warning: ignoring request to remove linux-image-3.19.0-25-generic which isn't installed
> (Reading database ... 321127 files and directories currently installed.)
> Removing linux-image-3.19.0-26-generic (3.19.0-26.28~14.04.1) ...
> Examining /etc/kernel/prerm.d.
> run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
> dkms: removing: ndiswrapper 1.59 (3.19.0-26-generic) (x86_64)
> 
> -------- Uninstall Beginning --------
> Module:  ndiswrapper
> Version: 1.59
> Kernel:  3.19.0-26-generic (x86_64)
> -------------------------------------
> 
> Status: Before uninstall, this module version was ACTIVE on this kernel.
> 
> ndiswrapper.ko:
>  - Uninstallation
>    - Deleting from: /lib/modules/3.19.0-26-generic/updates/dkms/
>  - Original module
>    - No original module was found for this module on this kernel.
>    - Use the dkms install command to reinstall any previous module version.
> 
> depmod....
> 
> DKMS: uninstall completed.
> Examining /etc/kernel/postrm.d .
> run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
> update-initramfs: Deleting /boot/initrd.img-3.19.0-26-generic
> run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
> Generating grub configuration file ...
> Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
> Found linux image: /boot/vmlinuz-3.19.0-33-generic
> Found initrd image: /boot/initrd.img-3.19.0-33-generic
> Found linux image: /boot/vmlinuz-3.19.0-31-generic
> Found initrd image: /boot/initrd.img-3.19.0-31-generic
> Found linux image: /boot/vmlinuz-3.19.0-30-generic
> Found initrd image: /boot/initrd.img-3.19.0-30-generic
> Found linux image: /boot/vmlinuz-3.19.0-28-generic
> Found initrd image: /boot/initrd.img-3.19.0-28-generic
> Found memtest86+ image: /memtest86+.elf
> Found memtest86+ image: /memtest86+.bin
> done
> Purging configuration files for linux-image-3.19.0-26-generic (3.19.0-26.28~14.04.1) ...
> Examining /etc/kernel/postrm.d .
> run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
> run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
> Removing linux-image-3.19.0-28-generic (3.19.0-28.30~14.04.1) ...
> Examining /etc/kernel/prerm.d.
> run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
> dkms: removing: ndiswrapper 1.59 (3.19.0-28-generic) (x86_64)
> 
> -------- Uninstall Beginning --------
> Module:  ndiswrapper
> Version: 1.59
> Kernel:  3.19.0-28-generic (x86_64)
> -------------------------------------
> 
> Status: Before uninstall, this module version was ACTIVE on this kernel.
> 
> ndiswrapper.ko:
>  - Uninstallation
>    - Deleting from: /lib/modules/3.19.0-28-generic/updates/dkms/
>  - Original module
>    - No original module was found for this module on this kernel.
>    - Use the dkms install command to reinstall any previous module version.
> 
> depmod....
> 
> DKMS: uninstall completed.
> Examining /etc/kernel/postrm.d .
> run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
> update-initramfs: Deleting /boot/initrd.img-3.19.0-28-generic
> run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
> Generating grub configuration file ...
> Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
> Found linux image: /boot/vmlinuz-3.19.0-33-generic
> Found initrd image: /boot/initrd.img-3.19.0-33-generic
> Found linux image: /boot/vmlinuz-3.19.0-31-generic
> Found initrd image: /boot/initrd.img-3.19.0-31-generic
> Found linux image: /boot/vmlinuz-3.19.0-30-generic
> Found initrd image: /boot/initrd.img-3.19.0-30-generic
> Found memtest86+ image: /memtest86+.elf
> Found memtest86+ image: /memtest86+.bin
> done
> Purging configuration files for linux-image-3.19.0-28-generic (3.19.0-28.30~14.04.1) ...
> Examining /etc/kernel/postrm.d .
> run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
> run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
> Removing linux-image-3.19.0-30-generic (3.19.0-30.34~14.04.1) ...
> Examining /etc/kernel/prerm.d.
> run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
> dkms: removing: ndiswrapper 1.59 (3.19.0-30-generic) (x86_64)
> 
> -------- Uninstall Beginning --------
> Module:  ndiswrapper
> Version: 1.59
> Kernel:  3.19.0-30-generic (x86_64)
> -------------------------------------
> 
> Status: Before uninstall, this module version was ACTIVE on this kernel.
> 
> ndiswrapper.ko:
>  - Uninstallation
>    - Deleting from: /lib/modules/3.19.0-30-generic/updates/dkms/
>  - Original module
>    - No original module was found for this module on this kernel.
>    - Use the dkms install command to reinstall any previous module version.
> 
> depmod....
> 
> DKMS: uninstall completed.
> Examining /etc/kernel/postrm.d .
> run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
> update-initramfs: Deleting /boot/initrd.img-3.19.0-30-generic
> run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
> Generating grub configuration file ...
> Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
> Found linux image: /boot/vmlinuz-3.19.0-33-generic
> Found initrd image: /boot/initrd.img-3.19.0-33-generic
> Found linux image: /boot/vmlinuz-3.19.0-31-generic
> Found initrd image: /boot/initrd.img-3.19.0-31-generic
> Found memtest86+ image: /memtest86+.elf
> Found memtest86+ image: /memtest86+.bin
> done
> Purging configuration files for linux-image-3.19.0-30-generic (3.19.0-30.34~14.04.1) ...
> Examining /etc/kernel/postrm.d .
> run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
> run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic

```

---

### Post by ewuntu on 2015-11-30
Software updater just advised it needs to restart the PC to complete the update.
From the last CLI output it looks like the kernal in use was deleted.
If the PC is restarted now dont think it will boot.

---

### Post by Bashing-om on 2015-11-30
ewuntu; Well ..

That all looked good to me ... you should now have the 3.19.0-31 and -33 kernels remaining on the system.
Do now:
```

df -h

```
to verify we have disk space reclaimed and now have operating head room.
Then we re-install linux-generic-lts-vivid and linux-image-generic-lts-vivid .
Might pay us to double check on the -25 kernel . Make sure it is gone:
```

dpkg -l | grep linux- 

```

as we proceed
[INDENT][INDENT][INDENT]merrily on our way
[/INDENT][/INDENT][/INDENT]

---

### Post by ewuntu on 2015-11-30
```

qrt67@qrt67-System-Product-Name:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root   71G  9.8G   58G  15% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         985M   12K  985M   1% /dev
tmpfs                        200M  1.4M  199M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                        1000M  7.9M  993M   1% /run/shm
none                         100M   48K  100M   1% /run/user
/dev/sda1                    236M   92M  133M  41% /boot
/home/qrt67/.Private          71G  9.8G   58G  15% /home/qrt67

```

---

### Post by ewuntu on 2015-11-30
```

qrt67@qrt67-System-Product-Name:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.18                                            all          Firmware for Linux kernel drivers
iU  linux-generic-lts-vivid                               3.19.0.33.20                                        amd64        Complete Generic Linux kernel and headers
pi  linux-headers-3.19.0-26                               3.19.0-26.28~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-26-generic                       3.19.0-26.28~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
pi  linux-headers-3.19.0-28                               3.19.0-28.30~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-28-generic                       3.19.0-28.30~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
pi  linux-headers-3.19.0-30                               3.19.0-30.34~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-30-generic                       3.19.0-30.34~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-31                               3.19.0-31.36~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-31-generic                       3.19.0-31.36~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-33                               3.19.0-33.38~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-33-generic                       3.19.0-33.38~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-vivid                       3.19.0.33.20                                        amd64        Generic Linux kernel headers
ii  linux-image-3.19.0-31-generic                         3.19.0-31.36~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-33-generic                         3.19.0-33.38~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-31-generic                   3.19.0-31.36~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
iF  linux-image-extra-3.19.0-33-generic                   3.19.0-33.38~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
iU  linux-image-generic-lts-vivid                         3.19.0.33.20                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-68.111                                       amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Bashing-om on 2015-11-30
ewuntu; Hummm ..

Looks 'fairly' good, but, something did not go right for the header fills:
run:
```

sudo dpkg -P linux-headers-3.19.0-26-generic 
sudo dpkg -P linux-headers-3.19.0-26
sudo dpkg -P linux-headers-3.19.0-28-generic 
sudo dpkg -P linux-headers-3.19.0-28
sudo dpkg -P linux-headers-3.19.0-30-generic
sudo dpkg -P linux-headers-3.19.0-30

```

I got the removal order reversed  before !

See if this cleans things up .

[INDENT][INDENT]try try try again
[/INDENT][/INDENT]

---

### Post by ewuntu on 2015-11-30
Can all six lines of code be run at once or one at at time?

---

### Post by Bashing-om on 2015-11-30
ewuntu; Yeah;

We could craft that up as a one liner .. but I would like to run them one at a time and insure there are no problems now .

Makes me feel real bad when I make an error as I did before .

[INDENT][INDENT]linux
[INDENT][INDENT][INDENT]if it is hard
[INDENT][INDENT][INDENT][INDENT]you are doing something wrong[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ewuntu on 2015-11-30
Ok.
```
qrt67@qrt67-System-Product-Name:~$ sudo dpkg -P linux-headers-3.19.0-26-generic[sudo] password for qrt67: 
(Reading database ... 318145 files and directories currently installed.)
Removing linux-headers-3.19.0-26-generic (3.19.0-26.28~14.04.1) ...

```

---

### Post by ewuntu on 2015-11-30
```

qrt67@qrt67-System-Product-Name:~$ sudo dpkg -P linux-headers-3.19.0-26
(Reading database ... 309010 files and directories currently installed.)
Removing linux-headers-3.19.0-26 (3.19.0-26.28~14.04.1) ...

```

---

### Post by ewuntu on 2015-11-30
```

qrt67@qrt67-System-Product-Name:~$ sudo dpkg -P linux-headers-3.19.0-28-generic 
(Reading database ... 293187 files and directories currently installed.)
Removing linux-headers-3.19.0-28-generic (3.19.0-28.30~14.04.1) ...

```

---

### Post by ewuntu on 2015-11-30
```

qrt67@qrt67-System-Product-Name:~$ sudo dpkg -P linux-headers-3.19.0-28
[sudo] password for qrt67: 
(Reading database ... 284051 files and directories currently installed.)
Removing linux-headers-3.19.0-28 (3.19.0-28.30~14.04.1) ...

```

---

### Post by Bashing-om on 2015-11-30
ewuntu; Uh Huh ;

Looks good ... carry on .
Advise when done OR there are errors reported ..

Then we carry on .

[INDENT][INDENT]small steps
[INDENT][INDENT][INDENT]one at a time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ewuntu on 2015-11-30
```

qrt67@qrt67-System-Product-Name:~$ sudo dpkg -P linux-headers-3.19.0-30-generic
(Reading database ... 268228 files and directories currently installed.)
Removing linux-headers-3.19.0-30-generic (3.19.0-30.34~14.04.1) ...

```

---

### Post by ewuntu on 2015-11-30
```

qrt67@qrt67-System-Product-Name:~$ sudo dpkg -P linux-headers-3.19.0-30
[sudo] password for qrt67: 
(Reading database ... 259092 files and directories currently installed.)
Removing linux-headers-3.19.0-30 (3.19.0-30.34~14.04.1) ...

```

---

### Post by ewuntu on 2015-11-30
all six lines of code sent

---

### Post by Bashing-om on 2015-11-30
ewuntu; Great;

And now:
```

sudo apt-get install --reinstall linux-generic-lts-vivid
sudo apt-get install --reinstall linux-image-generic-lts-vivid 

```

And now I expect
[INDENT][INDENT]all is well in your ubuntu world
[/INDENT][/INDENT]

---

### Post by ewuntu on 2015-11-30
```

qrt67@qrt67-System-Product-Name:~$ sudo apt-get install --reinstall linux-generic-lts-vivid[sudo] password for qrt67: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for linux-generic-lts-vivid:amd64

```

---

### Post by ewuntu on 2015-11-30
```

qrt67@qrt67-System-Product-Name:~$ sudo apt-get install --reinstall linux-image-generic-lts-vivid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for linux-image-generic-lts-vivid:amd64

```

---

### Post by Bashing-om on 2015-11-30
ewuntu; Humm ...

Surprise, surprise ... maybe the 'iU  ' on  " iU  linux-generic-lts-vivid" is the hint here for the condition . Not installed so can not --reinstall ?

let's try as:
```

sudo apt-get install linux-image-generic-lts-vivid
sudo apt-get install linux-image-lts-vivid

```
as we know the file(s) exist in the repo and we now know the order of installation:
> 
sysop@1404mini:~$ apt-cache show linux-generic-lts-vivid
<snip>
Depends: linux-image-generic-lts-vivid (= 3.19.0.33.20), linux-headers-generic-lts-vivid (= 3.19.0.33.20)
Filename: pool/main/l/linux-meta-lts-vivid/linux-generic-lts-vivid_3.19.0.33.20_amd64.deb
Size: 1798
<snip>


[INDENT][INDENT]if on 2nd one does not succeed
[INDENT][INDENT][INDENT]do something else
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ewuntu on 2015-11-30
```

qrt67@qrt67-System-Product-Name:~$ sudo apt-get install linux-image-generic-lts-vivid
[sudo] password for qrt67: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-generic-lts-vivid is already the newest version.
linux-image-generic-lts-vivid set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-image-extra-3.19.0-33-generic (3.19.0-33.38~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-33-generic /boot/vmlinuz-3.19.0-33-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-33-generic /boot/vmlinuz-3.19.0-33-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-33-generic /boot/vmlinuz-3.19.0-33-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-33-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-33-generic /boot/vmlinuz-3.19.0-33-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-33-generic /boot/vmlinuz-3.19.0-33-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-33-generic /boot/vmlinuz-3.19.0-33-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-33-generic
Found initrd image: /boot/initrd.img-3.19.0-33-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-generic-lts-vivid (3.19.0.33.20) ...
Setting up linux-generic-lts-vivid (3.19.0.33.20) ...

```

---

### Post by ewuntu on 2015-11-30
```

qrt67@qrt67-System-Product-Name:~$ sudo apt-get install linux-image-lts-vivid
[sudo] password for qrt67: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image-lts-vivid

```

---

### Post by Bashing-om on 2015-11-30
ewuntu; Yeah !

That is a fact:
we are working with:
> 
linux-generic-lts-vivid 
iU  linux-image-generic-lts-vivid ##done - sudo apt-get install linux-image-generic-lts-vivid

and instead of :
> 
sysop@1404mini:~$ apt-cache show linux-image-lts-vivid
N: Unable to locate package linux-image-lts-vivid
E: No packages found
sysop@1404mini:~$
E: Unable to locate package linux-image-lts-vivid


SO, the correct package to install is:
```

sudo apt-get install linux-generic-lts-vivid

```

[INDENT][INDENT]3rd time the charm ?
[/INDENT][/INDENT]

---

### Post by ewuntu on 2015-11-30
```

qrt67@qrt67-System-Product-Name:~$ sudo apt-get install linux-generic-lts-vivid
[sudo] password for qrt67: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-generic-lts-vivid is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Bashing-om on 2015-11-30
ewuntu; Outstanding !

Finally ...

OK .. have you rebooted .. and all is good ?

Is your disk space now at a level you can cope with ? Are your concerns now met in this matter ?

[INDENT][INDENT]I must say
[INDENT][INDENT][INDENT]I made this more difficult than it is .
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ewuntu on 2015-11-30
Did not reboot. Waiting for your go ahead. Will do now.
Thank you for sticking with it.

---

### Post by ewuntu on 2015-11-30
Reboot ok. No warning about "boot volume low".

Thanks again Bashin-om

---

### Post by Bashing-om on 2015-11-30
ewuntu; Good deal .

Sorry it took so long .

[INDENT][INDENT][INDENT]you do good work
[/INDENT][/INDENT][/INDENT]

---

