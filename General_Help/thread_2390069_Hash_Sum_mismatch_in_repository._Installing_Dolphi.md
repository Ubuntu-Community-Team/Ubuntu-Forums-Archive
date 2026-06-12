---
title: "Hash Sum mismatch in repository. Installing Dolphin"
date: 2018-04-25
forum: General Help
---

### Post by rudokf on 2018-04-25
Hi all,

Ubuntu 17.10

I am trying to install 'dolphin' as an alternative to nautilus file manager.
apt-get-install dolphin produces following error:

Err:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) artful/universe amd64 kdegraphics-thumbnailers amd64 4:17.04.3-0ubuntu1
  Hash Sum mismatch
  Hashes of expected file:
   - SHA256:89c7f9247a8d70ed3610ad748a86805ed9c81a36dc0891c857a9cd4e189d9a01
   - SHA1:ff24bbecfb6ed879c8c4a5af3ca8c8d8812b6dc1 [weak]
   - MD5Sum:ec88b0bb805b46d2dbd36bac121841ae [weak]
   - Filesize:32068 [weak]
  Hashes of received file:
   - SHA256:53c03bb4ce079f469d8bfa514e8a93344d6ae7004b609202915836ed7729d21e
   - SHA1:98d4438d9ab8115134b50beef89a3369807bf10b [weak]
   - MD5Sum:d25f449b715d1bbe464e8bcf97d713c5 [weak]
   - Filesize:32068 [weak]
  Last modification reported: Fri, 18 Aug 2017 10:19:50 +0000

Thanks,
Rudolf

---

### Post by again? on 2018-04-25
Run ```
sudo apt update
``` 
and try again.

Still errors, try a different source.
Might I suggest nemo as a replacement for nautilus.
Dolphin pulls in a lot of kde packages.

---

### Post by rudokf on 2018-04-26
Thanks,

i think there is something terribly wrong with AU repo at the moment.

I am trying Nemo now.

I am really after an File Manager that looks similar to File Explorer in Windows, so wanted to try few most popular ones. Nemo seem to be a bit better than Nautilus.

Rudolf

---

