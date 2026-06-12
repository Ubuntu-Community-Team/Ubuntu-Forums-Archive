---
title: "Drive Space error"
date: 2015-07-10
forum: General Help
---

### Post by stockpimp on 2015-07-10
I had an HD go bad on me a few weeks back.  I have replaced it and installed Ubuntu LTS.  For some reason (i have never had this issue with Ubuntu) I get an out of space error and I have no idea how to fix it.  I have used about 15G of 1T or there abouts so I have a "bit" or two of space left....  There's obviously some partition that's creating the error but when I get the error it doesn't provide a solution allowing me to move the partition, only very helpful advice like delete files etc.  As it sit's I can't add software updates or new programs as the boot drive (or equivalent) is full.  Appreciate any help!

Regards

D

---

### Post by Bashing-om on 2015-07-10
stockpimp; Hello;

When you installed did you choose 'encryption and/or LVM' ? There is a known bug where the /boot partition is created too small:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)

In any event we need to look at the disk space allocation, and see that we find the cause of the "out of disk space" condition:

Post back the outputs - Between code tags, please - of terminal commands:
```

df -h
df -i
dpkg -l | grep linux
cd /
sudo du -sx * | sort -n
cd

```

[INDENT][INDENT]and the tale will be told
[/INDENT][/INDENT]

---

### Post by stockpimp on 2015-07-10
> **Bashing-om said:**
> stockpimp; Hello;

When you installed did you choose 'encryption and/or LVM' ? There is a known bug where the /boot partition is created too small:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)

In any event we need to look at the disk space allocation, and see that we find the cause of the "out of disk space" condition:

Post back the outputs - Between code tags, please - of terminal commands:
```

df -h

Filesystem                   Size  Used Avail Use% Mounted on
udev                         3.9G     0  3.9G   0% /dev
tmpfs                        789M   20M  770M   3% /run
/dev/mapper/ubuntu--vg-root  909G   41G  823G   5% /
tmpfs                        3.9G  109M  3.8G   3% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda1                    236M  221M  2.3M 100% /boot
cgmfs                        100K     0  100K   0% /run/cgmanager/fs
/dev/sdb1                    466G  114G  353G  25% /media/dj/My Passport
tmpfs                        789M   56K  789M   1% /run/user/1000



df -i

Filesystem                     Inodes  IUsed     IFree IUse% Mounted on
udev                           996334    594    995740    1% /dev
tmpfs                         1008794    788   1008006    1% /run
/dev/mapper/ubuntu--vg-root  60514304 357823  60156481    1% /
tmpfs                         1008794    162   1008632    1% /dev/shm
tmpfs                         1008794      9   1008785    1% /run/lock
tmpfs                         1008794     17   1008777    1% /sys/fs/cgroup
/dev/sda1                       62248    322     61926    1% /boot
cgmfs                         1008794     13   1008781    1% /run/cgmanager/fs
/dev/sdb1                   369471240  79124 369392116    1% /media/dj/My Passport
tmpfs                         1008794     31   1008763    1% /run/user/1000



dpkg -l | grep linux

ii  console-setup-linux                                  1.108ubuntu5                               all          Linux specific part of console-setup
ii  libselinux1:amd64                                    2.3-2                                      amd64        SELinux runtime shared libraries
ii  libselinux1:i386                                     2.3-2                                      i386         SELinux runtime shared libraries
ii  libv4l-0:amd64                                       1.6.0-2                                    amd64        Collection of video4linux support libraries
ii  libv4lconvert0:amd64                                 1.6.0-2                                    amd64        Video4linux frame format conversion library
ii  linux-firmware                                       1.143.1                                    all          Firmware for Linux kernel drivers
iU  linux-generic                                        3.19.0.21.20                               amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.19.0-15                              3.19.0-15.15                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-15-generic                      3.19.0-15.15                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-16                              3.19.0-16.16                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-16-generic                      3.19.0-16.16                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-18                              3.19.0-18.18                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-18-generic                      3.19.0-18.18                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-20                              3.19.0-20.20                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-20-generic                      3.19.0-20.20                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-21                              3.19.0-21.21                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-21-generic                      3.19.0-21.21                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic                                3.19.0.21.20                               amd64        Generic Linux kernel headers
ii  linux-image-3.19.0-15-generic                        3.19.0-15.15                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-16-generic                        3.19.0-16.16                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-18-generic                        3.19.0-18.18                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-20-generic                        3.19.0-20.20                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-21-generic                        3.19.0-21.21                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-15-generic                  3.19.0-15.15                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-16-generic                  3.19.0-16.16                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-18-generic                  3.19.0-18.18                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-20-generic                  3.19.0-20.20                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
iF  linux-image-extra-3.19.0-21-generic                  3.19.0-21.21                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
iU  linux-image-generic                                  3.19.0.21.20                               amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                 3.19.0-21.21                               amd64        Linux Kernel Headers for development
ii  linux-sound-base                                     1.0.25+dfsg-0ubuntu4                       all          base package for ALSA and OSS sound systems
ii  pptp-linux                                           1.7.2-7                                    amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                             3:6.03+dfsg-5ubuntu1                       amd64        collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                                      3:6.03+dfsg-5ubuntu1                       all          collection of bootloaders (common)
ii  syslinux-legacy                                      2:3.63+dfsg-2ubuntu6                       amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                           2.25.2-4ubuntu2                            amd64        Miscellaneous system utilities



cd /



sudo du -sx * | sort -n

du: cannot access ‘proc/15730/task/15730/fd/4’: No such file or directory
du: cannot access ‘proc/15730/task/15730/fdinfo/4’: No such file or directory
du: cannot access ‘proc/15730/fd/4’: No such file or directory
du: cannot access ‘proc/15730/fdinfo/4’: No such file or directory
0       dev
0	initrd.img
0	initrd.img.old
0	proc
0	sys
0	vmlinuz
0	vmlinuz.old
4	cdrom
4	lib64
4	mnt
4	srv
8	media
16	lost+found
52	root
3720	lib32
12836	bin
13756	sbin
15640	etc
19572	run
182956	opt
224218	boot
544036	tmp
975108	var
1159836	lib
4756104	usr
34601864	home




cd



```
[INDENT][INDENT]and the tale will be told
[/INDENT]
[/INDENT]



Thanx!

---

### Post by Bashing-om on 2015-07-10
stockpimp; Hey hey !

Yeah, the tale is told. As suspected, /boot partition is full from old kernels.
Problem 'may' now be that at 100%, capacity 'apt' may not have the operating head room to deal with removing these old kernels.
But, let's give it a whirl and see what results. 
```

sudo apt-get autoremove

```

Holding breath, as the possibility does exist, this may get dirty !

[INDENT][INDENT]the simple things first
[/INDENT][/INDENT]

---

### Post by stockpimp on 2015-07-10
> **Bashing-om said:**
> stockpimp; Hey hey !

Yeah, the tale is told. As suspected, /boot partition is full from old kernels.
Problem 'may' now be that at 100%, capacity 'apt' may not have the operating head room to deal with removing these old kernels.
But, let's give it a whirl and see what results. 
```

sudo apt-get autoremove

```

Holding breath, as the possibility does exist, this may get dirty ![INDENT][INDENT]the simple things first
[/INDENT]
[/INDENT]

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  alien at debugedit lib32z1 libc6-i386 librpmbuild3 librpmsign1
  linux-headers-3.19.0-15 linux-headers-3.19.0-15-generic
  linux-image-3.19.0-15-generic linux-image-extra-3.19.0-15-generic lsb-core
  lsb-security m4 ncurses-term pax rpm
0 upgraded, 0 newly installed, 17 to remove and 46 not upgraded.
3 not fully installed or removed.
After this operation, 303 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 313969 files and directories currently installed.)
Removing lsb-core (4.1+Debian11ubuntu8) ...
Removing alien (8.93) ...
Removing at (3.1.16-1ubuntu1) ...
Removing rpm (4.11.3-1.1) ...
Removing debugedit (4.11.3-1.1) ...
Removing lib32z1 (1:1.2.8.dfsg-2ubuntu1) ...
Removing libc6-i386 (2.21-0ubuntu4) ...
Removing librpmbuild3 (4.11.3-1.1) ...
Removing librpmsign1 (4.11.3-1.1) ...
Removing linux-headers-3.19.0-15-generic (3.19.0-15.15) ...
Removing linux-headers-3.19.0-15 (3.19.0-15.15) ...
Removing linux-image-extra-3.19.0-15-generic (3.19.0-15.15) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-15-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found linux image: /boot/vmlinuz-3.19.0-15-generic
Found initrd image: /boot/initrd.img-3.19.0-15-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Removing linux-image-3.19.0-15-generic (3.19.0-15.15) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-15-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Removing lsb-security (4.1+Debian11ubuntu8) ...
Removing m4 (1.4.17-4) ...
Removing ncurses-term (5.9+20140712-2ubuntu2) ...
Removing pax (1:20140703-2) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Processing triggers for install-info (5.2.0.dfsg.1-6) ...
Setting up linux-image-extra-3.19.0-21-generic (3.19.0-21.21) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-generic (3.19.0.21.20) ...
Setting up linux-generic (3.19.0.21.20) ...
```

---

### Post by Bashing-om on 2015-07-10
stockpimp; Well !

Surprise, surprise. looks like 'autoremove' was able to run.

A bit of concern about the state of that foreign software. but ....

Let's see what we look like:
```

df -h

```
If there is now space in /boot (/dev/sda1 );
reboot.
What now results:
```

sudo apt update
sudo apt full-upgrade

```

In the event that a new kernel is installed. Reboot once more, and let's see what now you are running for a kernel :
```

uname -r

```

[INDENT][INDENT]could be
[INDENT][INDENT][INDENT]smelling like a rose
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by stockpimp on 2015-07-12
> **Bashing-om said:**
> stockpimp; Well !

Surprise, surprise. looks like 'autoremove' was able to run.

A bit of concern about the state of that foreign software. but ....

Let's see what we look like:
```

df -h

```
If there is now space in /boot (/dev/sda1 );
reboot.
What now results:
```

sudo apt update
sudo apt full-upgrade

```

In the event that a new kernel is installed. Reboot once more, and let's see what now you are running for a kernel :
```

uname -r

```
[INDENT][INDENT]could be[INDENT][INDENT][INDENT]smelling like a rose
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]



Looks like 3.19.0-21-generic

---

### Post by Bashing-om on 2015-07-12
stockpimp; Yeah;

Looks good:
> 
Looks like 3.19.0-21-generic

I think is the latest version available.
What now does /boot look like ?
```

ls -al /boot

```

Could be
[INDENT][INDENT][INDENT]the fat lady is singing
[/INDENT][/INDENT][/INDENT]

---

### Post by stockpimp on 2015-07-12
> **Bashing-om said:**
> stockpimp; Yeah;

Looks good:

I think is the latest version available.
What now does /boot look like ?
```

ls -al /boot

```

Could be[INDENT][INDENT][INDENT]the fat lady is singing
[/INDENT]
[/INDENT]
[/INDENT]


total 217386
drwxr-xr-x  4 root root     3072 Jul 12 15:27 .
drwxr-xr-x 23 root root     4096 Jul 12 15:26 ..
-rw-r--r--  1 root root  1268815 Apr 30 10:23 abi-3.19.0-16-generic
-rw-r--r--  1 root root  1269284 May 19 12:45 abi-3.19.0-18-generic
-rw-r--r--  1 root root  1269462 May 29 04:02 abi-3.19.0-20-generic
-rw-r--r--  1 root root  1269462 Jun 14 12:44 abi-3.19.0-21-generic
-rw-r--r--  1 root root  1269462 Jun 16 11:30 abi-3.19.0-22-generic
-rw-r--r--  1 root root   177656 Apr 30 10:23 config-3.19.0-16-generic
-rw-r--r--  1 root root   177700 May 19 12:45 config-3.19.0-18-generic
-rw-r--r--  1 root root   177700 May 29 04:02 config-3.19.0-20-generic
-rw-r--r--  1 root root   177700 Jun 14 12:44 config-3.19.0-21-generic
-rw-r--r--  1 root root   177705 Jun 16 11:30 config-3.19.0-22-generic
drwxr-xr-x  5 root root     1024 Jul 12 15:27 grub
-rw-r--r--  1 root root 32556395 May 29 19:18 initrd.img-3.19.0-16-generic
-rw-r--r--  1 root root 32552703 Jun 11 08:08 initrd.img-3.19.0-18-generic
-rw-r--r--  1 root root 32556449 Jun 11 08:10 initrd.img-3.19.0-20-generic
-rw-r--r--  1 root root 32554989 Jul 10 11:43 initrd.img-3.19.0-21-generic
-rw-r--r--  1 root root 32557838 Jul 12 15:27 initrd.img-3.19.0-22-generic
drwx------  2 root root    12288 May 10 12:41 lost+found
-rw-r--r--  1 root root   164216 Mar  6 08:23 memtest86+.bin
-rw-r--r--  1 root root   165892 Mar  6 08:23 memtest86+.elf
-rw-r--r--  1 root root   166396 Mar  6 08:23 memtest86+_multiboot.bin
-rw-------  1 root root  3615358 Apr 30 10:23 System.map-3.19.0-16-generic
-rw-------  1 root root  3616263 May 19 12:45 System.map-3.19.0-18-generic
-rw-------  1 root root  3617303 May 29 04:02 System.map-3.19.0-20-generic
-rw-------  1 root root  3617303 Jun 14 12:44 System.map-3.19.0-21-generic
-rw-------  1 root root  3617446 Jun 16 11:30 System.map-3.19.0-22-generic
-rw-------  1 root root  6611904 Apr 30 10:23 vmlinuz-3.19.0-16-generic
-rw-------  1 root root  6614144 May 19 12:45 vmlinuz-3.19.0-18-generic
-rw-------  1 root root  6616960 May 29 04:02 vmlinuz-3.19.0-20-generic
-rw-------  1 root root  6617408 Jun 14 12:44 vmlinuz-3.19.0-21-generic
-rw-------  1 root root  6616448 Jun 16 11:30 vmlinuz-3.19.0-22-generic

---

### Post by Bashing-om on 2015-07-12
stockpimp; UnGood !

OK, let's sic 'dpkg' on it and remove those old kernels .
Show now:
```

uname -r
dpkg -l | grep linux-

``` and I will craft us up a handy dandy removal procedure.

[INDENT][INDENT]if at 1st you do not succeed
[INDENT][INDENT][INDENT]do something else
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by stockpimp on 2015-07-12
ii  linux-firmware                                       1.143.1                                    all          Firmware for Linux kernel drivers
iU  linux-generic                                        3.19.0.22.21                               amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.19.0-16                              3.19.0-16.16                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-16-generic                      3.19.0-16.16                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-18                              3.19.0-18.18                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-18-generic                      3.19.0-18.18                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-20                              3.19.0-20.20                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-20-generic                      3.19.0-20.20                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-21                              3.19.0-21.21                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-21-generic                      3.19.0-21.21                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-22                              3.19.0-22.22                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-22-generic                      3.19.0-22.22                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic                                3.19.0.22.21                               amd64        Generic Linux kernel headers
rc  linux-image-3.19.0-15-generic                        3.19.0-15.15                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-16-generic                        3.19.0-16.16                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-18-generic                        3.19.0-18.18                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-20-generic                        3.19.0-20.20                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-21-generic                        3.19.0-21.21                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-22-generic                        3.19.0-22.22                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-15-generic                  3.19.0-15.15                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-16-generic                  3.19.0-16.16                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-18-generic                  3.19.0-18.18                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-20-generic                  3.19.0-20.20                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-21-generic                  3.19.0-21.21                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
iF  linux-image-extra-3.19.0-22-generic                  3.19.0-22.22                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
iU  linux-image-generic                                  3.19.0.22.21                               amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                 3.19.0-22.22                               amd64        Linux Kernel Headers for development
ii  linux-sound-base                                     1.0.25+dfsg-0ubuntu4                       all          base package for ALSA and OSS sound systems
ii  syslinux-common                                      3:6.03+dfsg-5ubuntu1                       all          collection of bootloaders (common)
ii  syslinux-legacy                                      2:3.63+dfsg-2ubuntu6                       amd64        Bootloader for Linux/i386 using MS-DOS floppies

---

### Post by Bashing-om on 2015-07-12
stockpimp; Well,

We have a bit of a problem ( the iU/iF status) with the -21 and 22 kernels.

Let's try this to remove them :
```

sudo apt-get remove --purge linux-generic-3.19.0-21
sudo apt-get remove --purge linux-image-3.19.0-21-generic
sudo apt-get remove --purge linux-headers-3.19.0-21-generic
sudo apt-get remove --purge linux-headers-3.19.0-21
sudo apt-get remove --purge linux-image-extra-3.19.0-21-generic

```
If that goes well, we do the same for the -22 kernel.

And if that too goes well we then sic 'dpkg' on those that remain.

[INDENT][INDENT]sounds like a plan to me
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-07-13
Please use code tags for terminal output. See the last link in my signature.

I am also running 14.04 LTS and the latest kernel is 3.13.0-55 or, if you have installed recently, it is the 3.16.0-45. Unsure where the 3.19 has come from.

Sure this is not a 15.04 install and not the LTS?

---

### Post by stockpimp on 2015-07-13
> **Bashing-om said:**
> stockpimp; Well,

We have a bit of a problem ( the iU/iF status) with the -21 and 22 kernels.

Let's try this to remove them :
```

sudo apt-get remove --purge linux-generic-3.19.0-21

[code}
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-generic-3.19.0-21
E: Couldn't find any package by regex 'linux-generic-3.19.0-21'

```


sudo apt-get remove --purge linux-image-3.19.0-21-generic

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.19.0-21-generic* linux-image-extra-3.19.0-21-generic*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 208 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 310721 files and directories currently installed.)
Removing linux-image-extra-3.19.0-21-generic (3.19.0-21.21) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.19.0-21-generic (3.19.0-21.21) ...
Removing linux-image-3.19.0-21-generic (3.19.0-21.21) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-3.19.0-21-generic (3.19.0-21.21) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
Setting up linux-image-extra-3.19.0-22-generic (3.19.0-22.22) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-generic (3.19.0.22.21) ...
Setting up linux-generic (3.19.0.22.21) ...

```



sudo apt-get remove --purge linux-headers-3.19.0-21-generic

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.19.0-21-generic*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 14.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 305498 files and directories currently installed.)
Removing linux-headers-3.19.0-21-generic (3.19.0-21.21) ...

```


sudo apt-get remove --purge linux-headers-3.19.0-21


```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.19.0-21*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 66.0 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 296362 files and directories currently installed.)
Removing linux-headers-3.19.0-21 (3.19.0-21.21) ...

```



sudo apt-get remove --purge linux-image-extra-3.19.0-21-generic

[code}
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'linux-image-extra-3.19.0-21-generic' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/code]

[/code]
If that goes well, we do the same for the -22 kernel.

And if that too goes well we then sic 'dpkg' on those that remain.
[INDENT][INDENT]sounds like a plan to me
[/INDENT]
[/INDENT]



Hope I did that right.

---

### Post by Bashing-om on 2015-07-13
stockpimp; Yepper;

Looks good to me.

Rinse off ( I was in a bit of a sweat) and repeat this procedure 
substituting 22 for 21 on each command.
As advised on the outputs - , do not reboot until we are done here and we manually update grub and confirm the symlinks are present.
If -22 goes well will next craft up the 'dpkg' commands to cope with the remainder .

[INDENT][INDENT]small steps, but getting there 
[/INDENT][/INDENT]

---

### Post by stockpimp on 2015-07-13
> **Bashing-om said:**
> stockpimp; Yepper;

Looks good to me.

Rinse off ( I was in a bit of a sweat) and repeat this procedure 
substituting 22 for 21 on each command.
As advised on the outputs - , do not reboot until we are done here and we manually update grub and confirm the symlinks are present.
If -22 goes well will next craft up the 'dpkg' commands to cope with the remainder .
[INDENT][INDENT]small steps, but getting there 
[/INDENT]
[/INDENT]

```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-generic-3.19.0-22
E: Couldn't find any package by regex 'linux-generic-3.19.0-22'
dj@Blackbox:~$ sudo apt-get remove --purge linux-image-3.19.0-22-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-generic thermald
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-generic* linux-image-3.19.0-22-generic*
  linux-image-extra-3.19.0-22-generic* linux-image-generic*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 209 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 280545 files and directories currently installed.)
Removing linux-generic (3.19.0.22.21) ...
Removing linux-image-generic (3.19.0.22.21) ...
Removing linux-image-extra-3.19.0-22-generic (3.19.0-22.22) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.19.0-22-generic (3.19.0-22.22) ...
Removing linux-image-3.19.0-22-generic (3.19.0-22.22) ...
WARN: Proceeding with removing running kernel image.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-3.19.0-22-generic (3.19.0-22.22) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
dj@Blackbox:~$ sudo apt-get remove --purge linux-headers-3.19.0-22-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-22 thermald
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-headers-3.19.0-22-generic* linux-headers-generic*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 14.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 275316 files and directories currently installed.)
Removing linux-headers-generic (3.19.0.22.21) ...
Removing linux-headers-3.19.0-22-generic (3.19.0-22.22) ...
dj@Blackbox:~$ sudo apt-get remove --purge linux-headers-3.19.0-22
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  thermald
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  linux-headers-3.19.0-22*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 66.0 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 266177 files and directories currently installed.)
Removing linux-headers-3.19.0-22 (3.19.0-22.22) ...
dj@Blackbox:~$ sudo apt-get remove --purge linux-image-extra-3.19.0-22-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'linux-image-extra-3.19.0-22-generic' is not installed, so not removed
The following package was automatically installed and is no longer required:
  thermald
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



