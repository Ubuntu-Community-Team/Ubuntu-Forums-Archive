---
title: "Errors were encountered while processing:  linux-image-5.3.0-18-generic"
date: 2019-12-10
forum: General Help
---

### Post by townhill on 2019-12-10
I'm having problems with installing new packages,  I get the same error with any installation and it seems to relate to  linux-image-5.3.0-18-generic.  For instance, trying to install Handbrake I get the following (but is the same for all attempted installs).  Any help will be appreciated.  I see a couple of similar posts on the forum but they are nor recent.  I'm running Ubuntu 19.10

bob@MSI:~$ sudo apt-get install handbrake
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-5.3.0-18-generic
The following NEW packages will be installed:
  handbrake
0 upgraded, 1 newly installed, 1 to remove and 7 not upgraded.
4 not fully installed or removed.
Need to get 0 B/3,198 kB of archives.
After this operation, 5,771 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 228514 files and directories currently installed.)
Removing linux-image-5.3.0-18-generic (5.3.0-18.19+1) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.3.0-18-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 10: /etc/default/grub: nvidia-drm.modeset=1: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.3.0-18-generic (--remove):
 installed linux-image-5.3.0-18-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.3.0-18-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Bashing-om on 2019-12-10
townhill; Hey hey -

We have:
> 
1 to remove and 7 not upgraded.
4 not fully installed or removed.


And the current eoan kernel is " 5.3.0.24.28 [security]: amd64":
Let's try this:
```

sudo apt update
sudo apt full-upgrade

```

and post back these complete results.

[INDENT][INDENT]see where we go from here
[/INDENT][/INDENT]

---

### Post by townhill on 2019-12-10
so for sudo apt update I get 

bob@MSI:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  firefox firefox-locale-en libsmbclient libssh-4 libssh-gcrypt-4 libwbclient0
  samba-libs
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0 B/65.5 MB of archives.
After this operation, 2,600 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 228515 files and directories currently installed.)
Preparing to unpack .../0-libsmbclient_2%3a4.10.7+dfsg-0ubuntu2.3_amd64.deb ...
Unpacking libsmbclient:amd64 (2:4.10.7+dfsg-0ubuntu2.3) over (2:4.10.7+dfsg-0ubu
ntu2.2) ...
Preparing to unpack .../1-samba-libs_2%3a4.10.7+dfsg-0ubuntu2.3_amd64.deb ...
Unpacking samba-libs:amd64 (2:4.10.7+dfsg-0ubuntu2.3) over (2:4.10.7+dfsg-0ubunt
u2.2) ...
Preparing to unpack .../2-libwbclient0_2%3a4.10.7+dfsg-0ubuntu2.3_amd64.deb ...
Unpacking libwbclient0:amd64 (2:4.10.7+dfsg-0ubuntu2.3) over (2:4.10.7+dfsg-0ubu
ntu2.2) ...
Preparing to unpack .../3-firefox_71.0+build5-0ubuntu0.19.10.1_amd64.deb ...
Unpacking firefox (71.0+build5-0ubuntu0.19.10.1) over (70.0.1+build1-0ubuntu0.19
.10.1) ...
Preparing to unpack .../4-firefox-locale-en_71.0+build5-0ubuntu0.19.10.1_amd64.d
eb ...
Unpacking firefox-locale-en (71.0+build5-0ubuntu0.19.10.1) over (70.0.1+build1-0
ubuntu0.19.10.1) ...
Preparing to unpack .../5-libssh-4_0.9.0-1ubuntu1.3_amd64.deb ...
Unpacking libssh-4:amd64 (0.9.0-1ubuntu1.3) over (0.9.0-1ubuntu1) ...
Preparing to unpack .../6-libssh-gcrypt-4_0.9.0-1ubuntu1.3_amd64.deb ...
Unpacking libssh-gcrypt-4:amd64 (0.9.0-1ubuntu1.3) over (0.9.0-1ubuntu1) ...
Setting up libssh-gcrypt-4:amd64 (0.9.0-1ubuntu1.3) ...
Setting up firefox (71.0+build5-0ubuntu0.19.10.1) ...
Please restart all running instances of firefox, or you will experience problems
.
Setting up libwbclient0:amd64 (2:4.10.7+dfsg-0ubuntu2.3) ...
Setting up grub-pc (2.04-1ubuntu12.1) ...
/var/lib/dpkg/info/grub-pc.config: 10: /etc/default/grub: nvidia-drm.modeset=1: 
not found
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error ex
it status 127
Setting up linux-image-5.3.0-24-generic (5.3.0-24.26) ...
Setting up firefox-locale-en (71.0+build5-0ubuntu0.19.10.1) ...
Setting up libssh-4:amd64 (0.9.0-1ubuntu1.3) ...
dpkg: dependency problems prevent configuration of grub-efi-amd64-signed:
 grub-efi-amd64-signed depends on grub-efi-amd64 | grub-pc; however:
  Package grub-efi-amd64 is not installed.
  Package grub-pc is not configured yet.


