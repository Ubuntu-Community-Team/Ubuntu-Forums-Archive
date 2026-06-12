---
title: "playonlinux install fail"
date: 2016-02-26
forum: General Help
---

### Post by bizhat on 2016-02-26
When i install playonlinux, i get following error

```

root@hon-pc-01:~# apt-get install playonlinux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 playonlinux : Depends: wine or
                        wine-unstable but it is not installable
E: Unable to correct problems, you have held broken packages.
root@hon-pc-01:~# 

```

I am using ubuntu 14.04

```

root@hon-pc-01:~# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty
root@hon-pc-01:~# uname -a
Linux hon-pc-01 3.13.0-79-generic #123-Ubuntu SMP Fri Feb 19 14:27:58 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
root@hon-pc-01:~# 

```

I have following wine package available

```

root@hon-pc-01:~# apt-cache search wine
playonlinux - front-end for Wine
wine-gecko2.21 - Microsoft Windows compatibility layer (embedded web browser)
wine-mono0.0.8 - Microsoft Windows compatibility layer (.NET compatibility)
gnome-colors - set of GNOME icon themes
gnome-exe-thumbnailer - Wine .exe and other executable thumbnailer for Gnome
gnome-wine-icon-theme - red variation of the GNOME-Colors icon theme
innoextract - Tool for extracting data from an Inno Setup installer
libkwineffects1abi4 - library used by effects for the KDE window manager
libwine-gecko-2.21 - Windows API implementation - web browser module
libwine-gecko-dbg-2.21 - Windows API implementation - web browser debug build
python-neo - Python IO library for electrophysiological data formats
q4wine - Qt4 GUI for wine (WINE)
shiki-colors - set of Metacity/GTK-2+ themes
shiki-wine-theme - red variation of the Shiki-Colors theme
tellico - Collection manager for books, videos, music, etc
tellico-data - Collection manager for books, videos, music, etc [data]
tellico-doc - Collection manager for books, videos, music, etc [doc]
tellico-scripts - Collection manager for books, videos, music, etc [scripts]
unmass - Extract game archive files
wine - Microsoft Windows Compatibility Layer (meta-package)
wine1.4 - Microsoft Windows Compatibility Layer (dummy package)
wine1.4-amd64 - Microsoft Windows Compatibility Layer (dummy package)
wine1.4-dbg - Microsoft Windows Compatibility Layer (dummy package)
wine1.4-dev - Microsoft Windows Compatibility Layer (dummy package)
wine1.6 - Microsoft Windows Compatibility Layer (Binary Emulator and Library)
wine1.6-amd64 - Microsoft Windows Compatibility Layer (64-bit support)
wine1.6-dbg - Microsoft Windows Compatibility Layer (debugging symbols)
wine1.6-dev - Microsoft Windows Compatibility Layer (Development files)
winefish - LaTeX Editor based on Bluefish
winetricks - Microsoft Windows Compatibility Layer (winetricks)
wine1.4-i386 - Microsoft Windows Compatibility Layer (dummy package)
wine1.6-i386 - Microsoft Windows Compatibility Layer (32-bit support)
twine - utility for interacting with PyPI
root@hon-pc-01:~# 

```

How i fix this problem ?

Thanks,

Boby

---

### Post by bizhat on 2016-02-26
I did try to install wine, but can't get it installed for some reason

```

boby@hon-pc-01:~ $ sudo apt-get install wine
[sudo] password for boby: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
boby@hon-pc-01:~ $ sudo apt-get install wine1.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.6 : Depends: wine1.6-amd64 (= 1:1.6.2-0ubuntu4) but it is not going to be installed
           Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu4)
           Recommends: winbind but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
boby@hon-pc-01:~ $ sudo apt-get install wine1.6-amd64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.6-amd64 : Depends: wine1.6:any (= 1:1.6.2-0ubuntu4)
E: Unable to correct problems, you have held broken packages.
boby@hon-pc-01:~ $ 

```

---

### Post by bizhat on 2016-02-28
I found the problem is with my GPU driver (NVIDIA GTX 750 TI). 

> 
boby@hon-pc-01:~ $ glxinfo | grep -i opengl
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTX 750 Ti/PCIe/SSE2
OpenGL core profile version string: 4.3.0 NVIDIA 361.28
OpenGL core profile shading language version string: 4.30 NVIDIA via Cg compiler
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.5.0 NVIDIA 361.28
OpenGL shading language version string: 4.50 NVIDIA
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
boby@hon-pc-01:~ $ 


Is it possible for me to install from source ?

---

