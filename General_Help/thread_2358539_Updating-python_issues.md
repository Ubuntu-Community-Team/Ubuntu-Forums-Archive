---
title: "Updating-python issues"
date: 2017-04-14
forum: General Help
---

### Post by DougieFresh4U on 2017-04-14
Using Zesty
while updating I am getting errors:
```
The following packages will be upgraded: 
  xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-libinput xserver-xorg-input-synaptics xserver-xorg-input-wacom 
  xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-mach64 
  xserver-xorg-video-nouveau xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-vesa 
  xserver-xorg-video-vmware 
The following partially installed packages will be configured:
  apt-xapian-index{b} 
16 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/2,859 kB of archives. After unpacking 22.5 kB will be used.
The following packages have unmet dependencies:
 apt-xapian-index : Depends: python3-xapian (>= 1.4.3-1) but it is not going to be installed
 xserver-xorg-input-vmmouse : Depends: xorg-input-abi-22 which is a virtual package, provided by:
                                       - xserver-xorg-core (2:1.18.4-1ubuntu9), but 2:1.19.3-1ubuntu1 is to be installed

The following actions will resolve these dependencies:

     Remove the following packages:                        
1)     xserver-xorg-input-vmmouse [1:13.1.0-1ubuntu2 (now)]

     Install the following packages:                       
2)     python3-xapian [1.4.3-1 (zesty)]                    



Accept this solution? [Y/n/q/?] Y
The following NEW packages will be installed:
  python3-xapian{a} 
The following packages will be REMOVED:
  xserver-xorg-input-vmmouse{a} 
The following packages will be upgraded:
  xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-libinput xserver-xorg-input-synaptics xserver-xorg-input-wacom 
  xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-mach64 
  xserver-xorg-video-nouveau xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-vesa 
  xserver-xorg-video-vmware 
The following partially installed packages will be configured:
  apt-xapian-index 
16 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0 B/3,322 kB of archives. After unpacking 3,603 kB will be used.
Do you want to continue? [Y/n/?] Y
(Reading database ... 665694 files and directories currently installed.)
Preparing to unpack .../python3-xapian_1.4.3-1_amd64.deb ...
Unpacking python3-xapian (1.4.3-1) ...
dpkg: error processing archive /var/cache/apt/archives/python3-xapian_1.4.3-1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/python3/dist-packages/xapian/__init__.py', which is also in package python3-xapian1.3 1.3.4-0ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/python3-xapian_1.4.3-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
dpkg: dependency problems prevent configuration of apt-xapian-index:
 apt-xapian-index depends on python3-xapian (>= 1.4.3-1); however:
  Package python3-xapian is not installed.
  Version of python3-xapian on system, provided by python3-xapian1.3:amd64, is <none>.

dpkg: error processing package apt-xapian-index (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.24-9ubuntu2) ...
Errors were encountered while processing:
 apt-xapian-index


```
Not sure what is going on and it has been a while since I've had to 'tinker' with my system!

Sorry, never mind as I think I sorted out.

---

### Post by eldados2 on 2017-04-15
Hey mate
I have the same issue here, how did you resolve yours?
cheers

---

### Post by keiser-stigandr on 2017-04-18
Hi
I had the same problem and I solved it by removing the old "python3-xapian1.3"-package and then installing the new package.

I ran:```
[INDENT]sudo dpkg -r --force-depends python3-xapian1.3 [/INDENT]

```to remove the old package

and then:```
[INDENT]sudo apt --fix-broken install[/INDENT]

```to install the new one.

I hope this helps

---

### Post by eldados2 on 2017-04-19
Thanks mate!
working great :)
(forgot about forcing, been a while)

---

