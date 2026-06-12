---
title: "Issue with trying to update."
date: 2014-02-22
forum: General Help
---

### Post by demonic_crow on 2014-02-22
It been a long time since I have updated my Ubuntu and now it wont let me. I tried to install gpac

```
demonic@laptop:~$ sudo apt-get install gpac
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gpac : Depends: gpac-modules-base (= 0.4.5+svn3462~dfsg0-1) but it is not going to be installed
        Depends: libgpac1 (= 0.4.5+svn3462~dfsg0-1) but it is not going to be installed
 libpython3.3 : Depends: python3.3 (= 3.3.2-1+precise1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
demonic@laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  lib32bz2-1.0 cups-pk-helper libavformat-extra-52 libktnef4
  libaccess-bridge-java libavdevice-extra-52
  libmono-compilerservices-symbolwriter4.0-cil libkxmlrpcclient4
  libpolkit-qt-1-0 blender-codecs-ffmpeg1.2 appmenu-gtk lib32ncurses5
  libxine1-x kpackagekit python-gobject-dev libmodplug0c2 libcvaux4
  lib32tinfo5 g++-4.4 libquicktime1 libglew1.5 packagekit-backend-aptcc
  libxcb-render-util0-dev libpython3.2 kdelibs5 libcheese-gtk18 libavfilter0
  python-gobject-2-dev libgtk2-ruby1.8 python-gtk2-dev libiso9660-7 podsleuth
  libdirectfb-extra libexiv2-6 libffi-dev libdvbpsi5 libmysqlclient16
  libsyndication4 libpython3.3-minimal kdesudo lib32gcc1 appmenu-qt
  libaccess-bridge-java-jni libqgpgme1 linux-headers-2.6.32-28 libgladeui-1-9
  python-gi-dev virtuoso-nepomuk libswscale-extra-0 libglade2-dev appmenu-gtk3
  libmatroska0 libkrossui4 eagle-data libiptcdata0 python2.6-dev
  libwebkit1.1-cil libpostproc51 libxine1-console libxml2-dev libglib2-ruby1.8
  libcv4 libkblog4 libcairo-ruby1.8 install-package libportaudiocpp0
  libqt4-assistant libgdata1.4-cil gdebi-kde libxine1-misc-plugins
  libkimproxy4 kdepimlibs5 libhighgui4 update-manager-kde libatk1-ruby1.8
  libattica0 libpango1-ruby1.8 libg15-1 libsoundtouch1c2 libf2c2 libid3tag0
  linux-headers-2.6.32-28-generic kdebase-runtime lib32stdc++6 libboo2.0.9-cil
  libgdk-pixbuf2-ruby1.8 libsox1a libgtk2.0-dev libdirectfb-dev libjpeg62-dev
  libebml0 gir1.2-panelapplet-4.0 libmpcdec3 libxine1-bin libkutils4
  libsysfs-dev libxine1-ffmpeg libgpgme++2 libstdc++6-4.4-dev
  packagekit-backend-apt libxine1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libpython3.3 python3.3 python3.3-minimal
Suggested packages:
  python3.3-doc
The following NEW packages will be installed:
  python3.3 python3.3-minimal
The following packages will be upgraded:
  libpython3.3
1 upgraded, 2 newly installed, 0 to remove and 583 not upgraded.
2 not fully installed or removed.
Need to get 0 B/5,918 kB of archives.
After this operation, 15.1 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 404409 files and directories currently installed.)
Unpacking python3.3-minimal (from .../python3.3-minimal_3.3.3-2+precise1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/python3.3-minimal_3.3.3-2+precise1_amd64.deb (--unpack):
 trying to overwrite '/etc/python3.3/sitecustomize.py', which is also in package libpython3.3-minimal 3.3.0-1irie1~precise1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking python3.3 (from .../python3.3_3.3.3-2+precise1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/python3.3_3.3.3-2+precise1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/python3.3/imp.py', which is also in package libpython3.3-minimal 3.3.0-1irie1~precise1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/python3.3-minimal_3.3.3-2+precise1_amd64.deb
 /var/cache/apt/archives/python3.3_3.3.3-2+precise1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
demonic@laptop:~$ 

```

