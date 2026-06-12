---
title: "Can't install python-pyopencl"
date: 2013-02-20
forum: General Help
---

### Post by s_grin on 2013-02-20
Hi, I'm trying to install pyopencl but apt-get outputs:
```
sudo apt-get install python-pyopencl 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 python-pyopencl : Depends: nvidia-current but it is not going to be installed
                   Recommends: nvidia-opencl-icd but it is not installable
E: Unable to correct problems, you have held broken packages.
```
My system is:
```
uname -a
Linux cldev 3.5.0-24-generic #37~precise1-Ubuntu SMP Thu Feb 7 22:09:59 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```
After fresh Ubuntu install packages fglrx-updates and fglrx-amdcccle-updates were installed using apt-get.
My video card:
```
lspci | grep VGA
06:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Antilles [AMD Radeon HD 6990]
```
How to get pyopencl installed?

---

### Post by sanderj on 2013-02-20
Did you Google "E: Unable to correct problems, you have held broken packages."?

---

### Post by slickymaster on 2013-02-20
You can get a list of actual held packages with:
```
dpkg --get-selections | grep hold
```

If you have a problem  with a broken package the first thing to try is:
```
sudo dpkg --configure -a
```

If this does not work try:
```
sudo apt-get install -f
```

---

### Post by s_grin on 2013-02-21
Thanks for answers!
> **sanderj said:**
> Did you Google "E: Unable to correct problems, you have held broken packages."?
My bad, I tried "pyopencl" and "nvidia-current" variants. Now found advice with aptitude, see below.
> **slickymaster said:**
> You can get a list of actual held packages with:
```
dpkg --get-selections | grep hold
```

If you have a problem  with a broken package the first thing to try is:
```
sudo dpkg --configure -a
```

If this does not work try:
```
sudo apt-get install -f
```

dpkg --get-selections | grep hold
and
dpkg --configure -a
output nothing
```
apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
Tried aptitude:
```
aptitude install python-pyopencl
The following NEW packages will be installed:
  blt{a} freeglut3{a} libblas3gf{a} libboost-python1.46.1{a} libgfortran3{a} libgl1-mesa-dri{a} liblapack3gf{a} libllvm3.0{a} 
  nvidia-current{a} nvidia-settings{a} python-decorator{a} python-matplotlib{a} python-matplotlib-data{a} python-numpy{a} 
  python-opengl{a} python-pyopencl python-pyparsing{a} python-pytools{a} python-tk{a} python-tz{a} screen-resolution-extra{a} 
  tcl8.5{a} tk8.5{a} ttf-lyx{a} xserver-xorg-core{a} 
0 packages upgraded, 25 newly installed, 0 to remove and 0 not upgraded.
Need to get 88.4 MB of archives. After unpacking 284 MB will be used.
The following packages have unmet dependencies:
 libgl1-mesa-dri-lts-quantal : Conflicts: libgl1-mesa-dri but 8.0.4-0ubuntu0.3 is to be installed.
 xserver-xorg-lts-quantal : Conflicts: libgl1-mesa-dri (>= 0~) but 8.0.4-0ubuntu0.3 is to be installed.
                            Conflicts: xserver-xorg-core (>= 0~) but 2:1.11.4-0ubuntu10.11 is to be installed.
 xserver-xorg-core-lts-quantal : Conflicts: xserver-xorg-core but 2:1.11.4-0ubuntu10.11 is to be installed.
The following actions will resolve these dependencies:

      Remove the following packages:                                          
1)      ubuntu-desktop                                                        
2)      xorg                                                                  
3)      xserver-xorg-core-lts-quantal                                         
4)      xserver-xorg-input-all-lts-quantal                                    
5)      xserver-xorg-input-evdev-lts-quantal                                  
6)      xserver-xorg-input-mouse-lts-quantal                                  
7)      xserver-xorg-input-synaptics-lts-quantal                              
8)      xserver-xorg-input-vmmouse-lts-quantal                                
9)      xserver-xorg-input-wacom-lts-quantal                                  
10)     xserver-xorg-lts-quantal                                              
11)     xserver-xorg-video-all-lts-quantal                                    
12)     xserver-xorg-video-ati-lts-quantal                                    
13)     xserver-xorg-video-cirrus-lts-quantal                                 
14)     xserver-xorg-video-fbdev-lts-quantal                                  
15)     xserver-xorg-video-intel-lts-quantal                                  
16)     xserver-xorg-video-mach64-lts-quantal                                 
17)     xserver-xorg-video-mga-lts-quantal                                    
18)     xserver-xorg-video-modesetting-lts-quantal                            
19)     xserver-xorg-video-neomagic-lts-quantal                               
20)     xserver-xorg-video-nouveau-lts-quantal                                
21)     xserver-xorg-video-openchrome-lts-quantal                             
22)     xserver-xorg-video-r128-lts-quantal                                   
23)     xserver-xorg-video-radeon-lts-quantal                                 
24)     xserver-xorg-video-s3-lts-quantal                                     
25)     xserver-xorg-video-savage-lts-quantal                                 
26)     xserver-xorg-video-siliconmotion-lts-quantal                          
27)     xserver-xorg-video-sis-lts-quantal                                    
28)     xserver-xorg-video-sisusb-lts-quantal                                 
29)     xserver-xorg-video-tdfx-lts-quantal                                   
30)     xserver-xorg-video-trident-lts-quantal                                
31)     xserver-xorg-video-vesa-lts-quantal                                   
32)     xserver-xorg-video-vmware-lts-quantal                                 

      Keep the following packages at their current version:                   
33)     libgl1-mesa-dri [Not Installed]                                       

      Leave the following dependencies unresolved:                            
34)     xinit recommends xserver-xorg | xserver                               
35)     lightdm recommends xserver-xorg                                       
36)     xserver-xorg-core recommends libgl1-mesa-dri (>= 7.10.2-4)            
37)     xserver-xorg-lts-quantal recommends xserver-xorg-input-all-lts-quantal


Accept this solution? [Y/n/q/?] 

```
I don't know what to answer.

---

### Post by giancarlocp on 2013-10-12
Is a headache, i do many tries (messy things) in ubuntu 12.04 to run pyopencl.
I format and install ubuntu 13.10 waiting this problem solved, but is harderd, i couldn't install and run this time.
I have an APU A8.
```
 $ lspci |grep -i vga
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7560D] 
```

When install pyopencl is forced to **install nvidia-current** and **remove fglrx** and *viceversa*.
When reinstall fglrx conflict resolve to remove nvidia and pyopencl.
are AMD users a *second*-*class citizens*? is a joke, but
here we have a _eternal_ problem with pyopencl-nvidia dependences and AMD users.

Now i have to **downgrade**, but i don't remember how i do last time,
i didn't think that steps would helpfull in a near future.

---

### Post by vinx on 2014-01-19
It is solved in Debian since 2012(!!), so it just needs to be taken from upstream.

[http://wiki.tiker.net/PyOpenCL/Installation/Linux/Ubuntu](http://wiki.tiker.net/PyOpenCL/Installation/Linux/Ubuntu) has a working solution.

---