### Post by again? on 2018-04-26
I'm in Aus but use the iinet repo.
Switched to au.archive.ubuntu.com and don't see any issues although I've seen similar errors in the past that usually clear up the next day.
```
**glen@Xubarty:~$** sudo apt update
[sudo] password for glen:         
Get:1 http://au.archive.ubuntu.com/ubuntu artful InRelease [237 kB]
Hit:2 http://archive.canonical.com/ubuntu artful InRelease                                                                       
Get:3 http://au.archive.ubuntu.com/ubuntu artful-updates InRelease [88.7 kB]                                                     
Ign:4 http://dl.google.com/linux/chrome/deb stable InRelease                                                                     
Hit:5 http://ppa.launchpad.net/peek-developers/stable/ubuntu artful InRelease                                                    
Get:6 http://au.archive.ubuntu.com/ubuntu artful-backports InRelease [74.6 kB]                                                   
Get:7 http://au.archive.ubuntu.com/ubuntu artful-security InRelease [83.2 kB]                                                    
Hit:8 http://dl.google.com/linux/chrome/deb stable Release                                                                       
Get:9 http://au.archive.ubuntu.com/ubuntu artful/main amd64 Packages [1,071 kB]                                                  
Ign:11 http://repo.vivaldi.com/snapshot/deb stable InRelease                                                                     
Hit:12 http://ppa.launchpad.net/rvm/smplayer-qt4/ubuntu artful InRelease                                               
Ign:13 http://repo.vivaldi.com/stable/deb stable InRelease                                                                       
Hit:14 http://repo.vivaldi.com/snapshot/deb stable Release                                                             
Hit:15 http://ppa.launchpad.net/tista/adapta/ubuntu artful InRelease                                                        
Hit:16 http://repo.vivaldi.com/stable/deb stable Release                                                                    
Get:19 http://au.archive.ubuntu.com/ubuntu artful/main i386 Packages [1,067 kB]                                             
Ign:20 https://mega.nz/linux/MEGAsync/xUbuntu_17.10 ./ InRelease                 
Get:21 http://au.archive.ubuntu.com/ubuntu artful/main Translation-en [542 kB]   
Get:22 https://mega.nz/linux/MEGAsync/xUbuntu_17.10 ./ Release [980 B]                                
Get:24 http://au.archive.ubuntu.com/ubuntu artful/main Translation-en_AU [2,424 B]                                               
Get:25 http://au.archive.ubuntu.com/ubuntu artful/main amd64 DEP-11 Metadata [397 kB]                                            
Get:26 http://au.archive.ubuntu.com/ubuntu artful/main DEP-11 64x64 Icons [263 kB]                                               
Get:27 http://au.archive.ubuntu.com/ubuntu artful/restricted amd64 Packages [8,852 B]                                            
Get:28 http://au.archive.ubuntu.com/ubuntu artful/restricted i386 Packages [8,876 B]                                             
Get:29 http://au.archive.ubuntu.com/ubuntu artful/restricted Translation-en [2,788 B]                                            
Get:30 http://au.archive.ubuntu.com/ubuntu artful/restricted Translation-en_AU [1,340 B]                                         
Get:31 http://au.archive.ubuntu.com/ubuntu artful/universe amd64 Packages [8,103 kB]                                             
Get:32 http://au.archive.ubuntu.com/ubuntu artful/universe i386 Packages [8,066 kB]                                              
Get:33 http://au.archive.ubuntu.com/ubuntu artful/universe Translation-en_AU [1,128 B]                                           
Get:34 http://au.archive.ubuntu.com/ubuntu artful/universe Translation-en [4,789 kB]                                             
Get:35 http://au.archive.ubuntu.com/ubuntu artful/universe amd64 DEP-11 Metadata [2,845 kB]                                      
Get:36 http://au.archive.ubuntu.com/ubuntu artful/universe DEP-11 64x64 Icons [7,915 kB]                                         
Get:37 http://au.archive.ubuntu.com/ubuntu artful/multiverse amd64 Packages [150 kB]                                             
Get:38 http://au.archive.ubuntu.com/ubuntu artful/multiverse i386 Packages [143 kB]                                              
Get:39 http://au.archive.ubuntu.com/ubuntu artful/multiverse Translation-en_AU [60.6 kB]                                         
Get:40 http://au.archive.ubuntu.com/ubuntu artful/multiverse Translation-en [108 kB]                                             
Get:41 http://au.archive.ubuntu.com/ubuntu artful/multiverse amd64 DEP-11 Metadata [43.8 kB]                                     
Get:42 http://au.archive.ubuntu.com/ubuntu artful/multiverse DEP-11 64x64 Icons [207 kB]                                         
Get:43 http://au.archive.ubuntu.com/ubuntu artful-updates/main amd64 Packages [251 kB]                                           
Get:44 http://au.archive.ubuntu.com/ubuntu artful-updates/main i386 Packages [246 kB]                                            
Get:45 http://au.archive.ubuntu.com/ubuntu artful-updates/main Translation-en [111 kB]                                           
Get:46 http://au.archive.ubuntu.com/ubuntu artful-updates/main amd64 DEP-11 Metadata [83.4 kB]                                   
Get:47 http://au.archive.ubuntu.com/ubuntu artful-updates/main DEP-11 64x64 Icons [44.4 kB]                                      
Get:48 http://au.archive.ubuntu.com/ubuntu artful-updates/restricted amd64 Packages [2,192 B]                                    
Get:49 http://au.archive.ubuntu.com/ubuntu artful-updates/restricted i386 Packages [2,180 B]                                     
Get:50 http://au.archive.ubuntu.com/ubuntu artful-updates/restricted Translation-en [1,284 B]                                    
Get:51 http://au.archive.ubuntu.com/ubuntu artful-updates/universe i386 Packages [108 kB]                                        
Get:52 http://au.archive.ubuntu.com/ubuntu artful-updates/universe amd64 Packages [109 kB]                                       
Get:53 http://au.archive.ubuntu.com/ubuntu artful-updates/universe Translation-en [60.9 kB]                                      
Get:54 http://au.archive.ubuntu.com/ubuntu artful-updates/universe amd64 DEP-11 Metadata [83.7 kB]                               
Get:55 http://au.archive.ubuntu.com/ubuntu artful-updates/universe DEP-11 64x64 Icons [106 kB]                                   
Get:56 http://au.archive.ubuntu.com/ubuntu artful-updates/multiverse amd64 Packages [4,128 B]                                    
Get:57 http://au.archive.ubuntu.com/ubuntu artful-updates/multiverse i386 Packages [4,276 B]                                     
Get:58 http://au.archive.ubuntu.com/ubuntu artful-updates/multiverse Translation-en [2,264 B]                                    
Get:59 http://au.archive.ubuntu.com/ubuntu artful-updates/multiverse amd64 DEP-11 Metadata [2,468 B]                             
Get:60 http://au.archive.ubuntu.com/ubuntu artful-updates/multiverse DEP-11 64x64 Icons [2,638 B]                                
Get:61 http://au.archive.ubuntu.com/ubuntu artful-backports/main i386 Packages [1,512 B]                                         
Get:62 http://au.archive.ubuntu.com/ubuntu artful-backports/main amd64 Packages [1,516 B]                                        
Get:63 http://au.archive.ubuntu.com/ubuntu artful-backports/main Translation-en [668 B]                                          
Get:64 http://au.archive.ubuntu.com/ubuntu artful-backports/universe i386 Packages [3,848 B]                                     
Get:65 http://au.archive.ubuntu.com/ubuntu artful-backports/universe amd64 Packages [4,076 B]                                    
Get:66 http://au.archive.ubuntu.com/ubuntu artful-backports/universe Translation-en [2,116 B]                                    
Get:67 http://au.archive.ubuntu.com/ubuntu artful-backports/universe amd64 DEP-11 Metadata [5,088 B]                             
Get:68 http://au.archive.ubuntu.com/ubuntu artful-backports/universe DEP-11 64x64 Icons [2,717 B]                                
Get:69 http://au.archive.ubuntu.com/ubuntu artful-security/main i386 Packages [153 kB]                                           
Get:70 http://au.archive.ubuntu.com/ubuntu artful-security/main amd64 Packages [156 kB]                                          
Get:71 http://au.archive.ubuntu.com/ubuntu artful-security/main Translation-en [67.8 kB]                                         
Get:72 http://au.archive.ubuntu.com/ubuntu artful-security/main amd64 DEP-11 Metadata [17.2 kB]                                  
Get:73 http://au.archive.ubuntu.com/ubuntu artful-security/main DEP-11 64x64 Icons [27.5 kB]                                     
Get:74 http://au.archive.ubuntu.com/ubuntu artful-security/restricted i386 Packages [2,180 B]                                    
Get:75 http://au.archive.ubuntu.com/ubuntu artful-security/restricted amd64 Packages [2,192 B]                                   
Get:76 http://au.archive.ubuntu.com/ubuntu artful-security/restricted Translation-en [1,284 B]                                   
Get:77 http://au.archive.ubuntu.com/ubuntu artful-security/universe i386 Packages [60.5 kB]                                      
Get:78 http://au.archive.ubuntu.com/ubuntu artful-security/universe amd64 Packages [61.0 kB]                                     
Get:79 http://au.archive.ubuntu.com/ubuntu artful-security/universe Translation-en [36.1 kB]                                     
Get:80 http://au.archive.ubuntu.com/ubuntu artful-security/universe amd64 DEP-11 Metadata [39.5 kB]                              
Get:81 http://au.archive.ubuntu.com/ubuntu artful-security/universe DEP-11 64x64 Icons [39.7 kB]                                 
Get:82 http://au.archive.ubuntu.com/ubuntu artful-security/multiverse amd64 Packages [1,824 B]                                   
Get:83 http://au.archive.ubuntu.com/ubuntu artful-security/multiverse i386 Packages [1,984 B]                                    
Get:84 http://au.archive.ubuntu.com/ubuntu artful-security/multiverse Translation-en [1,124 B]                                   
Fetched 38.2 MB in 1min 11s (535 kB/s)                                                                                           
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

**glen@Xubarty:~$** sudo apt install dolphin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt4-designer libqt4-help libqt4-scripttools libqt4-test libqtassistantclient4 linux-headers-4.13.0-37
  linux-headers-4.13.0-37-generic linux-image-4.13.0-37-generic linux-image-extra-4.13.0-37-generic python-qt4 python-qt4-dbus
  python-sip
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  baloo-kf5 catdoc ffmpegthumbs kactivities-bin kactivitymanagerd kdegraphics-thumbnailers kdelibs5-data kinit kio
  kpackagelauncherqml kpackagetool5 kwayland-data kwayland-integration libattica0.4 libdbusmenu-qt2 libdbusmenu-qt5
  libdlrestrictions1 libdolphinvcs5 libepub0 libfam0 libhfstospell9 libkdecore5 libkdeui5 libkf5activities5 libkf5archive5
  libkf5attica5 libkf5auth-data libkf5auth5 libkf5baloo5 libkf5balooengine5 libkf5baloowidgets-bin libkf5baloowidgets-data
  libkf5baloowidgets5 libkf5bookmarks-data libkf5bookmarks5 libkf5calendarevents5 libkf5codecs-data libkf5codecs5
  libkf5completion-data libkf5completion5 libkf5config-bin libkf5config-data libkf5configcore5 libkf5configgui5
  libkf5configwidgets-data libkf5configwidgets5 libkf5coreaddons-data libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-bin
  libkf5dbusaddons-data libkf5dbusaddons5 libkf5declarative-data libkf5declarative5 libkf5doctools5 libkf5filemetadata-bin
  libkf5filemetadata-data libkf5filemetadata3 libkf5globalaccel-bin libkf5globalaccel-data libkf5globalaccel5
  libkf5globalaccelprivate5 libkf5guiaddons5 libkf5i18n-data libkf5i18n5 libkf5iconthemes-bin libkf5iconthemes-data
  libkf5iconthemes5 libkf5idletime5 libkf5itemviews-data libkf5itemviews5 libkf5jobwidgets-data libkf5jobwidgets5
  libkf5kcmutils-data libkf5kcmutils5 libkf5kdcraw5 libkf5kexiv2-15.0.0 libkf5kiocore5 libkf5kiofilewidgets5 libkf5kiontlm5
  libkf5kiowidgets5 libkf5newstuff-data libkf5newstuff5 libkf5newstuffcore5 libkf5notifications-data libkf5notifications5
  libkf5package-data libkf5package5 libkf5parts-data libkf5parts-plugins libkf5parts5 libkf5plasma5 libkf5plasmaquick5
  libkf5quickaddons5 libkf5service-bin libkf5service-data libkf5service5 libkf5solid5 libkf5solid5-data libkf5sonnet5-data
  libkf5sonnetcore5 libkf5sonnetui5 libkf5textwidgets-data libkf5textwidgets5 libkf5wallet-bin libkf5wallet-data libkf5wallet5
  libkf5waylandclient5 libkf5widgetsaddons-data libkf5widgetsaddons5 libkf5windowsystem-data libkf5windowsystem5
  libkf5xmlgui-bin libkf5xmlgui-data libkf5xmlgui5 libkio5 libkonq-common libkonq5-templates libkwalletbackend5-5 liblmdb0
  libphonon4 libphonon4qt5-4 libpolkit-qt5-1-1 libpoppler-qt5-1 libqt5quickcontrols2-5 libqt5quicktemplates2-5 libqt5script5
  libqt5waylandclient5 libqt5waylandcompositor5 libsolid4 libstreamanalyzer0v5 libstreams0v5 libvoikko1 libxcb-composite0
  libxcb-damage0 libzip4 media-player-info phonon phonon-backend-gstreamer phonon-backend-gstreamer-common phonon4qt5
  phonon4qt5-backend-vlc plasma-framework qml-module-org-kde-kconfig qml-module-org-kde-kirigami
  qml-module-org-kde-kquickcontrols qml-module-org-kde-kquickcontrolsaddons qml-module-org-kde-newstuff
  qml-module-qtgraphicaleffects qml-module-qtqml-models2 qml-module-qtquick-controls qml-module-qtquick-controls2
  qml-module-qtquick-dialogs qml-module-qtquick-layouts qml-module-qtquick-privatewidgets qml-module-qtquick-templates2
  qml-module-qtquick-window2 qml-module-qtquick2 qtwayland5 sonnet-plugins
Suggested packages:
  dolphin-plugins go-mtpfs fam hspell kdelibs5-plugins voikko-fi phonon-backend-vlc phonon4qt5-backend-gstreamer
The following NEW packages will be installed:
  baloo-kf5 catdoc dolphin ffmpegthumbs kactivities-bin kactivitymanagerd kdegraphics-thumbnailers kdelibs5-data kinit kio
  kpackagelauncherqml kpackagetool5 kwayland-data kwayland-integration libattica0.4 libdbusmenu-qt2 libdbusmenu-qt5
  libdlrestrictions1 libdolphinvcs5 libepub0 libfam0 libhfstospell9 libkdecore5 libkdeui5 libkf5activities5 libkf5archive5
  libkf5attica5 libkf5auth-data libkf5auth5 libkf5baloo5 libkf5balooengine5 libkf5baloowidgets-bin libkf5baloowidgets-data
  libkf5baloowidgets5 libkf5bookmarks-data libkf5bookmarks5 libkf5calendarevents5 libkf5codecs-data libkf5codecs5
  libkf5completion-data libkf5completion5 libkf5config-bin libkf5config-data libkf5configcore5 libkf5configgui5
  libkf5configwidgets-data libkf5configwidgets5 libkf5coreaddons-data libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-bin
  libkf5dbusaddons-data libkf5dbusaddons5 libkf5declarative-data libkf5declarative5 libkf5doctools5 libkf5filemetadata-bin
  libkf5filemetadata-data libkf5filemetadata3 libkf5globalaccel-bin libkf5globalaccel-data libkf5globalaccel5
  libkf5globalaccelprivate5 libkf5guiaddons5 libkf5i18n-data libkf5i18n5 libkf5iconthemes-bin libkf5iconthemes-data
  libkf5iconthemes5 libkf5idletime5 libkf5itemviews-data libkf5itemviews5 libkf5jobwidgets-data libkf5jobwidgets5
  libkf5kcmutils-data libkf5kcmutils5 libkf5kdcraw5 libkf5kexiv2-15.0.0 libkf5kiocore5 libkf5kiofilewidgets5 libkf5kiontlm5
  libkf5kiowidgets5 libkf5newstuff-data libkf5newstuff5 libkf5newstuffcore5 libkf5notifications-data libkf5notifications5
  libkf5package-data libkf5package5 libkf5parts-data libkf5parts-plugins libkf5parts5 libkf5plasma5 libkf5plasmaquick5
  libkf5quickaddons5 libkf5service-bin libkf5service-data libkf5service5 libkf5solid5 libkf5solid5-data libkf5sonnet5-data
  libkf5sonnetcore5 libkf5sonnetui5 libkf5textwidgets-data libkf5textwidgets5 libkf5wallet-bin libkf5wallet-data libkf5wallet5
  libkf5waylandclient5 libkf5widgetsaddons-data libkf5widgetsaddons5 libkf5windowsystem-data libkf5windowsystem5
  libkf5xmlgui-bin libkf5xmlgui-data libkf5xmlgui5 libkio5 libkonq-common libkonq5-templates libkwalletbackend5-5 liblmdb0
  libphonon4 libphonon4qt5-4 libpolkit-qt5-1-1 libpoppler-qt5-1 libqt5quickcontrols2-5 libqt5quicktemplates2-5 libqt5script5
  libqt5waylandclient5 libqt5waylandcompositor5 libsolid4 libstreamanalyzer0v5 libstreams0v5 libvoikko1 libxcb-composite0
  libxcb-damage0 libzip4 media-player-info phonon phonon-backend-gstreamer phonon-backend-gstreamer-common phonon4qt5
  phonon4qt5-backend-vlc plasma-framework qml-module-org-kde-kconfig qml-module-org-kde-kirigami
  qml-module-org-kde-kquickcontrols qml-module-org-kde-kquickcontrolsaddons qml-module-org-kde-newstuff
  qml-module-qtgraphicaleffects qml-module-qtqml-models2 qml-module-qtquick-controls qml-module-qtquick-controls2
  qml-module-qtquick-dialogs qml-module-qtquick-layouts qml-module-qtquick-privatewidgets qml-module-qtquick-templates2
  qml-module-qtquick-window2 qml-module-qtquick2 qtwayland5 sonnet-plugins
0 to upgrade, 161 to newly install, 0 to remove and 0 not to upgrade.
Need to get 32.0 MB of archives.
After this operation, 153 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```

---

