---
title: "Ubuntu Won't Upgrade To 7.04!"
date: 2007-05-01
forum: General Help
---

### Post by theaverageidiot on 2007-05-01
When I turn my Ubuntu on, it tells me it needs upgrades. I click the icon and it tells me that it can't upgrade because it needs a distribution upgrade. Fine, so I click "Upgrade" to 7.04. It looks like it'll do it then it throws this error:
> Failed to lock /var/lib/apt/lists/lock
Now what?

---

### Post by taurus on 2007-05-01
What happens if you run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by theaverageidiot on 2007-05-03
> **taurus said:**
> What happens if you run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

sudo aptitude update
```
theaverageidiot@theidiots-computer:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Writing extended state information... Done
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]             
Ign http://security.ubuntu.com feisty-security/main Translation-en_US           
Get:2 http://archive.ubuntu.com feisty-updates Release.gpg [191B]               
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_US       
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US     
Get:3 http://archive.canonical.com feisty-commercial Release.gpg [191B]         
Ign http://archive.canonical.com feisty-commercial/main Translation-en_US       
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US       
Get:4 http://us.archive.ubuntu.com feisty Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                  
Hit http://security.ubuntu.com feisty-security Release                          
Get:5 http://archive.ubuntu.com feisty-security Release.gpg [191B]              
Ign http://archive.ubuntu.com feisty-security/main Translation-en_US            
Ign http://archive.ubuntu.com feisty-security/restricted Translation-en_US      
Ign http://archive.ubuntu.com feisty-security/universe Translation-en_US        
Ign http://archive.ubuntu.com feisty-security/multiverse Translation-en_US      
Hit http://archive.canonical.com feisty-commercial Release                      
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US   
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US   
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US              
Get:6 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]            
Hit http://security.ubuntu.com feisty-security/main Packages                    
Hit http://archive.ubuntu.com feisty-updates Release                            
Hit http://archive.canonical.com feisty-commercial/main Packages                
Hit http://archive.ubuntu.com feisty-security Release                           
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/universe Translation-en_US
Hit http://security.ubuntu.com feisty-security/restricted Packages   
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages     
Hit http://security.ubuntu.com feisty-security/restricted Sources    
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://archive.ubuntu.com feisty-security/main Packages
Hit http://archive.ubuntu.com feisty-security/restricted Packages
Hit http://archive.ubuntu.com feisty-security/universe Packages
Hit http://archive.ubuntu.com feisty-security/multiverse Packages
Get:7 http://us.archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://us.archive.ubuntu.com feisty-backports Release
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/universe Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://us.archive.ubuntu.com feisty-updates/universe Sources
Hit http://us.archive.ubuntu.com feisty-backports/main Packages
Hit http://us.archive.ubuntu.com feisty-backports/restricted Packages
Hit http://us.archive.ubuntu.com feisty-backports/universe Packages
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-backports/main Sources
Hit http://us.archive.ubuntu.com feisty-backports/restricted Sources
Hit http://us.archive.ubuntu.com feisty-backports/universe Sources
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Sources
Fetched 7B in 4s (1B/s)
Reading package lists... Done
```

