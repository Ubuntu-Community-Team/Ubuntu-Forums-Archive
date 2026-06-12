---
title: "Not enough disk space with applying software updates"
date: 2016-01-06
forum: General Help
---

### Post by carmen2012 on 2016-01-06
I am running Ubuntu 14.04 on my PC that has about 500 GIG of free space.

I am being prompted to perform the security updates, but they will not apply as I am getting the message " The upgrade needs a total of 83.6 M free space on disk '/boot'. Please free at least an additional 22.9 M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

I have tried running sudo apt-get clean but the issue remains.

Could someone please help me in clearing this message so that I can complete my updates?

Thank you

---

### Post by blm-ubunet on 2016-01-06
Your /boot partition contains grub/efi stuff & kernel images.
This can get filled up if the old kernel packages are not removed (the images are built from the packages).
Old kernels are meant to get removed automatically..

```
sudo apt-get autoremove
sudo apt-get autoclean
```
Should get your /boot space back & clean out the old package local cache.

Then
```
sudo apt-get update
sudo apt-get dist-upgrade
``` (latest point release in 14.04LTS)

This will likely update the kernel & so after a reboot & all is stable, you could remove another old kernel..

---

### Post by ian-weisser on 2016-01-06
This is a bug: [LP #1357093]("https://bugs.launchpad.net/bugs/1357093"). A fix has been proposed, and is awaiting the next release of unattended-upgrades.

blm-ubunet's suggestions may sometimes fail (or merely won't help) due to the 'disk full' condition AND the separate /boot partition.

How to fix it:
Use dpkg to remove one old kernel  (occasionally two kernels), freeing enough space for the queued apt  install to complete, then autoremove can run and happily remove all the  rest of the old kernels.
See  [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels)  for an example of how to do it safely.

How to prevent the problem after it's fixed:
Run 'apt-get autoremove' regularly. Every two  weeks, every day, whenever...but regularly. Or enable the unattended upgrades setting  to run autoremove daily for you. Autoremove will keep /boot from filling (its really good at that!), but you must run it *before* the disk is full.

---

### Post by carmen2012 on 2016-01-06
Thank you, I'm going to try both of these suggestions when I'm back in front of my PC tomorrow.

I don't suppose there is a way to just automate this.  I'm quite green when it comes to terminal commands and while they are copy/paste, I'd hate to make a mistake and remove the wrong file, rendering my system unusable.

---

### Post by ian-weisser on 2016-01-06
> **carmen2012 said:**
> I don't suppose there is a way to just automate this.
Your wish is granted.

There is indeed a way to automate prevention of recurrence...once you have manually fixed the space issue. See [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Automatic_Maintenance](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Automatic_Maintenance) for instructions. It does, unfortunately, require just a little terminal.

