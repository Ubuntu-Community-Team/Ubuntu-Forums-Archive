---
title: "Packages System broken, software updater crashes, how to fix?"
date: 2013-11-08
forum: General Help
---

### Post by boletusatanas on 2013-11-08
Hey Guys,
I am experiencing very annoying problem with the software updater and packages manager. It says I have problem with thirty party sources. Idisabled them but it doest work.
I have the updated version of Ubuntu,  the 13.10 and due to this problem I cannot use the software updater, nor I can install or unistall software.
I pasted some outputs from my shell. they might be useful.

Thanks in advance for the help.




sudo apt-get update
```

boletusatanas@SpartanDell:~$ sudo apt-get update 
[sudo] password for boletusatanas: 
Ign http://mirror.optimate-server.de saucy InRelease
Ign http://mirror.optimate-server.de saucy-security InRelease                  
Ign http://mirror.optimate-server.de saucy-updates InRelease                   
Ign http://dl.google.com stable InRelease                                      
Hit http://repository.spotify.com stable InRelease                             
Hit http://mirror.optimate-server.de saucy Release.gpg                         
Ign http://archive.canonical.com saucy InRelease                               
Hit http://dl.google.com stable Release.gpg                                    
Hit http://mirror.optimate-server.de saucy-security Release.gpg                
Hit http://mirror.optimate-server.de saucy-updates Release.gpg                 
Hit http://dl.google.com stable Release                                        
Hit http://archive.canonical.com saucy Release.gpg                             
Hit http://mirror.optimate-server.de saucy Release                             
Hit http://repository.spotify.com stable/non-free amd64 Packages               
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://mirror.optimate-server.de saucy-security Release                    
Hit http://archive.canonical.com saucy Release                                 
Hit http://mirror.optimate-server.de saucy-updates Release                     
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://repository.spotify.com stable/non-free i386 Packages                
Hit http://mirror.optimate-server.de saucy/main Sources                        
Hit http://mirror.optimate-server.de saucy/restricted Sources                  
Hit http://archive.canonical.com saucy/partner Sources                         
Hit http://mirror.optimate-server.de saucy/universe Sources                    
Hit http://mirror.optimate-server.de saucy/multiverse Sources                  
Hit http://mirror.optimate-server.de saucy/main amd64 Packages                 
Hit http://archive.canonical.com saucy/partner amd64 Packages                  
Hit http://mirror.optimate-server.de saucy/restricted amd64 Packages           
Hit http://mirror.optimate-server.de saucy/universe amd64 Packages             
Hit http://archive.canonical.com saucy/partner i386 Packages                   
Hit http://mirror.optimate-server.de saucy/multiverse amd64 Packages           
Hit http://mirror.optimate-server.de saucy/main i386 Packages                  
Hit http://mirror.optimate-server.de saucy/restricted i386 Packages            
Hit http://mirror.optimate-server.de saucy/universe i386 Packages              
Ign http://ppa.launchpad.net saucy InRelease                                   
Hit http://mirror.optimate-server.de saucy/multiverse i386 Packages            
Ign http://dl.google.com stable/main Translation-en_GB                         
Hit http://mirror.optimate-server.de saucy/main Translation-en_GB              
Ign http://dl.google.com stable/main Translation-en                            
Ign http://ppa.launchpad.net saucy InRelease                                   
Hit http://mirror.optimate-server.de saucy/main Translation-en                 
Ign http://linux.dropbox.com precise InRelease                                 
Hit http://mirror.optimate-server.de saucy/multiverse Translation-en_GB        
Ign http://ppa.launchpad.net saucy InRelease                                   
Hit http://mirror.optimate-server.de saucy/multiverse Translation-en           
Ign http://ppa.launchpad.net saucy InRelease                                   
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://mirror.optimate-server.de saucy/restricted Translation-en_GB        
Hit http://mirror.optimate-server.de saucy/restricted Translation-en           
Ign http://ppa.launchpad.net saucy InRelease                                   
Hit http://mirror.optimate-server.de saucy/universe Translation-en_GB          
Hit http://mirror.optimate-server.de saucy/universe Translation-en             
Get:1 http://linux.dropbox.com precise Release.gpg [489 B]                     
Hit http://mirror.optimate-server.de saucy-security/main Sources               
Hit http://mirror.optimate-server.de saucy-security/restricted Sources         
Hit http://mirror.optimate-server.de saucy-security/universe Sources           
Hit http://mirror.optimate-server.de saucy-security/multiverse Sources         
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Get:2 http://linux.dropbox.com precise Release [2.603 B]                       
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Ign http://repository.spotify.com stable/non-free Translation-en_GB            
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Ign http://repository.spotify.com stable/non-free Translation-en               
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Ign http://repository.spotify.com stable/non-free Translation-en_US            
Ign http://archive.canonical.com saucy/partner Translation-en_GB               
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Hit http://mirror.optimate-server.de saucy-security/main amd64 Packages        
Hit http://mirror.optimate-server.de saucy-security/restricted amd64 Packages
Hit http://mirror.optimate-server.de saucy-security/universe amd64 Packages    
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://mirror.optimate-server.de saucy-security/multiverse amd64 Packages  
Hit http://mirror.optimate-server.de saucy-security/main i386 Packages         
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://mirror.optimate-server.de saucy-security/restricted i386 Packages   
Hit http://mirror.optimate-server.de saucy-security/universe i386 Packages     
Get:3 http://linux.dropbox.com precise/main amd64 Packages [1.148 B]           
Hit http://ppa.launchpad.net saucy Release                                     
Ign http://archive.canonical.com saucy/partner Translation-en                  
Hit http://mirror.optimate-server.de saucy-security/multiverse i386 Packages   
Ign http://archive.canonical.com saucy/partner Translation-en_US               
Hit http://ppa.launchpad.net saucy Release                           
Hit http://mirror.optimate-server.de saucy-security/main Translation-en        
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Hit http://ppa.launchpad.net saucy/main i386 Packages                
Get:4 http://linux.dropbox.com precise/main i386 Packages [1.148 B]
Hit http://mirror.optimate-server.de saucy-security/multiverse Translation-en
Hit http://ppa.launchpad.net saucy/main amd64 Packages               
Hit http://ppa.launchpad.net saucy/main i386 Packages                
Hit http://mirror.optimate-server.de saucy-security/restricted Translation-en
Hit http://mirror.optimate-server.de saucy-security/universe Translation-en
Hit http://mirror.optimate-server.de saucy-updates/main amd64 Packages
Hit http://ppa.launchpad.net saucy/main amd64 Packages
Hit http://mirror.optimate-server.de saucy-updates/restricted amd64 Packages
Hit http://mirror.optimate-server.de saucy-updates/multiverse amd64 Packages
Hit http://ppa.launchpad.net saucy/main i386 Packages                
Hit http://mirror.optimate-server.de saucy-updates/universe amd64 Packages
Hit http://mirror.optimate-server.de saucy-updates/main i386 Packages
Hit http://mirror.optimate-server.de saucy-updates/restricted i386 Packages
Hit http://mirror.optimate-server.de saucy-updates/multiverse i386 Packages
Hit http://mirror.optimate-server.de saucy-updates/universe i386 Packages
Hit http://mirror.optimate-server.de saucy-updates/main Translation-en
Hit http://mirror.optimate-server.de saucy-updates/multiverse Translation-en
Hit http://mirror.optimate-server.de saucy-updates/restricted Translation-en
Hit http://mirror.optimate-server.de saucy-updates/universe Translation-en
Hit http://ppa.launchpad.net saucy/main amd64 Packages
Hit http://ppa.launchpad.net saucy/main i386 Packages                
Hit http://ppa.launchpad.net saucy/main amd64 Packages               
Hit http://ppa.launchpad.net saucy/main i386 Packages                
Ign http://mirror.optimate-server.de saucy/main Translation-en_US    
Ign http://linux.dropbox.com precise/main Translation-en_GB          
Ign http://mirror.optimate-server.de saucy/multiverse Translation-en_US
Ign http://linux.dropbox.com precise/main Translation-en
Ign http://mirror.optimate-server.de saucy/restricted Translation-en_US
Ign http://mirror.optimate-server.de saucy/universe Translation-en_US
Ign http://mirror.optimate-server.de saucy-security/main Translation-en_GB
Ign http://mirror.optimate-server.de saucy-security/main Translation-en_US
Ign http://mirror.optimate-server.de saucy-security/multiverse Translation-en_GB
Ign http://mirror.optimate-server.de saucy-security/multiverse Translation-en_US
Ign http://mirror.optimate-server.de saucy-security/restricted Translation-en_GB
Ign http://mirror.optimate-server.de saucy-security/restricted Translation-en_US
Ign http://mirror.optimate-server.de saucy-security/universe Translation-en_GB
Ign http://mirror.optimate-server.de saucy-security/universe Translation-en_US
Ign http://mirror.optimate-server.de saucy-updates/main Translation-en_GB
Ign http://mirror.optimate-server.de saucy-updates/main Translation-en_US
Ign http://mirror.optimate-server.de saucy-updates/multiverse Translation-en_GB
Ign http://mirror.optimate-server.de saucy-updates/multiverse Translation-en_US
Ign http://mirror.optimate-server.de saucy-updates/restricted Translation-en_GB
Ign http://linux.dropbox.com precise/main Translation-en_US           
Ign http://mirror.optimate-server.de saucy-updates/restricted Translation-en_US
Ign http://mirror.optimate-server.de saucy-updates/universe Translation-en_GB
Ign http://mirror.optimate-server.de saucy-updates/universe Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en_GB
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en_GB
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en_GB
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en_GB
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en_GB
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Fetched 5.388 B in 4s (1.129 B/s)
Reading package lists... Done

```



