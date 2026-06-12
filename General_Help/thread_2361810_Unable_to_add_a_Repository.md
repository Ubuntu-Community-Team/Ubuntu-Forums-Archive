---
title: "Unable to add a Repository"
date: 2017-05-21
forum: General Help
---

### Post by natesnape on 2017-05-21
Hello, I'm unable to add this repository add-apt-repository ppa:gezakovacs/ppa &#8203;and getting this error, please help

```

Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 95, in <module>
    sp = SoftwareProperties(options=options)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 114, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 607, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 89, in get_sources
    (self.id, self.codename))
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template for Ubuntu/zesty
*
```*

---

### Post by wildmanne39 on 2017-05-21
> aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template for Ubuntu/zesty
To me that means this version of the application is not made for 17.04.

---

### Post by again? on 2017-05-21
No problem here on zesty.
```
glen@GU17:~$ **lsb_release -a**
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 17.04
Release:	17.04
Codename:	zesty

glen@GU17:~$ **sudo add-apt-repository ppa:gezakovacs/ppa**
[sudo] password for glen: 
 UNetbootin http://unetbootin.github.io/ is a cross-platform utility that can create Live USB systems and can load a variety of system utilities or install various Linux distributions and other operating systems without a CD.

Homepage: http://unetbootin.github.io/
Wiki: http://unetbootin.wiki.sourceforge.net/
Downloads: http://sourceforge.net/project/showfiles.php?group_id=222386
Sourceforge: http://sourceforge.net/projects/unetbootin
Launchpad: http://launchpad.net/unetbootin
 More info: https://launchpad.net/~gezakovacs/+archive/ubuntu/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keybox '/tmp/tmpjluwhu93/pubring.gpg' created
gpg: /tmp/tmpjluwhu93/trustdb.gpg: trustdb created
gpg: key D45DF2E8FC91AE7E: public key "Launchpad PPA for Geza Kovacs" imported
gpg: Total number processed: 1
gpg:               imported: 1
OK
glen@GU17:~$ 
```

```
glen@GU17:~$ **apt policy unetbootin**
unetbootin:
  Installed: 638-1~zesty1
  Candidate: 647-1~zesty1
  Version table:
     647-1~zesty1 500
        500 http://ppa.launchpad.net/gezakovacs/ppa/ubuntu zesty/main amd64 Packages
 *** 638-1~zesty1 100
        100 /var/lib/dpkg/status
     608-1 500
        500 http://ftp.iinet.net.au/pub/ubuntu zesty/universe amd64 Packages
```



Any errors when you run
```
sudo apt update
sudo apt upgrade 
```

---

