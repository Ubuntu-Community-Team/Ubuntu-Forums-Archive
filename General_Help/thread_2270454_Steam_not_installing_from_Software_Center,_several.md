---
title: "Steam not installing from Software Center, several errors..."
date: 2015-03-23
forum: General Help
---

### Post by pickettbrenton on 2015-03-23
First when install Steam from the Software Center, it updates Steam and seems like it's installing. I click on the desktop icon for Steam and a terminal pops with:
```
Steam needs to install these additional packages: 
    libgl1-mesa-dri:i386, libgl1-mesa-glx:i386
```
And asks for my password.
 
When I put in my password, a bunch of dots go across the screen and then I get:
```
............................................................................................................
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cups : Depends: libc-bin (>= 2.13)
 libc6-dbg : Depends: libc6 (= 2.19-0ubuntu6.5) but 2.19-0ubuntu6.6 is to be installed
 libc6-dev : Depends: libc6 (= 2.19-0ubuntu6.5) but 2.19-0ubuntu6.6 is to be installed
 libgl1-mesa-dri:i386 : Depends: libdrm-intel1:i386 (>= 2.4.48) but it is not going to be installed
                        Depends: libdrm-nouveau2:i386 (>= 2.4.38) but it is not going to be installed
                        Depends: libdrm-radeon1:i386 (>= 2.4.31) but it is not going to be installed
                        Depends: libdrm2:i386 (>= 2.4.38) but it is not going to be installed
                        Depends: libelf1:i386 (>= 0.142) but it is not going to be installed
                        Depends: libexpat1:i386 (>= 2.0.1) but it is not going to be installed
                        Depends: libllvm3.6:i386 but it is not going to be installed
                        Depends: libstdc++6:i386 (>= 4.6) but it is not going to be installed
                        Recommends: libtxc-dxtn-s2tc0:i386 but it is not going to be installed or
                                    libtxc-dxtn0:i386
 libgl1-mesa-dri-lts-utopic : Conflicts: libgl1-mesa-dri:i386
 libgl1-mesa-glx:i386 : Depends: libdrm2:i386 (>= 2.3.1) but it is not going to be installed
                        Depends: libexpat1:i386 (>= 2.0.1) but it is not going to be installed
                        Depends: libglapi-mesa:i386 (= 10.6.0~git20150318.27bf37ba-0ubuntu0ricotz~trusty)
                        Depends: libx11-6:i386 (>= 2:1.4.99.1) but it is not going to be installed
                        Depends: libx11-xcb1:i386 but it is not going to be installed
                        Depends: libxcb-dri2-0:i386 (>= 1.8) but it is not going to be installed
                        Depends: libxcb-dri3-0:i386 but it is not going to be installed
                        Depends: libxcb-glx0:i386 (>= 1.8) but it is not going to be installed
                        Depends: libxcb-present0:i386 but it is not going to be installed
                        Depends: libxcb-sync1:i386 but it is not going to be installed
                        Depends: libxcb1:i386 (>= 1.9.2) but it is not going to be installed
                        Depends: libxdamage1:i386 (>= 1:1.1) but it is not going to be installed
                        Depends: libxext6:i386 but it is not going to be installed
                        Depends: libxfixes3:i386 but it is not going to be installed
                        Depends: libxshmfence1:i386 but it is not going to be installed
                        Depends: libxxf86vm1:i386 but it is not going to be installed
                        Depends: libudev1:i386 but it is not going to be installed
                        Conflicts: libgl1
 libgl1-mesa-glx-lts-utopic : Conflicts: libgl1:i386
                              Conflicts: libgl1-mesa-glx:i386
 xserver-xorg-lts-utopic : Conflicts: libgl1-mesa-dri:i386 (>= 0~)
                           Conflicts: libgl1-mesa-glx:i386 (>= 0~)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
Press return to continue: 

```

When I press "return" I get the error "You are missing the following 32-bit libraries, and Steam may not run:
libc.so.6". Steam will load, but give another "Fatal Error: Failed to load steamui.so". I Googled this and tried all options to get the 32-bit library, but everything just returns more errors.

I tried removing Steam in the Software Center, but now it's giving me repair errors and I have no idea what else to do. I've tried everything I've found in these forums and can't find a solution. I'm new to Ubuntu and just wanted to use this computer as basically a Steam machine. 

I also have question about my nVidia and Xonar drivers, but will save those for another thread.

---

### Post by pickettbrenton on 2015-03-23
Although I tried this before I ran```
sudo apt-get -f install
``` and then ```
sudo apt-get install steam
``` and it worked. Don't know why it didn't work the first few times I tried that.

---

### Post by enricobe on 2015-03-23
Steam seems to be a bit buggy. Yesterday I tried to install Steam on my  fresh Xubuntu install and I get some errors about dependencies, some freezes while installing the libs that you are talking about, and other problems. Today I've tried to reinstall Xubuntu and install again Steam and it worked fine.

---