sudo apt-get upgrade
```

boletusatanas@SpartanDell:~$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 gir1.2-rb-3.0 : Depends: librhythmbox-core8 (>= 3.0.1) but it is not installed
 rhythmbox : Depends: librhythmbox-core8 (= 3.0.1-1ubuntu2~ppa0) but it is not installed
 rhythmbox-plugin-cdrecorder : Depends: librhythmbox-core8 (>= 3.0) but it is not installed
 rhythmbox-plugins : Depends: librhythmbox-core8 (= 3.0.1-1ubuntu2~ppa0) but it is not installed
E: Unmet dependencies. Try using -f.

```



sudo apt-get -f install
```

boletusatanas@SpartanDell:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  gir1.2-zeitgeist-2.0
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  librhythmbox-core8
The following NEW packages will be installed
  librhythmbox-core8
0 upgraded, 1 newly installed, 0 to remove and 38 not upgraded.
7 not fully installed or removed.
Need to get 0 B/819 kB of archives.
After this operation, 1.776 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 185000 files and directories currently installed.)
Unpacking librhythmbox-core8 (from .../librhythmbox-core8_3.0.1-1ubuntu2~ppa0_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/librhythmbox-core8_3.0.1-1ubuntu2~ppa0_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/librhythmbox-core.so.8.0.0', which is also in package librhythmbox-core7 3.0.1-0~13.10~ppa1
No apport report written because MaxReports has already been reached
                                                                     dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/librhythmbox-core8_3.0.1-1ubuntu2~ppa0_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```



