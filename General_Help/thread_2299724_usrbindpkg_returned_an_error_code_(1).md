---
title: "/usr/bin/dpkg returned an error code (1)"
date: 2015-10-20
forum: General Help
---

### Post by Sujay_Kirti on 2015-10-20
I searched quite a bit for this and none of the solutions worked for me. In most of the cases, this issue was due to /boot being full, which is not my case. Anyway, I've not even created separate /boot.

The culprit files are - **linux-image-3.16.0.30-generic** and [B]linux-image-extra-3.16.0.30-generic.

[/B]I don't know how this issue occurred as I had not booted into my Linux since long (fortnight), and then I saw this.

Any help will be appreciated.

Thanks !

PS: Currently on 14.04 LTS / 3.16.0.49-generic

---

### Post by ian-weisser on 2015-10-20
Please open a terminal and show us the complete output of the commands:
```
sudo apt-get update
sudo apt-get upgrade
```
Copy-and-paste the complete output here.
Use [code tags]("http://ubuntuforums.org/showthread.php?t=1189729") to make the output readable.

---

### Post by Sujay_Kirti on 2015-10-21
sudo apt-get update
```

Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty InRelease                              
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates InRelease [64.4 kB]          
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [64.4 kB]           
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports InRelease [64.5 kB]        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [97.6 kB]        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/main Sources [240 kB]        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [3,357 B]  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [31.0 kB]    
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [2,346 B]  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_IN                     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [356 kB] 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/restricted Sources [4,722 B]
Get:11 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/universe Sources [140 kB]   
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [12.4 kB]
Get:13 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/multiverse Sources [5,145 B]
Get:14 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/main amd64 Packages [635 kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [117 kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [3,688 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [338 kB]  
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12.2 kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [117 kB]
Get:20 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [15.4 kB]
Get:21 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/universe amd64 Packages [323 kB]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [3,846 B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [194 kB] 
Get:24 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [12.0 kB]
Get:25 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/main i386 Packages [615 kB] 
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en [1,679 B]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en [3,076 B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [68.3 kB]
Get:29 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.1 kB]
Get:30 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/universe i386 Packages [324 kB]
Get:31 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [12.1 kB]
Get:32 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/main Translation-en [308 kB]
Get:33 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/multiverse Translation-en [6,148 B]
Get:34 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/restricted Translation-en [3,569 B]
Get:35 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/universe Translation-en [170 kB]
Get:36 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/main Sources [6,687 B]    
Get:37 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/restricted Sources [28 B] 
Get:38 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/universe Sources [30.4 kB]
Get:39 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/multiverse Sources [1,898 B]
Get:40 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/main amd64 Packages [6,643 B]
Get:41 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/restricted amd64 Packages [28 B]
Get:42 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/universe amd64 Packages [36.2 kB]
Get:43 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages [1,571 B]
Get:44 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/main i386 Packages [6,645 B]
Get:45 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/restricted i386 Packages [28 B]
Get:46 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/universe i386 Packages [36.3 kB]
Get:47 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [1,552 B]
Get:48 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/main Translation-en [3,795 B]
Get:49 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/multiverse Translation-en [1,215 B]
Get:50 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/restricted Translation-en [14 B]
Get:51 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/universe Translation-en [32.1 kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty Release                                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/main Sources                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/universe Translation-en                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/main Translation-en_IN                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/multiverse Translation-en_IN           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/restricted Translation-en_IN           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/universe Translation-en_IN             
Fetched 4,549 kB in 26s (171 kB/s)                                             
Reading package lists... Done

```

sudo apt-get upgrade

