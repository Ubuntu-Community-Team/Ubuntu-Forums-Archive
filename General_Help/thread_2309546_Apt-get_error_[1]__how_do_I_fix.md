---
title: "Apt-get error [1]  how do I fix"
date: 2016-01-11
forum: General Help
---

### Post by MechaMechanism on 2016-01-11
```
nate@frontier:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.2.0-19 linux-headers-4.2.0-19-generic
  linux-image-4.2.0-19-generic linux-image-extra-4.2.0-19-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up virtualbox-ext-pack (5.0.4-2) ...
dpkg: error processing package virtualbox-ext-pack (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 virtualbox-ext-pack
[ Rootkit Hunter version 1.4.2 ]
File updated: searched for 176 files, found 148
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

No matter what I do the problem won't go away.  I can't remove, purge nothing.

System76
Wild Dog Pro
Ubuntu 15.10 with all updates.
nate@frontier:~$ uname -a
Linux frontier 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by ian-weisser on 2016-01-11
Try
```
sudo apt-get clean virtualbox-ext-pack
sudo apt-get install --reinstall virtualbox-ext-pack
```

If it does not work, please show the complete output of both commands.

---

### Post by MechaMechanism on 2016-01-11
```
nate@frontier:~$ sudo apt-get clean virtualbox-ext-pack
nate@frontier:~$ sudo apt-get install --reinstall virtualbox-ext-pack
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.2.0-19 linux-headers-4.2.0-19-generic
  linux-image-4.2.0-19-generic linux-image-extra-4.2.0-19-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for virtualbox-ext-pack:amd64