```

---

### Post by Bucky Ball on 2015-07-14
And one more time, just to check you get no errors and everything looks normal and proceeds as expected. :)

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

---

### Post by stockpimp on 2015-07-14
> **Bucky Ball said:**
> And one more time, just to check you get no errors and everything looks normal and proceeds as expected. :)

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  thermald
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 643 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 250360 files and directories currently installed.)
Removing thermald (1.3-9) ...
Processing triggers for dbus (1.8.12-1ubuntu5) ...
Processing triggers for man-db (2.7.0.2-5) ...
dj@Blackbox:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Ign http://security.ubuntu.com vivid-security InRelease                        
Ign http://download.ebz.epson.net lsb3.2 InRelease                             
Get:1 http://security.ubuntu.com vivid-security Release.gpg [933 B]            
Hit http://dl.google.com stable/main amd64 Packages                            
Ign http://ppa.launchpad.net vivid InRelease                                   
Ign http://ca.archive.ubuntu.com vivid InRelease                               
Ign http://archive.canonical.com vivid InRelease                               
Hit http://dl.google.com stable/main i386 Packages                             
Get:2 http://security.ubuntu.com vivid-security Release [63.5 kB]              
Hit http://download.ebz.epson.net lsb3.2 Release.gpg                           
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Ign http://ca.archive.ubuntu.com vivid-updates InRelease                       
Ign http://download.jitsi.org unstable/ InRelease                              
Hit http://archive.canonical.com vivid Release.gpg                             
Hit http://download.ebz.epson.net lsb3.2 Release                               
Hit http://ppa.launchpad.net vivid Release                                     
Ign http://ca.archive.ubuntu.com vivid-backports InRelease                     
Hit http://archive.canonical.com vivid Release                                 
Hit http://download.jitsi.org unstable/ Release.gpg                            
Ign http://dl.google.com stable/main Translation-en_CA                         
Get:3 http://security.ubuntu.com vivid-security/main Sources [26.4 kB]         
Hit http://download.ebz.epson.net lsb3.2/main amd64 Packages                   
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ca.archive.ubuntu.com vivid Release.gpg                             
Hit http://ppa.launchpad.net vivid/main Sources                                
Get:4 http://security.ubuntu.com vivid-security/restricted Sources [28 B]      
Hit http://archive.canonical.com vivid/partner Sources                         
Hit http://download.jitsi.org unstable/ Release                                
Hit http://download.ebz.epson.net lsb3.2/main i386 Packages                    
Get:5 http://security.ubuntu.com vivid-security/universe Sources [12.9 kB]     
Get:6 http://ca.archive.ubuntu.com vivid-updates Release.gpg [933 B]           
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://download.ebz.epson.net lsb3.2/main Translation-en_CA                
Hit http://archive.canonical.com vivid/partner amd64 Packages                  
Get:7 http://security.ubuntu.com vivid-security/multiverse Sources [1,955 B]   
Hit http://download.jitsi.org unstable/ Packages                               
Get:8 http://ca.archive.ubuntu.com vivid-backports Release.gpg [933 B]         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://download.ebz.epson.net lsb3.2/main Translation-en                   
Get:9 http://security.ubuntu.com vivid-security/main amd64 Packages [80.6 kB]  
Hit http://archive.canonical.com vivid/partner i386 Packages                   
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ca.archive.ubuntu.com vivid Release                                 
Hit http://archive.canonical.com vivid/partner Translation-en                  
Get:10 http://security.ubuntu.com vivid-security/restricted amd64 Packages [28 B]
Get:11 http://security.ubuntu.com vivid-security/universe amd64 Packages [40.9 kB]
Get:12 http://ca.archive.ubuntu.com vivid-updates Release [63.5 kB]            
Get:13 http://security.ubuntu.com vivid-security/multiverse amd64 Packages [3,492 B]
Get:14 http://security.ubuntu.com vivid-security/main i386 Packages [79.9 kB]  
Get:15 http://security.ubuntu.com vivid-security/restricted i386 Packages [28 B]
Get:16 http://security.ubuntu.com vivid-security/universe i386 Packages [40.9 kB]
Get:17 http://ca.archive.ubuntu.com vivid-backports Release [63.5 kB]          
Get:18 http://security.ubuntu.com vivid-security/multiverse i386 Packages [3,673 B]
Hit http://security.ubuntu.com vivid-security/main Translation-en              
Hit http://security.ubuntu.com vivid-security/multiverse Translation-en        
Hit http://ca.archive.ubuntu.com vivid/main Sources                            
Hit http://security.ubuntu.com vivid-security/restricted Translation-en        
Hit http://ca.archive.ubuntu.com vivid/restricted Sources                      
Get:19 http://security.ubuntu.com vivid-security/universe Translation-en [26.3 kB]
Hit http://ca.archive.ubuntu.com vivid/universe Sources                        
Ign http://download.jitsi.org unstable/ Translation-en_CA     
Hit http://ca.archive.ubuntu.com vivid/multiverse Sources     
Hit http://ca.archive.ubuntu.com vivid/main amd64 Packages
Ign http://download.jitsi.org unstable/ Translation-en
Hit http://ca.archive.ubuntu.com vivid/restricted amd64 Packages
Hit http://ca.archive.ubuntu.com vivid/universe amd64 Packages
Hit http://ca.archive.ubuntu.com vivid/multiverse amd64 Packages
Hit http://ca.archive.ubuntu.com vivid/main i386 Packages
Hit http://ca.archive.ubuntu.com vivid/restricted i386 Packages
Hit http://ca.archive.ubuntu.com vivid/universe i386 Packages
Hit http://ca.archive.ubuntu.com vivid/multiverse i386 Packages
Hit http://ca.archive.ubuntu.com vivid/main Translation-en_CA
Hit http://ca.archive.ubuntu.com vivid/main Translation-en
Hit http://ca.archive.ubuntu.com vivid/multiverse Translation-en
Hit http://ca.archive.ubuntu.com vivid/restricted Translation-en
Hit http://ca.archive.ubuntu.com vivid/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com vivid/universe Translation-en
Get:20 http://ca.archive.ubuntu.com vivid-updates/main Sources [59.1 kB]       
Get:21 http://ca.archive.ubuntu.com vivid-updates/restricted Sources [28 B]    
Get:22 http://ca.archive.ubuntu.com vivid-updates/universe Sources [27.3 kB]   
Get:23 http://ca.archive.ubuntu.com vivid-updates/multiverse Sources [1,955 B] 
Get:24 http://ca.archive.ubuntu.com vivid-updates/main amd64 Packages [138 kB] 
Get:25 http://ca.archive.ubuntu.com vivid-updates/restricted amd64 Packages [28 B]
Get:26 http://ca.archive.ubuntu.com vivid-updates/universe amd64 Packages [79.0 kB]
Get:27 http://ca.archive.ubuntu.com vivid-updates/multiverse amd64 Packages [3,492 B]
Get:28 http://ca.archive.ubuntu.com vivid-updates/main i386 Packages [135 kB]  
Get:29 http://ca.archive.ubuntu.com vivid-updates/restricted i386 Packages [28 B]
Get:30 http://ca.archive.ubuntu.com vivid-updates/universe i386 Packages [78.9 kB]
Get:31 http://ca.archive.ubuntu.com vivid-updates/multiverse i386 Packages [3,673 B]
Hit http://ca.archive.ubuntu.com vivid-updates/main Translation-en             
Hit http://ca.archive.ubuntu.com vivid-updates/multiverse Translation-en       
Hit http://ca.archive.ubuntu.com vivid-updates/restricted Translation-en       
Get:32 http://ca.archive.ubuntu.com vivid-updates/universe Translation-en [45.2 kB]
Get:33 http://ca.archive.ubuntu.com vivid-backports/main Sources [28 B]        
Get:34 http://ca.archive.ubuntu.com vivid-backports/restricted Sources [28 B]  
Get:35 http://ca.archive.ubuntu.com vivid-backports/universe Sources [5,268 B] 
Get:36 http://ca.archive.ubuntu.com vivid-backports/multiverse Sources [28 B]  
Get:37 http://ca.archive.ubuntu.com vivid-backports/main amd64 Packages [28 B] 
Get:38 http://ca.archive.ubuntu.com vivid-backports/restricted amd64 Packages [28 B]
Get:39 http://ca.archive.ubuntu.com vivid-backports/universe amd64 Packages [4,022 B]
Get:40 http://ca.archive.ubuntu.com vivid-backports/multiverse amd64 Packages [28 B]
Get:41 http://ca.archive.ubuntu.com vivid-backports/main i386 Packages [28 B]  
Get:42 http://ca.archive.ubuntu.com vivid-backports/restricted i386 Packages [28 B]
Get:43 http://ca.archive.ubuntu.com vivid-backports/universe i386 Packages [4,021 B]
Get:44 http://ca.archive.ubuntu.com vivid-backports/multiverse i386 Packages [28 B]
Hit http://ca.archive.ubuntu.com vivid-backports/main Translation-en           
Hit http://ca.archive.ubuntu.com vivid-backports/multiverse Translation-en     
Hit http://ca.archive.ubuntu.com vivid-backports/restricted Translation-en     
Hit http://ca.archive.ubuntu.com vivid-backports/universe Translation-en       
Fetched 1,096 kB in 13s (80.4 kB/s)                                            
Reading package lists... Done
dj@Blackbox:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  mariadb-client mariadb-client-10.0 mariadb-client-core-10.0 mariadb-common
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,998 kB of archives.
After this operation, 15.4 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ vivid-updates/universe mariadb-common all 10.0.20-0ubuntu0.15.04.1 [18.3 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ vivid-updates/universe mariadb-client-core-10.0 amd64 10.0.20-0ubuntu0.15.04.1 [804 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ vivid-updates/universe mariadb-client-10.0 amd64 10.0.20-0ubuntu0.15.04.1 [1,162 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ vivid-updates/universe mariadb-client all 10.0.20-0ubuntu0.15.04.1 [13.4 kB]
Fetched 1,998 kB in 4s (491 kB/s)        
(Reading database ... 250353 files and directories currently installed.)
Preparing to unpack .../mariadb-common_10.0.20-0ubuntu0.15.04.1_all.deb ...
Unpacking mariadb-common (10.0.20-0ubuntu0.15.04.1) over (10.0.17-0ubuntu1) ...
Preparing to unpack .../mariadb-client-core-10.0_10.0.20-0ubuntu0.15.04.1_amd64.deb ...
Unpacking mariadb-client-core-10.0 (10.0.20-0ubuntu0.15.04.1) over (10.0.17-0ubuntu1) ...
Preparing to unpack .../mariadb-client-10.0_10.0.20-0ubuntu0.15.04.1_amd64.deb ...
Unpacking mariadb-client-10.0 (10.0.20-0ubuntu0.15.04.1) over (10.0.17-0ubuntu1) ...
Preparing to unpack .../mariadb-client_10.0.20-0ubuntu0.15.04.1_all.deb ...
Unpacking mariadb-client (10.0.20-0ubuntu0.15.04.1) over (10.0.17-0ubuntu1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Setting up mariadb-common (10.0.20-0ubuntu0.15.04.1) ...
Setting up mariadb-client-core-10.0 (10.0.20-0ubuntu0.15.04.1) ...
Setting up mariadb-client-10.0 (10.0.20-0ubuntu0.15.04.1) ...
Setting up mariadb-client (10.0.20-0ubuntu0.15.04.1) ...
dj@Blackbox:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

---

### Post by Bashing-om on 2015-07-14
stockpimp; Uh OH !

I have grave concerns at this time.
You were booting the -51 kernel, and that last showed a warning :
> 
WARN: Proceeding with removing running kernel image.

in removing the -22 kernel. What did you do ?

Let's at this time see what is, from the ground up, prior to proceeding.
```

ls -al /
ls -al /boot
dpkg -l | grep linux-

```
Maybe the update/upgrade fixed the issue ??

As if you are set to boot the system with a non-existent kernel, well, going to be a pain to fix.

However, this is 'buntu
[INDENT][INDENT]it's all fixable
[/INDENT][/INDENT]

---

### Post by stockpimp on 2015-07-14
> **Bashing-om said:**
> stockpimp; Uh OH !

I have grave concerns at this time.
You were booting the -51 kernel, and that last showed a warning :

in removing the -22 kernel. What did you do ?

Let's at this time see what is, from the ground up, prior to proceeding.
```

ls -al /

total 103
drwxr-xr-x  23 root root  4096 Jul 13 19:02 .
drwxr-xr-x  23 root root  4096 Jul 13 19:02 ..
drwxr-xr-x   2 root root  4096 Jul 10 11:43 bin
drwxr-xr-x   4 root root  3072 Jul 13 19:02 boot
drwxrwxr-x   2 root root  4096 May 10 12:48 cdrom
drwxr-xr-x  20 root root  4500 Jul 14 06:52 dev
drwxr-xr-x 149 root root 12288 Jul 12 15:28 etc
drwxr-xr-x   3 root root  4096 May 10 12:49 home
drwxr-xr-x  26 root root  4096 Jul 10 11:42 lib
drwxr-xr-x   2 root root  4096 Jul 10 11:42 lib64
drwx------   2 root root 16384 May 10 12:42 lost+found
drwxr-xr-x   3 root root  4096 May 20 13:51 media
drwxr-xr-x   2 root root  4096 Apr 17 14:34 mnt
drwxr-xr-x   3 root root  4096 May 10 18:27 opt
dr-xr-xr-x 322 root root     0 Jul 12 19:14 proc
drwx------   6 root root  4096 Jul 10 08:58 root
drwxr-xr-x  29 root root   920 Jul 13 14:42 run
drwxr-xr-x   2 root root 12288 Jun 29 08:03 sbin
drwxr-xr-x   2 root root  4096 Apr 22 05:01 srv
dr-xr-xr-x  13 root root     0 Jul 12 19:14 sys
drwxrwxrwt  16 root root  4096 Jul 14 19:17 tmp
drwxr-xr-x  10 root root  4096 Jul 10 11:42 usr
drwxr-xr-x  14 root root  4096 May 10 18:35 var



ls -al /boot

total 130630
drwxr-xr-x  4 root root     3072 Jul 13 19:02 .
drwxr-xr-x 23 root root     4096 Jul 13 19:02 ..
-rw-r--r--  1 root root  1268815 Apr 30 10:23 abi-3.19.0-16-generic
-rw-r--r--  1 root root  1269284 May 19 12:45 abi-3.19.0-18-generic
-rw-r--r--  1 root root  1269462 May 29 04:02 abi-3.19.0-20-generic
-rw-r--r--  1 root root   177656 Apr 30 10:23 config-3.19.0-16-generic
-rw-r--r--  1 root root   177700 May 19 12:45 config-3.19.0-18-generic
-rw-r--r--  1 root root   177700 May 29 04:02 config-3.19.0-20-generic
drwxr-xr-x  5 root root     1024 Jul 13 19:02 grub
-rw-r--r--  1 root root 32556395 May 29 19:18 initrd.img-3.19.0-16-generic
-rw-r--r--  1 root root 32552703 Jun 11 08:08 initrd.img-3.19.0-18-generic
-rw-r--r--  1 root root 32556449 Jun 11 08:10 initrd.img-3.19.0-20-generic
drwx------  2 root root    12288 May 10 12:41 lost+found
-rw-r--r--  1 root root   164216 Mar  6 08:23 memtest86+.bin
-rw-r--r--  1 root root   165892 Mar  6 08:23 memtest86+.elf
-rw-r--r--  1 root root   166396 Mar  6 08:23 memtest86+_multiboot.bin
-rw-------  1 root root  3615358 Apr 30 10:23 System.map-3.19.0-16-generic
-rw-------  1 root root  3616263 May 19 12:45 System.map-3.19.0-18-generic
-rw-------  1 root root  3617303 May 29 04:02 System.map-3.19.0-20-generic
-rw-------  1 root root  6611904 Apr 30 10:23 vmlinuz-3.19.0-16-generic
-rw-------  1 root root  6614144 May 19 12:45 vmlinuz-3.19.0-18-generic
-rw-------  1 root root  6616960 May 29 04:02 vmlinuz-3.19.0-20-generic



dpkg -l | grep linux-

ii  linux-firmware                                       1.143.1                                    all          Firmware for Linux kernel drivers
ii  linux-headers-3.19.0-16                              3.19.0-16.16                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-16-generic                      3.19.0-16.16                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-18                              3.19.0-18.18                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-18-generic                      3.19.0-18.18                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-20                              3.19.0-20.20                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-20-generic                      3.19.0-20.20                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-15-generic                        3.19.0-15.15                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-16-generic                        3.19.0-16.16                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-18-generic                        3.19.0-18.18                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-20-generic                        3.19.0-20.20                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-15-generic                  3.19.0-15.15                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-16-generic                  3.19.0-16.16                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-18-generic                  3.19.0-18.18                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-20-generic                  3.19.0-20.20                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                                 3.19.0-22.22                               amd64        Linux Kernel Headers for development
ii  linux-sound-base                                     1.0.25+dfsg-0ubuntu4                       all          base package for ALSA and OSS sound systems
ii  syslinux-common                                      3:6.03+dfsg-5ubuntu1                       all          collection of bootloaders (common)
ii  syslinux-legacy                                      2:3.63+dfsg-2ubuntu6                       amd64        Bootloader for Linux/i386 using MS-DOS floppies




```
Maybe the update/upgrade fixed the issue ??

As if you are set to boot the system with a non-existent kernel, well, going to be a pain to fix.

However, this is 'buntu[INDENT][INDENT]it's all fixable
[/INDENT]
[/INDENT]



Cheers...  Hope I didn't mess some thing up?

---

### Post by Bashing-om on 2015-07-14
stockpimp; Nope !

To be truthful ... that is all my fault ( after looking at the kernel image that "should" be installed. I guess I got my wires crossed somewhere as my notes do show -51 as booting .. But that is a falsity !

Let's try and fix it:
```

sudo apt-get install --reinstall linux-headers-3.19.0-22
sudo apt-get install --reinstall linux-headers-3.19.0-22-generic
sudo apt-get install --reinstall linux-image-3.19.0-22-generic
sudo apt-get install --reinstall linux-image-extra-3.19.0-22-generic

```

See if grub has picked up the new kernel :
```

sudo update-grub

```

Now what do we have for '/' for a booting kernel ?
show :
```

ls -al /

```

We do want to see something similar:
> 
lrwxrwxrwx   1 root root    30 Jul  6 13:58 vmlinuz -> boot/vmlinuz-3.19.0-22-generic


I do apologize 
[INDENT][INDENT]I sure messed this up
[/INDENT][/INDENT]

---

### Post by stockpimp on 2015-07-15
> **Bashing-om said:**
> stockpimp; Nope !

To be truthful ... that is all my fault ( after looking at the kernel image that "should" be installed. I guess I got my wires crossed somewhere as my notes do show -51 as booting .. But that is a falsity !

Let's try and fix it:
```

sudo apt-get install --reinstall linux-headers-3.19.0-22
sudo apt-get install --reinstall linux-headers-3.19.0-22-generic
sudo apt-get install --reinstall linux-image-3.19.0-22-generic
sudo apt-get install --reinstall linux-image-extra-3.19.0-22-generic

```

See if grub has picked up the new kernel :
```

sudo update-grub


Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done




```

Now what do we have for '/' for a booting kernel ?
show :
```

ls -al /

total 103
drwxr-xr-x  23 root root  4096 Jul 15 08:25 .
drwxr-xr-x  23 root root  4096 Jul 15 08:25 ..
drwxr-xr-x   2 root root  4096 Jul 10 11:43 bin
drwxr-xr-x   4 root root  3072 Jul 15 08:26 boot
drwxrwxr-x   2 root root  4096 May 10 12:48 cdrom
drwxr-xr-x  20 root root  4500 Jul 14 06:52 dev
drwxr-xr-x 149 root root 12288 Jul 15 08:22 etc
drwxr-xr-x   3 root root  4096 May 10 12:49 home
lrwxrwxrwx   1 root root    33 Jul 15 08:25 initrd.img -> boot/initrd.img-3.19.0-22-generic
drwxr-xr-x  26 root root  4096 Jul 10 11:42 lib
drwxr-xr-x   2 root root  4096 Jul 10 11:42 lib64
drwx------   2 root root 16384 May 10 12:42 lost+found
drwxr-xr-x   3 root root  4096 May 20 13:51 media
drwxr-xr-x   2 root root  4096 Apr 17 14:34 mnt
drwxr-xr-x   3 root root  4096 May 10 18:27 opt
dr-xr-xr-x 328 root root     0 Jul 12 19:14 proc
drwx------   6 root root  4096 Jul 10 08:58 root
drwxr-xr-x  29 root root   920 Jul 13 14:42 run
drwxr-xr-x   2 root root 12288 Jun 29 08:03 sbin
drwxr-xr-x   2 root root  4096 Apr 22 05:01 srv
dr-xr-xr-x  13 root root     0 Jul 14 19:20 sys
drwxrwxrwt  16 root root  4096 Jul 15 08:27 tmp
drwxr-xr-x  10 root root  4096 Jul 10 11:42 usr
drwxr-xr-x  14 root root  4096 May 10 18:35 var
lrwxrwxrwx   1 root root    30 Jul 15 08:25 vmlinuz -> boot/vmlinuz-3.19.0-22-generic




```

We do want to see something similar:


I do apologize [INDENT][INDENT]I sure messed this up
[/INDENT]
[/INDENT]



Cheers.... it;s a journey not a destination lol.

---

### Post by Bashing-om on 2015-07-15
stockpimp; Wow ;

Look'n good - I did have some concern, and I did loose sleep over this !

So OK, we have our booting kernel back, and now it is fully installed whereas formerly we had a "iU" status.

Now we can proceed to remove those old kernels, and then we install a backup kernel;

The removal:
```

sudo dpkg -P linux-image-extra-3.19.0-{16,18}-generic
sudo dpkg -P linux-image-3.19.0-{16,18}-generic
sudo dpkg -P linux-headers-3.19.0-{16,18}-generic
sudo dpkg -P linux-headers-3.19.0-{16,18}

```

When these complete and we have the known operating head room; install the backup kernel:
```

sudo apt-get install --reinstall linux-headers-3.19.0-21
sudo apt-get install --reinstall linux-headers-3.19.0-21-generic
sudo apt-get install --reinstall linux-image-3.19.0-21-generic
sudo apt-get install --reinstall linux-image-extra-3.19.0-21-generic

```
At this point we should be setting pretty,
See now about grub picking up and making the symlink for the backup kernel:
```

sudo update-grub

```

To know that all is now good :
```

ls -al /

```

When that comes back, and all is good ->
[INDENT][INDENT][INDENT]I can cease sweat condition 3
[/INDENT][/INDENT][/INDENT]

---

### Post by stockpimp on 2015-07-17
> **Bashing-om said:**
> stockpimp; Wow ;

Look'n good - I did have some concern, and I did loose sleep over this !

So OK, we have our booting kernel back, and now it is fully installed whereas formerly we had a "iU" status.

Now we can proceed to remove those old kernels, and then we install a backup kernel;

The removal:
```

sudo dpkg -P linux-image-extra-3.19.0-{16,18}-generic
sudo dpkg -P linux-image-3.19.0-{16,18}-generic
sudo dpkg -P linux-headers-3.19.0-{16,18}-generic
sudo dpkg -P linux-headers-3.19.0-{16,18}

```

When these complete and we have the known operating head room; install the backup kernel:
```

sudo apt-get install --reinstall linux-headers-3.19.0-21
sudo apt-get install --reinstall linux-headers-3.19.0-21-generic
sudo apt-get install --reinstall linux-image-3.19.0-21-generic
sudo apt-get install --reinstall linux-image-extra-3.19.0-21-generic

```
At this point we should be setting pretty,
See now about grub picking up and making the symlink for the backup kernel:
```

sudo update-grub

```

To know that all is now good :
```

ls -al /

```

When that comes back, and all is good ->[INDENT][INDENT][INDENT]I can cease sweat condition 3
[/INDENT]
[/INDENT]
[/INDENT]



Here ya go.


```

(Reading database ... 280528 files and directories currently installed.)
Removing linux-image-extra-3.19.0-16-generic (3.19.0-16.16) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.19.0-16-generic (3.19.0-16.16) ...
Removing linux-image-extra-3.19.0-18-generic (3.19.0-18.18) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.19.0-18-generic (3.19.0-18.18) ...
dj@Blackbox:~$ sudo dpkg -P linux-image-3.19.0-{16,18}-generic
(Reading database ... 272062 files and directories currently installed.)
Removing linux-image-3.19.0-16-generic (3.19.0-16.16) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-16-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.19.0-16-generic (3.19.0-16.16) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
Removing linux-image-3.19.0-18-generic (3.19.0-18.18) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-18-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.19.0-18-generic (3.19.0-18.18) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
dj@Blackbox:~$ sudo dpkg -P linux-headers-3.19.0-{16,18}-generic
(Reading database ... 270082 files and directories currently installed.)
Removing linux-headers-3.19.0-16-generic (3.19.0-16.16) ...
Removing linux-headers-3.19.0-18-generic (3.19.0-18.18) ...
dj@Blackbox:~$ sudo dpkg -P linux-headers-3.19.0-{16,18}
(Reading database ... 251812 files and directories currently installed.)
Removing linux-headers-3.19.0-16 (3.19.0-16.16) ...
Removing linux-headers-3.19.0-18 (3.19.0-18.18) ...
dj@Blackbox:~$ sudo apt-get install --reinstall linux-headers-3.19.0-21
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-headers-3.19.0-21
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Need to get 0 B/9,331 kB of archives.
After this operation, 66.0 MB of additional disk space will be used.
Selecting previously unselected package linux-headers-3.19.0-21.
(Reading database ... 220182 files and directories currently installed.)
Preparing to unpack .../linux-headers-3.19.0-21_3.19.0-21.21_all.deb ...
Unpacking linux-headers-3.19.0-21 (3.19.0-21.21) ...
Setting up linux-headers-3.19.0-21 (3.19.0-21.21) ...
dj@Blackbox:~$ sudo apt-get install --reinstall linux-headers-3.19.0-21-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-headers-3.19.0-21-generic
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Need to get 0 B/754 kB of archives.
After this operation, 14.4 MB of additional disk space will be used.
Selecting previously unselected package linux-headers-3.19.0-21-generic.
(Reading database ... 235999 files and directories currently installed.)
Preparing to unpack .../linux-headers-3.19.0-21-generic_3.19.0-21.21_amd64.deb ...
Unpacking linux-headers-3.19.0-21-generic (3.19.0-21.21) ...
Setting up linux-headers-3.19.0-21-generic (3.19.0-21.21) ...
dj@Blackbox:~$ sudo apt-get install --reinstall linux-image-3.19.0-21-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  fdutils linux-doc-3.19.0 linux-source-3.19.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.19.0-21-generic
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Need to get 0 B/16.8 MB of archives.
After this operation, 47.8 MB of additional disk space will be used.
Selecting previously unselected package linux-image-3.19.0-21-generic.
(Reading database ... 245135 files and directories currently installed.)
Preparing to unpack .../linux-image-3.19.0-21-generic_3.19.0-21.21_amd64.deb ...
Done.
Unpacking linux-image-3.19.0-21-generic (3.19.0-21.21) ...
Setting up linux-image-3.19.0-21-generic (3.19.0-21.21) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
dj@Blackbox:~$ sudo apt-get install --reinstall linux-image-extra-3.19.0-21-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-image-extra-3.19.0-21-generic
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Need to get 0 B/38.4 MB of archives.
After this operation, 161 MB of additional disk space will be used.
Selecting previously unselected package linux-image-extra-3.19.0-21-generic.
(Reading database ... 246125 files and directories currently installed.)
Preparing to unpack .../linux-image-extra-3.19.0-21-generic_3.19.0-21.21_amd64.deb ...
Unpacking linux-image-extra-3.19.0-21-generic (3.19.0-21.21) ...
Setting up linux-image-extra-3.19.0-21-generic (3.19.0-21.21) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
dj@Blackbox:~$ sudo update-grub
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
dj@Blackbox:~$ ls -al /
total 103
drwxr-xr-x  23 root root  4096 Jul 17 08:09 .
drwxr-xr-x  23 root root  4096 Jul 17 08:09 ..
drwxr-xr-x   2 root root  4096 Jul 10 11:43 bin
drwxr-xr-x   4 root root  3072 Jul 17 08:10 boot
drwxrwxr-x   2 root root  4096 May 10 12:48 cdrom
drwxr-xr-x  20 root root  4440 Jul 15 15:22 dev
drwxr-xr-x 149 root root 12288 Jul 15 08:22 etc
drwxr-xr-x   3 root root  4096 May 10 12:49 home
lrwxrwxrwx   1 root root    33 Jul 17 08:09 initrd.img -> boot/initrd.img-3.19.0-21-generic
lrwxrwxrwx   1 root root    33 Jul 15 08:25 initrd.img.old -> boot/initrd.img-3.19.0-22-generic
drwxr-xr-x  26 root root  4096 Jul 10 11:42 lib
drwxr-xr-x   2 root root  4096 Jul 10 11:42 lib64
drwx------   2 root root 16384 May 10 12:42 lost+found
drwxr-xr-x   3 root root  4096 May 20 13:51 media
drwxr-xr-x   2 root root  4096 Apr 17 14:34 mnt
drwxr-xr-x   3 root root  4096 May 10 18:27 opt
dr-xr-xr-x 330 root root     0 Jul 12 19:14 proc
drwx------   6 root root  4096 Jul 10 08:58 root
drwxr-xr-x  29 root root   920 Jul 13 14:42 run
drwxr-xr-x   2 root root 12288 Jun 29 08:03 sbin
drwxr-xr-x   2 root root  4096 Apr 22 05:01 srv
dr-xr-xr-x  13 root root     0 Jul 14 19:20 sys
drwxrwxrwt  16 root root  4096 Jul 17 08:13 tmp
drwxr-xr-x  10 root root  4096 Jul 10 11:42 usr
drwxr-xr-x  14 root root  4096 May 10 18:35 var
lrwxrwxrwx   1 root root    30 Jul 17 08:09 vmlinuz -> boot/vmlinuz-3.19.0-21-generic
lrwxrwxrwx   1 root root    30 Jul 15 08:25 vmlinuz.old -> boot/vmlinuz-3.19.0-22-generic

