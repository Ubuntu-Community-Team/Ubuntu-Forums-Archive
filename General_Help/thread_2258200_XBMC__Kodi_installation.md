---
title: "XBMC / Kodi installation"
date: 2014-12-25
forum: General Help
---

### Post by petermartin2 on 2014-12-25
I tried installing XBMC using Ubuntu After Install as I've done before with success. However during the installation process the program (Ubuntu After Install) crashed and when I restarted it again everything seemed to be fine it checked all the installed and continued instlaling. However afterwards a few of the programs are not showing up in dash unity search. The only one I really cared about is XBMC so I tried removing it and installing it again from software center. When this didn't work I went through these steps in terminal:

```
sudo apt-get install python-software-properties pkg-config
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update

 sudo apt-get install xbmc # for 13.2

sudo apt-get install kodi # for 14.0 and up
```
Still no XBMC in dash unity search or in /usr/bin/

What could be the problem?

---

### Post by papibe on 2014-12-25
Hi  petermartin2

Could you open a terminal, run this command and post back the results (you can copy/paste the text)?
```
apt-cache policy xbmc kodi
```
Regards.

---

### Post by petermartin2 on 2014-12-25
E: Opening configuration file ache - ifstream::ifstream (2: No such file or directory)

however in software center and ubuntu after install it appears as installed

I'm getting system program problem detected's on startup and opening browser etc etc now so I think I'm going to have to do a complete reinstall of ubuntu anyway. Must have been the crash during Ubuntu After Install?

---

### Post by papibe on 2014-12-25
Thanks.

It may be a problem with the packaging system. Please run these commands and post the output:
```
sudo dpkg --configure -a

sudo apt-get install -f

sudo apt-get update
```
Regards.

---

### Post by petermartin2 on 2014-12-25
> **papibe said:**
> Thanks.

It may be a problem with the packaging system. Please run these commands and post the output:
```
sudo dpkg --configure -a

sudo apt-get install -f

sudo apt-get update
```
Regards.