When your system gets the bugfix to [LP #1357093]("https://bugs.launchpad.net/bugs/1357093"), then you won't even need to do that, It will be totally automatic, and done by default.

---

### Post by carmen2012 on 2016-01-07
I got a little lucky in that I was able to use @blm-ubunet instructions above to complete the update....phew

I had two quick questions:

1. @ian-weisser, you mentioned that a bug fix is going to get pushed down to Ubuntu in LP #1357093.  Unless I missed it, I didn't see a date listed, would you know when it will be available?

2.  On one of the links, it said the below.  If I am understanding this correctly, does this mean that if I run the below command, I won't run into this issue again?

Manual Maintenance
If your system is operating without error, you should be able to remove old kernels with a simple autoremove command, available using Synaptic or the shell:


sudo apt-get autoremove
The system keeps track of which kernels are older and marks them eligible for removal using this method. Most users should run autoremove every few months or so. Systems with a separate /boot partition should run autoremove every two-four weeks. Mark your calendar, make it a routine. Autoremove can be run as often as you like - running it more often will not harm your system. The automated method below runs autoremove every day.

---

### Post by ian-weisser on 2016-01-07
The date is whenever the upstream developers decide the date will be. This is an annoying bug, but not critical.

Yes, until the bugfix reaches you, you must do regular maintenance to prevent recurrence. That wiki page show two ways of doing that regular maintenance.

---

### Post by carmen2012 on 2016-01-22
This has been a bit disappointing.  I was able to complete the last security update about a week ago and then ran sudo apt-get autoremove daily as it only takes a second.

I was prompted yesterday for another update but it failed with the message in the original post.  I then ran through the instructions on this url [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels) but I obviously did something wrong.

Now the updates fail, I get a critical error with a request to send information and I get another prompt "low disk space - The volume boot has only 0 bytes disk space remaining."

For someone not technically inclined, it is really important that this bug gets fixed, but I also need help in completing the update.  Hopefully I don't need to reinstall the OS?

---

### Post by ian-weisser on 2016-01-22
Yes, everyone agrees that bugs that bite us should be fixed.
Let's find out if your current problem is related to the bug or merely presents a similar set of symptoms.

Please run the following commands and show us the complete output of each:
```
uname -r
df
df -i
ls -l /boot
sudo apt update
sudo apt upgrade
```

---

### Post by carmen2012 on 2016-01-22
> **ian-weisser said:**
> Yes, everyone agrees that bugs that bite us should be fixed.
Let's find out if your current problem is related to the bug or merely presents a similar set of symptoms.

Please run the following commands and show us the complete output of each:
```
uname -r
df
df -i
ls -l /boot
sudo apt update
sudo apt upgrade
```

@ian-weisser - Thank you for helping me with this issue.  I do enjoy your analogy, this bug does bite hard (at least for me).

Below is the output of the commands that you requested.  In hindsight, I probably should have run them one at a time and put them in separate quotes (sorry).  I should just give you a heads up that I will be away for the weekend.  I'll be able to read your comments, but will try any suggestions that you offer on Monday.  Thank you again for your time.

```
administrator@M91:~$ uname -r3.13.0-76-generic
administrator@M91:~$ df
Filesystem                  1K-blocks     Used Available Use% Mounted on
udev                          1918888        4   1918884   1% /dev
tmpfs                          387008     1104    385904   1% /run
/dev/mapper/ubuntu--vg-root 476341280 12266324 439855104   3% /
none                                4        0         4   0% /sys/fs/cgroup
none                             5120        0      5120   0% /run/lock
none                          1935040    18988   1916052   1% /run/shm
none                           102400       40    102360   1% /run/user
/dev/sda1                      240972   232365         0 100% /boot
administrator@M91:~$ df -i
Filesystem                    Inodes  IUsed    IFree IUse% Mounted on
udev                          479722    529   479193    1% /dev
tmpfs                         483760    540   483220    1% /run
/dev/mapper/ubuntu--vg-root 30261248 635747 29625501    3% /
none                          483760      2   483758    1% /sys/fs/cgroup
none                          483760      2   483758    1% /run/lock
none                          483760     40   483720    1% /run/shm
none                          483760     26   483734    1% /run/user
/dev/sda1                      62248    327    61921    1% /boot
administrator@M91:~$ ls -l /boot
total 223474
-rw-r--r-- 1 root root  1164723 Apr 10  2015 abi-3.13.0-49-generic
-rw-r--r-- 1 root root  1164671 May 20  2015 abi-3.13.0-53-generic
-rw-r--r-- 1 root root  1165260 Oct 23 07:39 abi-3.13.0-67-generic
-rw-r--r-- 1 root root  1165260 Nov  6 11:57 abi-3.13.0-68-generic
-rw-r--r-- 1 root root  1165334 Dec 17 16:42 abi-3.13.0-74-generic
-rw-r--r-- 1 root root  1165334 Jan 18 10:16 abi-3.13.0-76-generic
-rw-r--r-- 1 root root   165773 Apr 10  2015 config-3.13.0-49-generic
-rw-r--r-- 1 root root   165762 May 20  2015 config-3.13.0-53-generic
-rw-r--r-- 1 root root   165763 Oct 23 07:39 config-3.13.0-67-generic
-rw-r--r-- 1 root root   165763 Nov  6 11:57 config-3.13.0-68-generic
-rw-r--r-- 1 root root   165763 Dec 17 16:42 config-3.13.0-74-generic
-rw-r--r-- 1 root root   165763 Jan 18 10:16 config-3.13.0-76-generic
drwxr-xr-x 5 root root     1024 Jan 22 11:52 grub
-rw-r--r-- 1 root root 13018160 Jan 22 11:51 initrd.img-3.13.0-49-generic
-rw-r--r-- 1 root root 30207997 Nov  6 11:02 initrd.img-3.13.0-53-generic
-rw-r--r-- 1 root root 30212091 Nov  6 11:17 initrd.img-3.13.0-67-generic
-rw-r--r-- 1 root root 30217711 Nov 27 09:45 initrd.img-3.13.0-68-generic
-rw-r--r-- 1 root root 30211408 Jan 14 08:13 initrd.img-3.13.0-74-generic
-rw-r--r-- 1 root root 30213167 Jan 22 11:52 initrd.img-3.13.0-76-generic
drwx------ 2 root root    12288 Aug 15  2014 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3389437 Apr 10  2015 System.map-3.13.0-49-generic
-rw------- 1 root root  3390132 May 20  2015 System.map-3.13.0-53-generic
-rw------- 1 root root  3392383 Oct 23 07:39 System.map-3.13.0-67-generic
-rw------- 1 root root  3392383 Nov  6 11:57 System.map-3.13.0-68-generic
-rw------- 1 root root  3392888 Dec 17 16:42 System.map-3.13.0-74-generic
-rw------- 1 root root  3392888 Jan 18 10:16 System.map-3.13.0-76-generic
-rw------- 1 root root  5815392 Apr 10  2015 vmlinuz-3.13.0-49-generic
-rw------- 1 root root  5821152 May 20  2015 vmlinuz-3.13.0-53-generic
-rw------- 1 root root  5822368 Oct 23 07:39 vmlinuz-3.13.0-67-generic
-rw------- 1 root root  5822400 Nov  6 11:57 vmlinuz-3.13.0-68-generic
-rw------- 1 root root  5825376 Dec 17 16:42 vmlinuz-3.13.0-74-generic
-rw------- 1 root root  5825088 Jan 18 10:16 vmlinuz-3.13.0-76-generic
administrator@M91:~$ sudo apt update
[sudo] password for administrator: 
Ign http://dl.google.com stable InRelease                                      
Ign http://dl.google.com stable InRelease                                      
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release.gpg                                    
Ign http://ca.archive.ubuntu.com trusty InRelease                              
Hit http://dl.google.com stable Release                                        
Get:1 http://ca.archive.ubuntu.com trusty-updates InRelease [64.4 kB]          
Hit http://ca.archive.ubuntu.com trusty-backports InRelease                    
Get:2 http://ca.archive.ubuntu.com trusty Release.gpg [933 B]                  
Get:3 http://ca.archive.ubuntu.com trusty-updates/main Sources [248 kB]        
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://dl.google.com stable/main amd64 Packages                            
Get:4 http://security.ubuntu.com trusty-security InRelease [64.4 kB]           
Hit http://dl.google.com stable/main i386 Packages                             
Get:5 http://ca.archive.ubuntu.com trusty-updates/restricted Sources [5,359 B] 
Get:6 http://security.ubuntu.com trusty-security/main Sources [103 kB]         
Get:7 http://ca.archive.ubuntu.com trusty-updates/universe Sources [147 kB]    
Get:8 http://security.ubuntu.com trusty-security/restricted Sources [4,035 B]  
Get:9 http://security.ubuntu.com trusty-security/universe Sources [32.7 kB]    
Get:10 http://ca.archive.ubuntu.com trusty-updates/multiverse Sources [5,161 B]
Get:11 http://security.ubuntu.com trusty-security/multiverse Sources [2,357 B] 
Get:12 http://security.ubuntu.com trusty-security/main amd64 Packages [410 kB] 
Get:13 http://ca.archive.ubuntu.com trusty-updates/main amd64 Packages [689 kB]
Ign http://dl.google.com stable/main Translation-en_CA                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_CA                         
Ign http://dl.google.com stable/main Translation-en                            
Get:14 http://ca.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Get:15 http://ca.archive.ubuntu.com trusty-updates/universe amd64 Packages [334 kB]
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty Release                         
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Get:16 http://security.ubuntu.com trusty-security/restricted amd64 Packages [13.0 kB]
Get:17 http://security.ubuntu.com trusty-security/universe amd64 Packages [123 kB]
Get:18 http://ca.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.0 kB]
Get:19 http://ca.archive.ubuntu.com trusty-updates/main i386 Packages [664 kB] 
Ign http://extras.ubuntu.com trusty/main Translation-en_CA                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:20 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [4,798 B]
Get:21 http://security.ubuntu.com trusty-security/main i386 Packages [384 kB]  
Get:22 http://ca.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:23 http://ca.archive.ubuntu.com trusty-updates/universe i386 Packages [335 kB]
Get:24 http://ca.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.1 kB]
Get:25 http://ca.archive.ubuntu.com trusty-updates/main Translation-en [348 kB]
Get:26 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.7 kB]
Get:27 http://security.ubuntu.com trusty-security/universe i386 Packages [123 kB]
Get:28 http://ca.archive.ubuntu.com trusty-updates/multiverse Translation-en [6,832 B]
Get:29 http://security.ubuntu.com trusty-security/multiverse i386 Packages [4,955 B]
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Get:30 http://ca.archive.ubuntu.com trusty-updates/restricted Translation-en [3,699 B]
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Get:31 http://ca.archive.ubuntu.com trusty-updates/universe Translation-en [175 kB]
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://ca.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://ca.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://ca.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://ca.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://ca.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://ca.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://ca.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://ca.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://ca.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://ca.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://ca.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://ca.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://ca.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://ca.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://ca.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://ca.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://ca.archive.ubuntu.com trusty Release                                
Hit http://ca.archive.ubuntu.com trusty/main Sources                           
Hit http://ca.archive.ubuntu.com trusty/restricted Sources                     
Hit http://ca.archive.ubuntu.com trusty/universe Sources                       
Hit http://ca.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://ca.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://ca.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://ca.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://ca.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://ca.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://ca.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://ca.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://ca.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://ca.archive.ubuntu.com trusty/main Translation-en_CA                 
Hit http://ca.archive.ubuntu.com trusty/main Translation-en                    
Hit http://ca.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://ca.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://ca.archive.ubuntu.com trusty/universe Translation-en_CA             
Hit http://ca.archive.ubuntu.com trusty/universe Translation-en                
Ign http://ca.archive.ubuntu.com trusty/multiverse Translation-en_CA           
Ign http://ca.archive.ubuntu.com trusty/restricted Translation-en_CA           
Fetched 4,367 kB in 49s (87.4 kB/s)                                            
Reading package lists... Done
administrator@M91:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  google-chrome-stable libegl1-mesa libegl1-mesa-drivers libgbm1
  libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libgles2-mesa libopenvg1-mesa
  libwayland-egl1-mesa libxatracker2 linux-firmware os-prober rsync
14 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 80.2 MB of archives.
After this operation, 3,965 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-firmware all 1.127.20 [24.5 MB]
Get:2 http://dl.google.com/linux/chrome/deb/ stable/main google-chrome-stable amd64 48.0.2564.82-1 [48.2 MB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main libgl1-mesa-dri amd64 10.1.3-0ubuntu0.6 [4,823 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main libgbm1 amd64 10.1.3-0ubuntu0.6 [19.0 kB]
Get:5 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main libgl1-mesa-glx amd64 10.1.3-0ubuntu0.6 [113 kB]
Get:6 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main libgles2-mesa amd64 10.1.3-0ubuntu0.6 [12.6 kB]
Get:7 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main libwayland-egl1-mesa amd64 10.1.3-0ubuntu0.6 [6,484 B]
Get:8 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main libegl1-mesa-drivers amd64 10.1.3-0ubuntu0.6 [1,993 kB]
Get:9 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main libglapi-mesa amd64 10.1.3-0ubuntu0.6 [21.0 kB]
Get:10 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main libopenvg1-mesa amd64 10.1.3-0ubuntu0.6 [12.9 kB]
Get:11 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main libegl1-mesa amd64 10.1.3-0ubuntu0.6 [59.1 kB]
Get:12 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main libxatracker2 amd64 10.1.3-0ubuntu0.6 [143 kB]
Get:13 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main rsync amd64 3.1.0-2ubuntu0.2 [284 kB]
Get:14 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main os-prober amd64 1.63ubuntu1.1 [18.0 kB]
Fetched 80.2 MB in 6min 13s (215 kB/s)                                         
(Reading database ... 603112 files and directories currently installed.)
Preparing to unpack .../linux-firmware_1.127.20_all.deb ...
Unpacking linux-firmware (1.127.20) over (1.127.19) ...
Preparing to unpack .../google-chrome-stable_48.0.2564.82-1_amd64.deb ...
Unpacking google-chrome-stable (48.0.2564.82-1) over (47.0.2526.111-1) ...
Preparing to unpack .../libgl1-mesa-dri_10.1.3-0ubuntu0.6_amd64.deb ...
Unpacking libgl1-mesa-dri:amd64 (10.1.3-0ubuntu0.6) over (10.1.3-0ubuntu0.5) ...
Preparing to unpack .../libgbm1_10.1.3-0ubuntu0.6_amd64.deb ...
Unpacking libgbm1:amd64 (10.1.3-0ubuntu0.6) over (10.1.3-0ubuntu0.5) ...
Preparing to unpack .../libgl1-mesa-glx_10.1.3-0ubuntu0.6_amd64.deb ...
Unpacking libgl1-mesa-glx:amd64 (10.1.3-0ubuntu0.6) over (10.1.3-0ubuntu0.5) ...
Preparing to unpack .../libgles2-mesa_10.1.3-0ubuntu0.6_amd64.deb ...
Unpacking libgles2-mesa:amd64 (10.1.3-0ubuntu0.6) over (10.1.3-0ubuntu0.5) ...
Preparing to unpack .../libwayland-egl1-mesa_10.1.3-0ubuntu0.6_amd64.deb ...
Unpacking libwayland-egl1-mesa:amd64 (10.1.3-0ubuntu0.6) over (10.1.3-0ubuntu0.5) ...
Preparing to unpack .../libegl1-mesa-drivers_10.1.3-0ubuntu0.6_amd64.deb ...
Unpacking libegl1-mesa-drivers:amd64 (10.1.3-0ubuntu0.6) over (10.1.3-0ubuntu0.5) ...
Preparing to unpack .../libglapi-mesa_10.1.3-0ubuntu0.6_amd64.deb ...
Unpacking libglapi-mesa:amd64 (10.1.3-0ubuntu0.6) over (10.1.3-0ubuntu0.5) ...
Preparing to unpack .../libopenvg1-mesa_10.1.3-0ubuntu0.6_amd64.deb ...
Unpacking libopenvg1-mesa:amd64 (10.1.3-0ubuntu0.6) over (10.1.3-0ubuntu0.5) ...
Preparing to unpack .../libegl1-mesa_10.1.3-0ubuntu0.6_amd64.deb ...
Unpacking libegl1-mesa:amd64 (10.1.3-0ubuntu0.6) over (10.1.3-0ubuntu0.5) ...
Preparing to unpack .../libxatracker2_10.1.3-0ubuntu0.6_amd64.deb ...
Unpacking libxatracker2:amd64 (10.1.3-0ubuntu0.6) over (10.1.3-0ubuntu0.5) ...
Preparing to unpack .../rsync_3.1.0-2ubuntu0.2_amd64.deb ...
Unpacking rsync (3.1.0-2ubuntu0.2) over (3.1.0-2ubuntu0.1) ...
Preparing to unpack .../os-prober_1.63ubuntu1.1_amd64.deb ...
Unpacking os-prober (1.63ubuntu1.1) over (1.63ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Setting up linux-image-extra-3.13.0-76-generic (3.13.0-76.120) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-76-generic /boot/vmlinuz-3.13.0-76-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-76-generic /boot/vmlinuz-3.13.0-76-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-76-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-76-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-76-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-firmware (1.127.20) ...
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-3.13.0-76-generic; however:
  Package linux-image-extra-3.13.0-76-generic is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.76.82); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Setting up google-chrome-stable (48.0.2564.82-1) ...
Setting up libgl1-mesa-dri:amd64 (10.1.3-0ubuntu0.6) ...
Setting up libgbm1:amd64 (10.1.3-0ubuntu0.6) ...
Setting up libglapi-mesa:amd64 (10.1.3-0ubuntu0.6) ...
Setting up libgl1-mesa-glx:amd64 (10.1.3-0ubuntu0.6) ...
Setting up libgles2-mesa:amd64 (10.1.3-0ubuntu0.6) ...
Setting up libegl1-mesa:amd64 (10.1.3-0ubuntu0.6) ...
Setting up libwayland-egl1-mesa:amd64 (10.1.3-0ubuntu0.6) ...
Setting up libopenvg1-mesa:amd64 (10.1.3-0ubuntu0.6) ...
Setting up libegl1-mesa-drivers:amd64 (10.1.3-0ubuntu0.6) ...
Setting up libxatracker2:amd64 (10.1.3-0ubuntu0.6) ...
Setting up rsync (3.1.0-2ubuntu0.2) ...
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match rsync Default-Stop values (none)
 System start/stop links for /etc/init.d/rsync already exist.
Setting up os-prober (1.63ubuntu1.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Errors were encountered while processing:
 linux-image-extra-3.13.0-76-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
administrator@M91:~$ 



```

---

### Post by blm-ubunet on 2016-01-22
You haven't removed any old kernels.
Problem still is you have too many old kernels installed for the size of your /boot partition.

IMO the easiest soln is to use synaptic package manager:- (may have to install first)
- sort installed packages by size
- select old kernels & mark for complete removal
- "Apply"
just do one or two at once to get the feel for it..

Could just use synaptic for managing all updates.. cos you need to use something to get rid of old kernels!

---

### Post by ian-weisser on 2016-01-22
> **carmen2012 said:**
>  I then ran through the instructions on this url [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels) but I obviously did something wrong.

Why don't you simply run through the instructions again? This time show us the output of your complete session.
"I [...] did something wong" doesn't help either of us. We can help you discover where it went wrong, and make it right.

---

### Post by carmen2012 on 2016-01-25
I took a sledgehammer to my Ubuntu install and decided to reinstall the entire OS.  It only took about 1.5 hours because I use a very basic install with few additional apps.

Hopefully this issue will be fixed with the next LTS which I hope to use in a couple of months.

---

### Post by ian-weisser on 2016-01-25
Reminder: A trivially simple workaround that will permanently prevent this bug from ever biting you again is *already installed* on every release of Ubuntu. Simply turn it on.

---

### Post by carmen2012 on 2016-01-26
> **ian-weisser said:**
> Reminder: A trivially simple workaround that will permanently prevent this bug from ever biting you again is *already installed* on every release of Ubuntu. Simply turn it on.

Thanks for the friendly reminder.  I believe you are referring to the instructions at the bottom of this message.

Rather than modify files, I think I'm going to get into the habit of running sudo apt-get autoremove daily so that I can keep my system files in pristine format.  I've got a friendly reminder to run it.

If the issue gets fixed in the next LTS, that would be great, but if not, the reimage is quick.


[h=2]Automatic Maintenance[/h][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]The unattended-upgrades package, included with the default install of all Ubuntu flavors, includes a setting to run autoremove automatically. Enabling this setting is a two-step process.[/FONT][/COLOR]

---