dpkg: error processing package grub-efi-amd64-signed (--configure):
 dependency problems - leaving unconfigured
Setting up samba-libs:amd64 (2:4.10.7+dfsg-0ubuntu2.3) ...
No apport report written because the error message indicates its a followup erro
r from a previous failure.
                          Setting up libsmbclient:amd64 (2:4.10.7+dfsg-0ubuntu2.
3) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu1) ...
Processing triggers for mime-support (3.63ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.32.0-1ubuntu1) ...
Processing triggers for libc-bin (2.30-0ubuntu2) ...
Processing triggers for man-db (2.8.7-3) ...
Processing triggers for bamfdaemon (0.5.3+18.04.20180207.2-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for linux-image-5.3.0-24-generic (5.3.0-24.26) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.3.0-24-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.3.0-24-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 10: /etc/default/grub: nvidia-drm.modeset=1: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.3.0-24-generic (--configure):
 installed linux-image-5.3.0-24-generic package post-installation script subproc
ess returned error exit status 1
Errors were encountered while processing:
 grub-pc
 grub-efi-amd64-signed
 linux-image-5.3.0-24-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

and for sudo apt full-upgrade I get

bob@MSI:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  firefox firefox-locale-en libsmbclient libssh-4 libssh-gcrypt-4 libwbclient0
  samba-libs
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0 B/65.5 MB of archives.
After this operation, 2,600 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 228515 files and directories currently installed.)
Preparing to unpack .../0-libsmbclient_2%3a4.10.7+dfsg-0ubuntu2.3_amd64.deb ...
Unpacking libsmbclient:amd64 (2:4.10.7+dfsg-0ubuntu2.3) over (2:4.10.7+dfsg-0ubu
ntu2.2) ...
Preparing to unpack .../1-samba-libs_2%3a4.10.7+dfsg-0ubuntu2.3_amd64.deb ...
Unpacking samba-libs:amd64 (2:4.10.7+dfsg-0ubuntu2.3) over (2:4.10.7+dfsg-0ubunt
u2.2) ...
Preparing to unpack .../2-libwbclient0_2%3a4.10.7+dfsg-0ubuntu2.3_amd64.deb ...
Unpacking libwbclient0:amd64 (2:4.10.7+dfsg-0ubuntu2.3) over (2:4.10.7+dfsg-0ubu
ntu2.2) ...
Preparing to unpack .../3-firefox_71.0+build5-0ubuntu0.19.10.1_amd64.deb ...
Unpacking firefox (71.0+build5-0ubuntu0.19.10.1) over (70.0.1+build1-0ubuntu0.19
.10.1) ...
Preparing to unpack .../4-firefox-locale-en_71.0+build5-0ubuntu0.19.10.1_amd64.d
eb ...
Unpacking firefox-locale-en (71.0+build5-0ubuntu0.19.10.1) over (70.0.1+build1-0
ubuntu0.19.10.1) ...
Preparing to unpack .../5-libssh-4_0.9.0-1ubuntu1.3_amd64.deb ...
Unpacking libssh-4:amd64 (0.9.0-1ubuntu1.3) over (0.9.0-1ubuntu1) ...
Preparing to unpack .../6-libssh-gcrypt-4_0.9.0-1ubuntu1.3_amd64.deb ...
Unpacking libssh-gcrypt-4:amd64 (0.9.0-1ubuntu1.3) over (0.9.0-1ubuntu1) ...
Setting up libssh-gcrypt-4:amd64 (0.9.0-1ubuntu1.3) ...
Setting up firefox (71.0+build5-0ubuntu0.19.10.1) ...
Please restart all running instances of firefox, or you will experience problems
.
Setting up libwbclient0:amd64 (2:4.10.7+dfsg-0ubuntu2.3) ...
Setting up grub-pc (2.04-1ubuntu12.1) ...
/var/lib/dpkg/info/grub-pc.config: 10: /etc/default/grub: nvidia-drm.modeset=1: 
not found
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error ex
it status 127
Setting up linux-image-5.3.0-24-generic (5.3.0-24.26) ...
Setting up firefox-locale-en (71.0+build5-0ubuntu0.19.10.1) ...
Setting up libssh-4:amd64 (0.9.0-1ubuntu1.3) ...
dpkg: dependency problems prevent configuration of grub-efi-amd64-signed:
 grub-efi-amd64-signed depends on grub-efi-amd64 | grub-pc; however:
  Package grub-efi-amd64 is not installed.
  Package grub-pc is not configured yet.


