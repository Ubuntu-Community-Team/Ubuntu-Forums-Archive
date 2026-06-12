---
title: "Unable to run update"
date: 2022-07-06
forum: General Help
---

### Post by satimis on 2022-07-06
Hi all,

This is a spare PC
OS - Ubuntu 20.04 desktop
It hasn't be run for sometimes

$ sudo apt update```

Ign:1 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal InRelease
Hit:2 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal Release
Hit:3 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:4 http://download.virtualbox.org/virtualbox/debian focal InRelease                                                        
Media change: please insert the disc labeled                                                                                  
 'Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1)'
in the drive '/media/cdrom/' and press [Enter]

```

On screen top-bar I couldn't find ubuntu software center.

Please advise how to fix the problem.

Thanks in advance

Regards

---

### Post by #&amp;thj^% on 2022-07-06
:D
Just remove the cdrom entry from the sources.list file. This can be done easily:

```
sudo sed -i '/cdrom/d' /etc/apt/sources.list
```

This should take care of the problem. The message is because somehow you still have the cdrom entry in your sources.list file, you can check the content of the file using:

```
grep -v '#' /etc/apt/sources.list
```

This will show you all the repositories you have activated.

---

### Post by satimis on 2022-07-06
> **1fallen said:**
> :D
Just remove the cdrom entry from the sources.list file. This can be done easily:

```
sudo sed -i '/cdrom/d' /etc/apt/sources.list
```

This should take care of the problem. The message is because somehow you still have the cdrom entry in your sources.list file, you can check the content of the file using:

```
grep -v '#' /etc/apt/sources.list
```

This will show you all the repositories you have activated.
Thanks for your advice.

$ sudo sed -i '/cdrom/d' /etc/apt/sources.list
[sudo] password for satimis: 
No password can work ????

$ grep -v '#' /etc/apt/sources.list```


deb http://hk.archive.ubuntu.com/ubuntu/ focal main restricted

deb http://hk.archive.ubuntu.com/ubuntu/ focal-updates main restricted

deb http://hk.archive.ubuntu.com/ubuntu/ focal universe
deb http://hk.archive.ubuntu.com/ubuntu/ focal-updates universe

deb http://hk.archive.ubuntu.com/ubuntu/ focal multiverse
deb http://hk.archive.ubuntu.com/ubuntu/ focal-updates multiverse

deb http://hk.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu focal-security main restricted
deb http://security.ubuntu.com/ubuntu focal-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse

deb [arch=amd64] http://download.virtualbox.org/virtualbox/debian focal contrib

```

Regards

Edit
===

$ sudo apt update```

Hit:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://security.ubuntu.com/ubuntu focal-security InRelease
Hit:3 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu focal InRelease     
Hit:4 http://hk.archive.ubuntu.com/ubuntu focal InRelease                      
Hit:5 http://ppa.launchpad.net/inkscape.dev/stable/ubuntu focal InRelease  
Hit:6 http://hk.archive.ubuntu.com/ubuntu focal-updates InRelease
Hit:7 http://hk.archive.ubuntu.com/ubuntu focal-backports InRelease        
Hit:8 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu focal InRelease
Hit:9 http://ppa.launchpad.net/tomtomtom/woeusb/ubuntu focal InRelease
Hit:10 http://download.virtualbox.org/virtualbox/debian focal InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

```

It is very strange to me?

---

