---
title: "Dont install skype after update to 14.10"
date: 2014-11-05
forum: General Help
---

### Post by monk3 on 2014-11-05
Hello all
sorry, but bad speak english.

i install ubuntu 14.04. install skype.

after i update 14.04 to 14.10.
and erased skype during the update 


after install skype
```

root@Monastery:/home/monk/download# apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.

```


```

root@Monastery:/home/monk/download# apt-get update && apt-get upgrade
Ign http://mirror.yandex.ru utopic InRelease
Ign http://mirror.yandex.ru utopic-updates InRelease
Ign http://mirror.yandex.ru utopic-security InRelease
Ign http://mirror.yandex.ru utopic-backports InRelease
Hit http://mirror.yandex.ru utopic Release.gpg 
Get:1 http://mirror.yandex.ru utopic-updates Release.gpg [933 B]
Ign http://archive.canonical.com utopic InRelease                          
Get:2 http://mirror.yandex.ru utopic-security Release.gpg [933 B]          
Hit http://archive.canonical.com utopic Release.gpg                         
Ign http://extras.ubuntu.com utopic InRelease                               
Get:3 http://mirror.yandex.ru utopic-backports Release.gpg [933 B]
Hit http://archive.canonical.com utopic Release                             
Hit http://extras.ubuntu.com utopic Release.gpg                             
Hit http://mirror.yandex.ru utopic Release                                    
Get:4 http://mirror.yandex.ru utopic-updates Release [62,0 kB]                              
Hit http://extras.ubuntu.com utopic Release                                                    
Hit http://archive.canonical.com utopic/partner amd64 Packages                  
Get:5 http://mirror.yandex.ru utopic-security Release [62,0 kB]                                               
Get:6 http://mirror.yandex.ru utopic-backports Release [62,0 kB]                                   
Hit http://extras.ubuntu.com utopic/main Sources                          
Hit http://archive.canonical.com utopic/partner i386 Packages             
Hit http://mirror.yandex.ru utopic/restricted Sources                                          
Hit http://mirror.yandex.ru utopic/main Sources                                         
Hit http://mirror.yandex.ru utopic/universe Sources                                 
Hit http://mirror.yandex.ru utopic/multiverse Sources                               
Hit http://extras.ubuntu.com utopic/main amd64 Packages             
Hit http://mirror.yandex.ru utopic/restricted amd64 Packages        
Hit http://mirror.yandex.ru utopic/main amd64 Packages              
Hit http://mirror.yandex.ru utopic/universe amd64 Packages          
Hit http://mirror.yandex.ru utopic/multiverse amd64 Packages        
Hit http://extras.ubuntu.com utopic/main i386 Packages                                    
Hit http://mirror.yandex.ru utopic/restricted i386 Packages                               
Hit http://mirror.yandex.ru utopic/main i386 Packages                                     
Hit http://mirror.yandex.ru utopic/universe i386 Packages                                 
Hit http://mirror.yandex.ru utopic/multiverse i386 Packages                               
Hit http://mirror.yandex.ru utopic/main Translation-en                                    
Hit http://mirror.yandex.ru utopic/multiverse Translation-en                        
Hit http://mirror.yandex.ru utopic/restricted Translation-en  
Hit http://mirror.yandex.ru utopic/universe Translation-en        
Get:7 http://mirror.yandex.ru utopic-updates/restricted Sources [14 B]
Get:8 http://mirror.yandex.ru utopic-updates/main Sources [8 178 B]                                           
Get:9 http://mirror.yandex.ru utopic-updates/universe Sources [14 B]                                          
Ign http://archive.canonical.com utopic/partner Translation-en                            
Get:10 http://mirror.yandex.ru utopic-updates/multiverse Sources [14 B]                   
Get:11 http://mirror.yandex.ru utopic-updates/restricted amd64 Packages [14 B]           
Get:12 http://mirror.yandex.ru utopic-updates/main amd64 Packages [16,3 kB]               
Get:13 http://mirror.yandex.ru utopic-updates/universe amd64 Packages [2 645 B]           
Get:14 http://mirror.yandex.ru utopic-updates/multiverse amd64 Packages [14 B]            
Get:15 http://mirror.yandex.ru utopic-updates/restricted i386 Packages [14 B]
Get:16 http://mirror.yandex.ru utopic-updates/main i386 Packages [15,9 kB]
Get:17 http://mirror.yandex.ru utopic-updates/universe i386 Packages [2 652 B]
Ign http://extras.ubuntu.com utopic/main Translation-en_US                
Get:18 http://mirror.yandex.ru utopic-updates/multiverse i386 Packages [14 B]                
Ign http://extras.ubuntu.com utopic/main Translation-en                  
Hit http://mirror.yandex.ru utopic-updates/main Translation-en           
Hit http://mirror.yandex.ru utopic-updates/multiverse Translation-en
Hit http://mirror.yandex.ru utopic-updates/restricted Translation-en
Hit http://mirror.yandex.ru utopic-updates/universe Translation-en
Get:19 http://mirror.yandex.ru utopic-security/restricted Sources [14 B]
Get:20 http://mirror.yandex.ru utopic-security/main Sources [8 178 B]
Get:21 http://mirror.yandex.ru utopic-security/universe Sources [14 B]
Get:22 http://mirror.yandex.ru utopic-security/multiverse Sources [14 B]
Get:23 http://mirror.yandex.ru utopic-security/restricted amd64 Packages [14 B]
Get:24 http://mirror.yandex.ru utopic-security/main amd64 Packages [16,3 kB]
Get:25 http://mirror.yandex.ru utopic-security/universe amd64 Packages [2 645 B]
Get:26 http://mirror.yandex.ru utopic-security/multiverse amd64 Packages [14 B]
Get:27 http://mirror.yandex.ru utopic-security/restricted i386 Packages [14 B]
Get:28 http://mirror.yandex.ru utopic-security/main i386 Packages [15,9 kB]
Get:29 http://mirror.yandex.ru utopic-security/universe i386 Packages [2 652 B]
Get:30 http://mirror.yandex.ru utopic-security/multiverse i386 Packages [14 B]
Hit http://mirror.yandex.ru utopic-security/main Translation-en      
Hit http://mirror.yandex.ru utopic-security/multiverse Translation-en
Hit http://mirror.yandex.ru utopic-security/restricted Translation-en
Hit http://mirror.yandex.ru utopic-security/universe Translation-en
Get:31 http://mirror.yandex.ru utopic-backports/restricted amd64 Packages [14 B]
Get:32 http://mirror.yandex.ru utopic-backports/universe amd64 Packages [1 772 B]
Get:33 http://mirror.yandex.ru utopic-backports/main amd64 Packages [14 B]
Get:34 http://mirror.yandex.ru utopic-backports/multiverse amd64 Packages [14 B]
Get:35 http://mirror.yandex.ru utopic-backports/restricted i386 Packages [14 B]
Get:36 http://mirror.yandex.ru utopic-backports/universe i386 Packages [1 772 B]
Get:37 http://mirror.yandex.ru utopic-backports/main i386 Packages [14 B]
Get:38 http://mirror.yandex.ru utopic-backports/multiverse i386 Packages [14 B]
Hit http://mirror.yandex.ru utopic-backports/main Translation-en     
Hit http://mirror.yandex.ru utopic-backports/multiverse Translation-en
Hit http://mirror.yandex.ru utopic-backports/restricted Translation-en
Hit http://mirror.yandex.ru utopic-backports/universe Translation-en
Fetched 284 kB in 2s (96,4 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```

