---
title: "apt-get update errors, /boot full, can't remove old kernels?"
date: 2015-08-22
forum: General Help
---

### Post by hutchinson-karl on 2015-08-22
Hi. I'm running Lubuntu, on Ubuntu 14.04.3 LTS. I've been having trouble getting updates. I think my problem is that my boot partition is full (full of old kernels), but I can't seem to remove old kernels. Am I reading these error messages correctly? Is there anything else I should try? I'd appreciate any help!

When I run sudo apt-get upgrade, I see:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-3.13.0-62-generic : Depends: linux-image-3.13.0-62-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.13.0-62-generic but it is not installed
E: Unmet dependencies. Try using -f.
```

I've tried apt-get -f install as is suggests, but get:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  exo-utils libgarcon-1-0 libgarcon-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.13.0-62-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.13.0-62-generic
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
4 not fully installed or removed.
Need to get 0 B/14.7 MB of archives.
After this operation, 32.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 366559 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-62-generic_3.13.0-62.102_i386.deb ...
Done.
Unpacking linux-image-3.13.0-62-generic (3.13.0-62.102) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-62-generic_3.13.0-62.102_i386.deb (--unpack):
 cannot copy extracted data for './boot/abi-3.13.0-62-generic' to '/boot/abi-3.13.0-62-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-62-generic_3.13.0-62.102_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

The apt-get autoremove command it suggests also doesn't work here.

So I see it says it can't copy data to /boot because the device is full. Disks tells me my boot partition (dev/sda1, Linux bootable) is 255MB, 774KB free (99.7% full). So that seems to be a problem. My research so far led me to the suggestion to remove old kernels. 
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)

uname -r tells me my current kernel is **3.13.0-61-generic**, and "dpkg -l | grep linux-image-" tells me I also have linux-image-3.13.0-[32, 39, 40, 43, 46, 48, 49, 52, 61]-generic. Actually, I also see I have linux-image-**extra**-3.13.0-**62**-generic. Is that a problem??

So I try removing the oldest kernel using "sudo apt-get autoremove linux-image-extra-3.13.0-32-generic" and I get:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'linux-image-extra-3.13.0-32-generic' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.13.0-62-generic : Depends: linux-image-3.13.0-62-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-62-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

I get the same result as I try to autoremove each of the other old kernels (not including -61-generic or -62-generic, I'm not trying to remove them). So I feel like I'm stuck in a loop. Is there something else I should do here? Please let me know if I can provide more details. Thanks!!

---

### Post by sandyd on 2015-08-22
Hi, can you post the output of
```

ls -l /boot