```

sudo dpkg --configure -a
this one nothing

p@p:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmono-accessibility4.0-cil libmono-data-tds4.0-cil
  libmono-system-data4.0-cil libmono-system-enterpriseservices4.0-cil
  libmono-system-runtime-serialization-formatters-soap4.0-cil
  libmono-system-transactions4.0-cil libmono-system-windows-forms4.0-cil
  libmono-webbrowser4.0-cil xsel
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

p@p:~$ sudo apt-get update
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://archive.canonical.com](http://archive.canonical.com) utopic InRelease                              
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic InRelease                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security InRelease                       
Get:1 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources [549 B]               
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-updates InRelease                      
Get:2 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages [604 B]        
Hit [http://archive.canonical.com](http://archive.canonical.com) utopic Release.gpg                            
Ign [http://download.videolan.org](http://download.videolan.org)  InRelease                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security Release.gpg                     
Get:3 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages [804 B]         
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-backports InRelease                    
Get:4 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1 217 B]                
Hit [http://archive.canonical.com](http://archive.canonical.com) utopic Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security Release                         
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic Release.gpg                            
Hit [http://download.videolan.org](http://download.videolan.org)  Release.gpg                                  
Get:5 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1 203 B]                 
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-updates Release.gpg                    
Hit [http://download.videolan.org](http://download.videolan.org)  Release                                      
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-backports Release.gpg                  
Get:6 [http://download.videolan.org](http://download.videolan.org)  Packages [1 355 B]                         
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic Release                                
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-updates Release                        
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-backports Release                      
Hit [http://archive.canonical.com](http://archive.canonical.com) utopic/partner Sources                        
Hit [http://archive.canonical.com](http://archive.canonical.com) utopic/partner amd64 Packages                 
Hit [http://archive.canonical.com](http://archive.canonical.com) utopic/partner i386 Packages                  
Hit [http://archive.canonical.com](http://archive.canonical.com) utopic/partner Translation-en                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic InRelease                                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main Sources                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic InRelease                                  
Err [http://download.videolan.org](http://download.videolan.org)  Translation-en_US                            
  Bad header line
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main amd64 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic InRelease                                  
Err [http://download.videolan.org](http://download.videolan.org)  Translation-en                               
  Bad header line
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main i386 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted Sources              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe Sources                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/multiverse Sources              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main amd64 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release.gpg                                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted amd64 Packages       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe amd64 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/multiverse amd64 Packages       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main i386 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted i386 Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe i386 Packages          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/multiverse i386 Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main Translation-en             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/multiverse Translation-en       
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-backports/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted Translation-en       
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-backports/multiverse Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe Translation-en         
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-backports/restricted amd64 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-backports/multiverse amd64 Packages    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-backports/restricted i386 Packages     
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-backports/multiverse i386 Packages     
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-backports/multiverse Translation-en    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-backports/restricted Translation-en    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic/main Sources                           
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic/restricted Sources                     
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic/universe Sources                       
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic/multiverse Sources                     
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic/main amd64 Packages       
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic/restricted amd64 Packages 
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic/universe amd64 Packages   
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic/multiverse amd64 Packages 
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic/main i386 Packages        
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic/restricted i386 Packages  
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic/universe i386 Packages    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic/multiverse i386 Packages               
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic/main Translation-en                    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic/multiverse Translation-en              
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic/restricted Translation-en  
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic/universe Translation-en    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-updates/main Sources                   
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-updates/restricted Sources             
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-updates/universe Sources   
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-updates/multiverse Sources             
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_US               
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-updates/main amd64 Packages            
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-updates/restricted amd64 Packages      
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-updates/universe amd64 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-updates/multiverse amd64 Packages
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en      
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-updates/main i386 Packages 
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-updates/restricted i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-updates/universe i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-updates/multiverse i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main amd64 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-updates/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main i386 Packages               
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-updates/multiverse Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-updates/restricted Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main Translation-en              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-updates/universe Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-backports/main Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-backports/universe Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main amd64 Packages       
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-backports/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main i386 Packages               
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-backports/universe amd64 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-backports/main i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-backports/universe i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main amd64 Packages        
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-backports/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main i386 Packages               
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) utopic-backports/universe Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main Translation-en                        
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main amd64 Packages                        
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main i386 Packages                         
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main Translation-en                        
Fetched 1 957 B in 8s (239 B/s)                                                
W: Failed to fetch [http://download.videolan.org/pub/debian/stable/en_US](http://download.videolan.org/pub/debian/stable/en_US)  Bad header line

W: Failed to fetch [http://download.videolan.org/pub/debian/stable/en](http://download.videolan.org/pub/debian/stable/en)  Bad header line

W: Failed to fetch [http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu/dists/utopic/main/binary-amd64/Packages](http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu/dists/utopic/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu/dists/utopic/main/binary-i386/Packages](http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu/dists/utopic/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by petermartin2 on 2014-12-25
I've been experiencing a lot of crashes which researching has led me to believe is connected with my [COLOR=#000000]1 gb radeon HD7770 card. However I also had a lot of problem with to many partitions so I reinstalled and now I don't know why I'm getting all these system program problem detected's but it might have to do with the video card? Or could it be something with the crashed ubuntu after install installation?[/COLOR]

I just edited apport instead and turned the crashreports off I don't want to do a fourth OS installation within a week or so. I've tried downloading and installing smaller software and everything seems to work fine except compiz that never worked anyway

Would be nice to know how I could reinstall or install xbmc though... important software

---

### Post by papibe on 2014-12-25
Thanks. I see that you're running Utopic.

I don't see the XBMC/Kodi ppa so you may need to do this again:
```
sudo add-apt-repository ppa:team-xbmc/ppa

sudo apt-get update

sudo apt-get install kodi
```
However, there are several sources errors. Could you run this command and paste back the result:
```
find /etc/apt/sources.list.d/  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
Regards.