### Post by natesnape on 2017-05-21
```

natesnape@A-Toaster:~$ sudo apt update
[sudo] password for natesnape: 
Hit:1 http://ph.archive.ubuntu.com/ubuntu yakkety InRelease                    
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
Get:3 http://ph.archive.ubuntu.com/ubuntu yakkety-updates InRelease [102 kB]   
Hit:4 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:5 http://download.mono-project.com/repo/debian wheezy InRelease            
Get:6 http://ph.archive.ubuntu.com/ubuntu yakkety-backports InRelease [102 kB] 
Hit:7 http://download.mono-project.com/repo/debian wheezy-apache24-compat InRelease
Get:8 http://security.ubuntu.com/ubuntu yakkety-security InRelease [102 kB]    
Hit:9 http://archive.canonical.com/ubuntu yakkety InRelease                    
Hit:10 http://repository.spotify.com stable InRelease                          
Hit:12 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu yakkety InRelease
Hit:13 http://ppa.launchpad.net/deluge-team/ppa/ubuntu yakkety InRelease       
Hit:14 http://ppa.launchpad.net/dolphin-emu/ppa/ubuntu yakkety InRelease       
Hit:15 http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu yakkety InRelease
Hit:16 http://ppa.launchpad.net/jd-team/jdownloader/ubuntu yakkety InRelease   
Hit:17 http://ppa.launchpad.net/libreoffice/ppa/ubuntu yakkety InRelease       
Hit:18 http://ppa.launchpad.net/libretro/stable/ubuntu yakkety InRelease       
Hit:19 http://ppa.launchpad.net/libretro/testing/ubuntu yakkety InRelease      
Hit:20 http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu yakkety InRelease
Hit:21 http://repo.steampowered.com/steam precise InRelease               
Hit:22 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu yakkety InRelease
Hit:23 http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu yakkety InRelease
Hit:24 http://ppa.launchpad.net/ppsspp/stable/ubuntu yakkety InRelease         
Hit:25 http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu yakkety InRelease
Hit:26 http://ppa.launchpad.net/wine/wine-builds/ubuntu yakkety InRelease      
Fetched 306 kB in 11s (25.8 kB/s)                                              
Reading package lists... Done
Building dependency tree       
Reading state information... Done
5 packages can be upgraded. Run 'apt list --upgradable' to see them.
natesnape@A-Toaster:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libao-common libao4 libbonobo2-0 libbonobo2-common libechonest2.3 libftgl2
  libgnome-2-0 libgnome2-common libgnomevfs2-0 libgnomevfs2-common libjasper1
  libmbedcrypto0 libmbedtls10 libmbedx509-0 libmygpo-qt1 liborbit-2-0
  libprojectm2v5 libqxt-core0 libqxt-gui0 libreoffice-sdbc-firebird
  libsoundtouch1 linux-headers-4.8.0-22 linux-headers-4.8.0-22-generic
  linux-headers-4.8.0-39 linux-headers-4.8.0-39-generic
  linux-image-4.8.0-22-generic linux-image-4.8.0-39-generic
  linux-image-extra-4.8.0-22-generic linux-image-extra-4.8.0-39-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  gstreamer1.0-pulseaudio libusb-0.1-4:i386 linux-headers-4.8.0-52
  linux-headers-4.8.0-52-generic linux-image-4.8.0-52-generic
  linux-image-extra-4.8.0-52-generic
The following packages will be upgraded:
  clementine linux-generic linux-headers-generic linux-image-generic
  pcsx2:i386
5 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 80.5 MB of archives.
After this operation, 322 MB of additional disk space will be used.
Do you want to continue? [Y/n]  

```

I don't think I have any errors?

---

### Post by again? on 2017-05-21
Error and your forum profile refer to zesty but apt update shows yakkety.
What release are you using?
```
lsb_release -a
```

In any case I would install updates, reboot and try to add repo again.

---

### Post by natesnape on 2017-05-21
> **guber2 said:**
> Error and your forum profile refer to zesty but apt update shows yakkety.
What release are you using?
```
lsb_release -a
```

In any case I would install updates, reboot and try to add repo again.

```

natesnape@A-Toaster:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Zesty Zapus (development branch)
Release:	17.04
Codename:	zesty

```

Currently installing that 300MB plus update, and it's stuck at 64%.

> **natesnape said:**
> ```

natesnape@A-Toaster:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Zesty Zapus (development branch)
Release:    17.04
Codename:    zesty

```

Currently installing that 300MB plus update, and it's stuck at 64%.

Done with the update

