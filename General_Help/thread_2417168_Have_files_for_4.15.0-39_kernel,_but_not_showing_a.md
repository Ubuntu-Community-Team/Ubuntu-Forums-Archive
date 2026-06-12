---
title: "Have files for 4.15.0-39 kernel, but not showing as installed?"
date: 2019-04-22
forum: General Help
---

### Post by sremick on 2019-04-22
So I'm trying to free up space on /boot. Silly me allowed Ubuntu to use a recommended size for /boot when I first installed, so I'm stuck with 240MB. I currently only have 130MB free.... so it's "only" 43% used, but it's enough to break many updates that complain about insufficient space.

As I use whole-disk encryption, I don't have an easy path to address this. So I continue to try and limp by.

Right now I show abi-4.15.0-39-generic, config-4.15.0-39-generic, retpoline-4.15.0-39-generic and System.map-4.15.0-39-generic but according to uname -r I'm using 4.15.0-38 (I have files for it as well). Neither Synaptic nor apt list 4.15.0-39... is it safe to just delete these files?

---

### Post by Impavidus on 2019-04-22
You're supposed to be on 4.15.0-47. -38 and -39 are old. The thing to do is to make room by cleanly removing old packages, then installing the latest kernel from the repositories.

Let's see what exactly is installed according to the package manager and what files are there.```
ls /boot
dpkg --list | grep linux-
```

---

### Post by sremick on 2019-04-22
> **Impavidus said:**
> You're supposed to be on 4.15.0-47. -38 and -39 are old. The thing to do is to make room by cleanly removing old packages, then installing the latest kernel from the repositories.

Let's see what exactly is installed according to the package manager and what files are there.
```

$ ls /boot
abi-4.15.0-38-generic     config-4.15.0-39-generic      lost+found      memtest86+_multiboot.bin     System.map-4.15.0-38-generic
abi-4.15.0-39-generic     grub                          memtest86+.bin  retpoline-4.15.0-38-generic  System.map-4.15.0-39-generic
config-4.15.0-38-generic  initrd.img-4.15.0-38-generic  memtest86+.elf  retpoline-4.15.0-39-generic  vmlinuz-4.15.0-38-generic

```

```
dpkg --list | grep linux-
ii  binutils-x86-64-linux-gnu                    2.31.1-6ubuntu1                            amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                                   4.5ubuntu1                                 all          Linux image base package
ii  linux-cloud-tools-4.15.0-38                  4.15.0-38.41                               amd64        Linux kernel version specific cloud tools for version 4.15.0-38
ii  linux-cloud-tools-4.15.0-38-generic          4.15.0-38.41                               amd64        Linux kernel version specific cloud tools for version 4.15.0-38
ii  linux-cloud-tools-4.18.0-10                  4.18.0-10.11                               amd64        Linux kernel version specific cloud tools for version 4.18.0-10
ii  linux-cloud-tools-4.18.0-10-generic          4.18.0-10.11                               amd64        Linux kernel version specific cloud tools for version 4.18.0-10
ii  linux-cloud-tools-common                     4.18.0-10.11                               all          Linux kernel version specific cloud tools for version 4.18.0
ii  linux-cloud-tools-generic                    4.18.0.10.11                               amd64        Generic Linux kernel cloud tools
ii  linux-firmware                               1.175                                      all          Firmware for Linux kernel drivers
ii  linux-headers-4.15.0-38                      4.15.0-38.41                               all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-38-generic              4.15.0-38.41                               amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-26-generic                3.19.0-26.28                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-4.15.0-38-generic                4.15.0-38.41                               amd64        Signed kernel image generic
rc  linux-image-unsigned-4.15.0-39-generic       4.15.0-39.42                               amd64        Linux kernel image for version 4.15.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                         4.18.0-10.11                               amd64        Linux Kernel Headers for development
rc  linux-modules-4.15.0-32-generic              4.15.0-32.35                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-33-generic              4.15.0-33.36                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-34-generic              4.15.0-34.37                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-36-generic              4.15.0-36.39                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-38-generic              4.15.0-38.41                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-39-generic              4.15.0-39.42                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-34-generic        4.15.0-34.37                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-38-generic        4.15.0-38.41                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-signed-image-3.19.0-26-generic         3.19.0-26.28                               amd64        Signed kernel image generic
ii  linux-sound-base                             1.0.25+dfsg-0ubuntu5                       all          base package for ALSA and OSS sound systems
ii  linux-tools-4.15.0-38                        4.15.0-38.41                               amd64        Linux kernel version specific tools for version 4.15.0-38
ii  linux-tools-4.15.0-38-generic                4.15.0-38.41                               amd64        Linux kernel version specific tools for version 4.15.0-38
ii  linux-tools-4.18.0-10                        4.18.0-10.11                               amd64        Linux kernel version specific tools for version 4.18.0-10
ii  linux-tools-4.18.0-10-generic                4.18.0-10.11                               amd64        Linux kernel version specific tools for version 4.18.0-10
ii  linux-tools-common                           4.18.0-10.11                               all          Linux kernel version specific tools for version 4.18.0
ii  linux-tools-generic                          4.18.0.10.11                               amd64        Generic Linux kernel tools
ii  syslinux-common                              3:6.04~git20171011.af7e95c3+dfsg1-4ubuntu1 all          collection of bootloaders (common)
ii  syslinux-legacy                              2:3.63+dfsg-2ubuntu9                       amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

