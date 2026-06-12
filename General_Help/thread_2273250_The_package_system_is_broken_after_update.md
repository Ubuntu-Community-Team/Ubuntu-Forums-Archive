---
title: "The package system is broken after update"
date: 2015-04-11
forum: General Help
---

### Post by ibod on 2015-04-11
Hi All,

After running an update containing :- 

```

Linux Kernel headers for version 3.2.0 on 64 bit SMP linux-headers-3.2.0-80-generic (New install) (Size: 979kB)

```

The update manager reports :-

If you are using third party repositories then disable them, since they are a common source of problems.
Now run the following command in a terminal: apt-get install -f

```

tony@tony-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  bluez-alsa:i386 libsdl-ttf2.0-0:i386 libgconf-2-4:i386 libatk1.0-0:i386
  libstdc++5:i386 ia32-libs-multiarch:i386 libgail18:i386 libao-common
  libunistring0:i386 libcupsimage2:i386 libidn11:i386 libnss3:i386
  libcaca0:i386 gtk2-engines:i386 libgudev-1.0-0:i386 libcairo-gobject2:i386
  libavc1394-0:i386 ia32-libs libaio1:i386 odbcinst1debian2:i386
  libsdl-mixer1.2:i386 libcap2:i386 libproxy1:i386 ibus-gtk:i386
  libdbus-glib-1-2:i386 libtdb1:i386 libspeex1:i386 libgomp1:i386
  python-central libibus-1.0-0:i386 libcairo2:i386 libcanberra-gtk-module:i386
  libcanberra0:i386 gtk2-engines-murrine:i386 libwavpack1:i386
  libqt4-opengl:i386 libsoup-gnome2.4-1:i386 gstreamer0.10-plugins-good:i386
  lib32gcc1 librsvg2-common:i386 libiec61883-0:i386 lib32asound2
  libgdk-pixbuf2.0-0:i386 libsdl-image1.2:i386 libpixman-1-0:i386
  libsdl1.2debian:i386 libxaw7:i386 libgdbm3:i386 libcurl3:i386 libesd0:i386
  libmikmod2:i386 libxft2:i386 libcroco3:i386 libpulse-mainloop-glib0:i386
  libaa1:i386 libao4:i386 libxmu6:i386 libcanberra-gtk0:i386
  libvorbisfile3:i386 esound-common language-pack-kde-en libqt4-svg:i386
  libgail-common:i386 libraw1394-11:i386 libnspr4:i386 libshout3:i386
  libdv4:i386 kde-l10n-engb gstreamer0.10-x:i386 libgettextpo0:i386
  libsdl-net1.2:i386 libjasper1:i386 libgnome-keyring0:i386
  gtk2-engines-pixbuf:i386 libtag1c2a:i386 librsvg2-2:i386 libssl0.9.8:i386
  libmad0:i386 gtk2-engines-oxygen:i386 xaw3dg:i386 libpango1.0-0:i386
  libpulsedsp:i386 lib32stdc++6 libxcb-render0:i386 libodbc1:i386
  librtmp0:i386 libxp6:i386 libxcb-shm0:i386 language-pack-kde-en-base
  libgtk2.0-0:i386 glib-networking:i386 libsoup2.4-1:i386 libtag1-vanilla:i386
  libaudiofile1:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.2.0-80-generic
The following NEW packages will be installed
  linux-headers-3.2.0-80-generic
0 to upgrade, 1 to newly install, 0 to remove and 3 not to upgrade.
2 not fully installed or removed.
Need to get 0 B/978 kB of archives.
After this operation, 11.4 MB of additional disk space will be used.
Do you want to continue [Y/n]?  y
(Reading database ... 1224862 files and directories currently installed.)
Unpacking linux-headers-3.2.0-80-generic (from .../linux-headers-3.2.0-80-generic_3.2.0-80.116_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-80-generic_3.2.0-80.116_amd64.deb (--unpack):
 error creating symbolic link `./usr/src/linux-headers-3.2.0-80-generic/include/linux/ip.h': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-80-generic_3.2.0-80.116_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@tony-desktop:~$ 

```

having seen the "No space left on device"

```

tony@tony-desktop:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        19G   16G  2.8G  85% /
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           781M  1.2M  780M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  536K  3.9G   1% /run/shm
/dev/sda3        84G   51G   29G  65% /home
tony@tony-desktop:~$ 

```

and only 85% used, nearly 3G space 
at this point I am not at all sure what is going wrong, or that I had a clue in the first place !

Thanks for any guidance you can give

---

### Post by Bashing-om on 2015-04-11
ibod; Hi !

Another possibility, the allotment of inodes has been reached ?
what returns:
```

df -i

```

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe dig deeper
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ibod on 2015-04-11
Hi,

```

tony@tony-desktop:~$ df -i
Filesystem      Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1      1250928 1242946    7982  100% /
udev            997280     576  996704    1% /dev
tmpfs           999479     528  998951    1% /run
none            999479       3  999476    1% /run/lock
none            999479       8  999471    1% /run/shm
/dev/sda3      5578752   45854 5532898    1% /home