```

---

### Post by Bashing-om on 2015-07-17
stockpimp; That went ->

pretty well .. But but but .....
I fail to understand why the newer -22 kernel is the one marked as '.old' .

Reboot the system to grub's boot menu, choose the -22 kernel to boot. 
Now with the -22 kernel booted, let's see what results:
```

sudo update-grub

```
If that does not make the situation right, we can reimage 'initramfs' .

[INDENT][INDENT]we are not done
[INDENT][INDENT][INDENT]'til it is all right
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-07-19
stockpimp; Hey !

Status ?

Is this a done deal, or does the fight continue ?

[INDENT][INDENT]or, have I erred
[INDENT][INDENT][INDENT]on the side of breakage
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by stockpimp on 2015-07-21
> **Bashing-om said:**
> stockpimp; That went ->

pretty well .. But but but .....
I fail to understand why the newer -22 kernel is the one marked as '.old' .

Reboot the system to grub's boot menu, choose the -22 kernel to boot. 
Now with the -22 kernel booted, let's see what results:
```

sudo update-grub

```
If that does not make the situation right, we can reimage 'initramfs' .
[INDENT][INDENT]we are not done[INDENT][INDENT][INDENT]'til it is all right
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Sorry, was pre occupied with work related issues.

```

Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done

```

---

### Post by Bashing-om on 2015-07-21
stockpimp; Eyhh,

We work at your pace.

That update-grub looks good to me.

Now are the symlinks correct ?
```

ls -al /

```

Maybe yes
[INDENT][INDENT]maybe more to do
[/INDENT][/INDENT]

---

### Post by stockpimp on 2015-07-22
> **Bashing-om said:**
> stockpimp; Eyhh,

We work at your pace.

That update-grub looks good to me.

Now are the symlinks correct ?
```

ls -al /

```

Maybe yes[INDENT][INDENT]maybe more to do
[/INDENT]
[/INDENT]



> 
total 103
drwxr-xr-x  23 root root  4096 Jul 17 08:09 .
drwxr-xr-x  23 root root  4096 Jul 17 08:09 ..
drwxr-xr-x   2 root root  4096 Jul 10 11:43 bin
drwxr-xr-x   4 root root  3072 Jul 17 08:10 boot
drwxrwxr-x   2 root root  4096 May 10 12:48 cdrom
drwxr-xr-x  20 root root  4480 Jul 21 08:25 dev
drwxr-xr-x 149 root root 12288 Jul 21 08:07 etc
drwxr-xr-x   3 root root  4096 May 10 12:49 home
lrwxrwxrwx   1 root root    33 Jul 17 08:09 initrd.img -> boot/initrd.img-3.19.0-21-generic
lrwxrwxrwx   1 root root    33 Jul 15 08:25 initrd.img.old -> boot/initrd.img-3.19.0-22-generic
drwxr-xr-x  26 root root  4096 Jul 10 11:42 lib
drwxr-xr-x   2 root root  4096 Jul 10 11:42 lib64
drwx------   2 root root 16384 May 10 12:42 lost+found
drwxr-xr-x   3 root root  4096 May 20 13:51 media
drwxr-xr-x   2 root root  4096 Apr 17 14:34 mnt
drwxr-xr-x   3 root root  4096 May 10 18:27 opt
dr-xr-xr-x 281 root root     0 Jul 21 08:24 proc
drwx------   6 root root  4096 Jul 10 08:58 root
drwxr-xr-x  29 root root   840 Jul 21 08:26 run
drwxr-xr-x   2 root root 12288 Jun 29 08:03 sbin
drwxr-xr-x   2 root root  4096 Apr 22 05:01 srv
dr-xr-xr-x  13 root root     0 Jul 21 08:24 sys
drwxrwxrwt  12 root root  4096 Jul 22 06:39 tmp
drwxr-xr-x  10 root root  4096 Jul 10 11:42 usr
drwxr-xr-x  14 root root  4096 May 10 18:35 var
lrwxrwxrwx   1 root root    30 Jul 17 08:09 vmlinuz -> boot/vmlinuz-3.19.0-21-generic
lrwxrwxrwx   1 root root    30 Jul 15 08:25 vmlinuz.old -> boot/vmlinuz-3.19.0-22-generic


Cheers

---

### Post by Bashing-om on 2015-07-22
stockpimp; Yuk;;Yep. 

More work to do. However, I am a bit hesitant to use upstart tools for 15.04's systemd.

It is a working system, and no real harm in booting an older kernel as the latest one. Maybe in a forthcoming update when a new kernel is installed the situation will be corrected ?

Else; if you want we can plow ahead with 'initramfs' tools and see what results. With 15.04 and systemd, it is a fertile field for learning.

[INDENT][INDENT]just my thoughts
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-07-22
Would it be an idea to make a clone of the functional partition before proceeding with further experimentation? :)

---

### Post by Bashing-om on 2015-07-23
stockpimp; Bucky Ball; Uh Huh -> yes

^^ +10, backups are always important - never can tell what might happen . Me though, all I back up are my personal files in my /home and as well - I maintain a "change log" of any alterations I make to the default install .
In those rare events that I do a (RE-)install, I am back up in 20 minutes - with the help of 'rsync'; good as ever.

[INDENT][INDENT]cheap insurance
[/INDENT][/INDENT]

---

### Post by stockpimp on 2015-07-24
> **Bashing-om said:**
> stockpimp; Bucky Ball; Uh Huh -> yes

^^ +10, backups are always important - never can tell what might happen . Me though, all I back up are my personal files in my /home and as well - I maintain a "change log" of any alterations I make to the default install .
In those rare events that I do a (RE-)install, I am back up in 20 minutes - with the help of 'rsync'; good as ever.
[INDENT][INDENT]cheap insurance
[/INDENT]
[/INDENT]



Ok.  I'll be away from this system for a few weeks as of today so I'll touch base with yo when I return.  I'd like to get it cleaned up and I wont have a chance till the end of August.  Thanx for the help and I'll be back to ya shortly!  Cheers!

---

### Post by stockpimp on 2016-05-23
hi guys.  I'm having the same issue as last time.  I have looked back at the previous issue and responses how ever I have no idea how to interpret the data etc.  I would greatly appreciate some assistance straightening his issue out again.  sorry to be a pain.  Cheers.

---

### Post by stockpimp on 2016-05-23
here's the print out from the first dew commands by the way
"dj@Blackbox:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.8G     0  3.8G   0% /dev
tmpfs           789M  9.5M  779M   2% /run
/dev/dm-1       909G  293G  570G  34% /
tmpfs           3.9G  2.5M  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda1       236M  144M   80M  65% /boot
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           789M   48K  789M   1% /run/user/1000
dj@Blackbox:~$ df -l
Filesystem     1K-blocks      Used Available Use% Mounted on
udev             3983716         0   3983716   0% /dev
tmpfs             807008      9728    797280   2% /run
/dev/dm-1      952856484 307097832 597333284  34% /
tmpfs            4035040      2548   4032492   1% /dev/shm
tmpfs               5120         4      5116   1% /run/lock
tmpfs            4035040         0   4035040   0% /sys/fs/cgroup
/dev/sda1         240972    146673     81858  65% /boot
cgmfs                100         0       100   0% /run/cgmanager/fs
tmpfs             807008        48    806960   1% /run/user/1000
dj@Blackbox:~$ dpkg =l | grep linux
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !
dj@Blackbox:~$ dpkg =l|grep linux
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !
dj@Blackbox:~$ cd /
dj@Blackbox:/$ sudo du -sx * | sort -n
[sudo] password for dj: 
du: cannot access ‘proc/6140/task/6140/fd/4’: No such file or directory
du: cannot access ‘proc/6140/task/6140/fdinfo/4’: No such file or directory
du: cannot access ‘proc/6140/fd/4’: No such file or directory
du: cannot access ‘proc/6140/fdinfo/4’: No such file or directory
0    dev
0    initrd.img
0    initrd.img.old
0    proc
0    sys
0    vmlinuz
0    vmlinuz.old
4    cdrom
4    lib64
4    mnt
4    srv
12    media
16    lost+found
76    tmp
80    root
9724    run
12724    bin
14492    sbin
16516    etc
144624    boot
181284    opt
790160    lib
992412    var
5256584    usr
299757780    home
dj@Blackbox:/$ cd
dj@Blackbox:~$ 
"

---

### Post by Bashing-om on 2016-05-23
stockpimp; Welllll ...

/boot is mighty small .. only 80 M .. not enough space to work in another kernel.
try :
```

sudo apt-get autoremove

```
and 
/home is large !// clean out the old videos and music .. see what is in downloads directory ?

[INDENT][INDENT]housecleaning
[INDENT][INDENT][INDENT]everybody has got it to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by stockpimp on 2016-05-23
I believe the partition is the issue.  I did the auto remove as you have suggested but it only removed 2,000kb's and the download update requires several mb's.  I can for sure del all kinds of crap from my drive etc but this partion area I have no idea how to clean out and this is where the issue appears to be.

---

### Post by Bashing-om on 2016-05-23
stockpimp; Welp;

When you look at it .. the /boot partition is very small at only 236M .
It is either work real hard to expand the partition to prolong having to remove old kernels
Or keep up on removing old kernels prior to installing any new one.
for now we can look at what is:
```

dpkg -l | grep linux-

```

see if there is aught that can be done more.

[INDENT][INDENT]keep it clean as you go
[/INDENT][/INDENT]

---

### Post by stockpimp on 2016-05-23
> **Bashing-om said:**
> stockpimp; Welp;

When you look at it .. the /boot partition is very small at only 236M .
It is either work real hard to expand the partition to prolong having to remove old kernels
Or keep up on removing old kernels prior to installing any new one.
for now we can look at what is:
```

dpkg -l | grep linux

```

see if there is aught that can be done more.[INDENT][INDENT]keep it clean as you go
[/INDENT]
[/INDENT]


k.  this is what I got.
```

dj@Blackbox:~$ dpkg -l | grep linux
ii  console-setup-linux                                  1.108ubuntu9                               all          Linux specific part of console-setup
ii  libselinux1:amd64                                    2.3-2build1                                amd64        SELinux runtime shared libraries
ii  libselinux1:i386                                     2.3-2build1                                i386         SELinux runtime shared libraries
ii  libv4l-0:amd64                                       1.6.3-1                                    amd64        Collection of video4linux support libraries
ii  libv4lconvert0:amd64                                 1.6.3-1                                    amd64        Video4linux frame format conversion library
ii  linux-firmware                                       1.149.3                                    all          Firmware for Linux kernel drivers
ii  linux-generic                                        4.2.0.30.33                                amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.2.0-27                               4.2.0-27.32                                all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-27-generic                       4.2.0-27.32                                amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-30                               4.2.0-30.36                                all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-30-generic                       4.2.0-30.36                                amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                                4.2.0.30.33                                amd64        Generic Linux kernel headers
rc  linux-image-3.19.0-15-generic                        3.19.0-15.15                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-20-generic                        3.19.0-20.20                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-21-generic                        3.19.0-21.21                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-22-generic                        3.19.0-22.22                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-27-generic                         4.2.0-27.32                                amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-30-generic                         4.2.0-30.36                                amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-15-generic                  3.19.0-15.15                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-20-generic                  3.19.0-20.20                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-21-generic                  3.19.0-21.21                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-22-generic                  3.19.0-22.22                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-27-generic                   4.2.0-27.32                                amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-30-generic                   4.2.0-30.36                                amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-generic                                  4.2.0.30.33                                amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                 4.2.0-30.36                                amd64        Linux Kernel Headers for development
ii  linux-sound-base                                     1.0.25+dfsg-0ubuntu5                       all          base package for ALSA and OSS sound systems
ii  pptp-linux                                           1.8.0-1                                    amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                             3:6.03+dfsg-8ubuntu2                       amd64        collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                                      3:6.03+dfsg-8ubuntu2                       all          collection of bootloaders (common)
ii  syslinux-legacy                                      2:3.63+dfsg-2ubuntu8                       amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                           2.26.2-6ubuntu3                            amd64        Miscellaneous system utilities
dj@Blackbox:~$ 


```

is this good bad?  Not sure what I'm ment to do with this info.  Cheers and thank-you for the help.  Conpletely out of my depth with this type of issue.

---

### Post by Bashing-om on 2016-05-23
stockpimp; Well ..

That tells us, there is not a whole lot we can do . Remove the -22 image and a small amount of clean up. Will not gain much.

So next is what is the booting kernel ? - we do not mess about with this kernel !
```

uname -r

```

And I want to know that this system is fully updated and the package manager is in a consistent state.
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install
sudo dpkg -C

``` post the results if there are any errors.

[INDENT][INDENT]'bout all we can do
[/INDENT][/INDENT]

---

### Post by stockpimp on 2016-05-23
> **Bashing-om said:**
> stockpimp; Well ..

That tells us, there is not a whole lot we can do . Remove the -22 image and a small amount of clean up. Will not gain much.

So next is what is the booting kernel ? - we do not mess about with this kernel !
```

uname -r

```

