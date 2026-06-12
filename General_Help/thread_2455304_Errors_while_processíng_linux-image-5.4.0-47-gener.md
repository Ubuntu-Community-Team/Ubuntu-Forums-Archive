---
title: "Errors while processíng linux-image-5.4.0-47-generic"
date: 2020-12-17
forum: General Help
---

### Post by siloswagster on 2020-12-17
Hello,
I'm new to Ubuntu and got this during executing ```
sudo apt upgrade
```.
I found some threads with this issue, but none of them seemed to solve it. 

```
silas@silas-Zephyrus-G-GU502DU-GA502DU:/$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libdrm2:i386 libexpat1:i386 libfprint-2-tod1 libglapi-mesa:i386 libglvnd0:i386 libnvidia-common-450 libx11-xcb1:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386
  libxcb-sync1:i386 libxdamage1:i386 libxfixes3:i386 libxshmfence1:i386 libxxf86vm1:i386
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  libnvidia-cfg1-440 libnvidia-compute-440 libnvidia-compute-440:i386 libnvidia-decode-440 libnvidia-decode-440:i386 libnvidia-encode-440 libnvidia-encode-440:i386 libnvidia-extra-440 libnvidia-fbc1-440
  libnvidia-gl-440 libnvidia-gl-440:i386 libnvidia-ifr1-440 nvidia-compute-utils-440 nvidia-driver-440 nvidia-kernel-common-440 nvidia-kernel-source-440 nvidia-utils-440 xserver-xorg-video-nvidia-440
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
2 not fully installed or removed.
Need to get 0 B/8.881 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up linux-image-5.4.0-47-generic (5.4.0-47.51) ...
Processing triggers for linux-image-5.4.0-47-generic (5.4.0-47.51) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.4.0-47-generic
Error! Your kernel headers for kernel 5.4.0-47-generic cannot be found.
Please install the linux-headers-5.4.0-47-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.4.0-47-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: nouveau.modeset=0: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.4.0-47-generic (--configure):
 installed linux-image-5.4.0-47-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-5.4.0-47-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by tea for one on 2020-12-17
There is a clue in the output:-
> Please install the linux-headers-5.4.0-47-generic package

```
sudo apt install linux-headers-5.4.0-47-generic
```

---

### Post by ajgreeny on 2020-12-17
The kernel from linux-image-5.4.0-47 is now pretty old and Ubuntu 20.04 is currently using 5.4.0-58 in Ubuntu 20.04.
What version of Ubuntu are you using, and is it 64 bit?
Also note that before running ***sudo apt upgrade*** you must run ***sudo apt update*** to refresh the sources from which you download packages; perhaps you did so but you did not mention that.

Try running commands ***sudo apt update && sudo apt full-upgrade*** and you should be upgraded to the newest kernel available

Check that you have linux-headers installed with command ***dpkg -s linux-headers-generic*** which hopefully will show output similar to mine below, though details of the version may be different at the moment.
```
dpkg -s linux-headers-generic
Package: linux-headers-generic
Status: install ok installed
Priority: optional
Section: kernel
Installed-Size: 18
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-meta
Version: 5.4.0.58.61
Depends: linux-headers-5.4.0-58-generic
Description: Generic Linux kernel headers
 This package will always depend on the latest generic kernel headers
 available.

```

---

### Post by ActionParsnip on 2020-12-17
What is the output of:
```

cat -n /etc/default/grub

```
Thanks

---

### Post by siloswagster on 2020-12-17
This didn't work