```

ok so it says Inodes: 1250928  Used: 1242946   Free: 7982  100% so how can there be 7,982 free Inodes - and it be 100% used

confusing ?

and how can I fix it ?

As I understand it - one Inode used per file - thats 1.25 Million Files !!! 

that can't be correct

---

### Post by Bashing-om on 2015-04-11
ibod; Humm ..

I agree, 7982 inodes free but at 100% use . Above my skill set to explain.
But, might try and delete a bunch of files, and see if that eliminates the problem 'till we know better.

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by mc4man on 2015-04-11
Well 7982 left out of 1,250,928 is less than 1% so maybe in that case it just reports 100%

---

### Post by ibod on 2015-04-11
Hi Bashing-om,


I Hope someone can explain...

I have already deleted many files but this has not solved the problem 

I have looked at all system folders to see if any have an unusual number of files and have found that /lib has well over 1 million
Also /usr also has over 1 million (more files than Inodes) ???

Ok this is getting weird ...

Re checked /lib and it now has 36 thousand (normal) 

Someone must know what is happening here 

could the failed update have screwed things up ?

system seems to be fine other than updates are broken

Anyone got any thoughts

---

### Post by ibod on 2015-04-11
> **mc4man said:**
> Well 7982 left out of 1,250,928 is less than 1% so maybe in that case it just reports 100%

Good point, that makes sense ;)

---

### Post by grahammechanical on 2015-04-11
The fact is that sda1 is 88% used. linux-headers-3.2.0-80-generic might be only 979 Kb ion size but unpacking it will use up 11.4 MB of disk space. linux-headers is only one of the kernel packages that are downloaded and installed with a kernel update. The other packages might already have been downloaded but not installed because the set of packages was not complete or they might be downloaded at the next update in a day or two.

There is another fact to take into account and that is you have a lot of packages no longer being used. How much space on sda1 do they take up. If this is an install of 12.04 that has been around for a few years it will have several older kernels and they are all taking up disk space and could be removed. 

Regards.

---

### Post by mörgæs on 2015-04-11
> **ibod said:**
> 
could the failed update have screwed things up ?


Yes. Have you considered a fresh install of 14.04.2?

---

### Post by claracc on 2015-04-12
I think I have had a similar problem with last kernel update in ubuntu 12.04.

Please see thread:[http://ubuntuforums.org/showthread.php?t=2272859](http://ubuntuforums.org/showthread.php?t=2272859)

What I would do is to try to recover some of inodes removing linux-headers from old unused kernels, to see them you can use command:

```
dpkg --get-selections | grep linux
```

Remove from folder /usr/src/ one of the old  linux-headers not used:

```
sudo rm -rf linux-headers-3.2.0-35 (becarefull with -rf option)
```

I think this way can prevent you to do a re-installation of the system.

In this way you will recover some of inodes to fix the broken update and you will be able to remove the old unused linux-headers in the proper way:

```
sudo apt-get purge linux-headers-3.2.0-41 linux-headers-3.2.0-44 linux-headers-3.2.0-45 linux-headers-3.2.0-48
```

sudo apt-get --fix-broken install

I think this is a seious ubuntu problem which had to be in the documentation when you remove old linux kernels. I have not find information in oficial documentation neither in the fora.

---

### Post by ibod on 2015-04-21
Hi Claracc,

Sorry about the delay in replying, work gets in the way of more important things some times lol 

to start check inodes and space

```

tony@tony-desktop:~$ df -i
Filesystem      Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1      1250928 1242925    8003  100% /
udev            997280     576  996704    1% /dev
tmpfs           999479     529  998950    1% /run
none            999479       3  999476    1% /run/lock
none            999479       5  999474    1% /run/shm
/dev/sda3      5578752   45786 5532966    1% /home
tony@tony-desktop:~$ df -i
Filesystem      Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1      1250928 1242925    8003  100% /
udev            997280     576  996704    1% /dev
tmpfs           999479     529  998950    1% /run
none            999479       3  999476    1% /run/lock
none            999479       5  999474    1% /run/shm
/dev/sda3      5578752   45786 5532966    1% /home
tony@tony-desktop:~$ 

```

so find oldest headers and try to remove the oldest headers to free up inodes

```