```

Do you want to continue? [Y/n] y
Get:1 http://ph.archive.ubuntu.com/ubuntu yakkety-updates/main amd64 gstreamer1.0-pulseaudio amd64 1.8.3-1ubuntu1.3 [56.3 kB]
Get:2 http://ph.archive.ubuntu.com/ubuntu yakkety/main i386 libusb-0.1-4 i386 2:0.1.12-30 [17.7 kB]
Get:3 http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu yakkety/main amd64 clementine amd64 1.3.1-333-gf854bc5~yakkety [5,290 kB]
Get:4 http://ph.archive.ubuntu.com/ubuntu yakkety-updates/main amd64 linux-image-4.8.0-52-generic amd64 4.8.0-52.55 [23.6 MB]
Get:5 http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu yakkety/main i386 pcsx2 i386 1:1.4.0-8 [3,054 kB]
Get:6 http://ph.archive.ubuntu.com/ubuntu yakkety-updates/main amd64 linux-image-extra-4.8.0-52-generic amd64 4.8.0-52.55 [37.4 MB]
Get:7 http://ph.archive.ubuntu.com/ubuntu yakkety-updates/main amd64 linux-generic amd64 4.8.0.52.64 [1,780 B]
Get:8 http://ph.archive.ubuntu.com/ubuntu yakkety-updates/main amd64 linux-image-generic amd64 4.8.0.52.64 [2,352 B]
Get:9 http://ph.archive.ubuntu.com/ubuntu yakkety-updates/main amd64 linux-headers-4.8.0-52 all 4.8.0-52.55 [10.2 MB]
Get:10 http://ph.archive.ubuntu.com/ubuntu yakkety-updates/main amd64 linux-headers-4.8.0-52-generic amd64 4.8.0-52.55 [814 kB]
Get:11 http://ph.archive.ubuntu.com/ubuntu yakkety-updates/main amd64 linux-headers-generic amd64 4.8.0.52.64 [2,324 B]
Fetched 80.5 MB in 2min 14s (600 kB/s)                                         
Selecting previously unselected package gstreamer1.0-pulseaudio:amd64.
(Reading database ... 263003 files and directories currently installed.)
Preparing to unpack .../00-gstreamer1.0-pulseaudio_1.8.3-1ubuntu1.3_amd64.deb ...
Unpacking gstreamer1.0-pulseaudio:amd64 (1.8.3-1ubuntu1.3) ...
Preparing to unpack .../01-clementine_1.3.1-333-gf854bc5~yakkety_amd64.deb ...
Unpacking clementine (1.3.1-333-gf854bc5~yakkety) over (1.3.1+dfsg-1build1) ...
Selecting previously unselected package libusb-0.1-4:i386.
Preparing to unpack .../02-libusb-0.1-4_2%3a0.1.12-30_i386.deb ...
Unpacking libusb-0.1-4:i386 (2:0.1.12-30) ...
Selecting previously unselected package linux-image-4.8.0-52-generic.
Preparing to unpack .../03-linux-image-4.8.0-52-generic_4.8.0-52.55_amd64.deb ...
Done.
Unpacking linux-image-4.8.0-52-generic (4.8.0-52.55) ...
Selecting previously unselected package linux-image-extra-4.8.0-52-generic.
Preparing to unpack .../04-linux-image-extra-4.8.0-52-generic_4.8.0-52.55_amd64.deb ...
Unpacking linux-image-extra-4.8.0-52-generic (4.8.0-52.55) ...
Preparing to unpack .../05-linux-generic_4.8.0.52.64_amd64.deb ...
Unpacking linux-generic (4.8.0.52.64) over (4.8.0.46.58) ...
Preparing to unpack .../06-linux-image-generic_4.8.0.52.64_amd64.deb ...
Unpacking linux-image-generic (4.8.0.52.64) over (4.8.0.46.58) ...
Selecting previously unselected package linux-headers-4.8.0-52.
Preparing to unpack .../07-linux-headers-4.8.0-52_4.8.0-52.55_all.deb ...
Unpacking linux-headers-4.8.0-52 (4.8.0-52.55) ...
Selecting previously unselected package linux-headers-4.8.0-52-generic.
Preparing to unpack .../08-linux-headers-4.8.0-52-generic_4.8.0-52.55_amd64.deb ...
Unpacking linux-headers-4.8.0-52-generic (4.8.0-52.55) ...
Preparing to unpack .../09-linux-headers-generic_4.8.0.52.64_amd64.deb ...
Unpacking linux-headers-generic (4.8.0.52.64) over (4.8.0.46.58) ...
Preparing to unpack .../10-pcsx2_1%3a1.4.0-8_i386.deb ...
Unpacking pcsx2:i386 (1:1.4.0-8) over (1.4.0+dfsg-2) ...
Processing triggers for gconf2 (3.2.6-3ubuntu7) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Setting up gstreamer1.0-pulseaudio:amd64 (1.8.3-1ubuntu1.3) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu1.1) ...
Setting up linux-image-4.8.0-52-generic (4.8.0-52.55) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.8.0-52-generic /boot/vmlinuz-4.8.0-52-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.8.0-52-generic /boot/vmlinuz-4.8.0-52-generic
^[[A^[[A^[[A^[[A^[[A^[[A^[[B^[[B^[[B^[[B^[[B^[[B^[[A^[[A^[[A^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[B^[[B^[[B^[[B^[[B^[[B^[[A^[[A^[[A^[[B^[[B^[[B^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[B^[[B^[[Brun-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.8.0-52-generic /boot/vmlinuz-4.8.0-52-generic
update-initramfs: Generating /boot/initrd.img-4.8.0-52-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.8.0-52-generic /boot/vmlinuz-4.8.0-52-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.8.0-52-generic /boot/vmlinuz-4.8.0-52-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.8.0-52-generic /boot/vmlinuz-4.8.0-52-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.8.0-52-generic /boot/vmlinuz-4.8.0-52-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.8.0-52-generic
Found initrd image: /boot/initrd.img-4.8.0-52-generic
^[[B^[[B^[[BFound linux image: /boot/vmlinuz-4.8.0-46-generic
Found initrd image: /boot/initrd.img-4.8.0-46-generic
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-22-generic
Found initrd image: /boot/initrd.img-4.8.0-22-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 10 (loader) on /dev/sdb1
done
Processing triggers for libc-bin (2.24-3ubuntu2) ...
/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link


/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link


Setting up linux-headers-4.8.0-52 (4.8.0-52.55) ...
Setting up pcsx2:i386 (1:1.4.0-8) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for hicolor-icon-theme (0.15-1) ...
Setting up linux-headers-4.8.0-52-generic (4.8.0-52.55) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.8.0-52-generic /boot/vmlinuz-4.8.0-52-generic
Setting up libusb-0.1-4:i386 (2:0.1.12-30) ...
Setting up linux-headers-generic (4.8.0.52.64) ...
Setting up clementine (1.3.1-333-gf854bc5~yakkety) ...
Setting up linux-image-extra-4.8.0-52-generic (4.8.0-52.55) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.8.0-52-generic /boot/vmlinuz-4.8.0-52-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.8.0-52-generic /boot/vmlinuz-4.8.0-52-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.8.0-52-generic /boot/vmlinuz-4.8.0-52-generic
update-initramfs: Generating /boot/initrd.img-4.8.0-52-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.8.0-52-generic /boot/vmlinuz-4.8.0-52-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.8.0-52-generic /boot/vmlinuz-4.8.0-52-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.8.0-52-generic /boot/vmlinuz-4.8.0-52-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.8.0-52-generic /boot/vmlinuz-4.8.0-52-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.8.0-52-generic
Found initrd image: /boot/initrd.img-4.8.0-52-generic
Found linux image: /boot/vmlinuz-4.8.0-46-generic
Found initrd image: /boot/initrd.img-4.8.0-46-generic
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-22-generic
Found initrd image: /boot/initrd.img-4.8.0-22-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 10 (loader) on /dev/sdb1
done
Setting up linux-image-generic (4.8.0.52.64) ...
Setting up linux-generic (4.8.0.52.64) ...
Processing triggers for libc-bin (2.24-3ubuntu2) ...
/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link


/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link


natesnape@A-Toaster:~$ 

```

