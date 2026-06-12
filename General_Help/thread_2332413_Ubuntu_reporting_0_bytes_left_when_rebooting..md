---
title: "Ubuntu reporting 0 bytes left when rebooting."
date: 2016-07-31
forum: General Help
---

### Post by nzdreamer55 on 2016-07-31
Hello everyone,

I had a problem that the community helped me solve at this thread [https://ubuntuforums.org/showthread.php?t=2324098&page=3](https://ubuntuforums.org/showthread.php?t=2324098&page=3) involving a space issue on my hard drive.  I marked it solved, but just this past week when I restarted my computer I got an error that said I had 0 bytes of space (see attached image)
[ATTACH=CONFIG]270478[/ATTACH]

I tried following the advice from my previous help thread and it didn't seem like there were any hidden files present.  When I run the disk analyse I don't get much help either (see attached picture).

What is my next step in trouble shooting this?

Thanks.

---

### Post by Bashing-om on 2016-07-31
nzdreamer55; Hello;

Again, we start this process by looking at what the system reports for disk space usage.
Post back:
```

df -h
df -i

```

And away we go on the hunt to know where to look and then what to do.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by nzdreamer55 on 2016-07-31
Thanks for the help.  So does the mount at //192.168.1.104/offlinesorage look to be the issue?  when I umount this point and then try to check it though the Files icon, it says that it isn't accessible.

---

### Post by &amp;KyT$0P# on 2016-07-31
No it's your /boot partition and this means you'll need to purge old kernels to get the free disk space back.  The procedure is the same as I outlined in [this post]("https://ubuntuforums.org/showthread.php?t=2331032&p=13518771&viewfull=1#post13518771"), but your kernel versions will probably be different from theirs.  Do **not** just run the literal apt-get purge command I later posted there, because it is probably not right for you and at worst might result in your OS being bricked.

Let us know, thanks.

---

### Post by nzdreamer55 on 2016-07-31
Ok.  So here is the output from that last thread.  So it looks like I want to keep the 4.2.0-42 right?  

So do I type in

"[COLOR=#000000][FONT=&quot]sudo apt-get purge" for all of the things that are not 4.2.0-42 or is there an easier way?[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-07-31
nzdreamer55; Hey ...

As all kernels are wily's .. let us try a simpler approach .
May not work as at 100% capacity, I can accept that the system has no operating head room .. but maybe:
```

sudo apt-get autoremove

```
else;
I want to see what the installed kernels are in a format that is manageable .
Please post back - Between Code Tags - the output of terminal command:
```

dpkg -l | grep linux-

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And let's get this system stable .. release 15.10 is End_of_Life now and will soon loose all support. Let's get you upgraded before we loose access to the software repository !

[INDENT][INDENT]there is a way that seems right
[INDENT][INDENT][INDENT]but leads to a broken system
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nzdreamer55 on 2016-07-31
Thanks for the help.  When I tried to get the autoremove I got this

```
linux@linuxlaptop:~$ sudo apt-get autoremove[sudo] password for linux: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-extra-4.2.0-42-generic (4.2.0-42.49~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-42-generic /boot/vmlinuz-4.2.0-42-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-42-generic /boot/vmlinuz-4.2.0-42-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-42-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.2.0-42-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.2.0-42-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)
linux@linuxlaptop:~$ 

```

And here is the output from the second command

```
linux@linuxlaptop:~$ dpkg -l | grep linux-ii  linux-firmware                                        1.127.22                                            all          Firmware for Linux kernel drivers
iU  linux-generic-lts-wily                                4.2.0.42.34                                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.2.0-30                                4.2.0-30.36~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-30-generic                        4.2.0-30.36~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-34                                4.2.0-34.39~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-34-generic                        4.2.0-34.39~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-35                                4.2.0-35.40~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-35-generic                        4.2.0-35.40~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-36                                4.2.0-36.42~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-36-generic                        4.2.0-36.42~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-38                                4.2.0-38.45~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-38-generic                        4.2.0-38.45~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-41                                4.2.0-41.48~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-41-generic                        4.2.0-41.48~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-42                                4.2.0-42.49~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-42-generic                        4.2.0-42.49~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-wily                        4.2.0.42.34                                         amd64        Generic Linux kernel headers
rc  linux-image-4.2.0-27-generic                          4.2.0-27.32~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-30-generic                          4.2.0-30.36~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-34-generic                          4.2.0-34.39~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-35-generic                          4.2.0-35.40~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-36-generic                          4.2.0-36.42~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-38-generic                          4.2.0-38.45~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-41-generic                          4.2.0-41.48~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-42-generic                          4.2.0-42.49~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-27-generic                    4.2.0-27.32~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-30-generic                    4.2.0-30.36~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-34-generic                    4.2.0-34.39~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-35-generic                    4.2.0-35.40~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-36-generic                    4.2.0-36.42~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-38-generic                    4.2.0-38.45~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-41-generic                    4.2.0-41.48~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
iF  linux-image-extra-4.2.0-42-generic                    4.2.0-42.49~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
iU  linux-image-generic-lts-wily                          4.2.0.42.34                                         amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-92.139                                       amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies



```

---

### Post by Bashing-om on 2016-07-31
nzdreamer55; Ho Kay ..

No operating head room. and we have:
> 
iF  linux-image-extra-4.2.0-42-generic

as we are out of space, can not be fully installed . So now we drop down to a lower level to deal with this conundrum.
We must know at this point what the booting kernel is .. we MUST not mess with it !
show us:
```

uname -r

```
and we sic 'dpkg' on those kernels .. see what we can do at that level.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by nzdreamer55 on 2016-07-31
It says

4.2.0-42-generic

Thanks so much for the help.  So how do I "[COLOR=#000000]sic 'dpkg' on those kernels"[/COLOR]

---

### Post by ajgreeny on 2016-07-31
We will need to remove excess kernels using dpkg so let's start with ```
sudo dpkg -P linux-image{,-extra}-4.2.0-{30,34,35,36}-generic
``` which should remove 4 of those unwanted kernels and leave you with two plus the one that you appear to be running but is shown as not fully installed.

Hopefully that will sort out your lack of space problem and we can then work out what extra needs removing, which if you have by then upgraded to 16.04 should be simply to run ```
sudo apt-get autoremove
```

---

### Post by nzdreamer55 on 2016-07-31
Ok.  So I did the following and here is what I got (see below).  It seems like there were a lot of errors.

```
linux@linuxlaptop:~$ sudo dpkg -P linux-image{,-extra}-4.2.0-{30,34,35,36}-generic[sudo] password for linux: 
(Reading database ... 386681 files and directories currently installed.)
Removing linux-image-extra-4.2.0-30-generic (4.2.0-30.36~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-30-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.2.0-30-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.2.0-30-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.2.0-34-generic (4.2.0-34.39~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-34-generic /boot/vmlinuz-4.2.0-34-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-34-generic /boot/vmlinuz-4.2.0-34-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-34-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.2.0-34-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.2.0-34-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.2.0-35-generic (4.2.0-35.40~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-35-generic /boot/vmlinuz-4.2.0-35-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-35-generic /boot/vmlinuz-4.2.0-35-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-35-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.2.0-35-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.2.0-35-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.2.0-36-generic (4.2.0-36.42~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-36-generic /boot/vmlinuz-4.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-36-generic /boot/vmlinuz-4.2.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-36-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.2.0-36-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.2.0-36-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.2.0-30-generic (4.2.0-30.36~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
update-initramfs: Deleting /boot/initrd.img-4.2.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-42-generic
Found initrd image: /boot/initrd.img-4.2.0-42-generic
Found linux image: /boot/vmlinuz-4.2.0-41-generic
Found initrd image: /boot/initrd.img-4.2.0-41-generic
Found linux image: /boot/vmlinuz-4.2.0-38-generic
Found initrd image: /boot/initrd.img-4.2.0-38-generic
Found linux image: /boot/vmlinuz-4.2.0-36-generic
Found initrd image: /boot/initrd.img-4.2.0-36-generic
Found linux image: /boot/vmlinuz-4.2.0-35-generic
Found initrd image: /boot/initrd.img-4.2.0-35-generic
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-4.2.0-30-generic (4.2.0-30.36~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
Removing linux-image-4.2.0-34-generic (4.2.0-34.39~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-34-generic /boot/vmlinuz-4.2.0-34-generic
update-initramfs: Deleting /boot/initrd.img-4.2.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-34-generic /boot/vmlinuz-4.2.0-34-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-42-generic
Found initrd image: /boot/initrd.img-4.2.0-42-generic
Found linux image: /boot/vmlinuz-4.2.0-41-generic
Found initrd image: /boot/initrd.img-4.2.0-41-generic
Found linux image: /boot/vmlinuz-4.2.0-38-generic
Found initrd image: /boot/initrd.img-4.2.0-38-generic
Found linux image: /boot/vmlinuz-4.2.0-36-generic
Found initrd image: /boot/initrd.img-4.2.0-36-generic
Found linux image: /boot/vmlinuz-4.2.0-35-generic
Found initrd image: /boot/initrd.img-4.2.0-35-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-4.2.0-34-generic (4.2.0-34.39~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-34-generic /boot/vmlinuz-4.2.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-34-generic /boot/vmlinuz-4.2.0-34-generic
Removing linux-image-4.2.0-35-generic (4.2.0-35.40~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-35-generic /boot/vmlinuz-4.2.0-35-generic
update-initramfs: Deleting /boot/initrd.img-4.2.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-35-generic /boot/vmlinuz-4.2.0-35-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-42-generic
Found initrd image: /boot/initrd.img-4.2.0-42-generic
Found linux image: /boot/vmlinuz-4.2.0-41-generic
Found initrd image: /boot/initrd.img-4.2.0-41-generic
Found linux image: /boot/vmlinuz-4.2.0-38-generic
Found initrd image: /boot/initrd.img-4.2.0-38-generic
Found linux image: /boot/vmlinuz-4.2.0-36-generic
Found initrd image: /boot/initrd.img-4.2.0-36-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-4.2.0-35-generic (4.2.0-35.40~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-35-generic /boot/vmlinuz-4.2.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-35-generic /boot/vmlinuz-4.2.0-35-generic
Removing linux-image-4.2.0-36-generic (4.2.0-36.42~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-36-generic /boot/vmlinuz-4.2.0-36-generic
update-initramfs: Deleting /boot/initrd.img-4.2.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-36-generic /boot/vmlinuz-4.2.0-36-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-42-generic
Found initrd image: /boot/initrd.img-4.2.0-42-generic
Found linux image: /boot/vmlinuz-4.2.0-41-generic
Found initrd image: /boot/initrd.img-4.2.0-41-generic
Found linux image: /boot/vmlinuz-4.2.0-38-generic
Found initrd image: /boot/initrd.img-4.2.0-38-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-4.2.0-36-generic (4.2.0-36.42~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-36-generic /boot/vmlinuz-4.2.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-36-generic /boot/vmlinuz-4.2.0-36-generic
Errors were encountered while processing:
 linux-image-extra-4.2.0-30-generic
 linux-image-extra-4.2.0-34-generic
 linux-image-extra-4.2.0-35-generic
 linux-image-extra-4.2.0-36-generic



```

But here is the output after

```
linux@linuxlaptop:~$ dpkg -l | grep linux-ii  linux-firmware                                        1.127.22                                            all          Firmware for Linux kernel drivers
iU  linux-generic-lts-wily                                4.2.0.42.34                                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.2.0-30                                4.2.0-30.36~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-30-generic                        4.2.0-30.36~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-34                                4.2.0-34.39~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-34-generic                        4.2.0-34.39~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-35                                4.2.0-35.40~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-35-generic                        4.2.0-35.40~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-36                                4.2.0-36.42~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-36-generic                        4.2.0-36.42~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-38                                4.2.0-38.45~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-38-generic                        4.2.0-38.45~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-41                                4.2.0-41.48~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-41-generic                        4.2.0-41.48~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-42                                4.2.0-42.49~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-42-generic                        4.2.0-42.49~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-wily                        4.2.0.42.34                                         amd64        Generic Linux kernel headers
rc  linux-image-4.2.0-27-generic                          4.2.0-27.32~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-38-generic                          4.2.0-38.45~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-41-generic                          4.2.0-41.48~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-42-generic                          4.2.0-42.49~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-27-generic                    4.2.0-27.32~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
pH  linux-image-extra-4.2.0-30-generic                    4.2.0-30.36~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
pH  linux-image-extra-4.2.0-34-generic                    4.2.0-34.39~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
pH  linux-image-extra-4.2.0-35-generic                    4.2.0-35.40~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
pH  linux-image-extra-4.2.0-36-generic                    4.2.0-36.42~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-38-generic                    4.2.0-38.45~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-41-generic                    4.2.0-41.48~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
iF  linux-image-extra-4.2.0-42-generic                    4.2.0-42.49~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
iU  linux-image-generic-lts-wily                          4.2.0.42.34                                         amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-92.139                                       amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies



```

So do I have room now and should I upgrade 16.04?  I want a stable system that is supported by wonderful people like you guys since I don't know linux well.


Also when I rebooted, I didn't get the error so that is fixed. I did run sudo apt-get install -f and got the following

```
linux@linuxlaptop:~$ sudo apt-get install -f[sudo] password for linux: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-4.2.0-30-generic linux-image-extra-4.2.0-34-generic
  linux-image-extra-4.2.0-35-generic linux-image-extra-4.2.0-36-generic
0 upgraded, 0 newly installed, 4 to remove and 15 not upgraded.
7 not fully installed or removed.
After this operation, 646 MB disk space will be freed.
Do you want to continue? [Y/n] 



```

But said no.  Does it seem like this would remove the kernal that I am using?

---

### Post by Bashing-om on 2016-07-31
nzdreamer55; OK // so;

We run:
```

sudo dpkg -P linux-image-4.2.0-{33,34,35,36,38}-generic 
sudo dpkg -P linux-headers-4.2.0-{33,34,35,36,38}-generic 
sudo dpkg -P linux-headers-4.2.0-{33,34,35,36,38}
sudo dpkg -P linux-image-extra-4.2.0-{33,34,35,36,38}-generic

```

When these complete .. we try and complete the 4.2.0-42 kernel install:
```

sudo apt update
sudo apt upgrade
sudo apt -f install

```

And when this completes show me a now:
```

dpkg -l | grep linux-

```
to see what there is for final cleanup.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2016-07-31
Hmmm!
Not sure that worked, though the actual kernels seem to have been removed, but to be sure let's see the output of ```
df -h /boot
```
EDIT:
Ninja'd by Bashing-om who is much better at this **dpkg -P** stuff than I am, so I'll leave you in his good hands.

---

### Post by deadflowr on 2016-07-31
> **nzdreamer55 said:**
> 
Also when I rebooted, I didn't get the error so that is fixed. I did run sudo apt-get install -f and got the following

```
linux@linuxlaptop:~$ sudo apt-get install -f[sudo] password for linux: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-4.2.0-30-generic linux-image-extra-4.2.0-34-generic
  linux-image-extra-4.2.0-35-generic linux-image-extra-4.2.0-36-generic
0 upgraded, 0 newly installed, 4 to remove and 15 not upgraded.
7 not fully installed or removed.
After this operation, 646 MB disk space will be freed.
Do you want to continue? [Y/n] 
```

But said no.  Does it seem like this would remove the kernal that I am using?

Did you switch kernels on the reboot?  
Because the current kernel you where using was 4.2.0-42, which is not listed there in the install -f output.
So it would not be removed, in that case.

---

### Post by Bashing-om on 2016-07-31
@ajgreeny; Sorry.

Did not note that you had posted .. did not mean to step on your toes !

@ nzdreamer55; Where do we stand presently ?
show us a brand new output:
```

dpkg -l | grep linux-

```
to see what we need to do now.

[INDENT][INDENT]together we do
[/INDENT][/INDENT]

---

### Post by nzdreamer55 on 2016-07-31
OK so that took a bit but I follow what [COLOR=#000000]Bashing-om said and here is the output of dpkg[/COLOR]

```
linux@linuxlaptop:~$ dpkg -l | grep linux-ii  linux-firmware                                        1.127.22                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-wily                                4.2.0.42.34                                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.2.0-30                                4.2.0-30.36~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-30-generic                        4.2.0-30.36~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-41                                4.2.0-41.48~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-41-generic                        4.2.0-41.48~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-42                                4.2.0-42.49~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-42-generic                        4.2.0-42.49~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-wily                        4.2.0.42.34                                         amd64        Generic Linux kernel headers
rc  linux-image-4.2.0-27-generic                          4.2.0-27.32~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
pi  linux-image-4.2.0-38-generic                          4.2.0-38.45~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-41-generic                          4.2.0-41.48~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-42-generic                          4.2.0-42.49~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-27-generic                    4.2.0-27.32~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-30-generic                    4.2.0-30.36~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-41-generic                    4.2.0-41.48~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-42-generic                    4.2.0-42.49~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-wily                          4.2.0.42.34                                         amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-92.139                                       amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

Are there still old Kernels present?

---

### Post by Bashing-om on 2016-07-31
nzdreamer55; Yuk !

> **nzdreamer55 said:**
> OK so that took a bit but I follow what [COLOR=#000000]Bashing-om said and here is the output of dpkg[/COLOR]

```
linux@linuxlaptop:~$ dpkg -l | grep linux-ii  linux-firmware                                        1.127.22                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-wily                                4.2.0.42.34                                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.2.0-30                                4.2.0-30.36~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-30-generic                        4.2.0-30.36~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-41                                4.2.0-41.48~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-41-generic                        4.2.0-41.48~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-42                                4.2.0-42.49~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-42-generic                        4.2.0-42.49~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-wily                        4.2.0.42.34                                         amd64        Generic Linux kernel headers
rc  linux-image-4.2.0-27-generic                          4.2.0-27.32~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
pi  linux-image-4.2.0-38-generic                          4.2.0-38.45~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-41-generic                          4.2.0-41.48~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-42-generic                          4.2.0-42.49~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-27-generic                    4.2.0-27.32~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-30-generic                    4.2.0-30.36~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-41-generic                    4.2.0-41.48~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-42-generic                    4.2.0-42.49~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-wily                          4.2.0.42.34                                         amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-92.139                                       amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

Are there still old Kernels present?

Yeah .. we may have a mess on our hands.

I want at this time that you understand what we are doing and how:
Just for edification, do:
```

dpkg -l linux-generic-lts-wily

```
in that output note that the "legend" is provided .. such that you see that 'ii' means desired status is Installed and the actual status is also Installed. where as " pi " is Purge but still installed .. and "rc' is Removed but Config files remain .. we may have to get dirty now to correct this.

So let's look and see if we must get dirty .. show us :
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-

```

[INDENT][INDENT]how low can we go
[/INDENT][/INDENT]

---

### Post by nzdreamer55 on 2016-07-31
Thanks so much for your time.  Here are the outputs

```
linux@linuxlaptop:~$ ls -al /usr/src/total 32
drwxr-xr-x  8 root root 4096 Jul 31 11:13 .
drwxr-xr-x 10 root root 4096 Feb 17 15:12 ..
drwxr-xr-x 24 root root 4096 Mar 13 16:33 linux-headers-4.2.0-30
drwxr-xr-x  7 root root 4096 Mar 13 16:34 linux-headers-4.2.0-30-generic
drwxr-xr-x 24 root root 4096 Jun 30 17:55 linux-headers-4.2.0-41
drwxr-xr-x  7 root root 4096 Jun 30 17:55 linux-headers-4.2.0-41-generic
drwxr-xr-x 24 root root 4096 Jul 27 19:26 linux-headers-4.2.0-42
drwxr-xr-x  7 root root 4096 Jul 27 19:26 linux-headers-4.2.0-42-generic
linux@linuxlaptop:~$ ls -al /lib/modules/
total 24
drwxr-xr-x  6 root root 4096 Jul 31 11:13 .
drwxr-xr-x 23 root root 4096 May 12 13:28 ..
drwxr-xr-x  2 root root 4096 Jul 31 11:17 4.2.0-30-generic
drwxr-xr-x  5 root root 4096 Jul 31 11:14 4.2.0-38-generic
drwxr-xr-x  5 root root 4096 Jun 30 17:56 4.2.0-41-generic
drwxr-xr-x  5 root root 4096 Jul 31 11:17 4.2.0-42-generic
linux@linuxlaptop:~$ ls -al /boot/
total 97402
drwxr-xr-x  4 root root     3072 Jul 31 11:17 .
drwxr-xr-x 23 root root     4096 Jul 27 19:27 ..
-rw-r--r--  1 root root  1313411 Jun  9 03:51 abi-4.2.0-38-generic
-rw-r--r--  1 root root  1313640 Jun 24 11:37 abi-4.2.0-41-generic
-rw-r--r--  1 root root  1313590 Jun 29 15:31 abi-4.2.0-42-generic
-rw-r--r--  1 root root   184897 Jun  9 03:51 config-4.2.0-38-generic
-rw-r--r--  1 root root   184897 Jun 24 11:37 config-4.2.0-41-generic
-rw-r--r--  1 root root   184934 Jun 29 15:31 config-4.2.0-42-generic
drwxr-xr-x  5 root root     1024 Jul 31 11:17 grub
-rw-r--r--  1 root root  3324767 Jul 31 11:17 initrd.img-4.2.0-30-generic
-rw-r--r--  1 root root  3324799 Jul 31 11:14 initrd.img-4.2.0-34-generic
-rw-r--r--  1 root root  3324789 Jul 31 11:14 initrd.img-4.2.0-35-generic
-rw-r--r--  1 root root  3324768 Jul 31 11:14 initrd.img-4.2.0-36-generic
-rw-r--r--  1 root root  6732634 Jul 31 11:14 initrd.img-4.2.0-38-generic
-rw-r--r--  1 root root 21378657 Jun 30 17:56 initrd.img-4.2.0-41-generic
-rw-r--r--  1 root root 21378113 Jul 31 11:17 initrd.img-4.2.0-42-generic
drwx------  2 root root    12288 Mar 13 15:30 lost+found
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3759342 Jun  9 03:51 System.map-4.2.0-38-generic
-rw-------  1 root root  3759492 Jun 24 11:37 System.map-4.2.0-41-generic
-rw-------  1 root root  3760051 Jun 29 15:31 System.map-4.2.0-42-generic
-rw-------  1 root root  6732272 Jun  9 03:51 vmlinuz-4.2.0-38-generic
-rw-------  1 root root  6734768 Jun 24 11:37 vmlinuz-4.2.0-41-generic
-rw-------  1 root root  6736496 Jun 29 15:31 vmlinuz-4.2.0-42-generic
linux@linuxlaptop:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.22                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-wily                                4.2.0.42.34                                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.2.0-30                                4.2.0-30.36~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-30-generic                        4.2.0-30.36~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-41                                4.2.0-41.48~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-41-generic                        4.2.0-41.48~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-42                                4.2.0-42.49~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-42-generic                        4.2.0-42.49~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-wily                        4.2.0.42.34                                         amd64        Generic Linux kernel headers
rc  linux-image-4.2.0-27-generic                          4.2.0-27.32~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
pi  linux-image-4.2.0-38-generic                          4.2.0-38.45~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-41-generic                          4.2.0-41.48~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-42-generic                          4.2.0-42.49~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-27-generic                    4.2.0-27.32~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-30-generic                    4.2.0-30.36~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-41-generic                    4.2.0-41.48~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-42-generic                    4.2.0-42.49~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-wily                          4.2.0.42.34                                         amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-92.139                                       amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

And

```
linux@linuxlaptop:~$ dpkg -l linux-generic-lts-wily
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                         Version                     Architecture                Description
+++-============================================-===========================-===========================-==============================================================================================
ii  linux-generic-lts-wily                       4.2.0.42.34                 amd64                       Complete Generic Linux kernel and headers



```

---

### Post by Bashing-om on 2016-07-31
nzdreamer55; Welp ....

As you can see .. miss-matches on what all is installed where ... we are going to get dirty ..

For others viewing this thread ... getting to this point is not a good thing ! .. and doing what we have to do ... is also not a good thing .
It is a DIRTY solution to a bad situation .. and one MUST exercise caution and care !

@nzdreamer55, give me a bit of time to clear my mind and come up with the proper procedure .

[INDENT][INDENT][INDENT]I will be Baaccckkk
[/INDENT][/INDENT][/INDENT]

---

### Post by nzdreamer55 on 2016-07-31
No problem.  I'll monitor the thread and give you feedback as needed.

---

### Post by deadflowr on 2016-07-31
> **Bashing-om said:**
> nzdreamer55; Welp ....

As you can see .. miss-matches on what all is installed where ... we are going to get dirty ..

For others viewing this thread ... getting to this point is not a good thing ! .. and doing what we have to do ... is also not a good thing .
It is a DIRTY solution to a bad situation .. and one MUST exercise caution and care !

@nzdreamer55, give me a bit of time to clear my mind and come up with the proper procedure .

[INDENT][INDENT][INDENT]I will be Baaccckkk
[/INDENT][/INDENT][/INDENT]

I'm a glass-half-full kinda guy, so as I see it, if the removal of those 33,34,35,36,et cetra kernels freed space, that helps tremendously.
Dirty? Sure. But at least there should be wiggle-room, now.

Which leads us to need to know what the new output for the df -h command is?
/boot should be a tad lighter, I would think...

My 2 cents on it.
At least

---

### Post by Bashing-om on 2016-07-31
@deadflowr; Hey hey ..

wiggle room is a thought // maybe we see just how smart 'autoremove' is ( in 16.04 it has gotten a lot smarter).
We can not make the situation much worse. Let's see what magic the package manager can work.

@nzdreamer55; Uh Huh ...

Let's give:
```

sudo apt-get autoremove

```
a whirl. See if the package manager will make things all right .

[INDENT][INDENT]hey. it could happen
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2016-07-31
> **deadflowr said:**
> I'm a glass-half-full kinda guy, so as I see it, if the removal of those 33,34,35,36,et cetra kernels freed space, that helps tremendously.
Dirty? Sure. But at least there should be wiggle-room, now.

Which leads us to need to know what the new output for the df -h command is?
/boot should be a tad lighter, I would think...

My 2 cents on it.
At least
+1
That was my thoughts as well, and if there is enough room, surely it may now be easier to use apt-get (or my favourite, synaptic) to remove any unwanted packages that remain.  It is very easy with synaptic to search for kernels and related packages with specific number versions simply by searching, name only, for packages with that version number, eg 4.2.0-30 and 4.2.0-38, etc etc, and remove completely using synaptic any that are remaining on the system but no longer needed.

---

### Post by nzdreamer55 on 2016-07-31
So I did sudo apt-get autoremove

```
linux@linuxlaptop:~$ sudo apt-get autoremove[sudo] password for linux: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
linux@linuxlaptop:~$ 



```

Do I need to run autoremove now?

sudo autoremove?

---

### Post by nzdreamer55 on 2016-07-31
Should have posted this too

```
linux@linuxlaptop:~$ df -hFilesystem                      Size  Used Avail Use% Mounted on
udev                            985M  4.0K  985M   1% /dev
tmpfs                           200M  1.2M  198M   1% /run
/dev/dm-0                        57G  9.8G   44G  19% /
none                            4.0K     0  4.0K   0% /sys/fs/cgroup
none                            5.0M     0  5.0M   0% /run/lock
none                            996M   11M  986M   2% /run/shm
none                            100M   52K  100M   1% /run/user
/dev/sda1                       236M  104M  120M  47% /boot
//192.168.1.170/Film.Pool        14T   12T  2.4T  83% /home/linux/mnt/Film.Pool
//192.168.1.170/Series.Pool      18T   16T  1.5T  92% /home/linux/mnt/Series.Pool
//192.168.1.170/Om              3.7T  2.1T  1.6T  57% /home/linux/mnt/Om
//192.168.1.104/OffLineStorage  1.8T  908G  922G  50% /home/linux/mnt/Diskstation
/dev/sdb1                       932G  245G  687G  27% /media/linux/1TB.Scratch



```

---

### Post by Bashing-om on 2016-07-31
nzdreamer55; Yeah ....

Things do look a lot bright, now do they not ?

However, that:
> 
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

makes we wonder what and why ..

let's do a "simulation" and see what the package manager has in mind:
```

sudo apt -s full-upgrade

```
depending on what the package manager tells us, is what we do next.

[INDENT][INDENT]easy does it
[/INDENT][/INDENT]

---

### Post by nzdreamer55 on 2016-07-31
Here is what it says

"linux@linuxlaptop:~$ sudo apt -s full-upgrade[sudo] password for linux: 
E: Command line option 's' [from -s] is not known.
"

---

### Post by Bashing-om on 2016-07-31
nzdreamer55; Well !

Some things 'apt' did not inherit from 'apt-get' - as I live and learn .
try as:
```

sudo apt-get -s dist-upgrade

```
That is NOT a distribution upgrade, just for upgrading what is presently installed .. and the 's' to "simulate' .

[INDENT][INDENT]sometimes,
[INDENT][INDENT][INDENT]I just do not know any better
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nzdreamer55 on 2016-07-31
Here you go

```

linux@linuxlaptop:~$ sudo apt-get -s dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libunity-core-6.0-9 unity unity-services
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Inst unity [7.2.6+14.04.20151021-0ubuntu1] (7.2.6+14.04.20160408-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libunity-core-6.0-9 [7.2.6+14.04.20151021-0ubuntu1] (7.2.6+14.04.20160408-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst unity-services [7.2.6+14.04.20151021-0ubuntu1] (7.2.6+14.04.20160408-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf unity-services (7.2.6+14.04.20160408-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libunity-core-6.0-9 (7.2.6+14.04.20160408-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf unity (7.2.6+14.04.20160408-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])

```

---

### Post by Bashing-om on 2016-07-31
nzdreamer55; Huh ??

Now that has nothing to do with the kernels .. I must wonder what is up that these updates have not to this time been installed .. and why they may have been held back ! disk space issue ?? could well be .. as that is now behind us.

If It Were me, I would go ahead and install the updates. Paying very close attention to what the package manager reports;
```

sudo apt full-upgrade

```
and then we return to our kernel issue.

[INDENT][INDENT]we like it clean behind us
[/INDENT][/INDENT]

---

### Post by nzdreamer55 on 2016-07-31
OK done.  where to next?

```

linux@linuxlaptop:~$ sudo apt full-upgrade
[sudo] password for linux: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libunity-core-6.0-9 unity unity-services
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,985 kB of archives.
After this operation, 3,072 B disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main unity amd64 7.2.6+14.04.20160408-0ubuntu1 [1,517 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libunity-core-6.0-9 amd64 7.2.6+14.04.20160408-0ubuntu1 [435 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main unity-services amd64 7.2.6+14.04.20160408-0ubuntu1 [33.3 kB]
Fetched 1,985 kB in 1s (1,243 kB/s)      
(Reading database ... 257422 files and directories currently installed.)
Preparing to unpack .../unity_7.2.6+14.04.20160408-0ubuntu1_amd64.deb ...
Unpacking unity (7.2.6+14.04.20160408-0ubuntu1) over (7.2.6+14.04.20151021-0ubuntu1) ...
Preparing to unpack .../libunity-core-6.0-9_7.2.6+14.04.20160408-0ubuntu1_amd64.deb ...
Unpacking libunity-core-6.0-9 (7.2.6+14.04.20160408-0ubuntu1) over (7.2.6+14.04.20151021-0ubuntu1) ...
Preparing to unpack .../unity-services_7.2.6+14.04.20160408-0ubuntu1_amd64.deb ...
Unpacking unity-services (7.2.6+14.04.20160408-0ubuntu1) over (7.2.6+14.04.20151021-0ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
Setting up unity-services (7.2.6+14.04.20160408-0ubuntu1) ...
Setting up libunity-core-6.0-9 (7.2.6+14.04.20160408-0ubuntu1) ...
Setting up unity (7.2.6+14.04.20160408-0ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.9) ...

```

---

### Post by Bashing-om on 2016-07-31
nzdreamer55; Uh Huh //looks good .

Back to our kernels/
What now:
```

sudo apt update
sudo apt upgrade
sudo apt -f install
dpkg -l | grep linux-

```
see where we stand .

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nzdreamer55 on 2016-07-31
Here it is

sudo apt update

```

linux@linuxlaptop:~$ sudo apt update
[sudo] password for linux: 
Ign http://dl.google.com stable InRelease
Hit http://dl.google.com stable Release.gpg                                    
Hit http://security.ubuntu.com trusty-security InRelease                       
Hit http://dl.google.com stable Release                                        
Ign http://us.archive.ubuntu.com trusty InRelease                              
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:1 http://us.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Hit http://security.ubuntu.com trusty-security/main Sources                    
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Ign http://dl.google.com stable/main Translation-en                            
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:2 http://us.archive.ubuntu.com trusty-updates/main Sources [379 kB]        
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Get:3 http://us.archive.ubuntu.com trusty-updates/restricted Sources [5,352 B] 
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Get:4 http://us.archive.ubuntu.com trusty-updates/universe Sources [160 kB]    
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Get:5 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,929 B] 
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Get:6 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [876 kB] 
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Get:7 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Get:8 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [367 kB]
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://ppa.launchpad.net trusty Release                                    
Get:9 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.2 kB]
Get:10 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [838 kB] 
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:11 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:12 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [368 kB]
Get:13 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.6 kB]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en   
Ign http://extras.ubuntu.com trusty/main Translation-en_US                  
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/main Sources            
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://us.archive.ubuntu.com trusty Release   
Hit http://us.archive.ubuntu.com trusty/main Sources
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 3,123 kB in 10s (297 kB/s)                                             
Reading package lists... Done

```

sudo apt upgrade

```

sudo apt upgradlinux@linuxlaptop:~$ sudo apt upgrade
[sudo] password for linux: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

sudo apt -f install

```

linux@linuxlaptop:~$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

dpkg -l | grep linux-

```

linux@linuxlaptop:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.22                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-wily                                4.2.0.42.34                                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.2.0-30                                4.2.0-30.36~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-30-generic                        4.2.0-30.36~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-41                                4.2.0-41.48~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-41-generic                        4.2.0-41.48~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-42                                4.2.0-42.49~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-42-generic                        4.2.0-42.49~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-wily                        4.2.0.42.34                                         amd64        Generic Linux kernel headers
rc  linux-image-4.2.0-27-generic                          4.2.0-27.32~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
pi  linux-image-4.2.0-38-generic                          4.2.0-38.45~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-41-generic                          4.2.0-41.48~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-42-generic                          4.2.0-42.49~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-27-generic                    4.2.0-27.32~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-30-generic                    4.2.0-30.36~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-41-generic                    4.2.0-41.48~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-42-generic                    4.2.0-42.49~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-wily                          4.2.0.42.34                                         amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-92.139                                       amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Bashing-om on 2016-07-31
nzdreamer55; Well now ...

That looks pretty dog gone good .

A spot or so we can try and clean up:
```

sudo dpkg -P linux-headers-4.2.0-30-generic
sudo dpkg -P linux-headers-4.2.0-30
sudo dpkg -P linux-image-4.2.0-38-generic

```

Pending these results is one more little bit of cleanup.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by nzdreamer55 on 2016-07-31
OMG I think it is getting close to being done

```

linux@linuxlaptop:~$ sudo dpkg -P linux-headers-4.2.0-30-generic
[sudo] password for linux: 
(Reading database ... 257421 files and directories currently installed.)
Removing linux-headers-4.2.0-30-generic (4.2.0-30.36~14.04.1) ...
dpkg: warning: while removing linux-headers-4.2.0-30-generic, directory '/lib/modules/4.2.0-30-generic' not empty so not removed
linux@linuxlaptop:~$ sudo dpkg -P linux-headers-4.2.0-30
(Reading database ... 247951 files and directories currently installed.)
Removing linux-headers-4.2.0-30 (4.2.0-30.36~14.04.1) ...
linux@linuxlaptop:~$ sudo dpkg -P linux-image-4.2.0-38-generic
(Reading database ... 231631 files and directories currently installed.)
Removing linux-image-4.2.0-38-generic (4.2.0-38.45~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-38-generic /boot/vmlinuz-4.2.0-38-generic
update-initramfs: Deleting /boot/initrd.img-4.2.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-38-generic /boot/vmlinuz-4.2.0-38-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-42-generic
Found initrd image: /boot/initrd.img-4.2.0-42-generic
Found linux image: /boot/vmlinuz-4.2.0-41-generic
Found initrd image: /boot/initrd.img-4.2.0-41-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-4.2.0-38-generic (4.2.0-38.45~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-38-generic /boot/vmlinuz-4.2.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-38-generic /boot/vmlinuz-4.2.0-38-generic
linux@linuxlaptop:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.22                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-wily                                4.2.0.42.34                                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.2.0-41                                4.2.0-41.48~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-41-generic                        4.2.0-41.48~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-42                                4.2.0-42.49~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-42-generic                        4.2.0-42.49~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-wily                        4.2.0.42.34                                         amd64        Generic Linux kernel headers
rc  linux-image-4.2.0-27-generic                          4.2.0-27.32~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-41-generic                          4.2.0-41.48~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-42-generic                          4.2.0-42.49~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-27-generic                    4.2.0-27.32~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-30-generic                    4.2.0-30.36~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-41-generic                    4.2.0-41.48~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-42-generic                    4.2.0-42.49~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-wily                          4.2.0.42.34                                         amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-92.139                                       amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Bashing-om on 2016-07-31
nzdreamer55; Yeah, Uh Huh ..

That do look really good .
confirmation :
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/

```
that all entries now agree .

If so .. we finalize the cleanup removing the 'rc' marked packages .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by nzdreamer55 on 2016-07-31
OK here it is

```

linux@linuxlaptop:~$ ls -al /usr/src/
total 24
drwxr-xr-x  6 root root 4096 Jul 31 13:57 .
drwxr-xr-x 10 root root 4096 Feb 17 15:12 ..
drwxr-xr-x 24 root root 4096 Jun 30 17:55 linux-headers-4.2.0-41
drwxr-xr-x  7 root root 4096 Jun 30 17:55 linux-headers-4.2.0-41-generic
drwxr-xr-x 24 root root 4096 Jul 27 19:26 linux-headers-4.2.0-42
drwxr-xr-x  7 root root 4096 Jul 27 19:26 linux-headers-4.2.0-42-generic
linux@linuxlaptop:~$ ls -al /lib/modules/
total 20
drwxr-xr-x  5 root root 4096 Jul 31 13:58 .
drwxr-xr-x 23 root root 4096 May 12 13:28 ..
drwxr-xr-x  2 root root 4096 Jul 31 13:57 4.2.0-30-generic
drwxr-xr-x  5 root root 4096 Jun 30 17:56 4.2.0-41-generic
drwxr-xr-x  5 root root 4096 Jul 31 11:17 4.2.0-42-generic
linux@linuxlaptop:~$ ls -al /boot/
total 79039
drwxr-xr-x  4 root root     3072 Jul 31 13:58 .
drwxr-xr-x 23 root root     4096 Jul 27 19:27 ..
-rw-r--r--  1 root root  1313640 Jun 24 11:37 abi-4.2.0-41-generic
-rw-r--r--  1 root root  1313590 Jun 29 15:31 abi-4.2.0-42-generic
-rw-r--r--  1 root root   184897 Jun 24 11:37 config-4.2.0-41-generic
-rw-r--r--  1 root root   184934 Jun 29 15:31 config-4.2.0-42-generic
drwxr-xr-x  5 root root     1024 Jul 31 13:58 grub
-rw-r--r--  1 root root  3324767 Jul 31 11:17 initrd.img-4.2.0-30-generic
-rw-r--r--  1 root root  3324799 Jul 31 11:14 initrd.img-4.2.0-34-generic
-rw-r--r--  1 root root  3324789 Jul 31 11:14 initrd.img-4.2.0-35-generic
-rw-r--r--  1 root root  3324768 Jul 31 11:14 initrd.img-4.2.0-36-generic
-rw-r--r--  1 root root 21378657 Jun 30 17:56 initrd.img-4.2.0-41-generic
-rw-r--r--  1 root root 21378113 Jul 31 11:17 initrd.img-4.2.0-42-generic
drwx------  2 root root    12288 Mar 13 15:30 lost+found
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3759492 Jun 24 11:37 System.map-4.2.0-41-generic
-rw-------  1 root root  3760051 Jun 29 15:31 System.map-4.2.0-42-generic
-rw-------  1 root root  6734768 Jun 24 11:37 vmlinuz-4.2.0-41-generic
-rw-------  1 root root 

```

---

### Post by Bashing-om on 2016-07-31
nzdreamer55; Welp ,,

I could hope ..

Let's do this:
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

Now look and see what remains:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-

```

[INDENT][INDENT]close;
[INDENT][INDENT]oh so close
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nzdreamer55 on 2016-07-31
Well it looks like it removed some files, but there is still a folder 

drwxr-xr-x  2 root root 4096 Jul 31 13:57 4.2.0-30-generic

I don't know if this matters.

```

linux@linuxlaptop:~$ dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
[sudo] password for linux: 
(Reading database ... 230601 files and directories currently installed.)
Removing libjansson4:amd64 (2.5-2) ...
Purging configuration files for libjansson4:amd64 (2.5-2) ...
Removing libntdb1:amd64 (1.0-2ubuntu1) ...
Purging configuration files for libntdb1:amd64 (1.0-2ubuntu1) ...
Removing linux-image-4.2.0-27-generic (4.2.0-27.32~14.04.1) ...
Purging configuration files for linux-image-4.2.0-27-generic (4.2.0-27.32~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-27-generic /boot/vmlinuz-4.2.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-27-generic /boot/vmlinuz-4.2.0-27-generic
Removing linux-image-extra-4.2.0-27-generic (4.2.0-27.32~14.04.1) ...
Purging configuration files for linux-image-extra-4.2.0-27-generic (4.2.0-27.32~14.04.1) ...
Removing linux-image-extra-4.2.0-30-generic (4.2.0-30.36~14.04.1) ...
Purging configuration files for linux-image-extra-4.2.0-30-generic (4.2.0-30.36~14.04.1) ...
linux@linuxlaptop:~$ ls -al /usr/src/
total 24
drwxr-xr-x  6 root root 4096 Jul 31 13:57 .
drwxr-xr-x 10 root root 4096 Feb 17 15:12 ..
drwxr-xr-x 24 root root 4096 Jun 30 17:55 linux-headers-4.2.0-41
drwxr-xr-x  7 root root 4096 Jun 30 17:55 linux-headers-4.2.0-41-generic
drwxr-xr-x 24 root root 4096 Jul 27 19:26 linux-headers-4.2.0-42
drwxr-xr-x  7 root root 4096 Jul 27 19:26 linux-headers-4.2.0-42-generic
linux@linuxlaptop:~$ ls -al /lib/modules/
total 20
drwxr-xr-x  5 root root 4096 Jul 31 13:58 .
drwxr-xr-x 23 root root 4096 May 12 13:28 ..
drwxr-xr-x  2 root root 4096 Jul 31 13:57 4.2.0-30-generic
drwxr-xr-x  5 root root 4096 Jun 30 17:56 4.2.0-41-generic
drwxr-xr-x  5 root root 4096 Jul 31 11:17 4.2.0-42-generic
linux@linuxlaptop:~$ ls -al /boot/
total 79039
drwxr-xr-x  4 root root     3072 Jul 31 13:58 .
drwxr-xr-x 23 root root     4096 Jul 27 19:27 ..
-rw-r--r--  1 root root  1313640 Jun 24 11:37 abi-4.2.0-41-generic
-rw-r--r--  1 root root  1313590 Jun 29 15:31 abi-4.2.0-42-generic
-rw-r--r--  1 root root   184897 Jun 24 11:37 config-4.2.0-41-generic
-rw-r--r--  1 root root   184934 Jun 29 15:31 config-4.2.0-42-generic
drwxr-xr-x  5 root root     1024 Jul 31 13:58 grub
-rw-r--r--  1 root root  3324767 Jul 31 11:17 initrd.img-4.2.0-30-generic
-rw-r--r--  1 root root  3324799 Jul 31 11:14 initrd.img-4.2.0-34-generic
-rw-r--r--  1 root root  3324789 Jul 31 11:14 initrd.img-4.2.0-35-generic
-rw-r--r--  1 root root  3324768 Jul 31 11:14 initrd.img-4.2.0-36-generic
-rw-r--r--  1 root root 21378657 Jun 30 17:56 initrd.img-4.2.0-41-generic
-rw-r--r--  1 root root 21378113 Jul 31 11:17 initrd.img-4.2.0-42-generic
drwx------  2 root root    12288 Mar 13 15:30 lost+found
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3759492 Jun 24 11:37 System.map-4.2.0-41-generic
-rw-------  1 root root  3760051 Jun 29 15:31 System.map-4.2.0-42-generic
-rw-------  1 root root  6734768 Jun 24 11:37 vmlinuz-4.2.0-41-generic
-rw-------  1 root root  6736496 Jun 29 15:31 vmlinuz-4.2.0-42-generic
linux@linuxlaptop:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.22                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-wily                                4.2.0.42.34                                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.2.0-41                                4.2.0-41.48~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-41-generic                        4.2.0-41.48~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-42                                4.2.0-42.49~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-42-generic                        4.2.0-42.49~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-wily                        4.2.0.42.34                                         amd64        Generic Linux kernel headers
ii  linux-image-4.2.0-41-generic                          4.2.0-41.48~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-42-generic                          4.2.0-42.49~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-41-generic                    4.2.0-41.48~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-42-generic                    4.2.0-42.49~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-wily                          4.2.0.42.34                                         amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-92.139                                       amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
linux@linuxlaptop:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.22                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-wily                                4.2.0.42.34                                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.2.0-41                                4.2.0-41.48~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-41-generic                        4.2.0-41.48~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-42                                4.2.0-42.49~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-42-generic                        4.2.0-42.49~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-wily                        4.2.0.42.34                                         amd64        Generic Linux kernel headers
ii  linux-image-4.2.0-41-generic                          4.2.0-41.48~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-42-generic                          4.2.0-42.49~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-41-generic                    4.2.0-41.48~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-42-generic                    4.2.0-42.49~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-wily                          4.2.0.42.34                                         amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-92.139                                       amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Bashing-om on 2016-07-31
nzdreamer55; Yeah ..

Probably of no import .. but let's make it squeaky clean .. in preparation for the release upgrade:

```

sudo rm -rf /lib/modules/4.2.0-30-generic*
sudo rm /boot/*-4.2.0-{30,34,35,36}-generic
sudo apt -f install
sudo apt purge linux-{headers,image}-4.2.0-{30,34,35,36}.*

```
As some of the kernels files are no longer present .. I can accept that the package manager will scream with the apt purge request . 
Let it ! I do think we are good .

Prior to rebooting .. let me see:
```

ls -al /vmlinuz*
ls -al /initrd*

```
let's make sure grub is happy with the state of the kernels .

[INDENT][INDENT]I do think so
[/INDENT][/INDENT]

---

### Post by nzdreamer55 on 2016-07-31
OK.  So I don't think much happened but here is the output from those commands
```

linux@linuxlaptop:~$ sudo rm -rf /lib/modules/4.2.0-30-generic*
[sudo] password for linux: 

linux@linuxlaptop:~$ sudo rm /boot/*-4.2.0-{30,34,35,36}-generic

linux@linuxlaptop:~$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

linux@linuxlaptop:~$ sudo apt purge linux-{headers,image}-4.2.0-{30,34,35,36}.*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-headers-4.2.0-30-generic' for regex 'linux-headers-4.2.0-30.*'
Note, selecting 'linux-headers-4.2.0-30' for regex 'linux-headers-4.2.0-30.*'
Note, selecting 'linux-headers-4.2.0-30-lowlatency' for regex 'linux-headers-4.2.0-30.*'
Note, selecting 'linux-headers-4.2.0-34-generic' for regex 'linux-headers-4.2.0-34.*'
Note, selecting 'linux-headers-4.2.0-34-lowlatency' for regex 'linux-headers-4.2.0-34.*'
Note, selecting 'linux-headers-4.2.0-34' for regex 'linux-headers-4.2.0-34.*'
Note, selecting 'linux-headers-4.2.0-35' for regex 'linux-headers-4.2.0-35.*'
Note, selecting 'linux-headers-4.2.0-35-generic' for regex 'linux-headers-4.2.0-35.*'
Note, selecting 'linux-headers-4.2.0-35-lowlatency' for regex 'linux-headers-4.2.0-35.*'
Note, selecting 'linux-headers-4.2.0-36-generic' for regex 'linux-headers-4.2.0-36.*'
Note, selecting 'linux-headers-4.2.0-36' for regex 'linux-headers-4.2.0-36.*'
Note, selecting 'linux-headers-4.2.0-36-lowlatency' for regex 'linux-headers-4.2.0-36.*'
Note, selecting 'linux-image-4.2.0-30-lowlatency' for regex 'linux-image-4.2.0-30.*'
Note, selecting 'linux-image-4.2.0-30-generic' for regex 'linux-image-4.2.0-30.*'
Note, selecting 'linux-image-4.2.0-34-generic' for regex 'linux-image-4.2.0-34.*'
Note, selecting 'linux-image-4.2.0-34-lowlatency' for regex 'linux-image-4.2.0-34.*'
Note, selecting 'linux-image-4.2.0-35-lowlatency' for regex 'linux-image-4.2.0-35.*'
Note, selecting 'linux-image-4.2.0-35-generic' for regex 'linux-image-4.2.0-35.*'
Note, selecting 'linux-image-4.2.0-36-generic' for regex 'linux-image-4.2.0-36.*'
Note, selecting 'linux-image-4.2.0-36-lowlatency' for regex 'linux-image-4.2.0-36.*'
Package 'linux-headers-4.2.0-30' is not installed, so not removed
Package 'linux-headers-4.2.0-30-generic' is not installed, so not removed
Package 'linux-headers-4.2.0-30-lowlatency' is not installed, so not removed
Package 'linux-headers-4.2.0-34' is not installed, so not removed
Package 'linux-headers-4.2.0-34-generic' is not installed, so not removed
Package 'linux-headers-4.2.0-34-lowlatency' is not installed, so not removed
Package 'linux-headers-4.2.0-35' is not installed, so not removed
Package 'linux-headers-4.2.0-35-generic' is not installed, so not removed
Package 'linux-headers-4.2.0-35-lowlatency' is not installed, so not removed
Package 'linux-headers-4.2.0-36' is not installed, so not removed
Package 'linux-headers-4.2.0-36-generic' is not installed, so not removed
Package 'linux-headers-4.2.0-36-lowlatency' is not installed, so not removed
Package 'linux-image-4.2.0-30-generic' is not installed, so not removed
Package 'linux-image-4.2.0-30-lowlatency' is not installed, so not removed
Package 'linux-image-4.2.0-34-generic' is not installed, so not removed
Package 'linux-image-4.2.0-34-lowlatency' is not installed, so not removed
Package 'linux-image-4.2.0-35-generic' is not installed, so not removed
Package 'linux-image-4.2.0-35-lowlatency' is not installed, so not removed
Package 'linux-image-4.2.0-36-generic' is not installed, so not removed
Package 'linux-image-4.2.0-36-lowlatency' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

linux@linuxlaptop:~$ ls -al /vmlinuz*
lrwxrwxrwx 1 root root 29 Jul 27 19:27 /vmlinuz -> boot/vmlinuz-4.2.0-42-generic
lrwxrwxrwx 1 root root 29 Jun 30 17:56 /vmlinuz.old -> boot/vmlinuz-4.2.0-41-generic

linux@linuxlaptop:~$ ls -al /initrd*
lrwxrwxrwx 1 root root 32 Jul 27 19:27 /initrd.img -> boot/initrd.img-4.2.0-42-generic
lrwxrwxrwx 1 root root 32 Jun 30 17:56 /initrd.img.old -> boot/initrd.img-4.2.0-41-generic

```

Should I reboot the computer?

---

### Post by Bashing-om on 2016-07-31
nzdreamer55;Yepper;

All finer than a frog's hair ..
Reboot and I bet we call this a done deal.

[INDENT][INDENT]were no step for a stepper
[/INDENT][/INDENT]

---

### Post by nzdreamer55 on 2016-07-31
Thanks.  Rebooted well.  Now should I update to 16.04?  Can I use the software updater?

---

### Post by Bashing-om on 2016-07-31
nzdreamer55; hey ..

Yeah .. upgrade to 16.04 asap .. no telling when the 15.10 repo will be turned down .
For the upgrade to 16.04 // make sure that you are not using a proprietary graphics driver . and IF you have PPAs check that these PPAs are still supported in 16.04 . Best practice I have seen for the long term is to disable the PPAs yourself rather than depending on the system to take care of it . Sometimes the system fails in this respect.

If and only IF you are satisfied that your space issue is now resolved:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]I will look forward to our next adventure
[/INDENT][/INDENT]

---

### Post by nzdreamer55 on 2016-07-31
Thanks.  I think that the space issue is solved.  I'll mark this as solved, but can you point me to how to uncheck the PPAs?

---

### Post by Bashing-om on 2016-07-31
nzdreamer55l Well ...

Only generally, As I do not run with the GUI you have .. unity .
But will be somewhat like in Software Center -> panel menu -> software sources (tab) other software . Uncheck them. That is the GUI way .

[INDENT][INDENT]just my bit to try and help
[/INDENT][/INDENT]

---

