---
title: "Problems with apt and strange install with aptitude?"
date: 2006-12-28
forum: General Help
---

### Post by Hellaxe on 2006-12-28
Hello people:
i'm having a strange error when i try to install the nvidia-glx package as you can see:
```
sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvidia-glx: Depends: libglu1-mesa but it is not going to be installed or
                       libglu1
E: Broken packages
```

Every one else is installing it with the same repos i'm using.

But when i use **aptitude** i get a strange report of what it needs to install to manage the dependencies:
```
The following NEW packages will be automatically installed:
  binutils-static linux-image-2.6.17-10-386 
  linux-restricted-modules-2.6.17-10-386 linux-restricted-modules-common 
  nvidia-kernel-common xserver-xorg-core xserver-xorg-input-all 
  xserver-xorg-input-elographics xserver-xorg-input-evdev 
  xserver-xorg-input-kbd xserver-xorg-input-mouse 
  xserver-xorg-input-synaptics xserver-xorg-input-wacom 
The following NEW packages will be installed:
  binutils-static linux-image-2.6.17-10-386 
  linux-restricted-modules-2.6.17-10-386 linux-restricted-modules-common 
  nvidia-glx nvidia-kernel-common xserver-xorg-core xserver-xorg-input-all 
  xserver-xorg-input-elographics xserver-xorg-input-evdev 
  xserver-xorg-input-kbd xserver-xorg-input-mouse 
  xserver-xorg-input-synaptics xserver-xorg-input-wacom 
0 packages upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 35.3MB/39.6MB of archives. After unpacking 113MB will be used.
The following packages have unmet dependencies:
  libgl1-mesa-swx11: Conflicts: nvidia-glx but 1.0.9631+2.6.17.8-1 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
xorg-driver-fglrx [7.1.0-8.30.3+2.6.17.8-1 (<NULL>)]

Keep the following packages at their current version:
nvidia-glx [Not Installed]
```

Why the hell does it need to install the kernel image 386? And that xorg packages?
For me this is wierd.

I'm using Edgy in this box.

Thanks.

---

### Post by bapoumba on 2006-12-28
```
~ $ sudo aptitude install --simulate nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  binutils-static linux-image-2.6.17-10-386 
  linux-restricted-modules-2.6.17-10-386 linux-restricted-modules-common 
  nvidia-kernel-common 
The following NEW packages will be installed:
  binutils-static linux-image-2.6.17-10-386 
  linux-restricted-modules-2.6.17-10-386 linux-restricted-modules-common 
  nvidia-glx nvidia-kernel-common 
0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 35.4MB of archives. After unpacking 101MB will be used.
Do you want to continue? [Y/n/?] n
Abort.

```

Do you have  xserver-xorg-driver-all installed ? (I use nv drivers)

---

### Post by Hellaxe on 2006-12-30
I think so. Everything is working.

---

### Post by finnomenon on 2007-01-15
I get the same errors when I try to install "nvidia-glx"
have been searching for an answer for a while now, but haven't found anything :(

---

### Post by bapoumba on 2007-01-15
Hi,
could you (both) please post the output to **cat /etc/apt/sources.list** ?

---

### Post by finnomenon on 2007-01-15
```
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted 


# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted  

deb http://de.archive.ubuntu.com/ubuntu/ edgy main restricted 
deb-src http://de.archive.ubuntu.com/ubuntu/ edgy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ edgy-updates main restricted  
deb-src http://de.archive.ubuntu.com/ubuntu/ edgy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://de.archive.ubuntu.com/ubuntu/ edgy universe 
deb-src http://de.archive.ubuntu.com/ubuntu/ edgy universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse 
deb-src http://de.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse 

## meins
deb http://de.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse 
deb http://de.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse 

#mehr meins
deb http://flomertens.keo.in/ubuntu/ edgy main main-all testing 

#deluge
deb http://espergreen.com/apt/ edgy main 

deb http://security.ubuntu.com/ubuntu/ edgy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ edgy-security main restricted 
# deb http://security.ubuntu.com/ubuntu/ edgy-security universe 
# deb-src http://security.ubuntu.com/ubuntu/ edgy-security universe 


```

---

### Post by bapoumba on 2007-01-15
I've browser through the two extra repositories from your sources.list, but did not find anything obvious (at least to me) that would mess up with nvidia-glx.
[http://packages.ubuntu.com/edgy/x11/nvidia-glx]("http://packages.ubuntu.com/edgy/x11/nvidia-glx")

Why did you add theses repos for, what did you install from them ?
Can you comment them out and post the output to 

```
sudo aptitude update
sudo aptitude install nvidia-glx
```

---

### Post by finnomenon on 2007-01-15
are you talking about:

```
#mehr meins
deb http://flomertens.keo.in/ubuntu/ edgy main main-all testing 

#deluge
deb http://espergreen.com/apt/ edgy main 
```

??

deluge is a bittorrent client, I can't remember what the other one did.

I commented both out, ran "sudo apt-get update" and tried to install nvidia-glx

gives me the same error as before.

---

### Post by bapoumba on 2007-01-15
Could you please post the complete apt-get error output ?
And may be try with aptitude, the error message may be more informative.

---

### Post by finnomenon on 2007-01-15
sudo aptitude install nvidia-glx

it said "something broken"
asked me if solution was ok, I answered yes.
and it magically fixed everything :)

nvidia-glx now installed.
thanks bapoumba

---

### Post by bapoumba on 2007-01-15
aptitude's magic ;)

---