```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic
The following packages will be upgraded:
  libminiupnpc8
1 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
8 not fully installed or removed.
Need to get 20.3 kB of archives.
After this operation, 201 MB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-updates/main libminiupnpc8 amd64 1.6-3ubuntu2.14.04.2 [20.3 kB]
Fetched 20.3 kB in 0s (25.4 kB/s)        
(Reading database ... 361325 files and directories currently installed.)
Removing linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
depmod: FATAL: could not load /boot/System.map-3.16.0-30-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-30-generic
grep: /boot/config-3.16.0-30-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_v6M1bm/lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_v6M1bm/lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-3.16.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.16.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.16.0-30-generic.postrm line 328.
dpkg: error processing package linux-image-3.16.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.16.0-30-generic
 linux-image-3.16.0-30-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

PS: I'm new to this forum. Doesn't this forum has spoiler tags ?

---

### Post by ian-weisser on 2015-10-21
> **Sujay_Kirti said:**
> Removing linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
depmod: FATAL: could not load /boot/System.map-3.16.0-30-generic: **No such file or directory**
[...]
PS: I'm new to this forum. Doesn't this forum has spoiler tags ?

See the problem (in bold)?
This usually happens when a well-intentioned user manually 'cleans out' files that are installed by the package manager. Never do that. Always use the package manager to uninstall the package.

The workaround to this specific problem is simple - create an empty dummy file for the package manager to remove.
```
sudo touch /boot/System.map-3.16.0-30-generic
```


What's a 'spoiler tag' ?

---

### Post by vasa1 on 2015-10-21
```
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
```
Is this a separate problem or is it related to the one ian-weisser pointed out?

---

### Post by deadflowr on 2015-10-21
> [COLOR=#000000]What's a 'spoiler tag' ?[/COLOR]
Spoiler tags are special tags that some forums and other places have that will hide sections of comments for view unless hovered(accessed) by a user to view.
Usually associated with threads or blogs or what have you on media sites, so users don't spoil certain parts of some show or movie or book or what have you.
Utterly pointless here. 

Also +1 to already suggested advice going forward, thus far.

---

### Post by Sujay_Kirti on 2015-10-21
> **ian-weisser said:**
> See the problem (in bold)?
This usually happens when a well-intentioned user manually 'cleans out' files that are installed by the package manager. Never do that. Always use the package manager to uninstall the package.

The workaround to this specific problem is simple - create an empty dummy file for the package manager to remove.
```
sudo touch /boot/System.map-3.16.0-30-generic
```


What's a 'spoiler tag' ?

I don't remember cleaning out any files, manually. I'm not so well versed in Ubuntu, just a normal dev. Thanks for the suggestion though.

I tried your command, but the **autoremove **didn't work, neither did update -> upgrade.

Here's the output of sudo apt-get upgrade

```
sudo apt-get upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic
The following packages will be upgraded:
  apache2 apache2-bin apache2-data gir1.2-nmgtk-1.0 indicator-session
  libminiupnpc8 libnm-gtk-common libnm-gtk0 network-manager-gnome