---

### Post by again? on 2017-05-21
```
Description:    Ubuntu Zesty Zapus (development branch)
```
I don't run development releases so am not familiar with the update procedures 
or  why you are still using yaketty sources.
I'll let someone who does guide you.

---

### Post by natesnape on 2017-05-21
I'm not entirely sure as well... I just installed 17.04 when it asked for the update, is there a way to install the official one and not the development branch?

---

### Post by howefield on 2017-05-21
Do a 

```
cat /etc/*-release
```

now that you have completed the update it should drop the "*development release*" tag.

Then try the

```
add-apt-repository ppa:gezakovacs/ppa
```

---

### Post by natesnape on 2017-05-21
> **howefield said:**
> Do a 

```
cat /etc/*-release
```

now that you have completed the update it should drop the "*development release*" tag.

Then try the

```
add-apt-repository ppa:gezakovacs/ppa
```

Still getting the same issue mate.

```

natesnape@A-Toaster:~$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.04
DISTRIB_CODENAME=zesty
DISTRIB_DESCRIPTION="Ubuntu Zesty Zapus (development branch)"
NAME="Ubuntu"
VERSION="17.04 (Zesty Zapus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu Zesty Zapus (development branch)"
VERSION_ID="17.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="http://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=zesty
UBUNTU_CODENAME=zesty
natesnape@A-Toaster:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Zesty Zapus (development branch)
Release:	17.04
Codename:	zesty
natesnape@A-Toaster:~$ add-apt-repository ppa:gezakovacs/ppa
Error: must run as root
natesnape@A-Toaster:~$ sudo add-apt-repository ppa:gezakovacs/ppa
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 95, in <module>
    sp = SoftwareProperties(options=options)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 114, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 607, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 89, in get_sources
    (self.id, self.codename))
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template for Ubuntu/zesty
natesnape@A-Toaster:~$ 

```