ls /etc/apt/sources.list.d
```

boletusatanas@SpartanDell:~$ ls /etc/apt/sources.list.d
atareao-atareao-saucy.list       jacob-media-saucy.list.save
atareao-atareao-saucy.list.save  peterlevi-ppa-saucy.list
dropbox.list                     peterlevi-ppa-saucy.list.save
dropbox.list.save                videolan-stable-daily-saucy.list
google-chrome.list               videolan-stable-daily-saucy.list.save
google-chrome.list.save          webupd8team-java-saucy.list
jacob-media-saucy.list           webupd8team-java-saucy.list.save

```

---

### Post by ian-weisser on 2013-11-08
Looks like a Rhythmbox 8 PPA broke your system.
You should probably tell the PPA maintainer that their software broke your system.
PPAs are supported by the maintainer, not by the community forums.

Here are a couple threads from earlier this week on how to fix it:
[http://ubuntuforums.org/showthread.php?t=2184822](http://ubuntuforums.org/showthread.php?t=2184822)
[http://ubuntuforums.org/showthread.php?t=2185025](http://ubuntuforums.org/showthread.php?t=2185025)
[http://ubuntuforums.org/showthread.php?t=2133247](http://ubuntuforums.org/showthread.php?t=2133247)

---

### Post by boletusatanas on 2013-11-08
Thank you very much!
I solved a lot of problems!

---

