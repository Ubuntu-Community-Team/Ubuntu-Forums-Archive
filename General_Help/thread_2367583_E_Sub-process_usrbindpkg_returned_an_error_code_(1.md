---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2017-08-01
forum: General Help
---

### Post by ljubinski on 2017-08-01
(there has been an old thread with this title, yet its been closed and i am not able to extract the solution for me, so - i have the same problem here)
  E: Sub-process /usr/bin/dpkg returned an error code (1)

   in a first attempt to copy the procedure of the old thread i tried this command :
 **sudo dpkg --configure -a**

  it returned this_:  
```

Setting up linux-image-4.4.0-72-generic (4.4.0-72.93) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-72-generic

gzip: stdout: No space left on device
E: mkinitramfs failure find 141 cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-72-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-72-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-72-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-4.4.0-87 (4.4.0-87.110) ...
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-83-generic:
 linux-image-extra-4.4.0-83-generic depends on linux-image-4.4.0-83-generic; however:
  Package linux-image-4.4.0-83-generic is not installed.

dpkg: error processing package linux-image-extra-4.4.0-83-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-72-generic:
 linux-image-extra-4.4.0-72-generic depends on linux-image-4.4.0-72-generic; however:
  Package linux-image-4.4.0-72-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-72-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-4.4.0-66-generic (4.4.0-66.87) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-4.4.0-72-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-66-generic

gzip: stdout: No space left on device
E: mkinitramfs failure find 141 cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-66-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-66-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-66-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-4.4.0-78 (4.4.0-78.99) ...
Setting up linux-headers-4.4.0-78-generic (4.4.0-78.99) ...
Setting up linux-headers-4.4.0-87-generic (4.4.0-87.110) ...
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-78-generic:
 linux-image-extra-4.4.0-78-generic depends on linux-image-4.4.0-78-generic; however:
  Package linux-image-4.4.0-78-generic is not installed.

dpkg: error processing package linux-image-extra-4.4.0-78-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-4.4.0-75-generic (4.4.0-75.96) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-4.4.0-66-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-75-generic

gzip: stdout: No space left on device
E: mkinitramfs failure find 141 cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-75-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-75-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-75-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-87-generic; however:
  Package linux-image-4.4.0-87-generic is not installed.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-4.4.0-83 (4.4.0-83.106) ...
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-87-generic:
 linux-image-extra-4.4.0-87-generic depends on linux-image-4.4.0-87-generic; however:
  Package linux-image-4.4.0-87-generic is not installed.

dpkg: error processing package linux-image-extra-4.4.0-87-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-generic (4.4.0.87.93) ...
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-75-generic:
 linux-image-extra-4.4.0-75-generic depends on linux-image-4.4.0-75-generic; however:
  Package linux-image-4.4.0-75-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-75-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-66-generic:
 linux-image-extra-4.4.0-66-generic depends on linux-image-4.4.0-66-generic; however:
  Package linux-image-4.4.0-66-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-66-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-4.4.0-83-generic (4.4.0-83.106) ...
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.87.93); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-4.4.0-72-generic
 linux-image-extra-4.4.0-83-generic
 linux-image-extra-4.4.0-72-generic
 linux-image-4.4.0-66-generic
 linux-image-extra-4.4.0-78-generic
 linux-image-4.4.0-75-generic
 linux-image-generic
 linux-image-extra-4.4.0-87-generic
 linux-image-extra-4.4.0-75-generic
 linux-image-extra-4.4.0-66-generic
 linux-generic
```


I also tried
**sudo apt-get install -f**


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  aften fonts-horai-umefont fonts-unfonts-core fonts-wqy-microhei
  gnome-exe-thumbnailer gpac gpac-modules-base icoutils lame
  libboost-regex1.58.0 libfreenect0.5 libgpac4 liblept5 liboggz2 libogmrip1
  libopenjp2-7 libtesseract3 linux-headers-4.4.0-21
  linux-headers-4.4.0-21-generic linux-headers-4.4.0-36
  linux-headers-4.4.0-36-generic linux-headers-4.4.0-38
  linux-headers-4.4.0-38-generic linux-headers-4.4.0-45
  linux-headers-4.4.0-45-generic linux-headers-4.4.0-51
  linux-headers-4.4.0-51-generic linux-headers-4.4.0-57
  linux-headers-4.4.0-57-generic linux-headers-4.4.0-59
  linux-headers-4.4.0-59-generic linux-headers-4.4.0-62
  linux-headers-4.4.0-62-generic linux-headers-4.4.0-66
  linux-headers-4.4.0-66-generic linux-headers-4.4.0-78
  linux-headers-4.4.0-78-generic linux-headers-4.4.0-83
  linux-headers-4.4.0-83-generic linux-image-4.4.0-21-generic
  linux-image-4.4.0-36-generic linux-image-4.4.0-38-generic
  linux-image-4.4.0-45-generic linux-image-4.4.0-51-generic
  linux-image-4.4.0-57-generic linux-image-4.4.0-59-generic
  linux-image-4.4.0-62-generic linux-image-4.4.0-66-generic
  linux-image-4.4.0-78-generic linux-image-4.4.0-83-generic
  linux-image-extra-4.4.0-21-generic linux-image-extra-4.4.0-36-generic
  linux-image-extra-4.4.0-38-generic linux-image-extra-4.4.0-45-generic
  linux-image-extra-4.4.0-51-generic linux-image-extra-4.4.0-57-generic
  linux-image-extra-4.4.0-59-generic linux-image-extra-4.4.0-62-generic
  linux-image-extra-4.4.0-66-generic linux-image-extra-4.4.0-78-generic
  linux-image-extra-4.4.0-83-generic mkvtoolnix odbcinst odbcinst1debian2
  oggz-tools ogmrip-dirac ogmrip-doc ogmrip-oggz ogmrip-plugins p7zip
  tesseract-ocr tesseract-ocr-eng tesseract-ocr-equ tesseract-ocr-osd
  ttf-wqy-microhei unixodbc wine-gecko2.21 wine-mono0.0.8 winetricks
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-4.4.0-78-generic linux-image-4.4.0-83-generic
  linux-image-4.4.0-87-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed:
  linux-image-4.4.0-78-generic linux-image-4.4.0-83-generic
  linux-image-4.4.0-87-generic
0 upgraded, 3 newly installed, 0 to remove and 373 not upgraded.
11 not fully installed or removed.
Need to get 0 B/61,6 MB of archives.
After this operation, 146 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 619711 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-87-generic_4.4.0-87.110_i386.deb ...
Done.
Unpacking linux-image-4.4.0-87-generic (4.4.0-87.110) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-87-generic_4.4.0-87.110_i386.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-87-generic' to '/boot/vmlinuz-4.4.0-87-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Preparing to unpack .../linux-image-4.4.0-78-generic_4.4.0-78.99_i386.deb ...
Done.
Unpacking linux-image-4.4.0-78-generic (4.4.0-78.99) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-78-generic_4.4.0-78.99_i386.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-78-generic' to '/boot/vmlinuz-4.4.0-78-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic
Preparing to unpack .../linux-image-4.4.0-83-generic_4.4.0-83.106_i386.deb ...
Done.
Unpacking linux-image-4.4.0-83-generic (4.4.0-83.106) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-83-generic_4.4.0-83.106_i386.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-83-generic' to '/boot/vmlinuz-4.4.0-83-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-87-generic_4.4.0-87.110_i386.deb
 /var/cache/apt/archives/linux-image-4.4.0-78-generic_4.4.0-78.99_i386.deb
 /var/cache/apt/archives/linux-image-4.4.0-83-generic_4.4.0-83.106_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Edit: i see that "No space left on device" and checkte, that there are 80GB on the File System left

---

### Post by kc1di on 2017-08-01
A Reboot may clear the problem. 
if not try this command in the terminal.```
sudo dpkg --configure -a
```

---

### Post by ljubinski on 2017-08-01
Thanks for the quick response!

i tried both suggestions, however this is the final lines i get when i try the --configure -a code:
```

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-4.4.0-72-generic
 linux-image-extra-4.4.0-83-generic
 linux-image-extra-4.4.0-72-generic
 linux-image-4.4.0-66-generic
 linux-image-extra-4.4.0-78-generic
 linux-image-4.4.0-75-generic
 linux-image-generic
 linux-image-extra-4.4.0-87-generic
 linux-image-extra-4.4.0-75-generic
 linux-image-extra-4.4.0-66-generic
 linux-generic
```

---

### Post by kc1di on 2017-08-01
do a```
sudo apt-get update && sudo apt-get upgrade
```
and try again.

---

### Post by BenginM on 2017-08-01
Hiya ..

```


gzip: stdout: No space left on device


```

seems like the /boot directory or partition is full ..

post the output of:

```

uname -a
 df -h 
ls /boot

```

---

### Post by ljubinski on 2017-08-01
Hello!
you can find a txt. attachement with the results to these codes and the requested ones 

```
apt-cache policy
apt-get update
dpkg --configure -a
apt-get -f install
apt-get upgrade 
```


the answers to the requested code is:

**uname -a**
```
Linux NAME 4.4.0-64-generic #85-Ubuntu SMP Mon Feb 20 11:49:39 UTC 2017 i686 i686 i686 GNU/Linux[/QUOTE]

**df -h**
[QUOTE]Filesystem                    Size  Used Avail Use% Mounted on
udev                          2,0G     0  2,0G   0% /dev
tmpfs                         401M  6,5M  395M   2% /run
/dev/mapper/xubuntu--vg-root  289G  199G   77G  73% /
tmpfs                         2,0G   18M  2,0G   1% /dev/shm
tmpfs                         5,0M  4,0K  5,0M   1% /run/lock
tmpfs                         2,0G     0  2,0G   0% /sys/fs/cgroup
/dev/sda1                     472M  468M     0 100% /boot
tmpfs                         401M   44K  401M   1% /run/user/1000
```

**ls /boot**
```
abi-4.4.0-21-generic         initrd.img-4.4.0-59-generic
abi-4.4.0-36-generic         initrd.img-4.4.0-62-generic
abi-4.4.0-38-generic         initrd.img-4.4.0-64-generic
abi-4.4.0-45-generic         lost+found
abi-4.4.0-51-generic         memtest86+.bin
abi-4.4.0-57-generic         memtest86+.elf
abi-4.4.0-59-generic         memtest86+_multiboot.bin
abi-4.4.0-62-generic         System.map-4.4.0-21-generic
abi-4.4.0-64-generic         System.map-4.4.0-36-generic
abi-4.4.0-66-generic         System.map-4.4.0-38-generic
abi-4.4.0-72-generic         System.map-4.4.0-45-generic
abi-4.4.0-75-generic         System.map-4.4.0-51-generic
config-4.4.0-21-generic      System.map-4.4.0-57-generic
config-4.4.0-36-generic      System.map-4.4.0-59-generic
config-4.4.0-38-generic      System.map-4.4.0-62-generic
config-4.4.0-45-generic      System.map-4.4.0-64-generic
config-4.4.0-51-generic      System.map-4.4.0-66-generic
config-4.4.0-57-generic      System.map-4.4.0-72-generic
config-4.4.0-59-generic      System.map-4.4.0-75-generic
config-4.4.0-62-generic      vmlinuz-4.4.0-21-generic
config-4.4.0-64-generic      vmlinuz-4.4.0-36-generic
config-4.4.0-66-generic      vmlinuz-4.4.0-38-generic
config-4.4.0-72-generic      vmlinuz-4.4.0-45-generic
config-4.4.0-75-generic      vmlinuz-4.4.0-51-generic
grub                         vmlinuz-4.4.0-57-generic
initrd.img-4.4.0-21-generic  vmlinuz-4.4.0-59-generic
initrd.img-4.4.0-36-generic  vmlinuz-4.4.0-62-generic
initrd.img-4.4.0-38-generic  vmlinuz-4.4.0-64-generic
initrd.img-4.4.0-45-generic  vmlinuz-4.4.0-66-generic
initrd.img-4.4.0-51-generic  vmlinuz-4.4.0-72-generic
initrd.img-4.4.0-57-generic  vmlinuz-4.4.0-75-generic

```

   **apt-cache policy**
```
Package files:
 100 /var/lib/dpkg/status
     release a=now
 500 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial/partner i386 Packages
     release v=16.04,o=Canonical,a=xenial,n=xenial,l=Partner archive,c=partner,b=i386
     origin archive.canonical.com
 500 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) xenial/main i386 Packages
     release v=16.04,o=LP-PPA-wine-wine-builds,a=xenial,n=xenial,l=Official Wine builds,c=main,b=i386
     origin ppa.launchpad.net
 500 [http://deb.opera.com/opera](http://deb.opera.com/opera) stable/non-free i386 Packages
     release o=Opera Software ASA,a=stable,n=stable,l=The Opera web browser,c=non-free,b=i386
     origin deb.opera.com
 500 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) xenial/main i386 Packages
     release v=16.04,o=LP-PPA-nilarimogard-webupd8,a=xenial,n=xenial,l=WebUpd8,c=main,b=i386
     origin ppa.launchpad.net
 500 [http://ppa.launchpad.net/forkotov02/ppa/ubuntu](http://ppa.launchpad.net/forkotov02/ppa/ubuntu) xenial/main i386 Packages
     release v=16.04,o=LP-PPA-forkotov02,a=xenial,n=xenial,l=qmmp-releases,c=main,b=i386
     origin ppa.launchpad.net
 500 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages
     release v=0.4,o=Spotify LTD,a=stable,n=stable,l=Spotify Public Repository,c=non-free,b=i386
     origin repository.spotify.com
 500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse i386 Packages
     release v=16.04,o=Ubuntu,a=xenial-security,n=xenial,l=Ubuntu,c=multiverse,b=i386
     origin security.ubuntu.com
 500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe i386 Packages
     release v=16.04,o=Ubuntu,a=xenial-security,n=xenial,l=Ubuntu,c=universe,b=i386
     origin security.ubuntu.com
 500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted i386 Packages
     release v=16.04,o=Ubuntu,a=xenial-security,n=xenial,l=Ubuntu,c=restricted,b=i386
     origin security.ubuntu.com
 500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages
     release v=16.04,o=Ubuntu,a=xenial-security,n=xenial,l=Ubuntu,c=main,b=i386
     origin security.ubuntu.com
 100 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-backports/universe i386 Packages
     release v=16.04,o=Ubuntu,a=xenial-backports,n=xenial,l=Ubuntu,c=universe,b=i386
     origin de.archive.ubuntu.com
 100 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-backports/main i386 Packages
     release v=16.04,o=Ubuntu,a=xenial-backports,n=xenial,l=Ubuntu,c=main,b=i386
     origin de.archive.ubuntu.com
 500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-updates/multiverse i386 Packages
     release v=16.04,o=Ubuntu,a=xenial-updates,n=xenial,l=Ubuntu,c=multiverse,b=i386
     origin de.archive.ubuntu.com
 500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages
     release v=16.04,o=Ubuntu,a=xenial-updates,n=xenial,l=Ubuntu,c=universe,b=i386
     origin de.archive.ubuntu.com
 500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-updates/restricted i386 Packages
     release v=16.04,o=Ubuntu,a=xenial-updates,n=xenial,l=Ubuntu,c=restricted,b=i386
     origin de.archive.ubuntu.com
 500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages
     release v=16.04,o=Ubuntu,a=xenial-updates,n=xenial,l=Ubuntu,c=main,b=i386
     origin de.archive.ubuntu.com
 500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial/multiverse i386 Packages
     release v=16.04,o=Ubuntu,a=xenial,n=xenial,l=Ubuntu,c=multiverse,b=i386
     origin de.archive.ubuntu.com
 500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial/universe i386 Packages
     release v=16.04,o=Ubuntu,a=xenial,n=xenial,l=Ubuntu,c=universe,b=i386
     origin de.archive.ubuntu.com
 500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial/restricted i386 Packages
     release v=16.04,o=Ubuntu,a=xenial,n=xenial,l=Ubuntu,c=restricted,b=i386
     origin de.archive.ubuntu.com
 500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial/main i386 Packages
     release v=16.04,o=Ubuntu,a=xenial,n=xenial,l=Ubuntu,c=main,b=i386
     origin de.archive.ubuntu.com
Pinned packages:
```

__________________________
**apt-get update**
```

W: chmod 0700 of directory /var/lib/apt/lists/partial failed - SetupAPTPartialDirectory (1: Operation not permitted)
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
sudo apt-get update

Hit:1 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:3 [http://ppa.launchpad.net/forkotov02/ppa/ubuntu](http://ppa.launchpad.net/forkotov02/ppa/ubuntu) xenial InRelease          
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:5 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-updates InRelease             
Get:2 [http://deb.opera.com/opera](http://deb.opera.com/opera) stable InRelease [2.592 B]                    
Hit:6 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) xenial InRelease    
Hit:7 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Hit:8 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) xenial InRelease        
Hit:9 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                           
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Err:2 [http://deb.opera.com/opera](http://deb.opera.com/opera) stable InRelease              
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D615560BA5C7FF72
Fetched 105 kB in 1s (79,0 kB/s)
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://deb.opera.com/opera](http://deb.opera.com/opera) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D615560BA5C7FF72
W: Failed to fetch [http://deb.opera.com/opera/dists/stable/InRelease](http://deb.opera.com/opera/dists/stable/InRelease)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D615560BA5C7FF72
W: Some index files failed to download. They have been ignored, or old ones used instead.

```




**apt-get upgrade**

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-78-generic : Depends: linux-image-4.4.0-78-generic but it is not installed
 linux-image-extra-4.4.0-83-generic : Depends: linux-image-4.4.0-83-generic but it is not installed
 linux-image-extra-4.4.0-87-generic : Depends: linux-image-4.4.0-87-generic but it is not installed
 linux-image-generic : Depends: linux-image-4.4.0-87-generic but it is not installed
E: Unmet dependencies. Try using -f.
```

---

### Post by BenginM on 2017-08-01
Well, thanks .. as you can see you have a separate /boot partition 

   ```


df -h
Filesystem                    Size  Used Avail Use% Mounted on
udev                          2,0G     0  2,0G   0% /dev
tmpfs                         401M  6,5M  395M   2% /run
/dev/mapper/xubuntu--vg-root  289G  199G   77G  73% /
tmpfs                         2,0G   18M  2,0G   1% /dev/shm
tmpfs                         5,0M  4,0K  5,0M   1% /run/lock
tmpfs                         2,0G     0  2,0G   0% /sys/fs/cgroup
/dev/sda1                     472M  468M     0 100% /boot
tmpfs                         401M   44K  401M   1% /run/user/1000
```

and it's full because it doesn't even have enough space to hold many kernels , And the best solution for this issue is not to have a separate /boot partition. If you really need it separated, then give it a large enough space! The default Ubuntu  installation partitioning  scheme does not have a separate /boot.

anyway , now you need to remove -purge those old kernels manually , but you must leave at least one previous kernel that is working properly to fall back into when need be. 

So, your current base kernel in use is    4.4.0-64-generic

check which of these other kernels prior to 4.4.0.-64 that is working properly keep one or two and remove the others , like in:

[https://help.ubuntu.com/community/RemoveOldKernels#Safely_Removing_Old_Kernels](https://help.ubuntu.com/community/RemoveOldKernels#Safely_Removing_Old_Kernels)

$ dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+' | grep -Fv $(uname -r)

so lets remove 4.4.0-21-generic 

$ sudo dpkg --purge linux-image-4.4.0-21-generic 
$ sudo dpkg --purge linux-headers-4.4.0-21-generic
$ sudo dpkg --purge linux-image-extra-4.4.0-21-generic
you got the idea , then when you reach the point of keepin' the last two working kernels , then run:

$ sudo dpkg --configure -a
$ sudo apt-get -f install

$ sudo apt clean 

$ sudo apt update

$ sudo apt upgrade && sudo apt dist-upgrade 

Then tell us how it went..

---

### Post by ljubinski on 2017-08-01
hey, thank you for this detailed instruction and explanation!
i started the purge linux **image** which went well i think, but the **headers** and **image-extra** always returned like in this example for nr. 38
 
```
sudo dpkg --purge linux-headers-4.4.0-38-generic
$: command not found

sudo dpkg --purge linux-image-extra-4.4.0-38-generic
$: command not found

```

after only two running kernels (62 and 64) were left i had about 150 MB free space and i started the 

$ sudo dpkg --configure -a
$ sudo apt-get -f install

$ sudo apt clean 
$ sudo apt update 

this last one however returned something i have seen before:

```
Hit:1 [http://ppa.launchpad.net/forkotov02/ppa/ubuntu](http://ppa.launchpad.net/forkotov02/ppa/ubuntu) xenial InRelease
Hit:2 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial InRelease                     
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Get:4 [http://deb.opera.com/opera](http://deb.opera.com/opera) stable InRelease [2.592 B]                    
Hit:5 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) xenial InRelease    
Get:6 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Hit:7 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) xenial InRelease        
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Get:9 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Hit:10 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                          
Err:4 [http://deb.opera.com/opera](http://deb.opera.com/opera) stable InRelease                              
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D615560BA5C7FF72
Get:11 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [572 kB]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 DEP-11 Metadata [59,3 kB]
Get:13 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-updates/main i386 DEP-11 Metadata [304 kB]
Get:14 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [205 kB]
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [49,6 kB]
Get:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe i386 DEP-11 Metadata [40,7 kB]
Get:17 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [493 kB]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [56,1 kB]
Get:19 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 DEP-11 Metadata [163 kB]
Get:20 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [212 kB]
Get:21 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-updates/multiverse i386 DEP-11 Metadata [7.060 B]
Get:22 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-backports/main i386 DEP-11 Metadata [3.324 B]
Get:23 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-backports/universe i386 DEP-11 Metadata [4.684 B]
Fetched 2.480 kB in 3s (790 kB/s)                                 
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
376 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://deb.opera.com/opera](http://deb.opera.com/opera) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D615560BA5C7FF72
W: Failed to fetch [http://deb.opera.com/opera/dists/stable/InRelease](http://deb.opera.com/opera/dists/stable/InRelease)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D615560BA5C7FF72
W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by BenginM on 2017-08-01
Ok, for the opera repo key.. try [nimbosa]("http://forums.opera.com/profile/229861439/nimbosa")['s answer here]("http://forums.opera.com/discussion/1866434/no-public-key-available-for-the-following-key-ids-63f7d4aff6d61d45-when-doing-apt-get-update/p1")

and do $ sudo apt update , again.

So how ls /boot , and df -h  looks like now!

you did a good job troubleshooting this ..

in ubuntu xenial , you should be running at least kernel base 4.8.0- , 

install the the HWE stack for Desktop , should give you a newer kernel , then remove the old one and only keep one working kernel beside the new kernel as you only have few MB left in /boot

 sudo apt-get install --install-recommends linux-generic-hwe-16.04 xserver-xorg-hwe-16.04

source :

[URL="https://wiki.ubuntu.com/Kernel/LTSEnablementStack"]https://wiki.ubuntu.com/Kernel/LTSEnablementStack


[/URL]

---

### Post by ljubinski on 2017-08-01
hmmm.. nimbosas proposal turned out not to be working as well...

```
sudo wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | apt-key add -
--2017-08-01 16:13:52--  [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key)
Resolving deb.opera.com (deb.opera.com)... 185.26.183.130
Connecting to deb.opera.com (deb.opera.com)|185.26.183.130|:80... connected.
HTTP request sent, awaiting response... ERROR: This command can only be used by root.
200 OK
Length: 3152 (3,1K) [application/pgp-keys]
Saving to: &#8216;STDOUT&#8217;

-                            0%[                                       ]       0  --.-KB/s    in 0s      


Cannot write to &#8216;-&#8217; (Broken pipe).


```

meanwhile ls /boot returns this here
ls /boot
```
abi-4.4.0-64-generic         initrd.img-4.4.0-38-generic  memtest86+_multiboot.bin
abi-4.4.0-66-generic         initrd.img-4.4.0-45-generic  System.map-4.4.0-64-generic
abi-4.4.0-72-generic         initrd.img-4.4.0-51-generic  System.map-4.4.0-66-generic
abi-4.4.0-75-generic         initrd.img-4.4.0-57-generic  System.map-4.4.0-72-generic
abi-4.4.0-87-generic         initrd.img-4.4.0-59-generic  System.map-4.4.0-75-generic
config-4.4.0-64-generic      initrd.img-4.4.0-64-generic  System.map-4.4.0-87-generic
config-4.4.0-66-generic      initrd.img-4.4.0-66-generic  vmlinuz-4.4.0-64-generic
config-4.4.0-72-generic      initrd.img-4.4.0-72-generic  vmlinuz-4.4.0-66-generic
config-4.4.0-75-generic      initrd.img-4.4.0-75-generic  vmlinuz-4.4.0-72-generic
config-4.4.0-87-generic      initrd.img-4.4.0-87-generic  vmlinuz-4.4.0-75-generic
grub                         lost+found                   vmlinuz-4.4.0-87-generic
initrd.img-4.4.0-21-generic  memtest86+.bin
initrd.img-4.4.0-36-generic  memtest86+.elf
```

---

### Post by kc1di on 2017-08-01
the opera error can be corrected by downloading opera 46 and installing that using software installer or installing gdebi.

---

### Post by BenginM on 2017-08-01
are you able to add the key this way :


wget -qO - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -
if that doesn;t work , you may have to run it as root , if you have your root passwd , $ su -
wget -qO - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | apt-key add -
##
someone should notify the opera devs to Change public signing key instructions to work with sudo!


please post the output of 
$ dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+' | grep -Fv $(uname -r)
$ ls -al /usr/src/
$ ls -al /lib/modules/

so we could have a clear picture of the kernels status. thanks
remember what ii, iU , r "removed" , H "half installed" ..

[https://help.ubuntu.com/community/RemoveOldKernels#Safely_Removing_Old_Kernels](https://help.ubuntu.com/community/RemoveOldKernels#Safely_Removing_Old_Kernels)

---

### Post by mahfoud-ws on 2017-08-05
i have the same problem, i always get this error  message "Sub-process /usr/bin/dpkg returned an error code (1)"

---