That certainly raises a lot of questions for this newbie, but I await your guidance.

---

### Post by Impavidus on 2019-04-23
Not all parts of kernel 4.15.0-39 have been installed, but fortunately your package manager is in a consistent state. Furthermore, the metapackage that is supposed to draw in new kernels as they are released is missing.

First of all, can you confirm you're currently running kernel 4.15.0-38? Use```
uname -r
``` to check. I think you do, as that's the only kernel that's fully installed. If not, don't do anything else and report back.

You've got some leftovers from old kernels. They are reported with status rc, meaning "removed, configuration files remaining". They don't actually take any disk space, but you can purge them to remove clutter in dpkg's output:```

sudo apt purge linux-image-3.19.0-26-generic linux-signed-image-3.19.0-26-generic
sudo apt purge linux-modules-4.15.0-32-generic
sudo apt purge linux-modules-4.15.0-33-generic
sudo apt purge linux-modules-4.15.0-34-generic linux-modules-extra-4.15.0-34-generic
sudo apt purge linux-modules-4.15.0-36-generic
```
Then remove all parts of 4.15.0-39. You don't use it now and it's old.```

sudo apt purge linux-image-unsigned-4.15.0-39-generic linux-modules-4.15.0-39-generic
```That should clear some space in /boot. See what that does to available disk space and have another look at dpkg:```
df -h /boot
dpkg --list | grep linux-
```
Next step is to get the right metapackages installed.

---

### Post by sremick on 2019-04-24
> **Impavidus said:**
> First of all, can you confirm you're currently running kernel 4.15.0-38? Use```
uname -r
``` to check. 
Yup:
```
$ uname -r
4.15.0-38-generic
```
> you can purge them to remove clutter in dpkg's output:
Completed all without error.

[quote]That should clear some space in /boot. See what that does to available disk space
Yup, 66.2MB to be exact. Yay.

```
$ df -h /boot
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       236M   90M  134M  41% /boot
```

```
$ dpkg --list | grep linux-
ii  binutils-x86-64-linux-gnu                    2.31.1-6ubuntu1                            amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                                   4.5ubuntu1                                 all          Linux image base package
ii  linux-cloud-tools-4.15.0-38                  4.15.0-38.41                               amd64        Linux kernel version specific cloud tools for version 4.15.0-38
ii  linux-cloud-tools-4.15.0-38-generic          4.15.0-38.41                               amd64        Linux kernel version specific cloud tools for version 4.15.0-38
ii  linux-cloud-tools-4.18.0-10                  4.18.0-10.11                               amd64        Linux kernel version specific cloud tools for version 4.18.0-10
ii  linux-cloud-tools-4.18.0-10-generic          4.18.0-10.11                               amd64        Linux kernel version specific cloud tools for version 4.18.0-10
ii  linux-cloud-tools-common                     4.18.0-10.11                               all          Linux kernel version specific cloud tools for version 4.18.0
ii  linux-cloud-tools-generic                    4.18.0.10.11                               amd64        Generic Linux kernel cloud tools
ii  linux-firmware                               1.175                                      all          Firmware for Linux kernel drivers
ii  linux-headers-4.15.0-38                      4.15.0-38.41                               all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-38-generic              4.15.0-38.41                               amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-image-4.15.0-38-generic                4.15.0-38.41                               amd64        Signed kernel image generic
ii  linux-libc-dev:amd64                         4.18.0-10.11                               amd64        Linux Kernel Headers for development
ii  linux-modules-4.15.0-38-generic              4.15.0-38.41                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-38-generic        4.15.0-38.41                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-sound-base                             1.0.25+dfsg-0ubuntu5                       all          base package for ALSA and OSS sound systems
ii  linux-tools-4.15.0-38                        4.15.0-38.41                               amd64        Linux kernel version specific tools for version 4.15.0-38
ii  linux-tools-4.15.0-38-generic                4.15.0-38.41                               amd64        Linux kernel version specific tools for version 4.15.0-38
ii  linux-tools-4.18.0-10                        4.18.0-10.11                               amd64        Linux kernel version specific tools for version 4.18.0-10
ii  linux-tools-4.18.0-10-generic                4.18.0-10.11                               amd64        Linux kernel version specific tools for version 4.18.0-10
ii  linux-tools-common                           4.18.0-10.11                               all          Linux kernel version specific tools for version 4.18.0
ii  linux-tools-generic                          4.18.0.10.11                               amd64        Generic Linux kernel tools
ii  syslinux-common                              3:6.04~git20171011.af7e95c3+dfsg1-4ubuntu1 all          collection of bootloaders (common)
ii  syslinux-legacy                              2:3.63+dfsg-2ubuntu9                       amd64        Bootloader for Linux/i386 using MS-DOS floppies