```
silas@silas-Zephyrus-G-GU502DU-GA502DU:/$ sudo apt install linux-headers-5.4.0-47-generic
[sudo] password for silas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdrm2:i386 libexpat1:i386 libfprint-2-tod1 libglapi-mesa:i386 libglvnd0:i386 libnvidia-common-450 libx11-xcb1:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386
  libxcb-sync1:i386 libxdamage1:i386 libxfixes3:i386 libxshmfence1:i386 libxxf86vm1:i386 linux-modules-5.4.0-42-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-headers-5.4.0-47
The following packages will be REMOVED:
  linux-image-5.4.0-42-generic
The following NEW packages will be installed:
  linux-headers-5.4.0-47 linux-headers-5.4.0-47-generic
0 upgraded, 2 newly installed, 1 to remove and 18 not upgraded.
2 not fully installed or removed.
Need to get 12,2 MB of archives.
After this operation, 73,5 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://de.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-headers-5.4.0-47 all 5.4.0-47.51 [11,0 MB]
Get:2 http://de.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-headers-5.4.0-47-generic amd64 5.4.0-47.51 [1.254 kB]                                                                                    
Fetched 12,2 MB in 16s (765 kB/s)                                                                                                                                                                                 
(Reading database ... 155517 files and directories currently installed.)
Removing linux-image-5.4.0-42-generic (5.4.0-42.46) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.4.0-42-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: nouveau.modeset=0: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.4.0-42-generic (--remove):
 installed linux-image-5.4.0-42-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.4.0-42-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by siloswagster on 2020-12-17
> **ajgreeny said:**
> The kernel from linux-image-5.4.0-47 is now pretty old and Ubuntu 20.04 is currently using 5.4.0-58 in Ubuntu 20.04.
What version of Ubuntu are you using, and is it 64 bit?
Also note that before running ***sudo apt upgrade*** you must run ***sudo apt update*** to refresh the sources from which you download packages; perhaps you did so but you did not mention that.

Try running commands ***sudo apt update && sudo apt full-upgrade*** and you should be upgraded to the newest kernel available

Check that you have linux-headers installed with command ***dpkg -s linux-headers-generic*** which hopefully will show output similar to mine below, though details of the version may be different at the moment.
```
dpkg -s linux-headers-generic
Package: linux-headers-generic
Status: install ok installed
Priority: optional
Section: kernel
Installed-Size: 18
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-meta
Version: 5.4.0.58.61
Depends: linux-headers-5.4.0-58-generic
Description: Generic Linux kernel headers
 This package will always depend on the latest generic kernel headers
 available.

```


I obviously ran **sudo apt update** and also tried sudo **apt full-upgrade.**
When trying*** dpkg -s linux-headers-generic ***this was the output:

```
silas@silas-Zephyrus-G-GU502DU-GA502DU:/$ dpkg -s linux-headers-generic
dpkg-query: package 'linux-headers-generic' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files.


```

---

### Post by siloswagster on 2020-12-17
> **ActionParsnip said:**
> What is the output of:
```

cat -n /etc/default/grub

```
Thanks

For me it seems like grub isn't able to delete the old kernel

```
silas@silas-Zephyrus-G-GU502DU-GA502DU:/$ cat -n /etc/default/grub
     1    # If you change this file, run 'update-grub' afterwards to update
     2    # /boot/grub/grub.cfg.
     3    # For full documentation of the options in this file, see:
     4    #   info -f grub -n 'Simple configuration'
     5    
     6    GRUB_DEFAULT=0
     7    GRUB_TIMEOUT_STYLE=hidden
     8    GRUB_TIMEOUT=10
     9    GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
    10    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
    11    nouveau.modeset=0 tpm_tis.interrupts=0 acpi_osi=Linux i915.preliminary_hw_support=1 idle=nomwait
    12    GRUB_CMDLINE_LINUX=""
    13    
    14    # Uncomment to enable BadRAM filtering, modify to suit your needs
    15    # This works with Linux (no patch required) and with any kernel that obtains
    16    # the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
    17    #GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
    18    
    19    # Uncomment to disable graphical terminal (grub-pc only)
    20    #GRUB_TERMINAL=console
    21    
    22    # The resolution used on graphical terminal
    23    # note that you can use only modes which your graphic card supports via VBE
    24    # you can see them in real GRUB with the command `vbeinfo'
    25    #GRUB_GFXMODE=640x480
    26    
    27    # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
    28    #GRUB_DISABLE_LINUX_UUID=true
    29    
    30    # Uncomment to disable generation of recovery mode menu entries
    31    #GRUB_DISABLE_RECOVERY="true"
    32    
    33    # Uncomment to get a beep at grub start
    34    #GRUB_INIT_TUNE="480 440 1"


```

---

### Post by siloswagster on 2020-12-17
I just found out that line 11 caused my issue. I previously added that line because of this post:
[https://ubuntuforums.org/showthread.php?t=2440670](https://ubuntuforums.org/showthread.php?t=2440670)

---

### Post by ajgreeny on 2020-12-18
That line 11 should not have been a separate  line in the file but a continuation of the line above with the contents coming after quiet splash but within the quote marks.

---