And I want to know that this system is fully updated and the package manager is in a consistent state.
```

sudo apt update
sudo apt full-upgrade

dj@Blackbox:~$ sudo apt update
[sudo] password for dj: 
Ign http://dl.google.com stable InRelease
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://archive.canonical.com wily InRelease                                
Hit http://ca.archive.ubuntu.com wily InRelease                          
Get:1 http://security.ubuntu.com wily-security InRelease [65.9 kB]             
Get:2 http://ca.archive.ubuntu.com wily-updates InRelease [65.9 kB]            
Get:3 http://security.ubuntu.com wily-security/main Sources [49.0 kB]          
Hit http://ca.archive.ubuntu.com wily-backports InRelease                      
Get:4 http://security.ubuntu.com wily-security/restricted Sources [2,854 B]    
Hit http://archive.canonical.com wily/partner Sources                          
Get:5 http://security.ubuntu.com wily-security/universe Sources [12.2 kB]      
Hit http://archive.canonical.com wily/partner amd64 Packages                   
Get:6 http://security.ubuntu.com wily-security/multiverse Sources [2,789 B]    
Hit http://archive.canonical.com wily/partner i386 Packages                    
Get:7 http://security.ubuntu.com wily-security/main amd64 Packages [155 kB]    
Hit http://archive.canonical.com wily/partner Translation-en                  
Get:8 http://security.ubuntu.com wily-security/restricted amd64 Packages [10.9 kB]
Get:9 http://security.ubuntu.com wily-security/universe amd64 Packages [53.0 kB]
Get:10 http://security.ubuntu.com wily-security/multiverse amd64 Packages [6,256 B]
Get:11 http://security.ubuntu.com wily-security/main i386 Packages [152 kB]
Get:12 http://security.ubuntu.com wily-security/restricted i386 Packages [10.8 kB]
Get:13 http://security.ubuntu.com wily-security/universe i386 Packages [53.1 kB]
Get:14 http://security.ubuntu.com wily-security/multiverse i386 Packages [6,434 B]
Hit http://security.ubuntu.com wily-security/main Translation-en        
Hit http://security.ubuntu.com wily-security/multiverse Translation-en
Get:15 http://ca.archive.ubuntu.com wily-updates/main Sources [79.8 kB]
Hit http://security.ubuntu.com wily-security/restricted Translation-en 
Get:16 http://ca.archive.ubuntu.com wily-updates/restricted Sources [3,741 B]
Hit http://security.ubuntu.com wily-security/universe Translation-en   
Get:17 http://ca.archive.ubuntu.com wily-updates/universe Sources [24.3 kB]
Get:18 http://ca.archive.ubuntu.com wily-updates/multiverse Sources [3,196 B]
Get:19 http://ca.archive.ubuntu.com wily-updates/main amd64 Packages [221 kB]
Get:20 http://ca.archive.ubuntu.com wily-updates/restricted amd64 Packages [13.3 kB]
Get:21 http://ca.archive.ubuntu.com wily-updates/universe amd64 Packages [96.5 kB]
Get:22 http://ca.archive.ubuntu.com wily-updates/multiverse amd64 Packages [6,256 B]
Get:23 http://ca.archive.ubuntu.com wily-updates/main i386 Packages [217 kB]
Get:24 http://ca.archive.ubuntu.com wily-updates/restricted i386 Packages [13.4 kB]
Get:25 http://ca.archive.ubuntu.com wily-updates/universe i386 Packages [94.0 kB]
Get:26 http://ca.archive.ubuntu.com wily-updates/multiverse i386 Packages [6,687 B]
Get:27 http://ca.archive.ubuntu.com wily-updates/main Translation-en [102 kB]
Get:28 http://ca.archive.ubuntu.com wily-updates/multiverse Translation-en [3,156 B]
Get:29 http://ca.archive.ubuntu.com wily-updates/restricted Translation-en [3,024 B]
Get:30 http://ca.archive.ubuntu.com wily-updates/universe Translation-en [55.3 kB]
Hit http://ca.archive.ubuntu.com wily-backports/restricted Sources             
Hit http://ca.archive.ubuntu.com wily-backports/multiverse Sources             
Hit http://ca.archive.ubuntu.com wily-backports/restricted amd64 Packages      
Hit http://ca.archive.ubuntu.com wily-backports/multiverse amd64 Packages      
Hit http://ca.archive.ubuntu.com wily-backports/restricted i386 Packages       
Hit http://ca.archive.ubuntu.com wily-backports/multiverse i386 Packages       
Hit http://ca.archive.ubuntu.com wily-backports/multiverse Translation-en      
Hit http://ca.archive.ubuntu.com wily-backports/restricted Translation-en      
Hit http://ca.archive.ubuntu.com wily/main Sources                             
Hit http://ca.archive.ubuntu.com wily/restricted Sources                       
Hit http://ca.archive.ubuntu.com wily/universe Sources                         
Hit http://ca.archive.ubuntu.com wily/multiverse Sources                       
Hit http://ca.archive.ubuntu.com wily/main amd64 Packages                      
Hit http://ca.archive.ubuntu.com wily/restricted amd64 Packages                
Hit http://ca.archive.ubuntu.com wily/universe amd64 Packages                  
Hit http://ca.archive.ubuntu.com wily/multiverse amd64 Packages                
Hit http://ca.archive.ubuntu.com wily/main i386 Packages                       
Hit http://ca.archive.ubuntu.com wily/restricted i386 Packages                 
Hit http://ca.archive.ubuntu.com wily/universe i386 Packages                   
Hit http://ca.archive.ubuntu.com wily/multiverse i386 Packages                 
Hit http://ca.archive.ubuntu.com wily/main Translation-en_CA                   
Hit http://ca.archive.ubuntu.com wily/main Translation-en                      
Hit http://ca.archive.ubuntu.com wily/multiverse Translation-en                
Hit http://ca.archive.ubuntu.com wily/restricted Translation-en                
Hit http://ca.archive.ubuntu.com wily/universe Translation-en_CA               
Hit http://ca.archive.ubuntu.com wily/universe Translation-en                  
Hit http://ca.archive.ubuntu.com wily-backports/main Sources                   
Hit http://ca.archive.ubuntu.com wily-backports/universe Sources               
Hit http://ca.archive.ubuntu.com wily-backports/main amd64 Packages            
Hit http://ca.archive.ubuntu.com wily-backports/universe amd64 Packages        
Hit http://ca.archive.ubuntu.com wily-backports/main i386 Packages             
Hit http://ca.archive.ubuntu.com wily-backports/universe i386 Packages         
Hit http://ca.archive.ubuntu.com wily-backports/main Translation-en            
Hit http://ca.archive.ubuntu.com wily-backports/universe Translation-en        
Fetched 1,589 kB in 11s (134 kB/s)                                             
W: There is no public key available for the following key IDs:
1397BC53640DB551
W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
dj@Blackbox:~$ sudo full-upgrade
sudo: full-upgrade: command not found
dj@Blackbox:~$ sudo apt full-upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
dj@Blackbox:~$ sudo dpkg --configure -a
Setting up libtdb1:amd64 (1.3.8-0ubuntu0.15.10.1) ...
Setting up libwbclient0:amd64 (2:4.3.9+dfsg-0ubuntu0.15.10.1) ...
Setting up libexpat1:amd64 (2.1.0-7ubuntu0.15.10.1) ...
Setting up libexpat1:i386 (2.1.0-7ubuntu0.15.10.1) ...
Setting up apt-transport-https (1.0.10.2ubuntu2) ...
Setting up libpam-systemd:amd64 (225-1ubuntu9.1) ...
Setting up libssl1.0.0:amd64 (1.0.2d-0ubuntu1.5) ...
Setting up libssl1.0.0:i386 (1.0.2d-0ubuntu1.5) ...
Processing triggers for mime-support (3.58ubuntu1) ...
Setting up python-tdb (1.3.8-0ubuntu0.15.10.1) ...
Setting up tzdata-java (2016d-0ubuntu0.15.10) ...
Setting up libapt-inst1.7:amd64 (1.0.10.2ubuntu2) ...
Setting up mysql-common (5.6.30-0ubuntu0.15.10.1) ...
Setting up samba-common (2:4.3.9+dfsg-0ubuntu0.15.10.1) ...
Setting up libmysqlclient18:amd64 (5.6.30-0ubuntu0.15.10.1) ...
Setting up libmysqlclient18:i386 (5.6.30-0ubuntu0.15.10.1) ...
Setting up libpcre3:amd64 (2:8.35-7.1ubuntu1.4) ...
Setting up libpcre3:i386 (2:8.35-7.1ubuntu1.4) ...
Setting up libtasn1-6:amd64 (4.5-2ubuntu0.1) ...
Setting up libtasn1-6:i386 (4.5-2ubuntu0.1) ...
Setting up libglib2.0-data (2.46.2-1ubuntu2) ...
Setting up init-system-helpers (1.23ubuntu4) ...
Setting up libldap-2.4-2:amd64 (2.4.41+dfsg-1ubuntu2.1) ...
Setting up chromium-codecs-ffmpeg-extra (50.0.2661.102-0ubuntu0.15.10.1.1227) ...
Setting up openssl (1.0.2d-0ubuntu1.5) ...
Setting up libexpat1-dev:amd64 (2.1.0-7ubuntu0.15.10.1) ...
Processing triggers for man-db (2.7.4-1) ...
Setting up libtalloc2:amd64 (2.1.5-0ubuntu0.15.10.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu1) ...
Setting up linux-image-4.2.0-36-generic (4.2.0-36.42) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-36-generic /boot/vmlinuz-4.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-36-generic /boot/vmlinuz-4.2.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.2.0-36-generic /boot/vmlinuz-4.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.2.0-36-generic /boot/vmlinuz-4.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.2.0-36-generic /boot/vmlinuz-4.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.2.0-36-generic /boot/vmlinuz-4.2.0-36-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-36-generic
Found initrd image: /boot/initrd.img-4.2.0-36-generic
Found linux image: /boot/vmlinuz-4.2.0-30-generic
Found initrd image: /boot/initrd.img-4.2.0-30-generic
Found linux image: /boot/vmlinuz-4.2.0-27-generic
Found initrd image: /boot/initrd.img-4.2.0-27-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up openssh-client (1:6.9p1-2ubuntu0.2) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Setting up python-talloc (2.1.5-0ubuntu0.15.10.1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Setting up apt-utils (1.0.10.2ubuntu2) ...
Setting up libglib2.0-0:amd64 (2.46.2-1ubuntu2) ...
Setting up libglib2.0-0:i386 (2.46.2-1ubuntu2) ...
Setting up openjdk-7-jre-headless:amd64 (7u101-2.6.6-0ubuntu0.15.10.1) ...
Installing new version of config file /etc/java-7-openjdk/management/management.properties ...
Processing triggers for bamfdaemon (0.5.2~bzr0+15.10.20150627.1-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up libtevent0:amd64 (0.9.28-0ubuntu0.15.10.1) ...
Setting up google-chrome-stable (50.0.2661.102-1) ...
Setting up openjdk-7-jre:amd64 (7u101-2.6.6-0ubuntu0.15.10.1) ...
Setting up libglib2.0-bin (2.46.2-1ubuntu2) ...
Setting up adobe-flashplugin (1:20160512.1-0ubuntu0.15.10.1) ...
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) in auto mode
Setting up adobe-flash-properties-gtk (1:20160512.1-0ubuntu0.15.10.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Setting up libldb1:amd64 (2:1.1.24-0ubuntu0.15.10.1) ...
Setting up python-ldb (2:1.1.24-0ubuntu0.15.10.1) ...
Setting up samba-libs:amd64 (2:4.3.9+dfsg-0ubuntu0.15.10.1) ...
Setting up python-samba (2:4.3.9+dfsg-0ubuntu0.15.10.1) ...
Setting up libsmbclient:amd64 (2:4.3.9+dfsg-0ubuntu0.15.10.1) ...
Setting up samba-common-bin (2:4.3.9+dfsg-0ubuntu0.15.10.1) ...
Processing triggers for libc-bin (2.21-0ubuntu4.1) ...
dj@Blackbox:~$ sudo full-upgrade
sudo: full-upgrade: command not found
dj@Blackbox:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following packages were automatically installed and are no longer required:
  linux-headers-4.2.0-27 linux-headers-4.2.0-27-generic
  linux-image-4.2.0-27-generic linux-image-extra-4.2.0-27-generic
Use 'apt-get autoremove' to remove them.
Done
The following NEW packages will be installed:
  linux-headers-4.2.0-36 linux-headers-4.2.0-36-generic
  linux-image-extra-4.2.0-36-generic
The following packages have been kept back:
  openjdk-8-jre openjdk-8-jre-headless
The following packages will be upgraded:
  firefox firefox-locale-en gir1.2-gstreamer-1.0 gir1.2-javascriptcoregtk-3.0
  gir1.2-soup-2.4 gir1.2-webkit-3.0 gstreamer1.0-tools libapache2-mod-php5
  libarchive13 libgraphite2-3 libgstreamer1.0-0 libgstreamer1.0-0:i386
  libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0 libndp0
  libnm-glib-vpn1 libnm-glib4 libnm-util2 libnm0 liboxideqt-qmlplugin
  liboxideqtcore0 liboxideqtquick0 libpcre16-3 libpoppler-glib8 libpoppler52
  libpq5 libsoup-gnome2.4-1 libsoup2.4-1 libtiff-tools libtiff5 libtiff5:i386
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwebkitgtk-3.0-0
  libwebkitgtk-3.0-common linux-generic linux-headers-generic
  linux-image-generic linux-libc-dev network-manager oxideqt-codecs-extra
  php-pear php5 php5-cli php5-common php5-gd php5-intl php5-mysqlnd
  php5-pspell php5-readline php5-sqlite poppler-utils python-pip simple-scan
  ssh-askpass-gnome thermald thunderbird thunderbird-gnome-support
  thunderbird-locale-en thunderbird-locale-en-us xserver-xorg-video-openchrome
61 upgraded, 3 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0 B/190 MB of archives.
After this operation, 244 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Extracting templates from packages: 100%
(Reading database ... 271699 files and directories currently installed.)
Preparing to unpack .../firefox_46.0.1+build1-0ubuntu0.15.10.2_amd64.deb ...
Unpacking firefox (46.0.1+build1-0ubuntu0.15.10.2) over (45.0+build2-0ubuntu0.15.10.1) ...
Preparing to unpack .../firefox-locale-en_46.0.1+build1-0ubuntu0.15.10.2_amd64.deb ...
Unpacking firefox-locale-en (46.0.1+build1-0ubuntu0.15.10.2) over (45.0+build2-0ubuntu0.15.10.1) ...
Preparing to unpack .../libgstreamer1.0-0_1.6.3-1ubuntu1_amd64.deb ...
De-configuring libgstreamer1.0-0:i386 (1.6.0-1) ...
Unpacking libgstreamer1.0-0:amd64 (1.6.3-1ubuntu1) over (1.6.0-1) ...
Preparing to unpack .../libgstreamer1.0-0_1.6.3-1ubuntu1_i386.deb ...
Unpacking libgstreamer1.0-0:i386 (1.6.3-1ubuntu1) over (1.6.0-1) ...
Preparing to unpack .../gir1.2-gstreamer-1.0_1.6.3-1ubuntu1_amd64.deb ...
Unpacking gir1.2-gstreamer-1.0 (1.6.3-1ubuntu1) over (1.6.0-1) ...
Preparing to unpack .../libsoup2.4-1_2.50.0-2ubuntu0.1_amd64.deb ...
Unpacking libsoup2.4-1:amd64 (2.50.0-2ubuntu0.1) over (2.50.0-2debian1) ...
Preparing to unpack .../libsoup-gnome2.4-1_2.50.0-2ubuntu0.1_amd64.deb ...
Unpacking libsoup-gnome2.4-1:amd64 (2.50.0-2ubuntu0.1) over (2.50.0-2debian1) ...
Preparing to unpack .../gir1.2-soup-2.4_2.50.0-2ubuntu0.1_amd64.deb ...
Unpacking gir1.2-soup-2.4 (2.50.0-2ubuntu0.1) over (2.50.0-2debian1) ...
Preparing to unpack .../libwebkitgtk-3.0-0_2.4.10-0ubuntu0.15.10.1_amd64.deb ...
Unpacking libwebkitgtk-3.0-0:amd64 (2.4.10-0ubuntu0.15.10.1) over (2.4.9-2ubuntu2) ...
Preparing to unpack .../libjavascriptcoregtk-3.0-0_2.4.10-0ubuntu0.15.10.1_amd64.deb ...
Unpacking libjavascriptcoregtk-3.0-0:amd64 (2.4.10-0ubuntu0.15.10.1) over (2.4.9-2ubuntu2) ...
Preparing to unpack .../libwebkitgtk-3.0-common_2.4.10-0ubuntu0.15.10.1_all.deb ...
Unpacking libwebkitgtk-3.0-common (2.4.10-0ubuntu0.15.10.1) over (2.4.9-2ubuntu2) ...
Preparing to unpack .../gir1.2-webkit-3.0_2.4.10-0ubuntu0.15.10.1_amd64.deb ...
Unpacking gir1.2-webkit-3.0:amd64 (2.4.10-0ubuntu0.15.10.1) over (2.4.9-2ubuntu2) ...
Preparing to unpack .../gir1.2-javascriptcoregtk-3.0_2.4.10-0ubuntu0.15.10.1_amd64.deb ...
Unpacking gir1.2-javascriptcoregtk-3.0:amd64 (2.4.10-0ubuntu0.15.10.1) over (2.4.9-2ubuntu2) ...
Preparing to unpack .../gstreamer1.0-tools_1.6.3-1ubuntu1_amd64.deb ...
Unpacking gstreamer1.0-tools (1.6.3-1ubuntu1) over (1.6.0-1) ...
Preparing to unpack .../php5-sqlite_5.6.11+dfsg-1ubuntu3.3_amd64.deb ...
Unpacking php5-sqlite (5.6.11+dfsg-1ubuntu3.3) over (5.6.11+dfsg-1ubuntu3.1) ...
Preparing to unpack .../php5-gd_5.6.11+dfsg-1ubuntu3.3_amd64.deb ...
Unpacking php5-gd (5.6.11+dfsg-1ubuntu3.3) over (5.6.11+dfsg-1ubuntu3.1) ...
Preparing to unpack .../php5-readline_5.6.11+dfsg-1ubuntu3.3_amd64.deb ...
Unpacking php5-readline (5.6.11+dfsg-1ubuntu3.3) over (5.6.11+dfsg-1ubuntu3.1) ...
Preparing to unpack .../php5-cli_5.6.11+dfsg-1ubuntu3.3_amd64.deb ...
Unpacking php5-cli (5.6.11+dfsg-1ubuntu3.3) over (5.6.11+dfsg-1ubuntu3.1) ...
Preparing to unpack .../php5-intl_5.6.11+dfsg-1ubuntu3.3_amd64.deb ...
Unpacking php5-intl (5.6.11+dfsg-1ubuntu3.3) over (5.6.11+dfsg-1ubuntu3.1) ...
Preparing to unpack .../php5-mysqlnd_5.6.11+dfsg-1ubuntu3.3_amd64.deb ...
Unpacking php5-mysqlnd (5.6.11+dfsg-1ubuntu3.3) over (5.6.11+dfsg-1ubuntu3.1) ...
Preparing to unpack .../php5-pspell_5.6.11+dfsg-1ubuntu3.3_amd64.deb ...
Unpacking php5-pspell (5.6.11+dfsg-1ubuntu3.3) over (5.6.11+dfsg-1ubuntu3.1) ...
Preparing to unpack .../libapache2-mod-php5_5.6.11+dfsg-1ubuntu3.3_amd64.deb ...
Unpacking libapache2-mod-php5 (5.6.11+dfsg-1ubuntu3.3) over (5.6.11+dfsg-1ubuntu3.1) ...
Preparing to unpack .../php5-common_5.6.11+dfsg-1ubuntu3.3_amd64.deb ...
Unpacking php5-common (5.6.11+dfsg-1ubuntu3.3) over (5.6.11+dfsg-1ubuntu3.1) ...
Preparing to unpack .../libarchive13_3.1.2-11ubuntu0.15.10.1_amd64.deb ...
Unpacking libarchive13:amd64 (3.1.2-11ubuntu0.15.10.1) over (3.1.2-11build1) ...
Preparing to unpack .../libgraphite2-3_1.3.6-1ubuntu0.15.10.1_amd64.deb ...
Unpacking libgraphite2-3:amd64 (1.3.6-1ubuntu0.15.10.1) over (1.2.4-3ubuntu1.1) ...
Preparing to unpack .../libwebkitgtk-1.0-common_2.4.10-0ubuntu0.15.10.1_all.deb ...
Unpacking libwebkitgtk-1.0-common (2.4.10-0ubuntu0.15.10.1) over (2.4.9-2ubuntu2) ...
Preparing to unpack .../libwebkitgtk-1.0-0_2.4.10-0ubuntu0.15.10.1_amd64.deb ...
Unpacking libwebkitgtk-1.0-0:amd64 (2.4.10-0ubuntu0.15.10.1) over (2.4.9-2ubuntu2) ...
Preparing to unpack .../libjavascriptcoregtk-1.0-0_2.4.10-0ubuntu0.15.10.1_amd64.deb ...
Unpacking libjavascriptcoregtk-1.0-0:amd64 (2.4.10-0ubuntu0.15.10.1) over (2.4.9-2ubuntu2) ...
Preparing to unpack .../libndp0_1.4-2ubuntu0.15.10.1_amd64.deb ...
Unpacking libndp0:amd64 (1.4-2ubuntu0.15.10.1) over (1.4-2) ...
Preparing to unpack .../libnm-util2_1.0.4-0ubuntu5.3_amd64.deb ...
Unpacking libnm-util2:amd64 (1.0.4-0ubuntu5.3) over (1.0.4-0ubuntu5.2) ...
Preparing to unpack .../libnm-glib-vpn1_1.0.4-0ubuntu5.3_amd64.deb ...
Unpacking libnm-glib-vpn1:amd64 (1.0.4-0ubuntu5.3) over (1.0.4-0ubuntu5.2) ...
Preparing to unpack .../libnm-glib4_1.0.4-0ubuntu5.3_amd64.deb ...
Unpacking libnm-glib4:amd64 (1.0.4-0ubuntu5.3) over (1.0.4-0ubuntu5.2) ...
Preparing to unpack .../libnm0_1.0.4-0ubuntu5.3_amd64.deb ...
Unpacking libnm0:amd64 (1.0.4-0ubuntu5.3) over (1.0.4-0ubuntu5.2) ...
Preparing to unpack .../libpcre16-3_2%3a8.35-7.1ubuntu1.4_amd64.deb ...
Unpacking libpcre16-3:amd64 (2:8.35-7.1ubuntu1.4) over (2:8.35-7.1ubuntu1) ...
Preparing to unpack .../libtiff5_4.0.3-12.3ubuntu2.1_amd64.deb ...
De-configuring libtiff5:i386 (4.0.3-12.3ubuntu2) ...
Unpacking libtiff5:amd64 (4.0.3-12.3ubuntu2.1) over (4.0.3-12.3ubuntu2) ...
Preparing to unpack .../libtiff5_4.0.3-12.3ubuntu2.1_i386.deb ...
Unpacking libtiff5:i386 (4.0.3-12.3ubuntu2.1) over (4.0.3-12.3ubuntu2) ...
Preparing to unpack .../libpoppler52_0.33.0-0ubuntu3.1_amd64.deb ...
Unpacking libpoppler52:amd64 (0.33.0-0ubuntu3.1) over (0.33.0-0ubuntu3) ...
Preparing to unpack .../libpoppler-glib8_0.33.0-0ubuntu3.1_amd64.deb ...
Unpacking libpoppler-glib8:amd64 (0.33.0-0ubuntu3.1) over (0.33.0-0ubuntu3) ...
Preparing to unpack .../libpq5_9.4.8-0ubuntu0.15.10_amd64.deb ...
Unpacking libpq5:amd64 (9.4.8-0ubuntu0.15.10) over (9.4.6-0ubuntu0.15.10) ...
Preparing to unpack .../libtiff-tools_4.0.3-12.3ubuntu2.1_amd64.deb ...
Unpacking libtiff-tools (4.0.3-12.3ubuntu2.1) over (4.0.3-12.3ubuntu2) ...
Selecting previously unselected package linux-image-extra-4.2.0-36-generic.
Preparing to unpack .../linux-image-extra-4.2.0-36-generic_4.2.0-36.42_amd64.deb ...
Unpacking linux-image-extra-4.2.0-36-generic (4.2.0-36.42) ...
Preparing to unpack .../linux-generic_4.2.0.36.39_amd64.deb ...
Unpacking linux-generic (4.2.0.36.39) over (4.2.0.30.33) ...
Preparing to unpack .../linux-image-generic_4.2.0.36.39_amd64.deb ...
Unpacking linux-image-generic (4.2.0.36.39) over (4.2.0.30.33) ...
Selecting previously unselected package linux-headers-4.2.0-36.
Preparing to unpack .../linux-headers-4.2.0-36_4.2.0-36.42_all.deb ...
Unpacking linux-headers-4.2.0-36 (4.2.0-36.42) ...
Selecting previously unselected package linux-headers-4.2.0-36-generic.
Preparing to unpack .../linux-headers-4.2.0-36-generic_4.2.0-36.42_amd64.deb ...
Unpacking linux-headers-4.2.0-36-generic (4.2.0-36.42) ...
Preparing to unpack .../linux-headers-generic_4.2.0.36.39_amd64.deb ...
Unpacking linux-headers-generic (4.2.0.36.39) over (4.2.0.30.33) ...
Preparing to unpack .../linux-libc-dev_4.2.0-36.42_amd64.deb ...
Unpacking linux-libc-dev:amd64 (4.2.0-36.42) over (4.2.0-30.36) ...
Preparing to unpack .../network-manager_1.0.4-0ubuntu5.3_amd64.deb ...
Unpacking network-manager (1.0.4-0ubuntu5.3) over (1.0.4-0ubuntu5.2) ...
Preparing to unpack .../php-pear_5.6.11+dfsg-1ubuntu3.3_all.deb ...
Unpacking php-pear (5.6.11+dfsg-1ubuntu3.3) over (5.6.11+dfsg-1ubuntu3.1) ...
Preparing to unpack .../php5_5.6.11+dfsg-1ubuntu3.3_all.deb ...
Unpacking php5 (5.6.11+dfsg-1ubuntu3.3) over (5.6.11+dfsg-1ubuntu3.1) ...
Preparing to unpack .../poppler-utils_0.33.0-0ubuntu3.1_amd64.deb ...
Unpacking poppler-utils (0.33.0-0ubuntu3.1) over (0.33.0-0ubuntu3) ...
Preparing to unpack .../python-pip_1.5.6-7ubuntu1.2_all.deb ...
Unpacking python-pip (1.5.6-7ubuntu1.2) over (1.5.6-7ubuntu1.1) ...
Preparing to unpack .../simple-scan_3.18.2-0ubuntu1_amd64.deb ...
Unpacking simple-scan (3.18.2-0ubuntu1) over (3.18.1-0ubuntu1) ...
Preparing to unpack .../ssh-askpass-gnome_1%3a6.9p1-2ubuntu0.2_amd64.deb ...
Unpacking ssh-askpass-gnome (1:6.9p1-2ubuntu0.2) over (1:6.9p1-2ubuntu0.1) ...
Preparing to unpack .../thermald_1.4.3-5ubuntu1_amd64.deb ...
Unpacking thermald (1.4.3-5ubuntu1) over (1.4.3-5) ...
Preparing to unpack .../thunderbird-locale-en_1%3a38.8.0+build1-0ubuntu0.15.10.1_amd64.deb ...
Unpacking thunderbird-locale-en (1:38.8.0+build1-0ubuntu0.15.10.1) over (1:38.6.0+build1-0ubuntu0.15.10.1) ...
Preparing to unpack .../thunderbird_1%3a38.8.0+build1-0ubuntu0.15.10.1_amd64.deb ...
Unpacking thunderbird (1:38.8.0+build1-0ubuntu0.15.10.1) over (1:38.6.0+build1-0ubuntu0.15.10.1) ...
Preparing to unpack .../thunderbird-gnome-support_1%3a38.8.0+build1-0ubuntu0.15.10.1_amd64.deb ...
Unpacking thunderbird-gnome-support (1:38.8.0+build1-0ubuntu0.15.10.1) over (1:38.6.0+build1-0ubuntu0.15.10.1) ...
Preparing to unpack .../thunderbird-locale-en-us_1%3a38.8.0+build1-0ubuntu0.15.10.1_all.deb ...
Unpacking thunderbird-locale-en-us (1:38.8.0+build1-0ubuntu0.15.10.1) over (1:38.6.0+build1-0ubuntu0.15.10.1) ...
Preparing to unpack .../xserver-xorg-video-openchrome_1%3a0.3.3-1ubuntu1.1_amd64.deb ...
Unpacking xserver-xorg-video-openchrome (1:0.3.3-1ubuntu1.1) over (1:0.3.3-1ubuntu1) ...
Preparing to unpack .../liboxideqt-qmlplugin_1.14.9-0ubuntu0.15.10.1_amd64.deb ...
Unpacking liboxideqt-qmlplugin:amd64 (1.14.9-0ubuntu0.15.10.1) over (1.13.6-0ubuntu0.15.10.1) ...
Preparing to unpack .../liboxideqtquick0_1.14.9-0ubuntu0.15.10.1_amd64.deb ...
Unpacking liboxideqtquick0:amd64 (1.14.9-0ubuntu0.15.10.1) over (1.13.6-0ubuntu0.15.10.1) ...
Preparing to unpack .../liboxideqtcore0_1.14.9-0ubuntu0.15.10.1_amd64.deb ...
Unpacking liboxideqtcore0:amd64 (1.14.9-0ubuntu0.15.10.1) over (1.13.6-0ubuntu0.15.10.1) ...
Preparing to unpack .../oxideqt-codecs-extra_1.14.9-0ubuntu0.15.10.1_amd64.deb ...
Unpacking oxideqt-codecs-extra:amd64 (1.14.9-0ubuntu0.15.10.1) over (1.13.6-0ubuntu0.15.10.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu1) ...
Processing triggers for bamfdaemon (0.5.2~bzr0+15.10.20150627.1-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for man-db (2.7.4-1) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (225-1ubuntu9.1) ...
Processing triggers for dbus (1.10.0-1ubuntu1) ...
Processing triggers for doc-base (0.10.6) ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Processing triggers for libglib2.0-0:i386 (2.46.2-1ubuntu2) ...
Processing triggers for libglib2.0-0:amd64 (2.46.2-1ubuntu2) ...
Setting up firefox (46.0.1+build1-0ubuntu0.15.10.2) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-locale-en (46.0.1+build1-0ubuntu0.15.10.2) ...
Setting up libgstreamer1.0-0:i386 (1.6.3-1ubuntu1) ...
Setcap worked! gst-ptp-helper is not suid!
Setting up libgstreamer1.0-0:amd64 (1.6.3-1ubuntu1) ...
Setcap worked! gst-ptp-helper is not suid!
Setting up gir1.2-gstreamer-1.0 (1.6.3-1ubuntu1) ...
Setting up libsoup2.4-1:amd64 (2.50.0-2ubuntu0.1) ...
Setting up libsoup-gnome2.4-1:amd64 (2.50.0-2ubuntu0.1) ...
Setting up gir1.2-soup-2.4 (2.50.0-2ubuntu0.1) ...
Setting up libjavascriptcoregtk-3.0-0:amd64 (2.4.10-0ubuntu0.15.10.1) ...
Setting up libwebkitgtk-3.0-common (2.4.10-0ubuntu0.15.10.1) ...
Setting up libwebkitgtk-3.0-0:amd64 (2.4.10-0ubuntu0.15.10.1) ...
Setting up gir1.2-javascriptcoregtk-3.0:amd64 (2.4.10-0ubuntu0.15.10.1) ...
Setting up gir1.2-webkit-3.0:amd64 (2.4.10-0ubuntu0.15.10.1) ...
Setting up gstreamer1.0-tools (1.6.3-1ubuntu1) ...
Setting up php5-common (5.6.11+dfsg-1ubuntu3.3) ...
Setting up php5-sqlite (5.6.11+dfsg-1ubuntu3.3) ...
Setting up php5-gd (5.6.11+dfsg-1ubuntu3.3) ...
Setting up php5-cli (5.6.11+dfsg-1ubuntu3.3) ...
Setting up php5-readline (5.6.11+dfsg-1ubuntu3.3) ...
Setting up php5-intl (5.6.11+dfsg-1ubuntu3.3) ...
Setting up php5-mysqlnd (5.6.11+dfsg-1ubuntu3.3) ...
Setting up php5-pspell (5.6.11+dfsg-1ubuntu3.3) ...
Setting up libapache2-mod-php5 (5.6.11+dfsg-1ubuntu3.3) ...
apache2_invoke php5: already enabled
Setting up libarchive13:amd64 (3.1.2-11ubuntu0.15.10.1) ...
Setting up libgraphite2-3:amd64 (1.3.6-1ubuntu0.15.10.1) ...
Setting up libwebkitgtk-1.0-common (2.4.10-0ubuntu0.15.10.1) ...
Setting up libjavascriptcoregtk-1.0-0:amd64 (2.4.10-0ubuntu0.15.10.1) ...
Setting up libwebkitgtk-1.0-0:amd64 (2.4.10-0ubuntu0.15.10.1) ...
Setting up libndp0:amd64 (1.4-2ubuntu0.15.10.1) ...
Setting up libnm-util2:amd64 (1.0.4-0ubuntu5.3) ...
Setting up libnm-glib-vpn1:amd64 (1.0.4-0ubuntu5.3) ...
Setting up libnm-glib4:amd64 (1.0.4-0ubuntu5.3) ...
Setting up libnm0:amd64 (1.0.4-0ubuntu5.3) ...
Setting up libpcre16-3:amd64 (2:8.35-7.1ubuntu1.4) ...
Setting up libtiff5:i386 (4.0.3-12.3ubuntu2.1) ...
Setting up libtiff5:amd64 (4.0.3-12.3ubuntu2.1) ...
Setting up libpoppler52:amd64 (0.33.0-0ubuntu3.1) ...
Setting up libpoppler-glib8:amd64 (0.33.0-0ubuntu3.1) ...
Setting up libpq5:amd64 (9.4.8-0ubuntu0.15.10) ...
Setting up libtiff-tools (4.0.3-12.3ubuntu2.1) ...
Setting up linux-image-extra-4.2.0-36-generic (4.2.0-36.42) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-36-generic /boot/vmlinuz-4.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-36-generic /boot/vmlinuz-4.2.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.2.0-36-generic /boot/vmlinuz-4.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.2.0-36-generic /boot/vmlinuz-4.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.2.0-36-generic /boot/vmlinuz-4.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.2.0-36-generic /boot/vmlinuz-4.2.0-36-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-36-generic
Found initrd image: /boot/initrd.img-4.2.0-36-generic
Found linux image: /boot/vmlinuz-4.2.0-30-generic
Found initrd image: /boot/initrd.img-4.2.0-30-generic
Found linux image: /boot/vmlinuz-4.2.0-27-generic
Found initrd image: /boot/initrd.img-4.2.0-27-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-generic (4.2.0.36.39) ...
Setting up linux-headers-4.2.0-36 (4.2.0-36.42) ...
Setting up linux-headers-4.2.0-36-generic (4.2.0-36.42) ...
Setting up linux-headers-generic (4.2.0.36.39) ...
Setting up linux-generic (4.2.0.36.39) ...
Setting up linux-libc-dev:amd64 (4.2.0-36.42) ...
Setting up network-manager (1.0.4-0ubuntu5.3) ...
Setting up php-pear (5.6.11+dfsg-1ubuntu3.3) ...
Installing new version of config file /etc/pear/pear.conf ...
Setting up php5 (5.6.11+dfsg-1ubuntu3.3) ...
Setting up poppler-utils (0.33.0-0ubuntu3.1) ...
Setting up python-pip (1.5.6-7ubuntu1.2) ...
Setting up simple-scan (3.18.2-0ubuntu1) ...
Setting up ssh-askpass-gnome (1:6.9p1-2ubuntu0.2) ...
Setting up thermald (1.4.3-5ubuntu1) ...
Installing new version of config file /etc/thermald/thermal-conf.xml ...
Setting up thunderbird (1:38.8.0+build1-0ubuntu0.15.10.1) ...
Setting up thunderbird-locale-en (1:38.8.0+build1-0ubuntu0.15.10.1) ...
Setting up thunderbird-gnome-support (1:38.8.0+build1-0ubuntu0.15.10.1) ...
Setting up thunderbird-locale-en-us (1:38.8.0+build1-0ubuntu0.15.10.1) ...
Setting up xserver-xorg-video-openchrome (1:0.3.3-1ubuntu1.1) ...
Setting up oxideqt-codecs-extra:amd64 (1.14.9-0ubuntu0.15.10.1) ...
Setting up liboxideqtcore0:amd64 (1.14.9-0ubuntu0.15.10.1) ...
Setting up liboxideqtquick0:amd64 (1.14.9-0ubuntu0.15.10.1) ...
Setting up liboxideqt-qmlplugin:amd64 (1.14.9-0ubuntu0.15.10.1) ...
Processing triggers for libc-bin (2.21-0ubuntu4.1) ...
dj@Blackbox:~$ 

```
now that step caused the system to shut down so had to restart and correct an issue as you can see