---

### Post by petermartin2 on 2014-12-25
I followed the three steps again. The funny thing is that no matter how many times I do "sudo apt-get update" it still promts me to do it again to correct problems after the installation:

```
p@p:~$ sudo apt-get install kodi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kodi is already the newest version.
The following packages were automatically installed and are no longer required:
  libmono-accessibility4.0-cil libmono-data-tds4.0-cil
  libmono-system-data4.0-cil libmono-system-enterpriseservices4.0-cil
  libmono-system-runtime-serialization-formatters-soap4.0-cil
  libmono-system-transactions4.0-cil libmono-system-windows-forms4.0-cil
  libmono-webbrowser4.0-cil xsel
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: Duplicate sources.list entry http://repo.steampowered.com/steam/ precise/steam amd64 Packages (/var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_binary-amd64_Packages)
W: Duplicate sources.list entry http://repo.steampowered.com/steam/ precise/steam i386 Packages (/var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

here's the result you asked:
```
p@p:~$ find /etc/apt/sources.list.d/ -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list.d/peterlevi-ubuntu-ppa-utopic.list

     1    deb http://ppa.launchpad.net/peterlevi/ppa/ubuntu utopic main
     2    # deb-src http://ppa.launchpad.net/peterlevi/ppa/ubuntu utopic main

/etc/apt/sources.list.d/libreoffice-ubuntu-ppa-utopic.list

     1    deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu utopic main
     2    # deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu utopic main
     3    # deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu utopic main

/etc/apt/sources.list.d/stebbins-ubuntu-handbrake-snapshots-utopic.list

     1    deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu utopic main
     2    # deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu utopic main
     3    # deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu utopic main

/etc/apt/sources.list.d/steam.list

     1    deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
     2    deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam

/etc/apt/sources.list.d/pmjdebruijn-ubuntu-darktable-release-utopic.list

     1    deb http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu utopic main
     2    # deb-src http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu utopic main

/etc/apt/sources.list.d/thefanclub-ubuntu-ubuntu-after-install-utopic.list

     1    deb http://ppa.launchpad.net/thefanclub/ubuntu-after-install/ubuntu utopic main
     2    # deb-src http://ppa.launchpad.net/thefanclub/ubuntu-after-install/ubuntu utopic main

/etc/apt/sources.list.d/libdvdcss2.list

     1    deb http://download.videolan.org/pub/debian/stable/ /

/etc/apt/sources.list.d/steam-launcher.list

     1    deb http://repo.steampowered.com/steam/ precise steam

/etc/apt/sources.list.d/google-chrome.list

     1    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2    # You may comment out this entry, but any other modifications may be lost.
     3    deb http://dl.google.com/linux/chrome/deb/ stable main

/etc/apt/sources.list.d/google-chrome-stable.list

     1    deb http://dl.google.com/linux/chrome/deb/ stable main

/etc/apt/sources.list.d/freyja-dev-ubuntu-unity-tweak-tool-daily-utopic.list

     1    deb http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu utopic main
     2    # deb-src http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu utopic main
     3    # deb-src http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu utopic main

/etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-utopic.list

     1    deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu utopic main
     2    # deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu utopic main
     3    # deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu utopic main
     4    # deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu utopic main
     5    # deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu utopic main

/etc/apt/sources.list.d/thefanclub-ubuntu-grive-tools-utopic.list

     1    deb http://ppa.launchpad.net/thefanclub/grive-tools/ubuntu utopic main
     2    # deb-src http://ppa.launchpad.net/thefanclub/grive-tools/ubuntu utopic main
     3    # deb-src http://ppa.launchpad.net/thefanclub/grive-tools/ubuntu utopic main

/etc/apt/sources.list.d/otto-kesselgulasch-ubuntu-gimp-utopic.list

     1    deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu utopic main
     2    # deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu utopic main
     3    # deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu utopic main