tony@tony-desktop:~$ dpkg --get-selections | grep linux
libselinux1                    install
libselinux1:i386                install
linux-firmware                    install
linux-generic                    install
linux-headers-3.2.0-29                install
linux-headers-3.2.0-29-generic            install
linux-headers-3.2.0-32                install
linux-headers-3.2.0-32-generic            install
linux-headers-3.2.0-33                install
linux-headers-3.2.0-33-generic            install
linux-headers-3.2.0-34                install
linux-headers-3.2.0-34-generic            install
linux-headers-3.2.0-35                install
linux-headers-3.2.0-35-generic            install
linux-headers-3.2.0-36                install
linux-headers-3.2.0-36-generic            install
linux-headers-3.2.0-37                install
linux-headers-3.2.0-37-generic            install
linux-headers-3.2.0-38                install
linux-headers-3.2.0-38-generic            install
linux-headers-3.2.0-39                install
linux-headers-3.2.0-39-generic            install
linux-headers-3.2.0-40                install
linux-headers-3.2.0-40-generic            install
linux-headers-3.2.0-41                install
linux-headers-3.2.0-41-generic            install
linux-headers-3.2.0-43                install
linux-headers-3.2.0-43-generic            install
linux-headers-3.2.0-44                install
linux-headers-3.2.0-44-generic            install
linux-headers-3.2.0-45                install
linux-headers-3.2.0-45-generic            install
linux-headers-3.2.0-48                install
linux-headers-3.2.0-48-generic            install
linux-headers-3.2.0-49                install
linux-headers-3.2.0-49-generic            install
linux-headers-3.2.0-51                install
linux-headers-3.2.0-51-generic            install
linux-headers-3.2.0-52                install
linux-headers-3.2.0-52-generic            install
linux-headers-3.2.0-53                install
linux-headers-3.2.0-53-generic            install
linux-headers-3.2.0-54                install
linux-headers-3.2.0-54-generic            install
linux-headers-3.2.0-55                install
linux-headers-3.2.0-55-generic            install
linux-headers-3.2.0-56                install
linux-headers-3.2.0-56-generic            install
linux-headers-3.2.0-57                install
linux-headers-3.2.0-57-generic            install
linux-headers-3.2.0-58                install
linux-headers-3.2.0-58-generic            install
linux-headers-3.2.0-59                install
linux-headers-3.2.0-59-generic            install
linux-headers-3.2.0-60                install
linux-headers-3.2.0-60-generic            install
linux-headers-3.2.0-61                install
linux-headers-3.2.0-61-generic            install
linux-headers-3.2.0-63                install
linux-headers-3.2.0-63-generic            install
linux-headers-3.2.0-64                install
linux-headers-3.2.0-64-generic            install
linux-headers-3.2.0-65                install
linux-headers-3.2.0-65-generic            install
linux-headers-3.2.0-67                install
linux-headers-3.2.0-67-generic            install
linux-headers-3.2.0-68                install
linux-headers-3.2.0-68-generic            install
linux-headers-3.2.0-69                install
linux-headers-3.2.0-69-generic            install
linux-headers-3.2.0-70                install
linux-headers-3.2.0-70-generic            install
linux-headers-3.2.0-72                install
linux-headers-3.2.0-72-generic            install
linux-headers-3.2.0-74                install
linux-headers-3.2.0-74-generic            install
linux-headers-3.2.0-75                install
linux-headers-3.2.0-75-generic            install
linux-headers-3.2.0-76                install
linux-headers-3.2.0-76-generic            install
linux-headers-3.2.0-77                install
linux-headers-3.2.0-77-generic            install
linux-headers-3.2.0-79                install
linux-headers-3.2.0-79-generic            install
linux-headers-3.2.0-80                install
linux-headers-generic                install
linux-image-3.2.0-29-generic            install
linux-image-3.2.0-32-generic            install
linux-image-3.2.0-33-generic            install
linux-image-3.2.0-34-generic            install
linux-image-3.2.0-35-generic            install
linux-image-3.2.0-36-generic            install
linux-image-3.2.0-37-generic            install
linux-image-3.2.0-38-generic            install
linux-image-3.2.0-39-generic            install
linux-image-3.2.0-40-generic            install
linux-image-3.2.0-41-generic            install
linux-image-3.2.0-43-generic            install
linux-image-3.2.0-44-generic            install
linux-image-3.2.0-45-generic            install
linux-image-3.2.0-48-generic            install
linux-image-3.2.0-49-generic            install
linux-image-3.2.0-51-generic            install
linux-image-3.2.0-52-generic            install
linux-image-3.2.0-53-generic            install
linux-image-3.2.0-54-generic            install
linux-image-3.2.0-55-generic            install
linux-image-3.2.0-56-generic            install
linux-image-3.2.0-57-generic            install
linux-image-3.2.0-58-generic            install
linux-image-3.2.0-59-generic            install
linux-image-3.2.0-60-generic            install
linux-image-3.2.0-61-generic            install
linux-image-3.2.0-63-generic            install
linux-image-3.2.0-64-generic            install
linux-image-3.2.0-65-generic            install
linux-image-3.2.0-67-generic            install
linux-image-3.2.0-68-generic            install
linux-image-3.2.0-69-generic            install
linux-image-3.2.0-70-generic            install
linux-image-3.2.0-72-generic            install
linux-image-3.2.0-74-generic            install
linux-image-3.2.0-75-generic            install
linux-image-3.2.0-76-generic            install
linux-image-3.2.0-77-generic            install
linux-image-3.2.0-79-generic            install
linux-image-3.2.0-80-generic            install
linux-image-generic                install
linux-libc-dev                    install
linux-sound-base                install
pptp-linux                    install
syslinux                    install
syslinux-common                    install
syslinux-legacy                    install
util-linux                    install
tony@tony-desktop:~$ 

```

I see "linux-headers-3.2.0-29" is my oldest linux headers

so 

```

tony@tony-desktop:~$ sudo rm -rf linux-headers-3.2.0-29
[sudo] password for tony: 
tony@tony-desktop:~$ 

```

then look to see if i have freed up any inodes

```

