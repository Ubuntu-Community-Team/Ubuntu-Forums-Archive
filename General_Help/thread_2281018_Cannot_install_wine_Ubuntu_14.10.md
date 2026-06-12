---
title: "Cannot install wine Ubuntu 14.10"
date: 2015-06-03
forum: General Help
---

### Post by musicboy on 2015-06-03
I have tried EVERYTHING I could even editing one of the files for the ubuntu updates with adding multi arch to the deb line here bellow is the full output if anyone has any help and ideas that would be great I have been trying to solve this for 3 days now!!

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


:~$ sudo apt-get isntall wine
[sudo] password for skelmy: 
E: Invalid operation isntall
:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 wine : Depends: wine1.6 or
                 wine1.7
E: Unable to correct problems, you have held broken packages.
:~$ sudo apt-get install wine1.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 wine1.6 : Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu6)
E: Unable to correct problems, you have held broken packages.
:~$ sudo apt-get install wine1.6-i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 wine1.6-i386:i386 : Depends: libgphoto2-6:i386 (>= 2.5.2) but it is not going to be installed
                     Recommends: libsane:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
:~$ sudo apt-get install libsane:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 libsane:i386 : Depends: libgphoto2-6:i386 (>= 2.5.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
:~$ sudo apt-get install libgphoto2-6:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 libgphoto2-6:i386 : Depends: libgd3:i386 (>= 2.1.0~alpha~) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
:~$ sudo apt-get install libgd3:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 libgd3:i386 : Depends: libvpx1:i386 (>= 1.0.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
:~$ sudo apt-get install libvpx1:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 blender : Depends: libavcodec56 (>= 6:11~beta1) but it is not going to be installed or
                    libavcodec-extra-56 (>= 6:11) but it is not going to be installed
 gstreamer0.10-plugins-bad : Depends: libvpx1 (>= 1.0.0) but it is not going to be installed
 gstreamer1.0-libav : Depends: libavcodec56 (>= 6:11~beta1) but it is not going to be installed or
                               libavcodec-extra-56 (>= 6:11) but it is not going to be installed
 idjc : Depends: libavcodec56 (>= 6:11~beta1) but it is not going to be installed or
                 libavcodec-extra-56 (>= 6:11~beta1) but it is not going to be installed
 libavdevice55 : Depends: libavcodec56 (>= 6:11~beta1) but it is not going to be installed or
                          libavcodec-extra-56 (>= 6:11.2) but it is not going to be installed
 libavformat56 : Depends: libavcodec56 (>= 6:11~beta1) but it is not going to be installed or
                          libavcodec-extra-56 (>= 6:11.2) but it is not going to be installed
 libchromaprint0 : Depends: libavcodec56 (>= 6:11~beta1) but it is not going to be installed or
                            libavcodec-extra-56 (>= 6:11~beta1) but it is not going to be installed
 libopencv-highgui2.4 : Depends: libavcodec56 (>= 6:11~beta1) but it is not going to be installed or
                                 libavcodec-extra-56 (>= 6:11~beta1) but it is not going to be installed
 vlc : Depends: libavcodec56 (>= 6:11~beta1) but it is not going to be installed or
                libavcodec-extra-56 (>= 6:11.2) but it is not going to be installed
 vlc-nox : Depends: libavcodec56 (>= 6:11~beta1) but it is not going to be installed or
                    libavcodec-extra-56 (>= 6:11.2) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
:~$ sudo aptitude install wine
The following NEW packages will be installed:
  fonts-horai-umefont{a} fonts-unfonts-core{a} fonts-wqy-microhei{a} 
  libasn1-8-heimdal:i386{a} libcapi20-3{a} libcapi20-3:i386{a} libexif12:i386{a} 
  libgcrypt20:i386{a} libgd3:i386{a} libgif4:i386{a} libgnutls26:i386{a} 
  libgphoto2-6{a} libgphoto2-6:i386{a} libgssapi3-heimdal:i386{a} 
  libgstreamer-plugins-base0.10-0:i386{a} libgstreamer0.10-0:i386{a} 
  libhcrypto4-heimdal:i386{a} libheimbase1-heimdal:i386{a} libheimntlm0-heimdal:i386{a} 
  libhx509-5-heimdal:i386{a} libieee1284-3:i386{a} libkrb5-26-heimdal:i386{a} 
  liblcms2-2:i386{a} libldap-2.4-2:i386{a} libmpg123-0:i386{a} libodbc1{a} 
  libopenal1:i386{a} libosmesa6:i386{a} libp11-kit-gnome-keyring:i386{a} 
  libroken18-heimdal:i386{a} libsane{a} libsane:i386{a} libsasl2-2:i386{a} 
  libsasl2-modules:i386{a} libsasl2-modules-db:i386{a} libv4l-0:i386{a} 
  libv4lconvert0:i386{a} libvpx1:i386{ab} libwind0-heimdal:i386{a} 
  libxcomposite1:i386{a} libxcursor1:i386{a} libxinerama1:i386{a} libxpm4:i386{a} 
  libxrandr2:i386{a} ocl-icd-libopencl1:i386{a} odbcinst{a} odbcinst1debian2{a} 
  p11-kit-modules:i386{a} p7zip{a} ttf-wqy-microhei{a} unixodbc{a} wine 
  wine-gecko2.21{a} wine-gecko2.21:i386{a} wine-mono0.0.8{a} wine1.6{a} 
  wine1.6-amd64{a} wine1.6-i386:i386{a} winetricks{a} 
0 packages upgraded, 59 newly installed, 0 to remove and 0 not upgraded.
Need to get 155 MB of archives. After unpacking 510 MB will be used.
The following packages have unmet dependencies:
 libvpx1 : Breaks: libvpx1:i386 (!= 1.3.0+git20150219-1~gd~u) but 1.3.0-2.1 is to be installed.
 libvpx1:i386 : Breaks: libvpx1 (!= 1.3.0-2.1) but 1.3.0+git20150219-1~gd~u is installed.
The following actions will resolve these dependencies:


      Keep the following packages at their current version:
1)      libgd3:i386 [Not Installed]                        
2)      libgphoto2-6:i386 [Not Installed]                  
3)      libsane:i386 [Not Installed]                       
4)      libvpx1:i386 [Not Installed]                       
5)      wine [Not Installed]                               
6)      wine1.6 [Not Installed]                            
7)      wine1.6-amd64 [Not Installed]                      
8)      wine1.6-i386:i386 [Not Installed]                  


      Leave the following dependencies unresolved:         