dpkg: error processing package grub-efi-amd64-signed (--configure):
 dependency problems - leaving unconfigured
Setting up samba-libs:amd64 (2:4.10.7+dfsg-0ubuntu2.3) ...
No apport report written because the error message indicates its a followup erro
r from a previous failure.
                          Setting up libsmbclient:amd64 (2:4.10.7+dfsg-0ubuntu2.
3) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu1) ...
Processing triggers for mime-support (3.63ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.32.0-1ubuntu1) ...
Processing triggers for libc-bin (2.30-0ubuntu2) ...
Processing triggers for man-db (2.8.7-3) ...
Processing triggers for bamfdaemon (0.5.3+18.04.20180207.2-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for linux-image-5.3.0-24-generic (5.3.0-24.26) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.3.0-24-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.3.0-24-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 10: /etc/default/grub: nvidia-drm.modeset=1: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.3.0-24-generic (--configure):
 installed linux-image-5.3.0-24-generic package post-installation script subproc
ess returned error exit status 1
Errors were encountered while processing:
 grub-pc
 grub-efi-amd64-signed
 linux-image-5.3.0-24-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Bashing-om on 2019-12-10
townhill; Well -

So the plot thickens :)

Post back -be tween code tags- these terminal outputs:
```

cat /proc/cmdline
cat /etc/default/grub
dpkg -l | grep linux-

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]see now where we go 
[/INDENT]

---

### Post by townhill on 2019-12-10
This is what I got 

```

bob@MSI:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-5.3.0-23-generic root=UUID=35a1d288-ae49-4c2f-827e-c01307bff4e8 ro quiet splash vt.handoff=7


bob@MSI:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" nvidia-drm.modeset=1
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1


bob@MSI:~$ dpkg -l | grep linux-
ii  binutils-x86-64-linux-gnu                     2.33-2ubuntu1                              amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  liblinux-epoll-perl                           0.016-1                                    amd64        perl epoll module for O(1) multiplexing
ii  linux-base                                    4.5ubuntu2                                 all          Linux image base package
ii  linux-firmware                                1.183.2                                    all          Firmware for Linux kernel drivers
ii  linux-generic                                 5.3.0.24.28                                amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.3.0-23                        5.3.0-23.25                                all          Header files related to Linux kernel version 5.3.0
ii  linux-headers-5.3.0-23-generic                5.3.0-23.25                                amd64        Linux kernel headers for version 5.3.0 on 64 bit x86 SMP
ii  linux-headers-5.3.0-24                        5.3.0-24.26                                all          Header files related to Linux kernel version 5.3.0
ii  linux-headers-5.3.0-24-generic                5.3.0-24.26                                amd64        Linux kernel headers for version 5.3.0 on 64 bit x86 SMP
ii  linux-headers-generic                         5.3.0.24.28                                amd64        Generic Linux kernel headers
rH  linux-image-5.3.0-18-generic                  5.3.0-18.19+1                              amd64        Signed kernel image generic
ii  linux-image-5.3.0-23-generic                  5.3.0-23.25                                amd64        Signed kernel image generic
iF  linux-image-5.3.0-24-generic                  5.3.0-24.26                                amd64        Signed kernel image generic
ii  linux-image-generic                           5.3.0.24.28                                amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                          5.3.0-24.26                                amd64        Linux Kernel Headers for development
ii  linux-modules-5.3.0-18-generic                5.3.0-18.19                                amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
ii  linux-modules-5.3.0-23-generic                5.3.0-23.25                                amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
ii  linux-modules-5.3.0-24-generic                5.3.0-24.26                                amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-18-generic          5.3.0-18.19                                amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.3.0-23-generic          5.3.0-23.25                                amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.3.0-24-generic          5.3.0-24.26                                amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
ii  linux-signed-generic                          5.3.0.24.28                                amd64        Complete Signed Generic Linux kernel and headers (dummy transitional package)
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5                       all          base package for ALSA and OSS sound systems
ii  syslinux-common                               3:6.04~git20190206.bf6db5b4+dfsg1-1        all          collection of bootloaders (common)
ii  syslinux-legacy                               2:3.63+dfsg-2ubuntu9                       amd64        Bootloader for Linux/i386 using MS-DOS floppies