The only thing that I haven't tried is updating my kernel...

---

### Post by vasa1 on 2017-05-21
Have you tried```
sudo apt-get dist-upgrade
```which will upgrade your kernel as well? Do you have some specific reason for not updating your kernel?

---

### Post by howefield on 2017-05-21
So why the yakkety repositories if you are on Zesty ?

What's the output of ..

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by natesnape on 2017-05-22
Will try this when I got home, Hopefully I'll have a stable internet connection for the update.

> **vasa1 said:**
> Have you tried```
sudo apt-get dist-upgrade
```which will upgrade your kernel as well? Do you have some specific reason for not updating your kernel?

I'm not sure, I just did the update when it offered me, btw what's the latest kernel version so I can check mine.

> **howefield said:**
> So why the yakkety repositories if you are on Zesty ?

What's the output of ..

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

I'm really not sure mate... I just did the update, I'm pretty new to this...

> **vasa1 said:**
> Have you tried```
sudo apt-get dist-upgrade
```which will upgrade your kernel as well? Do you have some specific reason for not updating your kernel?

Here's what I got.

```

natesnape@A-Toaster:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libao-common libao4 libbonobo2-0 libbonobo2-common libechonest2.3 libftgl2
  libgnome-2-0 libgnome2-common libgnomevfs2-0 libgnomevfs2-common libjasper1
  libmbedcrypto0 libmbedtls10 libmbedx509-0 libmygpo-qt1 liborbit-2-0
  libprojectm2v5 libqxt-core0 libqxt-gui0 libreoffice-sdbc-firebird
  libsoundtouch1 linux-headers-4.8.0-22 linux-headers-4.8.0-22-generic
  linux-headers-4.8.0-39 linux-headers-4.8.0-39-generic linux-headers-4.8.0-41
  linux-headers-4.8.0-41-generic linux-image-4.8.0-22-generic
  linux-image-4.8.0-39-generic linux-image-4.8.0-41-generic
  linux-image-extra-4.8.0-22-generic linux-image-extra-4.8.0-39-generic
  linux-image-extra-4.8.0-41-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
natesnape@A-Toaster:~$ 

```

> **howefield said:**
> So why the yakkety repositories if you are on Zesty ?

What's the output of ..

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

Here's the output.