9 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
8 not fully installed or removed.
Need to get 1,572 kB/1,592 kB of archives.
After this operation, 201 MB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main apache2 amd64 2.4.7-1ubuntu4.8 [87.6 kB]
Get:2 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main apache2-bin amd64 2.4.7-1ubuntu4.8 [840 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main apache2-data all 2.4.7-1ubuntu4.8 [160 kB]
Get:4 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main network-manager-gnome amd64 0.9.8.8-0ubuntu4.4 [312 kB]
Get:5 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main libnm-gtk0 amd64 0.9.8.8-0ubuntu4.4 [59.9 kB]
Get:6 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main libnm-gtk-common all 0.9.8.8-0ubuntu4.4 [4,320 B]
Get:7 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main gir1.2-nmgtk-1.0 amd64 0.9.8.8-0ubuntu4.4 [4,234 B]
Get:8 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main indicator-session amd64 12.10.5+14.04.20151008-0ubuntu1 [104 kB]
Fetched 1,572 kB in 7s (208 kB/s)                                              
(Reading database ... 361325 files and directories currently installed.)
Removing linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
depmod: WARNING: could not open /lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-30-generic
grep: /boot/config-3.16.0-30-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_CuOWQm/lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_CuOWQm/lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-3.16.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.16.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.16.0-30-generic.postrm line 328.
dpkg: error processing package linux-image-3.16.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.16.0-30-generic
 linux-image-3.16.0-30-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

PS: Spoiler - [http://www.digit.in/forum/chit-chat/190501-flash-arrow-thread-28.html#post2263236](http://www.digit.in/forum/chit-chat/190501-flash-arrow-thread-28.html#post2263236)

---

### Post by Sujay_Kirti on 2015-10-21
> **vasa1 said:**
> ```
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
```
Is this a separate problem or is it related to the one ian-weisser pointed out?

Don't know. May be you guys can throw some light.

> **deadflowr said:**
> Spoiler tags are special tags that some forums and other places have that will hide sections of comments for view unless hovered(accessed) by a user to view.
Usually associated with threads or blogs or what have you on media sites, so users don't spoil certain parts of some show or movie or book or what have you.
Utterly pointless here. 


Indeed the purpose of spoiler tag is what you mentioned, but sometimes, posts look clean when things are "minimized", just my view though. :)

---

### Post by vasa1 on 2015-10-21
Others may differ but I'd go with "backup your data and do a clean install".

---

### Post by ian-weisser on 2015-10-21
> **Sujay_Kirti said:**
> I tried your command, but the **autoremove **didn't work, neither did update -> upgrade.
Autoremove is unrelated to your problem, and wouldn't help anyway.
Apt already knows that you want to uninstall the package. It's trying, but one package is hopelessly broken, and cannot be uninstalled.

Try reinstalling the offending package
```
sudo apt-get install --reinstall linux-image-3.16.0-30-generic
sudo apt-get remove linux-image-3.16.0-30-generic
```

If that doesn't work, there are more powerful ways to accomplish it. We try the ways that don't cause damage first....

---

### Post by Sujay_Kirti on 2015-10-21
> **vasa1 said:**
> Others may differ but I'd go with "backup your data and do a clean install".

That's the last option. Last time, not long ago, I had to do that just because of a simple permission error. Sometimes, things get too complex in Linux or maybe I'm not that well versed.

> **ian-weisser said:**
> Autoremove is unrelated to your problem, and wouldn't help anyway.
Apt already knows that you want to uninstall the package. It's trying, but one package is hopelessly broken, and cannot be uninstalled.

Try reinstalling the offending package
```
sudo apt-get install --reinstall linux-image-3.16.0-30-generic
sudo apt-get remove linux-image-3.16.0-30-generic
```

If that doesn't work, there are more powerful ways to accomplish it. We try the ways that don't cause damage first....


Installation failed buddy. I am wondering, why is it trying to "remove" when we're giving the install command ? Or am I missing something here ?

```
 sudo apt-get install --reinstall linux-image-3.16.0-30-generic[sudo] password for jugs: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-3.16.0-30-generic
0 upgraded, 0 newly installed, 1 reinstalled, 1 to remove and 9 not upgraded.
8 not fully installed or removed.
Need to get 16.1 MB of archives.
After this operation, 156 MB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.16.0-30-generic amd64 3.16.0-30.40~14.04.1 [16.1 MB]
Fetched 16.1 MB in 5min 19s (50.4 kB/s)                                        
(Reading database ... 361325 files and directories currently installed.)
Removing linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
depmod: WARNING: could not open /lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-30-generic
grep: /boot/config-3.16.0-30-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_t1f1xn/lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_t1f1xn/lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-3.16.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.16.0-30-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by ian-weisser on 2015-10-21
Compare the output carefully with previous.  Reinstallation seems to have [I]succeeded.
[/I]Now do the same reinstall with the linux-image-extra-3.16.0-30-generic package.

---

### Post by Sujay_Kirti on 2015-10-22
sudo apt-get remove linux-image-extra-3.16.0-30-generic

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic
0 upgraded, 0 newly installed, 2 to remove and 9 not upgraded.
8 not fully installed or removed.
After this operation, 201 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 365585 files and directories currently installed.)
Removing linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
depmod: WARNING: could not open /lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-30-generic
grep: /boot/config-3.16.0-30-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_I149hW/lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_I149hW/lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-3.16.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.16.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.16.0-30-generic.postrm line 328.
dpkg: error processing package linux-image-3.16.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.16.0-30-generic
 linux-image-3.16.0-30-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

sudo apt-get upgrade

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic
The following packages will be upgraded:
  apache2 apache2-bin apache2-data gir1.2-nmgtk-1.0 indicator-session
  libminiupnpc8 libnm-gtk-common libnm-gtk0 network-manager-gnome
9 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
8 not fully installed or removed.
Need to get 0 B/1,592 kB of archives.
After this operation, 201 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 361325 files and directories currently installed.)
Removing linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
depmod: WARNING: could not open /lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-30-generic
grep: /boot/config-3.16.0-30-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_Nen3vn/lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_Nen3vn/lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-3.16.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.16.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.16.0-30-generic.postrm line 328.
dpkg: error processing package linux-image-3.16.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.16.0-30-generic
 linux-image-3.16.0-30-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by ian-weisser on 2015-10-22
Reinstall linux-image-extra-3.16.0-30-generic first, then remove it.
Just like you did with linux-image-3.16.0-30-generic.

---

### Post by Sujay_Kirti on 2015-10-22
> **ian-weisser said:**
> Reinstall linux-image-extra-3.16.0-30-generic first, then remove it.
Just like you did with linux-image-3.16.0-30-generic.

I already did it sire, just that I didn't post it here.

I followed exactly the same steps you asked me to do.

Install -> Removal.

---

### Post by ian-weisser on 2015-10-22
Next to try:
```
sudo dpkg --purge linux-image-extra-3.16.0-30-generic linux-image-3.16.0-30-generic
```
The error messages, if any, should be different.

---

### Post by Sujay_Kirti on 2015-10-26
Please find the output of the commands you requested:[B]


 sudo apt-get install --reinstall linux-image-3.16.0-30-generic
[/B]
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-3.16.0-30-generic
0 upgraded, 0 newly installed, 1 reinstalled, 1 to remove and 10 not upgraded.
8 not fully installed or removed.
Need to get 0 B/16.1 MB of archives.
After this operation, 156 MB disk space will be freed.
Do you want to continue? [Y/n] y\
(Reading database ... 361325 files and directories currently installed.)
Removing linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
depmod: WARNING: could not open /lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-30-generic
grep: /boot/config-3.16.0-30-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_tyuk7h/lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_tyuk7h/lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-3.16.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.16.0-30-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

**sudo apt-get remove linux-image-3.16.0-30-generic**

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic
0 upgraded, 0 newly installed, 2 to remove and 10 not upgraded.
8 not fully installed or removed.
After this operation, 201 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 361325 files and directories currently installed.)
Removing linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
depmod: WARNING: could not open /lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-30-generic
grep: /boot/config-3.16.0-30-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_6KWkXP/lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_6KWkXP/lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-3.16.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.16.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.16.0-30-generic.postrm line 328.
dpkg: error processing package linux-image-3.16.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.16.0-30-generic
 linux-image-3.16.0-30-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

[B]sudo apt-get install --reinstall linux-image-extra-3.16.0-30-generic

[/B]```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 10 not upgraded.
8 not fully installed or removed.
Need to get 0 B/53.8 MB of archives.
After this operation, 0 B of additional disk space will be used.
Selecting previously unselected package linux-image-extra-3.16.0-30-generic.
(Reading database ... 361326 files and directories currently installed.)
Preparing to unpack .../linux-image-extra-3.16.0-30-generic_3.16.0-30.40~14.04.1_amd64.deb ...
Unpacking linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1) over (3.16.0-30.40~14.04.1) ...
dpkg: error processing package linux-image-3.16.0-30-generic (--configure):
 package linux-image-3.16.0-30-generic is not ready for configuration
 cannot configure (current status `half-installed')
Setting up linux-image-3.16.0-50-generic (3.16.0-50.67~14.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-50-generic /boot/vmlinuz-3.16.0-50-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-50-generic /boot/vmlinuz-3.16.0-50-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-50-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-50-generic /boot/vmlinuz-3.16.0-50-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-50-generic /boot/vmlinuz-3.16.0-50-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-50-generic /boot/vmlinuz-3.16.0-50-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.16.0-50-generic.postinst line 1025.
dpkg: error processing package linux-image-3.16.0-50-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.16.0-51-generic (3.16.0-51.69~14.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-51-generic /boot/vmlinuz-3.16.0-51-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-51-generic /boot/vmlinuz-3.16.0-51-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-51-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-51-generic /boot/vmlinuz-3.16.0-51-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-51-generic /boot/vmlinuz-3.16.0-51-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-51-generic /boot/vmlinuz-3.16.0-51-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.16.0-51-generic.postinst line 1025.
dpkg: error processing package linux-image-3.16.0-51-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.16.0-51-generic:
 linux-image-extra-3.16.0-51-generic depends on linux-image-3.16.0-51-generic; however:
  Package linux-image-3.16.0-51-generic is not configured yet.


dpkg: error processing package linux-image-extra-3.16.0-51-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-lts-utopic:
 linux-image-generic-lts-utopic depends on linux-image-3.16.0-51-generic; however:
  Package linux-image-3.16.0-51-generic is not configured yet.
 linux-image-generic-lts-utopic depends on linux-image-extra-3.16.0-51-generic; however:
  Package linux-image-extra-3.16.0-51-generic is not configured yet.


dpkg: error processing package linux-image-generic-lts-utopic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-utopic:
 linux-generic-lts-utopic depends on linux-image-generic-No apport report written because MaxReports is reached already
                                 No apport report written because MaxReports is reached already
         No apport report written because MaxReports is reached already
                                                                       No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already
                       lts-utopic (= 3.16.0.51.42); however:
  Package linux-image-generic-lts-utopic is not configured yet.


dpkg: error processing package linux-generic-lts-utopic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.16.0-30-generic:
 linux-image-extra-3.16.0-30-generic depends on linux-image-3.16.0-30-generic; however:
  Package linux-image-3.16.0-30-generic is not installed.


dpkg: error processing package linux-image-extra-3.16.0-30-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.16.0-50-generic:
 linux-image-extra-3.16.0-50-generic depends on linux-image-3.16.0-50-generic; however:
  Package linux-image-3.16.0-50-generic is not configured yet.


dpkg: error processing package linux-image-extra-3.16.0-50-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.16.0-30-generic
 linux-image-3.16.0-50-generic
 linux-image-3.16.0-51-generic
 linux-image-extra-3.16.0-51-generic
 linux-image-generic-lts-utopic
 linux-generic-lts-utopic
 linux-image-extra-3.16.0-30-generic
 linux-image-extra-3.16.0-50-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


[B]sudo apt-get remove linux-image-extra-3.16.0-30-generic

[/B]```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic
0 upgraded, 0 newly installed, 2 to remove and 10 not upgraded.
8 not fully installed or removed.
After this operation, 201 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 365585 files and directories currently installed.)
Removing linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
depmod: WARNING: could not open /lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-30-generic
grep: /boot/config-3.16.0-30-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_paCy7H/lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_paCy7H/lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-3.16.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.16.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.16.0-30-generic.postrm line 328.
dpkg: error processing package linux-image-3.16.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.16.0-30-generic
 linux-image-3.16.0-30-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