```

---

### Post by Bashing-om on 2019-12-10
townhill; Uh Huh

Light :)

OK nvidia-drm.modeset=1 "
Why do you use this boot option ? 
*IF* you must have it .place this parameter also within the quotes beside quiet splash in the /etc/default/grub file.

And the -18 version kernel is only partially installed.
what kernel are you presently booting ?
```

uname -r

```
 IF the current boot is on the 5.3.0-24-generic kernel,
let's see what we can do to remove the old -18 version.
```

sudo dpkg -P linux-image-5.3.0-18-generic linux-modules{,-extra}-5.3.0-18-generic linux-headers-5.3.0-18{,-generic}

```

I can accept that there may be some balking here, If so we can get more hands on with these partials; If the package manager will not then handle it for us.

[INDENT]all in the process
[/INDENT]

---

### Post by townhill on 2019-12-10
Well, I'm not sure about the Nvidia, I was having a terrible time getting my Nvidia graphics card to be recognized so was fooling around with driver updates, but now that'a all working fine now.  I didn't know that I had changed a boot option and maybe don't need that.  the u-name -r command tells me 5.3.0-23-generic.

Meanwhile:

```

bob@MSI:~$ sudo dpkg -P linux-image-5.3.0-18-generic linux-modules{,-extra}-5.3.0-18-generic linux-headers-5.3.0-18{,-generic}
[sudo] password for bob: 
(Reading database ... 228514 files and directories currently installed.)
Removing linux-image-5.3.0-18-generic (5.3.0-18.19+1) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.3.0-18-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 10: /etc/default/grub: nvidia-drm.modeset=1: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.3.0-18-generic (--purge):
 installed linux-image-5.3.0-18-generic package post-removal script subprocess returned error exit status 1
Removing linux-modules-5.3.0-18-generic (5.3.0-18.19) ...
Purging configuration files for linux-modules-5.3.0-18-generic (5.3.0-18.19) ...
dpkg: warning: while removing linux-modules-5.3.0-18-generic, directory '/lib/modules/5.3.0-18-generic' not empty so not removed
Purging configuration files for linux-modules-extra-5.3.0-18-generic (5.3.0-18.19) ...
dpkg: warning: ignoring request to remove linux-headers-5.3.0-18 which isn't installed
dpkg: warning: ignoring request to remove linux-headers-5.3.0-18-generic which isn't installed
Errors were encountered while processing:
 linux-image-5.3.0-18-generic


```

---

### Post by townhill on 2019-12-10
Re the Nvidia boot option question, I'm too new to Linux to feel comfortable editing grub file, but I took a look using the *Grub Customizer* and got this error that seems related.  Not sure if this sheds any light
```

grub-mk.config couldn't be executed successfully error message:
Sourcing file '/etc/default/grub' 
/usr/sbin/grub-mkconfig;10:/etc/default/grub;nvida-drm.modset=1:not found

```

---

### Post by Bashing-om on 2019-12-10
townhill; Well -

the dpkg command result looks pretty decent. What have we now ?
```

dpkg -l | grep linux-

```

maybe now we change focus to know why the -24 kernel is not booting.

[INDENT]maybe Yes
[INDENT][INDENT]could be not so yes[/INDENT][/INDENT][/INDENT]

---

### Post by townhill on 2019-12-10
looks like this 

```