```


sudo apt -f install
dj@Blackbox:~$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.2.0-27 linux-headers-4.2.0-27-generic
  linux-image-4.2.0-27-generic linux-image-extra-4.2.0-27-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
dj@Blackbox:~$ 

```


```


sudo dpkg -C

``` post the results if there are any errors.
[INDENT][INDENT]'bout all we can do
[/INDENT]
[/INDENT]

cheers

---

### Post by Bashing-om on 2016-05-23
stockpimp;

```

uname -r

```

Post back the results:
```

apt-cache policy openjdk-8-jre openjdk-8-jre-headless

```

The GPG key for Google we will get back to .

[INDENT][INDENT]not too shabby
[/INDENT][/INDENT]

---

### Post by stockpimp on 2016-05-23
> **Bashing-om said:**
> stockpimp;

```

uname -r

```

Post back the results:
```

apt-cache policy openjdk-8-jre openjdk-8-jre-headless

```

The GPG key for Google we will get back to .
[INDENT][INDENT]not too shabby
[/INDENT]
[/INDENT]


```

dj@Blackbox:~$ apt-cache policy openjdk-8-jre openjdk-8-jre-headless
openjdk-8-jre:
  Installed: 8u66-b17-1
  Candidate: 8u91-b14-0ubuntu4~15.10.1
  Version table:
     8u91-b14-0ubuntu4~15.10.1 0
        500 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ wily-security/universe amd64 Packages
 *** 8u66-b17-1 0
        100 /var/lib/dpkg/status
     8u66-b01-5 0
        500 http://ca.archive.ubuntu.com/ubuntu/ wily/universe amd64 Packages
openjdk-8-jre-headless:
  Installed: 8u66-b17-1
  Candidate: 8u91-b14-0ubuntu4~15.10.1
  Version table:
     8u91-b14-0ubuntu4~15.10.1 0
        500 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ wily-security/universe amd64 Packages
 *** 8u66-b17-1 0
        100 /var/lib/dpkg/status
     8u66-b01-5 0
        500 http://ca.archive.ubuntu.com/ubuntu/ wily/universe amd64 Packages
dj@Blackbox:~$ 

```

---

### Post by Bashing-om on 2016-05-23
stockpimp; K;

Let's try the less invasive:
```

sudo apt install --reinstall openjdk-8-jre-headless openjdk-8-jre

```

getting the Package Manager happy .

[INDENT][INDENT]one must observe the proprieties
[/INDENT][/INDENT]

---

### Post by stockpimp on 2016-05-23
> **Bashing-om said:**
> stockpimp; K;

Let's try the less invasive:
```

sudo apt install --reinstall openjdk-8-jre-headless openjdk-8-jre

```

getting the Package Manager happy .[INDENT][INDENT]one must observe the proprieties
[/INDENT]
[/INDENT]


```

dj@Blackbox:~$ apt-cache policy openjdk-8-jre openjdk-8-jre-headless
openjdk-8-jre:
  Installed: 8u66-b17-1
  Candidate: 8u91-b14-0ubuntu4~15.10.1
  Version table:
     8u91-b14-0ubuntu4~15.10.1 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) wily-updates/universe amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) wily-security/universe amd64 Packages
 *** 8u66-b17-1 0
        100 /var/lib/dpkg/status
     8u66-b01-5 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) wily/universe amd64 Packages
openjdk-8-jre-headless:
  Installed: 8u66-b17-1
  Candidate: 8u91-b14-0ubuntu4~15.10.1
  Version table:
     8u91-b14-0ubuntu4~15.10.1 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) wily-updates/universe amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) wily-security/universe amd64 Packages
 *** 8u66-b17-1 0
        100 /var/lib/dpkg/status
     8u66-b01-5 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) wily/universe amd64 Packages
dj@Blackbox:~$ sudo apt install --reinstall openjdk-8-jre-headless openjdk-8-jre[sudo] password for dj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.2.0-27 linux-headers-4.2.0-27-generic
  linux-image-4.2.0-27-generic linux-image-extra-4.2.0-27-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  icedtea-8-plugin openjdk-8-jre-jamvm fonts-ipafont-gothic
  fonts-ipafont-mincho ttf-wqy-microhei ttf-wqy-zenhei fonts-indic
The following packages will be REMOVED:
  oracle-java8-installer oracle-java8-set-default
The following packages will be upgraded:
  openjdk-8-jre openjdk-8-jre-headless
2 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 26.9 MB of archives.
After this operation, 124 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) wily-updates/universe openjdk-8-jre amd64 8u91-b14-0ubuntu4~15.10.1 [69.8 kB]
Get:2 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) wily-updates/universe openjdk-8-jre-headless amd64 8u91-b14-0ubuntu4~15.10.1 [26.9 MB]
Fetched 26.9 MB in 14s (1,814 kB/s)                                            
(Reading database ... 301895 files and directories currently installed.)
Removing oracle-java8-set-default (8u72+8u71arm-1~webupd8~0) ...
Removing oracle-java8-installer (8u72+8u71arm-1~webupd8~0) ...
update-alternatives: removing manually selected alternative - switching appletviewer to auto mode
update-alternatives: removing manually selected alternative - switching extcheck to auto mode
update-alternatives: removing manually selected alternative - switching idlj to auto mode
update-alternatives: removing manually selected alternative - switching jar to auto mode
update-alternatives: removing manually selected alternative - switching jarsigner to auto mode
update-alternatives: removing manually selected alternative - switching javac to auto mode
update-alternatives: removing manually selected alternative - switching javadoc to auto mode
update-alternatives: removing manually selected alternative - switching javafxpackager to auto mode
update-alternatives: removing manually selected alternative - switching javah to auto mode
update-alternatives: removing manually selected alternative - switching javap to auto mode
update-alternatives: removing manually selected alternative - switching javapackager to auto mode
update-alternatives: removing manually selected alternative - switching jcmd to auto mode
update-alternatives: removing manually selected alternative - switching jconsole to auto mode
update-alternatives: removing manually selected alternative - switching jdb to auto mode
update-alternatives: removing manually selected alternative - switching jdeps to auto mode
update-alternatives: removing manually selected alternative - switching jhat to auto mode
update-alternatives: removing manually selected alternative - switching jinfo to auto mode
update-alternatives: removing manually selected alternative - switching jmap to auto mode
update-alternatives: removing manually selected alternative - switching jmc to auto mode
update-alternatives: removing manually selected alternative - switching jps to auto mode
update-alternatives: removing manually selected alternative - switching jrunscript to auto mode
update-alternatives: removing manually selected alternative - switching jsadebugd to auto mode
update-alternatives: removing manually selected alternative - switching jstack to auto mode
update-alternatives: removing manually selected alternative - switching jstat to auto mode
update-alternatives: removing manually selected alternative - switching jstatd to auto mode
update-alternatives: removing manually selected alternative - switching jvisualvm to auto mode
update-alternatives: removing manually selected alternative - switching native2ascii to auto mode
update-alternatives: removing manually selected alternative - switching rmic to auto mode
update-alternatives: removing manually selected alternative - switching schemagen to auto mode
update-alternatives: removing manually selected alternative - switching serialver to auto mode
update-alternatives: removing manually selected alternative - switching wsgen to auto mode
update-alternatives: removing manually selected alternative - switching wsimport to auto mode
update-alternatives: removing manually selected alternative - switching xjc to auto mode
update-alternatives: removing manually selected alternative - switching jexec to auto mode
update-alternatives: using /usr/lib/jvm/java-8-openjdk-amd64/jre/lib/jexec to provide /usr/bin/jexec (jexec) in auto mode
update-alternatives: removing manually selected alternative - switching java to auto mode
update-alternatives: using /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java to provide /usr/bin/java (java) in auto mode
update-alternatives: removing manually selected alternative - switching mozilla-javaplugin.so to auto mode
Processing triggers for gnome-menus (3.13.3-6ubuntu1) ...
Processing triggers for bamfdaemon (0.5.2~bzr0+15.10.20150627.1-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for shared-mime-info (1.3-1) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
(Reading database ... 301871 files and directories currently installed.)
Preparing to unpack .../openjdk-8-jre_8u91-b14-0ubuntu4~15.10.1_amd64.deb ...
Unpacking openjdk-8-jre:amd64 (8u91-b14-0ubuntu4~15.10.1) over (8u66-b17-1) ...
Preparing to unpack .../openjdk-8-jre-headless_8u91-b14-0ubuntu4~15.10.1_amd64.deb ...
Unpacking openjdk-8-jre-headless:amd64 (8u91-b14-0ubuntu4~15.10.1) over (8u66-b17-1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu1) ...
Processing triggers for bamfdaemon (0.5.2~bzr0+15.10.20150627.1-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Setting up openjdk-8-jre-headless:amd64 (8u91-b14-0ubuntu4~15.10.1) ...
Installing new version of config file /etc/java-8-openjdk/jvm-amd64.cfg ...
Installing new version of config file /etc/java-8-openjdk/security/blacklisted.certs ...
Installing new version of config file /etc/java-8-openjdk/security/java.security ...
Setting up openjdk-8-jre:amd64 (8u91-b14-0ubuntu4~15.10.1) ...
Processing triggers for libc-bin (2.21-0ubuntu4.1) ...
dj@Blackbox:~$ 

```

how's that look?

---

### Post by Bashing-om on 2016-05-23
stockpimp; Welp ...

Looks good to me ..

And now a new 'look' :
```

sudo apt update
sudo apt upgrade
sudo apt -f install

```

maybe all we have here is the GPG signing key to now deal with ?

[INDENT][INDENT]slowly
[INDENT][INDENT][INDENT]a step at the time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by stockpimp on 2016-05-23
How's that

```

dj@Blackbox:~$ sudo apt update
[sudo] password for dj: 
Ign http://dl.google.com stable InRelease
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://archive.canonical.com wily InRelease                                
Get:1 http://security.ubuntu.com wily-security InRelease [65.9 kB]             
Hit http://ca.archive.ubuntu.com wily InRelease                                
Get:2 http://ca.archive.ubuntu.com wily-updates InRelease [65.9 kB]            
Ign http://dl.google.com stable/main Translation-en_CA                         
Ign http://dl.google.com stable/main Translation-en                            
Get:3 http://security.ubuntu.com wily-security/main Sources [49.0 kB]          
Get:4 http://security.ubuntu.com wily-security/restricted Sources [2,854 B]    
Hit http://ca.archive.ubuntu.com wily-backports InRelease                      
Hit http://archive.canonical.com wily/partner Sources                          
Get:5 http://security.ubuntu.com wily-security/universe Sources [12.2 kB]      
Hit http://archive.canonical.com wily/partner amd64 Packages                   
Get:6 http://security.ubuntu.com wily-security/multiverse Sources [2,789 B]    
Hit http://archive.canonical.com wily/partner i386 Packages                    
Get:7 http://security.ubuntu.com wily-security/main amd64 Packages [155 kB]    
Hit http://archive.canonical.com wily/partner Translation-en                  
Get:8 http://security.ubuntu.com wily-security/restricted amd64 Packages [10.9 kB]
Get:9 http://security.ubuntu.com wily-security/universe amd64 Packages [53.0 kB]
Get:10 http://security.ubuntu.com wily-security/multiverse amd64 Packages [6,256 B]
Get:11 http://security.ubuntu.com wily-security/main i386 Packages [152 kB]
Get:12 http://security.ubuntu.com wily-security/restricted i386 Packages [10.8 kB]
Get:13 http://security.ubuntu.com wily-security/universe i386 Packages [53.1 kB]
Get:14 http://security.ubuntu.com wily-security/multiverse i386 Packages [6,434 B]
Hit http://security.ubuntu.com wily-security/main Translation-en        
Hit http://security.ubuntu.com wily-security/multiverse Translation-en
Hit http://security.ubuntu.com wily-security/restricted Translation-en
Hit http://security.ubuntu.com wily-security/universe Translation-en 
Get:15 http://ca.archive.ubuntu.com wily-updates/main Sources [79.8 kB]
Get:16 http://ca.archive.ubuntu.com wily-updates/restricted Sources [3,741 B]
Get:17 http://ca.archive.ubuntu.com wily-updates/universe Sources [24.3 kB]
Get:18 http://ca.archive.ubuntu.com wily-updates/multiverse Sources [3,196 B]
Get:19 http://ca.archive.ubuntu.com wily-updates/main amd64 Packages [221 kB]
Get:20 http://ca.archive.ubuntu.com wily-updates/restricted amd64 Packages [13.3 kB]
Get:21 http://ca.archive.ubuntu.com wily-updates/universe amd64 Packages [96.5 kB]
Get:22 http://ca.archive.ubuntu.com wily-updates/multiverse amd64 Packages [6,256 B]
Get:23 http://ca.archive.ubuntu.com wily-updates/main i386 Packages [217 kB]
Get:24 http://ca.archive.ubuntu.com wily-updates/restricted i386 Packages [13.4 kB]
Get:25 http://ca.archive.ubuntu.com wily-updates/universe i386 Packages [94.0 kB]
Get:26 http://ca.archive.ubuntu.com wily-updates/multiverse i386 Packages [6,687 B]
Hit http://ca.archive.ubuntu.com wily-backports/restricted Sources             
Hit http://ca.archive.ubuntu.com wily-backports/multiverse Sources             
Hit http://ca.archive.ubuntu.com wily-backports/restricted amd64 Packages      
Hit http://ca.archive.ubuntu.com wily-backports/multiverse amd64 Packages      
Hit http://ca.archive.ubuntu.com wily-backports/restricted i386 Packages       
Hit http://ca.archive.ubuntu.com wily-backports/multiverse i386 Packages       
Hit http://ca.archive.ubuntu.com wily-backports/multiverse Translation-en      
Hit http://ca.archive.ubuntu.com wily-backports/restricted Translation-en      
Hit http://ca.archive.ubuntu.com wily/main Sources                             
Hit http://ca.archive.ubuntu.com wily/restricted Sources                       
Hit http://ca.archive.ubuntu.com wily/universe Sources                         
Hit http://ca.archive.ubuntu.com wily/multiverse Sources                       
Hit http://ca.archive.ubuntu.com wily/main amd64 Packages                      
Hit http://ca.archive.ubuntu.com wily/restricted amd64 Packages                
Hit http://ca.archive.ubuntu.com wily/universe amd64 Packages                  
Hit http://ca.archive.ubuntu.com wily/multiverse amd64 Packages                
Hit http://ca.archive.ubuntu.com wily/main i386 Packages                       
Hit http://ca.archive.ubuntu.com wily/restricted i386 Packages                 
Hit http://ca.archive.ubuntu.com wily/universe i386 Packages                   
Hit http://ca.archive.ubuntu.com wily/multiverse i386 Packages                 
Hit http://ca.archive.ubuntu.com wily/main Translation-en_CA                   
Hit http://ca.archive.ubuntu.com wily/main Translation-en                      
Hit http://ca.archive.ubuntu.com wily/multiverse Translation-en                
Hit http://ca.archive.ubuntu.com wily/restricted Translation-en                
Hit http://ca.archive.ubuntu.com wily/universe Translation-en_CA               
Hit http://ca.archive.ubuntu.com wily/universe Translation-en                  
Hit http://ca.archive.ubuntu.com wily-updates/main Translation-en              
Hit http://ca.archive.ubuntu.com wily-updates/multiverse Translation-en        
Hit http://ca.archive.ubuntu.com wily-updates/restricted Translation-en        
Hit http://ca.archive.ubuntu.com wily-updates/universe Translation-en          
Hit http://ca.archive.ubuntu.com wily-backports/main Sources                   
Hit http://ca.archive.ubuntu.com wily-backports/universe Sources               
Hit http://ca.archive.ubuntu.com wily-backports/main amd64 Packages            
Hit http://ca.archive.ubuntu.com wily-backports/universe amd64 Packages        
Hit http://ca.archive.ubuntu.com wily-backports/main i386 Packages             
Hit http://ca.archive.ubuntu.com wily-backports/universe i386 Packages         
Hit http://ca.archive.ubuntu.com wily-backports/main Translation-en            
Hit http://ca.archive.ubuntu.com wily-backports/universe Translation-en        
Fetched 1,425 kB in 12s (112 kB/s)                                             
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
dj@Blackbox:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following packages were automatically installed and are no longer required:
  linux-headers-4.2.0-27 linux-headers-4.2.0-27-generic
  linux-image-4.2.0-27-generic linux-image-extra-4.2.0-27-generic
Use 'apt-get autoremove' to remove them.
Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dj@Blackbox:~$ sudo apt =f install
E: Invalid operation =f
dj@Blackbox:~$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.2.0-27 linux-headers-4.2.0-27-generic
  linux-image-4.2.0-27-generic linux-image-extra-4.2.0-27-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dj@Blackbox:~$ 

```

---

### Post by Bashing-om on 2016-05-23
stockpimp; all hunky dory !

So, back to the original issue (again);

show:
```

df -h
df -i
uname -r
dpkg -l | grep linux-

```

[INDENT]cocking to be
[INDENT][INDENT]ready for action[/INDENT][/INDENT][/INDENT]

---

### Post by stockpimp on 2016-05-23
> **Bashing-om said:**
> stockpimp; all hunky dory !

So, back to the original issue (again);

show:
```

df -h
df -i
uname -r
dpkg -l | grep linux-

```
[INDENT]cocking to be[INDENT][INDENT]ready for action[/INDENT]
[/INDENT]
[/INDENT]


Alright.  here it is


```

dj@Blackbox:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.8G     0  3.8G   0% /dev
tmpfs           789M  9.6M  779M   2% /run
/dev/dm-1       909G  293G  570G  34% /
tmpfs           3.9G   12M  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda1       236M  190M   35M  85% /boot
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           789M   52K  789M   1% /run/user/1000
dj@Blackbox:~$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
udev             995929    568   995361    1% /dev
tmpfs           1008760    826  1007934    1% /run
/dev/dm-1      60514304 370170 60144134    1% /
tmpfs           1008760     17  1008743    1% /dev/shm
tmpfs           1008760      9  1008751    1% /run/lock
tmpfs           1008760     17  1008743    1% /sys/fs/cgroup
/dev/sda1         62248    317    61931    1% /boot
cgmfs           1008760     13  1008747    1% /run/cgmanager/fs
tmpfs           1008760     29  1008731    1% /run/user/1000
dj@Blackbox:~$ uname -r
4.2.0-30-generic
dj@Blackbox:~$ dpkg -l|grep linux
ii  console-setup-linux                                  1.108ubuntu9                               all          Linux specific part of console-setup
ii  libselinux1:amd64                                    2.3-2build1                                amd64        SELinux runtime shared libraries
ii  libselinux1:i386                                     2.3-2build1                                i386         SELinux runtime shared libraries
ii  libv4l-0:amd64                                       1.6.3-1                                    amd64        Collection of video4linux support libraries
ii  libv4lconvert0:amd64                                 1.6.3-1                                    amd64        Video4linux frame format conversion library
ii  linux-firmware                                       1.149.3                                    all          Firmware for Linux kernel drivers
ii  linux-generic                                        4.2.0.36.39                                amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.2.0-27                               4.2.0-27.32                                all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-27-generic                       4.2.0-27.32                                amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-30                               4.2.0-30.36                                all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-30-generic                       4.2.0-30.36                                amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-36                               4.2.0-36.42                                all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-36-generic                       4.2.0-36.42                                amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                                4.2.0.36.39                                amd64        Generic Linux kernel headers
rc  linux-image-3.19.0-15-generic                        3.19.0-15.15                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-20-generic                        3.19.0-20.20                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-21-generic                        3.19.0-21.21                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-22-generic                        3.19.0-22.22                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-27-generic                         4.2.0-27.32                                amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-30-generic                         4.2.0-30.36                                amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-36-generic                         4.2.0-36.42                                amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-15-generic                  3.19.0-15.15                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-20-generic                  3.19.0-20.20                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-21-generic                  3.19.0-21.21                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-22-generic                  3.19.0-22.22                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-27-generic                   4.2.0-27.32                                amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-30-generic                   4.2.0-30.36                                amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-36-generic                   4.2.0-36.42                                amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-generic                                  4.2.0.36.39                                amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                 4.2.0-36.42                                amd64        Linux Kernel Headers for development
ii  linux-sound-base                                     1.0.25+dfsg-0ubuntu5                       all          base package for ALSA and OSS sound systems
ii  pptp-linux                                           1.8.0-1                                    amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                             3:6.03+dfsg-8ubuntu2                       amd64        collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                                      3:6.03+dfsg-8ubuntu2                       all          collection of bootloaders (common)
ii  syslinux-legacy                                      2:3.63+dfsg-2ubuntu8                       amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                           2.26.2-6ubuntu3                            amd64        Miscellaneous system utilities
dj@Blackbox:~$ 


```

---

### Post by Bashing-om on 2016-05-23
stockpimp; K


Rebooot .. do you come back up on the 4.2.0-36 kernel ?
```

uname -r

```

If on the -36 kernel -------
I do not think it is going to run.....
But try:
```

sudo apt-get autoremove

```
If/when that fails we remove the old linux images manually .

[INDENT][INDENT]keep it as simple as possible
[/INDENT][/INDENT]

---

### Post by stockpimp on 2016-05-23
> **Bashing-om said:**
> stockpimp; K


