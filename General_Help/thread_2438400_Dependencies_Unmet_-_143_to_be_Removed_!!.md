---
title: "Dependencies Unmet - 143 to be Removed ?!?!?"
date: 2020-03-11
forum: General Help
---

### Post by Rick St. George on 2020-03-11
Running UbuntuStudio v18.04, and after doing aptitude update", rec'd the following and wonder if this is ACCURATE as it wants to REMOVE 143 software pkgs, some of which I want, I use, and I like!

```

~$ sudo aptitude dist-upgrade
The following packages will be upgraded: 
  cpp-7 firefox firefox-locale-en g++-7 gcc-7 gcc-7-base gcc-8-base{b} 
  libasan4 libatomic1 libcc1-0 libcilkrts5 libgcc-7-dev libgcc1{b} 
  libgfortran4 libgomp1 libitm1 liblsan0 libmpx2 libquadmath0 libsqlite3-0 
  libstdc++-7-dev libstdc++6 libtsan0 libubsan0 linux-firmware 
25 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 53.8 MB/162 MB of archives. After unpacking 4,936 kB will be used.

The following packages have unmet dependencies:
 gcc-8-base : Breaks: gcc-8-base:i386 (!= 8.3.0-26ubuntu1~18.04) but 8.3.0-6ubuntu1~18.04.1 is installed
 gcc-8-base:i386 : Breaks: gcc-8-base (!= 8.3.0-6ubuntu1~18.04.1) but 8.3.0-26ubuntu1~18.04 is to be installed
 libgcc1 : Breaks: libgcc1:i386 (!= 1:8.3.0-26ubuntu1~18.04) but 1:8.3.0-6ubuntu1~18.04.1 is installed
 libgcc1:i386 : Breaks: libgcc1 (!= 1:8.3.0-6ubuntu1~18.04.1) but 1:8.3.0-26ubuntu1~18.04 is to be installed

The following actions will resolve these dependencies:
      Remove the following packages:                                      
1)      ardour [1:5.12.0-3 (now)]                                         
2)      blender [2.79.b+dfsg0-1ubuntu1.18.04.1 (now)]                     
3)      build-essential [12.4ubuntu1 (bionic, now)]                       
4)      debhelper [11.1.6ubuntu2 (bionic-updates, now)]                   
5)      dh-autoreconf [17 (bionic, now)]                                  
6)      dh-strip-nondeterminism [0.040-1.1~build1 (bionic, now)]          
7)      dispcalgui [3.5.0.0-1 (now)]                                      
8)      dkms [2.3-3ubuntu9.7 (bionic-updates, now)]                       
9)      g++ [4:7.4.0-1ubuntu2.3 (bionic-security, bionic-updates, now)]   
10)     g++-7 [7.4.0-1ubuntu1~18.04.1 (now)]                              
11)     gcc [4:7.4.0-1ubuntu2.3 (bionic-security, bionic-updates, now)]   
12)     gcc-7 [7.4.0-1ubuntu1~18.04.1 (now)]                              
13)     gimp [2.8.22-1 (now)]                                             
14)     libarmadillo8 [1:8.400.0+dfsg-2 (now)]                            
15)     libarpack2 [3.5.0+real-2 (now)]                                   
16)     libatlas3-base [3.10.3-5 (now)]                                   
17)     libcholmod2.1.2 [1:4.2.1-3ubuntu1 (now)]                          
18)     libcholmod3 [1:5.1.2-2 (bionic, now)]                             
19)     libdvd-pkg [1.4.2-1-1 (bionic, now)]                              
20)     libdvdcss-dev [1.4.2-1~local (now)]                               
21)     libdvdcss2 [1.4.2-1~local (now)]                                  
22)     libgcc-7-dev [7.4.0-1ubuntu1~18.04.1 (now)]                       
23)     libgdal20 [2.2.3+dfsg-2 (now)]                                    
24)     libgegl-0.3-0 [0.3.30-1ubuntu1 (now)]                             
25)     libgfortran4 [7.4.0-1ubuntu1~18.04.1 (now)]                       
26)     libhdf5-100 [1.10.0-patch1+docs-4 (now)]                          
27)     liblapack3 [3.7.1-4ubuntu1 (bionic, now)]                         
28)     libmpx2 [8.3.0-6ubuntu1~18.04.1 (now)]                            
29)     libnetcdf13 [1:4.6.0-2build1 (now)]                               
30)     libopencv-imgcodecs3.2 [3.2.0+dfsg-4ubuntu0.1 (now)]              
31)     libopencv-videoio3.2 [3.2.0+dfsg-4ubuntu0.1 (now)]                
32)     libopenimageio1.7 [1.7.17~dfsg0-1ubuntu2 (now)]                   
33)     libqm-dsp0 [1.7.1-4 (now)]                                        
34)     libquadmath0 [8.3.0-6ubuntu1~18.04.1 (now)]                       
35)     libstdc++-7-dev [7.4.0-1ubuntu1~18.04.1 (now)]                    
36)     libtool [2.4.6-2 (bionic, now)]                                   
37)     libumfpack5 [1:5.1.2-2 (bionic, now)]                             
38)     libumfpack5.6.2 [1:4.2.1-3ubuntu1 (now)]                          
39)     nvidia-384 [390.116-0ubuntu0.18.04.3 (bionic-updates, now)]       
40)     nvidia-dkms-390 [390.116-0ubuntu0.18.04.3 (bionic-updates, now)]  
41)     nvidia-driver-390 [390.116-0ubuntu0.18.04.3 (bionic-updates, now)]
42)     pd-py [0.2.2+git20170625.1.88fc77a-2 (now)]                       
43)     pitivi [0.99-3 (now)]                                             
44)     python-matplotlib [2.1.1-2ubuntu3 (now)]                          
45)     python-numpy [1:1.13.3-2ubuntu1 (bionic, now)]                    
46)     python3-matplotlib [2.1.1-2ubuntu3 (now)]                         
47)     python3-numpy [1:1.13.3-2ubuntu1 (bionic, now)]                   

      Keep the following packages at their current version:               
48)     gcc-8-base [8.3.0-6ubuntu1~18.04.1 (now)]                         
49)     libatomic1 [8.3.0-6ubuntu1~18.04.1 (now)]                         
50)     libcc1-0 [8.3.0-6ubuntu1~18.04.1 (now)]                           
51)     libgcc1 [1:8.3.0-6ubuntu1~18.04.1 (now)]                          
52)     libgomp1 [8.3.0-6ubuntu1~18.04.1 (now)]                           
53)     libitm1 [8.3.0-6ubuntu1~18.04.1 (now)]                            
54)     liblsan0 [8.3.0-6ubuntu1~18.04.1 (now)]                           
55)     libstdc++6 [8.3.0-6ubuntu1~18.04.1 (now)]                         
56)     libtsan0 [8.3.0-6ubuntu1~18.04.1 (now)]                           

      Leave the following dependencies unresolved:                        
57)     dpkg-dev recommends build-essential                               
58)     dpkg-dev recommends gcc | c-compiler                              
59)     libltdl-dev recommends libtool                                    
60)     ubuntustudio-publishing recommends gimp                           
61)     codeblocks recommends gcc | g++                                   
62)     ubuntustudio-audio recommends ardour                              
63)     multimedia-puredata recommends pd-py                              
64)     openshot-qt recommends blender                                    
65)     ubuntustudio-photography recommends dispcalgui                    
66)     ubuntustudio-photography recommends gimp                          
67)     ubuntustudio-video recommends blender                             
68)     ubuntustudio-video recommends pitivi                              
69)     ardour-data recommends ardour                                     
70)     inkscape recommends python-numpy                                  
71)     ubuntustudio-graphics recommends blender                          
72)     ubuntustudio-graphics recommends gimp                             


Accept this solution? [Y/n/q/?] y

The following packages have unmet dependencies:
 python3-pyqt5 : Depends: sip-py3api-12.3 which is a virtual package, provided by:
                          - python3-sip (4.19.7+dfsg-1), but it is not going to be installed

The following actions will resolve these dependencies:

      Remove the following packages:                       
1)      openshot [2.4.1-2build2 (now)]                     
2)      openshot-qt [2.4.1-2build2 (now)]                  
3)      python3-pyqt5 [5.10.1+dfsg-1ubuntu2 (now)]         
4)      python3-pyqt5.qtsvg [5.10.1+dfsg-1ubuntu2 (now)]   
5)      python3-pyqt5.qtwebkit [5.10.1+dfsg-1ubuntu2 (now)]

      Leave the following dependencies unresolved:         
6)      dpkg-dev recommends build-essential                
7)      dpkg-dev recommends gcc | c-compiler               
8)      ubuntustudio-publishing recommends gimp            
9)      codeblocks recommends gcc | g++                    
10)     ubuntustudio-audio recommends ardour               
11)     multimedia-puredata recommends pd-py               
12)     openshot-qt recommends blender                     
13)     ubuntustudio-photography recommends dispcalgui     
14)     ubuntustudio-photography recommends gimp           
15)     ubuntustudio-video recommends blender              
16)     ubuntustudio-video recommends openshot             
17)     ubuntustudio-video recommends pitivi               
18)     inkscape recommends python-numpy                   
19)     ubuntustudio-graphics recommends blender           
20)     ubuntustudio-graphics recommends gimp              



Accept this solution? [Y/n/q/?] y

The following packages will be REMOVED:
  ardour{a} ardour-data{u} ardour-video-timeline{u} blender{a} 
  blender-data{u} build-essential{a} debhelper{a} dh-autoreconf{a} 
  dh-strip-nondeterminism{a} dispcalgui{a} dkms{a} g++{a} g++-7{a} gcc{a} 
  gcc-7{a} gdal-data{u} gimp{a} gir1.2-ges-1.0{u} harvid{u} libaec0{u} 
  libamd2{u} libarchive-cpio-perl{u} libarmadillo8{a} libarpack2{a} 
  libasan4{u} libatlas3-base{a} libblosc1{u} libboost-regex1.65.1{u} 
  libcamd2{u} libccolamd2{u} libcharls1{u} libcholmod2.1.2{a} 
  libcholmod3{a} libcilkrts5{u} libdap25{u} libdapclient6v5{u} 
  libdvd-pkg{a} libdvdcss-dev{a} libdvdcss2{a} libepsilon1{u} 
  libfile-stripnondeterminism-perl{u} libfreexl1{u} libfyba0{u} 
  libgcc-7-dev{a} libgdal20{a} libgdcm2.8{u} libgegl-0.3-0{a} 
  libgeos-3.6.2{u} libgeos-c1v5{u} libgeotiff2{u} libges-1.0-0{u} 
  libgfortran4{a} libhdf4-0-alt{u} libhdf5-100{a} libjemalloc1{u} 
  libjs-jquery-ui{u} libjsoncpp1{u} libkmlbase1{u} libkmldom1{u} 
  libkmlengine1{u} liblapack3{a} liblog4cplus-1.1-9{u} liblsan0{u} 
  libltdl-dev{u} libmail-sendmail-perl{u} libmetis5{u} libminizip1{u} 
  libmpx2{a} libmysqlclient20{u} libnetcdf13{a} libnvidia-cfg1-390{u} 
  libnvidia-common-390{u} libnvidia-decode-390{u} libnvidia-encode-390{u} 
  libnvidia-fbc1-390{u} libnvidia-gl-390{u} libnvidia-ifr1-390{u} 
  libodbc1{u} libogdi3.2{u} libopencolorio1v5{u} libopencv-core3.2{u} 
  libopencv-imgcodecs3.2{a} libopencv-imgproc3.2{u} libopencv-videoio3.2{a} 
  libopenimageio1.7{a} libopenshot-audio6{u} libopenshot14{u} 
  libopenvdb5.0{u} libpq5{u} libproj12{u} libqhull7{u} libqm-dsp0{a} 
  libquadmath0{a} libsocket++1{u} libspatialite7{u} libspnav0{u} 
  libstdc++-7-dev{a} libsuperlu5{u} libsys-hostname-long-perl{u} libsz2{u} 
  libtinyxml2.6.2v5{u} libtool{a} libubsan0{u} libumfpack5{a} 
  libumfpack5.6.2{a} liburiparser1{u} libvamp-sdk2v5{u} libxerces-c3.2{u} 
  libyaml-cpp0.5v5{u} nvidia-384{a} nvidia-dkms-390{a} nvidia-driver-390{a} 
  nvidia-kernel-common-390{u} nvidia-prime{u} nvidia-settings{u} 
  nvidia-utils-390{u} openshot{a} openshot-qt{a} pd-py{a} pitivi{a} 
  po-debconf{u} proj-bin{u} proj-data{u} 
  python-backports.functools-lru-cache{u} python-cycler{u} 
  python-matplotlib{a} python-numpy{a} python-subprocess32{u} 
  python3-cycler{u} python3-gst-1.0{u} python3-matplotlib{a} 
  python3-numpy{a} python3-openshot{u} python3-pyparsing{u} 
  python3-pyqt5{a} python3-pyqt5.qtsvg{a} python3-pyqt5.qtwebkit{a} 
  python3-sip{u} python3-tz{u} python3-zmq{u} screen-resolution-extra{u} 
  vamp-plugin-sdk{u} xserver-xorg-video-nvidia-390{u} 

The following packages will be upgraded:
  cpp-7 firefox firefox-locale-en gcc-7-base libsqlite3-0 linux-firmware 
6 packages upgraded, 0 newly installed, 143 to remove and 8 not upgraded.
Need to get 52.6 MB/137 MB of archives. After unpacking 759 MB will be freed.

Do you want to continue? [Y/n/?] 


```

Should I accept, as this looks like a DRASTIC change to my system? Does this look right!?!

Thanks!

---

### Post by dino99 on 2020-03-11
Looks like a serious source(s) conflict; dont do the removal except if you wants killing your system :confused:

Check the activated sources (third parties) and may be deactivate the 'proposed' archive, then downgrade if needed

---

### Post by Rick St. George on 2020-03-11
Selected NO. Proposed was not checked. Deselected 'universe' and 'multiverse'. 

Then had this ...

```

~$ sudo aptitude upgrade
Resolving dependencies...                
The following packages will be upgraded:
  cpp-7 firefox firefox-locale-en g++-7 gcc-7 gcc-7-base libasan4 
  libcilkrts5 libgcc-7-dev libgfortran4 libsqlite3-0 libstdc++-7-dev 
  libubsan0 linux-firmware 
14 packages upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
Need to get 52.6 MB/161 MB of archives. After unpacking 4,953 kB will be used.
Do you want to continue? [Y/n/?] y


```

Much better - Right?! The difference too was I used upgrade rather than dist-upgrade. 

Did I do good? And what was the initial problem, and how do I fix it???

---