tony@tony-desktop:~$ df -i
Filesystem      Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1      1250928 1242928    8000  100% /
udev            997280     576  996704    1% /dev
tmpfs           999479     529  998950    1% /run
none            999479       3  999476    1% /run/lock
none            999479       5  999474    1% /run/shm
/dev/sda3      5578752   45785 5532967    1% /home
tony@tony-desktop:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        19G   16G  2.8G  85% /
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           781M  1.2M  780M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  124K  3.9G   1% /run/shm
/dev/sda3        84G   52G   29G  65% /home
tony@tony-desktop:~$ 

```

At this point I am confused, there was no error reported with the command and yet there is no extra space and no inodes have been freed up

---

### Post by matt_symes on 2015-04-21
Hi

Try this. Open a terminal and copy and paste this into it.

```
sudo dpkg -P linux-headers-3.2.0-3{2,3,4}{,-generic}
```

Then 

```
sudo apt-get install -f
```

and finally

```
sudo apt-get autoremove
```

If that works then post the output of these commands into your next post and we'll clean up most of those old kernel headers and images for you.

```
uname -r
```

and 

```
dpkg -l | egrep "linux-image|linux-headers|linux-signed"
```

This last command may have a lot of output but post it all anyway.

Kind regards

---

### Post by ibod on 2015-04-22
Hi Matt,

Thanks for your help

Well that all worked, here are the outputs you asked for.

First

```

tony@tony-desktop:~$ uname -r 
3.2.0-80-generic 
tony@tony-desktop:~$

```

Then

```

tony@tony-desktop:~$  dpkg -l | egrep "linux-image|linux-headers|linux-signed"
ii  linux-headers-3.2.0-29                 3.2.0-29.46                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-29-generic         3.2.0-29.46                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-35                 3.2.0-35.55                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-35-generic         3.2.0-35.55                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-36                 3.2.0-36.57                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-36-generic         3.2.0-36.57                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-37                 3.2.0-37.58                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-37-generic         3.2.0-37.58                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-38                 3.2.0-38.61                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-38-generic         3.2.0-38.61                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-39                 3.2.0-39.62                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-39-generic         3.2.0-39.62                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-40                 3.2.0-40.64                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-40-generic         3.2.0-40.64                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-41                 3.2.0-41.66                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-41-generic         3.2.0-41.66                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-43                 3.2.0-43.68                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-43-generic         3.2.0-43.68                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-44                 3.2.0-44.69                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-44-generic         3.2.0-44.69                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-45                 3.2.0-45.70                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-45-generic         3.2.0-45.70                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-48                 3.2.0-48.74                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-48-generic         3.2.0-48.74                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-49                 3.2.0-49.75                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-49-generic         3.2.0-49.75                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-51                 3.2.0-51.77                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-51-generic         3.2.0-51.77                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-52                 3.2.0-52.78                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-generic         3.2.0-52.78                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-53                 3.2.0-53.81                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-53-generic         3.2.0-53.81                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-54                 3.2.0-54.82                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-54-generic         3.2.0-54.82                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-55                 3.2.0-55.85                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-55-generic         3.2.0-55.85                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-56                 3.2.0-56.86                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-56-generic         3.2.0-56.86                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-57                 3.2.0-57.87                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-57-generic         3.2.0-57.87                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-58                 3.2.0-58.88                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-58-generic         3.2.0-58.88                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-59                 3.2.0-59.90                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-59-generic         3.2.0-59.90                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-60                 3.2.0-60.91                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-60-generic         3.2.0-60.91                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-61                 3.2.0-61.93                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-61-generic         3.2.0-61.93                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-63                 3.2.0-63.95                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-63-generic         3.2.0-63.95                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-64                 3.2.0-64.97                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-64-generic         3.2.0-64.97                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-65                 3.2.0-65.99                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-65-generic         3.2.0-65.99                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-67                 3.2.0-67.101                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-67-generic         3.2.0-67.101                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-68                 3.2.0-68.102                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-68-generic         3.2.0-68.102                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-69                 3.2.0-69.103                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-69-generic         3.2.0-69.103                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-70                 3.2.0-70.105                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-70-generic         3.2.0-70.105                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-72                 3.2.0-72.107                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-72-generic         3.2.0-72.107                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-74                 3.2.0-74.109                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-74-generic         3.2.0-74.109                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-75                 3.2.0-75.110                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-75-generic         3.2.0-75.110                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-76                 3.2.0-76.111                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-76-generic         3.2.0-76.111                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-77                 3.2.0-77.114                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-77-generic         3.2.0-77.114                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-79                 3.2.0-79.115                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-79-generic         3.2.0-79.115                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-80                 3.2.0-80.116                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-80-generic         3.2.0-80.116                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                  3.2.0.80.94                             Generic Linux kernel headers
ii  linux-image-3.2.0-29-generic           3.2.0-29.46                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-32-generic           3.2.0-32.51                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-33-generic           3.2.0-33.52                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-34-generic           3.2.0-34.53                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-35-generic           3.2.0-35.55                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-36-generic           3.2.0-36.57                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-37-generic           3.2.0-37.58                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-38-generic           3.2.0-38.61                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-39-generic           3.2.0-39.62                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-40-generic           3.2.0-40.64                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-41-generic           3.2.0-41.66                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-43-generic           3.2.0-43.68                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-44-generic           3.2.0-44.69                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-45-generic           3.2.0-45.70                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-48-generic           3.2.0-48.74                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-49-generic           3.2.0-49.75                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-51-generic           3.2.0-51.77                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-52-generic           3.2.0-52.78                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-53-generic           3.2.0-53.81                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-54-generic           3.2.0-54.82                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-55-generic           3.2.0-55.85                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-56-generic           3.2.0-56.86                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-57-generic           3.2.0-57.87                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-58-generic           3.2.0-58.88                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-59-generic           3.2.0-59.90                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-60-generic           3.2.0-60.91                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-61-generic           3.2.0-61.93                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-63-generic           3.2.0-63.95                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-64-generic           3.2.0-64.97                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-65-generic           3.2.0-65.99                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-67-generic           3.2.0-67.101                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-68-generic           3.2.0-68.102                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-69-generic           3.2.0-69.103                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-70-generic           3.2.0-70.105                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-72-generic           3.2.0-72.107                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-74-generic           3.2.0-74.109                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-75-generic           3.2.0-75.110                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-76-generic           3.2.0-76.111                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-77-generic           3.2.0-77.114                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-79-generic           3.2.0-79.115                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-80-generic           3.2.0-80.116                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-generic                    3.2.0.80.94                             Generic Linux kernel image
tony@tony-desktop:~$ 