Rebooot .. do you come back up on the 4.2.0-36 kernel ?
```

uname -r

```

If on the -36 kernel -------
I do not think it is going to run.....
But try:
```

sudo apt-get autoremove

```
If/when that fails we remove the old linux images manually .
[INDENT][INDENT]keep it as simple as possible
[/INDENT]
[/INDENT]


k.  that seemed to work and yes it was on that kernel

```

dj@Blackbox:~$ sudo apt-get autoremove
[sudo] password for dj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-4.2.0-27 linux-headers-4.2.0-27-generic
  linux-image-4.2.0-27-generic linux-image-extra-4.2.0-27-generic
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 287 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 301874 files and directories currently installed.)
Removing linux-headers-4.2.0-27-generic (4.2.0-27.32) ...
Removing linux-headers-4.2.0-27 (4.2.0-27.32) ...
Removing linux-image-extra-4.2.0-27-generic (4.2.0-27.32) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-27-generic /boot/vmlinuz-4.2.0-27-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-27-generic /boot/vmlinuz-4.2.0-27-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-27-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.2.0-27-generic /boot/vmlinuz-4.2.0-27-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.2.0-27-generic /boot/vmlinuz-4.2.0-27-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.2.0-27-generic /boot/vmlinuz-4.2.0-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.2.0-27-generic /boot/vmlinuz-4.2.0-27-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-36-generic
Found initrd image: /boot/initrd.img-4.2.0-36-generic
Found linux image: /boot/vmlinuz-4.2.0-30-generic
Found initrd image: /boot/initrd.img-4.2.0-30-generic
Found linux image: /boot/vmlinuz-4.2.0-27-generic
Found initrd image: /boot/initrd.img-4.2.0-27-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Removing linux-image-4.2.0-27-generic (4.2.0-27.32) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-27-generic /boot/vmlinuz-4.2.0-27-generic
update-initramfs: Deleting /boot/initrd.img-4.2.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-27-generic /boot/vmlinuz-4.2.0-27-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-36-generic
Found initrd image: /boot/initrd.img-4.2.0-36-generic
Found linux image: /boot/vmlinuz-4.2.0-30-generic
Found initrd image: /boot/initrd.img-4.2.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
dj@Blackbox:~$ 

```

---

### Post by Bashing-om on 2016-05-24
stockpimp; Well ..

Partly effective .. and better than I had expected . I do not see where the -22 image was removed .
Let's check and prepare to remove the -22 image:
Show me the output of:
```

dpkg -l | grep linux-

```

[INDENT][INDENT]good things do happen
[/INDENT][/INDENT]

---

### Post by stockpimp on 2016-05-24
> **Bashing-om said:**
> stockpimp; Well ..

Partly effective .. and better than I had expected . I do not see where the -22 image was removed .
Let's check and prepare to remove the -22 image:
Show me the output of:
```

dpkg -l | grep linux-

```
[INDENT][INDENT]good things do happen
[/INDENT]
[/INDENT]


```

dj@Blackbox:~$ dpkg -l | grep linux-
ii  linux-firmware                                       1.149.3                                    all          Firmware for Linux kernel drivers
ii  linux-generic                                        4.2.0.36.39                                amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.2.0-30                               4.2.0-30.36                                all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-30-generic                       4.2.0-30.36                                amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-36                               4.2.0-36.42                                all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-36-generic                       4.2.0-36.42                                amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                                4.2.0.36.39                                amd64        Generic Linux kernel headers
rc  linux-image-3.19.0-15-generic                        3.19.0-15.15                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-20-generic                        3.19.0-20.20                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-21-generic                        3.19.0-21.21                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-22-generic                        3.19.0-22.22                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-27-generic                         4.2.0-27.32                                amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-30-generic                         4.2.0-30.36                                amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-36-generic                         4.2.0-36.42                                amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-15-generic                  3.19.0-15.15                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-20-generic                  3.19.0-20.20                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-21-generic                  3.19.0-21.21                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-22-generic                  3.19.0-22.22                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-27-generic                   4.2.0-27.32                                amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-30-generic                   4.2.0-30.36                                amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-36-generic                   4.2.0-36.42                                amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-generic                                  4.2.0.36.39                                amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                 4.2.0-36.42                                amd64        Linux Kernel Headers for development
ii  linux-sound-base                                     1.0.25+dfsg-0ubuntu5                       all          base package for ALSA and OSS sound systems
ii  syslinux-common                                      3:6.03+dfsg-8ubuntu2                       all          collection of bootloaders (common)
ii  syslinux-legacy                                      2:3.63+dfsg-2ubuntu8                       amd64        Bootloader for Linux/i386 using MS-DOS floppies
dj@Blackbox:~$ 

```

---

### Post by Bashing-om on 2016-05-24
stockpimp; Ho Kay;

Run:
```

sudo dpkg -P linux-image-3.19.0-22-generic
sudo dpkg -P linux-image-extra-3.19.0-22-generic
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

And now verify that:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot
dpkg -l | grep linux-

```
are all the same same, nothing added to any one .... and nothing taken away .


And then tell me;
[INDENT][INDENT]all is finer than a frog's hair
[/INDENT][/INDENT]

---

### Post by stockpimp on 2016-05-24
first one was an issue?

dj@Blackbox:~$ sudo dpkg -P linux-image-3.19.0-22-generic
[sudo] password for dj: 
dpkg: dependency problems prevent removal of linux-image-3.19.0-22-generic:
 linux-image-extra-3.19.0-22-generic depends on linux-image-3.19.0-22-generic.

dpkg: error processing package linux-image-3.19.0-22-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.19.0-22-generic
dj@Blackbox:~$

---

### Post by Bashing-om on 2016-05-24
stockpimp; Ouch .

Well .. that just says I am tired and my think'n was backwards ./.. maybe ??

try as :
```

sudo dpkg -P linux-image-extra-3.19.0-22-generic
sudo dpkg -P linux-image-3.19.0-22-generic

```

carry on ?

---

### Post by stockpimp on 2016-05-24
k.  got this from the first three commands and I will try the following now


```

dj@Blackbox:~$ sudo dpkg -P linux-image-extra-3.19.0-22-generic
[sudo] password for dj: 
(Reading database ... 270652 files and directories currently installed.)
Removing linux-image-extra-3.19.0-22-generic (3.19.0-22.22) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-36-generic
Found initrd image: /boot/initrd.img-4.2.0-36-generic
Found linux image: /boot/vmlinuz-4.2.0-30-generic
Found initrd image: /boot/initrd.img-4.2.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.19.0-22-generic (3.19.0-22.22) ...
dj@Blackbox:~$ sudo dpkg -P linux-image-3.19.0-22-generic
(Reading database ... 266419 files and directories currently installed.)
Removing linux-image-3.19.0-22-generic (3.19.0-22.22) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-36-generic
Found initrd image: /boot/initrd.img-4.2.0-36-generic
Found linux image: /boot/vmlinuz-4.2.0-30-generic
Found initrd image: /boot/initrd.img-4.2.0-30-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.19.0-22-generic (3.19.0-22.22) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
dj@Blackbox:~$ dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
(Reading database ... 265428 files and directories currently installed.)
Removing account-plugin-windows-live (0.12+15.04.20150415.1-0ubuntu2) ...
Purging configuration files for account-plugin-windows-live (0.12+15.04.20150415.1-0ubuntu2) ...
Removing at (3.1.16-1ubuntu1) ...
Purging configuration files for at (3.1.16-1ubuntu1) ...
Removing flashplugin-installer (11.2.202.577ubuntu0.15.10.1) ...
Purging configuration files for flashplugin-installer (11.2.202.577ubuntu0.15.10.1) ...
Removing lib32z1 (1:1.2.8.dfsg-2ubuntu1) ...
Purging configuration files for lib32z1 (1:1.2.8.dfsg-2ubuntu1) ...
Removing libabw-0.1-1 (0.1.0-2) ...
Purging configuration files for libabw-0.1-1 (0.1.0-2) ...
Removing libapt-inst1.5:amd64 (1.0.9.7ubuntu4.2) ...
Purging configuration files for libapt-inst1.5:amd64 (1.0.9.7ubuntu4.2) ...
Removing libapt-pkg4.12:amd64 (1.0.9.7ubuntu4.2) ...
Purging configuration files for libapt-pkg4.12:amd64 (1.0.9.7ubuntu4.2) ...
Removing libaqbanking34 (5.4.3beta-2) ...
Purging configuration files for libaqbanking34 (5.4.3beta-2) ...
Removing libatkmm-1.6-1:amd64 (2.22.7-2.1) ...
Purging configuration files for libatkmm-1.6-1:amd64 (2.22.7-2.1) ...
Removing libavcodec56:amd64 (6:11.2-1) ...
Purging configuration files for libavcodec56:amd64 (6:11.2-1) ...
Removing libavdevice55:amd64 (6:11.2-1) ...
Purging configuration files for libavdevice55:amd64 (6:11.2-1) ...
Removing libavformat56:amd64 (6:11.2-1) ...
Purging configuration files for libavformat56:amd64 (6:11.2-1) ...
Removing libavresample2:amd64 (6:11.2-1) ...
Purging configuration files for libavresample2:amd64 (6:11.2-1) ...
Removing libavutil54:amd64 (6:11.2-1) ...
Purging configuration files for libavutil54:amd64 (6:11.2-1) ...
Removing libboost-date-time1.55.0:amd64 (1.55.0+dfsg-3ubuntu2) ...
Purging configuration files for libboost-date-time1.55.0:amd64 (1.55.0+dfsg-3ubuntu2) ...
Removing libboost-filesystem1.55.0:amd64 (1.55.0+dfsg-3ubuntu2) ...
Purging configuration files for libboost-filesystem1.55.0:amd64 (1.55.0+dfsg-3ubuntu2) ...
Removing libboost-iostreams1.55.0:amd64 (1.55.0+dfsg-3ubuntu2) ...
Purging configuration files for libboost-iostreams1.55.0:amd64 (1.55.0+dfsg-3ubuntu2) ...
Removing libboost-system1.55.0:amd64 (1.55.0+dfsg-3ubuntu2) ...
Purging configuration files for libboost-system1.55.0:amd64 (1.55.0+dfsg-3ubuntu2) ...
Removing libc6-i386 (2.21-0ubuntu4) ...
Purging configuration files for libc6-i386 (2.21-0ubuntu4) ...
Removing libcairomm-1.0-1:amd64 (1.11.2-0ubuntu1) ...
Purging configuration files for libcairomm-1.0-1:amd64 (1.11.2-0ubuntu1) ...
Removing libcamel-1.2-49 (3.12.11-0ubuntu1.15.04.1) ...
Purging configuration files for libcamel-1.2-49 (3.12.11-0ubuntu1.15.04.1) ...
Removing libcdr-0.1-1 (0.1.0-3) ...
Purging configuration files for libcdr-0.1-1 (0.1.0-3) ...
Removing libclucene-contribs1:amd64 (2.3.3.4-4build1) ...
Purging configuration files for libclucene-contribs1:amd64 (2.3.3.4-4build1) ...
Removing libclucene-core1:amd64 (2.3.3.4-4build1) ...
Purging configuration files for libclucene-core1:amd64 (2.3.3.4-4build1) ...
Removing libcmis-0.5-5 (0.5.0-1ubuntu1) ...
Purging configuration files for libcmis-0.5-5 (0.5.0-1ubuntu1) ...
Removing libcolumbus1:amd64 (1.1.0+14.04.20140325.3-0ubuntu3) ...
Purging configuration files for libcolumbus1:amd64 (1.1.0+14.04.20140325.3-0ubuntu3) ...
Removing libdirac-encoder0:amd64 (1.0.2-7.1) ...
Purging configuration files for libdirac-encoder0:amd64 (1.0.2-7.1) ...
Removing libdouble-conversion1:amd64 (2.0.1-1) ...
Purging configuration files for libdouble-conversion1:amd64 (2.0.1-1) ...
Removing libebackend-1.2-7 (3.12.11-0ubuntu1.15.04.1) ...
Purging configuration files for libebackend-1.2-7 (3.12.11-0ubuntu1.15.04.1) ...
Removing libebook-1.2-14 (3.12.11-0ubuntu1.15.04.1) ...
Purging configuration files for libebook-1.2-14 (3.12.11-0ubuntu1.15.04.1) ...
Removing libebook-contacts-1.2-0 (3.12.11-0ubuntu1.15.04.1) ...
Purging configuration files for libebook-contacts-1.2-0 (3.12.11-0ubuntu1.15.04.1) ...
Removing libecal-1.2-16 (3.12.11-0ubuntu1.15.04.1) ...
Purging configuration files for libecal-1.2-16 (3.12.11-0ubuntu1.15.04.1) ...
Removing libedata-book-1.2-20 (3.12.11-0ubuntu1.15.04.1) ...
Purging configuration files for libedata-book-1.2-20 (3.12.11-0ubuntu1.15.04.1) ...
Removing libedata-cal-1.2-23 (3.12.11-0ubuntu1.15.04.1) ...
Purging configuration files for libedata-cal-1.2-23 (3.12.11-0ubuntu1.15.04.1) ...
Removing libedataserver-1.2-18 (3.12.11-0ubuntu1.15.04.1) ...
Purging configuration files for libedataserver-1.2-18 (3.12.11-0ubuntu1.15.04.1) ...
Removing libexiv2-13:amd64 (0.24-4.1) ...
Purging configuration files for libexiv2-13:amd64 (0.24-4.1) ...
Removing libfarstream-0.2-2:amd64 (0.2.4-1ubuntu1) ...
Purging configuration files for libfarstream-0.2-2:amd64 (0.2.4-1ubuntu1) ...
Removing libgdata19 (0.16.1-1) ...
Purging configuration files for libgdata19 (0.16.1-1) ...
Removing libgegl-0.2-0:amd64 (0.2.0-7ubuntu1) ...
Purging configuration files for libgegl-0.2-0:amd64 (0.2.0-7ubuntu1) ...
Removing libglibmm-2.4-1c2a:amd64 (2.42.0-1) ...
Purging configuration files for libglibmm-2.4-1c2a:amd64 (2.42.0-1) ...
Removing libgnome-bluetooth11 (3.8.2.1-0ubuntu12) ...
Purging configuration files for libgnome-bluetooth11 (3.8.2.1-0ubuntu12) ...
Removing libgnome-control-center1 (1:3.14.2-2ubuntu3) ...
Purging configuration files for libgnome-control-center1 (1:3.14.2-2ubuntu3) ...
Removing libgnomescan0 (0.6.2-1.1ubuntu4) ...
Purging configuration files for libgnomescan0 (0.6.2-1.1ubuntu4) ...
Removing libgphoto2-port10:amd64 (2.5.4-1.1ubuntu1) ...
Purging configuration files for libgphoto2-port10:amd64 (2.5.4-1.1ubuntu1) ...
Removing libgtkmm-2.4-1c2a:amd64 (1:2.24.4-1.1) ...
Purging configuration files for libgtkmm-2.4-1c2a:amd64 (1:2.24.4-1.1) ...
Removing libgtkmm-3.0-1:amd64 (3.14.0-1) ...
Purging configuration files for libgtkmm-3.0-1:amd64 (3.14.0-1) ...
Removing libhogweed2:amd64 (2.7.1-5) ...
Purging configuration files for libhogweed2:amd64 (2.7.1-5) ...
Removing libhogweed2:i386 (2.7.1-5) ...
Purging configuration files for libhogweed2:i386 (2.7.1-5) ...
Removing libicu52:amd64 (52.1-8ubuntu0.2) ...
Purging configuration files for libicu52:amd64 (52.1-8ubuntu0.2) ...
Removing libicu52:i386 (52.1-8ubuntu0.2) ...
Purging configuration files for libicu52:i386 (52.1-8ubuntu0.2) ...
Removing libilmbase6:amd64 (1.0.1-6.1) ...
Purging configuration files for libilmbase6:amd64 (1.0.1-6.1) ...
Removing libinput7:amd64 (0.10.0-1) ...
Purging configuration files for libinput7:amd64 (0.10.0-1) ...
Removing libjsoncpp0:amd64 (0.6.0~rc2-3.1ubuntu1) ...
Purging configuration files for libjsoncpp0:amd64 (0.6.0~rc2-3.1ubuntu1) ...
Removing libkf5kcmutils5:amd64 (5.15.0-0ubuntu1) ...
Purging configuration files for libkf5kcmutils5:amd64 (5.15.0-0ubuntu1) ...
Removing libktoblzcheck1c2a (1.47-1) ...
Purging configuration files for libktoblzcheck1c2a (1.47-1) ...
Removing libleveldb1:amd64 (1.17-1) ...
Purging configuration files for libleveldb1:amd64 (1.17-1) ...
Removing libllvm3.6:amd64 (1:3.6-2ubuntu1) ...
Purging configuration files for libllvm3.6:amd64 (1:3.6-2ubuntu1) ...
Removing libllvm3.6:i386 (1:3.6-2ubuntu1) ...
Purging configuration files for libllvm3.6:i386 (1:3.6-2ubuntu1) ...
Removing libmagick++-6.q16-5:amd64 (8:6.8.9.9-5) ...
Purging configuration files for libmagick++-6.q16-5:amd64 (8:6.8.9.9-5) ...
Removing libmediaart-1.0-0:amd64 (0.7.0-2) ...
Purging configuration files for libmediaart-1.0-0:amd64 (0.7.0-2) ...
Removing libmetacity-private2 (1:3.14.3-1ubuntu7) ...
Purging configuration files for libmetacity-private2 (1:3.14.3-1ubuntu7) ...
Removing libmirclient8:amd64 (0.12.1+15.04.20150324-0ubuntu1) ...
Purging configuration files for libmirclient8:amd64 (0.12.1+15.04.20150324-0ubuntu1) ...
Removing libmircommon3:amd64 (0.12.1+15.04.20150324-0ubuntu1) ...
Purging configuration files for libmircommon3:amd64 (0.12.1+15.04.20150324-0ubuntu1) ...
Removing libmirprotobuf0:amd64 (0.12.1+15.04.20150324-0ubuntu1) ...
Purging configuration files for libmirprotobuf0:amd64 (0.12.1+15.04.20150324-0ubuntu1) ...
Removing libmwaw-0.3-3 (0.3.4-1) ...
Purging configuration files for libmwaw-0.3-3 (0.3.4-1) ...
Removing libnettle4:amd64 (2.7.1-5) ...
Purging configuration files for libnettle4:amd64 (2.7.1-5) ...
Removing libnettle4:i386 (2.7.1-5) ...
Purging configuration files for libnettle4:i386 (2.7.1-5) ...
Removing libodfgen-0.1-1 (0.1.1-2) ...
Purging configuration files for libodfgen-0.1-1 (0.1.1-2) ...
Removing libopencv-calib3d2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Purging configuration files for libopencv-calib3d2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Removing libopencv-contrib2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Purging configuration files for libopencv-contrib2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Removing libopencv-core2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Purging configuration files for libopencv-core2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Removing libopencv-features2d2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Purging configuration files for libopencv-features2d2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Removing libopencv-flann2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Purging configuration files for libopencv-flann2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Removing libopencv-highgui2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Purging configuration files for libopencv-highgui2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Removing libopencv-imgproc2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Purging configuration files for libopencv-imgproc2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Removing libopencv-legacy2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Purging configuration files for libopencv-legacy2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Removing libopencv-ml2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Purging configuration files for libopencv-ml2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Removing libopencv-objdetect2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Purging configuration files for libopencv-objdetect2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Removing libopencv-video2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Purging configuration files for libopencv-video2.4:amd64 (2.4.9+dfsg-1ubuntu4) ...
Removing libopenexr6:amd64 (1.6.1-8) ...
Purging configuration files for libopenexr6:amd64 (1.6.1-8) ...
Removing libpangomm-1.4-1:amd64 (2.34.0-1.1) ...
Purging configuration files for libpangomm-1.4-1:amd64 (2.34.0-1.1) ...
Removing libplist2:amd64 (1.11-3build1) ...
Purging configuration files for libplist2:amd64 (1.11-3build1) ...
Removing libpoppler49:amd64 (0.30.0-0ubuntu1) ...
Purging configuration files for libpoppler49:amd64 (0.30.0-0ubuntu1) ...
Removing libprotobuf9:amd64 (2.6.1-1) ...
Purging configuration files for libprotobuf9:amd64 (2.6.1-1) ...
Removing libproxy1:amd64 (0.4.11-4ubuntu2) ...
Purging configuration files for libproxy1:amd64 (0.4.11-4ubuntu2) ...
Removing libqca2:amd64 (2.1.0-0ubuntu6) ...
Purging configuration files for libqca2:amd64 (2.1.0-0ubuntu6) ...
Removing libqpdf13:amd64 (5.1.2-3) ...
Purging configuration files for libqpdf13:amd64 (5.1.2-3) ...
Removing libqqwing2:amd64 (1.3.2-1) ...
Purging configuration files for libqqwing2:amd64 (1.3.2-1) ...
Removing librhythmbox-core8 (3.1-1ubuntu3) ...
Purging configuration files for librhythmbox-core8 (3.1-1ubuntu3) ...
Removing librpmbuild3 (4.11.3-1.1) ...
Purging configuration files for librpmbuild3 (4.11.3-1.1) ...
Removing librpmsign1 (4.11.3-1.1) ...
Purging configuration files for librpmsign1 (4.11.3-1.1) ...
Removing libsidplay1 (1.36.59-7) ...
Purging configuration files for libsidplay1 (1.36.59-7) ...
Removing libsigc++-2.0-0c2a:amd64 (2.4.0-1) ...
Purging configuration files for libsigc++-2.0-0c2a:amd64 (2.4.0-1) ...
Removing libsnappy1 (1.1.2-3ubuntu1) ...
Purging configuration files for libsnappy1 (1.1.2-3ubuntu1) ...
Removing libstreamanalyzer0 (0.7.8-1ubuntu2build1) ...
Purging configuration files for libstreamanalyzer0 (0.7.8-1ubuntu2build1) ...
Removing libstreams0 (0.7.8-1ubuntu2build1) ...
Purging configuration files for libstreams0 (0.7.8-1ubuntu2build1) ...
Removing libswscale3:amd64 (6:11.2-1) ...
Purging configuration files for libswscale3:amd64 (6:11.2-1) ...
Removing libtag1-vanilla:amd64 (1.9.1-2.1ubuntu1) ...
Purging configuration files for libtag1-vanilla:amd64 (1.9.1-2.1ubuntu1) ...
Removing libtinyxml2.6.2:amd64 (2.6.2-2) ...
Purging configuration files for libtinyxml2.6.2:amd64 (2.6.2-2) ...
Removing libvncclient0:amd64 (0.9.9+dfsg-6.1) ...
Purging configuration files for libvncclient0:amd64 (0.9.9+dfsg-6.1) ...
Removing libvpx1:amd64 (1.3.0-3ubuntu1) ...
Purging configuration files for libvpx1:amd64 (1.3.0-3ubuntu1) ...
Removing libwps-0.3-3 (0.3.0-2) ...
Purging configuration files for libwps-0.3-3 (0.3.0-2) ...
Removing libwxbase3.0-0:amd64 (3.0.2-1) ...
Purging configuration files for libwxbase3.0-0:amd64 (3.0.2-1) ...
Removing libwxgtk3.0-0:amd64 (3.0.2-1) ...
Purging configuration files for libwxgtk3.0-0:amd64 (3.0.2-1) ...
Removing libx264-142:amd64 (2:0.142.2495+git6a301b6-1ubuntu1) ...
Purging configuration files for libx264-142:amd64 (2:0.142.2495+git6a301b6-1ubuntu1) ...
Removing libxapian22 (1.2.19-1) ...
Purging configuration files for libxapian22 (1.2.19-1) ...
Removing libxcb-util0:amd64 (0.3.8-3) ...
Purging configuration files for libxcb-util0:amd64 (0.3.8-3) ...
Removing libxp6:amd64 (1:1.0.2-2) ...
Purging configuration files for libxp6:amd64 (1:1.0.2-2) ...
Removing linux-image-3.19.0-15-generic (3.19.0-15.15) ...
Purging configuration files for linux-image-3.19.0-15-generic (3.19.0-15.15) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
Removing linux-image-3.19.0-20-generic (3.19.0-20.20) ...
Purging configuration files for linux-image-3.19.0-20-generic (3.19.0-20.20) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-20-generic /boot/vmlinuz-3.19.0-20-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-20-generic /boot/vmlinuz-3.19.0-20-generic
Removing linux-image-3.19.0-21-generic (3.19.0-21.21) ...
Purging configuration files for linux-image-3.19.0-21-generic (3.19.0-21.21) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
Removing linux-image-4.2.0-27-generic (4.2.0-27.32) ...
Purging configuration files for linux-image-4.2.0-27-generic (4.2.0-27.32) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-27-generic /boot/vmlinuz-4.2.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-27-generic /boot/vmlinuz-4.2.0-27-generic
Removing linux-image-extra-3.19.0-15-generic (3.19.0-15.15) ...
Purging configuration files for linux-image-extra-3.19.0-15-generic (3.19.0-15.15) ...
Removing linux-image-extra-3.19.0-20-generic (3.19.0-20.20) ...
Purging configuration files for linux-image-extra-3.19.0-20-generic (3.19.0-20.20) ...
Removing linux-image-extra-3.19.0-21-generic (3.19.0-21.21) ...
Purging configuration files for linux-image-extra-3.19.0-21-generic (3.19.0-21.21) ...
Removing linux-image-extra-4.2.0-27-generic (4.2.0-27.32) ...
Purging configuration files for linux-image-extra-4.2.0-27-generic (4.2.0-27.32) ...
Removing lsb-core (4.1+Debian11ubuntu8) ...
Purging configuration files for lsb-core (4.1+Debian11ubuntu8) ...
Removing mir-client-platform-mesa2:amd64 (0.12.1+15.04.20150324-0ubuntu1) ...
Purging configuration files for mir-client-platform-mesa2:amd64 (0.12.1+15.04.20150324-0ubuntu1) ...
Removing oracle-java8-installer (8u72+8u71arm-1~webupd8~0) ...
Purging configuration files for oracle-java8-installer (8u72+8u71arm-1~webupd8~0) ...
Removing oracle-java8-set-default (8u72+8u71arm-1~webupd8~0) ...
Purging configuration files for oracle-java8-set-default (8u72+8u71arm-1~webupd8~0) ...
Removing overlay-scrollbar-gtk3:amd64 (0.2.16+r359+15.04.20150319-0ubuntu1) ...
Purging configuration files for overlay-scrollbar-gtk3:amd64 (0.2.16+r359+15.04.20150319-0ubuntu1) ...
Removing rpm (4.11.3-1.1) ...
Purging configuration files for rpm (4.11.3-1.1) ...
Removing webaccounts-extension-common (0.5-0ubuntu4.15.04.1) ...
Purging configuration files for webaccounts-extension-common (0.5-0ubuntu4.15.04.1) ...
Removing xfonts-mathml (6ubuntu1) ...
Purging configuration files for xfonts-mathml (6ubuntu1) ...
dj@Blackbox:~$ 

```