**sudo dpkg --purge linux-image-extra-3.16.0-30-generic linux-image-3.16.0-30-generic**

```
(Reading database ... 361325 files and directories currently installed.)
Removing linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
depmod: WARNING: could not open /lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-30-generic
grep: /boot/config-3.16.0-30-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_EHLPuw/lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_EHLPuw/lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-3.16.0-30-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.16.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.16.0-30-generic.postrm line 328.
dpkg: error processing package linux-image-3.16.0-30-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.16.0-30-generic
 linux-image-3.16.0-30-generic



```

---

### Post by ian-weisser on 2015-10-26
Okay, next let's fix this error:
> /usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found

Try this:
```
sudo apt-get install --reinstall grub-common
```

Then:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Sujay_Kirti on 2015-10-27
[B]sudo apt-get install --reinstall grub-common

[/B]
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic
0 upgraded, 0 newly installed, 1 reinstalled, 2 to remove and 10 not upgraded.
8 not fully installed or removed.
Need to get 1,674 kB of archives.
After this operation, 201 MB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main grub-common amd64 2.02~beta2-9ubuntu1.3 [1,674 kB]
Fetched 1,674 kB in 7s (225 kB/s)                                              
(Reading database ... 361325 files and directories currently installed.)
Removing linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
depmod: WARNING: could not open /lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-30-generic
grep: /boot/config-3.16.0-30-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_20WrZS/lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_20WrZS/lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-3.16.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.16.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.16.0-30-generic.postrm line 328.
dpkg: error processing package linux-image-3.16.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.16.0-30-generic
 linux-image-3.16.0-30-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


