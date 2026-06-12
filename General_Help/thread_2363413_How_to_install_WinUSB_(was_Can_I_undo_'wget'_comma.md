---
title: "How to install WinUSB? (was Can I undo 'wget' command?)"
date: 2017-06-09
forum: General Help
---

### Post by dommel2002 on 2017-06-09
Hello, I am new here and I got stuck in the following issue:

In order to install WinUSB on Ubuntu 16.04 (64 bit) I referred to this website:
[https://itsfoss.com/install-winusb-in-ubuntu-14-04/](https://itsfoss.com/install-winusb-in-ubuntu-14-04/)

Unfortunately, I installed these two dependencies at the same time (I wasn't concentrating) using following commands:[B]
wget [https://launchpad.net/~colingille/+archive/freshlight/+files/winusb_1.0.11+saucy1_i386.deb](https://launchpad.net/~colingille/+archive/freshlight/+files/winusb_1.0.11+saucy1_i386.deb) [/B](for 32 bit)

and **wget [https://launchpad.net/~colingille/+archive/freshlight/+files/winusb_1.0.11+saucy1_amd64.deb](https://launchpad.net/~colingille/+archive/freshlight/+files/winusb_1.0.11+saucy1_amd64.deb) **(for 64 bit)

Now I cannot proceed with **sudo dpkg -i winusb* **which gives the following output:

```
dpkg-split: error: error reading winusb-1.0.11: Is a directory
dpkg:../../src/unpack.c:123:deb_reassemble: internal error: unexpected exit status 2 from dpkg-split
Aborted (core dumped)


```Is it possible to uninstall the first dependency?
I would be glad for any help!!!

---

### Post by monkeybrain20122 on 2017-06-09
The wget command just downloads the files from the url, it doesn't install anything, so there is nothing to undo, you just delete the downloaded files. But those two files you downloaded are very outdated since they are from saucy's archive (Ubuntu 13.10, long expired) You should just install it from 16.04's repository, it is there, I just checked.

```
sudo apt install winusb
```

You error seems to due to the fact that you have a directory called winusb-1.0.11, which is not a .deb.

---

### Post by dommel2002 on 2017-06-10
Sorry but this doesn't work for me:
output:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package winusb
```

---

### Post by howefield on 2017-06-10
> **dommel2002 said:**
> E: Unable to locate package winusb

There is no such package in the Xenial repositories.

---

### Post by dommel2002 on 2017-06-10
So how can I get winusb installed?

---

### Post by howefield on 2017-06-10
> **dommel2002 said:**
> So how can I get winusb installed?

I can't warrant it or endorse it but the tutorial [here]("https://onetransistor.blogspot.co.uk/2016/04/install-winusb-on-ubuntu-1604-lts.html") appears to work.

Basically, download the source code, create the .sh file and run it.

```
cd Downloads
sudo sh winusb.sh
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  python-gi
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  dpkg-dev fakeroot g++ g++-6 gcc-6 libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libasan3 libc-dev-bin
  libc6-dev libcilkrts5 libdrm-dev libfakeroot libgcc-6-dev libgl1-mesa-dev libglu1-mesa-dev libitm1 liblsan0 libmpx2
  libpthread-stubs0-dev libstdc++-6-dev libtsan0 libubsan0 libwxbase3.0-0v5 libwxgtk3.0-0v5 libx11-dev libx11-doc libx11-xcb-dev
  libxau-dev libxcb-dri2-0-dev libxcb-dri3-dev libxcb-glx0-dev libxcb-present-dev libxcb-randr0-dev libxcb-render0-dev libxcb-shape0-dev
  libxcb-sync-dev libxcb-xfixes0-dev libxcb1-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxshmfence-dev libxxf86vm-dev
  linux-libc-dev make manpages-dev mesa-common-dev wx-common wx3.0-headers x11proto-core-dev x11proto-damage-dev x11proto-dri2-dev
  x11proto-fixes-dev x11proto-gl-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev x11proto-xf86vidmode-dev xorg-sgml-doctools
  xtrans-dev
Suggested packages:
  debian-keyring g++-multilib g++-6-multilib gcc-6-doc libstdc++6-6-dbg gcc-multilib autoconf automake libtool flex bison gcc-doc
  gcc-6-multilib gcc-6-locales libgcc1-dbg libgomp1-dbg libitm1-dbg libatomic1-dbg libasan3-dbg liblsan0-dbg libtsan0-dbg libubsan0-dbg
  libcilkrts5-dbg libmpx2-dbg libquadmath0-dbg glibc-doc libstdc++-6-doc wx3.0-doc libxcb-doc libxext-doc make-doc
The following NEW packages will be installed
  build-essential dpkg-dev fakeroot g++ g++-6 gcc gcc-6 libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libasan3
  libc-dev-bin libc6-dev libcilkrts5 libdrm-dev libfakeroot libgcc-6-dev libgl1-mesa-dev libglu1-mesa-dev libitm1 liblsan0 libmpx2
  libpthread-stubs0-dev libstdc++-6-dev libtsan0 libubsan0 libwxbase3.0-0v5 libwxbase3.0-dev libwxgtk3.0-0v5 libwxgtk3.0-dev libx11-dev
  libx11-doc libx11-xcb-dev libxau-dev libxcb-dri2-0-dev libxcb-dri3-dev libxcb-glx0-dev libxcb-present-dev libxcb-randr0-dev
  libxcb-render0-dev libxcb-shape0-dev libxcb-sync-dev libxcb-xfixes0-dev libxcb1-dev libxdamage-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxshmfence-dev libxxf86vm-dev linux-libc-dev make manpages-dev mesa-common-dev wx-common wx3.0-headers x11proto-core-dev
  x11proto-damage-dev x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev
  x11proto-xf86vidmode-dev xorg-sgml-doctools xtrans-dev
0 to upgrade, 67 to newly install, 0 to remove and 4 not to upgrade.
Need to get 37.5 MB of archives.
After this operation, 166 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libc-dev-bin amd64 2.24-9ubuntu2 [68.5 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 linux-libc-dev amd64 4.10.0-22.24 [919 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libc6-dev amd64 2.24-9ubuntu2 [2,274 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libitm1 amd64 7.1.0-6ubuntu2 [27.6 kB]
Get:5 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libasan3 amd64 6.3.0-18ubuntu2 [315 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 liblsan0 amd64 7.1.0-6ubuntu2 [126 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libtsan0 amd64 7.1.0-6ubuntu2 [275 kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libubsan0 amd64 7.1.0-6ubuntu2 [119 kB]
Get:9 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libcilkrts5 amd64 7.1.0-6ubuntu2 [42.4 kB]
Get:10 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libmpx2 amd64 7.1.0-6ubuntu2 [11.7 kB]
Get:11 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libgcc-6-dev amd64 6.3.0-18ubuntu2 [2,311 kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 gcc-6 amd64 6.3.0-18ubuntu2 [7,220 kB]
Get:13 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 gcc amd64 4:6.3.0-2ubuntu1 [5,188 B]
Get:14 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libstdc++-6-dev amd64 6.3.0-18ubuntu2 [1,409 kB]
Get:15 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 g++-6 amd64 6.3.0-18ubuntu2 [7,405 kB]
Get:16 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 g++ amd64 4:6.3.0-2ubuntu1 [1,476 B]                                          
Get:17 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 make amd64 4.1-9.1 [154 kB]                                                   
Get:18 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 dpkg-dev all 1.18.24ubuntu1 [608 kB]                                          
Get:19 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 build-essential amd64 12.1ubuntu2 [4,758 B]                                   
Get:20 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libfakeroot amd64 1.21-1ubuntu2 [25.9 kB]                                     
Get:21 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 fakeroot amd64 1.21-1ubuntu2 [62.2 kB]                                        
Get:22 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libalgorithm-diff-perl all 1.19.03-1 [47.6 kB]                                
Get:23 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libalgorithm-diff-xs-perl amd64 0.04-4build2 [11.1 kB]                        
Get:24 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libalgorithm-merge-perl all 0.08-3 [12.0 kB]                                  
Get:25 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libdrm-dev amd64 2.4.80-1 [230 kB]                                            
Get:26 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 xorg-sgml-doctools all 1:1.11-1 [12.9 kB]                                     
Get:27 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 x11proto-core-dev all 7.0.31-1 [700 kB]                                       
Get:28 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libxau-dev amd64 1:1.0.8-1 [11.1 kB]                                          
Get:29 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libxdmcp-dev amd64 1:1.1.2-3 [25.1 kB]                                        
Get:30 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 x11proto-input-dev all 2.3.2-1 [118 kB]                                       
Get:31 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 x11proto-kb-dev all 1.0.7-1 [226 kB]                                          
Get:32 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 xtrans-dev all 1.3.5-1 [70.5 kB]                                              
Get:33 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libpthread-stubs0-dev amd64 0.3-4 [4,068 B]                                   
Get:34 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libxcb1-dev amd64 1.11.1-1ubuntu1 [74.2 kB]                                   
Get:35 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libx11-dev amd64 2:1.6.4-3 [642 kB]                                           
Get:36 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 mesa-common-dev amd64 17.1.2-1ubuntu1 [498 kB]                                
Get:37 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libx11-xcb-dev amd64 2:1.6.4-3 [9,660 B]                                      
Get:38 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libxcb-dri3-dev amd64 1.11.1-1ubuntu1 [5,752 B]                               
Get:39 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libxcb-render0-dev amd64 1.11.1-1ubuntu1 [15.3 kB]                            
Get:40 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libxcb-randr0-dev amd64 1.11.1-1ubuntu1 [18.2 kB]                             
Get:41 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libxcb-shape0-dev amd64 1.11.1-1ubuntu1 [6,900 B]                             
Get:42 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libxcb-xfixes0-dev amd64 1.11.1-1ubuntu1 [11.2 kB]                            
Get:43 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libxcb-sync-dev amd64 1.11.1-1ubuntu1 [10.1 kB]                               
Get:44 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libxcb-present-dev amd64 1.11.1-1ubuntu1 [6,618 B]                            
Get:45 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libxshmfence-dev amd64 1.2-1 [3,676 B]                                        
Get:46 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libxcb-dri2-0-dev amd64 1.11.1-1ubuntu1 [8,384 B]                             
Get:47 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libxcb-glx0-dev amd64 1.11.1-1ubuntu1 [26.9 kB]                               
Get:48 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 x11proto-xext-dev all 7.3.0-1 [212 kB]                                        
Get:49 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 x11proto-fixes-dev all 1:5.0-2ubuntu2 [14.2 kB]                               
Get:50 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libxfixes-dev amd64 1:5.0.3-1 [11.0 kB]                                       
Get:51 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 x11proto-damage-dev all 1:1.2.1-2 [8,286 B]                                   
Get:52 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libxdamage-dev amd64 1:1.1.4-2 [5,028 B]                                      
Get:53 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libxext-dev amd64 2:1.3.3-1 [82.1 kB]                                         
Get:54 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 x11proto-xf86vidmode-dev all 2.3.1-2 [6,116 B]                                
Get:55 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libxxf86vm-dev amd64 1:1.1.4-1 [13.3 kB]                                      
Get:56 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 x11proto-dri2-dev all 2.8-2 [12.6 kB]                                         
Get:57 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 x11proto-gl-dev all 1.4.17-1 [17.9 kB]                                        
Get:58 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libgl1-mesa-dev amd64 17.1.2-1ubuntu1 [4,424 B]                               
Get:59 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libglu1-mesa-dev amd64 9.0.0-2.1build1 [206 kB]                               
Get:60 http://gb.archive.ubuntu.com/ubuntu artful/universe amd64 libwxbase3.0-0v5 amd64 3.0.2+dfsg-4 [968 kB]                              
Get:61 http://gb.archive.ubuntu.com/ubuntu artful/universe amd64 wx3.0-headers amd64 3.0.2+dfsg-4 [1,021 kB]                               
Get:62 http://gb.archive.ubuntu.com/ubuntu artful/universe amd64 libwxbase3.0-dev amd64 3.0.2+dfsg-4 [29.2 kB]                             
Get:63 http://gb.archive.ubuntu.com/ubuntu artful/universe amd64 libwxgtk3.0-0v5 amd64 3.0.2+dfsg-4 [4,347 kB]                             
Get:64 http://gb.archive.ubuntu.com/ubuntu artful/universe amd64 wx-common amd64 3.0.2+dfsg-4 [68.2 kB]                                    
Get:65 http://gb.archive.ubuntu.com/ubuntu artful/universe amd64 libwxgtk3.0-dev amd64 3.0.2+dfsg-4 [29.4 kB]                              
Get:66 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 libx11-doc all 2:1.6.4-3 [2,067 kB]                                           
Get:67 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 manpages-dev all 4.10-2 [2,145 kB]                                            
Fetched 37.5 MB in 12s (2,938 kB/s)                                                                                                        
Extract templates from packages: 100%
Selecting previously unselected package libc-dev-bin.
(Reading database ... 198302 files and directories currently installed.)
Preparing to unpack .../00-libc-dev-bin_2.24-9ubuntu2_amd64.deb ...
Unpacking libc-dev-bin (2.24-9ubuntu2) ...
Selecting previously unselected package linux-libc-dev:amd64.
Preparing to unpack .../01-linux-libc-dev_4.10.0-22.24_amd64.deb ...
Unpacking linux-libc-dev:amd64 (4.10.0-22.24) ...
Selecting previously unselected package libc6-dev:amd64.
Preparing to unpack .../02-libc6-dev_2.24-9ubuntu2_amd64.deb ...
Unpacking libc6-dev:amd64 (2.24-9ubuntu2) ...
Selecting previously unselected package libitm1:amd64.
Preparing to unpack .../03-libitm1_7.1.0-6ubuntu2_amd64.deb ...
Unpacking libitm1:amd64 (7.1.0-6ubuntu2) ...
Selecting previously unselected package libasan3:amd64.
Preparing to unpack .../04-libasan3_6.3.0-18ubuntu2_amd64.deb ...
Unpacking libasan3:amd64 (6.3.0-18ubuntu2) ...
Selecting previously unselected package liblsan0:amd64.
Preparing to unpack .../05-liblsan0_7.1.0-6ubuntu2_amd64.deb ...
Unpacking liblsan0:amd64 (7.1.0-6ubuntu2) ...
Selecting previously unselected package libtsan0:amd64.
Preparing to unpack .../06-libtsan0_7.1.0-6ubuntu2_amd64.deb ...
Unpacking libtsan0:amd64 (7.1.0-6ubuntu2) ...
Selecting previously unselected package libubsan0:amd64.
Preparing to unpack .../07-libubsan0_7.1.0-6ubuntu2_amd64.deb ...
Unpacking libubsan0:amd64 (7.1.0-6ubuntu2) ...
Selecting previously unselected package libcilkrts5:amd64.
Preparing to unpack .../08-libcilkrts5_7.1.0-6ubuntu2_amd64.deb ...
Unpacking libcilkrts5:amd64 (7.1.0-6ubuntu2) ...
Selecting previously unselected package libmpx2:amd64.
Preparing to unpack .../09-libmpx2_7.1.0-6ubuntu2_amd64.deb ...
Unpacking libmpx2:amd64 (7.1.0-6ubuntu2) ...
Selecting previously unselected package libgcc-6-dev:amd64.
Preparing to unpack .../10-libgcc-6-dev_6.3.0-18ubuntu2_amd64.deb ...
Unpacking libgcc-6-dev:amd64 (6.3.0-18ubuntu2) ...
Selecting previously unselected package gcc-6.
Preparing to unpack .../11-gcc-6_6.3.0-18ubuntu2_amd64.deb ...
Unpacking gcc-6 (6.3.0-18ubuntu2) ...
Selecting previously unselected package gcc.
Preparing to unpack .../12-gcc_4%3a6.3.0-2ubuntu1_amd64.deb ...
Unpacking gcc (4:6.3.0-2ubuntu1) ...
Selecting previously unselected package libstdc++-6-dev:amd64.
Preparing to unpack .../13-libstdc++-6-dev_6.3.0-18ubuntu2_amd64.deb ...
Unpacking libstdc++-6-dev:amd64 (6.3.0-18ubuntu2) ...
Selecting previously unselected package g++-6.
Preparing to unpack .../14-g++-6_6.3.0-18ubuntu2_amd64.deb ...
Unpacking g++-6 (6.3.0-18ubuntu2) ...
Selecting previously unselected package g++.
Preparing to unpack .../15-g++_4%3a6.3.0-2ubuntu1_amd64.deb ...
Unpacking g++ (4:6.3.0-2ubuntu1) ...
Selecting previously unselected package make.
Preparing to unpack .../16-make_4.1-9.1_amd64.deb ...
Unpacking make (4.1-9.1) ...
Selecting previously unselected package dpkg-dev.
Preparing to unpack .../17-dpkg-dev_1.18.24ubuntu1_all.deb ...
Unpacking dpkg-dev (1.18.24ubuntu1) ...
Selecting previously unselected package build-essential.
Preparing to unpack .../18-build-essential_12.1ubuntu2_amd64.deb ...
Unpacking build-essential (12.1ubuntu2) ...
Selecting previously unselected package libfakeroot:amd64.
Preparing to unpack .../19-libfakeroot_1.21-1ubuntu2_amd64.deb ...
Unpacking libfakeroot:amd64 (1.21-1ubuntu2) ...
Selecting previously unselected package fakeroot.
Preparing to unpack .../20-fakeroot_1.21-1ubuntu2_amd64.deb ...
Unpacking fakeroot (1.21-1ubuntu2) ...
Selecting previously unselected package libalgorithm-diff-perl.
Preparing to unpack .../21-libalgorithm-diff-perl_1.19.03-1_all.deb ...
Unpacking libalgorithm-diff-perl (1.19.03-1) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Preparing to unpack .../22-libalgorithm-diff-xs-perl_0.04-4build2_amd64.deb ...
Unpacking libalgorithm-diff-xs-perl (0.04-4build2) ...
Selecting previously unselected package libalgorithm-merge-perl.
Preparing to unpack .../23-libalgorithm-merge-perl_0.08-3_all.deb ...
Unpacking libalgorithm-merge-perl (0.08-3) ...
Selecting previously unselected package libdrm-dev:amd64.
Preparing to unpack .../24-libdrm-dev_2.4.80-1_amd64.deb ...
Unpacking libdrm-dev:amd64 (2.4.80-1) ...
Selecting previously unselected package xorg-sgml-doctools.
Preparing to unpack .../25-xorg-sgml-doctools_1%3a1.11-1_all.deb ...
Unpacking xorg-sgml-doctools (1:1.11-1) ...
Selecting previously unselected package x11proto-core-dev.
Preparing to unpack .../26-x11proto-core-dev_7.0.31-1_all.deb ...
Unpacking x11proto-core-dev (7.0.31-1) ...
Selecting previously unselected package libxau-dev:amd64.
Preparing to unpack .../27-libxau-dev_1%3a1.0.8-1_amd64.deb ...
Unpacking libxau-dev:amd64 (1:1.0.8-1) ...
Selecting previously unselected package libxdmcp-dev:amd64.
Preparing to unpack .../28-libxdmcp-dev_1%3a1.1.2-3_amd64.deb ...
Unpacking libxdmcp-dev:amd64 (1:1.1.2-3) ...
Selecting previously unselected package x11proto-input-dev.
Preparing to unpack .../29-x11proto-input-dev_2.3.2-1_all.deb ...
Unpacking x11proto-input-dev (2.3.2-1) ...
Selecting previously unselected package x11proto-kb-dev.
Preparing to unpack .../30-x11proto-kb-dev_1.0.7-1_all.deb ...
Unpacking x11proto-kb-dev (1.0.7-1) ...
Selecting previously unselected package xtrans-dev.
Preparing to unpack .../31-xtrans-dev_1.3.5-1_all.deb ...
Unpacking xtrans-dev (1.3.5-1) ...
Selecting previously unselected package libpthread-stubs0-dev:amd64.
Preparing to unpack .../32-libpthread-stubs0-dev_0.3-4_amd64.deb ...
Unpacking libpthread-stubs0-dev:amd64 (0.3-4) ...
Selecting previously unselected package libxcb1-dev:amd64.
Preparing to unpack .../33-libxcb1-dev_1.11.1-1ubuntu1_amd64.deb ...
Unpacking libxcb1-dev:amd64 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libx11-dev:amd64.
Preparing to unpack .../34-libx11-dev_2%3a1.6.4-3_amd64.deb ...
Unpacking libx11-dev:amd64 (2:1.6.4-3) ...
Selecting previously unselected package mesa-common-dev:amd64.
Preparing to unpack .../35-mesa-common-dev_17.1.2-1ubuntu1_amd64.deb ...
Unpacking mesa-common-dev:amd64 (17.1.2-1ubuntu1) ...
Selecting previously unselected package libx11-xcb-dev:amd64.
Preparing to unpack .../36-libx11-xcb-dev_2%3a1.6.4-3_amd64.deb ...
Unpacking libx11-xcb-dev:amd64 (2:1.6.4-3) ...
Selecting previously unselected package libxcb-dri3-dev:amd64.
Preparing to unpack .../37-libxcb-dri3-dev_1.11.1-1ubuntu1_amd64.deb ...
Unpacking libxcb-dri3-dev:amd64 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libxcb-render0-dev:amd64.
Preparing to unpack .../38-libxcb-render0-dev_1.11.1-1ubuntu1_amd64.deb ...
Unpacking libxcb-render0-dev:amd64 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libxcb-randr0-dev:amd64.
Preparing to unpack .../39-libxcb-randr0-dev_1.11.1-1ubuntu1_amd64.deb ...
Unpacking libxcb-randr0-dev:amd64 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libxcb-shape0-dev:amd64.
Preparing to unpack .../40-libxcb-shape0-dev_1.11.1-1ubuntu1_amd64.deb ...
Unpacking libxcb-shape0-dev:amd64 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libxcb-xfixes0-dev:amd64.
Preparing to unpack .../41-libxcb-xfixes0-dev_1.11.1-1ubuntu1_amd64.deb ...
Unpacking libxcb-xfixes0-dev:amd64 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libxcb-sync-dev:amd64.
Preparing to unpack .../42-libxcb-sync-dev_1.11.1-1ubuntu1_amd64.deb ...
Unpacking libxcb-sync-dev:amd64 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libxcb-present-dev:amd64.
Preparing to unpack .../43-libxcb-present-dev_1.11.1-1ubuntu1_amd64.deb ...
Unpacking libxcb-present-dev:amd64 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libxshmfence-dev:amd64.
Preparing to unpack .../44-libxshmfence-dev_1.2-1_amd64.deb ...
Unpacking libxshmfence-dev:amd64 (1.2-1) ...
Selecting previously unselected package libxcb-dri2-0-dev:amd64.
Preparing to unpack .../45-libxcb-dri2-0-dev_1.11.1-1ubuntu1_amd64.deb ...
Unpacking libxcb-dri2-0-dev:amd64 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libxcb-glx0-dev:amd64.
Preparing to unpack .../46-libxcb-glx0-dev_1.11.1-1ubuntu1_amd64.deb ...
Unpacking libxcb-glx0-dev:amd64 (1.11.1-1ubuntu1) ...
Selecting previously unselected package x11proto-xext-dev.
Preparing to unpack .../47-x11proto-xext-dev_7.3.0-1_all.deb ...
Unpacking x11proto-xext-dev (7.3.0-1) ...
Selecting previously unselected package x11proto-fixes-dev.
Preparing to unpack .../48-x11proto-fixes-dev_1%3a5.0-2ubuntu2_all.deb ...
Unpacking x11proto-fixes-dev (1:5.0-2ubuntu2) ...
Selecting previously unselected package libxfixes-dev:amd64.
Preparing to unpack .../49-libxfixes-dev_1%3a5.0.3-1_amd64.deb ...
Unpacking libxfixes-dev:amd64 (1:5.0.3-1) ...
Selecting previously unselected package x11proto-damage-dev.
Preparing to unpack .../50-x11proto-damage-dev_1%3a1.2.1-2_all.deb ...
Unpacking x11proto-damage-dev (1:1.2.1-2) ...
Selecting previously unselected package libxdamage-dev:amd64.
Preparing to unpack .../51-libxdamage-dev_1%3a1.1.4-2_amd64.deb ...
Unpacking libxdamage-dev:amd64 (1:1.1.4-2) ...
Selecting previously unselected package libxext-dev:amd64.
Preparing to unpack .../52-libxext-dev_2%3a1.3.3-1_amd64.deb ...
Unpacking libxext-dev:amd64 (2:1.3.3-1) ...
Selecting previously unselected package x11proto-xf86vidmode-dev.
Preparing to unpack .../53-x11proto-xf86vidmode-dev_2.3.1-2_all.deb ...
Unpacking x11proto-xf86vidmode-dev (2.3.1-2) ...
Selecting previously unselected package libxxf86vm-dev:amd64.
Preparing to unpack .../54-libxxf86vm-dev_1%3a1.1.4-1_amd64.deb ...
Unpacking libxxf86vm-dev:amd64 (1:1.1.4-1) ...
Selecting previously unselected package x11proto-dri2-dev.
Preparing to unpack .../55-x11proto-dri2-dev_2.8-2_all.deb ...
Unpacking x11proto-dri2-dev (2.8-2) ...
Selecting previously unselected package x11proto-gl-dev.
Preparing to unpack .../56-x11proto-gl-dev_1.4.17-1_all.deb ...
Unpacking x11proto-gl-dev (1.4.17-1) ...
Selecting previously unselected package libgl1-mesa-dev:amd64.
Preparing to unpack .../57-libgl1-mesa-dev_17.1.2-1ubuntu1_amd64.deb ...
Unpacking libgl1-mesa-dev:amd64 (17.1.2-1ubuntu1) ...
Selecting previously unselected package libglu1-mesa-dev:amd64.
Preparing to unpack .../58-libglu1-mesa-dev_9.0.0-2.1build1_amd64.deb ...
Unpacking libglu1-mesa-dev:amd64 (9.0.0-2.1build1) ...
Selecting previously unselected package libwxbase3.0-0v5:amd64.
Preparing to unpack .../59-libwxbase3.0-0v5_3.0.2+dfsg-4_amd64.deb ...
Unpacking libwxbase3.0-0v5:amd64 (3.0.2+dfsg-4) ...
Selecting previously unselected package wx3.0-headers.
Preparing to unpack .../60-wx3.0-headers_3.0.2+dfsg-4_amd64.deb ...
Unpacking wx3.0-headers (3.0.2+dfsg-4) ...
Selecting previously unselected package libwxbase3.0-dev.
Preparing to unpack .../61-libwxbase3.0-dev_3.0.2+dfsg-4_amd64.deb ...
Unpacking libwxbase3.0-dev (3.0.2+dfsg-4) ...
Selecting previously unselected package libwxgtk3.0-0v5:amd64.
Preparing to unpack .../62-libwxgtk3.0-0v5_3.0.2+dfsg-4_amd64.deb ...
Unpacking libwxgtk3.0-0v5:amd64 (3.0.2+dfsg-4) ...
Selecting previously unselected package wx-common.
Preparing to unpack .../63-wx-common_3.0.2+dfsg-4_amd64.deb ...
Unpacking wx-common (3.0.2+dfsg-4) ...
Selecting previously unselected package libwxgtk3.0-dev.
Preparing to unpack .../64-libwxgtk3.0-dev_3.0.2+dfsg-4_amd64.deb ...
Unpacking libwxgtk3.0-dev (3.0.2+dfsg-4) ...
Selecting previously unselected package libx11-doc.
Preparing to unpack .../65-libx11-doc_2%3a1.6.4-3_all.deb ...
Unpacking libx11-doc (2:1.6.4-3) ...
Selecting previously unselected package manpages-dev.
Preparing to unpack .../66-manpages-dev_4.10-2_all.deb ...
Unpacking manpages-dev (4.10-2) ...
Setting up x11proto-dri2-dev (2.8-2) ...
Setting up make (4.1-9.1) ...
Setting up libasan3:amd64 (6.3.0-18ubuntu2) ...
Setting up libxshmfence-dev:amd64 (1.2-1) ...
Setting up libpthread-stubs0-dev:amd64 (0.3-4) ...
Setting up libcilkrts5:amd64 (7.1.0-6ubuntu2) ...
Setting up libdrm-dev:amd64 (2.4.80-1) ...
Setting up libubsan0:amd64 (7.1.0-6ubuntu2) ...
Setting up libtsan0:amd64 (7.1.0-6ubuntu2) ...
Setting up xorg-sgml-doctools (1:1.11-1) ...
Setting up linux-libc-dev:amd64 (4.10.0-22.24) ...
Setting up wx3.0-headers (3.0.2+dfsg-4) ...
Setting up x11proto-xf86vidmode-dev (2.3.1-2) ...
Setting up x11proto-kb-dev (1.0.7-1) ...
Processing triggers for sgml-base (1.29) ...
Setting up libwxbase3.0-0v5:amd64 (3.0.2+dfsg-4) ...
Setting up liblsan0:amd64 (7.1.0-6ubuntu2) ...
Setting up libmpx2:amd64 (7.1.0-6ubuntu2) ...
Setting up xtrans-dev (1.3.5-1) ...
Setting up dpkg-dev (1.18.24ubuntu1) ...
Processing triggers for libc-bin (2.24-9ubuntu2) ...
Setting up libfakeroot:amd64 (1.21-1ubuntu2) ...
Setting up x11proto-gl-dev (1.4.17-1) ...
Setting up libalgorithm-diff-perl (1.19.03-1) ...
Setting up libx11-doc (2:1.6.4-3) ...
Processing triggers for man-db (2.7.6.1-2) ...
Setting up libc-dev-bin (2.24-9ubuntu2) ...
Setting up manpages-dev (4.10-2) ...
Setting up libc6-dev:amd64 (2.24-9ubuntu2) ...
Setting up libitm1:amd64 (7.1.0-6ubuntu2) ...
Setting up wx-common (3.0.2+dfsg-4) ...
Setting up libgcc-6-dev:amd64 (6.3.0-18ubuntu2) ...
Setting up libstdc++-6-dev:amd64 (6.3.0-18ubuntu2) ...
Setting up x11proto-core-dev (7.0.31-1) ...
Setting up libwxgtk3.0-0v5:amd64 (3.0.2+dfsg-4) ...
Setting up libxau-dev:amd64 (1:1.0.8-1) ...
Setting up fakeroot (1.21-1ubuntu2) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up libwxbase3.0-dev (3.0.2+dfsg-4) ...
update-alternatives: using /usr/lib/x86_64-linux-gnu/wx/config/base-unicode-3.0 to provide /usr/bin/wx-config (wx-config) in auto mode
Setting up gcc-6 (6.3.0-18ubuntu2) ...
Setting up g++-6 (6.3.0-18ubuntu2) ...
Setting up libalgorithm-merge-perl (0.08-3) ...
Setting up libalgorithm-diff-xs-perl (0.04-4build2) ...
Setting up libxdmcp-dev:amd64 (1:1.1.2-3) ...
Setting up libxcb1-dev:amd64 (1.11.1-1ubuntu1) ...
Setting up libxcb-glx0-dev:amd64 (1.11.1-1ubuntu1) ...
Setting up x11proto-input-dev (2.3.2-1) ...
Setting up libxcb-sync-dev:amd64 (1.11.1-1ubuntu1) ...
Setting up gcc (4:6.3.0-2ubuntu1) ...
Setting up libxcb-dri2-0-dev:amd64 (1.11.1-1ubuntu1) ...
Setting up libxcb-render0-dev:amd64 (1.11.1-1ubuntu1) ...
Setting up libxcb-dri3-dev:amd64 (1.11.1-1ubuntu1) ...
Setting up x11proto-xext-dev (7.3.0-1) ...
Setting up libxcb-shape0-dev:amd64 (1.11.1-1ubuntu1) ...
Setting up g++ (4:6.3.0-2ubuntu1) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode
Setting up libx11-dev:amd64 (2:1.6.4-3) ...
Setting up libxxf86vm-dev:amd64 (1:1.1.4-1) ...
Setting up libx11-xcb-dev:amd64 (2:1.6.4-3) ...
Setting up libxcb-randr0-dev:amd64 (1.11.1-1ubuntu1) ...
Setting up mesa-common-dev:amd64 (17.1.2-1ubuntu1) ...
Setting up build-essential (12.1ubuntu2) ...
Setting up libxcb-xfixes0-dev:amd64 (1.11.1-1ubuntu1) ...
Setting up x11proto-fixes-dev (1:5.0-2ubuntu2) ...
Setting up x11proto-damage-dev (1:1.2.1-2) ...
Setting up libxext-dev:amd64 (2:1.3.3-1) ...
Setting up libxcb-present-dev:amd64 (1.11.1-1ubuntu1) ...
Setting up libxfixes-dev:amd64 (1:5.0.3-1) ...
Setting up libxdamage-dev:amd64 (1:1.1.4-2) ...
Setting up libgl1-mesa-dev:amd64 (17.1.2-1ubuntu1) ...
Setting up libglu1-mesa-dev:amd64 (9.0.0-2.1build1) ...
Setting up libwxgtk3.0-dev (3.0.2+dfsg-4) ...
update-alternatives: using /usr/lib/x86_64-linux-gnu/wx/config/gtk2-unicode-3.0 to provide /usr/bin/wx-config (wx-config) in auto mode
Processing triggers for libc-bin (2.24-9ubuntu2) ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking whether ln -s works... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking for ANSI C header files... no
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether make sets $(MAKE)... (cached) yes
checking if debug is enabled... no
checking for main in -lstdc++... yes
checking for wx-config... /usr/bin/wx-config
checking for wxWidgets version >= 2.8.4... yes (version 3.0.2)
checking for wxWidgets static library... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/data/Makefile
config.status: creating src/linux-menu/Makefile
config.status: creating src/win32/Makefile
config.status: creating src/locale/Makefile
config.status: creating src/locale/fr/Makefile
config.status: creating src/locale/fr/LC_MESSAGES/Makefile
config.status: creating debian/Makefile
config.status: creating innoSetup/Makefile
config.status: creating src/config.hpp
config.status: executing depfiles commands
config.status: executing libtool commands

####################################

The package is now configured. You should type make !
    DEBUG MODE          : disable.
    TARGET PLATFORM     : linux.
    INSTALLATION PREFIX : /usr/local.

####################################

Making all in src
make[1]: Entering directory '/Data/Downloads/winusb-1.0.11/src'
make  all-recursive
make[2]: Entering directory '/Data/Downloads/winusb-1.0.11/src'
Making all in data
make[3]: Entering directory '/Data/Downloads/winusb-1.0.11/src/data'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/data'
Making all in locale
make[3]: Entering directory '/Data/Downloads/winusb-1.0.11/src/locale'
Making all in fr
make[4]: Entering directory '/Data/Downloads/winusb-1.0.11/src/locale/fr'
Making all in LC_MESSAGES
make[5]: Entering directory '/Data/Downloads/winusb-1.0.11/src/locale/fr/LC_MESSAGES'
make[5]: Nothing to be done for 'all'.
make[5]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/locale/fr/LC_MESSAGES'
make[5]: Entering directory '/Data/Downloads/winusb-1.0.11/src/locale/fr'
make[5]: Nothing to be done for 'all-am'.
make[5]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/locale/fr'
make[4]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/locale/fr'
make[4]: Entering directory '/Data/Downloads/winusb-1.0.11/src/locale'
make[4]: Nothing to be done for 'all-am'.
make[4]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/locale'
make[3]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/locale'
Making all in win32
make[3]: Entering directory '/Data/Downloads/winusb-1.0.11/src/win32'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/win32'
Making all in linux-menu
make[3]: Entering directory '/Data/Downloads/winusb-1.0.11/src/linux-menu'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/linux-menu'
make[3]: Entering directory '/Data/Downloads/winusb-1.0.11/src'
g++ -DHAVE_CONFIG_H -I. -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-3.0 -I/usr/include/wx-3.0 -D_FILE_OFFSET_BITS=64 -DWXUSINGDLL -D__WXGTK__ -pthread  -s -O1  -Wall -Wclobbered -Wempty-body -Wmissing-field-initializers -Wsign-compare -Wtype-limits -Wuninitialized  -s -O1  -Wall -Wclobbered -Wempty-body -Wmissing-field-initializers -Wsign-compare -Wtype-limits -Wuninitialized -MT MainPanel.o -MD -MP -MF .deps/MainPanel.Tpo -c -o MainPanel.o MainPanel.cpp
mv -f .deps/MainPanel.Tpo .deps/MainPanel.Po
g++ -DHAVE_CONFIG_H -I. -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-3.0 -I/usr/include/wx-3.0 -D_FILE_OFFSET_BITS=64 -DWXUSINGDLL -D__WXGTK__ -pthread  -s -O1  -Wall -Wclobbered -Wempty-body -Wmissing-field-initializers -Wsign-compare -Wtype-limits -Wuninitialized  -s -O1  -Wall -Wclobbered -Wempty-body -Wmissing-field-initializers -Wsign-compare -Wtype-limits -Wuninitialized -MT App.o -MD -MP -MF .deps/App.Tpo -c -o App.o App.cpp
mv -f .deps/App.Tpo .deps/App.Po
g++ -DHAVE_CONFIG_H -I. -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-3.0 -I/usr/include/wx-3.0 -D_FILE_OFFSET_BITS=64 -DWXUSINGDLL -D__WXGTK__ -pthread  -s -O1  -Wall -Wclobbered -Wempty-body -Wmissing-field-initializers -Wsign-compare -Wtype-limits -Wuninitialized  -s -O1  -Wall -Wclobbered -Wempty-body -Wmissing-field-initializers -Wsign-compare -Wtype-limits -Wuninitialized -MT findFile.o -MD -MP -MF .deps/findFile.Tpo -c -o findFile.o findFile.cpp
mv -f .deps/findFile.Tpo .deps/findFile.Po
g++ -DHAVE_CONFIG_H -I. -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-3.0 -I/usr/include/wx-3.0 -D_FILE_OFFSET_BITS=64 -DWXUSINGDLL -D__WXGTK__ -pthread  -s -O1  -Wall -Wclobbered -Wempty-body -Wmissing-field-initializers -Wsign-compare -Wtype-limits -Wuninitialized  -s -O1  -Wall -Wclobbered -Wempty-body -Wmissing-field-initializers -Wsign-compare -Wtype-limits -Wuninitialized -MT MyException.o -MD -MP -MF .deps/MyException.Tpo -c -o MyException.o MyException.cpp
mv -f .deps/MyException.Tpo .deps/MyException.Po
g++ -DHAVE_CONFIG_H -I. -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-3.0 -I/usr/include/wx-3.0 -D_FILE_OFFSET_BITS=64 -DWXUSINGDLL -D__WXGTK__ -pthread  -s -O1  -Wall -Wclobbered -Wempty-body -Wmissing-field-initializers -Wsign-compare -Wtype-limits -Wuninitialized  -s -O1  -Wall -Wclobbered -Wempty-body -Wmissing-field-initializers -Wsign-compare -Wtype-limits -Wuninitialized -MT strWxStdConv.o -MD -MP -MF .deps/strWxStdConv.Tpo -c -o strWxStdConv.o strWxStdConv.cpp
mv -f .deps/strWxStdConv.Tpo .deps/strWxStdConv.Po
g++ -DHAVE_CONFIG_H -I. -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-3.0 -I/usr/include/wx-3.0 -D_FILE_OFFSET_BITS=64 -DWXUSINGDLL -D__WXGTK__ -pthread  -s -O1  -Wall -Wclobbered -Wempty-body -Wmissing-field-initializers -Wsign-compare -Wtype-limits -Wuninitialized  -s -O1  -Wall -Wclobbered -Wempty-body -Wmissing-field-initializers -Wsign-compare -Wtype-limits -Wuninitialized -MT MainFrame.o -MD -MP -MF .deps/MainFrame.Tpo -c -o MainFrame.o MainFrame.cpp
mv -f .deps/MainFrame.Tpo .deps/MainFrame.Po
g++ -DHAVE_CONFIG_H -I. -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-3.0 -I/usr/include/wx-3.0 -D_FILE_OFFSET_BITS=64 -DWXUSINGDLL -D__WXGTK__ -pthread  -s -O1  -Wall -Wclobbered -Wempty-body -Wmissing-field-initializers -Wsign-compare -Wtype-limits -Wuninitialized  -s -O1  -Wall -Wclobbered -Wempty-body -Wmissing-field-initializers -Wsign-compare -Wtype-limits -Wuninitialized -MT DialogAbout.o -MD -MP -MF .deps/DialogAbout.Tpo -c -o DialogAbout.o DialogAbout.cpp
mv -f .deps/DialogAbout.Tpo .deps/DialogAbout.Po
g++ -DHAVE_CONFIG_H -I. -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-3.0 -I/usr/include/wx-3.0 -D_FILE_OFFSET_BITS=64 -DWXUSINGDLL -D__WXGTK__ -pthread  -s -O1  -Wall -Wclobbered -Wempty-body -Wmissing-field-initializers -Wsign-compare -Wtype-limits -Wuninitialized  -s -O1  -Wall -Wclobbered -Wempty-body -Wmissing-field-initializers -Wsign-compare -Wtype-limits -Wuninitialized -MT processManager.o -MD -MP -MF .deps/processManager.Tpo -c -o processManager.o processManager.cpp
mv -f .deps/processManager.Tpo .deps/processManager.Po
/bin/bash ../libtool --tag=CXX   --mode=link g++  -s -O1  -Wall -Wclobbered -Wempty-body -Wmissing-field-initializers -Wsign-compare -Wtype-limits -Wuninitialized   -o winusbgui MainPanel.o App.o findFile.o MyException.o strWxStdConv.o MainFrame.o DialogAbout.o processManager.o -L/usr/lib/x86_64-linux-gnu -pthread   -lwx_gtk2u_xrc-3.0 -lwx_gtk2u_html-3.0 -lwx_gtk2u_qa-3.0 -lwx_gtk2u_adv-3.0 -lwx_gtk2u_core-3.0 -lwx_baseu_xml-3.0 -lwx_baseu_net-3.0 -lwx_baseu-3.0  -lstdc++ 
libtool: link: g++ -s -O1 -Wall -Wclobbered -Wempty-body -Wmissing-field-initializers -Wsign-compare -Wtype-limits -Wuninitialized -o winusbgui MainPanel.o App.o findFile.o MyException.o strWxStdConv.o MainFrame.o DialogAbout.o processManager.o -pthread  -L/usr/lib/x86_64-linux-gnu -lwx_gtk2u_xrc-3.0 -lwx_gtk2u_html-3.0 -lwx_gtk2u_qa-3.0 -lwx_gtk2u_adv-3.0 -lwx_gtk2u_core-3.0 -lwx_baseu_xml-3.0 -lwx_baseu_net-3.0 -lwx_baseu-3.0 -lstdc++ -pthread
make[3]: Leaving directory '/Data/Downloads/winusb-1.0.11/src'
make[2]: Leaving directory '/Data/Downloads/winusb-1.0.11/src'
make[1]: Leaving directory '/Data/Downloads/winusb-1.0.11/src'
Making all in innoSetup
make[1]: Entering directory '/Data/Downloads/winusb-1.0.11/innoSetup'
make[1]: Nothing to be done for 'all'.
make[1]: Leaving directory '/Data/Downloads/winusb-1.0.11/innoSetup'
Making all in debian
make[1]: Entering directory '/Data/Downloads/winusb-1.0.11/debian'
make[1]: Nothing to be done for 'all'.
make[1]: Leaving directory '/Data/Downloads/winusb-1.0.11/debian'
make[1]: Entering directory '/Data/Downloads/winusb-1.0.11'
make[1]: Nothing to be done for 'all-am'.
make[1]: Leaving directory '/Data/Downloads/winusb-1.0.11'
Making install in src
make[1]: Entering directory '/Data/Downloads/winusb-1.0.11/src'
Making install in data
make[2]: Entering directory '/Data/Downloads/winusb-1.0.11/src/data'
make[3]: Entering directory '/Data/Downloads/winusb-1.0.11/src/data'
test -z "/usr/local/share/winusb/data" || /bin/mkdir -p "/usr/local/share/winusb/data"
 /usr/bin/install -c listUsb listDvdDrive '/usr/local/share/winusb/data'
test -z "/usr/local/share/winusb/data" || /bin/mkdir -p "/usr/local/share/winusb/data"
 /usr/bin/install -c -m 644 ./c501-logo.png ./icon.png '/usr/local/share/winusb/data'
make[3]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/data'
make[2]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/data'
Making install in locale
make[2]: Entering directory '/Data/Downloads/winusb-1.0.11/src/locale'
Making install in fr
make[3]: Entering directory '/Data/Downloads/winusb-1.0.11/src/locale/fr'
Making install in LC_MESSAGES
make[4]: Entering directory '/Data/Downloads/winusb-1.0.11/src/locale/fr/LC_MESSAGES'
make[5]: Entering directory '/Data/Downloads/winusb-1.0.11/src/locale/fr/LC_MESSAGES'
make[5]: Nothing to be done for 'install-exec-am'.
test -z "/usr/local/share/winusb/locale/fr/LC_MESSAGES" || /bin/mkdir -p "/usr/local/share/winusb/locale/fr/LC_MESSAGES"
 /usr/bin/install -c -m 644 ./trad.mo ./wxstd.mo '/usr/local/share/winusb/locale/fr/LC_MESSAGES'
make[5]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/locale/fr/LC_MESSAGES'
make[4]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/locale/fr/LC_MESSAGES'
make[4]: Entering directory '/Data/Downloads/winusb-1.0.11/src/locale/fr'
make[5]: Entering directory '/Data/Downloads/winusb-1.0.11/src/locale/fr'
make[5]: Nothing to be done for 'install-exec-am'.
make[5]: Nothing to be done for 'install-data-am'.
make[5]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/locale/fr'
make[4]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/locale/fr'
make[3]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/locale/fr'
make[3]: Entering directory '/Data/Downloads/winusb-1.0.11/src/locale'
make[4]: Entering directory '/Data/Downloads/winusb-1.0.11/src/locale'
make[4]: Nothing to be done for 'install-exec-am'.
make[4]: Nothing to be done for 'install-data-am'.
make[4]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/locale'
make[3]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/locale'
make[2]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/locale'
Making install in win32
make[2]: Entering directory '/Data/Downloads/winusb-1.0.11/src/win32'
make[3]: Entering directory '/Data/Downloads/winusb-1.0.11/src/win32'
make[3]: Nothing to be done for 'install-exec-am'.
make[3]: Nothing to be done for 'install-data-am'.
make[3]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/win32'
make[2]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/win32'
Making install in linux-menu
make[2]: Entering directory '/Data/Downloads/winusb-1.0.11/src/linux-menu'
make[3]: Entering directory '/Data/Downloads/winusb-1.0.11/src/linux-menu'
make[3]: Nothing to be done for 'install-exec-am'.
test -z "/usr/local/share/applications" || /bin/mkdir -p "/usr/local/share/applications"
 /usr/bin/install -c -m 644 ./winusbgui.desktop '/usr/local/share/applications'
test -z "/usr/local/share/pixmaps" || /bin/mkdir -p "/usr/local/share/pixmaps"
 /usr/bin/install -c -m 644 ./winusbgui-icon.png '/usr/local/share/pixmaps'
make[3]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/linux-menu'
make[2]: Leaving directory '/Data/Downloads/winusb-1.0.11/src/linux-menu'
make[2]: Entering directory '/Data/Downloads/winusb-1.0.11/src'
make[3]: Entering directory '/Data/Downloads/winusb-1.0.11/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c winusbgui '/usr/local/bin'
libtool: install: /usr/bin/install -c winusbgui /usr/local/bin/winusbgui
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
 /usr/bin/install -c winusb '/usr/local/bin'
test -z "/usr/local/share/man/man1" || /bin/mkdir -p "/usr/local/share/man/man1"
 /usr/bin/install -c -m 644 winusbgui.1 winusb.1 '/usr/local/share/man/man1'
make  install-data-hook
make[4]: Entering directory '/Data/Downloads/winusb-1.0.11/src'
make[4]: Nothing to be done for 'install-data-hook'.
make[4]: Leaving directory '/Data/Downloads/winusb-1.0.11/src'
make[3]: Leaving directory '/Data/Downloads/winusb-1.0.11/src'
make[2]: Leaving directory '/Data/Downloads/winusb-1.0.11/src'
make[1]: Leaving directory '/Data/Downloads/winusb-1.0.11/src'
Making install in innoSetup
make[1]: Entering directory '/Data/Downloads/winusb-1.0.11/innoSetup'
make[2]: Entering directory '/Data/Downloads/winusb-1.0.11/innoSetup'
make[2]: Nothing to be done for 'install-exec-am'.
make[2]: Nothing to be done for 'install-data-am'.
make[2]: Leaving directory '/Data/Downloads/winusb-1.0.11/innoSetup'
make[1]: Leaving directory '/Data/Downloads/winusb-1.0.11/innoSetup'
Making install in debian
make[1]: Entering directory '/Data/Downloads/winusb-1.0.11/debian'
make[2]: Entering directory '/Data/Downloads/winusb-1.0.11/debian'
make[2]: Nothing to be done for 'install-exec-am'.
make[2]: Nothing to be done for 'install-data-am'.
make[2]: Leaving directory '/Data/Downloads/winusb-1.0.11/debian'
make[1]: Leaving directory '/Data/Downloads/winusb-1.0.11/debian'
make[1]: Entering directory '/Data/Downloads/winusb-1.0.11'
make[2]: Entering directory '/Data/Downloads/winusb-1.0.11'
make[2]: Nothing to be done for 'install-exec-am'.
test -z "/usr/local" || /bin/mkdir -p "/usr/local"
make[2]: Leaving directory '/Data/Downloads/winusb-1.0.11'
make[1]: Leaving directory '/Data/Downloads/winusb-1.0.11'
```

Caveat, this was done on a 17.10 installation, ymmv. You break something and you get to keep all the pieces.

---

### Post by monkeybrain20122 on 2017-06-10
Sorry, I did see it in synaptic. Turns out it is from the [webupd8]("https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8") ppa

```

sudo apt-get install -s winusb
[sudo] password for monkeybrain: Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  winusb
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Inst winusb (1.0.11.1+git20161204-1~webupd8~xenial0 WebUpd8:16.04/xenial [amd64])
Conf winusb (1.0.11.1+git20161204-1~webupd8~xenial0 WebUpd8:16.04/xenial [amd64])



```


so just add the ppa and install it.  From terminal
```
sudo add-apt-repository ppa:nilarimogard/webupd8 && sudo apt update && sudo apt install winusb
```

---

### Post by howefield on 2017-06-11
> **monkeybrain20122 said:**
> so just add the ppa and install it.  From terminal
```
sudo add-apt-repository ppa:nilarimogard/webupd8 && sudo apt update && sudo apt install winusb
```

+1 That would be an easier way to do it, it's also the current version and a good way to potentially get updates.

---

### Post by dommel2002 on 2017-06-11
Thank you very much!!!

---