```

Thanks!

---

### Post by hutchinson-karl on 2015-08-22
Sure.

```
total 231323
-rw-r--r-- 1 root root  1168764 Oct 28  2014 abi-3.13.0-39-generic
-rw-r--r-- 1 root root  1168726 Nov 13  2014 abi-3.13.0-40-generic
-rw-r--r-- 1 root root  1168937 Dec  8  2014 abi-3.13.0-43-generic
-rw-r--r-- 1 root root  1169069 Mar 10 13:53 abi-3.13.0-46-generic
-rw-r--r-- 1 root root  1168940 Mar 12 05:20 abi-3.13.0-48-generic
-rw-r--r-- 1 root root  1168940 Apr 10 14:00 abi-3.13.0-49-generic
-rw-r--r-- 1 root root  1168888 May  3 22:35 abi-3.13.0-52-generic
-rw-r--r-- 1 root root  1169346 Jul 29 05:40 abi-3.13.0-61-generic
-rw-r--r-- 1 root root   169782 Oct 28  2014 config-3.13.0-39-generic
-rw-r--r-- 1 root root   169815 Nov 13  2014 config-3.13.0-40-generic
-rw-r--r-- 1 root root   169815 Dec  8  2014 config-3.13.0-43-generic
-rw-r--r-- 1 root root   169818 Mar 10 13:53 config-3.13.0-46-generic
-rw-r--r-- 1 root root   169843 Mar 12 05:20 config-3.13.0-48-generic
-rw-r--r-- 1 root root   169843 Apr 10 14:00 config-3.13.0-49-generic
-rw-r--r-- 1 root root   169832 May  3 22:35 config-3.13.0-52-generic
-rw-r--r-- 1 root root   169833 Jul 29 05:40 config-3.13.0-61-generic
drwxr-xr-x 5 root root     1024 Aug  8 10:38 grub
-rw-r--r-- 1 root root 19512616 Nov 23  2014 initrd.img-3.13.0-39-generic
-rw-r--r-- 1 root root 19514346 Dec  1  2014 initrd.img-3.13.0-40-generic
-rw-r--r-- 1 root root 19544062 Mar  1 14:12 initrd.img-3.13.0-43-generic
-rw-r--r-- 1 root root 19552856 Mar 12 00:45 initrd.img-3.13.0-46-generic
-rw-r--r-- 1 root root 19553520 Mar 25 19:48 initrd.img-3.13.0-48-generic
-rw-r--r-- 1 root root 19554140 Apr 26 17:32 initrd.img-3.13.0-49-generic
-rw-r--r-- 1 root root 19554831 Aug  6 18:53 initrd.img-3.13.0-52-generic
-rw-r--r-- 1 root root 19559386 Aug  8 10:38 initrd.img-3.13.0-61-generic
drwx------ 2 root root    12288 Nov 23  2014 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  2697539 Oct 28  2014 System.map-3.13.0-39-generic
-rw------- 1 root root  2697648 Nov 13  2014 System.map-3.13.0-40-generic
-rw------- 1 root root  2699011 Dec  8  2014 System.map-3.13.0-43-generic
-rw------- 1 root root  2699562 Mar 10 13:53 System.map-3.13.0-46-generic
-rw------- 1 root root  2699351 Mar 12 05:20 System.map-3.13.0-48-generic
-rw------- 1 root root  2699535 Apr 10 14:00 System.map-3.13.0-49-generic
-rw------- 1 root root  2699822 May  3 22:35 System.map-3.13.0-52-generic
-rw------- 1 root root  2701185 Jul 29 05:40 System.map-3.13.0-61-generic
-rw------- 1 root root  5828720 Oct 28  2014 vmlinuz-3.13.0-39-generic
-rw------- 1 root root  5830128 Nov 13  2014 vmlinuz-3.13.0-40-generic
-rw------- 1 root root  5833296 Dec  8  2014 vmlinuz-3.13.0-43-generic
-rw------- 1 root root  5836592 Mar 10 13:53 vmlinuz-3.13.0-46-generic
-rw------- 1 root root  5837296 Mar 12 05:20 vmlinuz-3.13.0-48-generic
-rw------- 1 root root  5836528 Apr 10 14:00 vmlinuz-3.13.0-49-generic
-rw------- 1 root root  5837072 May  3 22:35 vmlinuz-3.13.0-52-generic
-rw------- 1 root root  5843472 Jul 29 05:40 vmlinuz-3.13.0-61-generic
```

---

### Post by XBNCPRk on 2015-08-22
You can remove old kernels/headers/images from the ununtu software center by searching for 'linux-h' and 'linux-i' under the insalled tab, and selecting the ones you wish to remove (make sure at the bottom of the search results screen youve clicked where it says show ### technical items).

Alternatively, you can uninstall them from the command line using apt-get remove 

Autoremove will only remove no-longer-needed packages that were used as dependencies for things that are no longer installed -- basically it sweeps out any trash left behind from uninstalls. Since the old kernels are still validly installed, autoremove will not do anything.

---

### Post by sandyd on 2015-08-22
Lets give this a try...
You're currently using 3.13.0-61-generic, lets remove everything else except for one kernel
```

sudo dpkg --purge linux-image-3.13.0-39-generic linux-image-3.13.0-40-generic linux-image-3.13.0-43-generic linux-image-3.13.0-46-generic linux-image-3.13.0-48-generic linux-image-3.13.0-49-generic linux-image-extra-3.13.0-39-generic linux-image-extra-3.13.0-40-generic linux-image-extra-3.13.0-43-generic linux-image-extra-3.13.0-46-generic linux-image-extra-3.13.0-48-generic linux-image-extra-3.13.0-49-generic
sudo apt-get -f install