[B]sudo apt-get update


[/B]
```
Ign http://dl.google.com stable InRelease
Ign http://in.archive.ubuntu.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://dl.google.com stable Release.gpg                                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:1 http://security.ubuntu.com trusty-security InRelease [64.4 kB]           
Hit http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Get:2 http://in.archive.ubuntu.com trusty-updates InRelease [64.4 kB]          
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Get:3 http://security.ubuntu.com trusty-security/main Sources [97.7 kB]        
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://in.archive.ubuntu.com trusty-backports InRelease                    
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://in.archive.ubuntu.com trusty Release.gpg                            
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:4 http://in.archive.ubuntu.com trusty-updates/main Sources [241 kB]        
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://dl.google.com stable/main Translation-en_IN                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://dl.google.com stable/main Translation-en                            
Get:5 http://security.ubuntu.com trusty-security/restricted Sources [3,357 B]  
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:6 http://security.ubuntu.com trusty-security/universe Sources [31.0 kB]    
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://extras.ubuntu.com trusty/main Translation-en_IN                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:7 http://in.archive.ubuntu.com trusty-updates/restricted Sources [4,722 B] 
Get:8 http://in.archive.ubuntu.com trusty-updates/universe Sources [140 kB]    
Get:9 http://security.ubuntu.com trusty-security/multiverse Sources [2,346 B] 
Get:10 http://security.ubuntu.com trusty-security/main amd64 Packages [356 kB]
Get:11 http://in.archive.ubuntu.com trusty-updates/multiverse Sources [5,145 B]
Get:12 http://in.archive.ubuntu.com trusty-updates/main amd64 Packages [636 kB]
Get:13 http://security.ubuntu.com trusty-security/restricted amd64 Packages [12.4 kB]
Get:14 http://security.ubuntu.com trusty-security/universe amd64 Packages [117 kB]
Get:15 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,688 B]
Get:16 http://security.ubuntu.com trusty-security/main i386 Packages [338 kB]  
Get:17 http://in.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.4 kB]
Get:18 http://in.archive.ubuntu.com trusty-updates/universe amd64 Packages [324 kB]
Get:19 http://in.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [12.0 kB]
Get:20 http://in.archive.ubuntu.com trusty-updates/main i386 Packages [616 kB] 
Get:21 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.2 kB]
Get:22 http://security.ubuntu.com trusty-security/universe i386 Packages [117 kB]
Get:23 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,846 B]
Get:24 http://security.ubuntu.com trusty-security/main Translation-en [194 kB] 
Get:25 http://security.ubuntu.com trusty-security/multiverse Translation-en [1,679 B]
Get:26 http://security.ubuntu.com trusty-security/restricted Translation-en [3,076 B]
Get:27 http://in.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.1 kB]
Get:28 http://security.ubuntu.com trusty-security/universe Translation-en [68.3 kB]
Get:29 http://in.archive.ubuntu.com trusty-updates/universe i386 Packages [325 kB]
Get:30 http://in.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Get:31 http://in.archive.ubuntu.com trusty-updates/main Translation-en [309 kB]
Get:32 http://in.archive.ubuntu.com trusty-updates/multiverse Translation-en [6,148 B]
Get:33 http://in.archive.ubuntu.com trusty-updates/restricted Translation-en [3,569 B]
Get:34 http://in.archive.ubuntu.com trusty-updates/universe Translation-en [171 kB]
Hit http://in.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://in.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://in.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://in.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://in.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://in.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://in.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://in.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://in.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://in.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://in.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://in.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://in.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://in.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://in.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://in.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://in.archive.ubuntu.com trusty Release                                
Hit http://in.archive.ubuntu.com trusty/main Sources                           
Hit http://in.archive.ubuntu.com trusty/restricted Sources                     
Hit http://in.archive.ubuntu.com trusty/universe Sources                       
Hit http://in.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://in.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://in.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://in.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://in.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://in.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://in.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://in.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://in.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://in.archive.ubuntu.com trusty/main Translation-en                    
Hit http://in.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://in.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://in.archive.ubuntu.com trusty/universe Translation-en                
Ign http://in.archive.ubuntu.com trusty/main Translation-en_IN                 
Ign http://in.archive.ubuntu.com trusty/multiverse Translation-en_IN           
Ign http://in.archive.ubuntu.com trusty/restricted Translation-en_IN           
Ign http://in.archive.ubuntu.com trusty/universe Translation-en_IN             
Fetched 4,326 kB in 34s (127 kB/s)                                             
Reading package lists... Done

```