### Post by #&amp;thj^% on 2022-07-06
How's the "update command now"?
EDIT: just noticed this>>"No password can work ????"
Did it work before? nothing we did here should have caused that.
EDIT 2:
```
~$ sudo sed -i '/cdrom/d' /etc/apt/sources.list
me@me-Standard-PC-Q35-ICH9-2009:~$ grep -v '#' /etc/apt/sources.list

deb http://ca.archive.ubuntu.com/ubuntu/ jammy main restricted

deb http://ca.archive.ubuntu.com/ubuntu/ jammy-updates main restricted

deb http://ca.archive.ubuntu.com/ubuntu/ jammy universe
deb http://ca.archive.ubuntu.com/ubuntu/ jammy-updates universe

deb http://ca.archive.ubuntu.com/ubuntu/ jammy multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ jammy-updates multiverse

deb http://ca.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu jammy-security main restricted
deb http://security.ubuntu.com/ubuntu jammy-security universe
deb http://security.ubuntu.com/ubuntu jammy-security multiverse


```
And: 
```
me@me-Standard-PC-Q35-ICH9-2009:~$ sudo apt update
Get:1 https://dl.google.com/linux/chrome/deb stable InRelease [1,811 B]
Get:2 https://dl.google.com/linux/chrome/deb stable/main amd64 Packages [1,093 B]
Get:3 https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease [7,426 B]
Get:4 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]      
Get:5 https://esm.ubuntu.com/infra/ubuntu jammy-infra-updates InRelease [7,425 B]
Hit:6 http://ca.archive.ubuntu.com/ubuntu jammy InRelease                      
Get:7 http://ca.archive.ubuntu.com/ubuntu jammy-updates InRelease [114 kB]     
Get:8 http://ca.archive.ubuntu.com/ubuntu jammy-backports InRelease [99.8 kB]  
Get:9 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy InRelease [23.8 kB]
Get:10 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages [151 kB]
Get:11 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [340 kB]
Get:12 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main Translation-en [85.7 kB]
Get:13 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 DEP-11 Metadata [91.0 kB]
Get:14 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 c-n-f Metadata [6,172 B]
Get:15 http://ca.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages [215 kB]
Get:16 http://ca.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [141 kB]
Get:17 http://ca.archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages [70.1 kB]
Get:18 http://ca.archive.ubuntu.com/ubuntu jammy-updates/universe Translation-en [50.8 kB]
Get:19 http://ca.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 DEP-11 Metadata [94.8 kB]
Get:20 http://ca.archive.ubuntu.com/ubuntu jammy-updates/universe DEP-11 48x48 Icons [38.0 kB]
Get:21 http://ca.archive.ubuntu.com/ubuntu jammy-updates/universe DEP-11 64x64 Icons [50.5 kB]
Get:22 http://ca.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 c-n-f Metadata [2,960 B]
Get:23 http://ca.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 Packages [7,032 B]
Get:24 http://ca.archive.ubuntu.com/ubuntu jammy-updates/multiverse i386 Packages [1,460 B]
Get:25 http://ca.archive.ubuntu.com/ubuntu jammy-updates/multiverse Translation-en [2,112 B]
Get:26 http://ca.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 DEP-11 Metadata [940 B]
Get:27 http://ca.archive.ubuntu.com/ubuntu jammy-updates/multiverse DEP-11 48x48 Icons [1,867 B]
Get:28 http://ca.archive.ubuntu.com/ubuntu jammy-updates/multiverse DEP-11 64x64 Icons [2,497 B]
Get:29 http://ca.archive.ubuntu.com/ubuntu jammy-updates/multiverse DEP-11 64x64@2 Icons [29 B]
Get:30 http://ca.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 c-n-f Metadata [420 B]
Get:31 http://security.ubuntu.com/ubuntu jammy-security/main i386 Packages [68.4 kB]
Get:32 http://ca.archive.ubuntu.com/ubuntu jammy-backports/universe i386 Packages [3,840 B]
Get:33 http://ca.archive.ubuntu.com/ubuntu jammy-backports/universe amd64 Packages [5,404 B]
Get:34 http://ca.archive.ubuntu.com/ubuntu jammy-backports/universe Translation-en [8,160 B]
Get:35 http://ca.archive.ubuntu.com/ubuntu jammy-backports/universe amd64 DEP-11 Metadata [12.5 kB]
Get:36 http://ca.archive.ubuntu.com/ubuntu jammy-backports/universe amd64 c-n-f Metadata [236 B]
Get:37 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages [197 kB]
Get:38 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy InRelease [23.9 kB]
Get:39 http://security.ubuntu.com/ubuntu jammy-security/main Translation-en [48.8 kB]
Get:40 http://security.ubuntu.com/ubuntu jammy-security/main amd64 DEP-11 Metadata [11.4 kB]
Get:41 http://security.ubuntu.com/ubuntu jammy-security/main amd64 c-n-f Metadata [3,336 B]
Get:42 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 Packages [177 kB]
Get:43 http://security.ubuntu.com/ubuntu jammy-security/restricted Translation-en [26.2 kB]
Get:44 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 Packages [79.6 kB]
Get:45 http://security.ubuntu.com/ubuntu jammy-security/universe i386 Packages [36.2 kB]
Get:46 http://security.ubuntu.com/ubuntu jammy-security/universe Translation-en [28.4 kB]
Get:47 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 DEP-11 Metadata [608 B]
Get:48 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 c-n-f Metadata [1,700 B]
Get:49 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main i386 Packages [2,200 B]
Get:50 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main amd64 Packages [33.8 kB]
Get:51 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main amd64 Packages [92.5 kB]
Get:52 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main i386 Packages [23.1 kB]
Get:53 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main Translation-en [28.7 kB]
Fetched 2,632 kB in 7s (366 kB/s)                                              

** (appstreamcli:5064): WARNING **: 09:16:11.586: Found icon of unknown type 'unknown' in 'system/flatpak/flatpak/cc.nift.nsm/*', skipping it.

** (appstreamcli:5064): WARNING **: 09:16:11.586: Found icon of unknown type 'unknown' in 'system/flatpak/flatpak/cc.nift.nsm/*', skipping it.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
36 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

---

### Post by satimis on 2022-07-06
> **1fallen said:**
> How's the "update command now"?

$ sudo apt update```

Hit:1 http://download.virtualbox.org/virtualbox/debian focal InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:3 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu focal InRelease     
Hit:4 http://hk.archive.ubuntu.com/ubuntu focal InRelease           
Hit:5 http://security.ubuntu.com/ubuntu focal-security InRelease           
Hit:6 http://hk.archive.ubuntu.com/ubuntu focal-updates InRelease          
Hit:7 http://ppa.launchpad.net/inkscape.dev/stable/ubuntu focal InRelease  
Hit:8 http://hk.archive.ubuntu.com/ubuntu focal-backports InRelease
Hit:9 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu focal InRelease
Hit:10 http://ppa.launchpad.net/tomtomtom/woeusb/ubuntu focal InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

```
It is quite strange to me

Regards

---

### Post by #&amp;thj^% on 2022-07-06
Those mysterious little Gremlins, that's my story....LOL

---

### Post by satimis on 2022-07-06
> **1fallen said:**
> Those mysterious little Gremlins, that's my story....LOL
This Ubuntu 20.04 desktop is the host of Oracle VirtualBox.  There are Ubuntu 20.04 VMs running here.  I'm now doing update/upgrade on them.  There are many packages to be upgraded.

It is because there is problem running GIMP on my daily working PC.  I dig this spare PC out.  LinuxMint and Debian are running as VMs on the PC.  I'm prepared testing GIMP on them.

Regards

---