root@Monastery:/home/monk/download# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```

root@Monastery:/home/monk/download# apt-get install skype skype-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype-bin:i386 : Depends: libqtwebkit4:i386 (>= 2.2~2011week36) but it is not going to be installed
                  Depends: libgl1-mesa-glx:i386 but it is not going to be installed
                  Recommends: libasound2-plugins:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```



I get last skype from skype.com:
```

root@Monastery:/home/monk/download# dpkg -i skype-install.deb 
Selecting previously unselected package skype.
(Reading database ... 232534 files and directories currently installed.)
Preparing to unpack skype-install.deb ...
Unpacking skype (4.3.0.37-1) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqtwebkit4 (>= 2.1.0~2011week13); however:
  Package libqtwebkit4:i386 is not installed.
 skype depends on libpulse0; however:
  Package libpulse0:i386 is not installed.
 skype depends on libasound2-plugins; however:

dpkg: error processing package skype (--install):
 dependency problems - leaving unconfigured
Processing triggers for dbus (1.8.8-1ubuntu2) ...
Processing triggers for bamfdaemon (0.5.1+14.10.20140925-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu2) ...
Processing triggers for mime-support (3.55ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Errors were encountered while processing:
 skype

```

search in Google and on this forum but nothing help.
please help me. thanks

---

### Post by slickymaster on 2014-11-05
Hi monk3, welcome to the forums.

You'll have to enable your partner repositories to be able to install Skype, and they were probably been disabled during the upgrading procedure. To enable the Canonical Partners repository, go to **Software & Updates** from Unity dash. Navigate to **Other Software** tab, and enable Canonical Partners repository. Click Close, and Reload buttons to update the cache. Then install Skype.

---

### Post by monk3 on 2014-11-05
canonical partner repo is enabled:
[IMG]http://storage7.static.itmages.com/i/14/1105/h_1415198316_7458373_f9c6381b60.png[/IMG]

---

### Post by slickymaster on 2014-11-05
You can try to to install the dependencies first:```
sudo apt-get install libqtwebkit4:i386 libgl1-mesa-glx:i386 libpulse0:i386 libasound2-plugins:i386
```and afterward install Skpe.

---

### Post by monk3 on 2014-11-05
```

root@Monastery:/home/monk/download# apt-get install libqtwebkit4:i386 libgl1-mesa-glx:i386 libpulse0:i386 libasound2-plugins:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-glx:i386 : Depends: libgl1-mesa-dri:i386 (= 10.3.0-0ubuntu3) but it is not going to be installed
 libpulse0:i386 : Depends: libjson-c2:i386 (>= 0.10) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


root@Monastery:/home/monk/download# apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.

```

---

### Post by slickymaster on 2014-11-05
Can you please post the output you get from```
uname -m
```

---

### Post by monk3 on 2014-11-05
```

root@Monastery:/home/monk/download# uname -m
x86_64

```


and
```

root@Monastery:/home/monk/download# dpkg --print-architecture 
amd64
root@Monastery:/home/monk/download# dpkg --print-foreign-architectures
i386

```

---

### Post by slickymaster on 2014-11-05
Please run the following```
sudo dpkg --add-architecture i386
sudo apt-get update
```and the retry to install Skype

---

### Post by monk3 on 2014-11-05
```

root@Monastery:/home/monk/download# dpkg --add-architecture i386
root@Monastery:/home/monk/download# apt-get update
Ign http://mirror.yandex.ru utopic InRelease
Ign http://mirror.yandex.ru utopic-updates InRelease
Ign http://mirror.yandex.ru utopic-security InRelease
Ign http://mirror.yandex.ru utopic-backports InRelease
Hit http://mirror.yandex.ru utopic Release.gpg 
Hit http://mirror.yandex.ru utopic-updates Release.gpg
Ign http://archive.canonical.com utopic InRelease
Hit http://mirror.yandex.ru utopic-security Release.gpg
Hit http://mirror.yandex.ru utopic-backports Release.gpg
Hit http://mirror.yandex.ru utopic Release     
Hit http://mirror.yandex.ru utopic-updates Release
Hit http://mirror.yandex.ru utopic-security Release                                        
Hit http://mirror.yandex.ru utopic-backports Release                                       
Hit http://mirror.yandex.ru utopic/restricted Sources                                      
Hit http://mirror.yandex.ru utopic/main Sources                                              
Hit http://mirror.yandex.ru utopic/universe Sources                                                        
Hit http://mirror.yandex.ru utopic/multiverse Sources                                                      
Ign http://extras.ubuntu.com utopic InRelease                                             
Hit http://archive.canonical.com utopic Release.gpg                                       
Hit http://mirror.yandex.ru utopic/restricted amd64 Packages        
Hit http://mirror.yandex.ru utopic/main amd64 Packages                                    
Hit http://mirror.yandex.ru utopic/universe amd64 Packages                                
Hit http://extras.ubuntu.com utopic Release.gpg                     
Hit http://mirror.yandex.ru utopic/multiverse amd64 Packages        
Hit http://archive.canonical.com utopic Release                     
Hit http://mirror.yandex.ru utopic/restricted i386 Packages                                 
Hit http://mirror.yandex.ru utopic/main i386 Packages                                       
Hit http://mirror.yandex.ru utopic/universe i386 Packages           
Hit http://mirror.yandex.ru utopic/multiverse i386 Packages         
Hit http://mirror.yandex.ru utopic/main Translation-en                                    
Hit http://mirror.yandex.ru utopic/multiverse Translation-en                              
Hit http://mirror.yandex.ru utopic/restricted Translation-en                              
Hit http://mirror.yandex.ru utopic/universe Translation-en                                
Hit http://mirror.yandex.ru utopic-updates/restricted Sources                             
Hit http://mirror.yandex.ru utopic-updates/main Sources                                   
Hit http://mirror.yandex.ru utopic-updates/universe Sources                               
Hit http://extras.ubuntu.com utopic Release                         
Hit http://mirror.yandex.ru utopic-updates/multiverse Sources                              
Hit http://archive.canonical.com utopic/partner amd64 Packages                      
Hit http://mirror.yandex.ru utopic-updates/restricted amd64 Packages                
Hit http://mirror.yandex.ru utopic-updates/main amd64 Packages
Hit http://mirror.yandex.ru utopic-updates/universe amd64 Packages
Hit http://extras.ubuntu.com utopic/main Sources                  
Hit http://archive.canonical.com utopic/partner i386 Packages     
Hit http://mirror.yandex.ru utopic-updates/multiverse amd64 Packages
Hit http://mirror.yandex.ru utopic-updates/restricted i386 Packages                     
Hit http://mirror.yandex.ru utopic-updates/main i386 Packages                           
Hit http://mirror.yandex.ru utopic-updates/universe i386 Packages                       
Hit http://mirror.yandex.ru utopic-updates/multiverse i386 Packages
Hit http://mirror.yandex.ru utopic-updates/main Translation-en    
Hit http://mirror.yandex.ru utopic-updates/multiverse Translation-en
Hit http://mirror.yandex.ru utopic-updates/restricted Translation-en                    
Hit http://mirror.yandex.ru utopic-updates/universe Translation-en                      
Hit http://mirror.yandex.ru utopic-security/restricted Sources                          
Hit http://mirror.yandex.ru utopic-security/main Sources                                
Hit http://mirror.yandex.ru utopic-security/universe Sources                            
Hit http://extras.ubuntu.com utopic/main amd64 Packages                                 
Get:1 http://archive.canonical.com utopic/partner Translation-en [1 507 B]
Hit http://mirror.yandex.ru utopic-security/multiverse Sources                                       
Hit http://mirror.yandex.ru utopic-security/restricted amd64 Packages                                
Hit http://mirror.yandex.ru utopic-security/main amd64 Packages                
Hit http://mirror.yandex.ru utopic-security/universe amd64 Packages            
Hit http://extras.ubuntu.com utopic/main i386 Packages                                         
Hit http://mirror.yandex.ru utopic-security/multiverse amd64 Packages
Hit http://mirror.yandex.ru utopic-security/restricted i386 Packages
Hit http://mirror.yandex.ru utopic-security/main i386 Packages
Hit http://mirror.yandex.ru utopic-security/universe i386 Packages
Hit http://mirror.yandex.ru utopic-security/multiverse i386 Packages
Hit http://mirror.yandex.ru utopic-security/main Translation-en
Hit http://mirror.yandex.ru utopic-security/multiverse Translation-en
Hit http://mirror.yandex.ru utopic-security/restricted Translation-en
Hit http://mirror.yandex.ru utopic-security/universe Translation-en
Hit http://mirror.yandex.ru utopic-backports/restricted amd64 Packages
Hit http://mirror.yandex.ru utopic-backports/universe amd64 Packages
Hit http://mirror.yandex.ru utopic-backports/main amd64 Packages  
Hit http://mirror.yandex.ru utopic-backports/multiverse amd64 Packages
Hit http://mirror.yandex.ru utopic-backports/restricted i386 Packages
Hit http://mirror.yandex.ru utopic-backports/universe i386 Packages
Hit http://mirror.yandex.ru utopic-backports/main i386 Packages
Hit http://mirror.yandex.ru utopic-backports/multiverse i386 Packages
Hit http://mirror.yandex.ru utopic-backports/main Translation-en
Hit http://mirror.yandex.ru utopic-backports/multiverse Translation-en
Hit http://mirror.yandex.ru utopic-backports/restricted Translation-en
Hit http://mirror.yandex.ru utopic-backports/universe Translation-en
Ign http://extras.ubuntu.com utopic/main Translation-en_US
Ign http://extras.ubuntu.com utopic/main Translation-en
Fetched 1 507 B in 2s (542 B/s)
Reading package lists... Done
root@Monastery:/home/monk/download# apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.

```

---

### Post by slickymaster on 2014-11-05
That's odd because enabling the 32-bit architecture should had resolved it. Let's try one last option:```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
sudo apt-get update && sudo apt-get install skype
```

---

### Post by monk3 on 2014-11-05
```

root@Monastery:/home/monk/download# add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
root@Monastery:/home/monk/download# apt-get update && sudo apt-get install skype
Ign http://mirror.yandex.ru utopic InRelease
Ign http://mirror.yandex.ru utopic-updates InRelease
Ign http://mirror.yandex.ru utopic-security InRelease
Ign http://mirror.yandex.ru utopic-backports InRelease
Hit http://mirror.yandex.ru utopic Release.gpg 
Hit http://mirror.yandex.ru utopic-updates Release.gpg
Hit http://mirror.yandex.ru utopic-security Release.gpg
Hit http://mirror.yandex.ru utopic-backports Release.gpg
Ign http://archive.canonical.com utopic InRelease
Hit http://mirror.yandex.ru utopic Release     
Hit http://mirror.yandex.ru utopic-updates Release
Hit http://mirror.yandex.ru utopic-security Release                                        
Hit http://mirror.yandex.ru utopic-backports Release                                        
Hit http://mirror.yandex.ru utopic/restricted Sources                                       
Hit http://mirror.yandex.ru utopic/main Sources                       
Hit http://mirror.yandex.ru utopic/universe Sources                                                           
Hit http://mirror.yandex.ru utopic/multiverse Sources                                                            
Hit http://mirror.yandex.ru utopic/restricted amd64 Packages                                                     
Hit http://mirror.yandex.ru utopic/main amd64 Packages                                     
Ign http://extras.ubuntu.com utopic InRelease                                             
Ign http://archive.canonical.com utopic InRelease                   
Hit http://mirror.yandex.ru utopic/universe amd64 Packages          
Hit http://mirror.yandex.ru utopic/multiverse amd64 Packages        
Hit http://mirror.yandex.ru utopic/restricted i386 Packages                               
Hit http://mirror.yandex.ru utopic/main i386 Packages                                     
Hit http://mirror.yandex.ru utopic/universe i386 Packages                                 
Hit http://extras.ubuntu.com utopic Release.gpg                                           
Hit http://archive.canonical.com utopic Release.gpg                 
Hit http://mirror.yandex.ru utopic/multiverse i386 Packages         
Hit http://mirror.yandex.ru utopic/main Translation-en              
Hit http://mirror.yandex.ru utopic/multiverse Translation-en                              
Hit http://mirror.yandex.ru utopic/restricted Translation-en                              
Hit http://mirror.yandex.ru utopic/universe Translation-en                                
Hit http://mirror.yandex.ru utopic-updates/restricted Sources                             
Hit http://mirror.yandex.ru utopic-updates/main Sources                                   
Hit http://mirror.yandex.ru utopic-updates/universe Sources                               
Hit http://mirror.yandex.ru utopic-updates/multiverse Sources                             
Hit http://mirror.yandex.ru utopic-updates/restricted amd64 Packages                
Hit http://mirror.yandex.ru utopic-updates/main amd64 Packages
Hit http://extras.ubuntu.com utopic Release                   
Get:1 http://archive.canonical.com utopic Release.gpg [933 B]                            
Hit http://mirror.yandex.ru utopic-updates/universe amd64 Packages                              
Hit http://mirror.yandex.ru utopic-updates/multiverse amd64 Packages                           
Hit http://mirror.yandex.ru utopic-updates/restricted i386 Packages                            
Hit http://mirror.yandex.ru utopic-updates/main i386 Packages     
Hit http://mirror.yandex.ru utopic-updates/universe i386 Packages 
Hit http://mirror.yandex.ru utopic-updates/multiverse i386 Packages                     
Hit http://extras.ubuntu.com utopic/main Sources                                        
Hit http://mirror.yandex.ru utopic-updates/main Translation-en    
Hit http://mirror.yandex.ru utopic-updates/multiverse Translation-en                    
Hit http://mirror.yandex.ru utopic-updates/restricted Translation-en                    
Hit http://mirror.yandex.ru utopic-updates/universe Translation-en                      
Hit http://mirror.yandex.ru utopic-security/restricted Sources                          
Hit http://mirror.yandex.ru utopic-security/main Sources                                
Hit http://mirror.yandex.ru utopic-security/universe Sources                            
Hit http://mirror.yandex.ru utopic-security/multiverse Sources                          
Hit http://archive.canonical.com utopic Release                   
Hit http://mirror.yandex.ru utopic-security/restricted amd64 Packages                                           
Hit http://mirror.yandex.ru utopic-security/main amd64 Packages                                                 
Hit http://mirror.yandex.ru utopic-security/universe amd64 Packages                     
Hit http://extras.ubuntu.com utopic/main amd64 Packages                                 
Hit http://mirror.yandex.ru utopic-security/multiverse amd64 Packages                   
Get:2 http://archive.canonical.com utopic Release [8 796 B]       
Hit http://mirror.yandex.ru utopic-security/restricted i386 Packages                          
Hit http://mirror.yandex.ru utopic-security/main i386 Packages                                
Hit http://mirror.yandex.ru utopic-security/universe i386 Packages      
Hit http://mirror.yandex.ru utopic-security/multiverse i386 Packages    
Hit http://mirror.yandex.ru utopic-security/main Translation-en                               
Hit http://extras.ubuntu.com utopic/main i386 Packages                                        
Hit http://mirror.yandex.ru utopic-security/multiverse Translation-en                         
Hit http://mirror.yandex.ru utopic-security/restricted Translation-en                         
Hit http://mirror.yandex.ru utopic-security/universe Translation-en                           
Hit http://mirror.yandex.ru utopic-backports/restricted amd64 Packages                        
Hit http://mirror.yandex.ru utopic-backports/universe amd64 Packages                                              
Hit http://mirror.yandex.ru utopic-backports/main amd64 Packages                                                  
Hit http://mirror.yandex.ru utopic-backports/multiverse amd64 Packages                  
Hit http://mirror.yandex.ru utopic-backports/restricted i386 Packages
Hit http://mirror.yandex.ru utopic-backports/universe i386 Packages
Hit http://mirror.yandex.ru utopic-backports/main i386 Packages   
Hit http://archive.canonical.com utopic/partner amd64 Packages                          
Hit http://mirror.yandex.ru utopic-backports/multiverse i386 Packages                   
Hit http://mirror.yandex.ru utopic-backports/main Translation-en
Hit http://mirror.yandex.ru utopic-backports/multiverse Translation-en
Hit http://mirror.yandex.ru utopic-backports/restricted Translation-en
Hit http://mirror.yandex.ru utopic-backports/universe Translation-en
Hit http://archive.canonical.com utopic/partner i386 Packages     
Get:3 http://archive.canonical.com utopic/partner amd64 Packages [2 899 B]
Get:4 http://archive.canonical.com utopic/partner i386 Packages [3 251 B]                
Ign http://extras.ubuntu.com utopic/main Translation-en_US                  
Ign http://extras.ubuntu.com utopic/main Translation-en
Ign http://archive.canonical.com utopic/partner Translation-en
Ign http://archive.canonical.com utopic/partner Translation-en
Fetched 15,9 kB in 2s (5 972 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.

```

and duplicate repo in "Software & Updates":
[IMG]http://i.imgur.com/C61XlrZ.png[/IMG]

---

### Post by slickymaster on 2014-11-05
> **monk3 said:**
> ```

root@Monastery:/home/monk/download# dpkg --add-architecture i386
root@Monastery:/home/monk/download# apt-get update
Ign http://mirror.yandex.ru utopic InRelease
Ign http://mirror.yandex.ru utopic-updates InRelease
Ign http://mirror.yandex.ru utopic-security InRelease
Ign http://mirror.yandex.ru utopic-backports InRelease
Hit http://mirror.yandex.ru utopic Release.gpg 
Hit http://mirror.yandex.ru utopic-updates Release.gpg
Ign http://archive.canonical.com utopic InRelease
Hit http://mirror.yandex.ru utopic-security Release.gpg
Hit http://mirror.yandex.ru utopic-backports Release.gpg
Hit http://mirror.yandex.ru utopic Release     
Hit http://mirror.yandex.ru utopic-updates Release
Hit http://mirror.yandex.ru utopic-security Release                                        
Hit http://mirror.yandex.ru utopic-backports Release                                       
Hit http://mirror.yandex.ru utopic/restricted Sources                                      
Hit http://mirror.yandex.ru utopic/main Sources                                              
Hit http://mirror.yandex.ru utopic/universe Sources                                                        
Hit http://mirror.yandex.ru utopic/multiverse Sources                                                      
Ign http://extras.ubuntu.com utopic InRelease                                             
Hit http://archive.canonical.com utopic Release.gpg                                       
Hit http://mirror.yandex.ru utopic/restricted amd64 Packages        
Hit http://mirror.yandex.ru utopic/main amd64 Packages                                    
Hit http://mirror.yandex.ru utopic/universe amd64 Packages                                
Hit http://extras.ubuntu.com utopic Release.gpg                     
Hit http://mirror.yandex.ru utopic/multiverse amd64 Packages        
Hit http://archive.canonical.com utopic Release                     
Hit http://mirror.yandex.ru utopic/restricted i386 Packages                                 
Hit http://mirror.yandex.ru utopic/main i386 Packages                                       
Hit http://mirror.yandex.ru utopic/universe i386 Packages           
Hit http://mirror.yandex.ru utopic/multiverse i386 Packages         
Hit http://mirror.yandex.ru utopic/main Translation-en                                    
Hit http://mirror.yandex.ru utopic/multiverse Translation-en                              
Hit http://mirror.yandex.ru utopic/restricted Translation-en                              
Hit http://mirror.yandex.ru utopic/universe Translation-en                                
Hit http://mirror.yandex.ru utopic-updates/restricted Sources                             
Hit http://mirror.yandex.ru utopic-updates/main Sources                                   
Hit http://mirror.yandex.ru utopic-updates/universe Sources                               
Hit http://extras.ubuntu.com utopic Release                         
Hit http://mirror.yandex.ru utopic-updates/multiverse Sources                              
Hit http://archive.canonical.com utopic/partner amd64 Packages                      
Hit http://mirror.yandex.ru utopic-updates/restricted amd64 Packages                
Hit http://mirror.yandex.ru utopic-updates/main amd64 Packages
Hit http://mirror.yandex.ru utopic-updates/universe amd64 Packages
Hit http://extras.ubuntu.com utopic/main Sources                  
Hit http://archive.canonical.com utopic/partner i386 Packages     
Hit http://mirror.yandex.ru utopic-updates/multiverse amd64 Packages
Hit http://mirror.yandex.ru utopic-updates/restricted i386 Packages                     
Hit http://mirror.yandex.ru utopic-updates/main i386 Packages                           
Hit http://mirror.yandex.ru utopic-updates/universe i386 Packages                       
Hit http://mirror.yandex.ru utopic-updates/multiverse i386 Packages
Hit http://mirror.yandex.ru utopic-updates/main Translation-en    
Hit http://mirror.yandex.ru utopic-updates/multiverse Translation-en
Hit http://mirror.yandex.ru utopic-updates/restricted Translation-en                    
Hit http://mirror.yandex.ru utopic-updates/universe Translation-en                      
Hit http://mirror.yandex.ru utopic-security/restricted Sources                          
Hit http://mirror.yandex.ru utopic-security/main Sources                                
Hit http://mirror.yandex.ru utopic-security/universe Sources                            
Hit http://extras.ubuntu.com utopic/main amd64 Packages                                 
Get:1 http://archive.canonical.com utopic/partner Translation-en [1 507 B]
Hit http://mirror.yandex.ru utopic-security/multiverse Sources                                       
Hit http://mirror.yandex.ru utopic-security/restricted amd64 Packages                                
Hit http://mirror.yandex.ru utopic-security/main amd64 Packages                
Hit http://mirror.yandex.ru utopic-security/universe amd64 Packages            
Hit http://extras.ubuntu.com utopic/main i386 Packages                                         
Hit http://mirror.yandex.ru utopic-security/multiverse amd64 Packages
Hit http://mirror.yandex.ru utopic-security/restricted i386 Packages
Hit http://mirror.yandex.ru utopic-security/main i386 Packages
Hit http://mirror.yandex.ru utopic-security/universe i386 Packages
Hit http://mirror.yandex.ru utopic-security/multiverse i386 Packages
Hit http://mirror.yandex.ru utopic-security/main Translation-en
Hit http://mirror.yandex.ru utopic-security/multiverse Translation-en
Hit http://mirror.yandex.ru utopic-security/restricted Translation-en
Hit http://mirror.yandex.ru utopic-security/universe Translation-en
Hit http://mirror.yandex.ru utopic-backports/restricted amd64 Packages
Hit http://mirror.yandex.ru utopic-backports/universe amd64 Packages
Hit http://mirror.yandex.ru utopic-backports/main amd64 Packages  
Hit http://mirror.yandex.ru utopic-backports/multiverse amd64 Packages
Hit http://mirror.yandex.ru utopic-backports/restricted i386 Packages
Hit http://mirror.yandex.ru utopic-backports/universe i386 Packages
Hit http://mirror.yandex.ru utopic-backports/main i386 Packages
Hit http://mirror.yandex.ru utopic-backports/multiverse i386 Packages
Hit http://mirror.yandex.ru utopic-backports/main Translation-en
Hit http://mirror.yandex.ru utopic-backports/multiverse Translation-en
Hit http://mirror.yandex.ru utopic-backports/restricted Translation-en
Hit http://mirror.yandex.ru utopic-backports/universe Translation-en
Ign http://extras.ubuntu.com utopic/main Translation-en_US
Ign http://extras.ubuntu.com utopic/main Translation-en
Fetched 1 507 B in 2s (542 B/s)
Reading package lists... Done
root@Monastery:/home/monk/download# apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.

```

I see that after enabling the [COLOR=#000000]32-bit architecture you didn't update your packages list, which you should have, like I posted, [/COLOR][COLOR=#000000]before installing Skipe. [/COLOR]:P

---

### Post by monk3 on 2014-11-05
in 2 line update package list or are you talking about something else?

---

### Post by slickymaster on 2014-11-05
> **monk3 said:**
> ```


and duplicate repo in "Software & Updates":
[IMG]http://i.imgur.com/C61XlrZ.png[/IMG]

That duplicate entry has to be removed. As a matter of fact remove all partner repositories entries, please

> **monk3 said:**
> in 2 line update package list or are you talking about something else?

Yeah, you're right. I didn't saw it.

Let's start fresh by entirely removing Skype[CODE]sudo apt-get remove skype skype-bin:i386 skype:i386
rm -rf ~/.Skype
```.

Then:```
sudo apt-get install sni-qt:i386
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
sudo apt-get update && sudo apt-get install skype
```
Keeping my fingers crossed.;)

---

### Post by monk3 on 2014-11-05
duplicate repo delete.

after in console:

```

root@Monastery:/home/monk/download# apt-get remove skype skype-bin:i386 skype:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'skype' is not installed, so not removed
Package 'skype:i386' is not installed, so not removed
Package 'skype-bin:i386' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@Monastery:/home/monk/download# rm -rf ~/.Skype

```

after:
```

root@Monastery:/home/monk/download# apt-get install sni-qt:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sni-qt:i386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@Monastery:/home/monk/download# add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
root@Monastery:/home/monk/download# apt-get update && sudo apt-get install skype
Ign http://mirror.yandex.ru utopic InRelease
Ign http://mirror.yandex.ru utopic-updates InRelease
Ign http://mirror.yandex.ru utopic-security InRelease
Ign http://mirror.yandex.ru utopic-backports InRelease
Hit http://mirror.yandex.ru utopic Release.gpg 
Ign http://archive.canonical.com utopic InRelease
Ign http://extras.ubuntu.com utopic InRelease  
Hit http://mirror.yandex.ru utopic-updates Release.gpg
Hit http://mirror.yandex.ru utopic-security Release.gpg
Hit http://mirror.yandex.ru utopic-backports Release.gpg
Hit http://mirror.yandex.ru utopic Release     
Hit http://mirror.yandex.ru utopic-updates Release                                         
Hit http://mirror.yandex.ru utopic-security Release                                        
Hit http://mirror.yandex.ru utopic-backports Release                                        
Hit http://mirror.yandex.ru utopic/restricted Sources                                       
Hit http://mirror.yandex.ru utopic/main Sources                                             
Hit http://mirror.yandex.ru utopic/universe Sources                                                           
Ign http://archive.canonical.com utopic InRelease                                                          
Hit http://mirror.yandex.ru utopic/multiverse Sources                                     
Hit http://extras.ubuntu.com utopic Release.gpg                                           
Hit http://mirror.yandex.ru utopic/restricted amd64 Packages                              
Hit http://mirror.yandex.ru utopic/main amd64 Packages              
Hit http://mirror.yandex.ru utopic/universe amd64 Packages          
Hit http://archive.canonical.com utopic Release.gpg                 
Hit http://mirror.yandex.ru utopic/multiverse amd64 Packages        
Hit http://extras.ubuntu.com utopic Release                         
Hit http://mirror.yandex.ru utopic/restricted i386 Packages                                
Hit http://mirror.yandex.ru utopic/main i386 Packages               
Hit http://mirror.yandex.ru utopic/universe i386 Packages                                 
Hit http://mirror.yandex.ru utopic/multiverse i386 Packages                               
Hit http://mirror.yandex.ru utopic/main Translation-en              
Hit http://mirror.yandex.ru utopic/multiverse Translation-en        
Hit http://mirror.yandex.ru utopic/restricted Translation-en        
Hit http://mirror.yandex.ru utopic/universe Translation-en          
Hit http://mirror.yandex.ru utopic-updates/restricted Sources                             
Get:1 http://archive.canonical.com utopic Release.gpg [933 B]                             
Hit http://mirror.yandex.ru utopic-updates/main Sources                                         
Hit http://mirror.yandex.ru utopic-updates/universe Sources                                
Hit http://extras.ubuntu.com utopic/main Sources                     
Hit http://mirror.yandex.ru utopic-updates/multiverse Sources        
Hit http://mirror.yandex.ru utopic-updates/restricted amd64 Packages                       
Hit http://mirror.yandex.ru utopic-updates/main amd64 Packages                             
Hit http://extras.ubuntu.com utopic/main amd64 Packages                  
Hit http://mirror.yandex.ru utopic-updates/universe amd64 Packages
Hit http://mirror.yandex.ru utopic-updates/multiverse amd64 Packages
Hit http://mirror.yandex.ru utopic-updates/restricted i386 Packages
Hit http://mirror.yandex.ru utopic-updates/main i386 Packages                           
Hit http://mirror.yandex.ru utopic-updates/universe i386 Packages                       
Hit http://mirror.yandex.ru utopic-updates/multiverse i386 Packages
Hit http://archive.canonical.com utopic Release                   
Hit http://mirror.yandex.ru utopic-updates/main Translation-en                                                  
Hit http://mirror.yandex.ru utopic-updates/multiverse Translation-en                    
Hit http://mirror.yandex.ru utopic-updates/restricted Translation-en                    
Hit http://mirror.yandex.ru utopic-updates/universe Translation-en
Hit http://mirror.yandex.ru utopic-security/restricted Sources    
Hit http://extras.ubuntu.com utopic/main i386 Packages                                  
Hit http://mirror.yandex.ru utopic-security/main Sources                                
Hit http://mirror.yandex.ru utopic-security/universe Sources                            
Hit http://mirror.yandex.ru utopic-security/multiverse Sources    
Hit http://mirror.yandex.ru utopic-security/restricted amd64 Packages
Get:2 http://archive.canonical.com utopic Release [8 796 B]       
Hit http://mirror.yandex.ru utopic-security/main amd64 Packages                               
Hit http://mirror.yandex.ru utopic-security/universe amd64 Packages                           
Hit http://mirror.yandex.ru utopic-security/multiverse amd64 Packages   
Hit http://mirror.yandex.ru utopic-security/restricted i386 Packages
Hit http://mirror.yandex.ru utopic-security/main i386 Packages
Hit http://mirror.yandex.ru utopic-security/universe i386 Packages
Hit http://mirror.yandex.ru utopic-security/multiverse i386 Packages
Hit http://archive.canonical.com utopic/partner amd64 Packages    
Hit http://mirror.yandex.ru utopic-security/main Translation-en   
Hit http://mirror.yandex.ru utopic-security/multiverse Translation-en
Hit http://mirror.yandex.ru utopic-security/restricted Translation-en
Hit http://mirror.yandex.ru utopic-security/universe Translation-en
Hit http://mirror.yandex.ru utopic-backports/restricted amd64 Packages
Hit http://mirror.yandex.ru utopic-backports/universe amd64 Packages
Hit http://mirror.yandex.ru utopic-backports/main amd64 Packages                        
Hit http://archive.canonical.com utopic/partner i386 Packages                           
Hit http://mirror.yandex.ru utopic-backports/multiverse amd64 Packages
Hit http://mirror.yandex.ru utopic-backports/restricted i386 Packages                   
Hit http://mirror.yandex.ru utopic-backports/universe i386 Packages                     
Hit http://mirror.yandex.ru utopic-backports/main i386 Packages   
Hit http://mirror.yandex.ru utopic-backports/multiverse i386 Packages                   
Hit http://mirror.yandex.ru utopic-backports/main Translation-en                        
Hit http://mirror.yandex.ru utopic-backports/multiverse Translation-en
Hit http://mirror.yandex.ru utopic-backports/restricted Translation-en
Hit http://mirror.yandex.ru utopic-backports/universe Translation-en
Get:3 http://archive.canonical.com utopic/partner amd64 Packages [2 899 B]
Get:4 http://archive.canonical.com utopic/partner i386 Packages [3 251 B]                
Ign http://extras.ubuntu.com utopic/main Translation-en_US                                  
Ign http://extras.ubuntu.com utopic/main Translation-en              
Ign http://archive.canonical.com utopic/partner Translation-en 
Ign http://archive.canonical.com utopic/partner Translation-en
Fetched 15,9 kB in 3s (5 154 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.

```

---

### Post by slickymaster on 2014-11-05
:mad::mad::mad::confused:

If you're up for it, try to install it from the .deb file:
[LIST=1]
[*][Download]("http://www.skype.com/en/download-skype/skype-for-linux/downloading/?type=ubuntu64") it from their site
[*]When the download has finished, open the downloaded file as normal from Nautilus.
[*]When prompted, select Open with Ubuntu Software Center (default).
[*]In the right side of the Ubuntu Software Center window that opens, select Install.
[/LIST]

If you're unable to install it this way, open a terminal window, navigate to the folder where the downloaded deb file is and run```
sudo dpkg --force-depends -i skype-ubuntu-precise_4.3.0.37-1_i386.deb
```

---

### Post by monk3 on 2014-11-05
i download in you link, after click from Nautilus, and after:
[IMG]http://storage6.static.itmages.com/i/14/1105/h_1415206775_6259484_8d844b30ec.png[/IMG]


:(

---

### Post by monk3 on 2014-11-05
and install from dpkg:

```

root@Monastery:/home/monk/download# dpkg --force-depends -i skype-ubuntu-precise_4.3.0.37-1_i386.deb
Selecting previously unselected package skype.
(Reading database ... 232534 files and directories currently installed.)
Preparing to unpack skype-ubuntu-precise_4.3.0.37-1_i386.deb ...
Unpacking skype (4.3.0.37-1) ...
dpkg: skype: dependency problems, but configuring anyway as you requested:
 skype depends on libqtwebkit4 (>= 2.2~2011week36); however:
  Package libqtwebkit4:i386 is not installed.
 skype depends on libpulse0; however:
  Package libpulse0:i386 is not installed.
 skype depends on libasound2-plugins; however:

Setting up skype (4.3.0.37-1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for bamfdaemon (0.5.1+14.10.20140925-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu2) ...
Processing triggers for mime-support (3.55ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for dbus (1.8.8-1ubuntu2) ...
root@Monastery:/home/monk/download# skype & 
[4] 20667
root@Monastery:/home/monk/download# skype: error while loading shared libraries: libQtWebKit.so.4: cannot open shared object file: No such file or directory

```

---

### Post by slickymaster on 2014-11-05
> **monk3 said:**
> and install from dpkg:

```

root@Monastery:/home/monk/download# dpkg --force-depends -i skype-ubuntu-precise_4.3.0.37-1_i386.deb
Selecting previously unselected package skype.
(Reading database ... 232534 files and directories currently installed.)
Preparing to unpack skype-ubuntu-precise_4.3.0.37-1_i386.deb ...
Unpacking skype (4.3.0.37-1) ...
dpkg: skype: dependency problems, but configuring anyway as you requested:
 skype depends on libqtwebkit4 (>= 2.2~2011week36); however:
  Package libqtwebkit4:i386 is not installed.
 skype depends on libpulse0; however:
  Package libpulse0:i386 is not installed.
 skype depends on libasound2-plugins; however:

Setting up skype (4.3.0.37-1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for bamfdaemon (0.5.1+14.10.20140925-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu2) ...
Processing triggers for mime-support (3.55ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for dbus (1.8.8-1ubuntu2) ...
root@Monastery:/home/monk/download# skype & 
[4] 20667
root@Monastery:/home/monk/download# skype: error while loading shared libraries: libQtWebKit.so.4: cannot open shared object file: No such file or directory

```

Let's try again to install those two missing packages```
sudo apt-get -f install libqtwebkit4:i386 libpulse0:i386
```

---

### Post by monk3 on 2014-11-06
again broken package:

```

root@Monastery:/home/monk/download#  apt-get -f install libqtwebkit4:i386 libpulse0:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libpulse0:i386 : Depends: libjson-c2:i386 (>= 0.10) but it is not going to be installed
 libqtwebkit4:i386 : Depends: libgl1-mesa-glx:i386 but it is not going to be installed or
                              libgl1:i386
                     Depends: libqt4-opengl:i386 (>= 4:4.5.3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by slickymaster on 2014-11-06
Just a shot in the dark here as I'm not 100% sure that it will work, but if you're willing to take the risk, download both packages from the Utopic's Package archive and try to force their installation.

[libqtwebkit4:i386]("http://packages.ubuntu.com/utopic/i386/libqtwebkit4/download")
[libpulse0:i386]("http://packages.ubuntu.com/utopic/i386/libpulse0/download")

After downloading them run```
sudo dpkg --force-depends -i libqtwebkit4_2.3.2-0ubuntu7_i386.deb
```and```
sudo dpkg --force-depends -i libpulse0_4.0-0ubuntu22_i386.deb
```

Good luck.

---

### Post by monk3 on 2014-11-06
hmmm

```

root@Monastery:/home/monk/download# dpkg --force-depends -i libqtwebkit4_2.3.2-0ubuntu7_i386.deb 
Selecting previously unselected package libqtwebkit4:i386.
(Reading database ... 232534 files and directories currently installed.)
Preparing to unpack libqtwebkit4_2.3.2-0ubuntu7_i386.deb ...
Unpacking libqtwebkit4:i386 (2.3.2-0ubuntu7) ...
dpkg: libqtwebkit4:i386: dependency problems, but configuring anyway as you requested:
 libqtwebkit4:i386 depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx:i386 is not installed.
  Package libgl1-mesa-glx:i386 which provides libgl1 is not installed.
 libqtwebkit4:i386 depends on libqt4-opengl (>= 4:4.5.3); however:
  Package libqt4-opengl:i386 is not installed.

Setting up libqtwebkit4:i386 (2.3.2-0ubuntu7) ...
Processing triggers for libc-bin (2.19-10ubuntu2) ...



root@Monastery:/home/monk/download# dpkg --force-depends -i libpulse0_4.0-0ubuntu22_i386.deb
Selecting previously unselected package libpulse0:i386.
(Reading database ... 232537 files and directories currently installed.)
Preparing to unpack libpulse0_4.0-0ubuntu22_i386.deb ...
Unpacking libpulse0:i386 (1:4.0-0ubuntu22) ...
dpkg: libpulse0:i386: dependency problems, but configuring anyway as you requested:
 libpulse0:i386 depends on libjson-c2 (>= 0.10); however:
  Package libjson-c2:i386 is not installed.

Setting up libpulse0:i386 (1:4.0-0ubuntu22) ...
Processing triggers for libc-bin (2.19-10ubuntu2) ...



root@Monastery:/home/monk/download# apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libpulse0:i386 : Depends: libjson-c2:i386 (>= 0.10) but it is not going to be installed
 libqtwebkit4:i386 : Depends: libgl1-mesa-glx:i386 but it is not going to be installed or
                              libgl1:i386
                     Depends: libqt4-opengl:i386 (>= 4:4.5.3) but it is not going to be installed
 skype : Depends: skype-bin
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


root@Monastery:/home/monk/download# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libmirplatform3driver-android ncurses-term openssh-server openssh-sftp-server qtmir-android ssh ssh-import-id
Suggested packages:
  rssh molly-guard monkeysphere
The following packages will be REMOVED:
  account-plugin-aim account-plugin-jabber account-plugin-salut account-plugin-yahoo cheese empathy gir1.2-totem-1.0 gnome-contacts libegl1-mesa-drivers
  libmirplatform3driver-mesa libpulse0:i386 libqtwebkit4:i386 libtotem0 libxatracker2 mcp-account-manager-uoa php-pear php5 php5-cli php5-fpm pkg-php-tools
  qtmir-desktop totem totem-mozilla totem-plugins xserver-xorg-video-all xserver-xorg-video-vmware
The following NEW packages will be installed:
  libmirplatform3driver-android ncurses-term openssh-server openssh-sftp-server qtmir-android ssh ssh-import-id
0 upgraded, 7 newly installed, 26 to remove and 24 not upgraded.
Need to get 841 kB of archives.
After this operation, 77,7 MB disk space will be freed.
Do you want to continue? [Y/n]

```


thanks all [**[COLOR=#C61919][B]slickymaster**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1753126")

in summ: full reinstall ubuntu 14.10
:(

---

