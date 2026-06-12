---
title: "Ubuntu 12.10 linux-image error processing"
date: 2013-02-12
forum: General Help
---

### Post by xTimeKillerx on 2013-02-12
I'm extremely new to Linux and Ubuntu, so please bear with me as I try to help you help me. I've spent about 4 hours searching through Google and fix after fix, but to no avail so I figured I'd try to get your help directly.

```
bryce@bryce-HP-G50-Notebook-PC:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal

```

All of a sudden I can't install anything because of these errors.

For example: Just trying to pull up uname -a says I need to install coreutils, this is the result

```
bryce@bryce-HP-G50-Notebook-PC:~$ uname -a
The program 'uname' is currently not installed. You can install it by typing:
sudo apt-get install coreutils
bryce@bryce-HP-G50-Notebook-PC:~$ sudo apt-get install coreutils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
coreutils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-3.5.0-23-generic (3.5.0-23.35) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
Generating grub.cfg ...
/etc/grub.d/10_linux: 1: /etc/grub.d/10_linux: uname: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.5.0-23-generic.postinst line 1010.
dpkg: error processing linux-image-3.5.0-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-extra-3.5.0-23-generic:
 linux-image-extra-3.5.0-23-generic depends on linux-image-3.5.0-23-generic; however:
  Package linux-image-3.5.0-23-generic is not configured yet.

dpkg: error processing linux-image-extra-3.5.0-23-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.5.0-23-generic; however:
  Package linux-image-3.5.0-23-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.5.0-23-generic; however:
  Package linux-image-extra-3.5.0-23-generic is not configured yet.

dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.

dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.5.0-23-generic
 linux-image-extra-3.5.0-23-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've ran 
> sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install dkms
sudo apt-get install -f 

Autoclean:
```
bryce@bryce-HP-G50-Notebook-PC:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

