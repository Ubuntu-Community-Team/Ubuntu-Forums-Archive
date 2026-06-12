---
title: "Notebook update stalls 14.04"
date: 2015-03-20
forum: General Help
---

### Post by RogerDavis on 2015-03-20
I'm trying to update the notebook, it's been at it for about 3 hours, progress bar has not moved from about half done.  The cursor "wheel" is constantly turning, but no advancement.

How do I most safely stop this if it continues to be stalled?

Then what do I do?

---

### Post by dino99 on 2015-03-20
which net connection is it ? (wire/wifi/...)
maybe try an other mirror

---

### Post by ajgreeny on 2015-03-20
What sort of update are you talking about?
Is this a standard sudo apt-get update, are you using the update-manager, or are you updating a system from a previous Ubuntu version; do you remember what packages were to be updated?

More info please.

---

### Post by grahammechanical on 2015-03-20
The stupid thing might be waiting some authentication from you but the dialog may be hidden behind the update window. Move the update window to one side and see if another window is being hidden.

Regards from the wild guess department.

---

### Post by RogerDavis on 2015-03-20
Details :
- Using Software Updater
- wireless connection, it can see the internet, can get pages
- The update that was in progress apparently finished overnight, restarted, check for updates, said "up to date"
- Attempt to recheck for updates later first says "Failed to download repository information"
- Try again, same result
- Just look at settings, no change, close, then it says "Updates available", about 43 megabytes worth
- Select "Install Now", says requires untrusted packages
- Select ok to install them, display disappears, no further actions or screen display from Software Updater.
- Shut down, repeat, all goes exactly as above from "Attempt to recheck..."

---

### Post by v3.xx on 2015-03-20
Please run
```
sudo apt-get update
```
and post any errors.

---

### Post by RogerDavis on 2015-03-20
RESULTS OF SUDO APT-GET UPDATE

roger@earlleen-ThinkPad-R50p:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [62.0 kB]             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Get:3 [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all InRelease [1,891 B]                 
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all InRelease                             
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main i386 Packages/DiffIndex          
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [62.0 kB]            
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [72.5 kB]        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release                      
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [2,061 B]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [17.9 kB]    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [1,905 B]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [212 kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [8,846 B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [88.2 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [3,628 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [184 kB]       
Err [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Sources                          
  404  Not Found
Hit [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main i386 Packages                    
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Translation-en_US                
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Translation-en                   
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [2,564 B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [107 kB]  
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [4,484 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [443 kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [9,256 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [260 kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [11.3 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Fetched 1,556 kB in 13s (112 kB/s)                                             
W: GPG error: [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29
W: Failed to fetch [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/main/source/Sources](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/main/source/Sources)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by v3.xx on 2015-03-20
With the exception of sourceforge, your sources look good.  For the moment I would disable (uncheck) sourceforge in 'Software Sources'.
```
software-properties-gtk
```
Do you use source code to build packages?  If not, I would just go ahead and also disable all source code in 'software sources' and run another update.

If your update now is good, try an upgrade.
```
sudo apt-get upgrade
```
And on a side note, code tags will keep this thread from becoming very long.
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by RogerDavis on 2015-03-20
We are making progress.

- Removed SourceForge from list, both regular and source
- Removed independent source from list
All seems to work well.

Added back the regular SourceForge (main, not source)
- same as before, not good
This leads to a question - don't I need the SourceForge main updates?   Also the line    [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all    is in the laptop list, the line on my desktop (no problems) is exactly the same.  Why the different result?  

Result of  sudo apt-get upgrade with all you suggested unchecked :
roger@earlleen-ThinkPad-R50p:~$ sudo apt-get upgrade
[sudo] password for roger:
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by RogerDavis on 2015-03-20
Rechecked SourceForge main on list, reran sudo apt-get upgrade :

roger@earlleen-ThinkPad-R50p:~$ sudo apt-get upgrade
[sudo] password for roger:
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  seamonkey-mozilla-build
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 43.0 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  seamonkey-mozilla-build
Install these packages without verification? [y/N] y
Get:1 [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/) all/main seamonkey-mozilla-build i386 2.33-0ubuntu1 [43.0 MB]
Fetched 43.0 MB in 1min 13s (587 kB/s)                                        
(Reading database ... 344328 files and directories currently installed.)
Preparing to unpack .../seamonkey-mozilla-build_2.33-0ubuntu1_i386.deb ...
Unpacking seamonkey-mozilla-build (2.33-0ubuntu1) over (2.32.1-0ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up seamonkey-mozilla-build (2.33-0ubuntu1) ...

The desktop doesn't have a problem with this being unauthenticated.  Do I need to change settings on the laptop to fix this?

Also, Software Updater now works with the SourceForge main rechecked !

---

### Post by v3.xx on 2015-03-20
> W: GPG error: [http://downloads.sourceforge.net](http://downloads.sourceforge.net)  all InRelease: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY CCC158AFC1289A29

You can either enter the pubkey or reset.  Both methods work.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+NO_PUBKEY&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+NO_PUBKEY&sa=Search&cof=FORID:9)

---

### Post by RogerDavis on 2015-03-20
I think I have it, just want to make REALLY sure before I commit it :

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CCC158AFC1289A29
```

Please confirm and much thanks!

---

### Post by v3.xx on 2015-03-20
I put a space in it
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CCC158AF C1289A29
```
Don't forget to update

---

### Post by RogerDavis on 2015-03-21
So then 

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CCC158AF C1289A29
```

and then

```
sudo apt-get update
```

Is the exact way to do it?

---

### Post by RogerDavis on 2015-03-21
I did the above - result :

roger@earlleen-ThinkPad-R50p:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CCC158AF C1289A29[sudo] password for roger: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.5PIx3RZGpP --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys CCC158AF C1289A29
gpg: requesting key CCC158AF from hkp server keyserver.ubuntu.com
gpg: requesting key C1289A29 from hkp server keyserver.ubuntu.com
gpgkeys: key CCC158AF not found on keyserver
gpg: key C1289A29: public key "Daniel Folkinshteyn (Ubuntuzilla signing key) <nanotube@users.sourceforge.net>" imported
gpg: Total number processed: 1
gpg:               imported: 1
roger@earlleen-ThinkPad-R50p:~$ 

roger@earlleen-ThinkPad-R50p:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [62.0 kB]             
Get:3 [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all InRelease [1,891 B]                 
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [72.5 kB]        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [2,061 B]  
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [17.9 kB]    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [1,905 B]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [212 kB]  
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [62.0 kB]           
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Translation-en_US                
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [8,846 B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [88.2 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Get:14 [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main i386 Packages [858 B]         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [3,628 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [184 kB]       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en    
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [2,564 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [107 kB]   
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [4,484 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [444 kB] 
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [9,256 B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [260 kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [11.3 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Fetched 1,558 kB in 33s (47.1 kB/s)                                            
Reading package lists... Done
roger@earlleen-ThinkPad-R50p:~$ 

I don't think I can really test Software Updater until SeaMonkey has another update, but this seems to have no errors except  "gpgkeys: key CCC158AF not found on keyserver" , but it seems to me that this might be part of the process?

Thanks !!

---

### Post by v3.xx on 2015-03-21
From the above update
> Get:3 [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all InRelease [1,891 B]
So its checking for seamonkey updates and no gpg error.

CCC158AF is no concern, gpgkey has been imported.

Looks good :)

---

### Post by RogerDavis on 2015-03-21
Thank you for your quick and knowledgeable help!!!

---