---

### Post by stockpimp on 2016-05-24
> **Bashing-om said:**
> stockpimp; Ho Kay;

Run:
```

sudo dpkg -P linux-image-3.19.0-22-generic
sudo dpkg -P linux-image-extra-3.19.0-22-generic
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

And now verify that:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot
dpkg -l | grep linux-

```
are all the same same, nothing added to any one .... and nothing taken away .


And then tell me;[INDENT][INDENT]all is finer than a frog's hair
[/INDENT]
[/INDENT]


here's the rest of it

```

dj@Blackbox:~$ ls -al /usr/src/
total 24
drwxr-xr-x  6 root root 4096 May 23 19:43 .
drwxr-xr-x 11 root root 4096 Feb 16 21:41 ..
drwxr-xr-x 24 root root 4096 Feb 27 10:00 linux-headers-4.2.0-30
drwxr-xr-x  7 root root 4096 Feb 27 10:01 linux-headers-4.2.0-30-generic
drwxr-xr-x 24 root root 4096 May 23 13:27 linux-headers-4.2.0-36
drwxr-xr-x  7 root root 4096 May 23 13:27 linux-headers-4.2.0-36-generic
dj@Blackbox:~$ ls -al /lib/modules/
total 16
drwxr-xr-x  4 root root 4096 May 23 23:07 .
drwxr-xr-x 26 root root 4096 Feb 16 21:56 ..
drwxr-xr-x  5 root root 4096 Feb 27 10:01 4.2.0-30-generic
drwxr-xr-x  5 root root 4096 May 23 13:28 4.2.0-36-generic
dj@Blackbox:~$ ls -al /boot
total 94396
drwxr-xr-x  4 root root     3072 May 23 23:07 .
drwxr-xr-x 23 root root     4096 May 23 13:25 ..
-rw-r--r--  1 root root  1312643 Feb 25 19:17 abi-4.2.0-30-generic
-rw-r--r--  1 root root  1313407 May 12 18:58 abi-4.2.0-36-generic
-rw-r--r--  1 root root   184888 Feb 25 19:17 config-4.2.0-30-generic
-rw-r--r--  1 root root   184888 May 12 18:58 config-4.2.0-36-generic
drwxr-xr-x  5 root root     1024 May 23 23:07 grub
-rw-r--r--  1 root root 35756432 May 23 12:24 initrd.img-4.2.0-30-generic
-rw-r--r--  1 root root 35811033 May 23 13:28 initrd.img-4.2.0-36-generic
drwx------  2 root root    12288 May 10  2015 lost+found
-rw-r--r--  1 root root   182704 Aug 27  2015 memtest86+.bin
-rw-r--r--  1 root root   184380 Aug 27  2015 memtest86+.elf
-rw-r--r--  1 root root   184840 Aug 27  2015 memtest86+_multiboot.bin
-rw-------  1 root root  3744565 Feb 25 19:17 System.map-4.2.0-30-generic
-rw-------  1 root root  3745958 May 12 18:58 System.map-4.2.0-36-generic
-rw-------  1 root root  6808720 Feb 25 19:17 vmlinuz-4.2.0-30-generic
-rw-------  1 root root  6830352 May 12 18:58 vmlinuz-4.2.0-36-generic
dj@Blackbox:~$ dpkg -l | grep linux-
ii  linux-firmware                                       1.149.3                                    all          Firmware for Linux kernel drivers
ii  linux-generic                                        4.2.0.36.39                                amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.2.0-30                               4.2.0-30.36                                all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-30-generic                       4.2.0-30.36                                amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-36                               4.2.0-36.42                                all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-36-generic                       4.2.0-36.42                                amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                                4.2.0.36.39                                amd64        Generic Linux kernel headers
ii  linux-image-4.2.0-30-generic                         4.2.0-30.36                                amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-36-generic                         4.2.0-36.42                                amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-30-generic                   4.2.0-30.36                                amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-36-generic                   4.2.0-36.42                                amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-generic                                  4.2.0.36.39                                amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                 4.2.0-36.42                                amd64        Linux Kernel Headers for development
ii  linux-sound-base                                     1.0.25+dfsg-0ubuntu5                       all          base package for ALSA and OSS sound systems
ii  syslinux-common                                      3:6.03+dfsg-8ubuntu2                       all          collection of bootloaders (common)
ii  syslinux-legacy                                      2:3.63+dfsg-2ubuntu8                       amd64        Bootloader for Linux/i386 using MS-DOS floppies
dj@Blackbox:~$ 


```

---

### Post by Bashing-om on 2016-05-24
stockpimp; Hey hey ...

Looks absolutely perfectly fine to me. You should be set to go now.

Lessons learned ? Keep the system updated .. and do the light housecleaning that is required. Install a new kernel .. remove the old ones once you are satisfied there is no problem with the new kernel ( autoremove) . If you do this then you avoid the hassle of expanding /boot.

At this point, you want to do away with the system cache, to gain some additional space .. all done and caught up ?
then:
```

sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean #To clear the cache
sudo apt update
sudo apt full-upgrade

```
which is all there is to that light house cleaning.

[INDENT][INDENT]the care and feeding
[INDENT][INDENT][INDENT]of your 'buntu
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by stockpimp on 2016-05-25
> **Bashing-om said:**
> stockpimp; Hey hey ...

Looks absolutely perfectly fine to me. You should be set to go now.

Lessons learned ? Keep the system updated .. and do the light housecleaning that is required. Install a new kernel .. remove the old ones once you are satisfied there is no problem with the new kernel ( autoremove) . If you do this then you avoid the hassle of expanding /boot.

At this point, you want to do away with the system cache, to gain some additional space .. all done and caught up ?
then:
```

sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean #To clear the cache
sudo apt update
sudo apt full-upgrade

```
which is all there is to that light house cleaning.
[INDENT][INDENT]the care and feeding[INDENT][INDENT][INDENT]of your 'buntu
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


```

dj@Blackbox:~$ sudo apt-get autoclean
[sudo] password for dj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del php5-pspell 5.6.11+dfsg-1ubuntu3.3 [8,182 B]
Del php5 5.6.11+dfsg-1ubuntu3.3 [1,298 B]
Del php5-gd 5.6.11+dfsg-1ubuntu3.3 [29.0 kB]
Del php5-intl 5.6.11+dfsg-1ubuntu3.3 [112 kB]
Del php5-common 5.6.11+dfsg-1ubuntu3.3 [482 kB]
Del php5-mysqlnd 5.6.11+dfsg-1ubuntu3.3 [141 kB]
Del libapache2-mod-php5 5.6.11+dfsg-1ubuntu3.3 [2,276 kB]
Del php5-cli 5.6.11+dfsg-1ubuntu3.3 [2,250 kB]
Del php5-sqlite 5.6.11+dfsg-1ubuntu3.3 [24.7 kB]
Del php-pear 5.6.11+dfsg-1ubuntu3.3 [268 kB]
Del php5-readline 5.6.11+dfsg-1ubuntu3.3 [13.2 kB]
dj@Blackbox:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-4.2.0-30 linux-headers-4.2.0-30-generic
  linux-image-4.2.0-30-generic linux-image-extra-4.2.0-30-generic
0 upgraded, 0 newly installed, 4 to remove and 18 not upgraded.
After this operation, 287 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 265416 files and directories currently installed.)
Removing linux-headers-4.2.0-30-generic (4.2.0-30.36) ...
Removing linux-headers-4.2.0-30 (4.2.0-30.36) ...
Removing linux-image-extra-4.2.0-30-generic (4.2.0-30.36) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-36-generic
Found initrd image: /boot/initrd.img-4.2.0-36-generic
Found linux image: /boot/vmlinuz-4.2.0-30-generic
Found initrd image: /boot/initrd.img-4.2.0-30-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Removing linux-image-4.2.0-30-generic (4.2.0-30.36) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
update-initramfs: Deleting /boot/initrd.img-4.2.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-36-generic
Found initrd image: /boot/initrd.img-4.2.0-36-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
dj@Blackbox:~$ sudo apt-get clean
dj@Blackbox:~$ sudo apt update
Ign http://dl.google.com stable InRelease
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://security.ubuntu.com wily-security InRelease                         
Hit http://ca.archive.ubuntu.com wily InRelease                                
Hit http://archive.canonical.com wily InRelease                                
Ign http://dl.google.com stable/main Translation-en_CA                         
Ign http://dl.google.com stable/main Translation-en                  
Hit http://ca.archive.ubuntu.com wily-updates InRelease              
Hit http://security.ubuntu.com wily-security/main Sources                      
Hit http://archive.canonical.com wily/partner Sources                 
Hit http://ca.archive.ubuntu.com wily-backports InRelease             
Hit http://security.ubuntu.com wily-security/restricted Sources                
Hit http://archive.canonical.com wily/partner amd64 Packages                   
Hit http://ca.archive.ubuntu.com wily/main Sources                             
Hit http://security.ubuntu.com wily-security/universe Sources                  
Hit http://archive.canonical.com wily/partner i386 Packages                    
Hit http://ca.archive.ubuntu.com wily/restricted Sources                       
Hit http://security.ubuntu.com wily-security/multiverse Sources                
Hit http://archive.canonical.com wily/partner Translation-en                   
Hit http://ca.archive.ubuntu.com wily/universe Sources                
Hit http://security.ubuntu.com wily-security/main amd64 Packages
Hit http://ca.archive.ubuntu.com wily/multiverse Sources      
Hit http://security.ubuntu.com wily-security/restricted amd64 Packages
Hit http://ca.archive.ubuntu.com wily/main amd64 Packages
Hit http://security.ubuntu.com wily-security/universe amd64 Packages
Hit http://ca.archive.ubuntu.com wily/restricted amd64 Packages
Hit http://security.ubuntu.com wily-security/multiverse amd64 Packages
Hit http://ca.archive.ubuntu.com wily/universe amd64 Packages  
Hit http://security.ubuntu.com wily-security/main i386 Packages
Hit http://ca.archive.ubuntu.com wily/multiverse amd64 Packages
Hit http://security.ubuntu.com wily-security/restricted i386 Packages
Hit http://ca.archive.ubuntu.com wily/main i386 Packages       
Hit http://security.ubuntu.com wily-security/universe i386 Packages
Hit http://security.ubuntu.com wily-security/multiverse i386 Packages
Hit http://ca.archive.ubuntu.com wily/restricted i386 Packages
Hit http://security.ubuntu.com wily-security/main Translation-en
Hit http://ca.archive.ubuntu.com wily/universe i386 Packages
Hit http://security.ubuntu.com wily-security/multiverse Translation-en
Hit http://ca.archive.ubuntu.com wily/multiverse i386 Packages     
Hit http://security.ubuntu.com wily-security/restricted Translation-en
Hit http://ca.archive.ubuntu.com wily/main Translation-en_CA   
Hit http://security.ubuntu.com wily-security/universe Translation-en 
Hit http://ca.archive.ubuntu.com wily/main Translation-en      
Hit http://ca.archive.ubuntu.com wily/multiverse Translation-en
Hit http://ca.archive.ubuntu.com wily/restricted Translation-en
Hit http://ca.archive.ubuntu.com wily/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com wily/universe Translation-en
Hit http://ca.archive.ubuntu.com wily-updates/main Sources
Hit http://ca.archive.ubuntu.com wily-updates/restricted Sources
Hit http://ca.archive.ubuntu.com wily-updates/universe Sources
Hit http://ca.archive.ubuntu.com wily-updates/multiverse Sources
Hit http://ca.archive.ubuntu.com wily-updates/main amd64 Packages
Hit http://ca.archive.ubuntu.com wily-updates/restricted amd64 Packages
Hit http://ca.archive.ubuntu.com wily-updates/universe amd64 Packages
Hit http://ca.archive.ubuntu.com wily-updates/multiverse amd64 Packages
Hit http://ca.archive.ubuntu.com wily-updates/main i386 Packages
Hit http://ca.archive.ubuntu.com wily-updates/restricted i386 Packages
Hit http://ca.archive.ubuntu.com wily-updates/universe i386 Packages
Hit http://ca.archive.ubuntu.com wily-updates/multiverse i386 Packages
Hit http://ca.archive.ubuntu.com wily-updates/main Translation-en
Hit http://ca.archive.ubuntu.com wily-updates/multiverse Translation-en
Hit http://ca.archive.ubuntu.com wily-updates/restricted Translation-en
Hit http://ca.archive.ubuntu.com wily-updates/universe Translation-en
Hit http://ca.archive.ubuntu.com wily-backports/main Sources
Hit http://ca.archive.ubuntu.com wily-backports/restricted Sources
Hit http://ca.archive.ubuntu.com wily-backports/universe Sources
Hit http://ca.archive.ubuntu.com wily-backports/multiverse Sources             
Hit http://ca.archive.ubuntu.com wily-backports/main amd64 Packages            
Hit http://ca.archive.ubuntu.com wily-backports/restricted amd64 Packages      
Hit http://ca.archive.ubuntu.com wily-backports/universe amd64 Packages        
Hit http://ca.archive.ubuntu.com wily-backports/multiverse amd64 Packages      
Hit http://ca.archive.ubuntu.com wily-backports/main i386 Packages             
Hit http://ca.archive.ubuntu.com wily-backports/restricted i386 Packages       
Hit http://ca.archive.ubuntu.com wily-backports/universe i386 Packages         
Hit http://ca.archive.ubuntu.com wily-backports/multiverse i386 Packages       
Hit http://ca.archive.ubuntu.com wily-backports/main Translation-en            
Hit http://ca.archive.ubuntu.com wily-backports/multiverse Translation-en      
Hit http://ca.archive.ubuntu.com wily-backports/restricted Translation-en      
Hit http://ca.archive.ubuntu.com wily-backports/universe Translation-en        
Reading package lists... Done                                                  
Building dependency tree       
Reading state information... Done
18 packages can be upgraded. Run 'apt list --upgradable' to see them.
dj@Blackbox:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libapache2-mod-php5 libc-bin libc-dev-bin libc6 libc6:i386 libc6-dbg
  libc6-dev multiarch-support php-pear php5 php5-cli php5-common php5-gd
  php5-intl php5-mysqlnd php5-pspell php5-readline php5-sqlite
18 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.2 MB of archives.
After this operation, 14.3 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main libc-dev-bin amd64 2.21-0ubuntu4.2 [68.6 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main libc6-dev amd64 2.21-0ubuntu4.2 [1,958 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main libc-bin amd64 2.21-0ubuntu4.2 [1,168 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main libc6-dbg amd64 2.21-0ubuntu4.2 [3,551 kB]
Get:5 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main libc6 i386 2.21-0ubuntu4.2 [4,054 kB]
Get:6 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main libc6 amd64 2.21-0ubuntu4.2 [4,756 kB]
Get:7 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main multiarch-support amd64 2.21-0ubuntu4.2 [7,180 B]
Get:8 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main php5-sqlite amd64 5.6.11+dfsg-1ubuntu3.4 [24.7 kB]
Get:9 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main php5-gd amd64 5.6.11+dfsg-1ubuntu3.4 [29.0 kB]
Get:10 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main php5-readline amd64 5.6.11+dfsg-1ubuntu3.4 [13.1 kB]
Get:11 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main php5-cli amd64 5.6.11+dfsg-1ubuntu3.4 [2,250 kB]
Get:12 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/universe php5-intl amd64 5.6.11+dfsg-1ubuntu3.4 [112 kB]
Get:13 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/universe php5-mysqlnd amd64 5.6.11+dfsg-1ubuntu3.4 [141 kB]
Get:14 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main php5-pspell amd64 5.6.11+dfsg-1ubuntu3.4 [8,162 B]
Get:15 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main libapache2-mod-php5 amd64 5.6.11+dfsg-1ubuntu3.4 [2,276 kB]
Get:16 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main php5-common amd64 5.6.11+dfsg-1ubuntu3.4 [481 kB]
Get:17 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main php-pear all 5.6.11+dfsg-1ubuntu3.4 [269 kB]
Get:18 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main php5 all 5.6.11+dfsg-1ubuntu3.4 [1,302 B]
Fetched 21.2 MB in 15s (1,362 kB/s)                                            
Preconfiguring packages ...
(Reading database ... 234195 files and directories currently installed.)
Preparing to unpack .../libc-dev-bin_2.21-0ubuntu4.2_amd64.deb ...
Unpacking libc-dev-bin (2.21-0ubuntu4.2) over (2.21-0ubuntu4.1) ...
Preparing to unpack .../libc6-dev_2.21-0ubuntu4.2_amd64.deb ...
Unpacking libc6-dev:amd64 (2.21-0ubuntu4.2) over (2.21-0ubuntu4.1) ...
Preparing to unpack .../libc-bin_2.21-0ubuntu4.2_amd64.deb ...
Unpacking libc-bin (2.21-0ubuntu4.2) over (2.21-0ubuntu4.1) ...
Processing triggers for man-db (2.7.4-1) ...
Setting up libc-bin (2.21-0ubuntu4.2) ...
(Reading database ... 234194 files and directories currently installed.)
Preparing to unpack .../libc6-dbg_2.21-0ubuntu4.2_amd64.deb ...
Unpacking libc6-dbg:amd64 (2.21-0ubuntu4.2) over (2.21-0ubuntu4.1) ...
Preparing to unpack .../libc6_2.21-0ubuntu4.2_amd64.deb ...
De-configuring libc6:i386 (2.21-0ubuntu4.1) ...
Unpacking libc6:amd64 (2.21-0ubuntu4.2) over (2.21-0ubuntu4.1) ...
Preparing to unpack .../libc6_2.21-0ubuntu4.2_i386.deb ...
Unpacking libc6:i386 (2.21-0ubuntu4.2) over (2.21-0ubuntu4.1) ...
Preparing to unpack .../multiarch-support_2.21-0ubuntu4.2_amd64.deb ...
Unpacking multiarch-support (2.21-0ubuntu4.2) over (2.21-0ubuntu4.1) ...
Setting up libc6:amd64 (2.21-0ubuntu4.2) ...
Setting up libc6:i386 (2.21-0ubuntu4.2) ...
Setting up multiarch-support (2.21-0ubuntu4.2) ...
Processing triggers for libc-bin (2.21-0ubuntu4.2) ...
(Reading database ... 234194 files and directories currently installed.)
Preparing to unpack .../php5-sqlite_5.6.11+dfsg-1ubuntu3.4_amd64.deb ...
Unpacking php5-sqlite (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Preparing to unpack .../php5-gd_5.6.11+dfsg-1ubuntu3.4_amd64.deb ...
Unpacking php5-gd (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Preparing to unpack .../php5-readline_5.6.11+dfsg-1ubuntu3.4_amd64.deb ...
Unpacking php5-readline (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Preparing to unpack .../php5-cli_5.6.11+dfsg-1ubuntu3.4_amd64.deb ...
Unpacking php5-cli (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Preparing to unpack .../php5-intl_5.6.11+dfsg-1ubuntu3.4_amd64.deb ...
Unpacking php5-intl (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Preparing to unpack .../php5-mysqlnd_5.6.11+dfsg-1ubuntu3.4_amd64.deb ...
Unpacking php5-mysqlnd (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Preparing to unpack .../php5-pspell_5.6.11+dfsg-1ubuntu3.4_amd64.deb ...
Unpacking php5-pspell (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Preparing to unpack .../libapache2-mod-php5_5.6.11+dfsg-1ubuntu3.4_amd64.deb ...
Unpacking libapache2-mod-php5 (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Preparing to unpack .../php5-common_5.6.11+dfsg-1ubuntu3.4_amd64.deb ...
Unpacking php5-common (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Preparing to unpack .../php-pear_5.6.11+dfsg-1ubuntu3.4_all.deb ...
Unpacking php-pear (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Preparing to unpack .../php5_5.6.11+dfsg-1ubuntu3.4_all.deb ...
Unpacking php5 (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Processing triggers for man-db (2.7.4-1) ...
Processing triggers for doc-base (0.10.6) ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Setting up libc-dev-bin (2.21-0ubuntu4.2) ...
Setting up libc6-dev:amd64 (2.21-0ubuntu4.2) ...
Setting up libc6-dbg:amd64 (2.21-0ubuntu4.2) ...
Setting up php5-common (5.6.11+dfsg-1ubuntu3.4) ...
Setting up php5-sqlite (5.6.11+dfsg-1ubuntu3.4) ...
Setting up php5-gd (5.6.11+dfsg-1ubuntu3.4) ...
Setting up php5-cli (5.6.11+dfsg-1ubuntu3.4) ...
Setting up php5-readline (5.6.11+dfsg-1ubuntu3.4) ...
Setting up php5-intl (5.6.11+dfsg-1ubuntu3.4) ...
Setting up php5-mysqlnd (5.6.11+dfsg-1ubuntu3.4) ...
Setting up php5-pspell (5.6.11+dfsg-1ubuntu3.4) ...
Setting up libapache2-mod-php5 (5.6.11+dfsg-1ubuntu3.4) ...
apache2_invoke php5: already enabled
Setting up php-pear (5.6.11+dfsg-1ubuntu3.4) ...
Installing new version of config file /etc/pear/pear.conf ...
Setting up php5 (5.6.11+dfsg-1ubuntu3.4) ...
dj@Blackbox:~$ 

```

---