```

I look forward to the help with cleaning up the remaining old kernel headers and images

Thanks

---

### Post by matt_symes on 2015-04-22
Hi

That's a whole lot of kernels and kernel headers kicking around on your system :)

Open a terminal and copy and paste this into it.

```
sudo apt-get purge "^linux-image-3.2.0-[3-7].-generic$"
```

This should remove all your old kernels bar the oldest (.29) and the current one (.80) and may take a while to complete.

Double check the kernel images it wants to remove before hitting the y key to remove them.

If that completes successfully we'll remove the header files.

Kind regards

---

### Post by claracc on 2015-04-23
I recovered some of the inodes by removing old unused linux-headers folders in /usr/src/ folder in the way I addressed :

Remove from folder /usr/src/ one of the old linux-headers not used:

sudo rm -rf linux-headers-3.2.0-29 (becarefull with -rf option)

but you have to be in the /usr/src/ folder

Then you can recover more inodes in the proper way, i.e.:

sudo apt-get purge linux-headers-3.2.0-41 linux-headers-3.2.0-44 linux-headers-3.2.0-45 and so on

---

### Post by matt_symes on 2015-04-23
Hi

> **claracc said:**
> 
Remove from folder /usr/src/ one of the old linux-headers not used:

sudo rm -rf linux-headers-3.2.0-29 (becarefull with -rf option)


Don't do this as it's bad practice.

Kind regards

---

### Post by ibod on 2015-04-23
Hi Matt, 

I not sure if  that all worked ok the terminal buffer did not capture the whole of the output but here is the bit that it did 

There were some differences ( removing vboxhost) ? with kernels 3.2.0-75 to 79 and kernel 3.2.0-79 also had some bad symbolic links  (vmlinuz.old  and  /initrd.img.old

Not at all sure if these are importent ?

Here is the output

```