Autoremove:
```
bryce@bryce-HP-G50-Notebook-PC:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.5.0-23-generic (3.5.0-23.35) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
Generating grub.cfg ...
/etc/grub.d/10_linux: 1: /etc/grub.d/10_linux: uname: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.5.0-23-generic.postinst line 1010.
dpkg: error processing linux-image-3.5.0-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.5.0-23-generic:
 linux-image-extra-3.5.0-23-generic depends on linux-image-3.5.0-23-generic; however:
  Package linux-image-3.5.0-23-generic is not configured yet.

dpkg: error processing linux-image-extra-3.5.0-23-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.5.0-23-generic; however:
  Package linux-image-3.5.0-23-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.5.0-23-generic; however:
  Package linux-image-extra-3.5.0-23-generic is not configured yet.

dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.

dpkg: error processing lNo apport report written because MaxReports is reached already
      No apport report written because MaxReports is reached already
                                                                    No apport report written because MaxReports is reached already
                                                  inux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.5.0-23-generic
 linux-image-extra-3.5.0-23-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Apt-get update:
```
bryce@bryce-HP-G50-Notebook-PC:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://security.ubuntu.com quantal-security InRelease                      
Ign http://us.archive.ubuntu.com quantal InRelease                             
Get:1 http://security.ubuntu.com quantal-security Release.gpg [933 B]          
Ign http://extras.ubuntu.com quantal InRelease                                 
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://us.archive.ubuntu.com quantal-updates InRelease                     
Get:2 http://security.ubuntu.com quantal-security Release [49.6 kB]            
Ign http://dl.google.com stable/main Translation-en                            
Ign http://archive.canonical.com quantal InRelease                             
Ign http://us.archive.ubuntu.com quantal-backports InRelease                   
Hit http://extras.ubuntu.com quantal Release.gpg                               
Hit http://us.archive.ubuntu.com quantal Release.gpg                           
Hit http://archive.canonical.com quantal Release.gpg                           
Get:3 http://us.archive.ubuntu.com quantal-updates Release.gpg [933 B]         
Hit http://extras.ubuntu.com quantal Release                                   
Get:4 http://security.ubuntu.com quantal-security/main Sources [29.5 kB]       
Get:5 http://us.archive.ubuntu.com quantal-backports Release.gpg [933 B]       
Hit http://archive.canonical.com quantal Release                               
Hit http://extras.ubuntu.com quantal/main Sources                              
Hit http://us.archive.ubuntu.com quantal Release                               
Get:6 http://security.ubuntu.com quantal-security/restricted Sources [14 B]    
Hit http://archive.canonical.com quantal/partner Sources                       
Get:7 http://us.archive.ubuntu.com quantal-updates Release [49.6 kB]           
Get:8 http://security.ubuntu.com quantal-security/universe Sources [14.1 kB]   
Hit http://extras.ubuntu.com quantal/main i386 Packages                        
Hit http://archive.canonical.com quantal/partner i386 Packages                 
Get:9 http://security.ubuntu.com quantal-security/multiverse Sources [688 B]   
Get:10 http://security.ubuntu.com quantal-security/main i386 Packages [75.8 kB]
Get:11 http://us.archive.ubuntu.com quantal-backports Release [49.6 kB]        
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://us.archive.ubuntu.com quantal/main Sources                          
Get:12 http://security.ubuntu.com quantal-security/restricted i386 Packages [14 B]
Hit http://us.archive.ubuntu.com quantal/restricted Sources                    
Hit http://ppa.launchpad.net quantal Release.gpg                               
Get:13 http://security.ubuntu.com quantal-security/universe i386 Packages [34.7 kB]
Hit http://us.archive.ubuntu.com quantal/universe Sources                      
Hit http://us.archive.ubuntu.com quantal/multiverse Sources                    
Get:14 http://security.ubuntu.com quantal-security/multiverse i386 Packages [1,385 B]
Hit http://us.archive.ubuntu.com quantal/main i386 Packages                    
Hit http://us.archive.ubuntu.com quantal/restricted i386 Packages              
Hit http://security.ubuntu.com quantal-security/main Translation-en            
Hit http://us.archive.ubuntu.com quantal/universe i386 Packages                
Hit http://us.archive.ubuntu.com quantal/multiverse i386 Packages              
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en      
Hit http://us.archive.ubuntu.com quantal/main Translation-en                   
Hit http://security.ubuntu.com quantal-security/restricted Translation-en      
Ign http://extras.ubuntu.com quantal/main Translation-en_US                    
Ign http://archive.canonical.com quantal/partner Translation-en_US             
Hit http://us.archive.ubuntu.com quantal/multiverse Translation-en             
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://security.ubuntu.com quantal-security/universe Translation-en        
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Ign http://archive.canonical.com quantal/partner Translation-en                
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://us.archive.ubuntu.com quantal/restricted Translation-en    
Hit http://ppa.launchpad.net quantal/main i386 Packages               
Hit http://us.archive.ubuntu.com quantal/universe Translation-en      
Get:15 http://us.archive.ubuntu.com quantal-updates/main Sources [75.3 kB]
Get:16 http://us.archive.ubuntu.com quantal-updates/restricted Sources [1,302 B]
Get:17 http://us.archive.ubuntu.com quantal-updates/universe Sources [77.6 kB] 
Get:18 http://us.archive.ubuntu.com quantal-updates/multiverse Sources [2,942 B]
Get:19 http://us.archive.ubuntu.com quantal-updates/main i386 Packages [186 kB]
Ign http://security.ubuntu.com quantal-security/main Translation-en_US     
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US   
Get:20 http://us.archive.ubuntu.com quantal-updates/restricted i386 Packages [3,067 B]
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US   
Get:21 http://us.archive.ubuntu.com quantal-updates/universe i386 Packages [163 kB]
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US     
Ign http://ppa.launchpad.net quantal/main Translation-en_US                    
Get:22 http://us.archive.ubuntu.com quantal-updates/multiverse i386 Packages [8,094 B]
Ign http://ppa.launchpad.net quantal/main Translation-en                      
Hit http://us.archive.ubuntu.com quantal-updates/main Translation-en
Hit http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com quantal-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com quantal-updates/universe Translation-en
Get:23 http://us.archive.ubuntu.com quantal-backports/main Sources [14 B]
Get:24 http://us.archive.ubuntu.com quantal-backports/restricted Sources [14 B]
Get:25 http://us.archive.ubuntu.com quantal-backports/universe Sources [6,399 B]
Get:26 http://us.archive.ubuntu.com quantal-backports/multiverse Sources [781 B]
Get:27 http://us.archive.ubuntu.com quantal-backports/main i386 Packages [14 B]
Get:28 http://us.archive.ubuntu.com quantal-backports/restricted i386 Packages [14 B]
Get:29 http://us.archive.ubuntu.com quantal-backports/universe i386 Packages [7,916 B]
Get:30 http://us.archive.ubuntu.com quantal-backports/multiverse i386 Packages [1,118 B]
Hit http://us.archive.ubuntu.com quantal-backports/main Translation-en
Hit http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com quantal-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com quantal-backports/universe Translation-en     
Ign http://us.archive.ubuntu.com quantal/main Translation-en_US                
Ign http://us.archive.ubuntu.com quantal/multiverse Translation-en_US          
Ign http://us.archive.ubuntu.com quantal/restricted Translation-en_US          
Ign http://us.archive.ubuntu.com quantal/universe Translation-en_US            
Ign http://us.archive.ubuntu.com quantal-updates/main Translation-en_US        
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com quantal-updates/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com quantal-updates/universe Translation-en_US    
Ign http://us.archive.ubuntu.com quantal-backports/main Translation-en_US      
Ign http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/universe Translation-en_US  
Fetched 842 kB in 11s (74.3 kB/s)                                              
Reading package lists... Done