```

---

### Post by hutchinson-karl on 2015-08-22
It says they're not installed??

```
sudo dpkg --purge linux-image-3.13.0-39 linux-image-3.13.0-40 linux-image-3.13.0-43 linux-image-3.13.0-46 linux-image-3.13.0-48 linux-image-3.13.0-49
dpkg: warning: ignoring request to remove linux-image-3.13.0-39 which isn't installed
dpkg: warning: ignoring request to remove linux-image-3.13.0-40 which isn't installed
dpkg: warning: ignoring request to remove linux-image-3.13.0-43 which isn't installed
dpkg: warning: ignoring request to remove linux-image-3.13.0-46 which isn't installed
dpkg: warning: ignoring request to remove linux-image-3.13.0-48 which isn't installed
dpkg: warning: ignoring request to remove linux-image-3.13.0-49 which isn't installed
```

---

### Post by hutchinson-karl on 2015-08-22
Hi [COLOR=#000000]XBNCPRk. With Lubuntu, I don't have the Ubuntu Software Center. I don't know how different the Lubuntu Software Center is, but on the Installed Software tab, when I search linux-h, I get no results.[/COLOR] I can do the search in Synaptic Package Manager, and it shows linux-header- and linux-image packages, checked and un-checked. Would it work if I marked the old linux-image files for removal?

---

### Post by sandyd on 2015-08-22
> **hutchinson-karl said:**
> It says they're not installed??

```
sudo dpkg --purge linux-image-3.13.0-39 linux-image-3.13.0-40 linux-image-3.13.0-43 linux-image-3.13.0-46 linux-image-3.13.0-48 linux-image-3.13.0-49
dpkg: warning: ignoring request to remove linux-image-3.13.0-39 which isn't installed
dpkg: warning: ignoring request to remove linux-image-3.13.0-40 which isn't installed
dpkg: warning: ignoring request to remove linux-image-3.13.0-43 which isn't installed
dpkg: warning: ignoring request to remove linux-image-3.13.0-46 which isn't installed
dpkg: warning: ignoring request to remove linux-image-3.13.0-48 which isn't installed
dpkg: warning: ignoring request to remove linux-image-3.13.0-49 which isn't installed
```

Fixed typing error

---

### Post by hutchinson-karl on 2015-08-22
Dependency problems. Does this mean the linux-image-extra- packages need to be removed first?

```
:~$ sudo dpkg --purge linux-image-3.13.0-39-generic linux-image-3.13.0-40-generic linux-image-3.13.0-43-generic linux-image-3.13.0-46-generic linux-image-3.13.0-48-generic linux-image-3.13.0-49-generic
dpkg: dependency problems prevent removal of linux-image-3.13.0-39-generic:
 linux-image-extra-3.13.0-39-generic depends on linux-image-3.13.0-39-generic.

dpkg: error processing package linux-image-3.13.0-39-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-40-generic:
 linux-image-extra-3.13.0-40-generic depends on linux-image-3.13.0-40-generic.

dpkg: error processing package linux-image-3.13.0-40-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-43-generic:
 linux-image-extra-3.13.0-43-generic depends on linux-image-3.13.0-43-generic.

dpkg: error processing package linux-image-3.13.0-43-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-46-generic:
 linux-image-extra-3.13.0-46-generic depends on linux-image-3.13.0-46-generic.

dpkg: error processing package linux-image-3.13.0-46-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-48-generic:
 linux-image-extra-3.13.0-48-generic depends on linux-image-3.13.0-48-generic.

dpkg: error processing package linux-image-3.13.0-48-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-49-generic:
 linux-image-extra-3.13.0-49-generic depends on linux-image-3.13.0-49-generic.

dpkg: error processing package linux-image-3.13.0-49-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.13.0-39-generic
 linux-image-3.13.0-40-generic
 linux-image-3.13.0-43-generic
 linux-image-3.13.0-46-generic
 linux-image-3.13.0-48-generic
 linux-image-3.13.0-49-generic
```

---

### Post by sandyd on 2015-08-22
> **hutchinson-karl said:**
> Dependency problems. Does this mean the linux-image-extra- packages need to be removed first?

```
:~$ sudo dpkg --purge linux-image-3.13.0-39-generic linux-image-3.13.0-40-generic linux-image-3.13.0-43-generic linux-image-3.13.0-46-generic linux-image-3.13.0-48-generic linux-image-3.13.0-49-generic
dpkg: dependency problems prevent removal of linux-image-3.13.0-39-generic:
 linux-image-extra-3.13.0-39-generic depends on linux-image-3.13.0-39-generic.