Found initrd image: /boot/initrd.img-3.2.0-79-generic
Found linux image: /boot/vmlinuz-3.2.0-77-generic
Found initrd image: /boot/initrd.img-3.2.0-77-generic
Found linux image: /boot/vmlinuz-3.2.0-76-generic
Found initrd image: /boot/initrd.img-3.2.0-76-generic
Found linux image: /boot/vmlinuz-3.2.0-75-generic
Found initrd image: /boot/initrd.img-3.2.0-75-generic
Found linux image: /boot/vmlinuz-3.2.0-74-generic
Found initrd image: /boot/initrd.img-3.2.0-74-generic
Found linux image: /boot/vmlinuz-3.2.0-72-generic
Found initrd image: /boot/initrd.img-3.2.0-72-generic
Found linux image: /boot/vmlinuz-3.2.0-70-generic
Found initrd image: /boot/initrd.img-3.2.0-70-generic
Found linux image: /boot/vmlinuz-3.2.0-69-generic
Found initrd image: /boot/initrd.img-3.2.0-69-generic
Found linux image: /boot/vmlinuz-3.2.0-68-generic
Found initrd image: /boot/initrd.img-3.2.0-68-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sdb1
Found Ubuntu 10.04.4 LTS (10.04) on /dev/sdc1
done
Purging configuration files for linux-image-3.2.0-65-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-65-generic /boot/vmlinuz-3.2.0-65-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-65-generic /boot/vmlinuz-3.2.0-65-generic
Removing linux-image-3.2.0-67-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-67-generic /boot/vmlinuz-3.2.0-67-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-67-generic /boot/vmlinuz-3.2.0-67-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-67-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-67-generic /boot/vmlinuz-3.2.0-67-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.2.0-80-generic
Found initrd image: /boot/initrd.img-3.2.0-80-generic
Found linux image: /boot/vmlinuz-3.2.0-79-generic
Found initrd image: /boot/initrd.img-3.2.0-79-generic
Found linux image: /boot/vmlinuz-3.2.0-77-generic
Found initrd image: /boot/initrd.img-3.2.0-77-generic
Found linux image: /boot/vmlinuz-3.2.0-76-generic
Found initrd image: /boot/initrd.img-3.2.0-76-generic
Found linux image: /boot/vmlinuz-3.2.0-75-generic
Found initrd image: /boot/initrd.img-3.2.0-75-generic
Found linux image: /boot/vmlinuz-3.2.0-74-generic
Found initrd image: /boot/initrd.img-3.2.0-74-generic
Found linux image: /boot/vmlinuz-3.2.0-72-generic
Found initrd image: /boot/initrd.img-3.2.0-72-generic
Found linux image: /boot/vmlinuz-3.2.0-70-generic
Found initrd image: /boot/initrd.img-3.2.0-70-generic
Found linux image: /boot/vmlinuz-3.2.0-69-generic
Found initrd image: /boot/initrd.img-3.2.0-69-generic
Found linux image: /boot/vmlinuz-3.2.0-68-generic
Found initrd image: /boot/initrd.img-3.2.0-68-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sdb1
Found Ubuntu 10.04.4 LTS (10.04) on /dev/sdc1
done
Purging configuration files for linux-image-3.2.0-67-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-67-generic /boot/vmlinuz-3.2.0-67-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-67-generic /boot/vmlinuz-3.2.0-67-generic
Removing linux-image-3.2.0-68-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-68-generic /boot/vmlinuz-3.2.0-68-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-68-generic /boot/vmlinuz-3.2.0-68-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-68-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-68-generic /boot/vmlinuz-3.2.0-68-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.2.0-80-generic
Found initrd image: /boot/initrd.img-3.2.0-80-generic
Found linux image: /boot/vmlinuz-3.2.0-79-generic
Found initrd image: /boot/initrd.img-3.2.0-79-generic
Found linux image: /boot/vmlinuz-3.2.0-77-generic
Found initrd image: /boot/initrd.img-3.2.0-77-generic
Found linux image: /boot/vmlinuz-3.2.0-76-generic
Found initrd image: /boot/initrd.img-3.2.0-76-generic
Found linux image: /boot/vmlinuz-3.2.0-75-generic
Found initrd image: /boot/initrd.img-3.2.0-75-generic
Found linux image: /boot/vmlinuz-3.2.0-74-generic
Found initrd image: /boot/initrd.img-3.2.0-74-generic
Found linux image: /boot/vmlinuz-3.2.0-72-generic
Found initrd image: /boot/initrd.img-3.2.0-72-generic
Found linux image: /boot/vmlinuz-3.2.0-70-generic
Found initrd image: /boot/initrd.img-3.2.0-70-generic
Found linux image: /boot/vmlinuz-3.2.0-69-generic
Found initrd image: /boot/initrd.img-3.2.0-69-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sdb1
Found Ubuntu 10.04.4 LTS (10.04) on /dev/sdc1
done
Purging configuration files for linux-image-3.2.0-68-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-68-generic /boot/vmlinuz-3.2.0-68-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-68-generic /boot/vmlinuz-3.2.0-68-generic
Removing linux-image-3.2.0-69-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-69-generic /boot/vmlinuz-3.2.0-69-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-69-generic /boot/vmlinuz-3.2.0-69-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-69-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-69-generic /boot/vmlinuz-3.2.0-69-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.2.0-80-generic
Found initrd image: /boot/initrd.img-3.2.0-80-generic
Found linux image: /boot/vmlinuz-3.2.0-79-generic
Found initrd image: /boot/initrd.img-3.2.0-79-generic
Found linux image: /boot/vmlinuz-3.2.0-77-generic
Found initrd image: /boot/initrd.img-3.2.0-77-generic
Found linux image: /boot/vmlinuz-3.2.0-76-generic
Found initrd image: /boot/initrd.img-3.2.0-76-generic
Found linux image: /boot/vmlinuz-3.2.0-75-generic
Found initrd image: /boot/initrd.img-3.2.0-75-generic
Found linux image: /boot/vmlinuz-3.2.0-74-generic
Found initrd image: /boot/initrd.img-3.2.0-74-generic
Found linux image: /boot/vmlinuz-3.2.0-72-generic
Found initrd image: /boot/initrd.img-3.2.0-72-generic
Found linux image: /boot/vmlinuz-3.2.0-70-generic
Found initrd image: /boot/initrd.img-3.2.0-70-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sdb1
Found Ubuntu 10.04.4 LTS (10.04) on /dev/sdc1
done
Purging configuration files for linux-image-3.2.0-69-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-69-generic /boot/vmlinuz-3.2.0-69-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-69-generic /boot/vmlinuz-3.2.0-69-generic
Removing linux-image-3.2.0-70-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-70-generic /boot/vmlinuz-3.2.0-70-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-70-generic /boot/vmlinuz-3.2.0-70-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-70-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-70-generic /boot/vmlinuz-3.2.0-70-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.2.0-80-generic
Found initrd image: /boot/initrd.img-3.2.0-80-generic
Found linux image: /boot/vmlinuz-3.2.0-79-generic
Found initrd image: /boot/initrd.img-3.2.0-79-generic
Found linux image: /boot/vmlinuz-3.2.0-77-generic
Found initrd image: /boot/initrd.img-3.2.0-77-generic
Found linux image: /boot/vmlinuz-3.2.0-76-generic
Found initrd image: /boot/initrd.img-3.2.0-76-generic
Found linux image: /boot/vmlinuz-3.2.0-75-generic
Found initrd image: /boot/initrd.img-3.2.0-75-generic
Found linux image: /boot/vmlinuz-3.2.0-74-generic
Found initrd image: /boot/initrd.img-3.2.0-74-generic
Found linux image: /boot/vmlinuz-3.2.0-72-generic
Found initrd image: /boot/initrd.img-3.2.0-72-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sdb1
Found Ubuntu 10.04.4 LTS (10.04) on /dev/sdc1
done
Purging configuration files for linux-image-3.2.0-70-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-70-generic /boot/vmlinuz-3.2.0-70-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-70-generic /boot/vmlinuz-3.2.0-70-generic
Removing linux-image-3.2.0-72-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-72-generic /boot/vmlinuz-3.2.0-72-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-72-generic /boot/vmlinuz-3.2.0-72-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-72-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-72-generic /boot/vmlinuz-3.2.0-72-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.2.0-80-generic
Found initrd image: /boot/initrd.img-3.2.0-80-generic
Found linux image: /boot/vmlinuz-3.2.0-79-generic
Found initrd image: /boot/initrd.img-3.2.0-79-generic
Found linux image: /boot/vmlinuz-3.2.0-77-generic
Found initrd image: /boot/initrd.img-3.2.0-77-generic
Found linux image: /boot/vmlinuz-3.2.0-76-generic
Found initrd image: /boot/initrd.img-3.2.0-76-generic
Found linux image: /boot/vmlinuz-3.2.0-75-generic
Found initrd image: /boot/initrd.img-3.2.0-75-generic
Found linux image: /boot/vmlinuz-3.2.0-74-generic
Found initrd image: /boot/initrd.img-3.2.0-74-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sdb1
Found Ubuntu 10.04.4 LTS (10.04) on /dev/sdc1
done
Purging configuration files for linux-image-3.2.0-72-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-72-generic /boot/vmlinuz-3.2.0-72-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-72-generic /boot/vmlinuz-3.2.0-72-generic
Removing linux-image-3.2.0-74-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-74-generic /boot/vmlinuz-3.2.0-74-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-74-generic /boot/vmlinuz-3.2.0-74-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-74-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-74-generic /boot/vmlinuz-3.2.0-74-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.2.0-80-generic
Found initrd image: /boot/initrd.img-3.2.0-80-generic
Found linux image: /boot/vmlinuz-3.2.0-79-generic
Found initrd image: /boot/initrd.img-3.2.0-79-generic
Found linux image: /boot/vmlinuz-3.2.0-77-generic
Found initrd image: /boot/initrd.img-3.2.0-77-generic
Found linux image: /boot/vmlinuz-3.2.0-76-generic
Found initrd image: /boot/initrd.img-3.2.0-76-generic
Found linux image: /boot/vmlinuz-3.2.0-75-generic
Found initrd image: /boot/initrd.img-3.2.0-75-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sdb1
Found Ubuntu 10.04.4 LTS (10.04) on /dev/sdc1
done
Purging configuration files for linux-image-3.2.0-74-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-74-generic /boot/vmlinuz-3.2.0-74-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-74-generic /boot/vmlinuz-3.2.0-74-generic
Removing linux-image-3.2.0-75-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-75-generic /boot/vmlinuz-3.2.0-75-generic
dkms: removing: vboxhost 4.1.36 (3.2.0-75-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 4.1.36
Kernel:  3.2.0-75-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-75-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-75-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-75-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-75-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-75-generic /boot/vmlinuz-3.2.0-75-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-75-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-75-generic /boot/vmlinuz-3.2.0-75-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.2.0-80-generic
Found initrd image: /boot/initrd.img-3.2.0-80-generic
Found linux image: /boot/vmlinuz-3.2.0-79-generic
Found initrd image: /boot/initrd.img-3.2.0-79-generic
Found linux image: /boot/vmlinuz-3.2.0-77-generic
Found initrd image: /boot/initrd.img-3.2.0-77-generic
Found linux image: /boot/vmlinuz-3.2.0-76-generic
Found initrd image: /boot/initrd.img-3.2.0-76-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sdb1
Found Ubuntu 10.04.4 LTS (10.04) on /dev/sdc1
done
Purging configuration files for linux-image-3.2.0-75-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-75-generic /boot/vmlinuz-3.2.0-75-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-75-generic /boot/vmlinuz-3.2.0-75-generic
Removing linux-image-3.2.0-76-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-76-generic /boot/vmlinuz-3.2.0-76-generic
dkms: removing: vboxhost 4.1.36 (3.2.0-76-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 4.1.36
Kernel:  3.2.0-76-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-76-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-76-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-76-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-76-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-76-generic /boot/vmlinuz-3.2.0-76-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-76-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-76-generic /boot/vmlinuz-3.2.0-76-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.2.0-80-generic
Found initrd image: /boot/initrd.img-3.2.0-80-generic
Found linux image: /boot/vmlinuz-3.2.0-79-generic
Found initrd image: /boot/initrd.img-3.2.0-79-generic
Found linux image: /boot/vmlinuz-3.2.0-77-generic
Found initrd image: /boot/initrd.img-3.2.0-77-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sdb1
Found Ubuntu 10.04.4 LTS (10.04) on /dev/sdc1
done
Purging configuration files for linux-image-3.2.0-76-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-76-generic /boot/vmlinuz-3.2.0-76-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-76-generic /boot/vmlinuz-3.2.0-76-generic
Removing linux-image-3.2.0-77-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-77-generic /boot/vmlinuz-3.2.0-77-generic
dkms: removing: vboxhost 4.1.36 (3.2.0-77-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 4.1.36
Kernel:  3.2.0-77-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-77-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-77-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-77-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-77-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-77-generic /boot/vmlinuz-3.2.0-77-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-77-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-77-generic /boot/vmlinuz-3.2.0-77-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.2.0-80-generic
Found initrd image: /boot/initrd.img-3.2.0-80-generic
Found linux image: /boot/vmlinuz-3.2.0-79-generic
Found initrd image: /boot/initrd.img-3.2.0-79-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sdb1
Found Ubuntu 10.04.4 LTS (10.04) on /dev/sdc1
done
Purging configuration files for linux-image-3.2.0-77-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-77-generic /boot/vmlinuz-3.2.0-77-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-77-generic /boot/vmlinuz-3.2.0-77-generic
Removing linux-image-3.2.0-79-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-79-generic /boot/vmlinuz-3.2.0-79-generic
dkms: removing: vboxhost 4.1.36 (3.2.0-79-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 4.1.36
Kernel:  3.2.0-79-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-79-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-79-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-79-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-79-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-79-generic /boot/vmlinuz-3.2.0-79-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-79-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-79-generic /boot/vmlinuz-3.2.0-79-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.2.0-80-generic
Found initrd image: /boot/initrd.img-3.2.0-80-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sdb1
Found Ubuntu 10.04.4 LTS (10.04) on /dev/sdc1
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-3.2.0-79-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-79-generic /boot/vmlinuz-3.2.0-79-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-79-generic /boot/vmlinuz-3.2.0-79-generic
tony@tony-desktop:~$ 

```

if its ok...

how do I remove the header files

Thanks

---

### Post by matt_symes on 2015-04-23
Hi

That's worked. You now have only two kernels left (.29 and .80).

To remove the headers, open a terminal and type.

```
sudo apt-get purge "^linux-headers-3.2.0-[3-7].*$"
```

Did you remove the .29 headers ?

Can you post the output of

```
ls /usr/src/linux-headers-3.2.0-29* | wc -l
```

> There were some differences ( removing vboxhost) ? with kernels 3.2.0-75  to 79 and kernel 3.2.0-79 also had some bad symbolic links   (vmlinuz.old  and  /initrd.img.old

We'll take a look at that after.

Kind regards

---

### Post by ibod on 2015-04-25
Hi Matt,

All the leaders 30 - 79 removed ok no errors 

Looks like the .29 headers were removed before while I was poking around

```

tony@tony-desktop:~$ ls /usr/src/linux-headers-3.2.0-29* | wc -l
55 
tony@tony-desktop:~$

```

What is the "55" response ? 

Would also like to understand the differences from earlier ( removing vboxhost) with kernels 3.2.0-75   to 79 and kernel 3.2.0-79 also had some bad symbolic links    (vmlinuz.old  and  /initrd.img.old

Thanks

---

### Post by matt_symes on 2015-04-25
Hi

> **ibod said:**
> Hi Matt,

All the leaders 30 - 79 removed ok no errors 

Yep. It looks great.

> Looks like the .29 headers were removed before while I was poking around

```

tony@tony-desktop:~$ ls /usr/src/linux-headers-3.2.0-29* | wc -l
55 
tony@tony-desktop:~$

```

What is the "55" response ? 


The .29 headers were not removed and that is no problem. The 55 is the number of lines returned from the command *ls /usr/src/linux-headers-3.2.0-29**. Anything less than 3 or so would have shown that the headers had been removed. I did not need to know the files in those folders so getting the count of the number of lines was sufficient to give me the information i needed.

> Would also like to understand the differences from earlier ( removing vboxhost) with kernels 3.2.0-75   to 79 and kernel 3.2.0-79 also had some bad symbolic links    (vmlinuz.old  and  /initrd.img.old

Thanks

Virtual box builds some kernel modules using dkms everytime you install a kernel or when you first install virtual box. I suspect that you got the vboxhost messages for kernels installed during and after you installed virtual box. Kernels installed before you installed vbox would have not needed to build any virtual box modules, hence no vboxhost messages. That's my supposition anyway.

The symbolic links should point to the last kernel. They are not absolutely required but if you want to fix them then open a terminal and copy and paste this into it.

```
sudo rm /vmlinuz.old
sudo rm /initrd.img.old
sudo ln -s /boot/vmlinuz-3.2.0-29-generic /vmlinuz.old
sudo ln -s /boot/initrd.img-3.2.0-29-generic /initrd.img.old
```

If either/both of the first two commands error, don't worry, just continue with the rest, as i'm not 100% sure if the bad symlinks are still on your system or not.

Kind regards

---

### Post by ibod on 2015-05-07
Hi Matt,

The last 4 commands worked fine.

Thanks for all the help and explanations, it looks like all is good now.

I will close this thread tomorrow unless there is anything else you think we need to do.

---