```

Obviously apt-get install dkms won't work, same errors

Apt-get install -f:
```
bryce@bryce-HP-G50-Notebook-PC:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.5.0-23-generic (3.5.0-23.35) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
/etc/kernel/postinst.d/dkms: line 6: uname: command not found
/usr/sbin/dkms: line 3380: uname: command not found
/usr/sbin/dkms: line 3381: uname: command not found
/usr/sbin/dkms: line 202: uname: command not found
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
Generating grub.cfg ...
/etc/grub.d/10_linux: 1: /etc/grub.d/10_linux: uname: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.5.0-23-generic.postinst line 1010.
dpkg: error processing linux-image-3.5.0-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.5.0-23-generic:
 linux-image-extra-3.5.0-23-generic depends on linux-image-3.5.0-23-generic; however:
  Package linux-image-3.5.0-23-generic is not configured yet.

dpkg: error processing linux-image-extra-3.5.0-23-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.5.0-23-generic; however:
  Package linux-image-3.5.0-23-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.5.0-23-generic; however:
  Package linux-image-extra-3.5.0-23-generic is not configured yet.

dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.

dpkg: error processing lNo apport report written because the error message indicates its a followup error from a previous failure.
                                                  No apport report written because the error message indicates its a followup error from a previous failure.
                                                                            No apport report written because MaxReports is reached already
                                                          inux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.5.0-23-generic
 linux-image-extra-3.5.0-23-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Installed kernels:
```
bryce@bryce-HP-G50-Notebook-PC:~$ dpkg-query -l linux*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-doc-3.5. <none>                    (no description available)
ii  linux-firmware 1.95         all          Firmware for Linux kernel drivers
iU  linux-generic  3.5.0.23.29  i386         Complete Generic Linux kernel and
un  linux-headers  <none>                    (no description available)
un  linux-headers- <none>                    (no description available)
un  linux-headers- <none>                    (no description available)
ii  linux-headers- 3.5.0-18.29  all          Header files related to Linux ker
ii  linux-headers- 3.5.0-18.29  i386         Linux kernel headers for version 
ii  linux-headers- 3.5.0-19.30  all          Header files related to Linux ker
ii  linux-headers- 3.5.0-19.30  i386         Linux kernel headers for version 
ii  linux-headers- 3.5.0-21.32  all          Header files related to Linux ker
ii  linux-headers- 3.5.0-21.32  i386         Linux kernel headers for version 
ii  linux-headers- 3.5.0-22.34  all          Header files related to Linux ker
ii  linux-headers- 3.5.0-22.34  i386         Linux kernel headers for version 
ii  linux-headers- 3.5.0-23.35  all          Header files related to Linux ker
ii  linux-headers- 3.5.0-23.35  i386         Linux kernel headers for version 
ii  linux-headers- 3.5.0.23.29  i386         Generic Linux kernel headers
ii  linux-headers- 3.5.0.23.29  i386         Transitional package
un  linux-image    <none>                    (no description available)
un  linux-image-3. <none>                    (no description available)
ii  linux-image-3. 3.5.0-22.34  i386         Linux kernel image for version 3.
iF  linux-image-3. 3.5.0-23.35  i386         Linux kernel image for version 3.
ii  linux-image-ex 3.5.0-22.34  i386         Linux kernel image for version 3.
iU  linux-image-ex 3.5.0-23.35  i386         Linux kernel image for version 3.
iU  linux-image-ge 3.5.0.23.29  i386         Generic Linux kernel image
un  linux-initramf <none>                    (no description available)
un  linux-kernel-h <none>                    (no description available)
un  linux-kernel-l <none>                    (no description available)
ii  linux-libc-dev 3.5.0-23.35  i386         Linux Kernel Headers for developm
un  linux-restrict <none>                    (no description available)
ii  linux-sound-ba 1.0.25+dfsg- all          base package for ALSA and OSS sou
un  linux-source-3 <none>                    (no description available)
un  linux-tools    <none>                    (no description available)
un  linux32        <none>                    (no description available)

```

I'm really sorry about the serious wall of text, but I'm getting frustrated after trying so many things and not getting it to work. 