```

---

### Post by Impavidus on 2019-04-24
Now try to get that new kernel installed. First refresh the list of available software:```
sudo apt update
```That may run automatically every day, but it won't harm to run it again.

Then install the meta-package. It will draw in some dependencies, including kernel 4.15.0-47:```
sudo apt install linux-generic
```
You're very tight on space in your /boot partition. Ideally, you have room for at least three kernels. Then you can install a new one alongside your current kernel and one old kernel, then use autoremove to remove the oldest. The system has been designed so that it keeps the two most recent kernels and makes the third autoremovable. You only have room for two kernels, meaning that you have to remove an old kernel before you can install a new one. You can't use apt's autoremove feature for that; you'll have to do it manually. It takes some more micro-management, but it's doable.

If you decide to make a fresh install someday, make the /boot partition half a GB at least. That may waste 300 MB, but you won't notice on a modern hard drive.

---

### Post by sremick on 2019-04-25
```
$ sudo apt install linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  amd64-microcode linux-headers-4.18.0-10 linux-headers-4.18.0-10-generic linux-headers-generic linux-image-4.18.0-10-generic linux-image-generic linux-modules-4.18.0-10-generic
  linux-modules-extra-4.18.0-10-generic thermald
Suggested packages:
  fdutils linux-doc-4.18.0 | linux-source-4.18.0
The following NEW packages will be installed:
  amd64-microcode linux-generic linux-headers-4.18.0-10 linux-headers-4.18.0-10-generic linux-headers-generic linux-image-4.18.0-10-generic linux-image-generic
  linux-modules-4.18.0-10-generic linux-modules-extra-4.18.0-10-generic thermald
