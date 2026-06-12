---
title: "Adding and removing Lib files difficulties ..."
date: 2016-05-05
forum: General Help
---

### Post by CCgirl6690 on 2016-05-05
hello 
I  am on ubuntu 14.04 LTS 64 bits I was trying to Install an older stand  alone version of flash player so i  searched forums and someone  suggested i ran this command.. 

       Code:

     ~$ sudo apt-get install libgtk2.0-0:i386 libnss3-1d:i386 libnspr4-0d:i386 lib32nss-mdns libxml2:i386 libxslt1.1:i386 
  Then i searched elsewhere and i relaized that 32 bit libs are no  good  for 64 bits system so what i did was to  run this command ...
       Code:
     ~$ sudo apt-get remove libgtk2.0-0:i386 libnss3-1d:i386 libnspr4-0d:i386 lib32nss-mdns libxml2:i386 libxslt1.1:i386 
  Sad thing is after i done that not only i lost my Skype but my  wine  is gone too and now that i'm trying to install wine from software  centre  after i click on install first software centre gets unresponding  and so  slow and a a message pops up saying downloading packages from   nontrusted sources and such... However i somehow fixed that but now some  of my apps are misbeaving.  My question is how do i restore my system  to what it was before i added  those lib files?  Thank you
Also did the remove command really removed those?
Thanks

---

### Post by izznogooood on 2016-05-05
You should use "sudo apt purge" if you want to completely remove something.

Could you please do "sudo apt update" and "sudo apt -f install" paste the output here.

Do you know: Google chrome has a build in flash player?

---

### Post by CCgirl6690 on 2016-05-05
> **izznogooood said:**
> You should use "sudo apt purge" if you want to completely remove something.

Could you please do "sudo apt update" and "sudo apt -f install" paste the output here.

Do you know: Google chrome has a build in flash player?

Hello here is output ,,,
Also yes i know about Chrome but i wanted the stand alone flash player...
```
~$ sudo apt update
Ign http://dl.google.com stable InRelease                                      
Ign http://us.archive.ubuntu.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                       
Hit http://ppa.launchpad.net trusty InRelease                       
Hit http://dl.google.com stable Release.gpg                                    
Hit http://us.archive.ubuntu.com trusty-updates InRelease                      
Hit http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                      
Hit http://us.archive.ubuntu.com trusty-backports InRelease          
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://us.archive.ubuntu.com trusty-security InRelease                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://us.archive.ubuntu.com trusty-updates/main Sources         
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages            
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages             
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages         
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-security/main Sources                  
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-security/restricted Sources            
Hit http://us.archive.ubuntu.com trusty-security/universe Sources              
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-security/multiverse Sources            
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-security/main amd64 Packages           
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-security/restricted amd64 Packages     
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-security/universe amd64 Packages       
Hit http://us.archive.ubuntu.com trusty-security/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com trusty-security/main i386 Packages            
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-security/restricted i386 Packages      
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-security/universe i386 Packages        
Hit http://us.archive.ubuntu.com trusty-security/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com trusty-security/main Translation-en           
Hit http://us.archive.ubuntu.com trusty-security/multiverse Translation-en     
Hit http://us.archive.ubuntu.com trusty-security/restricted Translation-en     
Hit http://us.archive.ubuntu.com trusty-security/universe Translation-en       
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Reading package lists... Done                                                  
none@none-Latitude:~$ sudo apt sudo apt -f install
E: Invalid operation sudo
none@none-Latitude:~$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  glib-networking:i386 gstreamer0.10-fluendo-mp3
  gstreamer0.10-plugins-bad-multiverse gstreamer1.0-x:i386 libaa1:i386
  libao-common libao4 libappframework-java libatk1.0-0:i386 libavc1394-0:i386
  libcaca0:i386 libcairo-gobject2:i386 libcairo2:i386 libdv4:i386 libfaac0
  libgdk-pixbuf2.0-0:i386 libgraphite2-3:i386
  libgstreamer-plugins-good1.0-0:i386 libharfbuzz0b:i386 libhdb9-heimdal
  libiec61883-0:i386 libjasper1:i386 libkdc2-heimdal libmjpegutils-2.1-0
  libmpeg2encpp-2.1-0 libmplex2-2.1-0 libnatpmp1 libnspr4:i386
  libnss-mdns-i386:i386 libnss3:i386 libntdb1 libpango-1.0-0:i386
  libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386 libpixman-1-0:i386
  libproxy1:i386 libraw1394-11:i386 libshout3:i386 libspeex1:i386
  libswingworker-java libtag1-vanilla:i386 libtag1c2a:i386 libwavpack1:i386
  libxcb-render0:i386 libxcb-shm0:i386 linux-image-3.19.0-25-generic
  linux-image-3.19.0-39-generic linux-image-extra-3.19.0-25-generic
  linux-image-extra-3.19.0-39-generic python-ntdb
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
none@none-
```