```No go.

---

### Post by ian-weisser on 2016-01-12
> **MechaMechanism said:**
> E: Internal Error, No file name for virtualbox-ext-pack:amd64

Hmmmm.
That's very interesting (sorry), because v-e-p doesn't have 32-bit and 64-bit versions. There's just one 'all' version. The error message is right.
I wonder where the call for a 64-bit version is coming from?

---

### Post by MechaMechanism on 2016-01-12
> **ian-weisser said:**
> Hmmmm.
That's very interesting (sorry), because v-e-p doesn't have 32-bit and 64-bit versions. There's just one 'all' version. The error message is right.
I wonder where the call for a 64-bit version is coming from?Ok.  Is there some way to just nuke the package completely and I can try again.  Software center froze during install and I had to kill it, maybe that's why I'm having trouble.

---

### Post by ian-weisser on 2016-01-12
> **MechaMechanism said:**
> Software center froze during install and I had to kill it
Ah, that's important information. Next time, please mention it up front.
It sometimes changes the best way to troubleshoot.

Try the following, and please show us the complete output if it doesn't work:
```
sudo apt update
sudo apt-get autoremove
sudo dpkg --remove virtualbox-ext-pack
```

---

### Post by MechaMechanism on 2016-01-12
Didn't work.

```
nate@frontier:~$ sudo apt update
[sudo] password for nate: 
Hit http://us.archive.ubuntu.com wily InRelease
Get:1 http://security.ubuntu.com wily-security InRelease [64.4 kB]             
Get:2 http://us.archive.ubuntu.com wily-updates InRelease [64.4 kB]            
Hit http://archive.canonical.com wily InRelease                                
Hit http://ppa.launchpad.net wily InRelease                                    
Hit http://archive.canonical.com wily/partner Sources                          
Get:3 http://security.ubuntu.com wily-security/main Sources [25.6 kB]          
Hit http://ppa.launchpad.net wily/main Sources                                 
Hit http://archive.canonical.com wily/partner amd64 Packages                   
Hit http://us.archive.ubuntu.com wily-backports InRelease                      
Hit http://ppa.launchpad.net wily/main amd64 Packages                          
Get:4 http://security.ubuntu.com wily-security/restricted Sources [2,854 B]    
Hit http://us.archive.ubuntu.com wily/main Sources                             
Hit http://archive.canonical.com wily/partner i386 Packages                    
Get:5 http://security.ubuntu.com wily-security/universe Sources [6,531 B]      
Hit http://us.archive.ubuntu.com wily/restricted Sources                       
Hit http://ppa.launchpad.net wily/main i386 Packages                           
Get:6 http://security.ubuntu.com wily-security/multiverse Sources [1,913 B]    
Hit http://us.archive.ubuntu.com wily/universe Sources                         
Hit http://archive.canonical.com wily/partner Translation-en                   
Get:7 http://security.ubuntu.com wily-security/main amd64 Packages [79.4 kB]   
Hit http://us.archive.ubuntu.com wily/multiverse Sources                       
Hit http://ppa.launchpad.net wily/main Translation-en                          
Hit http://us.archive.ubuntu.com wily/main amd64 Packages                   
Hit http://us.archive.ubuntu.com wily/restricted amd64 Packages                
Get:8 http://security.ubuntu.com wily-security/restricted amd64 Packages [10.9 kB]
Hit http://us.archive.ubuntu.com wily/universe amd64 Packages                  
Get:9 http://security.ubuntu.com wily-security/universe amd64 Packages [35.8 kB]
Hit http://us.archive.ubuntu.com wily/multiverse amd64 Packages               
Hit http://us.archive.ubuntu.com wily/main i386 Packages                       
Get:10 http://security.ubuntu.com wily-security/multiverse amd64 Packages [5,856 B]
Hit http://us.archive.ubuntu.com wily/restricted i386 Packages                 
Get:11 http://security.ubuntu.com wily-security/main i386 Packages [77.4 kB]
Hit http://us.archive.ubuntu.com wily/universe i386 Packages                  
Hit http://us.archive.ubuntu.com wily/multiverse i386 Packages                 
Hit http://us.archive.ubuntu.com wily/main Translation-en                      
Get:12 http://security.ubuntu.com wily-security/restricted i386 Packages [10.8 kB]
Hit http://us.archive.ubuntu.com wily/multiverse Translation-en                
Get:13 http://security.ubuntu.com wily-security/universe i386 Packages [35.8 kB]
Hit http://us.archive.ubuntu.com wily/restricted Translation-en               
Get:14 http://security.ubuntu.com wily-security/multiverse i386 Packages [6,064 B]
Hit http://us.archive.ubuntu.com wily/universe Translation-en                  
Get:15 http://security.ubuntu.com wily-security/main Translation-en [39.8 kB]
Get:16 http://us.archive.ubuntu.com wily-updates/main Sources [41.4 kB]        
Get:17 http://security.ubuntu.com wily-security/multiverse Translation-en [2,536 B]
Get:18 http://us.archive.ubuntu.com wily-updates/restricted Sources [3,741 B]  
Get:19 http://security.ubuntu.com wily-security/restricted Translation-en [2,666 B]
Get:20 http://us.archive.ubuntu.com wily-updates/universe Sources [11.3 kB]   
Get:21 http://security.ubuntu.com wily-security/universe Translation-en [23.8 kB]
Get:22 http://us.archive.ubuntu.com wily-updates/multiverse Sources [1,913 B]
Get:23 http://us.archive.ubuntu.com wily-updates/main amd64 Packages [111 kB]
Get:24 http://us.archive.ubuntu.com wily-updates/restricted amd64 Packages [13.3 kB]
Get:25 http://us.archive.ubuntu.com wily-updates/universe amd64 Packages [50.4 kB]
Get:26 http://us.archive.ubuntu.com wily-updates/multiverse amd64 Packages [5,856 B]
Get:27 http://us.archive.ubuntu.com wily-updates/main i386 Packages [108 kB]
Get:28 http://us.archive.ubuntu.com wily-updates/restricted i386 Packages [13.4 kB]
Get:29 http://us.archive.ubuntu.com wily-updates/universe i386 Packages [48.4 kB]
Get:30 http://us.archive.ubuntu.com wily-updates/multiverse i386 Packages [6,064 B]
Get:31 http://us.archive.ubuntu.com wily-updates/main Translation-en [54.3 kB]
Get:32 http://us.archive.ubuntu.com wily-updates/multiverse Translation-en [2,536 B]
Get:33 http://us.archive.ubuntu.com wily-updates/restricted Translation-en [3,024 B]
Get:34 http://us.archive.ubuntu.com wily-updates/universe Translation-en [32.5 kB]
Hit http://us.archive.ubuntu.com wily-backports/main Sources
Hit http://us.archive.ubuntu.com wily-backports/restricted Sources
Hit http://us.archive.ubuntu.com wily-backports/universe Sources               
Hit http://us.archive.ubuntu.com wily-backports/multiverse Sources             
Hit http://us.archive.ubuntu.com wily-backports/main amd64 Packages            
Hit http://us.archive.ubuntu.com wily-backports/restricted amd64 Packages      
Hit http://us.archive.ubuntu.com wily-backports/universe amd64 Packages        
Hit http://us.archive.ubuntu.com wily-backports/multiverse amd64 Packages      
Hit http://us.archive.ubuntu.com wily-backports/main i386 Packages             
Hit http://us.archive.ubuntu.com wily-backports/restricted i386 Packages       
Hit http://us.archive.ubuntu.com wily-backports/universe i386 Packages         
Hit http://us.archive.ubuntu.com wily-backports/multiverse i386 Packages       
Hit http://us.archive.ubuntu.com wily-backports/main Translation-en            
Hit http://us.archive.ubuntu.com wily-backports/multiverse Translation-en      
Hit http://us.archive.ubuntu.com wily-backports/restricted Translation-en      
Hit http://us.archive.ubuntu.com wily-backports/universe Translation-en        
Fetched 1,004 kB in 7s (128 kB/s)                                              
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
```

```
nate@frontier:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-4.2.0-19 linux-headers-4.2.0-19-generic
  linux-image-4.2.0-19-generic linux-image-extra-4.2.0-19-generic
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 287 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 250544 files and directories currently installed.)
Removing linux-headers-4.2.0-19-generic (4.2.0-19.23) ...
Removing linux-headers-4.2.0-19 (4.2.0-19.23) ...
Removing linux-image-extra-4.2.0-19-generic (4.2.0-19.23) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-19-generic /boot/vmlinuz-4.2.0-19-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.2.0-19-generic /boot/vmlinuz-4.2.0-19-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-19-generic /boot/vmlinuz-4.2.0-19-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-19-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.2.0-19-generic /boot/vmlinuz-4.2.0-19-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.2.0-19-generic /boot/vmlinuz-4.2.0-19-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.2.0-19-generic /boot/vmlinuz-4.2.0-19-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.2.0-19-generic /boot/vmlinuz-4.2.0-19-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-23-generic
Found initrd image: /boot/initrd.img-4.2.0-23-generic
Found linux image: /boot/vmlinuz-4.2.0-22-generic
Found initrd image: /boot/initrd.img-4.2.0-22-generic
Found linux image: /boot/vmlinuz-4.2.0-19-generic
Found initrd image: /boot/initrd.img-4.2.0-19-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Removing linux-image-4.2.0-19-generic (4.2.0-19.23) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.2.0-19-generic /boot/vmlinuz-4.2.0-19-generic
dkms: removing: virtualbox 5.0.10 (4.2.0-19-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 5.0.10
Kernel:  4.2.0-19-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.2.0-19-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.2.0-19-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.2.0-19-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.2.0-19-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-19-generic /boot/vmlinuz-4.2.0-19-generic
update-initramfs: Deleting /boot/initrd.img-4.2.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-19-generic /boot/vmlinuz-4.2.0-19-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-23-generic
Found initrd image: /boot/initrd.img-4.2.0-23-generic
Found linux image: /boot/vmlinuz-4.2.0-22-generic
Found initrd image: /boot/initrd.img-4.2.0-22-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up virtualbox-ext-pack (5.0.4-2) ...
dpkg: error processing package virtualbox-ext-pack (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 virtualbox-ext-pack
[ Rootkit Hunter version 1.4.2 ]
File updated: searched for 176 files, found 148
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
nate@frontier:~$ sudo dpkg --remove virtualbox-ext-pack
(Reading database ... 219321 files and directories currently installed.)
Removing virtualbox-ext-pack (5.0.4-2) ...
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
Successfully uninstalled "Oracle VM VirtualBox Extension Pack".
Successfully performed extension pack cleanup
dpkg: error processing package virtualbox-ext-pack (--remove):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 virtualbox-ext-pack
```

---

### Post by ian-weisser on 2016-01-12
> **MechaMechanism said:**
> 
Successfully uninstalled "Oracle VM VirtualBox Extension Pack".
Successfully performed extension pack cleanup

Perhaps it worked better than given credit for.
Seems like the package files are uninstalled (hooray), but the dpkg failure may indicate that the package manager still considers it installed.

Let's find out.

Try
```
dpkg -l | grep virtualbox    ## That's a lowercase '-L' 
```

---

### Post by MechaMechanism on 2016-01-13
```
nate@frontier:~$ dpkg -l | grep virtualbox
ii  unity-scope-virtualbox                        0.1+13.10.20130723-0ubuntu1                all          VirtualBox scope for Unity
ii  virtualbox                                    5.0.10-dfsg-2ubuntu1                       amd64        x86 virtualization solution - base binaries
ii  virtualbox-dkms                               5.0.10-dfsg-2ubuntu1                       all          x86 virtualization solution - kernel module sources for dkms
rF  virtualbox-ext-pack                           5.0.4-2                                    all          extra capabilities for VirtualBox
ii  virtualbox-guest-additions-iso                5.0.4-1                                    all          guest additions iso image for VirtualBox
ii  virtualbox-qt                                 5.0.10-dfsg-2ubuntu1                       amd64        x86 virtualization solution - Qt based user interface
```

---

### Post by ian-weisser on 2016-01-13
Okay, we were nice. Time to get out the dangerous medicine.
Don't use dpkg --force commands unless you have tried the safer stuff first...which you have done in this thread.

Try:
```
sudo dpkg --purge --force-remove-reinstreq virtualbox-ext-pack     ## Tell dpkg to 'forget' the package
sudo apt update
sudo apt upgrade                                                   ## Test the package manager for errors
sudo apt-get clean virtualbox-ext-pack                             ## Remove the package from your local cache
```

---

### Post by MechaMechanism on 2016-01-13
I don't think it worked.

```
nate@frontier:~$ sudo dpkg --purge --force-remove-reinstreq virtualbox-ext-pack
[sudo] password for nate: 
(Reading database ... 219321 files and directories currently installed.)
Removing virtualbox-ext-pack (5.0.4-2) ...
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
Successfully uninstalled "Oracle VM VirtualBox Extension Pack".
Successfully performed extension pack cleanup
dpkg: error processing package virtualbox-ext-pack (--purge):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 virtualbox-ext-pack
```

```
nate@frontier:~$ sudo apt update
Hit http://us.archive.ubuntu.com wily InRelease
Get:1 http://security.ubuntu.com wily-security InRelease [64.4 kB]             
Get:2 http://us.archive.ubuntu.com wily-updates InRelease [64.4 kB]            
Hit http://archive.canonical.com wily InRelease                                
Hit http://ppa.launchpad.net wily InRelease                                    
Hit http://archive.canonical.com wily/partner Sources                          
Get:3 http://security.ubuntu.com wily-security/main Sources [26.0 kB]          
Hit http://ppa.launchpad.net wily/main Sources                                 
Hit http://us.archive.ubuntu.com wily-backports InRelease                      
Hit http://archive.canonical.com wily/partner amd64 Packages                   
Get:4 http://security.ubuntu.com wily-security/restricted Sources [2,854 B]    
Hit http://us.archive.ubuntu.com wily/main Sources                             
Get:5 http://security.ubuntu.com wily-security/universe Sources [7,013 B]      
Hit http://ppa.launchpad.net wily/main amd64 Packages                          
Hit http://us.archive.ubuntu.com wily/restricted Sources                       
Hit http://archive.canonical.com wily/partner i386 Packages                    
Get:6 http://security.ubuntu.com wily-security/multiverse Sources [1,913 B]    
Hit http://us.archive.ubuntu.com wily/universe Sources                         
Get:7 http://security.ubuntu.com wily-security/main amd64 Packages [80.5 kB]   
Hit http://us.archive.ubuntu.com wily/multiverse Sources                       
Hit http://ppa.launchpad.net wily/main i386 Packages                           
Hit http://us.archive.ubuntu.com wily/main amd64 Packages                      
Hit http://us.archive.ubuntu.com wily/restricted amd64 Packages                
Hit http://ppa.launchpad.net wily/main Translation-en                          
Get:8 http://security.ubuntu.com wily-security/restricted amd64 Packages [10.9 kB]
Hit http://us.archive.ubuntu.com wily/universe amd64 Packages                  
Get:9 http://security.ubuntu.com wily-security/universe amd64 Packages [36.5 kB]
Hit http://us.archive.ubuntu.com wily/multiverse amd64 Packages                
Ign http://archive.canonical.com wily/partner Translation-en                   
Get:10 http://security.ubuntu.com wily-security/multiverse amd64 Packages [5,856 B]
Hit http://us.archive.ubuntu.com wily/main i386 Packages                       
Get:11 http://security.ubuntu.com wily-security/main i386 Packages [78.5 kB]
Hit http://us.archive.ubuntu.com wily/restricted i386 Packages                 
Hit http://us.archive.ubuntu.com wily/universe i386 Packages                   
Get:12 http://security.ubuntu.com wily-security/restricted i386 Packages [10.8 kB]
Hit http://us.archive.ubuntu.com wily/multiverse i386 Packages                 
Get:13 http://security.ubuntu.com wily-security/universe i386 Packages [36.5 kB]
Hit http://us.archive.ubuntu.com wily/main Translation-en                      
Get:14 http://security.ubuntu.com wily-security/multiverse i386 Packages [6,064 B]
Hit http://us.archive.ubuntu.com wily/multiverse Translation-en                
Hit http://security.ubuntu.com wily-security/main Translation-en               
Hit http://us.archive.ubuntu.com wily/restricted Translation-en    
Hit http://security.ubuntu.com wily-security/multiverse Translation-en
Hit http://security.ubuntu.com wily-security/restricted Translation-en
Hit http://us.archive.ubuntu.com wily/universe Translation-en  
Hit http://security.ubuntu.com wily-security/universe Translation-en
Get:15 http://us.archive.ubuntu.com wily-updates/main Sources [41.9 kB]
Get:16 http://us.archive.ubuntu.com wily-updates/restricted Sources [3,741 B]
Get:17 http://us.archive.ubuntu.com wily-updates/universe Sources [11.7 kB]
Get:18 http://us.archive.ubuntu.com wily-updates/multiverse Sources [1,913 B]
Get:19 http://us.archive.ubuntu.com wily-updates/main amd64 Packages [112 kB]
Get:20 http://us.archive.ubuntu.com wily-updates/restricted amd64 Packages [13.3 kB]
Get:21 http://us.archive.ubuntu.com wily-updates/universe amd64 Packages [51.1 kB]
Get:22 http://us.archive.ubuntu.com wily-updates/multiverse amd64 Packages [5,856 B]
Get:23 http://us.archive.ubuntu.com wily-updates/main i386 Packages [109 kB]
Get:24 http://us.archive.ubuntu.com wily-updates/restricted i386 Packages [13.4 kB]
Get:25 http://us.archive.ubuntu.com wily-updates/universe i386 Packages [49.2 kB]
Get:26 http://us.archive.ubuntu.com wily-updates/multiverse i386 Packages [6,064 B]
Hit http://us.archive.ubuntu.com wily-updates/main Translation-en
Hit http://us.archive.ubuntu.com wily-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com wily-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com wily-updates/universe Translation-en
Hit http://us.archive.ubuntu.com wily-backports/main Sources
Hit http://us.archive.ubuntu.com wily-backports/restricted Sources
Hit http://us.archive.ubuntu.com wily-backports/universe Sources
Hit http://us.archive.ubuntu.com wily-backports/multiverse Sources
Hit http://us.archive.ubuntu.com wily-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com wily-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com wily-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com wily-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com wily-backports/main i386 Packages
Hit http://us.archive.ubuntu.com wily-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com wily-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com wily-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com wily-backports/main Translation-en
Hit http://us.archive.ubuntu.com wily-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com wily-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com wily-backports/universe Translation-en
Fetched 851 kB in 4s (171 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
```

```
nate@frontier:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following packages were automatically installed and are no longer required:
  linux-headers-4.2.0-22 linux-headers-4.2.0-22-generic
  linux-image-4.2.0-22-generic linux-image-extra-4.2.0-22-generic
Use 'apt-get autoremove' to remove them.
Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up virtualbox-ext-pack (5.0.4-2) ...
dpkg: error processing package virtualbox-ext-pack (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 virtualbox-ext-pack
[ Rootkit Hunter version 1.4.2 ]
File updated: searched for 176 files, found 148
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


```
nate@frontier:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.2.0-22 linux-headers-4.2.0-22-generic
  linux-image-4.2.0-22-generic linux-image-extra-4.2.0-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up virtualbox-ext-pack (5.0.4-2) ...
dpkg: error processing package virtualbox-ext-pack (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 virtualbox-ext-pack
[ Rootkit Hunter version 1.4.2 ]
File updated: searched for 176 files, found 148
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by mc4man on 2016-01-13
Have you read thru /var/log/dpkg.log?
Does this help?
```
sudo dpkg --configure -a
```
Then ck. bottom of log again

---

### Post by MechaMechanism on 2016-01-13
Tail of log dpkg.log after running nate@frontier:~$ sudo dpkg --configure -a

```
2016-01-13 08:30:28 startup packages purge
2016-01-13 08:30:28 status half-configured virtualbox-ext-pack:all 5.0.4-2
2016-01-13 08:30:28 remove virtualbox-ext-pack:all 5.0.4-2 <none>
2016-01-13 08:30:28 status half-configured virtualbox-ext-pack:all 5.0.4-2
2016-01-13 08:30:28 status half-configured virtualbox-ext-pack:all 5.0.4-2
2016-01-13 08:31:19 startup packages configure
2016-01-13 08:31:19 configure virtualbox-ext-pack:all 5.0.4-2 <none>
2016-01-13 08:31:19 status half-configured virtualbox-ext-pack:all 5.0.4-2
2016-01-13 08:31:57 startup packages configure
2016-01-13 08:31:57 configure virtualbox-ext-pack:all 5.0.4-2 <none>
2016-01-13 08:31:57 status half-configured virtualbox-ext-pack:all 5.0.4-2
2016-01-13 13:48:07 startup packages configure
```

---

### Post by MechaMechanism on 2016-01-14
Still not working.  Here are more commands.

Does not work,  sudo dpkg --remove --force-remove-reinstreq package_name

Does not work, sudo rm -rf  /var/cache/apt/archives/name sudo apt-get autoclean sudo apt-get update sudo apt-get upgrade

Does not work, sudo dpkg -i --force-overwrite /var/cache/apt/archives/name

```
nate@frontier:~$ sudo dpkg -P virtualbox-ext-pack_5.0.4-2_all
dpkg: warning: ignoring request to remove virtualbox-ext-pack_5.0.4-2_all which isn't installed
```

```
nate@frontier:~$ sudo dpkg -r virtualbox-ext-pack_5.0.4-2_all
dpkg: warning: ignoring request to remove virtualbox-ext-pack_5.0.4-2_all which isn't installed
```

```
nate@frontier:~$ sudo dpkg -i virtualbox-ext-pack_5.0.4-2_all.deb
Selecting previously unselected package virtualbox-ext-pack.
(Reading database ... 219325 files and directories currently installed.)
Preparing to unpack virtualbox-ext-pack_5.0.4-2_all.deb ...
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
Successfully uninstalled "Oracle VM VirtualBox Extension Pack".
Successfully performed extension pack cleanup
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
Successfully uninstalled "Oracle VM VirtualBox Extension Pack".
Successfully performed extension pack cleanup
dpkg: error processing archive virtualbox-ext-pack_5.0.4-2_all.deb (--install):
 subprocess new pre-removal script returned error exit status 1
Errors were encountered while processing:
 virtualbox-ext-pack_5.0.4-2_all.deb
```

Grrr.

---

### Post by ian-weisser on 2016-01-14
Does the files /var/lib/dpkg/info/virtualbox-ext-pack_5.0.4-2* exist?
If so, please show us the contents of the prerm file.

---

### Post by MechaMechanism on 2016-01-14
```
#!/bin/sh
set -e

vboxmanage extpack uninstall "Oracle VM VirtualBox Extension Pack"
vboxmanage extpack cleanup
rm /usr/share/virtualbox-ext-pack/*.vbox-extpack 1>/dev/null 2>&1 # Maybe we should specify the file like in the postinst?


```

---

### Post by ian-weisser on 2016-01-14
Do the files in /usr/share/virtualbox-ext-pack/*.vbox-extpack exist?

If so, (use sudo and) delete them. Then (use sudo and) comment out the final line in the prerm file.
That shuld get rid of the error.

Then sudo dpkg -P virtualbox-ext-pack

---

### Post by MechaMechanism on 2016-01-14
> **ian-weisser said:**
> Do the files in /usr/share/virtualbox-ext-pack/*.vbox-extpack exist?

If so, (use sudo and) delete them. Then (use sudo and) comment out the final line in the prerm file.
That shuld get rid of the error.

Then sudo dpkg -P virtualbox-ext-packThat worked.  So like, I tried to reinstall from the Software Center and Software Center froze and I had to kill it.  I had to do the same process to remove it.  I tried to install from CLI using sudo dpkg -i virtualbox-ext-pack_5.0.4-2_all.deb and it worked.  I see that a EULA was present and also that the package downloaded something.  I think the EULA and download are messing up Software Center.

Thanks again.

Nate.

---