```

natesnape@A-Toaster:~$ egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:deb http://ph.archive.ubuntu.com/ubuntu/ yakkety main restricted
/etc/apt/sources.list:deb http://ph.archive.ubuntu.com/ubuntu/ yakkety-updates main restricted
/etc/apt/sources.list:deb http://ph.archive.ubuntu.com/ubuntu/ yakkety universe
/etc/apt/sources.list:deb http://ph.archive.ubuntu.com/ubuntu/ yakkety-updates universe
/etc/apt/sources.list:deb http://ph.archive.ubuntu.com/ubuntu/ yakkety multiverse
/etc/apt/sources.list:deb http://ph.archive.ubuntu.com/ubuntu/ yakkety-updates multiverse
/etc/apt/sources.list:deb http://ph.archive.ubuntu.com/ubuntu/ yakkety-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu yakkety partner
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu yakkety-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu yakkety-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu yakkety-security multiverse
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-yakkety.list:deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu yakkety main
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-yakkety.list.save:deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu yakkety main
/etc/apt/sources.list.d/deluge-team-ubuntu-ppa-yakkety.list:deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu yakkety main
/etc/apt/sources.list.d/deluge-team-ubuntu-ppa-yakkety.list.save:deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu yakkety main
/etc/apt/sources.list.d/dolphin-emu-ubuntu-ppa-yakkety.list:deb http://ppa.launchpad.net/dolphin-emu/ppa/ubuntu yakkety main
/etc/apt/sources.list.d/dolphin-emu-ubuntu-ppa-yakkety.list.save:deb http://ppa.launchpad.net/dolphin-emu/ppa/ubuntu yakkety main
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/gregory-hainaut-ubuntu-pcsx2_official_ppa-yakkety.list:deb http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu yakkety main
/etc/apt/sources.list.d/gregory-hainaut-ubuntu-pcsx2_official_ppa-yakkety.list.save:deb http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu yakkety main
/etc/apt/sources.list.d/jd-team-ubuntu-jdownloader-yakkety.list:deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu yakkety main
/etc/apt/sources.list.d/jd-team-ubuntu-jdownloader-yakkety.list.save:deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu yakkety main
/etc/apt/sources.list.d/libreoffice-ubuntu-ppa-yakkety.list:deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu yakkety main
/etc/apt/sources.list.d/libreoffice-ubuntu-ppa-yakkety.list.save:deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu yakkety main
/etc/apt/sources.list.d/libretro-ubuntu-stable-yakkety.list:deb http://ppa.launchpad.net/libretro/stable/ubuntu yakkety main
/etc/apt/sources.list.d/libretro-ubuntu-stable-yakkety.list.save:deb http://ppa.launchpad.net/libretro/stable/ubuntu yakkety main
/etc/apt/sources.list.d/libretro-ubuntu-testing-yakkety.list:deb http://ppa.launchpad.net/libretro/testing/ubuntu yakkety main
/etc/apt/sources.list.d/libretro-ubuntu-testing-yakkety.list.save:deb http://ppa.launchpad.net/libretro/testing/ubuntu yakkety main
/etc/apt/sources.list.d/me-davidsansome-ubuntu-clementine-yakkety.list:deb http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu yakkety main
/etc/apt/sources.list.d/me-davidsansome-ubuntu-clementine-yakkety.list.save:deb http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu yakkety main
/etc/apt/sources.list.d/mono-xamarin.list:deb http://download.mono-project.com/repo/debian wheezy main
/etc/apt/sources.list.d/mono-xamarin.list:deb http://download.mono-project.com/repo/debian wheezy-apache24-compat main
/etc/apt/sources.list.d/mono-xamarin.list.save:deb http://download.mono-project.com/repo/debian wheezy main
/etc/apt/sources.list.d/mono-xamarin.list.save:deb http://download.mono-project.com/repo/debian wheezy-apache24-compat main
/etc/apt/sources.list.d/otto-kesselgulasch-ubuntu-gimp-yakkety.list:deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu yakkety main
/etc/apt/sources.list.d/otto-kesselgulasch-ubuntu-gimp-yakkety.list.save:deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu yakkety main
/etc/apt/sources.list.d/plushuang-tw-ubuntu-uget-stable-yakkety.list:deb http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu yakkety main
/etc/apt/sources.list.d/plushuang-tw-ubuntu-uget-stable-yakkety.list.save:deb http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu yakkety main
/etc/apt/sources.list.d/ppsspp-ubuntu-stable-yakkety.list:deb http://ppa.launchpad.net/ppsspp/stable/ubuntu yakkety main
/etc/apt/sources.list.d/ppsspp-ubuntu-stable-yakkety.list.save:deb http://ppa.launchpad.net/ppsspp/stable/ubuntu yakkety main
/etc/apt/sources.list.d/spotify.list:deb http://repository.spotify.com stable non-free
/etc/apt/sources.list.d/spotify.list.save:deb http://repository.spotify.com stable non-free
/etc/apt/sources.list.d/steam.list:deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
/etc/apt/sources.list.d/steam.list:deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
/etc/apt/sources.list.d/steam.list.save:deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
/etc/apt/sources.list.d/steam.list.save:deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
/etc/apt/sources.list.d/ubuntu-toolchain-r-ubuntu-test-yakkety.list:deb http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu yakkety main
/etc/apt/sources.list.d/wine-ubuntu-wine-builds-yakkety.list:deb http://ppa.launchpad.net/wine/wine-builds/ubuntu yakkety main
/etc/apt/sources.list.d/wine-ubuntu-wine-builds-yakkety.list.save:deb http://ppa.launchpad.net/wine/wine-builds/ubuntu yakkety main
natesnape@A-Toaster:~$ 

```