I was having issues with old images like these, so I removed them from status (/var/lib/dpkg) and have them in a seperate text file
```
Package: linux-image-extra-3.5.0-21-generic
Status: deinstall ok half-installed
Priority: optional
Section: kernel
Installed-Size: 88279
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux
Version: 3.5.0-21.32
Config-Version: 3.5.0-21.32
Depends: linux-image-3.5.0-21-generic, crda (>= 1.1.1-1ubuntu2) | wireless-crda
Description: Linux kernel image for version 3.5.0 on 32 bit x86 SMP
 This package contains the Linux kernel image for version 3.5.0 on
 32 bit x86 SMP.
 .
 Also includes the corresponding System.map file, the modules built by the
 packager, and scripts that try to ensure that the system is not left in an
 unbootable state after an update.
 .
 Supports Generic processors.
 .
 Geared toward desktop and server systems.
 .
 You likely do not want to install this package directly. Instead, install
 the linux-generic meta-package, which will ensure that upgrades work
 correctly, and that supporting packages are also installed.

Package: linux-image-3.5.0-19-generic
Status: deinstall ok half-installed
Priority: optional
Section: kernel
Installed-Size: 24421
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux
Version: 3.5.0-19.30
Config-Version: 3.5.0-19.30
Provides: fuse-module, ivtv-modules, kvm-api-4, linux-image, linux-image-3.0, redhat-cluster-modules
Depends: initramfs-tools (>= 0.36ubuntu6), module-init-tools (>= 3.3-pre11-4ubuntu3)
Pre-Depends: dpkg (>= 1.10.24)
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo (>= 19.1)
Suggests: fdutils, linux-doc-3.5.0 | linux-source-3.5.0, linux-tools
Conflicts: hotplug (<< 0.0.20040105-1)
Description: Linux kernel image for version 3.5.0 on 32 bit x86 SMP
 This package contains the Linux kernel image for version 3.5.0 on
 32 bit x86 SMP.
 .
 Also includes the corresponding System.map file, the modules built by the
 packager, and scripts that try to ensure that the system is not left in an
 unbootable state after an update.
 .
 Supports Generic processors.
 .
 Geared toward desktop and server systems.
 .
 You likely do not want to install this package directly. Instead, install
 the linux-generic meta-package, which will ensure that upgrades work
 correctly, and that supporting packages are also installed.


Package: linux-image-extra-3.5.0-18-generic
Status: deinstall ok half-installed
Priority: optional
Section: kernel
Installed-Size: 87571
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux
Version: 3.5.0-18.29
Config-Version: 3.5.0-18.29
Depends: linux-image-3.5.0-18-generic, crda (>= 1.1.1-1ubuntu2) | wireless-crda
Description: Linux kernel image for version 3.5.0 on 32 bit x86 SMP
 This package contains the Linux kernel image for version 3.5.0 on
 32 bit x86 SMP.
 .
 Also includes the corresponding System.map file, the modules built by the
 packager, and scripts that try to ensure that the system is not left in an
 unbootable state after an update.
 .
 Supports Generic processors.
 .
 Geared toward desktop and server systems.
 .
 You likely do not want to install this package directly. Instead, install
 the linux-generic meta-package, which will ensure that upgrades work
 correctly, and that supporting packages are also installed.


Package: linux-image-extra-3.5.0-19-generic
Status: deinstall ok half-installed
Priority: optional
Section: kernel
Installed-Size: 87572
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux
Version: 3.5.0-19.30
Config-Version: 3.5.0-19.30
Depends: linux-image-3.5.0-19-generic, crda (>= 1.1.1-1ubuntu2) | wireless-crda
Description: Linux kernel image for version 3.5.0 on 32 bit x86 SMP
 This package contains the Linux kernel image for version 3.5.0 on
 32 bit x86 SMP.
 .
 Also includes the corresponding System.map file, the modules built by the
 packager, and scripts that try to ensure that the system is not left in an
 unbootable state after an update.
 .
 Supports Generic processors.
 .
 Geared toward desktop and server systems.
 .
 You likely do not want to install this package directly. Instead, install
 the linux-generic meta-package, which will ensure that upgrades work
 correctly, and that supporting packages are also installed.

Package: linux-image-3.5.0-21-generic
Status: deinstall ok half-installed
Priority: optional
Section: kernel
Installed-Size: 24440
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux
Version: 3.5.0-21.32
Config-Version: 3.5.0-21.32
Provides: fuse-module, ivtv-modules, kvm-api-4, linux-image, linux-image-3.0, redhat-cluster-modules
Depends: initramfs-tools (>= 0.36ubuntu6), module-init-tools (>= 3.3-pre11-4ubuntu3)
Pre-Depends: dpkg (>= 1.10.24)
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo (>= 19.1)
Suggests: fdutils, linux-doc-3.5.0 | linux-source-3.5.0, linux-tools
Conflicts: hotplug (<< 0.0.20040105-1)
Description: Linux kernel image for version 3.5.0 on 32 bit x86 SMP
 This package contains the Linux kernel image for version 3.5.0 on
 32 bit x86 SMP.
 .
 Also includes the corresponding System.map file, the modules built by the
 packager, and scripts that try to ensure that the system is not left in an
 unbootable state after an update.
 .
 Supports Generic processors.
 .
 Geared toward desktop and server systems.
 .
 You likely do not want to install this package directly. Instead, install
 the linux-generic meta-package, which will ensure that upgrades work
 correctly, and that supporting packages are also installed.


Package: linux-image-extra-3.5.0-17-generic
Status: deinstall ok half-installed
Priority: optional
Section: kernel
Installed-Size: 87666
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux
Version: 3.5.0-17.28
Config-Version: 3.5.0-17.28
Depends: linux-image-3.5.0-17-generic, crda (>= 1.1.1-1ubuntu2) | wireless-crda
Description: Linux kernel image for version 3.5.0 on 32 bit x86 SMP
 This package contains the Linux kernel image for version 3.5.0 on
 32 bit x86 SMP.
 .
 Also includes the corresponding System.map file, the modules built by the
 packager, and scripts that try to ensure that the system is not left in an
 unbootable state after an update.
 .
 Supports Generic processors.
 .
 Geared toward desktop and server systems.
 .
 You likely do not want to install this package directly. Instead, install
 the linux-generic meta-package, which will ensure that upgrades work
 correctly, and that supporting packages are also installed.

Package: linux-image-3.5.0-18-generic
Status: deinstall ok half-installed
Priority: optional
Section: kernel
Installed-Size: 24421
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux
Version: 3.5.0-18.29
Config-Version: 3.5.0-18.29
Provides: fuse-module, ivtv-modules, kvm-api-4, linux-image, linux-image-3.0, ndiswrapper-modules-1.9, redhat-cluster-modules
Depends: initramfs-tools (>= 0.36ubuntu6), module-init-tools (>= 3.3-pre11-4ubuntu3)
Pre-Depends: dpkg (>= 1.10.24)
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo (>= 19.1)
Suggests: fdutils, linux-doc-3.5.0 | linux-source-3.5.0, linux-tools
Conflicts: hotplug (<< 0.0.20040105-1)
Description: Linux kernel image for version 3.5.0 on 32 bit x86 SMP
 This package contains the Linux kernel image for version 3.5.0 on
 32 bit x86 SMP.
 .
 Also includes the corresponding System.map file, the modules built by the
 packager, and scripts that try to ensure that the system is not left in an
 unbootable state after an update.
 .
 Supports Generic processors.
 .
 Geared toward desktop and server systems.
 .
 You likely do not want to install this package directly. Instead, install
 the linux-generic meta-package, which will ensure that upgrades work
 correctly, and that supporting packages are also installed.

Package: linux-image-3.5.0-17-generic
Status: deinstall ok half-installed
Priority: optional
Section: kernel
Installed-Size: 24298
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux
Version: 3.5.0-17.28
Config-Version: 3.5.0-17.28
Provides: fuse-module, ivtv-modules, kvm-api-4, linux-image, linux-image-3.0, ndiswrapper-modules-1.9, redhat-cluster-modules
Depends: initramfs-tools (>= 0.36ubuntu6), module-init-tools (>= 3.3-pre11-4ubuntu3)
Pre-Depends: dpkg (>= 1.10.24)
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo (>= 19.1)
Suggests: fdutils, linux-doc-3.5.0 | linux-source-3.5.0, linux-tools
Conflicts: hotplug (<< 0.0.20040105-1)
Description: Linux kernel image for version 3.5.0 on 32 bit x86 SMP
 This package contains the Linux kernel image for version 3.5.0 on
 32 bit x86 SMP.
 .
 Also includes the corresponding System.map file, the modules built by the
 packager, and scripts that try to ensure that the system is not left in an
 unbootable state after an update.
 .
 Supports Generic processors.
 .
 Geared toward desktop and server systems.
 .
 You likely do not want to install this package directly. Instead, install
 the linux-generic meta-package, which will ensure that upgrades work
 correctly, and that supporting packages are also installed.


```