ob@MSI:~$ dpkg -l | grep linux-
ii  binutils-x86-64-linux-gnu                     2.33-2ubuntu1                              amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  liblinux-epoll-perl                           0.016-1                                    amd64        perl epoll module for O(1) multiplexing
ii  linux-base                                    4.5ubuntu2                                 all          Linux image base package
ii  linux-firmware                                1.183.2                                    all          Firmware for Linux kernel drivers
ii  linux-generic                                 5.3.0.24.28                                amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.3.0-23                        5.3.0-23.25                                all          Header files related to Linux kernel version 5.3.0
ii  linux-headers-5.3.0-23-generic                5.3.0-23.25                                amd64        Linux kernel headers for version 5.3.0 on 64 bit x86 SMP
ii  linux-headers-5.3.0-24                        5.3.0-24.26                                all          Header files related to Linux kernel version 5.3.0
ii  linux-headers-5.3.0-24-generic                5.3.0-24.26                                amd64        Linux kernel headers for version 5.3.0 on 64 bit x86 SMP
ii  linux-headers-generic                         5.3.0.24.28                                amd64        Generic Linux kernel headers
pH  linux-image-5.3.0-18-generic                  5.3.0-18.19+1                              amd64        Signed kernel image generic
ii  linux-image-5.3.0-23-generic                  5.3.0-23.25                                amd64        Signed kernel image generic
iF  linux-image-5.3.0-24-generic                  5.3.0-24.26                                amd64        Signed kernel image generic
ii  linux-image-generic                           5.3.0.24.28                                amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                          5.3.0-24.26                                amd64        Linux Kernel Headers for development
ii  linux-modules-5.3.0-23-generic                5.3.0-23.25                                amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
ii  linux-modules-5.3.0-24-generic                5.3.0-24.26                                amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.3.0-23-generic          5.3.0-23.25                                amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.3.0-24-generic          5.3.0-24.26                                amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
ii  linux-signed-generic                          5.3.0.24.28                                amd64        Complete Signed Generic Linux kernel and headers (dummy transitional package)
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5                       all          base package for ALSA and OSS sound systems
ii  syslinux-common                               3:6.04~git20190206.bf6db5b4+dfsg1-1        all          collection of bootloaders (common)
ii  syslinux-legacy                               2:3.63+dfsg-2ubuntu9                       amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Bashing-om on 2019-12-10
townhill - hummmm ---

ummphhh :(

what now again:
```

sudo dpkg -P linux-image-5.3.0-18-generic

```

And we need to know why the -24 kernel failed to install (pH).
What shows:
```

df -h
df -i

```

just to make sure it is not a disk space issue ( doubtful )
then we can try and reinstall the -24 version.

[INDENT][INDENT]where there is a will - there is a way [/INDENT][/INDENT]

---

### Post by Impavidus on 2019-12-11
The problem is this line in your /etc/default/grub:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" nvidia-drm.modeset=1
```
As the final part is not enclosed in the quotes, the shell thinks it's a command and tries to execute it. It fails, because that command doesn't exist. When you (or whatever script you decided to use) changed that line, update-grub could no longer work and this blocked all kernel upgrades. And when the package manager tries and fails to execute a kernel upgrade, it comes into an inconsistent state and stops working completely. This is why 5.3.0-18 can't be removed and 5.3.0-24 can't be installed.

Use```
sudoedit /etc/default/grub
```to change that line into```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia-drm.modeset=1"
```if you really need the nvidia-drm.modeset=1 option (watch the position of the quote character), or change it into```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```if you don't really need it. Then use```
sudo apt upgrade
```to complete installation/removal of packages.

Don't expect help from grub-customizer. It just makes it easier to break your system. And it only told you what you already knew: that that line in /etc/default/grub is broken. Don't get into the habit of installing applications to change the settings of other applications. Just use a text editor whenever you can.

---

### Post by townhill on 2019-12-12
I'm kinda at a loss here.  I'm thinking it does go back to the nvidia modeset.  I tried changing [COLOR=#000000]nvidia-drm.modeset=1 to [/COLOR][COLOR=#000000]nvidia-drm.modeset=0 and then Blender would not start so i reset it to *1*.  but in both cases after setting it to 1 or 0, when i ran sudo update-grub I got the errot 
```
 [/COLOR]$ sudo update-grub[sudo] password for bob: 
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 10: /etc/default/grub: nvidia-drm.modeset=1: not found

```

so I'm thinking that there is something in the /usr/sbin/grub-mkconfig file that is not right

---

### Post by townhill on 2019-12-12
just saw your post [COLOR=#000000]Imoavidus, checking it out now[/COLOR]

---

### Post by townhill on 2019-12-12
Thank you Impavidus, that did the trick.  Really appreciate your help and your advise re text editor is well taken.

---