sudo aptitude upgrade (there wasn't enough room, had to cut off a lot of the top)
```
........(lots of stuff here).......
1011 packages upgraded, 0 newly installed, 65 to remove and 352 not upgraded.
Need to get 126MB/685MB of archives. After unpacking 43.2MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 http://us.archive.ubuntu.com feisty/main locales 2.3.23 [3033kB]
Get:2 http://us.archive.ubuntu.com feisty/main libpam-runtime 0.79-4ubuntu2 [66.0kB]
Get:3 http://us.archive.ubuntu.com feisty/main libpam0g 0.79-4ubuntu2 [81.6kB]  
Get:4 http://us.archive.ubuntu.com feisty/main libpam-modules 0.79-4ubuntu2 [191kB]
Get:5 http://us.archive.ubuntu.com feisty/main gzip 1.3.9-2 [75.5kB]            
Get:6 http://us.archive.ubuntu.com feisty/main login 1:4.0.18.1-6ubuntu1 [332kB]
Get:7 http://us.archive.ubuntu.com feisty/main tar 1.16-2 [321kB]               
Get:8 http://us.archive.ubuntu.com feisty/main wget 1.10.2-2ubuntu2 [235kB]     
Get:9 http://us.archive.ubuntu.com feisty/main x11proto-kb-dev 1.0.3-2ubuntu1 [27.0kB]
Get:10 http://us.archive.ubuntu.com feisty/main x11proto-xext-dev 7.0.2-5ubuntu1 [42.2kB]
Get:11 http://us.archive.ubuntu.com feisty/main x11proto-render-dev 2:0.9.2-4ubuntu1 [6960B]
Get:12 http://us.archive.ubuntu.com feisty/main libxrender-dev 1:0.9.1-3 [24.4kB]
Get:13 http://us.archive.ubuntu.com feisty/main libxrender1 1:0.9.1-3 [21.4kB]  
Get:14 http://us.archive.ubuntu.com feisty/main libfontconfig1-dev 2.4.2-1ubuntu1 [344kB]
Get:15 http://us.archive.ubuntu.com feisty/main ttf-bitstream-vera 1.10-7 [354kB]
Get:16 http://us.archive.ubuntu.com feisty/main ttf-freefont 20060501cvs-10 [1802kB]
Get:17 http://us.archive.ubuntu.com feisty/universe cabextract 1.2-2 [53.9kB]   
Get:18 http://us.archive.ubuntu.com feisty/main xfonts-encodings 1:1.0.0-6 [585kB]
Get:19 http://us.archive.ubuntu.com feisty/main xfonts-utils 1:1.0.1-1ubuntu1 [73.6kB]
Get:20 http://us.archive.ubuntu.com feisty/main libfontconfig1 2.4.2-1ubuntu1 [209kB]
Get:21 http://us.archive.ubuntu.com feisty/main fontconfig-config 2.4.2-1ubuntu1 [149kB]
Get:22 http://us.archive.ubuntu.com feisty/main binutils 2.17.20070103cvs-0ubuntu2 [1580kB]
Get:23 http://us.archive.ubuntu.com feisty/main passwd 1:4.0.18.1-6ubuntu1 [793kB]
Get:24 http://us.archive.ubuntu.com feisty/main adduser 3.100 [137kB]           
Get:25 http://us.archive.ubuntu.com feisty/main makedev 2.3.1-83ubuntu2 [42.4kB]
Get:26 http://us.archive.ubuntu.com feisty/main gcc-3.3-base 1:3.3.6-15ubuntu1 [151kB]
Get:27 http://us.archive.ubuntu.com feisty/main libstdc++5 1:3.3.6-15ubuntu1 [296kB]
Get:28 http://us.archive.ubuntu.com feisty/main xutils-dev 1:7.1.ds-6ubuntu1 [300kB]
Get:29 http://us.archive.ubuntu.com feisty/main x11proto-xinerama-dev 1.1.2-4ubuntu1 [5424B]
Get:30 http://us.archive.ubuntu.com feisty/main xkb-data 0.9-4ubuntu1 [384kB]   
Get:31 http://us.archive.ubuntu.com feisty/main libpng12-dev 1.2.15~beta5-1 [172kB]
Get:32 http://us.archive.ubuntu.com feisty/main libpng12-0 1.2.15~beta5-1 [187kB]
Get:33 http://us.archive.ubuntu.com feisty/universe libwxgtk2.4-1 2.4.5.1ubuntu2 [1575kB]
Get:34 http://us.archive.ubuntu.com feisty/main fontconfig 2.4.2-1ubuntu1 [136kB]
Get:35 http://us.archive.ubuntu.com feisty/main libxxf86vm1 1:1.0.1-2 [9856B]   
Get:36 http://us.archive.ubuntu.com feisty/universe 3ddesktop 0.2.9-6 [75.2kB]  
Get:37 http://us.archive.ubuntu.com feisty/main libxdamage1 1:1.0.3-3 [6480B]   
Get:38 http://us.archive.ubuntu.com feisty/main libattr1 1:2.4.32-1.1ubuntu1 [9768B]
Get:39 http://us.archive.ubuntu.com feisty/main libacl1 2.2.42-1ubuntu1 [15.9kB]
Get:40 http://us.archive.ubuntu.com feisty/main mime-support 3.39-1 [30.9kB]    
Get:41 http://us.archive.ubuntu.com feisty/main linux-sound-base 1.0.13-3ubuntu1 [19.1kB]
Get:42 http://us.archive.ubuntu.com feisty/main alsa-base 1.0.13-3ubuntu1 [167kB]
Get:43 http://us.archive.ubuntu.com feisty/main console-tools 1:0.2.3dbs-65ubuntu3 [301kB]
Get:44 http://us.archive.ubuntu.com feisty/main libconsole 1:0.2.3dbs-65ubuntu3 [82.8kB]
Get:45 http://us.archive.ubuntu.com feisty/main console-terminus 4.20-5 [314kB] 
Get:46 http://us.archive.ubuntu.com feisty/main klibc-utils 1.4.30-3ubuntu2 [145kB]
Get:47 http://us.archive.ubuntu.com feisty/main libklibc 1.4.30-3ubuntu2 [43.9kB]
Get:48 http://us.archive.ubuntu.com feisty/main iproute 20061002-3ubuntu1 [285kB]
Get:49 http://us.archive.ubuntu.com feisty/main libiw28 28-1ubuntu3 [30.0kB]    
Get:50 http://us.archive.ubuntu.com feisty/main wireless-tools 28-1ubuntu3 [108kB]
Get:51 http://us.archive.ubuntu.com feisty/main bsdmainutils 6.1.5ubuntu1 [173kB]
Get:52 http://us.archive.ubuntu.com feisty/main cron 3.0pl1-100ubuntu1 [79.4kB] 
Get:53 http://us.archive.ubuntu.com feisty/main dosfstools 2.11-2.1ubuntu3 [53.5kB]
Get:54 http://us.archive.ubuntu.com feisty/main manpages 2.39-1 [484kB]         
Get:55 http://us.archive.ubuntu.com feisty/main pppconfig 2.3.15ubuntu1 [44.4kB]
Get:56 http://us.archive.ubuntu.com feisty/main pppoeconf 1.12ubuntu1 [21.4kB]  
Get:57 http://us.archive.ubuntu.com feisty/main python-support 0.5.6ubuntu1 [23.8kB]
Get:58 http://us.archive.ubuntu.com feisty/main reiserfsprogs 1:3.6.19-4ubuntu2 [476kB]
Get:59 http://us.archive.ubuntu.com feisty/main rsync 2.6.9-3ubuntu1 [260kB]    
Get:60 http://us.archive.ubuntu.com feisty/main strace 4.5.14-2ubuntu1 [95.4kB] 
Get:61 http://us.archive.ubuntu.com feisty/main telnet 0.17-35ubuntu1 [65.6kB]  
Get:62 http://us.archive.ubuntu.com feisty/main w3m 0.5.1-5.1ubuntu1 [1090kB]   
Get:63 http://us.archive.ubuntu.com feisty/main laptop-mode-tools 1.32-1ubuntu1 [94.4kB]
Get:64 http://us.archive.ubuntu.com feisty/main finger 0.17-10ubuntu1 [18.1kB]  
Get:65 http://us.archive.ubuntu.com feisty/universe aircrack-ng 1:0.6.2-7ubuntu1 [191kB]
Get:66 http://us.archive.ubuntu.com feisty/universe aircrack 1:0.6.2-7ubuntu1 [9438B]
Get:67 http://us.archive.ubuntu.com feisty/main intltool-debian 0.35.0+20060710.1 [31.6kB]
Get:68 http://us.archive.ubuntu.com feisty/main po-debconf 1.0.8 [111kB]        
Get:69 http://us.archive.ubuntu.com feisty/main debhelper 5.0.42ubuntu1 [514kB] 
Get:70 http://us.archive.ubuntu.com feisty/main alien 8.65 [104kB]              
Get:71 http://us.archive.ubuntu.com feisty/universe alsa-oss 1.0.12-1 [51.2kB]  
Get:72 http://us.archive.ubuntu.com feisty/main libarts1-dev 1.5.6-0ubuntu1 [1218kB]
Get:73 http://us.archive.ubuntu.com feisty/main libartsc0-dev 1.5.6-0ubuntu1 [20.8kB]
Get:74 http://us.archive.ubuntu.com feisty/main libartsc0 1.5.6-0ubuntu1 [14.8kB]
Get:75 http://us.archive.ubuntu.com feisty/universe liba52-0.7.4 0.7.4-7 [26.4kB]
Get:76 http://us.archive.ubuntu.com feisty/main libvorbis-dev 1.1.2.dfsg-1.2 [446kB]
Get:77 http://us.archive.ubuntu.com feisty/main libvorbisenc2 1.1.2.dfsg-1.2 [75.4kB]
Get:78 http://us.archive.ubuntu.com feisty/main libvorbisfile3 1.1.2.dfsg-1.2 [18.5kB]
Get:79 http://us.archive.ubuntu.com feisty/main libvorbis0a 1.1.2.dfsg-1.2 [98.3kB]
Get:80 http://us.archive.ubuntu.com feisty/universe libavcodec0d 3:0.cvs20060823-3.1ubuntu4 [1513kB]
Get:81 http://us.archive.ubuntu.com feisty/universe libmpeg2-4 0.4.1-1 [64.1kB]                                                                              
Get:82 http://us.archive.ubuntu.com feisty/universe libpostproc0d 3:0.cvs20060823-3.1ubuntu4 [35.6kB]                                                        
Get:83 http://us.archive.ubuntu.com feisty/universe libpvm3 3.4.5-7 [85.7kB]                                                                                 
Get:84 http://us.archive.ubuntu.com feisty/main xterm 223-1 [439kB]                                                                                          
Get:85 http://us.archive.ubuntu.com feisty/main gnome-mime-data 2.4.3-1 [361kB]                                                                              
Get:86 http://us.archive.ubuntu.com feisty/main gstreamer0.10-esd 0.10.5-1ubuntu2 [37.7kB]                                                                   
Get:87 http://us.archive.ubuntu.com feisty/main libspeex1 1.1.12-3 [76.7kB]                                                                                  
Get:88 http://us.archive.ubuntu.com feisty/main libestools1.2 1:1.2.3-9.4ubuntu1 [1319kB]                                                                    
Get:89 http://us.archive.ubuntu.com feisty/main festival 1.4.3-17.2ubuntu1 [729kB]                                                                           
Get:90 http://us.archive.ubuntu.com feisty/main libarts1c2a 1.5.6-0ubuntu1 [995kB]                                                                           
Get:91 http://us.archive.ubuntu.com feisty/main libattr1-dev 1:2.4.32-1.1ubuntu1 [30.0kB]                                                                    
Get:92 http://us.archive.ubuntu.com feisty/main libacl1-dev 2.2.42-1ubuntu1 [76.4kB]                                                                         
Get:93 http://us.archive.ubuntu.com feisty/main hicolor-icon-theme 0.10-1ubuntu1 [10.8kB]                                                                    
Get:94 http://us.archive.ubuntu.com feisty/main dictionaries-common 0.70.11ubuntu1 [252kB]                                                                   
Get:95 http://us.archive.ubuntu.com feisty/main aspell-en 6.0-0-5.1 [249kB]                                                                                  
Get:96 http://us.archive.ubuntu.com feisty/main autoconf 2.61-3 [448kB]                                                                                      
Get:97 http://us.archive.ubuntu.com feisty/main autotools-dev 20060920.1 [61.1kB]                                                                            
Get:98 http://us.archive.ubuntu.com feisty/main automake1.4 1:1.4-p6-12 [272kB]                                                                              
Get:99 http://us.archive.ubuntu.com feisty/universe bchunk 1.2.0-4 [13.5kB]                                                                                  
Get:100 http://us.archive.ubuntu.com feisty/main binutils-static 2.17.20070103cvs-0ubuntu2 [586kB]                                                           
Get:101 http://us.archive.ubuntu.com feisty/universe libavformat0d 3:0.cvs20060823-3.1ubuntu4 [286kB]                                                        
Get:102 http://us.archive.ubuntu.com feisty/main ca-certificates 20061027 [93.1kB]                                                                           
Get:103 http://us.archive.ubuntu.com feisty/main cli-common 0.4.6 [167kB]                                                                                    
Get:104 http://us.archive.ubuntu.com feisty/universe d4x 2.5.7.1-4 [739kB]                                                                                   
Get:105 http://us.archive.ubuntu.com feisty/universe d4x-common 2.5.7.1-4 [674kB]                                                                            
Get:106 http://us.archive.ubuntu.com feisty/multiverse daemontools-installer 0.76-9.2 [16.5kB]                                                               
Get:107 http://us.archive.ubuntu.com feisty/universe debsums 2.0.30 [30.6kB]                                                                                 
Get:108 http://us.archive.ubuntu.com feisty/main dh-make 0.42 [33.6kB]                                                                                       
Get:109 http://us.archive.ubuntu.com feisty/universe dvdauthor 0.6.11-5 [141kB]                                                                              
Get:110 http://us.archive.ubuntu.com feisty/universe edgy-session-splashes 0.5-0ubuntu1 [110kB]                                                              
Get:111 http://us.archive.ubuntu.com feisty/universe edgy-wallpapers 0.9-0ubuntu1 [1094kB]                                                                   
Get:112 http://us.archive.ubuntu.com feisty/universe egoboo-data 2.220-1 [15.6MB]                                                                            
Get:113 http://us.archive.ubuntu.com feisty/universe ffmpeg 3:0.cvs20060823-3.1ubuntu4 [181kB]                                                               
Get:114 http://us.archive.ubuntu.com feisty/multiverse figlet 2.2.2-1 [151kB]                                                                                
Get:115 http://us.archive.ubuntu.com feisty/universe freedoom 0.5-1 [7082kB]                                                                                 
Get:116 http://us.archive.ubuntu.com feisty/universe libfluidsynth1 1.0.7a-1 [156kB]                                                                         
Get:117 http://us.archive.ubuntu.com feisty/main ttf-dustin 20030517-4 [621kB]                                                                               
Get:118 http://us.archive.ubuntu.com feisty/universe freewheeling 0.5.2a-1build1 [234kB]                                                                     
Get:119 http://us.archive.ubuntu.com feisty/main libsdl-mixer1.2 1.2.6-1.1build1 [136kB]                                                                     
Get:120 http://us.archive.ubuntu.com feisty/main libg2c0 1:3.4.6-5ubuntu1 [50.4kB]                                                                           
Get:121 http://us.archive.ubuntu.com feisty/main gcc-3.4-base 3.4.6-5ubuntu1 [165kB]                                                                         
Get:122 http://us.archive.ubuntu.com feisty/universe gdesklets-data 0.35.6-1 [3931kB]                                                                        
Get:123 http://us.archive.ubuntu.com feisty/universe gocr 0.41-1ubuntu1 [322kB]                                                                              
Get:124 http://us.archive.ubuntu.com feisty/universe gpe-taskmanager 0.20-2 [15.6kB]                                                                         
Get:125 http://us.archive.ubuntu.com feisty/main gsfonts 1:8.11+urwcyr1.0.7~pre41-1 [4648kB]                                                                 
Get:126 http://us.archive.ubuntu.com feisty/main gs-common 0.3.11ubuntu1 [50.3kB]                                                                            
Get:127 http://us.archive.ubuntu.com feisty/universe gstreamer0.10-ffmpeg 0.10.2-0ubuntu4 [2880kB]                                                           
Get:128 http://us.archive.ubuntu.com feisty/multiverse libxvidcore4 2:1.1.2-0.1ubuntu1 [177kB]                                                               
Get:129 http://us.archive.ubuntu.com feisty/multiverse gstreamer0.10-plugins-bad-multiverse 0.10.4-3 [80.6kB]                                                
Get:130 http://us.archive.ubuntu.com feisty/universe gstreamer0.10-plugins-ugly 0.10.5-0ubuntu2 [207kB]                                                      
Get:131 http://us.archive.ubuntu.com feisty/multiverse gstreamer0.10-plugins-ugly-multiverse 0.10.5-2 [40.0kB]                                               
Get:132 http://us.archive.ubuntu.com feisty/universe libdvdnav4 0.1.10-0.1 [92.1kB]                                                                          
Get:133 http://us.archive.ubuntu.com feisty/universe gstreamer0.8-ffmpeg 0.8.7-10ubuntu1 [2367kB]                                                            
Get:134 http://us.archive.ubuntu.com feisty/main iso-codes 1.0-1 [1529kB]                                                                                    
Get:135 http://us.archive.ubuntu.com feisty/universe libjsw2 1:1.5.6-0ubuntu1 [27.1kB]                                                                       
Get:136 http://us.archive.ubuntu.com feisty/universe jscalibrator 1:1.5.6-0ubuntu1 [304kB]                                                                   
Get:137 http://us.archive.ubuntu.com feisty/main libopenobex1 1.3-3 [21.0kB]                                                                                 
Get:138 http://us.archive.ubuntu.com feisty/universe kftpgrabber 0.8.0-0ubuntu1 [1137kB]                                                                     
Get:139 http://us.archive.ubuntu.com feisty/universe lastfm 1.1.90-4 [478kB]                                                                                 
Get:140 http://us.archive.ubuntu.com feisty/universe libcfitsio2 2.510-1.3 [458kB]                                                                           
Get:141 http://us.archive.ubuntu.com feisty/main libenchant1c2a 1.3.0-2ubuntu1 [162kB]                                                                       
Get:142 http://us.archive.ubuntu.com feisty/universe libfile-which-perl 0.05-7 [12.2kB]                                                                      
Get:143 http://us.archive.ubuntu.com feisty/universe libflash-swfplayer 0.4.13-9ubuntu1 [13.3kB]                                                             
Get:144 http://us.archive.ubuntu.com feisty/universe libflash0c2 0.4.13-9ubuntu1 [70.2kB]                                                                    
Get:145 http://us.archive.ubuntu.com feisty/main libgda2-common 1.2.4-0ubuntu1 [81.0kB]                                                                      
Get:146 http://us.archive.ubuntu.com feisty/main libgda2-3 1.2.4-0ubuntu1 [230kB]                                                                            
Get:147 http://us.archive.ubuntu.com feisty/universe libgeos2c2a 2.2.3-3 [363kB]                                                                             
Get:148 http://us.archive.ubuntu.com feisty/universe libgii1 1:1.0.1-3 [235kB]                                                                               
Get:149 http://us.archive.ubuntu.com feisty/universe libgii1-target-x 1:1.0.1-3 [15.9kB]                                                                     
Get:150 http://us.archive.ubuntu.com feisty/main libxxf86dga1 2:1.0.1-2 [11.2kB]                                                                             
Get:151 http://us.archive.ubuntu.com feisty/universe libggi2 1:2.2.1-5ubuntu1 [481kB]                                                                        
Get:152 http://us.archive.ubuntu.com feisty/main libglibmm-2.4-1c2a 2.13.3-0ubuntu1 [148kB]                                                                  
Get:153 http://us.archive.ubuntu.com feisty/main libgmime-2.0-2 2.2.3-3ubuntu1 [184kB]                                                                       
Get:154 http://us.archive.ubuntu.com feisty/main libgmime2.2-cil 2.2.3-3ubuntu1 [95.2kB]                                                                     
Get:155 http://us.archive.ubuntu.com feisty/main libgnome-pilot2 2.0.15-0.1ubuntu1 [114kB]                                                                   
Get:156 http://us.archive.ubuntu.com feisty/main libkpathsea4 3.0-27ubuntu1 [81.9kB]                                                                         
Get:157 http://us.archive.ubuntu.com feisty/universe libmp3-info-perl 1.20-1 [37.7kB]                                                                        
Get:158 http://us.archive.ubuntu.com feisty/universe libopenal0a 1:0.0.8-3 [126kB]                                                                           
Get:159 http://us.archive.ubuntu.com feisty/main libsmokeqt1 4:3.5.5-1ubuntu4 [1312kB]                                                                       
Get:160 http://us.archive.ubuntu.com feisty/universe libqt0-ruby1.8 4:3.5.5-1ubuntu4 [324kB]                                                                 
Get:161 http://us.archive.ubuntu.com feisty/universe libxdelta2 1.1.3-7 [53.5kB]                                                                             
Get:162 http://us.archive.ubuntu.com feisty/main libxkbfile1 1:1.0.3-2 [67.8kB]                                                                              
Get:163 http://us.archive.ubuntu.com feisty/main libxmlsec1 1.2.9-5ubuntu1 [134kB]                                                                           
Get:164 http://us.archive.ubuntu.com feisty/main libxmlsec1-nss 1.2.9-5ubuntu1 [79.1kB]                                                                      
Get:165 http://us.archive.ubuntu.com feisty/main libxmlsec1-openssl 1.2.9-5ubuntu1 [84.8kB]                                                                  
Get:166 http://us.archive.ubuntu.com feisty/main libxres1 2:1.0.1-2 [5914B]                                                                                  
Get:167 http://us.archive.ubuntu.com feisty/main libxss1 1:1.1.0-1 [6718B]                                                                                   
Get:168 http://us.archive.ubuntu.com feisty/main libxxf86misc1 1:1.0.1-2 [7650B]                                                                             
Get:169 http://us.archive.ubuntu.com feisty/universe libzzip-0-12 0.12.83-8 [34.9kB]                                                                         
Get:170 http://us.archive.ubuntu.com feisty/universe localepurge 0.5.8 [37.0kB]                                                                              
Get:171 http://us.archive.ubuntu.com feisty/universe lomoco 1.0beta1+1.0-5 [15.8kB]                                                                          
Get:172 http://us.archive.ubuntu.com feisty/universe module-assistant 0.10.10 [88.5kB]                                                                       
Get:173 http://us.archive.ubuntu.com feisty/universe moto4lin 0.3+svn20060819-1 [151kB]                                                                      
Get:174 http://us.archive.ubuntu.com feisty/multiverse mozilla-mplayer 3.31+main-1ubuntu1 [489kB]                                                            
Get:175 http://us.archive.ubuntu.com feisty/main myspell-en-gb 1:2.0.4~rc1-3ubuntu1 [254kB]                                                                  
Get:176 http://us.archive.ubuntu.com feisty/main myspell-en-us 1:2.0.4~rc1-3ubuntu1 [252kB]                                                                  
Get:177 http://us.archive.ubuntu.com feisty/universe nn 6.7.3-1 [357kB]                                                                                      
Get:178 http://us.archive.ubuntu.com feisty/universe obexftp 0.19-7 [33.8kB]                                                                                 
Get:179 http://us.archive.ubuntu.com feisty/main openoffice.org-thesaurus-en-us 1:2.0.4~rc1-3ubuntu1 [5141kB]                                                
Get:180 http://us.archive.ubuntu.com feisty/universe p7zip 4.43~dfsg.1-1 [323kB]                                                                             
Get:181 http://us.archive.ubuntu.com feisty/universe p7zip-full 4.43~dfsg.1-1 [1393kB]                                                                       
Get:182 http://us.archive.ubuntu.com feisty/main portmap 5-24 [33.9kB]                                                                                       
Get:183 http://us.archive.ubuntu.com feisty/main powernowd 0.97-1ubuntu7 [24.8kB]                                                                            
Get:184 http://us.archive.ubuntu.com feisty/universe prboom 2:2.4.6+dfsg-1 [386kB]                                                                           
Get:185 http://us.archive.ubuntu.com feisty/main pykdeextensions 0.4.0-3ubuntu1 [108kB]                                                                      
Get:186 http://us.archive.ubuntu.com feisty/universe python-pygame 1.7.1release-4.1 [808kB]                                                                  
Get:187 http://us.archive.ubuntu.com feisty/main python-twisted-web 0.7.0-0ubuntu1 [316kB]                                                                   
Get:188 http://us.archive.ubuntu.com feisty/main python-twisted-lore 0.3.0-0ubuntu1 [76.0kB]                                                                 
Get:189 http://us.archive.ubuntu.com feisty/main python-twisted-mail 0.4.0-0ubuntu1 [164kB]                                                                  
Get:190 http://us.archive.ubuntu.com feisty/main python-twisted-names 0.4.0-0ubuntu1 [46.7kB]                                                                
Get:191 http://us.archive.ubuntu.com feisty/main python-twisted-news 0.3.0-0ubuntu1 [26.3kB]                                                                 
Get:192 http://us.archive.ubuntu.com feisty/main python-twisted-words 0.5.0-0ubuntu1 [197kB]                                                                 
Get:193 http://us.archive.ubuntu.com feisty/main tcl8.4 8.4.14-0ubuntu1 [1163kB]                                                                             
Get:194 http://us.archive.ubuntu.com feisty/main tk8.4 8.4.14-0ubuntu2 [996kB]                                                                               
Get:195 http://us.archive.ubuntu.com feisty/multiverse snes9x-x 1:1.5-1 [683kB]                                                                              
Get:196 http://us.archive.ubuntu.com feisty/universe soundkonverter 0.3.1-0ubuntu1 [374kB]                                                                   
Get:197 http://us.archive.ubuntu.com feisty/universe sox 12.18.2-1 [331kB]                                                                                   
Get:198 http://us.archive.ubuntu.com feisty/universe streamripper 1.61.27-1 [70.8kB]                                                                         
Get:199 http://us.archive.ubuntu.com feisty/universe plib1.8.4c2 1.8.4-6ubuntu1 [634kB]                                                                      
Get:200 http://us.archive.ubuntu.com feisty/main ttf-arphic-ukai 0.1.20060928-2 [12.0MB]                                                                     
Get:201 http://us.archive.ubuntu.com feisty/main ttf-bengali-fonts 1:0.4.7.3 [433kB]                                                                         
Get:202 http://us.archive.ubuntu.com feisty/main ttf-devanagari-fonts 1:0.4.7.3 [1177kB]                                                                     
Get:203 http://us.archive.ubuntu.com feisty/main ttf-gujarati-fonts 1:0.4.7.3 [219kB]                                                                        
Get:204 http://us.archive.ubuntu.com feisty/main ttf-kannada-fonts 1:0.4.7.3 [465kB]                                                                         
Get:205 http://us.archive.ubuntu.com feisty/main ttf-malayalam-fonts 1:0.4.7.3 [52.9kB]                                                                      
Get:206 http://us.archive.ubuntu.com feisty/main ttf-oriya-fonts 1:0.4.7.3 [97.7kB]                                                                          
Get:207 http://us.archive.ubuntu.com feisty/main ttf-punjabi-fonts 1:0.4.7.3 [80.2kB]                                                                        
Get:208 http://us.archive.ubuntu.com feisty/main ttf-tamil-fonts 1:0.4.7.3 [400kB]                                                                           
Get:209 http://us.archive.ubuntu.com feisty/main ttf-telugu-fonts 1:0.4.7.3 [221kB]                                                                          
Get:210 http://us.archive.ubuntu.com feisty/main ttf-indic-fonts 1:0.4.7.3 [4722B]                                                                           
Get:211 http://us.archive.ubuntu.com feisty/main x-ttcidfont-conf 25 [24.3kB]                                                                                
Get:212 http://us.archive.ubuntu.com feisty/universe ussp-push 0.9-2 [15.2kB]                                                                                
Get:213 http://us.archive.ubuntu.com feisty/main xcursor-themes 1.0.1-5ubuntu1 [462kB]                                                                       
Get:214 http://us.archive.ubuntu.com feisty/universe xdelta 1.1.3-7 [28.5kB]                                                                                 
Get:215 http://us.archive.ubuntu.com feisty/main xfonts-100dpi 1:1.0.0-3 [3907kB]                                                                            
Get:216 http://us.archive.ubuntu.com feisty/main xfonts-75dpi 1:1.0.0-3 [3471kB]                                                                             
Get:217 http://us.archive.ubuntu.com feisty/main xfonts-base 1:1.0.0-4 [6131kB]                                                                              
Get:218 http://us.archive.ubuntu.com feisty/main xfonts-scalable 1:1.0.0-6 [342kB]                                                                           
Get:219 http://us.archive.ubuntu.com feisty/multiverse zsnes 1.420-2.1ubuntu1 [526kB]                                                                        
Get:220 http://us.archive.ubuntu.com feisty/universe bluez-hcidump 1.33-0ubuntu1 [80.5kB]                                                                    
Get:221 http://us.archive.ubuntu.com feisty/main cdrdao 1:1.2.2-5ubuntu1 [432kB]                                                                             
Get:222 http://us.archive.ubuntu.com feisty/main dcraw 8.39-1 [136kB]                                                                                        
Get:223 http://us.archive.ubuntu.com feisty/main python-twisted-conch 1:0.8.0-0ubuntu1 [173kB]                                                               
Get:224 http://us.archive.ubuntu.com feisty/universe xkeyboard-config 0.9-4ubuntu1 [21.7kB]                                                                  
Fetched 126MB in 24m2s (87.3kB/s)                                                                                                                            
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 189169 files and directories currently installed.)
Removing kdm ...
Removing kdnssd ...
Removing keep ...
Removing kio-apt ...
Removing kio-locate ...
Removing kipi-plugins ...
Removing kitchensync ...
Removing kmag ...
Removing kmailcvt ...
Removing kmilo ...
Removing kmix ...
Removing kmousetool ...
Removing kmplayer-konq-plugins ...
Removing kmplayer-base ...
Removing knetworkconf ...
Removing knode ...
Removing knotes ...
Removing krita ...
Removing koffice-libs ...
Removing koffice-data ...
Removing konq-plugins ...
Removing kontact ...
Removing konversation ...
Removing kooka ...
Removing korganizer ...
Removing kpf ...
Removing kppp ...
Removing krdc ...
Removing krfb ...
Removing krita-data ...
Removing kscd ...
Removing kscreensaver ...
Removing kscreensaver-xsavers ...
Removing ksnapshot ...
Removing ksplash-engine-moodin ...
Removing ksvg ...
Removing ksystemlog ...
Removing kubuntu-artwork-usplash ...
Removing kubuntu-docs ...
Removing kubuntu-konqueror-shortcuts ...
Removing kwalletmanager ...
Removing kwin-style-crystal ...
Removing latex-xft-fonts ...
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
opendir: No such file or directory
Regenerating fonts cache...done.
Removing libgphoto2-2-dev ...
Removing libexif-dev ...
Removing libgsl0 ...
Removing libkexif1 ...
Removing libkipi0 ...
Removing libkpimexchange1 ...
Removing libkscan1 ...
Removing libmagick++9c2a ...
Removing libpoppler1-qt ...
Removing libpythonize0 ...
Removing libqt-perl ...
Removing rdiff-backup ...
Removing librsync1 ...
Removing skim ...
Removing libskim0 ...
Removing libtdb1 ...
Removing openoffice.org-kde ...
Removing python-qt4 ...
Removing python-elementtree ...
Removing scim-qtimm ...
Removing speedcrunch ...
Removing wlassistant ...
dpkg: syntax error: unknown user `postfix' in statoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
```

---

### Post by theaverageidiot on 2007-05-03
bumperz:popcorn:

---

### Post by theaverageidiot on 2007-05-03
:KS Bu-bu-BUMP! :KS

---

### Post by theaverageidiot on 2007-05-03
bump

---

### Post by theaverageidiot on 2007-05-03
Bump

---

### Post by riksweeney on 2007-05-03
Run the update again and see what happens this time

---

### Post by theaverageidiot on 2007-05-03
> **riksweeney said:**
> Run the update again and see what happens this time

```
theaverageidiot@theidiots-computer:~$ sudo aptitude upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  amarok-xine amule-common apache2-mpm-prefork apache2-utils dvipng 
  fb-music-high frozen-bubble-data gambas-gb-db-postgresql gftp-common 
  gstreamer0.8-caca gstreamer0.8-gtk gstreamer0.8-misc kaffeine-xine 
  kdepim-kio-plugins libapache2-mod-php5 libgnash0 libgtkmm-2.4-1c2a 
  libjack0.100.0-0 libqt4-qt3support libqt4-sql libwxgtk2.6-0 libxine1 
  linux-image-generic linux-restricted-modules-generic mixxx-data 
  network-manager nfs-common openoffice.org-style-crystal php5-common 
  php5-mysql postfix python-dev python-matplotlib-data qt4-qtconfig vlc 
  vlc-nox xchat-common 
The following packages have been kept back:
  amarok amule apache2 apport apport-gtk apt apt-utils aptitude at-spi 
  audacity avahi-daemon avidemux beep-media-player beep-media-player-dev 
  bind9-host bittorrent bluefish bluez-pin brltty brltty-x11 bug-buddy 
  capplets-data cdda2wav cdrecord contact-lookup-applet cupsys-bsd 
  cupsys-client deskbar-applet dnsutils dvd+rw-tools easytag ekiga eog 
  evince evolution evolution-data-server evolution-data-server-common 
  evolution-exchange evolution-plugins evolution-webcal f-spot 
  fglrx-kernel-source file-roller firefox firefox-gnome-support foo2zjs 
  frozen-bubble gaim gaim-data gcalctool gconf-editor gconf2 gconf2-common 
  gdebi gdesklets gdm gedit gedit-common gftp-gtk gimp gimp-data gimp-print 
  gimp-python gksu gnash gnome-about gnome-app-install gnome-applets 
  gnome-applets-data gnome-bluetooth gnome-control-center 
  gnome-cups-manager gnome-games gnome-games-data gnome-keyring 
  gnome-keyring-manager gnome-mag gnome-media gnome-media-common 
  gnome-menus gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel 
  gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager 
  gnome-screensaver gnome-session gnome-spell gnome-system-monitor 
  gnome-system-tools gnome-terminal gnome-terminal-data gnome-utils 
  gnome-volume-manager gnupg gs-esp gstreamer0.10-plugins-bad 
  gstreamer0.10-plugins-good gstreamer0.10-x gthumb gtk2-engines 
  gtk2-engines-pixbuf gtk2-engines-ubuntulooks gtkhtml3.8 gtkpod gucharmap 
  hal hplip hplip-data human-theme jackd k3b kate kcontrol kdebase-bin 
  kdebase-data kdebase-dev kdebase-kio-plugins kdeprint kdesktop kfind 
  khelpcenter kicker klash klipper kmenuedit konqueror konqueror-nsplugins 
  konsole ksmserver ksplash ksysguard ksysguardd kwin language-support-en 
  libapache2-mod-auth-mysql libatspi1.0-0 libbind9-0 libbonoboui2-0 
  libbonoboui2-common libdevmapper1.02 libebook1.2-9 libecal1.2-7 
  libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2 
  libeel2-data libgail-common libgail18 libgconf2-4 libgimp2.0 libgksu2-0 
  libgksuui1.0-1 libglade2-0 libglade2.0-cil libgnome-desktop-2 
  libgnome-keyring0 libgnome-media0 libgnome-speech3 
  libgnome-window-settings1 libgnome2-canvas-perl libgnome2.0-cil 
  libgnomebt0 libgnomecanvas2-0 libgnomecanvas2-common 
  libgnomecupsui1.0-1c2a libgnomeprint2.2-0 libgnomeprint2.2-data 
  libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 
  libgnomeui-common libgpod-dev libgtk2-perl libgtk2.0-0 libgtk2.0-bin 
  libgtk2.0-cil libgtk2.0-dev libgtkhtml2-0 libgtkhtml3.8-15 
  libgtksourceview1.0-0 libgutenprintui2-1 libisccfg1 
  liblaunchpad-integration0 libldap2 libldap2-dev liblpint-bonobo0 
  libmetacity0 libmono-system1.0-cil libnautilus-burn4 
  libnautilus-extension1 libnet-dbus-perl libnotify1 libnss-mdns 
  libopal-2.2.0 libpanel-applet2-0 libpango1.0-0 libpango1.0-dev 
  libpoppler1 libpoppler1-glib libpt-1.10.0 libpt-plugins-alsa 
  libpt-plugins-v4l libpt-plugins-v4l2 libsasl2 libsasl2-dev 
  libsasl2-modules libsdl1.2debian libsdl1.2debian-alsa libsexy2 
  libtotem-plparser1 libvte-common libvte9 libwnck18 libxalan2-java 
  libxerces2-java libxerces27 libxfcegui4-4 libxine-extracodecs 
  linux-headers-generic metacity metacity-common mixxx mjpegtools mkisofs 
  mozilla-plugin-vlc mplayer nautilus nautilus-cd-burner nautilus-data 
  nautilus-sendto netbase network-manager-gnome nfs-kernel-server 
  notification-daemon ntfsprogs openoffice.org openoffice.org-base 
  openoffice.org-calc openoffice.org-common openoffice.org-core 
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress 
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math 
  openoffice.org-style-default openoffice.org-style-industrial 
  openoffice.org-writer php5 python python-apt python-at-spi python-glade2 
  python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras 
  python-gnomecanvas python-gpod python-gtk2 python-gtk2-dev 
  python-gtkhtml2 python-matplotlib python-minimal python-uno python-vte 
  quicktime-x11utils rhythmbox samba samba-common scim scim-gtk2-immodule 
  scim-modules-socket scite serpentine smbclient sound-juicer 
  ssh-askpass-gnome streamtuner subversion synaptic timidity 
  timidity-interfaces-extra tomboy totem totem-mozilla totem-xine tsclient 
  ubuntu-artwork ubuntu-desktop ubuntu-docs udev update-manager 
  update-notifier usplash vbetool vino volumeid xarchiver xcdroast xchat 
  xfwm4 xfwm4-themes xine-ui yelp zenity 
The following packages will be upgraded:
  3ddesktop acpi-support acpid adduser aircrack aircrack-ng alacarte alien 
  alsa-base alsa-oss alsa-utils anacron apmd app-install-data 
  app-install-data-commercial ark aspell-en at autoconf automake1.4 
  autotools-dev base-files bash bc bchunk bcm43xx-fwcutter 
  belocs-locales-bin binutils binutils-static blender bluetooth bluez-btsco 
  bluez-cups bluez-hcidump bluez-pcmcia-support bluez-utils bsdmainutils 
  bsdutils busybox-initramfs bzip2 ca-certificates cabextract cdparanoia 
  cdrdao cli-common comerr-dev console-setup console-terminus console-tools 
  coreutils cpp cpp-4.1 cron cupsys cupsys-common cupsys-driver-gutenprint 
  cvs d4x d4x-common daemontools-installer dash dbus dbus-1-utils dc dcraw 
  debconf debconf-i18n debhelper debianutils debsums desktop-file-utils 
  dh-make dhcdbd dhcp3-client dhcp3-common dictionaries-common diff 
  diveintopython doc-base dosfstools dpkg dpkg-dev dselect dvdauthor dvdrip 
  e2fslibs e2fsprogs edgy-community-wallpapers edgy-gdm-themes 
  edgy-session-splashes edgy-wallpapers egoboo-data eject enscript esound 
  esound-common ethtool example-content fakeroot fdutils festival ffmpeg 
  fglrx-control figlet file findutils finger flac fontconfig 
  fontconfig-config foomatic-db foomatic-db-engine foomatic-db-hpijs 
  foomatic-filters fortune-mod fortunes-min freedoom freewheeling 
  fuse-utils g++ g++-4.1 gambas gambas-doc gambas-gb-compress gambas-gb-db 
  gambas-gb-db-mysql gambas-gb-db-sqlite gambas-gb-debug gambas-gb-eval 
  gambas-gb-net gambas-gb-net-curl gambas-gb-qt gambas-gb-qt-editor 
  gambas-gb-qt-ext gambas-gb-qt-kde gambas-gb-qt-kde-html gambas-gb-sdl 
  gambas-gb-vb gambas-gb-xml gambas-runtime gamin gawk gcc gcc-3.3-base 
  gcc-3.4-base gcc-4.1 gcc-4.1-base gcj-4.1-base gdb gdesklets-data gettext 
  gettext-base gij gij-4.1 gnome-accessibility-themes gnome-btdownload 
  gnome-desktop-data gnome-doc-utils gnome-icon-theme gnome-mime-data 
  gnome-themes gocr gpe-taskmanager grep grub gs-common gsfonts 
  gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-ffmpeg 
  gstreamer0.10-gnomevfs gstreamer0.10-pitfdll 
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base 
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-ugly 
  gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-tools 
  gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-alsa gstreamer0.8-artsd 
  gstreamer0.8-audiofile gstreamer0.8-cdio gstreamer0.8-cdparanoia 
  gstreamer0.8-dv gstreamer0.8-dvd gstreamer0.8-esd gstreamer0.8-festival 
  gstreamer0.8-ffmpeg gstreamer0.8-flac gstreamer0.8-gnomevfs 
  gstreamer0.8-gsm gstreamer0.8-hermes gstreamer0.8-jpeg gstreamer0.8-mad 
  gstreamer0.8-mikmod gstreamer0.8-mms gstreamer0.8-mpeg2dec 
  gstreamer0.8-musepack gstreamer0.8-oss gstreamer0.8-plugin-apps 
  gstreamer0.8-plugins gstreamer0.8-sdl gstreamer0.8-sid gstreamer0.8-speex 
  gstreamer0.8-swfdec gstreamer0.8-theora gstreamer0.8-vorbis 
  gstreamer0.8-x guile-1.6-libs gzip hal-device-manager hdparm 
  hicolor-icon-theme hostname hotkey-setup hpijs hspell httrack 
  human-cursors-theme human-icon-theme hwdb-client-common hwdb-client-gnome 
  ifupdown imagemagick info initramfs-tools initscripts intltool-debian 
  iproute iptables iputils-arping iputils-ping iputils-tracepath iso-codes 
  java-common jscalibrator kaddressbook kaffeine kamera kdebluetooth 
  kdelibs kdelibs-data kdelibs4-dev kdelibs4c2a kdemultimedia-kio-plugins 
  kdesdk-scripts kftpgrabber kghostview klibc-utils klogd kmail kolourpaint 
  kopete kpdf ktorrent lame lame-extras language-pack-en 
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base 
  language-selector language-selector-common lapack3 laptop-detect 
  laptop-mode-tools lastfm launchpad-integration less lftp liba52-0.7.4 
  libacl1 libacl1-dev libadns1 libakode2 libapm1 libarts1-akode 
  libarts1-dev libarts1c2a libartsc0 libartsc0-dev libasound2 
  libasound2-dev libatk1.0-0 libatk1.0-dev libattr1 libattr1-dev 
  libaudio-dev libaudio2 libaudiofile-dev libaudiofile0 libavahi-client-dev 
  libavahi-client3 libavahi-common-data libavahi-common-dev 
  libavahi-common3 libavahi-compat-libdnssd1 libavahi-glib1 libavahi-qt3-1 
  libavahi-qt3-dev libavcodec0d libavformat0d libbeagle0 libbeecrypt6 
  libblkid1 libbluetooth2 libbluetooth2-dev libbonobo2-0 libbonobo2-common 
  libbrlapi1 libbtctl4 libbz2-1.0 libbz2-dev libc6 libc6-dev libc6-i686 
  libcairo-perl libcairo2 libcairo2-dev libcairomm-1.0-1 libcdio6 
  libcdparanoia0 libcfitsio2 libcomerr2 libconsole libcupsimage2 libcupsys2 
  libcupsys2-dev libcurl3 libcurl3-gnutls libdb3 libdb4.3 libdb4.3-dev 
  libdb4.4 libdbd-mysql-perl libdbi-perl libdbus-1-3 libdbus-1-dev 
  libdbus-glib-1-2 libdbus-qt-1-1c2 libdc1394-13 libdjvulibre15 libdmx1 
  libdrm2 libdv4 libdvdnav4 libdvdread3 libenchant1c2a libesd-alsa0 
  libesd0-dev libestools1.2 libexif12 libexpat1 libexpat1-dev 
  libfile-which-perl libflac++5c2 libflac7 libflash-swfplayer libflash0c2 
  libfluidsynth1 libfontconfig1 libfontconfig1-dev libfontenc1 libfreetype6 
  libfreetype6-dev libfribidi0 libfs6 libfuse2 libg2c0 libgadu3 libgamin0 
  libgc1c2 libgcc1 libgcj-bc libgcj-common libgcj7-0 libgconf2.0-cil 
  libgcrypt11 libgcrypt11-dev libgd2-xpm libgd2-xpm-dev libgda2-3 
  libgda2-common libgeos2c2a libggi2 libgii1 libgii1-target-x libgksu1.2-1 
  libgl1-mesa-dev libgl1-mesa-dri libgl1-mesa-glx libglew1 libglib-perl 
  libglib1.2 libglib2.0-0 libglib2.0-cil libglib2.0-dev libglibmm-2.4-1c2a 
  libglu1-mesa libglu1-mesa-dev libgmime-2.0-2 libgmime2.2-cil libgmp3c2 
  libgnome-mag2 libgnome-menu2 libgnome-pilot2 libgnome2-0 libgnome2-common 
  libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra 
  libgnutls-dev libgnutls13 libgpg-error-dev libgpg-error0 libgpgme11 
  libgphoto2-2 libgphoto2-port0 libgpmg1 libgpod-common libgsf-1-114 
  libgsf-1-common libgsf-1-dev libgssapi2 libgstreamer-gconf0.8-0 
  libgstreamer-plugins-base0.10-0 libgstreamer-plugins0.8-0 
  libgstreamer0.10-0 libgtk2.0-common libgtksourceview-common libgtop2-7 
  libgtop2-common libguile-ltdl-1 libgutenprint2 libhal-storage1 libhal1 
  libhsqldb-java libhtml-parser-perl libhttrack1 libice-dev libice6 
  libid3-3.8.3c2a libidl0 libidn11 libidn11-dev libiec61883-0 libieee1284-3 
  libimlib2 libisc11 libisccc0 libiso9660-4 libiw28 libjline-java libjsw2 
  libk3b-dev libk3b2 libk3b2-mp3 libkadm55 libkcal2b libkcddb1 libkdepim1a 
  libkleopatra1 libklibc libkmime2 libkonq4 libkpathsea4 libkpimidentities1 
  libkrb5-dev libkrb53 libksieve0 libktnef1 liblame0 liblircclient0 
  liblockdev1 liblog4j1.2-java liblua50 liblua50-dev liblualib50 
  liblualib50-dev liblwres9 libmagic1 libmagick9 libmdbtools libmikmod2 
  libmimelib1c2a libmjpegtools0c2a libmms0 libmodplug0c2 
  libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-data-tds1.0-cil 
  libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil 
  libmono-system-data1.0-cil libmono-system-web1.0-cil libmono0 
  libmono1.0-cil libmozjs0d libmp3-info-perl libmpeg2-4 libmusicbrainz4c2a 
  libmyspell3c2 libmysqlclient15off libncurses5 libncursesw5 libneon25 
  libnetcdf3 libnetpbm10 libnewt0.52 libnjb5 libnl1-pre6 libnm-util0 
  libnspr4 libnspr4-0d libnss3 libntfs-3g0 libogg-dev libogg0 liboggflac3 
  liboil0.3 libopenal0a libopencdk8 libopencdk8-dev libopenexr-dev 
  libopenexr2c2a libopenobex1 liborbit2 libpam-modules libpam-runtime 
  libpam0g libpango1.0-common libpaper1 libparted1.7-1 libpcap0.8 libpci2 
  libpcre3 libpcre3-dev libpcrecpp0 libperl5.8 libpisock9 libpisync0 
  libpng12-0 libpng12-dev libpopt-dev libpopt0 libpostproc0d libpq4 libpvm3 
  libqt0-ruby1.8 libqt3-headers libqt3-mt libqt3-mt-dev libqt4-core 
  libqt4-gui libqthreads-12 libquicktime0 libraw1394-8 libreadline5 
  librecode0 librpm4 libruby1.8 libscim8c2a libscrollkeeper0 
  libsdl-gfx1.2-4 libsdl-mixer1.2 libsdl-perl libsdl-sound1.2 
  libsdl-ttf2.0-0 libselinux1 libsensors3 libsepol1 libservlet2.3-java 
  libshout3 libsigc++-2.0-0c2a libslang2 libslp1 libsm-dev libsm6 
  libsmbclient libsmokeqt1 libsmpeg0 libsndfile1 libsnmp-base libsnmp9 
  libsoup2.2-8 libspeex1 libsqlite0 libsqlite3-0 libss2 libssl-dev 
  libssl0.9.8 libstartup-notification0 libstdc++5 libstdc++6 
  libstdc++6-4.1-dev libstlport4.6c2 libswfdec0.3 libsysfs2 libtag1-dev 
  libtag1c2a libtagc0 libtagc0-dev libtasn1-3 libtasn1-3-dev 
  libtext-charwidth-perl libtheora0 libungif4g libuniconf4.2 libuuid1 
  libvisual-0.4-0 libvlc0 libvorbis-dev libvorbis0a libvorbisenc2 
  libvorbisfile3 libwmf0.2-7 libwnck-common libwpd8c2a libwrap0 
  libwvstreams4.2-base libwvstreams4.2-extras libwxbase2.6-0 libwxgtk2.4-1 
  libx11-6 libx11-data libx11-dev libxau-dev libxau6 libxaw7 libxcomposite1 
  libxcursor-dev libxcursor1 libxdamage1 libxdelta2 libxdmcp-dev libxdmcp6 
  libxevie1 libxext-dev libxext6 libxfce4mcs-client3 libxfce4mcs-manager3 
  libxfce4util4 libxfixes-dev libxfixes3 libxfont1 libxft-dev libxft2 
  libxi-dev libxi6 libxine-main1 libxkbfile1 libxklavier11 
  libxml-parser-perl libxml2 libxml2-dev libxml2-utils libxmlsec1 
  libxmlsec1-nss libxmlsec1-openssl libxmu-dev libxmu-headers libxmu6 
  libxmuu1 libxp6 libxpm-dev libxpm4 libxrandr-dev libxrandr2 
  libxrender-dev libxrender1 libxres1 libxslt1-dev libxslt1.1 libxss1 
  libxt-dev libxt6 libxv1 libxvidcore4 libxxf86dga1 libxxf86misc1 
  libxxf86vm1 libzzip-0-12 linux-generic linux-libc-dev 
  linux-restricted-modules-common linux-sound-base localepurge locales 
  login lomoco lsb-base lsb-release lshw lua50 m4 make makedev man-db 
  manpages mcpp mencoder mesa-common-dev mesa-utils mime-support min12xxw 
  mkvtoolnix module-assistant module-init-tools mono-common mono-gac 
  mono-jit mono-runtime moto4lin mount mozilla-firefox-locale-en-gb 
  mozilla-mplayer mpg123 msttcorefonts myspell-en-gb myspell-en-us 
  mysql-client-5.0 mysql-common mysql-server-5.0 nano ncurses-base 
  ncurses-bin nn ntfs-3g ntpdate obexftp onboard openoffice.org-java-common 
  openoffice.org-l10n-common openoffice.org-thesaurus-en-us openssh-client 
  openssl p7zip p7zip-full parted passwd pciutils pcmciautils perl 
  perl-base perl-modules perl-suid phpmyadmin pkg-config plib1.8.4c2 
  pnm2ppa po-debconf poppler-utils popularity-contest portmap 
  powermanagement-interface powermgmt-base powernowd ppp pppconfig 
  pppoeconf prboom procmail procps psmisc psutils pykdeextensions 
  python-cairo python-central python-crypto python-dbus python-gconf 
  python-gdbm python-gobject python-gobject-dev python-gst0.10 python-kde3 
  python-launchpad-integration python-libxml2 python-numeric 
  python-numeric-ext python-problem-report python-pycurl python-pygame 
  python-pyorbit python-qt3 python-sip4 python-support python-twisted 
  python-twisted-bin python-twisted-conch python-twisted-core 
  python-twisted-lore python-twisted-mail python-twisted-names 
  python-twisted-news python-twisted-runner python-twisted-web 
  python-twisted-words python-tz python-xdg python-xml python-zopeinterface 
  python2.4 python2.4-dev python2.4-minimal python2.5 python2.5-dbg 
  python2.5-dev python2.5-doc python2.5-examples python2.5-minimal qobex 
  qt3-dev-tools qtparted quicktime-utils radeontool rar rdesktop readahead 
  readline-common refblas3 reiserfsprogs rpm rss-glx rsync ruby1.8 
  ruby1.8-dev screen scrollkeeper shared-mime-info slocate snes9x-x 
  soundconverter soundkonverter sox startup-tasks strace streamripper 
  sun-java5-bin sun-java5-jre sun-java5-plugin sun-java6-bin sun-java6-jre 
  supertux supertux-data supertuxkart supertuxkart-data sysklogd 
  system-services system-tools-backends sysv-rc sysvutils 
  tangerine-icon-theme tango-icon-theme tango-icon-theme-common tar tasksel 
  tasksel-data tcl8.4 tcpd tcpdump telnet thunderbird-locale-en-gb tk8.4 
  toshset transcode ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk 
  ttf-bengali-fonts ttf-bitstream-vera ttf-dejavu ttf-devanagari-fonts 
  ttf-dustin ttf-freefont ttf-gentium ttf-gujarati-fonts ttf-indic-fonts 
  ttf-kannada-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-malayalam-fonts 
  ttf-opensymbol ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts 
  ttf-telugu-fonts ttf-thai-tlwg tzdata ubuntu-minimal ubuntu-sounds 
  ubuntu-standard ucf unattended-upgrades unrar unzip upstart 
  upstart-compat-sysv upstart-logd usbutils usplash-theme-ubuntu ussp-push 
  util-linux util-linux-locales vim-common vim-tiny vlc-plugin-arts 
  vlc-plugin-esd vnc-common vorbis-tools w3m webhttrack wesnoth 
  wesnoth-data wget whiptail whois wifi-radar wireless-tools 
  wireshark-common wpasupplicant wvdial wxvlc x-ttcidfont-conf x11-common 
  x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev 
  x11proto-randr-dev x11proto-render-dev x11proto-xext-dev 
  x11proto-xinerama-dev xbase-clients xcin xcursor-themes xdelta 
  xfonts-100dpi xfonts-75dpi xfonts-base xfonts-encodings xfonts-scalable 
  xfonts-utils xinetd xkb-data xkeyboard-config xmms xorg xpdf-common 
  xpdf-reader xpmutils xscreensaver-data xscreensaver-gl xserver-xorg 
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-elographics 
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse 
  xserver-xorg-input-synaptics xserver-xorg-input-wacom 
  xserver-xorg-video-all xserver-xorg-video-apm xserver-xorg-video-ark 
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus 
  xserver-xorg-video-cyrix xserver-xorg-video-dummy 
  xserver-xorg-video-fbdev xserver-xorg-video-glint xserver-xorg-video-i128 
  xserver-xorg-video-i740 xserver-xorg-video-i810 xserver-xorg-video-imstt 
  xserver-xorg-video-mga xserver-xorg-video-neomagic 
  xserver-xorg-video-newport xserver-xorg-video-nsc xserver-xorg-video-nv 
  xserver-xorg-video-rendition xserver-xorg-video-s3 
  xserver-xorg-video-s3virge xserver-xorg-video-savage 
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis 
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga 
  xserver-xorg-video-trident xserver-xorg-video-tseng 
  xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vga 
  xserver-xorg-video-via xserver-xorg-video-vmware 
  xserver-xorg-video-voodoo xsltproc xterm xtrans-dev xutils xutils-dev 
  xvncviewer zlib1g zlib1g-dev zsnes 
1011 packages upgraded, 0 newly installed, 0 to remove and 352 not upgraded.
Need to get 0B/685MB of archives. After unpacking 96.1MB will be used.
Do you want to continue? [Y/n/?] Y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: syntax error: unknown user `postfix' in statoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
```

---

### Post by theaverageidiot on 2007-05-03
bump

---

### Post by mtalexan on 2007-05-03
I've got the same problem but the file is /var/apt/archives/lock instead.  When I run the update and upgrade commands everything works perfectly, but that's probably because a bunch of stuff was uninstalled when I initially tried to upgrade to Feisty.  After I ran update and upgrade a couple times (after the first it found nothing to upgrade) I tried to upgrade to Feisty and still had the same problem.

---

### Post by theaverageidiot on 2007-05-03
Bump-it!

---

### Post by mtalexan on 2007-05-03
I got Feisty to install without bugging up but I'm not sure which thing I did solved to problem.

I went into Synaptic Package Manager and unchecked all Third-Party repositories.  Next I attempted to run Feisty from the Live! CD but it kept failing checks and having problems accessing one of the hardware devices so I was forced to remove all power from the system and eject the CD.  Next I put the alternate version CD in (yes I made 2 Feisty CDs, one including Live! and one with the alternate version) after booting into Edgy.  A box popped up telling me the CD contained upgrade files so I clicked OK and it opened Synaptic.  I closed Synaptic and a new update notification popped up so I installed the 2 new files (both upgrades to Feisty versions of system programs like dpkg) and restarted.  After I restarted I started Update Manager again and ran the distribution upgrade with no problems.

Sorry I can't tell you exactly which portion of my process fixed the error, but I don't know what caused the error in the first place so I can't test it any further.  Hope something in here works for you.

---

### Post by TriggerHappyChewie on 2007-05-06
Back up your stuff and do a clean install.

---

### Post by balivo on 2007-05-09
Yes, just remove all third party repository entries!

---