Any help is appreciated... I just want to be able to use my computer..


Edit:
Added lshw
```
bryce@bryce-HP-G50-Notebook-PC:~$ sudo lshw
bryce-hp-g50-notebook-pc  
    description: Notebook
    product: HP G50 Notebook PC (FR956UA#ABA)
    vendor: Hewlett-Packard
    version: F.25
    serial: 2CE8403YPK
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook family=103C_5335KV sku=FR956UA#ABA uuid=56DA4A60-9898-11DD-9395-AE7628920C8D
  *-core
       description: Motherboard
       product: 360B
       vendor: Wistron
       physical id: 0
       version: 09.44
       serial: 2CE8403YPK
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.25
          date: 09/04/2008
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: DOVE1B163BE
             vendor: 7F7F7F7FCB000000
             physical id: 0
             serial: 00000000
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: RMN1150EC48D7F-667
             vendor: Ramaxel Technology
             physical id: 1
             serial: 00000000
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1c
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: CPU
          size: 1GHz
          capacity: 2GHz
          width: 64 bits
          clock: 667MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm cpufreq
          configuration: id=1
        *-cache:0
             description: L2 cache
             physical id: 1d
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 1f
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back data
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-cache
          description: L1 cache
          physical id: 1e
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back instruction
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5110(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:d2500000-d25fffff
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:50e0(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:50c0(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:50a0(size=32)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:d4705c00-d4705fff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:d4700000-d4703fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=8192) memory:d3700000-d46fffff ioport:d0400000(size=17825792)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 02
                serial: 00:1f:16:40:c9:9b
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:43 ioport:3000(size=256) memory:d0410000-d0410fff memory:d0400000-d040ffff memory:d0420000-d043ffff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:d2600000-d36fffff ioport:d1500000(size=16777216)
           *-network
                description: Wireless interface
                product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 00:23:4d:2e:6e:12
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=3.5.0-22-generic firmware=N/A ip=192.168.1.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:d2600000-d260ffff
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:5080(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:5060(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:5040(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:d4705800-d4705bff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:42 ioport:5108(size=8) ioport:511c(size=4) ioport:5100(size=8) ioport:5118(size=4) ioport:5020(size=32) memory:d4705000-d47057ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d4706000-d47060ff ioport:5000(size=32)
        *-generic UNCLAIMED
             description: Signal processing controller
             product: 82801I (ICH9 Family) Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:d4704000-d4704fff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST9160827AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.AH
             serial: 5RF24322
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0009193b
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: d8301fdd-5695-46b2-8d30-02a4012cc983
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable ext2 initialized
                configuration: filesystem=ext2 modified=2013-02-12 01:00:32 mount.fstype=ext2 mount.options=rw,relatime,errors=continue state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 148GiB
                capacity: 148GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 148GiB
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD RW AD-7560S
             vendor: Optiarc
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: SH03
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@2:1
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Desktop
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             version: 0130
             serial: 2GHMZEPZ
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 sectorsize=512 signature=7669a53c
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/bryce/Expansion Drive
                version: 3.1
                serial: 5efd189c-352b-2c46-b895-7e9eca7106b1
                size: 931GiB
                capacity: 931GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2011-01-13 22:30:18 filesystem=ntfs label=Expansion Drive mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
     *-scsi:3
          physical id: 4
          bus info: usb@1:3
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdc
             configuration: sectorsize=512
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define4
       vendor: OEM_Define2
       physical id: 1
       version: OEM_Define5
       serial: OEM_Define2
       capacity: 75mWh

```