```

---

### Post by papibe on 2014-12-25
So there is a problem with the sources files.

I made a mistake, this is the command I want to run:
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
Regards.

---

### Post by petermartin2 on 2014-12-25
> **papibe said:**
> So there is a problem with the sources files.

I made a mistake, this is the command I want to run:
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
Regards.

```
p@p:~$ find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list.d/peterlevi-ubuntu-ppa-utopic.list

     1    deb [http://ppa.launchpad.net/peterlevi/ppa/ubuntu](http://ppa.launchpad.net/peterlevi/ppa/ubuntu) utopic main
     2    # deb-src [http://ppa.launchpad.net/peterlevi/ppa/ubuntu](http://ppa.launchpad.net/peterlevi/ppa/ubuntu) utopic main

/etc/apt/sources.list.d/libreoffice-ubuntu-ppa-utopic.list

     1    deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) utopic main
     2    # deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) utopic main
     3    # deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) utopic main

/etc/apt/sources.list.d/stebbins-ubuntu-handbrake-snapshots-utopic.list

     1    deb [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu) utopic main
     2    # deb-src [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu) utopic main
     3    # deb-src [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu) utopic main

/etc/apt/sources.list.d/steam.list

     1    deb [arch=amd64,i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam
     2    deb-src [arch=amd64,i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam

/etc/apt/sources.list.d/pmjdebruijn-ubuntu-darktable-release-utopic.list

     1    deb [http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu](http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu) utopic main
     2    # deb-src [http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu](http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu) utopic main

/etc/apt/sources.list.d/thefanclub-ubuntu-ubuntu-after-install-utopic.list

     1    deb [http://ppa.launchpad.net/thefanclub/ubuntu-after-install/ubuntu](http://ppa.launchpad.net/thefanclub/ubuntu-after-install/ubuntu) utopic main
     2    # deb-src [http://ppa.launchpad.net/thefanclub/ubuntu-after-install/ubuntu](http://ppa.launchpad.net/thefanclub/ubuntu-after-install/ubuntu) utopic main

/etc/apt/sources.list.d/libdvdcss2.list

     1    deb [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /

/etc/apt/sources.list.d/steam-launcher.list

     1    deb [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam

/etc/apt/sources.list.d/google-chrome.list

     1    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2    # You may comment out this entry, but any other modifications may be lost.
     3    deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

/etc/apt/sources.list.d/google-chrome-stable.list

     1    deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

/etc/apt/sources.list.d/freyja-dev-ubuntu-unity-tweak-tool-daily-utopic.list

     1    deb [http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu](http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu) utopic main
     2    # deb-src [http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu](http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu) utopic main
     3    # deb-src [http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu](http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu) utopic main

/etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-utopic.list

     1    deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) utopic main
     2    # deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) utopic main
     3    # deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) utopic main
     4    # deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) utopic main
     5    # deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) utopic main

/etc/apt/sources.list.d/thefanclub-ubuntu-grive-tools-utopic.list

     1    deb [http://ppa.launchpad.net/thefanclub/grive-tools/ubuntu](http://ppa.launchpad.net/thefanclub/grive-tools/ubuntu) utopic main
     2    # deb-src [http://ppa.launchpad.net/thefanclub/grive-tools/ubuntu](http://ppa.launchpad.net/thefanclub/grive-tools/ubuntu) utopic main
     3    # deb-src [http://ppa.launchpad.net/thefanclub/grive-tools/ubuntu](http://ppa.launchpad.net/thefanclub/grive-tools/ubuntu) utopic main

/etc/apt/sources.list.d/otto-kesselgulasch-ubuntu-gimp-utopic.list

     1    deb [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) utopic main
     2    # deb-src [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) utopic main
     3    # deb-src [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) utopic main

/etc/apt/sources.list

     1    # deb cdrom:[Ubuntu 14.10 _Utopic Unicorn_ - Release amd64 (20141022.1)]/ utopic main restricted
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) utopic main restricted
     6    deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) utopic main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) utopic-updates main restricted
    11    deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) utopic-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) utopic universe
    17    deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) utopic universe
    18    deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) utopic-updates universe
    19    deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) utopic-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) utopic multiverse
    27    deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) utopic multiverse
    28    deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) utopic-updates multiverse
    29    deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) utopic-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) utopic-backports main restricted universe multiverse
    37    deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) utopic-backports main restricted universe multiverse
    38    
    39    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security main restricted
    40    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security main restricted
    41    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security universe
    42    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security universe
    43    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security multiverse
    44    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) utopic partner
    51    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) utopic partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) utopic main
    56    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) utopic main
