---
title: "Problems installing Skype (and other software)"
date: 2013-04-04
forum: General Help
---

### Post by Mongtard on 2013-04-04
Hello all,

I used to have skype installed but, in the process of installing Blender, I managed to uninstall Skype and mess a load of things up (although Blender works :)). Now I'm unable to reinstall Skype. Hopefully the following is self-explanatory:

$ sudo apt-get install skype
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 libatk-wrapper-java-jni : Depends: libatk1.0-0 (>= 1.18.0) but it is not going to be installed
                           Depends: libgtk2.0-0 (>= 2.12.0) but it is not going to be installed
 libpulse0 : Depends: libsndfile1 (>= 1.0.20) but it is not going to be installed
 openjdk-6-jre : Depends: openjdk-6-jre-headless (>= 6b24-1.11.1-4ubuntu2) but it is not going to be installed
 skype : Depends: skype-bin
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

$ sudo aptitude install skype
```
Reading package lists...Building dependency tree...
Reading state information...
Reading extended state information...
Initialising package states...
The following NEW packages will be installed:
  libasound2:i386{ab} libasound2-plugins:i386{a} libasyncns0:i386{a} 
  libaudio2:i386{a} libavahi-client3:i386{a} libavahi-common-data:i386{a} 
  libavahi-common3:i386{a} libc-bin:i386{ab} libc6:i386{ab} 
  libcomerr2:i386{a} libcups2:i386{ab} libdbus-1-3:i386{ab} 
  libdbusmenu-qt2:i386{a} libelf1:i386{a} libexpat1:i386{ab} 
  libffi6:i386{a} libflac8:i386{a} libfontconfig1:i386{ab} 
  libfreetype6:i386{a} libgcc1:i386{a} libgcrypt11:i386{ab} 
  libglib2.0-0:i386{ab} libgnutls26:i386{ab} libgpg-error0:i386{a} 
  libgssapi-krb5-2:i386{ab} libgstreamer-plugins-base0.10-0:i386{ab} 
  libgstreamer0.10-0:i386{a} libice6:i386{a} libjack-jackd2-0:i386{a} 
  libjpeg-turbo8:i386{ab} libjpeg8:i386{a} libjson0:i386{a} 
  libk5crypto3:i386{ab} libkeyutils1:i386{a} libkrb5-3:i386{ab} 
  libkrb5support0:i386{ab} liblcms1:i386{a} libmng1:i386{a} 
  libmysqlclient18:i386{ab} libogg0:i386{a} liborc-0.4-0:i386{a} 
  libp11-kit0:i386{a} libpcre3:i386{a} libpng12-0:i386{a} 
  libpulse0:i386{ab} libqt4-dbus:i386{a} libqt4-declarative:i386{a} 
  libqt4-network:i386{a} libqt4-script:i386{a} libqt4-sql:i386{a} 
  libqt4-sql-mysql:i386{a} libqt4-xml:i386{a} libqt4-xmlpatterns:i386{a} 
  libqtcore4:i386{a} libqtgui4:i386{a} libqtwebkit4:i386{a} 
  libsamplerate0:i386{a} libselinux1:i386{a} libsm6:i386{a} 
  libsndfile1:i386{a} libspeexdsp1:i386{a} libsqlite3-0:i386{ab} 
  libssl1.0.0:i386{ab} libstdc++6:i386{a} libtasn1-3:i386{ab} 
  libtiff4:i386{ab} libuuid1:i386{a} libvorbis0a:i386{a} 
  libvorbisenc2:i386{a} libwrap0:i386{a} libx11-6:i386{a} libxau6:i386{a} 
  libxcb1:i386{a} libxdmcp6:i386{a} libxext6:i386{a} libxi6:i386{a} 
  libxml2:i386{ab} libxrender1:i386{a} libxss1:i386{a} libxt6:i386{a} 
  libxv1:i386{a} skype skype-bin:i386{a} sni-qt:i386{a} zlib1g:i386{a} 
0 packages upgraded, 85 newly installed, 0 to remove and 3 not upgraded.
Need to get 66.0 MB of archives. After unpacking 155 MB will be used.
The following packages have unmet dependencies:
 libkrb5-3 : Breaks: libkrb5-3:i386 (!= 1.10+dfsg~beta1-2ubuntu0.3) but 1.10+dfsg~beta1-2 is to be installed.
 libkrb5-3:i386 : Breaks: libkrb5-3 (!= 1.10+dfsg~beta1-2) but 1.10+dfsg~beta1-2ubuntu0.3 is installed.
 libk5crypto3 : Breaks: libk5crypto3:i386 (!= 1.10+dfsg~beta1-2ubuntu0.3) but 1.10+dfsg~beta1-2 is to be installed.
 libk5crypto3:i386 : Breaks: libk5crypto3 (!= 1.10+dfsg~beta1-2) but 1.10+dfsg~beta1-2ubuntu0.3 is installed.
 libc-bin : Conflicts: libc-bin:i386 but 2.15-0ubuntu10 is to be installed.
 libc-bin:i386 : Conflicts: libc-bin but 2.15-0ubuntu10.2 is installed.
 libjpeg-turbo8 : Breaks: libjpeg-turbo8:i386 (!= 1.1.90+svn733-0ubuntu4.1) but 1.1.90+svn733-0ubuntu4 is to be installed.
 libjpeg-turbo8:i386 : Breaks: libjpeg-turbo8 (!= 1.1.90+svn733-0ubuntu4) but 1.1.90+svn733-0ubuntu4.1 is installed.
 libdbus-1-3 : Breaks: libdbus-1-3:i386 (!= 1.4.18-1ubuntu1.3) but 1.4.18-1ubuntu1 is to be installed.
 libdbus-1-3:i386 : Breaks: libdbus-1-3 (!= 1.4.18-1ubuntu1) but 1.4.18-1ubuntu1.3 is installed.
 libgnutls26 : Breaks: libgnutls26:i386 (!= 2.12.14-5ubuntu3.1) but 2.12.14-5ubuntu3 is to be installed.
 libgnutls26:i386 : Breaks: libgnutls26 (!= 2.12.14-5ubuntu3) but 2.12.14-5ubuntu3.1 is installed.
 libtasn1-3 : Breaks: libtasn1-3:i386 (!= 2.10-1ubuntu1.1) but 2.10-1ubuntu1 is to be installed.
 libtasn1-3:i386 : Breaks: libtasn1-3 (!= 2.10-1ubuntu1) but 2.10-1ubuntu1.1 is installed.
 libglib2.0-0 : Breaks: libglib2.0-0:i386 (!= 2.32.3-0ubuntu1) but 2.32.1-0ubuntu2 is to be installed.
 libglib2.0-0:i386 : Breaks: libglib2.0-0 (!= 2.32.1-0ubuntu2) but 2.32.3-0ubuntu1 is installed.
 libmysqlclient18 : Breaks: libmysqlclient18:i386 (!= 5.5.24-0ubuntu0.12.04.1) but 5.5.22-0ubuntu1 is to be installed.
 libmysqlclient18:i386 : Breaks: libmysqlclient18 (!= 5.5.22-0ubuntu1) but 5.5.24-0ubuntu0.12.04.1 is installed.
 libexpat1 : Breaks: libexpat1:i386 (!= 2.0.1-7.2ubuntu1.1) but 2.0.1-7.2ubuntu1 is to be installed.
 libexpat1:i386 : Breaks: libexpat1 (!= 2.0.1-7.2ubuntu1) but 2.0.1-7.2ubuntu1.1 is installed.
 libcups2 : Breaks: libcups2:i386 (!= 1.5.3-0ubuntu4) but 1.5.2-9ubuntu1 is to be installed.
 libcups2:i386 : Breaks: libcups2 (!= 1.5.2-9ubuntu1) but 1.5.3-0ubuntu4 is installed.
 libkrb5support0 : Breaks: libkrb5support0:i386 (!= 1.10+dfsg~beta1-2ubuntu0.3) but 1.10+dfsg~beta1-2 is to be installed.
 libkrb5support0:i386 : Breaks: libkrb5support0 (!= 1.10+dfsg~beta1-2) but 1.10+dfsg~beta1-2ubuntu0.3 is installed.
 libgcrypt11 : Breaks: libgcrypt11:i386 (!= 1.5.0-3ubuntu0.1) but 1.5.0-3 is to be installed.
 libgcrypt11:i386 : Breaks: libgcrypt11 (!= 1.5.0-3) but 1.5.0-3ubuntu0.1 is installed.
 libxml2 : Breaks: libxml2:i386 (!= 2.7.8.dfsg-5.1ubuntu4.2) but 2.7.8.dfsg-5.1ubuntu4 is to be installed.
 libxml2:i386 : Breaks: libxml2 (!= 2.7.8.dfsg-5.1ubuntu4) but 2.7.8.dfsg-5.1ubuntu4.2 is installed.
 libasound2 : Breaks: libasound2:i386 (!= 1.0.25-1ubuntu10.1) but 1.0.25-1ubuntu10 is to be installed.
 libasound2:i386 : Breaks: libasound2 (!= 1.0.25-1ubuntu10) but 1.0.25-1ubuntu10.1 is installed.
 libtiff4 : Breaks: libtiff4:i386 (!= 3.9.5-2ubuntu1.2) but 3.9.5-2ubuntu1 is to be installed.
 libtiff4:i386 : Breaks: libtiff4 (!= 3.9.5-2ubuntu1) but 3.9.5-2ubuntu1.2 is installed.
 libgstreamer-plugins-base0.10-0 : Breaks: libgstreamer-plugins-base0.10-0:i386 (!= 0.10.36-1ubuntu0.1) but 0.10.36-1 is to be installed.
 libgstreamer-plugins-base0.10-0:i386 : Breaks: libgstreamer-plugins-base0.10-0 (!= 0.10.36-1) but 0.10.36-1ubuntu0.1 is installed.
 libfontconfig1 : Breaks: libfontconfig1:i386 (!= 2.8.0-3ubuntu9.1) but 2.8.0-3ubuntu9 is to be installed.
 libfontconfig1:i386 : Depends: fontconfig-config:i386 (= 2.8.0-3ubuntu9) which is a virtual package.
                       Breaks: libfontconfig1 (!= 2.8.0-3ubuntu9) but 2.8.0-3ubuntu9.1 is installed.
 libpulse0 : Breaks: libpulse0:i386 (!= 1:1.1-0ubuntu15.1) but 1:1.1-0ubuntu15 is to be installed.
 libpulse0:i386 : Breaks: libpulse0 (!= 1:1.1-0ubuntu15) but 1:1.1-0ubuntu15.1 is installed.
 libgssapi-krb5-2 : Breaks: libgssapi-krb5-2:i386 (!= 1.10+dfsg~beta1-2ubuntu0.3) but 1.10+dfsg~beta1-2 is to be installed.
 libgssapi-krb5-2:i386 : Breaks: libgssapi-krb5-2 (!= 1.10+dfsg~beta1-2) but 1.10+dfsg~beta1-2ubuntu0.3 is installed.
 libc6 : Breaks: libc6:i386 (!= 2.15-0ubuntu10.2) but 2.15-0ubuntu10 is to be installed.
 libc6:i386 : Breaks: libc6 (!= 2.15-0ubuntu10) but 2.15-0ubuntu10.2 is installed.
 libsqlite3-0 : Breaks: libsqlite3-0:i386 (!= 3.7.9-2ubuntu1.1) but 3.7.9-2ubuntu1 is to be installed.
 libsqlite3-0:i386 : Breaks: libsqlite3-0 (!= 3.7.9-2ubuntu1) but 3.7.9-2ubuntu1.1 is installed.
 libssl1.0.0 : Breaks: libssl1.0.0:i386 (!= 1.0.1-4ubuntu5.5) but 1.0.1-4ubuntu3 is to be installed.
 libssl1.0.0:i386 : Breaks: libssl1.0.0 (!= 1.0.1-4ubuntu3) but 1.0.1-4ubuntu5.5 is installed.
Internal error: the solver Install(libc-bin:amd64 2.15-0ubuntu10 <libc6:i386 2.15-0ubuntu10 -> {libc-bin:amd64 2.15-0ubuntu10 libc-bin:i386 2.15-0ubuntu10}>) of a supposedly unresolved dependency is already installed in step 108
Internal error: the solver Install(espeak:i386 1.46.02-0ubuntu1 <espeak-data:amd64 1.46.02-0ubuntu1 -S> {espeak:amd64 1.46.02-0ubuntu1 espeak:i386 1.46.02-0ubuntu1}>) of a supposedly unresolved dependency is already installed in step 217
Internal error: the solver Install(espeak:i386 1.46.02-0ubuntu1 <espeak-data:amd64 1.46.02-0ubuntu1 -S> {espeak:amd64 1.46.02-0ubuntu1 espeak:i386 1.46.02-0ubuntu1}>) of a supposedly unresolved dependency is already installed in step 253
Internal error: the solver Install(libc-bin:amd64 2.15-0ubuntu10 <libc6:i386 2.15-0ubuntu10 -> {libc-bin:amd64 2.15-0ubuntu10 libc-bin:i386 2.15-0ubuntu10}>) of a supposedly unresolved dependency is already installed in step 270
Internal error: the solver Install(libc-bin:amd64 2.15-0ubuntu10 <libc6:i386 2.15-0ubuntu10 -> {libc-bin:amd64 2.15-0ubuntu10 libc-bin:i386 2.15-0ubuntu10}>) of a supposedly unresolved dependency is already installed in step 346
Internal error: the solver Install(libc-bin:amd64 2.15-0ubuntu10 <libc6:i386 2.15-0ubuntu10 -> {libc-bin:amd64 2.15-0ubuntu10 libc-bin:i386 2.15-0ubuntu10}>) of a supposedly unresolved dependency is already installed in step 351
The following actions will resolve these dependencies:


      Keep the following packages at their current version:        
1)      libasound2:i386 [Not Installed]                            
2)      libasound2-plugins:i386 [Not Installed]                    
3)      libasyncns0:i386 [Not Installed]                           
4)      libaudio2:i386 [Not Installed]                             
5)      libavahi-client3:i386 [Not Installed]                      
6)      libavahi-common3:i386 [Not Installed]                      
7)      libc-bin:i386 [Not Installed]                              
8)      libc6:i386 [Not Installed]                                 
9)      libcomerr2:i386 [Not Installed]                            
10)     libcups2:i386 [Not Installed]                              
11)     libdbus-1-3:i386 [Not Installed]                           
12)     libdbusmenu-qt2:i386 [Not Installed]                       
13)     libelf1:i386 [Not Installed]                               
14)     libexpat1:i386 [Not Installed]                             
15)     libffi6:i386 [Not Installed]                               
16)     libflac8:i386 [Not Installed]                              
17)     libfontconfig1:i386 [Not Installed]                        
18)     libfreetype6:i386 [Not Installed]                          
19)     libgcc1:i386 [Not Installed]                               
20)     libgcrypt11:i386 [Not Installed]                           
21)     libglib2.0-0:i386 [Not Installed]                          
22)     libgnutls26:i386 [Not Installed]                           
23)     libgpg-error0:i386 [Not Installed]                         
24)     libgssapi-krb5-2:i386 [Not Installed]                      
25)     libgstreamer-plugins-base0.10-0:i386 [Not Installed]       
26)     libgstreamer0.10-0:i386 [Not Installed]                    
27)     libice6:i386 [Not Installed]                               
28)     libjack-jackd2-0:i386 [Not Installed]                      
29)     libjpeg-turbo8:i386 [Not Installed]                        
30)     libjpeg8:i386 [Not Installed]                              
31)     libjson0:i386 [Not Installed]                              
32)     libk5crypto3:i386 [Not Installed]                          
33)     libkeyutils1:i386 [Not Installed]                          
34)     libkrb5-3:i386 [Not Installed]                             
35)     libkrb5support0:i386 [Not Installed]                       
36)     liblcms1:i386 [Not Installed]                              
37)     libmng1:i386 [Not Installed]                               
38)     libmysqlclient18:i386 [Not Installed]                      
39)     libogg0:i386 [Not Installed]                               
40)     liborc-0.4-0:i386 [Not Installed]                          
41)     libp11-kit0:i386 [Not Installed]                           
42)     libpcre3:i386 [Not Installed]                              
43)     libpng12-0:i386 [Not Installed]                            
44)     libpulse0:i386 [Not Installed]                             
45)     libqt4-dbus:i386 [Not Installed]                           
46)     libqt4-declarative:i386 [Not Installed]                    
47)     libqt4-network:i386 [Not Installed]                        
48)     libqt4-script:i386 [Not Installed]                         
49)     libqt4-sql:i386 [Not Installed]                            
50)     libqt4-sql-mysql:i386 [Not Installed]                      
51)     libqt4-xml:i386 [Not Installed]                            
52)     libqt4-xmlpatterns:i386 [Not Installed]                    
53)     libqtcore4:i386 [Not Installed]                            
54)     libqtgui4:i386 [Not Installed]                             
55)     libqtwebkit4:i386 [Not Installed]                          
56)     libsamplerate0:i386 [Not Installed]                        
57)     libselinux1:i386 [Not Installed]                           
58)     libsm6:i386 [Not Installed]                                
59)     libsndfile1:i386 [Not Installed]                           
60)     libspeexdsp1:i386 [Not Installed]                          
61)     libsqlite3-0:i386 [Not Installed]                          
62)     libssl1.0.0:i386 [Not Installed]                           
63)     libstdc++6:i386 [Not Installed]                            
64)     libtasn1-3:i386 [Not Installed]                            
65)     libtiff4:i386 [Not Installed]                              
66)     libuuid1:i386 [Not Installed]                              
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
67)     libvorbis0a:i386 [Not Installed]                           
 68)     libvorbisenc2:i386 [Not Installed]                         
69)     libwrap0:i386 [Not Installed]                              
70)     libx11-6:i386 [Not Installed]                              
71)     libxau6:i386 [Not Installed]                               
72)     libxcb1:i386 [Not Installed]                               
73)     libxdmcp6:i386 [Not Installed]                             
74)     libxext6:i386 [Not Installed]                              
75)     libxi6:i386 [Not Installed]                                
76)     libxml2:i386 [Not Installed]                               
77)     libxrender1:i386 [Not Installed]                           
78)     libxss1:i386 [Not Installed]                               
79)     libxt6:i386 [Not Installed]                                
80)     libxv1:i386 [Not Installed]                                
81)     skype [Not Installed]                                      
82)     skype-bin:i386 [Not Installed]                             
83)     sni-qt:i386 [Not Installed]                                
84)     zlib1g:i386 [Not Installed]                                


      Leave the following dependencies unresolved:                 
85)     libqt4-dbus:i386 recommends qdbus:i386 (= 4:4.8.1-0ubuntu4)
86)     skype-bin:i386 recommends sni-qt:i386                      




Accept this solution? [Y/n/q/?] Abandoning all efforts to resolve these dependencies.
Abort.
```

I have no idea where to start with this. Can someone please push me in the right direction?

Thanks very much in advance.

---