There's definitely something wrong with my OS. I've checked my kernel version and got. 

```

natesnape@A-Toaster:~$ uname -r4.8.0-52-generic
natesnape@A-Toaster:~$ 

```

But the latest version according to lubuntu's version is [COLOR=#333333][FONT=&amp]Linux Kernel 4.10.
Is there a way to reinstall 17.04 completely with all the repositories and kernel without loosing all my data??[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2017-05-22
Yep...Using the install disk/usb when it come to the part to install>>>Select the Option "choose Something else"
Then set the mount point on your **already made partition **>>>>now do not format it...Make sure to choose the format you already had (ext4/ext3) and it should keep all your data in place.
But>>>and this is a big But>>>remove all PPA's and Remove any Drivers IE: Nvidia etc etc.
Then you "should" be Ok.
But things can still go bad...just saying.

---

### Post by natesnape on 2017-05-22
> **1fallen said:**
> Yep...Using the install disk/usb when it come to the part to install>>>Select the Option "choose Something else"
Then set the mount point on your **already made partition **>>>>now do not format it and should keep all your data in place.
But>>>and this is a big But>>>remove all PPA's and Remove any Drivers IE: Nvidia etc etc.
Then you "should" be Ok.
But things can still go bad...just saying.

Is there a way to do it via the command prompt?

---

### Post by #&amp;thj^% on 2017-05-22
> **natesnape said:**
> Is there a way to do it via the command prompt?
Not that I'm aware of.

---

### Post by again? on 2017-05-22
Have a read of this post.
[https://askubuntu.com/questions/49040/apt-could-not-find-a-distribution-template-error](https://askubuntu.com/questions/49040/apt-could-not-find-a-distribution-template-error)
Last answer would be what I would try, downloading the basefiles for yakkety as 
that appears to be what you are using despite the lsb_release output.
Backup and be prepared to fresh install if necessary.

---

### Post by natesnape on 2017-05-22
> **1fallen said:**
> Not that I'm aware of.

Man that's though, I mean most of my installers depends on their ppa for updates, I'll keep my games right? But still, Crazy...

---

### Post by natesnape on 2017-05-31
I did it without re installation

```

natesnape@A-Toaster:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 17.04
Release:	17.04
Codename:	zesty
natesnape@A-Toaster:~$ 

```

```

natesnape@A-Toaster:~$ sudo add-apt-repository ppa:gezakovacs/ppa
[sudo] password for natesnape: 
 UNetbootin http://unetbootin.github.io/ is a cross-platform utility that can create Live USB systems and can load a variety of system utilities or install various Linux distributions and other operating systems without a CD.


Homepage: http://unetbootin.github.io/
Wiki: http://unetbootin.wiki.sourceforge.net/
Downloads: http://sourceforge.net/project/showfiles.php?group_id=222386
Sourceforge: http://sourceforge.net/projects/unetbootin
Launchpad: http://launchpad.net/unetbootin
 More info: https://launchpad.net/~gezakovacs/+archive/ubuntu/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keybox '/tmp/tmpgct3wk4_/pubring.gpg' created
gpg: /tmp/tmpgct3wk4_/trustdb.gpg: trustdb created
gpg: key D45DF2E8FC91AE7E: public key "Launchpad PPA for Geza Kovacs" imported
gpg: Total number processed: 1
gpg:               imported: 1
OK
natesnape@A-Toaster:~$ 

```

---

### Post by natesnape on 2017-06-01
Now my only problem is how to update those repositories...

---

### Post by #&amp;thj^% on 2017-06-01
Just do:
```
sudo apt-get update
sudo apt-get upgrade
```
That updates the source's and added PPA's

---

### Post by coder91 on 2018-02-16
Hi, I've been stuck in a similar problem. My basefile also contained "development branch". I want to know how did you resolve the problem without re-install?

---

### Post by coder91 on 2018-02-16
How did you manage to do it?

---

### Post by wildmanne39 on 2018-02-16
Hi coder91, the OP of this thread has not been on the forum since right after he created this thread, please start your own thread if you need help.

Thanks

---

### Post by coder91 on 2018-02-16
Okay, thanks. I'll start my own thread in that case!

---