[B]sudo apt-get upgrade

[/B]
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic
The following packages will be upgraded:
  apache2 apache2-bin apache2-data apport apport-gtk gir1.2-nmgtk-1.0
  google-chrome-stable indicator-session libminiupnpc8 libmysqlclient18
  libnm-gtk-common libnm-gtk0 mysql-client-5.5 mysql-client-core-5.5
  mysql-common mysql-server mysql-server-5.5 mysql-server-core-5.5
  network-manager-gnome ntpdate python3-apport python3-problem-report
22 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
8 not fully installed or removed.
Need to get 55.6 MB/57.2 MB of archives.
After this operation, 201 MB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://dl.google.com/linux/chrome/deb/ stable/main google-chrome-stable amd64 46.0.2490.80-1 [47.3 MB]
Get:2 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main ntpdate amd64 1:4.2.6.p5+dfsg-3ubuntu2.14.04.5 [57.0 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main mysql-common all 5.5.46-0ubuntu0.14.04.2 [14.1 kB]
Get:4 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main libmysqlclient18 amd64 5.5.46-0ubuntu0.14.04.2 [597 kB]
Get:5 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main mysql-server all 5.5.46-0ubuntu0.14.04.2 [12.4 kB]
Get:6 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main mysql-server-5.5 amd64 5.5.46-0ubuntu0.14.04.2 [1,981 kB]
Get:7 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main mysql-client-core-5.5 amd64 5.5.46-0ubuntu0.14.04.2 [706 kB]
Get:8 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main mysql-client-5.5 amd64 5.5.46-0ubuntu0.14.04.2 [1,461 kB]
Get:9 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main mysql-server-core-5.5 amd64 5.5.46-0ubuntu0.14.04.2 [3,223 kB]
Get:10 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-problem-report all 2.14.1-0ubuntu3.18 [9,926 B]
Get:11 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-apport all 2.14.1-0ubuntu3.18 [75.2 kB]
Get:12 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main apport all 2.14.1-0ubuntu3.18 [182 kB]
Get:13 http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main apport-gtk all 2.14.1-0ubuntu3.18 [9,548 B]
Fetched 55.6 MB in 2min 55s (317 kB/s)                                         
Preconfiguring packages ...
(Reading database ... 361325 files and directories currently installed.)
Removing linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
depmod: WARNING: could not open /lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-30-generic
grep: /boot/config-3.16.0-30-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_8QgZQM/lib/modules/3.16.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_8QgZQM/lib/modules/3.16.0-30-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-3.16.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.16.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.16.0-30-generic.postrm line 328.
dpkg: error processing package linux-image-3.16.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.16.0-30-generic
 linux-image-3.16.0-30-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)





