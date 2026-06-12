---
title: "Computer will not allow me to shut down"
date: 2015-10-16
forum: General Help
---

### Post by SUPERFITTER on 2015-10-16
Computer will not allow me to shut down.  I get this message when I go to shut down the computer, (See Attachment).   I have to manually hold the computer start button to shut down.

I also have problems with switching to another site, a video etc. Once I get something going, switching is not possible to an other program. 
Thank you

---

### Post by yancek on 2015-10-16
Which version of Ubuntu are you using?  What method are you using to shutdown?  Have you tried to shutdown or reboot from a terminal?

---

### Post by SUPERFITTER on 2015-10-17
> **yancek said:**
> Which version of Ubuntu are you using?  What method are you using to shutdown?  Have you tried to shutdown or reboot from a terminal?

I am using Ubuntu 14.04.

Menu> Quit: Shut down the Computer

Have you tried to shut down or reboot from a terminal?  No, I don't know the right commands to run in terminal.

I am using Cinnamon Desktop and that will not allow me to turn off the computer.  I log out of Cinnamon Desktop and logged in to just Ubuntu14.04 with the unity icons.  Now I can shut off the computer: Gear then Shut Down

It looks like I have to fix Cinnamon Desktop, I have no idea where to go to fix this?


Just found this:    
[h=2][SIZE=2]Popular Cinnamon PPA for Ubuntu 14.04 To Close[/SIZE][/h]         [http://www.omgubuntu.co.uk/2014/05/ubuntu-cinnamon-desktop-ppa-retired](http://www.omgubuntu.co.uk/2014/05/ubuntu-cinnamon-desktop-ppa-retired)

Looks like I am out of luck running Cinnamon on Ubuntu.

---

### Post by SUPERFITTER on 2015-10-17
I uninstalled Cinnamon and rebooted, but I still have a problems with switching to another site, a video, email etc. Once I  get something going, switching is not possible to an other program.  All the sites do is a continuous buffering that does not stop.  If I go back the screen is frozen on that site.

```
dennis@dennis1:~$ sudo apt-get update
[sudo] password for dennis: 
Ign http://us.archive.ubuntu.com trusty InRelease
Hit http://us.archive.ubuntu.com trusty-updates InRelease                      
Hit http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://archive.canonical.com trusty InRelease                              
Hit http://security.ubuntu.com trusty-security InRelease                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://archive.canonical.com quantal InRelease                             
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages            
Hit http://extras.ubuntu.com trusty Release                                    
Ign http://archive.canonical.com trusty InRelease                              
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages        
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages             
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Hit http://archive.canonical.com quantal/partner amd64 Packages                
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages         
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Hit http://archive.canonical.com quantal/partner i386 Packages                 
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://archive.canonical.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://archive.canonical.com trusty Release                                
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Ign http://ppa.launchpad.net trusty/main Translation-en_US        
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages   
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages 
Hit http://archive.canonical.com trusty/partner amd64 Packages    
Hit http://us.archive.ubuntu.com trusty/main i386 Packages        
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages  
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages    
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages  
Ign http://ppa.launchpad.net trusty/main Translation-en           
Hit http://us.archive.ubuntu.com trusty/main Translation-en       
Hit http://archive.canonical.com trusty/partner i386 Packages     
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en   
Hit http://archive.canonical.com trusty/partner Translation-en      
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en   
Hit http://us.archive.ubuntu.com trusty/universe Translation-en    
Ign http://archive.canonical.com quantal/partner Translation-en_US
Ign http://archive.canonical.com quantal/partner Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Reading package lists... Done 
dennis@dennis1:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  caribou cinnamon-bluetooth cinnamon-common cinnamon-control-center
  cinnamon-control-center-data cinnamon-screensaver cinnamon-settings-daemon
  cinnamon-translations cjs gir1.2-accountsservice-1.0 gir1.2-caribou-1.0
  gir1.2-cinnamondesktop-3.0 gir1.2-clutter-1.0 gir1.2-cmenu-3.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gkbd-3.0 gir1.2-gtkclutter-1.0
  gir1.2-json-1.0 gir1.2-muffin-3.0 gir1.2-nmgtk-1.0 gir1.2-polkit-1.0
  gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 libblas3 libcaribou-common libcaribou0
  libcinnamon-control-center1 libcinnamon-desktop4 libcinnamon-menu-3-0
  libgfortran3 libgtkglext1 libilmbase6 liblapack3 libmuffin0
  libnemo-extension1 libopencv-calib3d2.4 libopencv-contrib2.4
  libopencv-core2.4 libopencv-features2d2.4 libopencv-flann2.4
  libopencv-highgui2.4 libopencv-imgproc2.4 libopencv-legacy2.4
  libopencv-ml2.4 libopencv-objdetect2.4 libopencv-photo2.4 libopencv-video2.4
  libopenexr6 libtbb2 muffin-common nemo nemo-data nemo-fileroller
  python-numpy python-opencv python-pyatspi python-pyinotify
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dennis@dennis1:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  caribou cinnamon-bluetooth cinnamon-common cinnamon-control-center
  cinnamon-control-center-data cinnamon-screensaver cinnamon-settings-daemon
  cinnamon-translations cjs gir1.2-accountsservice-1.0 gir1.2-caribou-1.0
  gir1.2-cinnamondesktop-3.0 gir1.2-clutter-1.0 gir1.2-cmenu-3.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gkbd-3.0 gir1.2-gtkclutter-1.0
  gir1.2-json-1.0 gir1.2-muffin-3.0 gir1.2-nmgtk-1.0 gir1.2-polkit-1.0
  gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 libblas3 libcaribou-common libcaribou0
  libcinnamon-control-center1 libcinnamon-desktop4 libcinnamon-menu-3-0
  libgfortran3 libgtkglext1 libilmbase6 liblapack3 libmuffin0
  libnemo-extension1 libopencv-calib3d2.4 libopencv-contrib2.4
  libopencv-core2.4 libopencv-features2d2.4 libopencv-flann2.4
  libopencv-highgui2.4 libopencv-imgproc2.4 libopencv-legacy2.4
  libopencv-ml2.4 libopencv-objdetect2.4 libopencv-photo2.4 libopencv-video2.4
  libopenexr6 libtbb2 muffin-common nemo nemo-data nemo-fileroller
  python-numpy python-opencv python-pyatspi python-pyinotify
0 upgraded, 0 newly installed, 58 to remove and 0 not upgraded.
After this operation, 85.6 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 901665 files and directories currently installed.)
Removing caribou (0.4.13-0ubuntu1) ...
Removing cinnamon-bluetooth (3.8.8-20151017012004-trusty) ...
Removing cinnamon-common (2.6.13-20151017040014-trusty) ...
Removing cinnamon-control-center (2.8.0-20151017013044-trusty) ...
Removing cinnamon-control-center-data (2.8.0-20151017013044-trusty) ...
Removing cinnamon-screensaver (2.8.0-20151017013226-trusty) ...
Removing cinnamon-settings-daemon (2.8.0-20151017004504-trusty) ...
Removing nemo-fileroller (2.6.1-20151017020004-trusty) ...
Removing nemo (2.6.7-20151017010005-trusty) ...
Removing cinnamon-translations (2.6.3-20151017040242-trusty) ...
Removing cjs (2.8.0-20151017020139-trusty) ...
Removing gir1.2-accountsservice-1.0 (0.6.35-0ubuntu7.2) ...
Removing gir1.2-caribou-1.0 (0.4.13-0ubuntu1) ...
Removing gir1.2-muffin-3.0 (2.8.0-20151017003034-trusty) ...
Removing gir1.2-cinnamondesktop-3.0 (2.8.0-20151017000446-trusty) ...
Removing gir1.2-gtkclutter-1.0 (1.4.4-3ubuntu2.2) ...
Removing gir1.2-clutter-1.0 (1.16.4-0ubuntu2) ...
Removing gir1.2-cmenu-3.0 (2.8.0-20151017012126-trusty) ...
Removing gir1.2-coglpango-1.0 (1.16.2-1) ...
Removing gir1.2-cogl-1.0 (1.16.2-1) ...
Removing gir1.2-gkbd-3.0 (3.6.0-0ubuntu2) ...
Removing gir1.2-json-1.0 (0.16.2-1ubuntu1) ...
Removing gir1.2-nmgtk-1.0 (0.9.8.8-0ubuntu4.3) ...
Removing gir1.2-polkit-1.0 (0.105-4ubuntu2.14.04.1) ...
Removing gir1.2-upowerglib-1.0 (0.9.23-2ubuntu1) ...
Removing gir1.2-xkl-1.0 (5.4-0ubuntu1) ...
Removing python-opencv (2.4.8+dfsg1-2ubuntu1) ...
Removing python-numpy (1:1.8.2-0ubuntu0.1) ...
Removing liblapack3 (3.5.0-2ubuntu1) ...
Removing libblas3 (1.2.20110419-7) ...
Removing libcaribou0:amd64 (0.4.13-0ubuntu1) ...
Removing libcaribou-common (0.4.13-0ubuntu1) ...
Removing libcinnamon-control-center1:amd64 (2.8.0-20151017013044-trusty) ...
Removing libcinnamon-desktop4:amd64 (2.8.0-20151017000446-trusty) ...
Removing libcinnamon-menu-3-0 (2.8.0-20151017012126-trusty) ...
Removing libgfortran3:amd64 (4.8.4-2ubuntu1~14.04) ...
Removing libopencv-contrib2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libopencv-objdetect2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libopencv-legacy2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libopencv-highgui2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libgtkglext1 (1.2.0-3.1fakesync3) ...
Removing libopenexr6:amd64 (1.6.1-7ubuntu1) ...
Removing libilmbase6:amd64 (1.0.1-6ubuntu1) ...
Removing libmuffin0 (2.8.0-20151017003034-trusty) ...
Removing libnemo-extension1 (2.6.7-20151017010005-trusty) ...
Removing libopencv-calib3d2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libopencv-video2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libopencv-photo2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libopencv-features2d2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libopencv-flann2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libopencv-imgproc2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libopencv-ml2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing muffin-common (2.8.0-20151017003034-trusty) ...
Removing nemo-data (2.6.7-20151017010005-trusty) ...
Removing python-pyatspi (2.10.0+dfsg-1) ...
Removing python-pyinotify (0.9.4-1build1) ...
Removing libopencv-core2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libtbb2 (4.2~20130725-1.1ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
dennis@dennis1:~$ 
```

---

### Post by SUPERFITTER on 2015-10-25
I dumped Cinnamon and found I had a problem with this driver [B]           rtl8192cu.

Problem solved on this posting:[/B]  [http://ubuntuforums.org/showthread.php?t=2299428](http://ubuntuforums.org/showthread.php?t=2299428)

---