---

### Post by izznogooood on 2016-05-05
Do you need any of this packages? There are a lot of leftovers from your i386 support.

If you dont need them do "sudo apt-get autoremove" and reboot, this might solve your problem.

And you said you "fixed that", did you edit your sources? I dont have 14.04 so I have nothing to compare it to but that list was looooooooong... 

```
glib-networking:i386 gstreamer0.10-fluendo-mp3
  gstreamer0.10-plugins-bad-multiverse gstreamer1.0-x:i386 libaa1:i386
  libao-common libao4 libappframework-java libatk1.0-0:i386 libavc1394-0:i386
  libcaca0:i386 libcairo-gobject2:i386 libcairo2:i386 libdv4:i386 libfaac0
  libgdk-pixbuf2.0-0:i386 libgraphite2-3:i386
  libgstreamer-plugins-good1.0-0:i386 libharfbuzz0b:i386 libhdb9-heimdal
  libiec61883-0:i386 libjasper1:i386 libkdc2-heimdal libmjpegutils-2.1-0
  libmpeg2encpp-2.1-0 libmplex2-2.1-0 libnatpmp1 libnspr4:i386
  libnss-mdns-i386:i386 libnss3:i386 libntdb1 libpango-1.0-0:i386
  libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386 libpixman-1-0:i386
  libproxy1:i386 libraw1394-11:i386 libshout3:i386 libspeex1:i386
  libswingworker-java libtag1-vanilla:i386 libtag1c2a:i386 libwavpack1:i386
  libxcb-render0:i386 libxcb-shm0:i386 linux-image-3.19.0-25-generic
  linux-image-3.19.0-39-generic linux-image-extra-3.19.0-25-generic
  linux-image-extra-3.19.0-39-generic python-ntdb
```

---

### Post by CCgirl6690 on 2016-05-06
> **izznogooood said:**
> Do you need any of this packages? There are a lot of leftovers from your i386 support.

If you dont need them do "sudo apt-get autoremove" and reboot, this might solve your problem.

And you said you "fixed that", did you edit your sources? I dont have 14.04 so I have nothing to compare it to but that list was looooooooong... 

```
glib-networking:i386 gstreamer0.10-fluendo-mp3
  gstreamer0.10-plugins-bad-multiverse gstreamer1.0-x:i386 libaa1:i386
  libao-common libao4 libappframework-java libatk1.0-0:i386 libavc1394-0:i386
  libcaca0:i386 libcairo-gobject2:i386 libcairo2:i386 libdv4:i386 libfaac0
  libgdk-pixbuf2.0-0:i386 libgraphite2-3:i386
  libgstreamer-plugins-good1.0-0:i386 libharfbuzz0b:i386 libhdb9-heimdal
  libiec61883-0:i386 libjasper1:i386 libkdc2-heimdal libmjpegutils-2.1-0
  libmpeg2encpp-2.1-0 libmplex2-2.1-0 libnatpmp1 libnspr4:i386
  libnss-mdns-i386:i386 libnss3:i386 libntdb1 libpango-1.0-0:i386
  libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386 libpixman-1-0:i386
  libproxy1:i386 libraw1394-11:i386 libshout3:i386 libspeex1:i386
  libswingworker-java libtag1-vanilla:i386 libtag1c2a:i386 libwavpack1:i386
  libxcb-render0:i386 libxcb-shm0:i386 linux-image-3.19.0-25-generic
  linux-image-3.19.0-39-generic linux-image-extra-3.19.0-25-generic
  linux-image-extra-3.19.0-39-generic python-ntdb
```

Hello again..... 
No i don't think i will need them.  Would autoremove only remove them or other things as well? 
Regarding your second question. They somehow got fixed themselves/ Auto updated asked me to repair and i hit repair and couple times and updated again. and the error msg was gone  anyway. 
I will try the auto remove and will let you know thw results....
Again thanks alot for helping. I appreciate this much!!

---

### Post by Impavidus on 2016-05-06
That first command you used installed all those 32 bit libraries, except if they were already installed. Some may have been installed as dependencies of skype or wine. The remove command removed all of them, including those that had been installed earlier, along with everything that depended upon those 32 bit libraries. That's why skype and wine may have disappeared. Pay attention when using uninstall commands. It lists which additional packages will be uninstalled.

For future reference, a better way to uninstall those 32 bit libraries would have been to mark them as automatically installed. This is easy in synaptic, but you can also use the command line. Then, autoremove should uninstall them, except those still relied upon by other packages like skype or wine.

---