dpkg: error processing package linux-image-3.13.0-39-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-40-generic:
 linux-image-extra-3.13.0-40-generic depends on linux-image-3.13.0-40-generic.

dpkg: error processing package linux-image-3.13.0-40-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-43-generic:
 linux-image-extra-3.13.0-43-generic depends on linux-image-3.13.0-43-generic.

dpkg: error processing package linux-image-3.13.0-43-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-46-generic:
 linux-image-extra-3.13.0-46-generic depends on linux-image-3.13.0-46-generic.

dpkg: error processing package linux-image-3.13.0-46-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-48-generic:
 linux-image-extra-3.13.0-48-generic depends on linux-image-3.13.0-48-generic.

dpkg: error processing package linux-image-3.13.0-48-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-49-generic:
 linux-image-extra-3.13.0-49-generic depends on linux-image-3.13.0-49-generic.

dpkg: error processing package linux-image-3.13.0-49-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.13.0-39-generic
 linux-image-3.13.0-40-generic
 linux-image-3.13.0-43-generic
 linux-image-3.13.0-46-generic
 linux-image-3.13.0-48-generic
 linux-image-3.13.0-49-generic
```
Fixed in the earlier command.

---

### Post by hutchinson-karl on 2015-08-22
Longer output this time. Seems to be complaining that there's no room on the /root partition.

```
:~$ sudo dpkg --purge linux-image-3.13.0-39-generic linux-image-3.13.0-40-generic linux-image-3.13.0-43-generic linux-image-3.13.0-46-generic linux-image-3.13.0-48-generic linux-image-3.13.0-49-generic linux-image-extra-3.13.0-39-generic linux-image-extra-3.13.0-40-generic linux-image-extra-3.13.0-43-generic linux-image-extra-3.13.0-46-generic linux-image-extra-3.13.0-48-generic linux-image-extra-3.13.0-49-generic
(Reading database ... 366559 files and directories currently installed.)
Removing linux-image-extra-3.13.0-39-generic (3.13.0-39.66) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-39-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-39-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-39-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-40-generic (3.13.0-40.69) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-40-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-40-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-40-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-43-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-43-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-46-generic (3.13.0-46.79) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-46-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-46-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-46-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-48-generic (3.13.0-48.80) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-48-generic /boot/vmlinuz-3.13.0-48-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-48-generic /boot/vmlinuz-3.13.0-48-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-48-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-48-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-48-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-49-generic (3.13.0-49.83) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-49-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-49-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-49-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-39-generic (3.13.0-39.66) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-39-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-61-generic
Found initrd image: /boot/initrd.img-3.13.0-61-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
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
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-61-generic
Found initrd image: /boot/initrd.img-3.13.0-61-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.13.0-40-generic (3.13.0-40.69) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
Removing linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-61-generic
Found initrd image: /boot/initrd.img-3.13.0-61-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Removing linux-image-3.13.0-46-generic (3.13.0-46.79) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-46-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-61-generic
Found initrd image: /boot/initrd.img-3.13.0-61-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.13.0-46-generic (3.13.0-46.79) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
Removing linux-image-3.13.0-48-generic (3.13.0-48.80) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-48-generic /boot/vmlinuz-3.13.0-48-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-48-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-48-generic /boot/vmlinuz-3.13.0-48-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-61-generic
Found initrd image: /boot/initrd.img-3.13.0-61-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.13.0-48-generic (3.13.0-48.80) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-48-generic /boot/vmlinuz-3.13.0-48-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-48-generic /boot/vmlinuz-3.13.0-48-generic
Removing linux-image-3.13.0-49-generic (3.13.0-49.83) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-49-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-61-generic
Found initrd image: /boot/initrd.img-3.13.0-61-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.13.0-49-generic (3.13.0-49.83) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
Errors were encountered while processing:
 linux-image-extra-3.13.0-39-generic
 linux-image-extra-3.13.0-40-generic
 linux-image-extra-3.13.0-43-generic
 linux-image-extra-3.13.0-46-generic
 linux-image-extra-3.13.0-48-generic
 linux-image-extra-3.13.0-49-generic