```

---

### Post by ian-weisser on 2015-10-27
> **Sujay_Kirti said:**
> 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
**/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found**
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-3.16.0-30-generic (--remove):


Please show us lines 1-20 of /usr/sbin/grub-mkconfig.
My version doesn't seem to have the word 'splash' in it.

---

### Post by Sujay_Kirti on 2015-11-02
> **ian-weisser said:**
> Please show us lines 1-20 of /usr/sbin/grub-mkconfig.
My version doesn't seem to have the word 'splash' in it.

Output:

```
11: /etc/default/grub: splash: not found
```

I remember how "splash" came in the game.

First of all here's output of **sudo gedit /etc/default/grub**

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet **splash** pcie_aspm=force
GRUB_CMDLINE_LINUX=""

```

Now, today I suddenly remember that I did some changes to **/etc/default/grub **in attempt to disable the dGPU.

What can be done now ?

---

### Post by ian-weisser on 2015-11-02
Since grub-mkconfig has a problem with that word...remove it.
Then try again.

---

### Post by Sujay_Kirti on 2015-11-02
Now the errors seem to be gone.

I did a apt-update/upgrade, and everything went swiftly !

Thanks a ton for your help @ian-weisser , really appreciate it :) .

---

### Post by ian-weisser on 2015-11-02
Very pleased you seem to have it fixed!

---