0 upgraded, 10 newly installed, 0 to remove and 1 not upgraded.
Need to get 66.1 MB of archives.
After this operation, 331 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu cosmic/main amd64 linux-modules-4.18.0-10-generic amd64 4.18.0-10.11 [13.5 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu cosmic/main amd64 linux-image-4.18.0-10-generic amd64 4.18.0-10.11 [8,148 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu cosmic/main amd64 linux-modules-extra-4.18.0-10-generic amd64 4.18.0-10.11 [32.6 MB]
Get:4 http://us.archive.ubuntu.com/ubuntu cosmic/main amd64 amd64-microcode amd64 3.20180524.1ubuntu1 [33.0 kB]                                                                               
Get:5 http://us.archive.ubuntu.com/ubuntu cosmic/main amd64 linux-image-generic amd64 4.18.0.10.11 [2,304 B]                                                                                  
Get:6 http://us.archive.ubuntu.com/ubuntu cosmic/main amd64 linux-headers-4.18.0-10 all 4.18.0-10.11 [10.5 MB]                                                                                
Get:7 http://us.archive.ubuntu.com/ubuntu cosmic/main amd64 linux-headers-4.18.0-10-generic amd64 4.18.0-10.11 [1,159 kB]                                                                     
Get:8 http://us.archive.ubuntu.com/ubuntu cosmic/main amd64 linux-headers-generic amd64 4.18.0.10.11 [2,264 B]                                                                                
Get:9 http://us.archive.ubuntu.com/ubuntu cosmic/main amd64 linux-generic amd64 4.18.0.10.11 [1,860 B]                                                                                        
Get:10 http://us.archive.ubuntu.com/ubuntu cosmic/main amd64 thermald amd64 1.7.0-8 [185 kB]                                                                                                  
Fetched 66.1 MB in 10s (6,618 kB/s)                                                                                                                                                           
Selecting previously unselected package linux-modules-4.18.0-10-generic.
(Reading database ... 242183 files and directories currently installed.)
Preparing to unpack .../0-linux-modules-4.18.0-10-generic_4.18.0-10.11_amd64.deb ...
Unpacking linux-modules-4.18.0-10-generic (4.18.0-10.11) ...
Selecting previously unselected package linux-image-4.18.0-10-generic.
Preparing to unpack .../1-linux-image-4.18.0-10-generic_4.18.0-10.11_amd64.deb ...
Unpacking linux-image-4.18.0-10-generic (4.18.0-10.11) ...
Selecting previously unselected package linux-modules-extra-4.18.0-10-generic.
Preparing to unpack .../2-linux-modules-extra-4.18.0-10-generic_4.18.0-10.11_amd64.deb ...
Unpacking linux-modules-extra-4.18.0-10-generic (4.18.0-10.11) ...
Selecting previously unselected package amd64-microcode.
Preparing to unpack .../3-amd64-microcode_3.20180524.1ubuntu1_amd64.deb ...
Unpacking amd64-microcode (3.20180524.1ubuntu1) ...
Selecting previously unselected package linux-image-generic.
Preparing to unpack .../4-linux-image-generic_4.18.0.10.11_amd64.deb ...
Unpacking linux-image-generic (4.18.0.10.11) ...
Selecting previously unselected package linux-headers-4.18.0-10.
Preparing to unpack .../5-linux-headers-4.18.0-10_4.18.0-10.11_all.deb ...
Unpacking linux-headers-4.18.0-10 (4.18.0-10.11) ...
Selecting previously unselected package linux-headers-4.18.0-10-generic.
Preparing to unpack .../6-linux-headers-4.18.0-10-generic_4.18.0-10.11_amd64.deb ...
Unpacking linux-headers-4.18.0-10-generic (4.18.0-10.11) ...
Selecting previously unselected package linux-headers-generic.
Preparing to unpack .../7-linux-headers-generic_4.18.0.10.11_amd64.deb ...
Unpacking linux-headers-generic (4.18.0.10.11) ...
Selecting previously unselected package linux-generic.
Preparing to unpack .../8-linux-generic_4.18.0.10.11_amd64.deb ...
Unpacking linux-generic (4.18.0.10.11) ...
Selecting previously unselected package thermald.
Preparing to unpack .../9-thermald_1.7.0-8_amd64.deb ...
Unpacking thermald (1.7.0-8) ...
Setting up thermald (1.7.0-8) ...
Setting up linux-headers-4.18.0-10 (4.18.0-10.11) ...
Setting up linux-headers-4.18.0-10-generic (4.18.0-10.11) ...
Setting up linux-modules-4.18.0-10-generic (4.18.0-10.11) ...
Processing triggers for man-db (2.8.4-2) ...
Processing triggers for dbus (1.12.10-1ubuntu2) ...
Setting up amd64-microcode (3.20180524.1ubuntu1) ...
update-initramfs: deferring update (trigger activated)
amd64-microcode: microcode will be updated at next boot
Setting up linux-headers-generic (4.18.0.10.11) ...
Setting up linux-image-4.18.0-10-generic (4.18.0-10.11) ...
I: /vmlinuz is now a symlink to boot/vmlinuz-4.18.0-10-generic
I: /initrd.img is now a symlink to boot/initrd.img-4.18.0-10-generic
Setting up linux-modules-extra-4.18.0-10-generic (4.18.0-10.11) ...
Setting up linux-image-generic (4.18.0.10.11) ...
Setting up linux-generic (4.18.0.10.11) ...
Processing triggers for initramfs-tools (0.131ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-38-generic
Processing triggers for linux-image-4.18.0-10-generic (4.18.0-10.11) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.18.0-10-generic
/etc/kernel/postinst.d/zz-update-grub:
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.18.0-10-generic
Found initrd image: /boot/initrd.img-4.18.0-10-generic
Found linux image: /boot/vmlinuz-4.15.0-38-generic
Found initrd image: /boot/initrd.img-4.15.0-38-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done


```

So far so good...?

I know I need more space on /boot, and it's going to be a royal PITA to redo the entire computer just to get more space. What frustrates me is that I used the partition size that Ubuntu recommended when I installed. So basically, by naively accepting the recommended size, I screwed myself over. If having such a small /boot partition is so problematic, Ubuntu should not be recommending such a small size.

---

### Post by Impavidus on 2019-04-25
That's not entirely right...

From your 4.15 kernel I assumed you were on Ubuntu 18.04, but it appears you're on 18.10. You forgot to tell, I forgot to ask. You now installed 4.18.0-10, which is an improvement, but it should have installed 4.18.0-18. Maybe the cosmic-updates repository is disabled? Let's have a look at your repositories.```
cat /etc/apt/sources.list
```In the meantime, can you reboot and run the 4.18.0-10 kernel?

The space required for a /boot partition slowly grows, but the size created by the installer lags a bit behind. That's what causes the /boot partition created by the installer to be a bit tight. What's more, people use the same /boot partition for a long time, with several upgrades or fresh installs, during which time the size you need grows even more. Ideally, the installer would make a /boot partition ten times as large as would be needed when the installer was created, but it doesn't. A full /boot partition is a fairly common problem.

---

### Post by sremick on 2019-05-02
Sorry for the delay. Life. I'm back. Let's proceed where we left off:

```
$ uname -r
4.18.0-10-generic
```

```
$ cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to

# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ cosmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ cosmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ cosmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ cosmic universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ cosmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ cosmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu bionic-security main restricted
deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu vivid partner
# deb-src http://archive.canonical.com/ubuntu vivid partner
# deb http://download.virtualbox.org/virtualbox/debian bionic contrib # disabled on upgrade to bionic
deb https://dl.bintray.com/resin-io/debian stable etcher
# deb-src https://dl.bintray.com/resin-io/debian stable etcher
deb https://download.virtualbox.org/virtualbox/debian cosmic contrib
# deb-src https://download.virtualbox.org/virtualbox/debian bionic contrib
deb http://archive.ubuntu.com/ubuntu/ cosmic main
# deb-src http://archive.ubuntu.com/ubuntu/ cosmic main

```

The current state of attempting to upgrade:
```
The upgrade has aborted. The upgrade needs a total of 167 M free space on disk '/boot'. Please free at least an additional 44.1 M of disk space on '/boot'. 
```

---

### Post by Impavidus on 2019-05-02
You've got a strange mixture of software sources from 18.04 and 18.10.

First make a bit of room in /boot. Now that you have kernel 4.18.0-10 running, it's time to remove 4.15.0-38. It would be better to keep it in case you develop some problem with 4.18.0-10, but you don't have the room.```
sudo apt purge linux-cloud-tools-4.15.0-38 linux-cloud-tools-4.15.0-38-generic
sudo apt purge linux-tools-4.15.0-38 linux-tools-4.15.0-38-generic
sudo apt purge linux-image-4.15.0-38-generic linux-modules-4.15.0-38-generic linux-modules-extra-4.15.0-38-generic
sudo apt purge linux-headers-4.15.0-38 linux-headers-4.15.0-38-generic
```
Now make a backup of your sources.list:```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bck
```
That's just in case something goes wrong with the following commands. Then replace all instances of bionic with cosmic:```
sudo sed -i s/bionic/cosmic/g /etc/apt/sources.list
```The partner repository still points to vivid (17.04). It's disabled, so that doesn't matter, but just in case you want to enable it at some future date, let's change that as well.```
sudo sed -i s/vivid/cosmic/g /etc/apt/sources.list
```You've got one disabled PPA (for virtualbox) from bionic, which has by these commands been changed to cosmic. [s]I don't know if that will work. If you want to enable that PPA and it doesn't work for cosmic, change it back to bionic.[/s] Never mind, you've already got a line for the cosmic version of that PPA.

Now you should have a proper sources.list. Update and upgrade:```
sudo apt update
sudo apt upgrade
```That should get you all upgrades for 18.10 since the release date.

---