```

But when I list /boot now, they seem to be gone.

```
ls -l /boot
total 58273
-rw-r--r-- 1 root root  1168888 May  3 22:35 abi-3.13.0-52-generic
-rw-r--r-- 1 root root  1169346 Jul 29 05:40 abi-3.13.0-61-generic
-rw-r--r-- 1 root root   169832 May  3 22:35 config-3.13.0-52-generic
-rw-r--r-- 1 root root   169833 Jul 29 05:40 config-3.13.0-61-generic
drwxr-xr-x 5 root root     1024 Aug 22 17:32 grub
-rw-r--r-- 1 root root 19554831 Aug  6 18:53 initrd.img-3.13.0-52-generic
-rw-r--r-- 1 root root 19559386 Aug  8 10:38 initrd.img-3.13.0-61-generic
drwx------ 2 root root    12288 Nov 23  2014 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  2699822 May  3 22:35 System.map-3.13.0-52-generic
-rw------- 1 root root  2701185 Jul 29 05:40 System.map-3.13.0-61-generic
-rw------- 1 root root  5837072 May  3 22:35 vmlinuz-3.13.0-52-generic
-rw------- 1 root root  5843472 Jul 29 05:40 vmlinuz-3.13.0-61-generic
```

---

### Post by hutchinson-karl on 2015-08-22
I've confirmed, my /dev/sda1 is now just 30.1% full, 178MB free!

---

### Post by hutchinson-karl on 2015-08-22
Now, when I run -f install, it seems it's going to re-install all those kernel packages again.

```
:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  exo-utils libgarcon-1-0 libgarcon-common linux-headers-3.13.0-52
  linux-headers-3.13.0-52-generic linux-image-3.13.0-52-generic
  linux-image-extra-3.13.0-52-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.13.0-39-generic linux-image-3.13.0-40-generic
  linux-image-3.13.0-43-generic linux-image-3.13.0-46-generic
  linux-image-3.13.0-48-generic linux-image-3.13.0-49-generic
  linux-image-3.13.0-62-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.13.0-39-generic linux-image-3.13.0-40-generic
  linux-image-3.13.0-43-generic linux-image-3.13.0-46-generic
  linux-image-3.13.0-48-generic linux-image-3.13.0-49-generic
  linux-image-3.13.0-62-generic
0 upgraded, 7 newly installed, 0 to remove and 3 not upgraded.
10 not fully installed or removed.
Need to get 310 MB/325 MB of archives.
After this operation, 229 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
```

Do I want to say YES?

---

### Post by hutchinson-karl on 2015-08-22
I ran the dpkg --purge command again from above, with all the same arguments, and it seems to have finished purging. When I run apt-get upgrade I don't get any error messages, and it doesn't want to install any missing packages for those old linux images. Thank you!

I'd love to understand the process of what happened here. Can you describe what the problem was, and what the commands did to fix it?

---

### Post by sandyd on 2015-08-22
Sorry, i was going to suggest running the command again after it was successful, but at that time, i was out on a walk

What we did was remove the kernels that were taking up space

Normally, apt will balk at removing the kernels because the disk is full. Instead, we jumped to a lower level tool (dpkg) to remove the packages that were filling up /boot. To simplfy things, you can think of apt being a frontend to dpkg.

When dpkg finally worked, it still failed because the packages (kernels) would run a postrm script after the package files were deleted. When you ran it again, there was now enough space emptied, so the postrm script ran fine.

---

### Post by hutchinson-karl on 2015-08-23
Great. Thank you again for your help. I'm comfortable using terminal commands ... I just don't know what most of them do.

---

### Post by The Frenchman on 2015-08-31
I can't update from software updater,keep getting check your internet connection,even though I am connected a opening pages at the time.Have tried terminal sudo apt-get update and upgrade commands but still get[ATTACH=CONFIG]264131[/ATTACH]  after running upgrade command is there another way to handle updates that will work?

---

### Post by The Frenchman on 2015-09-08
> **The Frenchman said:**
> I can't update from software updater,keep getting check your internet connection,even though I am connected a opening pages at the time.Have tried terminal sudo apt-get update and upgrade commands but still get[ATTACH=CONFIG]264131[/ATTACH]  after running upgrade command is there another way to handle updates that will work?
Thanks for all the help! What an excellent forum.......

---

