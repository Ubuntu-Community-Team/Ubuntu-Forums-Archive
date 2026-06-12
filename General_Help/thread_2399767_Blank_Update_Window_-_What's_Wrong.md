---
title: "Blank Update Window - What's Wrong?"
date: 2018-08-29
forum: General Help
---

### Post by AngelOfNorath on 2018-08-29
Hello,


For a month at least, my Ubuntu 16.04 Update Manager shows an update window. The difference between this one and the previous is that this one is completely blank and I don't know if I should install the updates. Here how it looks:

[ATTACH=CONFIG]280890[/ATTACH]

---

### Post by Impavidus on 2018-08-29
Seems to be a known issue. See these threads:
[https://ubuntuforums.org/showthread.php?t=2396226](https://ubuntuforums.org/showthread.php?t=2396226)
[https://ubuntuforums.org/showthread.php?t=2394240](https://ubuntuforums.org/showthread.php?t=2394240)
And also this bug report:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1783023](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1783023)

For the time being, you can use the terminal to autoremove old kernels:```
sudo apt-get autoremove --purge
```

---

### Post by Holger_Gehrke on 2018-08-29
Seems to be a bug in the Updater as reported in [this thread]("https://ubuntuforums.org/showthread.php?t=2394240").The current work-around seems to be to run 'apt list --upgradeable' in a terminal and do 'sudo apt dist-upgrade' after checking the list of upgrades. Looks like the bug is related to having packages installed that can be automatically removed, so 'sudo apt autoremove' probably gets the Updater back to working until the next kernel update (which will make an old kernel autoremove-able ...

Holger

---

### Post by AngelOfNorath on 2018-08-29
At first, thank you both for your answers.

So to get it right, tell me if this steps are right:

1.
```
apt list --upgradeable
```

2. 
```
[COLOR=#000000]sudo apt dist-upgrade[/COLOR]
```

3. 
```
[COLOR=#000000][FONT=&amp]sudo apt-get autoremove --purge[/FONT][/COLOR]
```

Is this the right hierarchy of the commands? 

Also from the threads you both send I saw that the output of ***sudo apt update*** helps. So I will put it here to see if it leads anywhere.

```
Hit:1 http://ppa.launchpad.net/rvm/smplayer/ubuntu xenial InReleaseHit:2 http://packages.microsoft.com/repos/vscode stable InRelease              
Ign:3 http://linux.dropbox.com/ubuntu wily InRelease                           
Hit:4 http://ppa.launchpad.net/stefansundin/truecrypt/ubuntu xenial InRelease  
Get:5 http://linux.dropbox.com/ubuntu wily Release [6596 B]                    
Hit:7 http://repo.steampowered.com/steam precise InRelease                     
Hit:8 https://deb.opera.com/opera-stable stable InRelease
Hit:9 https://apt-mo.trafficmanager.net//repos/dotnet-release xenial InRelease
Hit:10 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease
Hit:11 http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu xenial InRelease
Hit:12 http://gr.archive.ubuntu.com/ubuntu xenial InRelease                    
Get:13 http://security.ubuntu.com/ubuntu xenial-security InRelease [107 kB]    
Ign:14 http://dl.google.com/linux/chrome/deb stable InRelease                  
Get:15 http://gr.archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]   
Get:16 http://dl.google.com/linux/chrome/deb stable Release [1189 B]           
Hit:17 http://gr.archive.ubuntu.com/ubuntu xenial-backports InRelease    
Get:18 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [549 kB]
Get:19 http://dl.google.com/linux/chrome/deb stable Release.gpg [819 B]        
Get:20 http://gr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [840 kB]
Hit:21 https://repo.skype.com/deb stable InRelease                             
Get:22 http://dl.google.com/linux/chrome/deb stable/main amd64 Packages [1391 B]
Hit:23 https://packages.microsoft.com/ubuntu/16.04/prod xenial InRelease       
Get:24 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages [476 kB]
Hit:25 https://download.mono-project.com/repo/ubuntu stable-xenial InRelease   
Get:26 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [368 kB]
Get:27 http://gr.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [757 kB]
Get:28 http://gr.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [681 kB]
Get:29 http://gr.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [622 kB]
Fetched 4518 kB in 9s (502 kB/s)                                               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
250 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

---

### Post by Impavidus on 2018-08-30
```
apt list --upgradable
```lists the packages that can be upgraded, just for your information. I never use it. I just run apt upgrade, which shows the list that will be upgraded again and offers an opportunity to abort. So that command is optional.

```
sudo apt dist-upgrade
```will install all upgrades, even if that means removing something (which is rarely the case). It should first tell you what it's going to do and give you an opportunity to abort, if something seems to go wrong.```
sudo apt upgrade
```is a somewhat more cautious version of that command.

```
sudo apt autoremove --purge
```removes old stuff, like old kernels that have been replaced by a new one installed using the apt upgrade command. You can run that command whenever you like, but I like to keep my system clean, so after a kernel upgrade, I immediately reboot and run autoremove.

You have quite a diverse collection of repositories. This may destabilise your system, but I see no immediate problem. Just to tell you where to look if problems occur. I also see you have 250 upgrades available, which is a lot. The bug report mentions that this blank window problem happens when there are only phased upgrades and autoremovable packages, but I doubt all these upgrades are phased. Many must be old. I suggest you install them.

---

### Post by AngelOfNorath on 2018-08-30
Ok I run the last command, you said. I thought it was the more suitable for my situation. Here is the output:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dotnet-runtime-deps-2.1.0-rc1* libenca0* libguess1* libllvm4.0*
  libsdl2-2.0-0* libsndio6.1* libxaw3dxft6* linux-headers-4.13.0-43*
  linux-headers-4.13.0-43-generic* linux-headers-4.13.0-45*
  linux-headers-4.13.0-45-generic* linux-headers-4.15.0-24*
  linux-headers-4.15.0-24-generic* linux-headers-4.15.0-29*
  linux-headers-4.15.0-29-generic* linux-headers-4.15.0-30*
  linux-headers-4.15.0-30-generic* linux-image-4.13.0-43-generic*
  linux-image-4.13.0-45-generic* linux-image-4.15.0-24-generic*
  linux-image-4.15.0-29-generic* linux-image-4.15.0-30-generic*
  linux-image-extra-4.13.0-43-generic* linux-image-extra-4.13.0-45-generic*
  linux-modules-4.15.0-24-generic* linux-modules-4.15.0-29-generic*
  linux-modules-4.15.0-30-generic* linux-modules-extra-4.15.0-24-generic*
  rtmpdump* youtube-dl*
0 upgraded, 0 newly installed, 30 to remove and 247 not upgraded.
After this operation, 1365 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 442828 files and directories currently installed.)
Removing dotnet-runtime-deps-2.1.0-rc1 (2.1.0-rc1-1) ...
Removing libenca0:amd64 (1.18-1) ...
Removing libguess1:amd64 (1.2-1.1) ...
Removing libllvm4.0:amd64 (1:4.0-1ubuntu1~16.04.2) ...
Removing libsdl2-2.0-0:amd64 (2.0.4+dfsg1-2ubuntu2) ...
Removing libsndio6.1:amd64 (1.1.0-2) ...
Removing libxaw3dxft6 (2.9.1.4-3.1) ...
Purging configuration files for libxaw3dxft6 (2.9.1.4-3.1) ...
Removing linux-headers-4.13.0-43-generic (4.13.0-43.48~16.04.1) ...
Removing linux-headers-4.13.0-43 (4.13.0-43.48~16.04.1) ...
Removing linux-headers-4.13.0-45-generic (4.13.0-45.50~16.04.1) ...
Removing linux-headers-4.13.0-45 (4.13.0-45.50~16.04.1) ...
Removing linux-headers-4.15.0-24-generic (4.15.0-24.26~16.04.1) ...
Removing linux-headers-4.15.0-24 (4.15.0-24.26~16.04.1) ...
Removing linux-headers-4.15.0-29-generic (4.15.0-29.31~16.04.1) ...
Removing linux-headers-4.15.0-29 (4.15.0-29.31~16.04.1) ...
Removing linux-headers-4.15.0-30-generic (4.15.0-30.32~16.04.1) ...
Removing linux-headers-4.15.0-30 (4.15.0-30.32~16.04.1) ...
Removing linux-image-extra-4.13.0-43-generic (4.13.0-43.48~16.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-33-generic
Found initrd image: /boot/initrd.img-4.15.0-33-generic
Found linux image: /boot/vmlinuz-4.15.0-32-generic
Found initrd image: /boot/initrd.img-4.15.0-32-generic
Found linux image: /boot/vmlinuz-4.15.0-30-generic
Found initrd image: /boot/initrd.img-4.15.0-30-generic
Found linux image: /boot/vmlinuz-4.15.0-29-generic
Found initrd image: /boot/initrd.img-4.15.0-29-generic
Found linux image: /boot/vmlinuz-4.15.0-24-generic
Found initrd image: /boot/initrd.img-4.15.0-24-generic
Found linux image: /boot/vmlinuz-4.13.0-45-generic
Found initrd image: /boot/initrd.img-4.13.0-45-generic
Found linux image: /boot/vmlinuz-4.13.0-43-generic
Found initrd image: /boot/initrd.img-4.13.0-43-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 10 (loader) on /dev/sda2
done
Purging configuration files for linux-image-extra-4.13.0-43-generic (4.13.0-43.48~16.04.1) ...
Removing linux-image-4.13.0-43-generic (4.13.0-43.48~16.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
update-initramfs: Deleting /boot/initrd.img-4.13.0-43-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-33-generic
Found initrd image: /boot/initrd.img-4.15.0-33-generic
Found linux image: /boot/vmlinuz-4.15.0-32-generic
Found initrd image: /boot/initrd.img-4.15.0-32-generic
Found linux image: /boot/vmlinuz-4.15.0-30-generic
Found initrd image: /boot/initrd.img-4.15.0-30-generic
Found linux image: /boot/vmlinuz-4.15.0-29-generic
Found initrd image: /boot/initrd.img-4.15.0-29-generic
Found linux image: /boot/vmlinuz-4.15.0-24-generic
Found initrd image: /boot/initrd.img-4.15.0-24-generic
Found linux image: /boot/vmlinuz-4.13.0-45-generic
Found initrd image: /boot/initrd.img-4.13.0-45-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 10 (loader) on /dev/sda2
done
Purging configuration files for linux-image-4.13.0-43-generic (4.13.0-43.48~16.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
dpkg: warning: while removing linux-image-4.13.0-43-generic, directory '/lib/modules/4.13.0-43-generic' not empty so not removed
Removing linux-image-extra-4.13.0-45-generic (4.13.0-45.50~16.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-45-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-33-generic
Found initrd image: /boot/initrd.img-4.15.0-33-generic
Found linux image: /boot/vmlinuz-4.15.0-32-generic
Found initrd image: /boot/initrd.img-4.15.0-32-generic
Found linux image: /boot/vmlinuz-4.15.0-30-generic
Found initrd image: /boot/initrd.img-4.15.0-30-generic
Found linux image: /boot/vmlinuz-4.15.0-29-generic
Found initrd image: /boot/initrd.img-4.15.0-29-generic
Found linux image: /boot/vmlinuz-4.15.0-24-generic
Found initrd image: /boot/initrd.img-4.15.0-24-generic
Found linux image: /boot/vmlinuz-4.13.0-45-generic
Found initrd image: /boot/initrd.img-4.13.0-45-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 10 (loader) on /dev/sda2
done
Purging configuration files for linux-image-extra-4.13.0-45-generic (4.13.0-45.50~16.04.1) ...
Removing linux-image-4.13.0-45-generic (4.13.0-45.50~16.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
update-initramfs: Deleting /boot/initrd.img-4.13.0-45-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-33-generic
Found initrd image: /boot/initrd.img-4.15.0-33-generic
Found linux image: /boot/vmlinuz-4.15.0-32-generic
Found initrd image: /boot/initrd.img-4.15.0-32-generic
Found linux image: /boot/vmlinuz-4.15.0-30-generic
Found initrd image: /boot/initrd.img-4.15.0-30-generic
Found linux image: /boot/vmlinuz-4.15.0-29-generic
Found initrd image: /boot/initrd.img-4.15.0-29-generic
Found linux image: /boot/vmlinuz-4.15.0-24-generic
Found initrd image: /boot/initrd.img-4.15.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 10 (loader) on /dev/sda2
done
Purging configuration files for linux-image-4.13.0-45-generic (4.13.0-45.50~16.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
dpkg: warning: while removing linux-image-4.13.0-45-generic, directory '/lib/modules/4.13.0-45-generic' not empty so not removed
Removing linux-modules-extra-4.15.0-24-generic (4.15.0-24.26~16.04.1) ...
Purging configuration files for linux-modules-extra-4.15.0-24-generic (4.15.0-24.26~16.04.1) ...
Removing linux-image-4.15.0-24-generic (4.15.0-24.26~16.04.1) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.15.0-24-generic
/etc/kernel/postrm.d/zz-update-grub:
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-33-generic
Found initrd image: /boot/initrd.img-4.15.0-33-generic
Found linux image: /boot/vmlinuz-4.15.0-32-generic
Found initrd image: /boot/initrd.img-4.15.0-32-generic
Found linux image: /boot/vmlinuz-4.15.0-30-generic
Found initrd image: /boot/initrd.img-4.15.0-30-generic
Found linux image: /boot/vmlinuz-4.15.0-29-generic
Found initrd image: /boot/initrd.img-4.15.0-29-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 10 (loader) on /dev/sda2
done
Purging configuration files for linux-image-4.15.0-24-generic (4.15.0-24.26~16.04.1) ...
rmdir: failed to remove '/lib/modules/4.15.0-24-generic': Directory not empty
Removing linux-image-4.15.0-29-generic (4.15.0-29.31~16.04.1) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.15.0-29-generic
/etc/kernel/postrm.d/zz-update-grub:
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-33-generic
Found initrd image: /boot/initrd.img-4.15.0-33-generic
Found linux image: /boot/vmlinuz-4.15.0-32-generic
Found initrd image: /boot/initrd.img-4.15.0-32-generic
Found linux image: /boot/vmlinuz-4.15.0-30-generic
Found initrd image: /boot/initrd.img-4.15.0-30-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 10 (loader) on /dev/sda2
done
Purging configuration files for linux-image-4.15.0-29-generic (4.15.0-29.31~16.04.1) ...
rmdir: failed to remove '/lib/modules/4.15.0-29-generic': Directory not empty
Removing linux-image-4.15.0-30-generic (4.15.0-30.32~16.04.1) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.15.0-30-generic
/etc/kernel/postrm.d/zz-update-grub:
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-33-generic
Found initrd image: /boot/initrd.img-4.15.0-33-generic
Found linux image: /boot/vmlinuz-4.15.0-32-generic
Found initrd image: /boot/initrd.img-4.15.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 10 (loader) on /dev/sda2
done
Purging configuration files for linux-image-4.15.0-30-generic (4.15.0-30.32~16.04.1) ...
rmdir: failed to remove '/lib/modules/4.15.0-30-generic': Directory not empty
Removing linux-modules-4.15.0-24-generic (4.15.0-24.26~16.04.1) ...
Purging configuration files for linux-modules-4.15.0-24-generic (4.15.0-24.26~16.04.1) ...
dpkg: warning: while removing linux-modules-4.15.0-24-generic, directory '/lib/modules/4.15.0-24-generic' not empty so not removed
Removing linux-modules-4.15.0-29-generic (4.15.0-29.31~16.04.1) ...
Purging configuration files for linux-modules-4.15.0-29-generic (4.15.0-29.31~16.04.1) ...
dpkg: warning: while removing linux-modules-4.15.0-29-generic, directory '/lib/modules/4.15.0-29-generic' not empty so not removed
Removing linux-modules-4.15.0-30-generic (4.15.0-30.32~16.04.1) ...
Purging configuration files for linux-modules-4.15.0-30-generic (4.15.0-30.32~16.04.1) ...
dpkg: warning: while removing linux-modules-4.15.0-30-generic, directory '/lib/modules/4.15.0-30-generic' not empty so not removed
Removing rtmpdump (2.4+20151223.gitfa8646d-1ubuntu0.1) ...
Removing youtube-dl (1:2018.04.03-1~webupd8~xenial0) ...
Purging configuration files for youtube-dl (1:2018.04.03-1~webupd8~xenial0) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for man-db (2.7.5-1) ...



```

---