---

### Post by dabl on 2013-02-12
For starters, I'd like to see the ouput of these commands:

```
df -h
```

```
sudo dpkg --configure -a
```

---

### Post by xTimeKillerx on 2013-02-12
I'm at work now so I will get to running that and post the results when I get home tonight, thank you for the start

---

### Post by schragge on 2013-02-12
These are strange:
```

/etc/grub.d/10_linux: 1: /etc/grub.d/10_linux: uname: not found

``````

/etc/kernel/postinst.d/dkms: line 6: uname: command not found

```What does 'which uname' show?

[COLOR=blue]**Update.**[/COLOR]
Sorry, didn't read your first post well. You've already tried to install *coreutils*. OK, what's in your PATH? What does 'echo $PATH' show? What are the file permissions of */usr/bin/uname*? 'ls -l /usr/bin/uname' should show '-rwxr-xr-x' among other data.

The thread should probably be renamed *uname: command not found*. That's the root cause. Failing kernel upgrade is only an external symptom. The problem has nothing to do with the package management system in general, nor with *linux-image* in particular.

Look, *coreutils* is a **required** package. Configuration scripts for *grub* and for the newly installed kernel assume it's already installed and *uname* is available, are trying to invoke it and fail. If 'ls -l /usr/bin/uname' doesn't show you anything, try to reinstall *coreutils*.
```

sudo apt-get -f --reinstall install coreutils

```I guess *dpkg --configure* as suggested above won't work without working *uname*.

---