### Post by stockpimp on 2016-05-25
> **stockpimp said:**
> ```

dj@Blackbox:~$ sudo apt-get autoclean
[sudo] password for dj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del php5-pspell 5.6.11+dfsg-1ubuntu3.3 [8,182 B]
Del php5 5.6.11+dfsg-1ubuntu3.3 [1,298 B]
Del php5-gd 5.6.11+dfsg-1ubuntu3.3 [29.0 kB]
Del php5-intl 5.6.11+dfsg-1ubuntu3.3 [112 kB]
Del php5-common 5.6.11+dfsg-1ubuntu3.3 [482 kB]
Del php5-mysqlnd 5.6.11+dfsg-1ubuntu3.3 [141 kB]
Del libapache2-mod-php5 5.6.11+dfsg-1ubuntu3.3 [2,276 kB]
Del php5-cli 5.6.11+dfsg-1ubuntu3.3 [2,250 kB]
Del php5-sqlite 5.6.11+dfsg-1ubuntu3.3 [24.7 kB]
Del php-pear 5.6.11+dfsg-1ubuntu3.3 [268 kB]
Del php5-readline 5.6.11+dfsg-1ubuntu3.3 [13.2 kB]
dj@Blackbox:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-4.2.0-30 linux-headers-4.2.0-30-generic
  linux-image-4.2.0-30-generic linux-image-extra-4.2.0-30-generic
0 upgraded, 0 newly installed, 4 to remove and 18 not upgraded.
After this operation, 287 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 265416 files and directories currently installed.)
Removing linux-headers-4.2.0-30-generic (4.2.0-30.36) ...
Removing linux-headers-4.2.0-30 (4.2.0-30.36) ...
Removing linux-image-extra-4.2.0-30-generic (4.2.0-30.36) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-36-generic
Found initrd image: /boot/initrd.img-4.2.0-36-generic
Found linux image: /boot/vmlinuz-4.2.0-30-generic
Found initrd image: /boot/initrd.img-4.2.0-30-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Removing linux-image-4.2.0-30-generic (4.2.0-30.36) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
update-initramfs: Deleting /boot/initrd.img-4.2.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-36-generic
Found initrd image: /boot/initrd.img-4.2.0-36-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
dj@Blackbox:~$ sudo apt-get clean
dj@Blackbox:~$ sudo apt update
Ign http://dl.google.com stable InRelease
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://security.ubuntu.com wily-security InRelease                         
Hit http://ca.archive.ubuntu.com wily InRelease                                
Hit http://archive.canonical.com wily InRelease                                
Ign http://dl.google.com stable/main Translation-en_CA                         
Ign http://dl.google.com stable/main Translation-en                  
Hit http://ca.archive.ubuntu.com wily-updates InRelease              
Hit http://security.ubuntu.com wily-security/main Sources                      
Hit http://archive.canonical.com wily/partner Sources                 
Hit http://ca.archive.ubuntu.com wily-backports InRelease             
Hit http://security.ubuntu.com wily-security/restricted Sources                
Hit http://archive.canonical.com wily/partner amd64 Packages                   
Hit http://ca.archive.ubuntu.com wily/main Sources                             
Hit http://security.ubuntu.com wily-security/universe Sources                  
Hit http://archive.canonical.com wily/partner i386 Packages                    
Hit http://ca.archive.ubuntu.com wily/restricted Sources                       
Hit http://security.ubuntu.com wily-security/multiverse Sources                
Hit http://archive.canonical.com wily/partner Translation-en                   
Hit http://ca.archive.ubuntu.com wily/universe Sources                
Hit http://security.ubuntu.com wily-security/main amd64 Packages
Hit http://ca.archive.ubuntu.com wily/multiverse Sources      
Hit http://security.ubuntu.com wily-security/restricted amd64 Packages
Hit http://ca.archive.ubuntu.com wily/main amd64 Packages
Hit http://security.ubuntu.com wily-security/universe amd64 Packages
Hit http://ca.archive.ubuntu.com wily/restricted amd64 Packages
Hit http://security.ubuntu.com wily-security/multiverse amd64 Packages
Hit http://ca.archive.ubuntu.com wily/universe amd64 Packages  
Hit http://security.ubuntu.com wily-security/main i386 Packages
Hit http://ca.archive.ubuntu.com wily/multiverse amd64 Packages
Hit http://security.ubuntu.com wily-security/restricted i386 Packages
Hit http://ca.archive.ubuntu.com wily/main i386 Packages       
Hit http://security.ubuntu.com wily-security/universe i386 Packages
Hit http://security.ubuntu.com wily-security/multiverse i386 Packages
Hit http://ca.archive.ubuntu.com wily/restricted i386 Packages
Hit http://security.ubuntu.com wily-security/main Translation-en
Hit http://ca.archive.ubuntu.com wily/universe i386 Packages
Hit http://security.ubuntu.com wily-security/multiverse Translation-en
Hit http://ca.archive.ubuntu.com wily/multiverse i386 Packages     
Hit http://security.ubuntu.com wily-security/restricted Translation-en
Hit http://ca.archive.ubuntu.com wily/main Translation-en_CA   
Hit http://security.ubuntu.com wily-security/universe Translation-en 
Hit http://ca.archive.ubuntu.com wily/main Translation-en      
Hit http://ca.archive.ubuntu.com wily/multiverse Translation-en
Hit http://ca.archive.ubuntu.com wily/restricted Translation-en
Hit http://ca.archive.ubuntu.com wily/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com wily/universe Translation-en
Hit http://ca.archive.ubuntu.com wily-updates/main Sources
Hit http://ca.archive.ubuntu.com wily-updates/restricted Sources
Hit http://ca.archive.ubuntu.com wily-updates/universe Sources
Hit http://ca.archive.ubuntu.com wily-updates/multiverse Sources
Hit http://ca.archive.ubuntu.com wily-updates/main amd64 Packages
Hit http://ca.archive.ubuntu.com wily-updates/restricted amd64 Packages
Hit http://ca.archive.ubuntu.com wily-updates/universe amd64 Packages
Hit http://ca.archive.ubuntu.com wily-updates/multiverse amd64 Packages
Hit http://ca.archive.ubuntu.com wily-updates/main i386 Packages
Hit http://ca.archive.ubuntu.com wily-updates/restricted i386 Packages
Hit http://ca.archive.ubuntu.com wily-updates/universe i386 Packages
Hit http://ca.archive.ubuntu.com wily-updates/multiverse i386 Packages
Hit http://ca.archive.ubuntu.com wily-updates/main Translation-en
Hit http://ca.archive.ubuntu.com wily-updates/multiverse Translation-en
Hit http://ca.archive.ubuntu.com wily-updates/restricted Translation-en
Hit http://ca.archive.ubuntu.com wily-updates/universe Translation-en
Hit http://ca.archive.ubuntu.com wily-backports/main Sources
Hit http://ca.archive.ubuntu.com wily-backports/restricted Sources
Hit http://ca.archive.ubuntu.com wily-backports/universe Sources
Hit http://ca.archive.ubuntu.com wily-backports/multiverse Sources             
Hit http://ca.archive.ubuntu.com wily-backports/main amd64 Packages            
Hit http://ca.archive.ubuntu.com wily-backports/restricted amd64 Packages      
Hit http://ca.archive.ubuntu.com wily-backports/universe amd64 Packages        
Hit http://ca.archive.ubuntu.com wily-backports/multiverse amd64 Packages      
Hit http://ca.archive.ubuntu.com wily-backports/main i386 Packages             
Hit http://ca.archive.ubuntu.com wily-backports/restricted i386 Packages       
Hit http://ca.archive.ubuntu.com wily-backports/universe i386 Packages         
Hit http://ca.archive.ubuntu.com wily-backports/multiverse i386 Packages       
Hit http://ca.archive.ubuntu.com wily-backports/main Translation-en            
Hit http://ca.archive.ubuntu.com wily-backports/multiverse Translation-en      
Hit http://ca.archive.ubuntu.com wily-backports/restricted Translation-en      
Hit http://ca.archive.ubuntu.com wily-backports/universe Translation-en        
Reading package lists... Done                                                  
Building dependency tree       
Reading state information... Done
18 packages can be upgraded. Run 'apt list --upgradable' to see them.
dj@Blackbox:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libapache2-mod-php5 libc-bin libc-dev-bin libc6 libc6:i386 libc6-dbg
  libc6-dev multiarch-support php-pear php5 php5-cli php5-common php5-gd
  php5-intl php5-mysqlnd php5-pspell php5-readline php5-sqlite
18 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.2 MB of archives.
After this operation, 14.3 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main libc-dev-bin amd64 2.21-0ubuntu4.2 [68.6 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main libc6-dev amd64 2.21-0ubuntu4.2 [1,958 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main libc-bin amd64 2.21-0ubuntu4.2 [1,168 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main libc6-dbg amd64 2.21-0ubuntu4.2 [3,551 kB]
Get:5 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main libc6 i386 2.21-0ubuntu4.2 [4,054 kB]
Get:6 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main libc6 amd64 2.21-0ubuntu4.2 [4,756 kB]
Get:7 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main multiarch-support amd64 2.21-0ubuntu4.2 [7,180 B]
Get:8 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main php5-sqlite amd64 5.6.11+dfsg-1ubuntu3.4 [24.7 kB]
Get:9 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main php5-gd amd64 5.6.11+dfsg-1ubuntu3.4 [29.0 kB]
Get:10 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main php5-readline amd64 5.6.11+dfsg-1ubuntu3.4 [13.1 kB]
Get:11 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main php5-cli amd64 5.6.11+dfsg-1ubuntu3.4 [2,250 kB]
Get:12 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/universe php5-intl amd64 5.6.11+dfsg-1ubuntu3.4 [112 kB]
Get:13 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/universe php5-mysqlnd amd64 5.6.11+dfsg-1ubuntu3.4 [141 kB]
Get:14 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main php5-pspell amd64 5.6.11+dfsg-1ubuntu3.4 [8,162 B]
Get:15 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main libapache2-mod-php5 amd64 5.6.11+dfsg-1ubuntu3.4 [2,276 kB]
Get:16 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main php5-common amd64 5.6.11+dfsg-1ubuntu3.4 [481 kB]
Get:17 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main php-pear all 5.6.11+dfsg-1ubuntu3.4 [269 kB]
Get:18 http://ca.archive.ubuntu.com/ubuntu/ wily-updates/main php5 all 5.6.11+dfsg-1ubuntu3.4 [1,302 B]
Fetched 21.2 MB in 15s (1,362 kB/s)                                            
Preconfiguring packages ...
(Reading database ... 234195 files and directories currently installed.)
Preparing to unpack .../libc-dev-bin_2.21-0ubuntu4.2_amd64.deb ...
Unpacking libc-dev-bin (2.21-0ubuntu4.2) over (2.21-0ubuntu4.1) ...
Preparing to unpack .../libc6-dev_2.21-0ubuntu4.2_amd64.deb ...
Unpacking libc6-dev:amd64 (2.21-0ubuntu4.2) over (2.21-0ubuntu4.1) ...
Preparing to unpack .../libc-bin_2.21-0ubuntu4.2_amd64.deb ...
Unpacking libc-bin (2.21-0ubuntu4.2) over (2.21-0ubuntu4.1) ...
Processing triggers for man-db (2.7.4-1) ...
Setting up libc-bin (2.21-0ubuntu4.2) ...
(Reading database ... 234194 files and directories currently installed.)
Preparing to unpack .../libc6-dbg_2.21-0ubuntu4.2_amd64.deb ...
Unpacking libc6-dbg:amd64 (2.21-0ubuntu4.2) over (2.21-0ubuntu4.1) ...
Preparing to unpack .../libc6_2.21-0ubuntu4.2_amd64.deb ...
De-configuring libc6:i386 (2.21-0ubuntu4.1) ...
Unpacking libc6:amd64 (2.21-0ubuntu4.2) over (2.21-0ubuntu4.1) ...
Preparing to unpack .../libc6_2.21-0ubuntu4.2_i386.deb ...
Unpacking libc6:i386 (2.21-0ubuntu4.2) over (2.21-0ubuntu4.1) ...
Preparing to unpack .../multiarch-support_2.21-0ubuntu4.2_amd64.deb ...
Unpacking multiarch-support (2.21-0ubuntu4.2) over (2.21-0ubuntu4.1) ...
Setting up libc6:amd64 (2.21-0ubuntu4.2) ...
Setting up libc6:i386 (2.21-0ubuntu4.2) ...
Setting up multiarch-support (2.21-0ubuntu4.2) ...
Processing triggers for libc-bin (2.21-0ubuntu4.2) ...
(Reading database ... 234194 files and directories currently installed.)
Preparing to unpack .../php5-sqlite_5.6.11+dfsg-1ubuntu3.4_amd64.deb ...
Unpacking php5-sqlite (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Preparing to unpack .../php5-gd_5.6.11+dfsg-1ubuntu3.4_amd64.deb ...
Unpacking php5-gd (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Preparing to unpack .../php5-readline_5.6.11+dfsg-1ubuntu3.4_amd64.deb ...
Unpacking php5-readline (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Preparing to unpack .../php5-cli_5.6.11+dfsg-1ubuntu3.4_amd64.deb ...
Unpacking php5-cli (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Preparing to unpack .../php5-intl_5.6.11+dfsg-1ubuntu3.4_amd64.deb ...
Unpacking php5-intl (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Preparing to unpack .../php5-mysqlnd_5.6.11+dfsg-1ubuntu3.4_amd64.deb ...
Unpacking php5-mysqlnd (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Preparing to unpack .../php5-pspell_5.6.11+dfsg-1ubuntu3.4_amd64.deb ...
Unpacking php5-pspell (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Preparing to unpack .../libapache2-mod-php5_5.6.11+dfsg-1ubuntu3.4_amd64.deb ...
Unpacking libapache2-mod-php5 (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Preparing to unpack .../php5-common_5.6.11+dfsg-1ubuntu3.4_amd64.deb ...
Unpacking php5-common (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Preparing to unpack .../php-pear_5.6.11+dfsg-1ubuntu3.4_all.deb ...
Unpacking php-pear (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Preparing to unpack .../php5_5.6.11+dfsg-1ubuntu3.4_all.deb ...
Unpacking php5 (5.6.11+dfsg-1ubuntu3.4) over (5.6.11+dfsg-1ubuntu3.3) ...
Processing triggers for man-db (2.7.4-1) ...
Processing triggers for doc-base (0.10.6) ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Setting up libc-dev-bin (2.21-0ubuntu4.2) ...
Setting up libc6-dev:amd64 (2.21-0ubuntu4.2) ...
Setting up libc6-dbg:amd64 (2.21-0ubuntu4.2) ...
Setting up php5-common (5.6.11+dfsg-1ubuntu3.4) ...
Setting up php5-sqlite (5.6.11+dfsg-1ubuntu3.4) ...
Setting up php5-gd (5.6.11+dfsg-1ubuntu3.4) ...
Setting up php5-cli (5.6.11+dfsg-1ubuntu3.4) ...
Setting up php5-readline (5.6.11+dfsg-1ubuntu3.4) ...
Setting up php5-intl (5.6.11+dfsg-1ubuntu3.4) ...
Setting up php5-mysqlnd (5.6.11+dfsg-1ubuntu3.4) ...
Setting up php5-pspell (5.6.11+dfsg-1ubuntu3.4) ...
Setting up libapache2-mod-php5 (5.6.11+dfsg-1ubuntu3.4) ...
apache2_invoke php5: already enabled
Setting up php-pear (5.6.11+dfsg-1ubuntu3.4) ...
Installing new version of config file /etc/pear/pear.conf ...
Setting up php5 (5.6.11+dfsg-1ubuntu3.4) ...
dj@Blackbox:~$ 

```


For some reason my post prior to this wasn't "posted"... at any rate HUGE thanx for your help.... lost with out you guys.  Your efforts are greatly appreciated!  As far as the future goes... I need to run the above scripts every now and then to keep the drive cleaned up... is that the take away here?  Short of a re-install this is the best way to deal with the small drive partition?

---

### Post by Bashing-om on 2016-05-25
stockpimp; Yeah ..

every once in a while .. clean up the system with the commands given above.

Did you note what the package manager told you ? We need to address these notices.
Is grub happy now after all the updates have been done ?
I do not know why 'autoremove' would remove the -30 kernel .. ??? It is supposed - in a undisturbed state - to leave a backup kernel . Maybe we want to re-install that backup kernel ??
```

ls -al /vmlinuz*
ls -al /initrd.img*
ls -al /boot

```

As a side thing .. IF you are not going to directly manage your system to keep it updated .. there are procedures to insure " unattended upgrades" take place . A subject for a different thread.

Again, Happy to help .

[INDENT][INDENT]the care and feeding of your 'buntu
[/INDENT][/INDENT]

---

### Post by stockpimp on 2016-05-25
> **Bashing-om said:**
> stockpimp; Yeah ..

every once in a while .. clean up the system with the commands given above.

Did you note what the package manager told you ? We need to address these notices.
Is grub happy now after all the updates have been done ?
I do not know why 'autoremove' would remove the -30 kernel .. ??? It is supposed - in a undisturbed state - to leave a backup kernel . Maybe we want to re-install that backup kernel ??
```

ls -al /vmlinuz*
ls -al /initrd.img*
ls -al /boot

```

As a side thing .. IF you are not going to directly manage your system to keep it updated .. there are procedures to insure " unattended upgrades" take place . A subject for a different thread.

Again, Happy to help .[INDENT][INDENT]the care and feeding of your 'buntu
[/INDENT]
[/INDENT]


k.  I'm happy to do what needs to be done to keep the system running properly so auto is good or manual if needed, what ever works.  Here's the output from the last set of commands.

```

dj@Blackbox:~$ ls -al /vmlinuz*
lrwxrwxrwx 1 root root 29 May 23 13:25 /vmlinuz -> boot/vmlinuz-4.2.0-36-generic
dj@Blackbox:~$ ls -al /initrd.img*
lrwxrwxrwx 1 root root 32 May 23 13:25 /initrd.img -> boot/initrd.img-4.2.0-36-generic
dj@Blackbox:~$ ls -al /boot
total 47519
drwxr-xr-x  4 root root     3072 May 25 07:57 .
drwxr-xr-x 23 root root     4096 May 25 07:57 ..
-rw-r--r--  1 root root  1313407 May 12 18:58 abi-4.2.0-36-generic
-rw-r--r--  1 root root   184888 May 12 18:58 config-4.2.0-36-generic
drwxr-xr-x  5 root root     1024 May 25 07:57 grub
-rw-r--r--  1 root root 35811033 May 23 13:28 initrd.img-4.2.0-36-generic
drwx------  2 root root    12288 May 10  2015 lost+found
-rw-r--r--  1 root root   182704 Aug 27  2015 memtest86+.bin
-rw-r--r--  1 root root   184380 Aug 27  2015 memtest86+.elf
-rw-r--r--  1 root root   184840 Aug 27  2015 memtest86+_multiboot.bin
-rw-------  1 root root  3745958 May 12 18:58 System.map-4.2.0-36-generic
-rw-------  1 root root  6830352 May 12 18:58 vmlinuz-4.2.0-36-generic
dj@Blackbox:~$ 

```

---

### Post by Bashing-om on 2016-05-25
stockpimp; Welp ..

As suspected .. no backup kernel .. That in and of it's self is not bad ,, so long as there is no problem in the present booting kernel.
Ya want to install a back up kernel ??.. Or leave well enough alone and await the installation of a new kernel ?

Me, I am a hands on type of guy .. and as curious as a cat .. I want to know what is taking place on my system and I do mange it manually.
Each time I boot up I check for updates;
I run a real tight install and I MUST be aware of disk space usage;
 .. I watch my usage like a hawk . Linux starts getting cranky when space usage exceeds 90% or so ... depending on some variables.

[INDENT][INDENT]it it ain't broke
[INDENT][INDENT][INDENT]don't fix it ??
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by stockpimp on 2016-05-25
well... if that's advisable let's do it.  My system has been running like crap for weeks now including intermittent shut downs for no apparent reason etc etc.  It's REAL slow to update some browser pages as well.  I assumed it was due to the os being out of date or drive / memory space but wasn't sure what to do about it as I couldn't update the os.

---

### Post by Bashing-om on 2016-05-25
stockpimp; Youch !


Let's just let things lie for now, as the system is stable and see what results in the next kernel upgrade.

> **stockpimp said:**
> well... if that's advisable let's do it.  My system has been running like crap for weeks now including intermittent shut downs for no apparent reason etc etc.  It's REAL slow to update some browser pages as well.  I assumed it was due to the os being out of date or drive / memory space but wasn't sure what to do about it as I couldn't update the os.

Now those are horses of different colors.
Most depends on ram .. how much is installed .. and what is using it ? Is swap being pounded ? .. in that case got enough swap space allocated ?
terminal commands:
```

free -m
top

```
'q' to quit out of 'top' .

If it is browser related .. might try clearing the browser cache and cookies .. see if that makes a difference .. maybe remove the profiles ?

And when you do not know, and there is no apparent reason for problems .. one then starts reading the log files . Once the kernel is up nothing happens on the system that is not logged somewhere. Most of the system logs are in the /var/log/ directory and make for interesting reading . One "should" become familiar with the logs while the system is in a happy state to facilitate recognizing a problem .


Then there is
[INDENT][INDENT]which way did he go George
[/INDENT][/INDENT]

---

### Post by stockpimp on 2016-05-25
> **Bashing-om said:**
> stockpimp; Youch !


Let's just let things lie for now, as the system is stable and see what results in the next kernel upgrade.



Now those are horses of different colors.
Most depends on ram .. how much is installed .. and what is using it ? Is swap being pounded ? .. in that case got enough swap space allocated ?
terminal commands:
```

free -m
top

```
'q' to quit out of 'top' .

If it is browser related .. might try clearing the browser cache and cookies .. see if that makes a difference .. maybe remove the profiles ?

And when you do not know, and there is no apparent reason for problems .. one then starts reading the log files . Once the kernel is up nothing happens on the system that is not logged somewhere. Most of the system logs are in the /var/log/ directory and make for interesting reading . One "should" become familiar with the logs while the system is in a happy state to facilitate recognizing a problem .


Then there is[INDENT][INDENT]which way did he go George
[/INDENT]
[/INDENT]

I'll try clearing cookies etc any way but here are the results

```

dj@Blackbox:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7880       2309       5570         34        112        654
-/+ buffers/cache:       1543       6337
Swap:         8087          0       8087
dj@Blackbox:~$ top

top - 16:10:31 up  2:36,  2 users,  load average: 1.00, 1.07, 1.04
Tasks: 256 total,   2 running, 254 sleeping,   0 stopped,   0 zombie
%Cpu(s):  9.7 us,  1.3 sy,  0.0 ni, 88.8 id,  0.3 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   8070052 total,  2362360 used,  5707692 free,   114940 buffers
KiB Swap:  8282108 total,        0 used,  8282108 free.   670580 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 3075 dj        20   0 1100908 328336  69184 S  58.8  4.1  16:18.35 plugin-con+ 
 2277 dj        20   0 1782016 694736 110312 S  23.2  8.6  53:57.28 firefox     
 1052 root      20   0  249280  49620  28488 S   3.0  0.6   4:05.48 Xorg        
 1859 dj         9 -11  573948  11956   8764 S   2.7  0.1   0:47.49 pulseaudio  
 3299 dj        20   0  645564  34208  27184 R   2.3  0.4   0:00.55 gnome-term+ 
 1709 dj        20   0 1513804 115108  68872 S   1.7  1.4   1:43.31 compiz      
  384 root      20   0       0      0      0 S   0.3  0.0   0:01.57 kworker/u1+ 
 1688 dj        20   0  351352   6708   5464 S   0.3  0.1   0:00.54 ibus-daemon 
 1950 dj        20   0 1472600  54364  41372 S   0.3  0.7   0:03.78 nautilus    
    1 root      20   0  185212   5760   3940 S   0.0  0.1   0:01.26 systemd     
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd    
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ksoftirqd/0 
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:+ 
    7 root      20   0       0      0      0 S   0.0  0.0   0:11.01 rcu_sched   
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh      
    9 root      20   0       0      0      0 S   0.0  0.0   0:02.32 rcuos/0     
   10 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/0    


```

---

### Post by Bashing-om on 2016-05-25
stockpimp; Welp;

For sure not physical memory or swap as any problem .

But, but but !!
> 
 load average: 1.00, 1.07, 1.04

in top, says you may have a memory management issue ; depending: how many CPU processors  are in this mother board ?
```

grep 'model name' /proc/cpuinfo | wc -l

```

maybe;
[INDENT]gonna have to look elsewhere
[/INDENT]

---

### Post by stockpimp on 2016-05-25
8 processors.

---

### Post by Bashing-om on 2016-05-25
stockpimp; K;

Then :
> 
load average: 1.00, 1.07, 1.04

is not much of a load at all for 8 processors !

Let's mark this thread solved. and if there is still a problem with the browser, open a new thread . 

leastways
[INDENT][INDENT]that is what I think
[/INDENT][/INDENT]

---

### Post by stockpimp on 2016-05-26
> **Bashing-om said:**
> stockpimp; K;

Then :

is not much of a load at all for 8 processors !

Let's mark this thread solved. and if there is still a problem with the browser, open a new thread . 

leastways[INDENT][INDENT]that is what I think
[/INDENT]
[/INDENT]


Sure.  As I say I think it may / might be a ram issue or some such.  I have an insane amount of "power" for the VERY minor requirements I need meeting so it confuses me when the performance is so poor.  I thought perhaps it was the update issue but I guess we will see.  Thank-you again for your help!

---

### Post by Bashing-om on 2016-05-26
stockpimp; Welp;

With no more load than is in that system. with those specs it should be flying !
Let's close this thread:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And open a new one to gain a wider audience to those who have the knowledge .

I am always willing to help - and learn . At this time we have drifted far off the topic of this thread . I will look for this new thread and we continue this with the aid of those better informed than I.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