This is what I get when I tried to upate:

```
demonic@laptop:~/Desktop/android$ sudo apt-get update
[sudo] password for demonic: 
Hit http://dl.google.com stable Release.gpg
Hit http://dl.google.com stable Release                                        
Hit http://archive.ubuntu.com precise Release.gpg                              
Get:1 http://archive.ubuntu.com precise-updates Release.gpg [198 B]            
Hit http://archive.ubuntu.com precise-backports Release.gpg                    
Get:2 http://archive.ubuntu.com precise-security Release.gpg [198 B]           
Get:3 http://archive.ubuntu.com precise-proposed Release.gpg [198 B]           
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://archive.ubuntu.com precise Release                                  
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.canonical.com precise Release                               
Hit http://archive.canonical.com precise/partner Sources                       
Get:4 http://archive.ubuntu.com precise-updates Release [49.6 kB]              
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://dl.google.com stable/main Translation-en_CA                         
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://archive.ubuntu.com precise-backports Release                        
Get:5 http://archive.ubuntu.com precise-security Release [49.6 kB]             
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Get:6 http://archive.ubuntu.com precise-proposed Release [49.6 kB]             
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://archive.ubuntu.com precise/main Sources                             
Hit http://archive.ubuntu.com precise/restricted Sources                       
Hit http://archive.ubuntu.com precise/multiverse Sources                       
Hit http://archive.ubuntu.com precise/universe Sources                         
Hit http://archive.ubuntu.com precise/main amd64 Packages                      
Hit http://archive.ubuntu.com precise/restricted amd64 Packages                
Hit http://archive.ubuntu.com precise/universe amd64 Packages                  
Hit http://archive.ubuntu.com precise/multiverse amd64 Packages                
Hit http://archive.ubuntu.com precise/main i386 Packages                       
Hit http://archive.ubuntu.com precise/restricted i386 Packages                 
Hit http://archive.ubuntu.com precise/universe i386 Packages                   
Hit http://archive.ubuntu.com precise/multiverse i386 Packages                 
Hit http://archive.ubuntu.com precise/main TranslationIndex                    
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex              
Hit http://archive.ubuntu.com precise/restricted TranslationIndex              
Hit http://archive.ubuntu.com precise/universe TranslationIndex                
Get:7 http://archive.ubuntu.com precise-updates/restricted Sources [8,028 B]   
Get:8 http://archive.ubuntu.com precise-updates/main Sources [452 kB]          
Ign http://archive.canonical.com precise/partner Translation-en_CA             
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-en_CA                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_CA             
Ign http://ppa.launchpad.net precise/main Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-en_CA             
Ign http://ppa.launchpad.net precise/main Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-en_CA             
Ign http://ppa.launchpad.net precise/main Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-en_CA             
Ign http://ppa.launchpad.net precise/main Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-en_CA             
Ign http://ppa.launchpad.net precise/main Translation-en                
Get:9 http://archive.ubuntu.com precise-updates/multiverse Sources [8,490 B]   
Get:10 http://archive.ubuntu.com precise-updates/universe Sources [105 kB]     
Get:11 http://archive.ubuntu.com precise-updates/main amd64 Packages [752 kB]  
Err http://packages.medibuntu.org precise Release.gpg                          
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Get:12 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [12.2 kB]
Get:13 http://archive.ubuntu.com precise-updates/universe amd64 Packages [236 kB]
Get:14 http://archive.ubuntu.com precise-updates/multiverse amd64 Packages [14.5 kB]
Get:15 http://archive.ubuntu.com precise-updates/main i386 Packages [774 kB]   
Get:16 http://archive.ubuntu.com precise-updates/restricted i386 Packages [12.2 kB]
Get:17 http://archive.ubuntu.com precise-updates/universe i386 Packages [241 kB]
Get:18 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [14.7 kB]
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex            
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://archive.ubuntu.com precise-backports/main Sources       
Hit http://archive.ubuntu.com precise-backports/restricted Sources 
Hit http://archive.ubuntu.com precise-backports/universe Sources   
Hit http://archive.ubuntu.com precise-backports/multiverse Sources 
Hit http://archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://archive.ubuntu.com precise-backports/restricted amd64 Packages      
Hit http://archive.ubuntu.com precise-backports/universe amd64 Packages        
Hit http://archive.ubuntu.com precise-backports/multiverse amd64 Packages      
Ign http://packages.medibuntu.org precise Release                              
Hit http://archive.ubuntu.com precise-backports/main i386 Packages             
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages       
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages         
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages       
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex          
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex    
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex    
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex      
Get:19 http://archive.ubuntu.com precise-security/restricted Sources [2,494 B] 
Get:20 http://archive.ubuntu.com precise-security/main Sources [97.7 kB]       
Get:21 http://archive.ubuntu.com precise-security/multiverse Sources [1,782 B] 
Get:22 http://archive.ubuntu.com precise-security/universe Sources [30.9 kB]   
Get:23 http://archive.ubuntu.com precise-security/main amd64 Packages [363 kB] 
Get:24 http://archive.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:25 http://archive.ubuntu.com precise-security/universe amd64 Packages [90.9 kB]
Get:26 http://archive.ubuntu.com precise-security/multiverse amd64 Packages [2,443 B]
Get:27 http://archive.ubuntu.com precise-security/main i386 Packages [387 kB]  
Get:28 http://archive.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:29 http://archive.ubuntu.com precise-security/universe i386 Packages [95.4 kB]
Get:30 http://archive.ubuntu.com precise-security/multiverse i386 Packages [2,641 B]
Hit http://archive.ubuntu.com precise-security/main TranslationIndex           
Hit http://archive.ubuntu.com precise-security/multiverse TranslationIndex     
Hit http://archive.ubuntu.com precise-security/restricted TranslationIndex     
Hit http://archive.ubuntu.com precise-security/universe TranslationIndex       
Get:31 http://archive.ubuntu.com precise-proposed/restricted Sources [928 B]   
Get:32 http://archive.ubuntu.com precise-proposed/main Sources [10.8 kB]       
Get:33 http://archive.ubuntu.com precise-proposed/multiverse Sources [1,899 B] 
Get:34 http://archive.ubuntu.com precise-proposed/universe Sources [5,579 B]   
Get:35 http://archive.ubuntu.com precise-proposed/restricted amd64 Packages [755 B]
Get:36 http://archive.ubuntu.com precise-proposed/main amd64 Packages [99.0 kB]
Get:37 http://archive.ubuntu.com precise-proposed/multiverse amd64 Packages [1,442 B]
Get:38 http://archive.ubuntu.com precise-proposed/universe amd64 Packages [11.4 kB]
Get:39 http://archive.ubuntu.com precise-proposed/restricted i386 Packages [743 B]
Get:40 http://archive.ubuntu.com precise-proposed/main i386 Packages [121 kB]  
Get:41 http://archive.ubuntu.com precise-proposed/multiverse i386 Packages [1,449 B]
Get:42 http://archive.ubuntu.com precise-proposed/universe i386 Packages [15.8 kB]
Hit http://archive.ubuntu.com precise-proposed/main TranslationIndex           
Hit http://archive.ubuntu.com precise-proposed/multiverse TranslationIndex     
Hit http://archive.ubuntu.com precise-proposed/restricted TranslationIndex     
Hit http://archive.ubuntu.com precise-proposed/universe TranslationIndex       
Hit http://archive.ubuntu.com precise/main Translation-en_CA                   
Hit http://archive.ubuntu.com precise/main Translation-en                      
Hit http://archive.ubuntu.com precise/multiverse Translation-en                
Hit http://archive.ubuntu.com precise/restricted Translation-en                
Hit http://archive.ubuntu.com precise/universe Translation-en_CA               
Hit http://archive.ubuntu.com precise/universe Translation-en                  
Hit http://archive.ubuntu.com precise-updates/main Translation-en_CA           
Hit http://archive.ubuntu.com precise-updates/main Translation-en              
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en        
Hit http://archive.ubuntu.com precise-updates/universe Translation-en_CA       
Ign http://packages.medibuntu.org precise/free amd64 Packages/DiffIndex        
Hit http://archive.ubuntu.com precise-updates/universe Translation-en          
Hit http://archive.ubuntu.com precise-backports/main Translation-en            
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en      
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en      
Hit http://archive.ubuntu.com precise-backports/universe Translation-en        
Hit http://archive.ubuntu.com precise-security/main Translation-en             
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en       
Hit http://archive.ubuntu.com precise-security/restricted Translation-en       
Hit http://archive.ubuntu.com precise-security/universe Translation-en         
Hit http://archive.ubuntu.com precise-proposed/main Translation-en_CA          
Hit http://archive.ubuntu.com precise-proposed/main Translation-en             
Hit http://archive.ubuntu.com precise-proposed/multiverse Translation-en       
Hit http://archive.ubuntu.com precise-proposed/restricted Translation-en       
Hit http://archive.ubuntu.com precise-proposed/universe Translation-en_CA      
Hit http://archive.ubuntu.com precise-proposed/universe Translation-en         
Ign http://packages.medibuntu.org precise/non-free amd64 Packages/DiffIndex    
Ign http://packages.medibuntu.org precise/free i386 Packages/DiffIndex
Ign http://packages.medibuntu.org precise/non-free i386 Packages/DiffIndex
Ign http://packages.medibuntu.org precise/free TranslationIndex
Ign http://packages.medibuntu.org precise/non-free TranslationIndex
Err http://packages.medibuntu.org precise/free amd64 Packages
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err http://packages.medibuntu.org precise/non-free amd64 Packages
  Could not resolve 'packages.medibuntu.org'
Err http://packages.medibuntu.org precise/free i386 Packages
  Could not resolve 'packages.medibuntu.org'
Err http://packages.medibuntu.org precise/non-free i386 Packages
  Could not resolve 'packages.medibuntu.org'
Err http://packages.medibuntu.org precise/free Translation-en_CA
  Could not resolve 'packages.medibuntu.org'
Err http://packages.medibuntu.org precise/free Translation-en
  Could not resolve 'packages.medibuntu.org'
Err http://packages.medibuntu.org precise/non-free Translation-en_CA
  Could not resolve 'packages.medibuntu.org'
Err http://packages.medibuntu.org precise/non-free Translation-en
  Could not resolve 'packages.medibuntu.org'
Fetched 4,132 kB in 7min 16s (9,476 B/s)
W: Failed to fetch http://packages.medibuntu.org/dists/precise/Release.gpg  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://packages.medibuntu.org/dists/precise/free/binary-amd64/Packages  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://packages.medibuntu.org/dists/precise/non-free/binary-amd64/Packages  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en_CA  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en_CA  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en  Could not resolve 'packages.medibuntu.org'

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by deadflowr on 2014-02-22
You need to get into the software sources program and disable the medibuntu repos.
They no longer exist.
Quickest way is to open the update manager and go to the Settings button, this will open the software sources.
Then go to other software and find the entries for medibuntu and uncheck them
(You'll be ask to input your password the first time)
After you uncheck all the medibuntu entires, close the window and back in the update manager click on check, this run the apt-get update command, more or less.

Hope this helps.

---

### Post by demonic_crow on 2014-02-26
It did work but now I ran into another problem after.

```
demonic@laptop:~$ sudo apt-get install gpac
[sudo] password for demonic: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gpac : Depends: gpac-modules-base (= 0.4.5+svn3462~dfsg0-1) but it is not going to be installed
        Depends: libgpac1 (= 0.4.5+svn3462~dfsg0-1) but it is not going to be installed
 libpython3.3 : Depends: python3.3 (= 3.3.2-1+precise1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
demonic@laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  lib32bz2-1.0 cups-pk-helper libavformat-extra-52 libktnef4
  libaccess-bridge-java libavdevice-extra-52
  libmono-compilerservices-symbolwriter4.0-cil libkxmlrpcclient4
  libpolkit-qt-1-0 blender-codecs-ffmpeg1.2 appmenu-gtk lib32ncurses5
  libxine1-x kpackagekit python-gobject-dev libmodplug0c2 libcvaux4
  lib32tinfo5 g++-4.4 libquicktime1 libglew1.5 packagekit-backend-aptcc
  libxcb-render-util0-dev libpython3.2 kdelibs5 libcheese-gtk18 libavfilter0
  python-gobject-2-dev libgtk2-ruby1.8 python-gtk2-dev libiso9660-7 podsleuth
  libdirectfb-extra libexiv2-6 libffi-dev libdvbpsi5 libmysqlclient16
  libsyndication4 libpython3.3-minimal kdesudo lib32gcc1 appmenu-qt
  libaccess-bridge-java-jni libqgpgme1 linux-headers-2.6.32-28 libgladeui-1-9
  python-gi-dev virtuoso-nepomuk libswscale-extra-0 libglade2-dev appmenu-gtk3
  libmatroska0 libkrossui4 eagle-data libiptcdata0 python2.6-dev
  libwebkit1.1-cil libpostproc51 libxine1-console libxml2-dev libglib2-ruby1.8
  libcv4 libkblog4 libcairo-ruby1.8 install-package libportaudiocpp0
  libqt4-assistant libgdata1.4-cil gdebi-kde libxine1-misc-plugins
  libkimproxy4 kdepimlibs5 libhighgui4 update-manager-kde libatk1-ruby1.8
  libattica0 libpango1-ruby1.8 libg15-1 libsoundtouch1c2 libf2c2 libid3tag0
  linux-headers-2.6.32-28-generic kdebase-runtime lib32stdc++6 libboo2.0.9-cil
  libgdk-pixbuf2-ruby1.8 libsox1a libgtk2.0-dev libdirectfb-dev libjpeg62-dev
  libebml0 gir1.2-panelapplet-4.0 libmpcdec3 libxine1-bin libkutils4
  libsysfs-dev libxine1-ffmpeg libgpgme++2 libstdc++6-4.4-dev
  packagekit-backend-apt libxine1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libpython3.3 python3.3 python3.3-minimal
Suggested packages:
  python3.3-doc
The following NEW packages will be installed:
  python3.3 python3.3-minimal
The following packages will be upgraded:
  libpython3.3
1 upgraded, 2 newly installed, 0 to remove and 525 not upgraded.
2 not fully installed or removed.
Need to get 0 B/5,918 kB of archives.
After this operation, 15.1 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 404418 files and directories currently installed.)
Unpacking python3.3-minimal (from .../python3.3-minimal_3.3.3-2+precise1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/python3.3-minimal_3.3.3-2+precise1_amd64.deb (--unpack):
 trying to overwrite '/etc/python3.3/sitecustomize.py', which is also in package libpython3.3-minimal 3.3.0-1irie1~precise1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking python3.3 (from .../python3.3_3.3.3-2+precise1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/python3.3_3.3.3-2+precise1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/python3.3/imp.py', which is also in package libpython3.3-minimal 3.3.0-1irie1~precise1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/python3.3-minimal_3.3.3-2+precise1_amd64.deb
 /var/cache/apt/archives/python3.3_3.3.3-2+precise1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Thanks for the help.

---

### Post by deadflowr on 2014-02-26
Did you try the suggested command
```
sudo apt-get -f install
```
(Type this as is, don't add anything to it.
It should be just apt-get-f install, and not apt-get -f install packagename)

---