```

---

### Post by papibe on 2014-12-25
Thanks.

There are 2 google repos. You need just one:
```
/etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/google-chrome-stable.list

```
There are 2 steam repos. You need just one:
```
/etc/apt/sources.list.d/steam-launcher.list
/etc/apt/sources.list.d/steam.list
```
To remove, or disable one of the duplicated sources, you can
[LIST][*]use the command "apt-add-repository -r", or
[*]open 'Software & Upadtes', go to the tab 'Other Software' and uncheck the repos there.[/LIST]
After that update your sources and post back the result if you see any hit of error:
```
sudo apt-get update
```
If you see no error, try to continue the installation of kodi.

Regards.

---

### Post by petermartin2 on 2014-12-25
I also tried running these commands 
```
sudo apt-get purge xbmc xbmc-standalone
killall -9 xbmc.bin 
rm ~/.xbmc{-backup} 

```
to try and remove everything but still get this after update:
```
Some index files failed to download. They have been ignored, or old ones used instead.
```

and this after install
```
W: You may want to run apt-get update to correct these problems
```

---

### Post by petermartin2 on 2014-12-25
> **papibe said:**
> Thanks.

There are 2 google repos. You need just one:
```
/etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/google-chrome-stable.list

```
There are 2 steam repos. You need just one:
```
/etc/apt/sources.list.d/steam-launcher.list
/etc/apt/sources.list.d/steam.list
```
To remove, or disable one of the duplicated sources, you can
[LIST]
[*]use the command "apt-add-repository -r", or
[*]open 'Software & Upadtes', go to the tab 'Other Software' and uncheck the repos there.
[/LIST]
After that update your sources and post back the result if you see any hit of error:
```
sudo apt-get update
```
If you see no error, try to continue the installation of kodi.

Regards.

Ok, I wrote as you said:
```
p@p:~$ sudo apt-add-repository -r google-chrome.list
p@p:~$ sudo apt-add-repository -r steam-launcher.list
p@p:~$ 
```

and after 
```
sudo apt-get install python-software-properties pkg-config
sudo apt-get install software-properties-common
sudo apt-get update
sudo apt-get install kodi





```
And now it's working! Thanks a bunch

---

### Post by mc4man on 2014-12-25
That thefanclub deal should update their 'thing' as it's adding 2 ppa's it shouldn't (videolan & freyja-dev) & trying to install skype which I don't see as avail. anymore
(- for steam it likely could just install the repo installer, steam-launcher

---

### Post by craig25 on 2014-12-27
> **petermartin2 said:**
> I've been experiencing a lot of crashes which researching has led me to believe is connected with my [COLOR=#000000]1 gb radeon HD7770 card. However I also had a lot of problem with to many partitions so I reinstalled and now I don't know why I'm getting all these system program problem detected's but it might have to do with the video card? Or could it be something with the crashed ubuntu after install installation?[/COLOR]

I just edited apport instead and turned the crashreports off I don't want to do a fourth OS installation within a week or so. I've tried downloading and installing smaller software and everything seems to work fine except compiz that never worked anyway

Would be nice to know how I could reinstall or install xbmc though... important software

Very helpful post. Much appreciated.

---

### Post by redhotdaddy on 2015-01-08
I was considering installing mandriva and running kodi. Would this same process work with mandriva? Or is ubuntu better suited for running kodi?

---