9)      wine1.6-i386:i386 recommends libsane:i386          
10)     winetricks recommends wine                         




Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                         
:~$ 

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


I have tried EVERYTHING I could with no results.

That only thing I can actually do is install Ubuntu 14.04 again if this does not work. I have tried everything I could

Thanks :guitar:

---

### Post by mc4man on 2015-06-03
It seems you are using or had used this ppa - 
[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

Is it still enabled?, if not then re-enable, reload your sources & try again 
or
 re-enable, reload your sources & use ppa-purge on the ppa, then try again...

Edit: do note that soon 14.10 is dead & you'll need to either go to 15.04 or back to 14.04. In either case best done as a fresh install or by 1st. purging that ppa if trying a 14.10 > 15.04 upgrade.

---

### Post by mc4man on 2015-06-03
Actually I believe your only choices may be to
1.  purge that ppa if you got for instance libvpx1 from it (1.3.0+git20150219-1~gd~u
or
2. remove libvpx1 which could be a hassle
or
3. downgrade libvpx1 to Ubuntu repo version, you may be able to do so in synaptic or manually always is an option

It appears he has removed it from the ppa for some unknown reason so no source,  no i386 package
There may be other removed sources from that ppa?? It's quite a stupid thing he did..

---

### Post by musicboy on 2015-06-05
Well I fixed it but thank's for the pointers. I resolved some of the dependencies manually then notice that sudo aptitude install wine and some how ubuntu software center got un installed as well ahaha and I have no idea how it must have been messing with the dependencies, I then managed to install wine and ubuntu software centre, to find out that file manager and nautilus had gone as well as settings manager haha i have no idea how all this happened.

I did not realise 14.10 was dead. I had a nightmare working out how to get my right click to work on my click pad on an Acer laptop it drove me up the wall trying to figure out the synaptic file edit trick but that worked. if it happens when installing 15.04 I will be ready and now I have everything working the way I want it to work again I will do a back up and install 15.05.
I have another desktop with 14.04 and its staying that way until I am certain that 15.04 doesn't have all the problems I had with 14.10 to manually fix.

Thank you very much for the replies great pointers.

Sometimes i just plug away different methods and get lucky!!

---

### Post by mc4man on 2015-06-05
All of the non lts releases now only 'live' (EOL) for 9 months. This also includes the ability for ppa's to do new builds, so 15.04 goes eol next Feb, ect. The next lts is 16.04

---

