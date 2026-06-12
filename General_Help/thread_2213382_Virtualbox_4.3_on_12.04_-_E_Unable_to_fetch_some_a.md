---
title: "Virtualbox 4.3 on 12.04 - E: Unable to fetch some archives"
date: 2014-03-26
forum: General Help
---

### Post by samwillc on 2014-03-26
Hi everyone,

Not sure what the problem is here as I've installed virtualbox before without hitch. Using this guide:

[http://linuxg.net/how-to-install-virtualbox-4-3-on-ubuntu-13-04-12-10-12-04-linux-mint-15-14-13-pear-os-8-pear-os-7-and-elementary-os-0-2-via-the-official-virtualbox-repository/](http://linuxg.net/how-to-install-virtualbox-4-3-on-ubuntu-13-04-12-10-12-04-linux-mint-15-14-13-pear-os-8-pear-os-7-and-elementary-os-0-2-via-the-official-virtualbox-repository/)

Everything runs smooth until the actual install:

```

sam@sam-pc:~$ wget -q -O - http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc | sudo apt-key add -
[sudo] password for sam: 
OK
sam@sam-pc:~$ sudo sh -c 'echo "deb http://download.virtualbox.org/virtualbox/debian precise non-free contrib" >> /etc/apt/sources.list.d/virtualbox.org.list'
sam@sam-pc:~$ sudo apt-get update
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Hit http://ppa.launchpad.net precise Release.gpg                                      
Hit http://ppa.launchpad.net precise Release.gpg                                      
Hit http://ppa.launchpad.net precise Release.gpg                                      
Hit http://ppa.launchpad.net precise Release.gpg                                      
Hit http://ppa.launchpad.net precise Release.gpg                                      
Get:2 http://ppa.launchpad.net precise Release.gpg [316 B]                            
Hit http://ppa.launchpad.net precise Release.gpg                                      
Hit http://ppa.launchpad.net precise Release.gpg                                      
Hit http://gb.archive.ubuntu.com precise Release.gpg                                  
Get:3 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]                
Get:4 http://gb.archive.ubuntu.com precise-backports Release.gpg [198 B]              
Get:5 http://security.ubuntu.com precise-security Release [49.6 kB]                   
Hit http://ppa.launchpad.net precise Release                                          
Hit http://ppa.launchpad.net precise Release                                          
Hit http://ppa.launchpad.net precise Release                                          
Hit http://ppa.launchpad.net precise Release                                          
Hit http://gb.archive.ubuntu.com precise Release                                      
Hit http://ppa.launchpad.net precise Release                                          
Get:6 http://ppa.launchpad.net precise Release [11.9 kB]                              
Get:7 http://gb.archive.ubuntu.com precise-updates Release [49.6 kB]                  
Hit http://ppa.launchpad.net precise Release                                          
Hit http://ppa.launchpad.net precise Release                                          
Hit http://ppa.launchpad.net precise/main Sources                                     
Hit http://ppa.launchpad.net precise/main amd64 Packages                              
Hit http://ppa.launchpad.net precise/main i386 Packages                               
Ign http://ppa.launchpad.net precise/main TranslationIndex                            
Hit http://ppa.launchpad.net precise/main Sources                                     
Get:8 http://security.ubuntu.com precise-security/main Sources [101 kB]               
Hit http://ppa.launchpad.net precise/main amd64 Packages                              
Hit http://ppa.launchpad.net precise/main i386 Packages                               
Ign http://ppa.launchpad.net precise/main TranslationIndex                            
Hit http://ppa.launchpad.net precise/main Sources                                     
Hit http://ppa.launchpad.net precise/main amd64 Packages                              
Hit http://ppa.launchpad.net precise/main i386 Packages                               
Ign http://ppa.launchpad.net precise/main TranslationIndex                            
Hit http://ppa.launchpad.net precise/main Sources                                     
Get:9 http://gb.archive.ubuntu.com precise-backports Release [49.6 kB]                
Hit http://ppa.launchpad.net precise/main amd64 Packages                              
Hit http://ppa.launchpad.net precise/main i386 Packages                               
Ign http://ppa.launchpad.net precise/main TranslationIndex                            
Hit http://ppa.launchpad.net precise/main Sources                                     
Hit http://ppa.launchpad.net precise/main amd64 Packages                              
Hit http://ppa.launchpad.net precise/main i386 Packages                               
Ign http://ppa.launchpad.net precise/main TranslationIndex                            
Get:10 http://ppa.launchpad.net precise/main Sources [13.3 kB]                        
Get:11 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]       
Get:12 http://security.ubuntu.com precise-security/universe Sources [30.9 kB]         
Get:13 http://security.ubuntu.com precise-security/multiverse Sources [1,789 B]       
Get:14 http://security.ubuntu.com precise-security/main amd64 Packages [375 kB]       
Hit http://gb.archive.ubuntu.com precise/main Sources                                 
Hit http://gb.archive.ubuntu.com precise/restricted Sources                           
Hit http://gb.archive.ubuntu.com precise/universe Sources                             
Hit http://gb.archive.ubuntu.com precise/multiverse Sources                           
Hit http://gb.archive.ubuntu.com precise/main amd64 Packages                          
Hit http://gb.archive.ubuntu.com precise/restricted amd64 Packages                    
Hit http://gb.archive.ubuntu.com precise/universe amd64 Packages                      
Hit http://gb.archive.ubuntu.com precise/multiverse amd64 Packages                    
Hit http://gb.archive.ubuntu.com precise/main i386 Packages                           
Get:15 http://ppa.launchpad.net precise/main amd64 Packages [13.6 kB]                 
Get:16 http://ppa.launchpad.net precise/main i386 Packages [13.6 kB]                  
Hit http://gb.archive.ubuntu.com precise/restricted i386 Packages                     
Get:17 http://download.virtualbox.org precise Release.gpg [198 B]                     
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages                       
Hit http://gb.archive.ubuntu.com precise/multiverse i386 Packages                     
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex                        
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex                  
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                            
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main amd64 Packages                        
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                                     
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex                    
Get:18 http://gb.archive.ubuntu.com precise-updates/main Sources [453 kB]             
Hit http://ppa.launchpad.net precise/main amd64 Packages                              
Hit http://ppa.launchpad.net precise/main i386 Packages                               
Ign http://ppa.launchpad.net precise/main TranslationIndex                            
Get:19 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:20 http://security.ubuntu.com precise-security/universe amd64 Packages [91.7 kB]  
Get:21 http://download.virtualbox.org precise Release [5,393 B]                       
Get:22 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,446 B]
Get:23 http://security.ubuntu.com precise-security/main i386 Packages [401 kB]        
Get:24 http://gb.archive.ubuntu.com precise-updates/restricted Sources [8,028 B]      
Get:25 http://gb.archive.ubuntu.com precise-updates/universe Sources [105 kB]         
Get:26 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [8,900 B]      
Get:27 http://gb.archive.ubuntu.com precise-updates/main amd64 Packages [760 kB]      
Get:28 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B] 
Get:29 http://security.ubuntu.com precise-security/universe i386 Packages [96.5 kB]   
Get:30 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,646 B] 
Hit http://security.ubuntu.com precise-security/main TranslationIndex                 
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex           
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex           
Hit http://security.ubuntu.com precise-security/universe TranslationIndex             
Hit http://security.ubuntu.com precise-security/main Translation-en                   
Hit http://security.ubuntu.com precise-security/multiverse Translation-en             
Hit http://security.ubuntu.com precise-security/restricted Translation-en             
Hit http://security.ubuntu.com precise-security/universe Translation-en               
Get:31 http://gb.archive.ubuntu.com precise-updates/restricted amd64 Packages [12.2 kB]
Get:32 http://gb.archive.ubuntu.com precise-updates/universe amd64 Packages [237 kB]  
Ign http://ppa.launchpad.net precise/main Translation-en_GB                           
Ign http://ppa.launchpad.net precise/main Translation-en                              
Ign http://ppa.launchpad.net precise/main Translation-en_GB                           
Ign http://ppa.launchpad.net precise/main Translation-en                              
Ign http://ppa.launchpad.net precise/main Translation-en_GB                      
Get:33 http://download.virtualbox.org precise/non-free amd64 Packages [14 B]     
Ign http://ppa.launchpad.net precise/main Translation-en                         
Ign http://ppa.launchpad.net precise/main Translation-en_GB                        
Ign http://ppa.launchpad.net precise/main Translation-en                           
Get:34 http://gb.archive.ubuntu.com precise-updates/multiverse amd64 Packages [15.3 kB]
Get:35 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [783 kB]       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                           
Ign http://ppa.launchpad.net precise/main Translation-en                              
Ign http://ppa.launchpad.net precise/main Translation-en_GB                           
Ign http://ppa.launchpad.net precise/main Translation-en                              
Ign http://ppa.launchpad.net precise/main Translation-en_GB                           
Ign http://ppa.launchpad.net precise/main Translation-en                              
Ign http://ppa.launchpad.net precise/main Translation-en_GB                           
Ign http://ppa.launchpad.net precise/main Translation-en                              
Get:36 http://download.virtualbox.org precise/contrib amd64 Packages [1,557 B]   
Get:37 http://download.virtualbox.org precise/non-free i386 Packages [14 B]           
Get:38 http://download.virtualbox.org precise/contrib i386 Packages [1,533 B]         
Get:39 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [12.2 kB]
Get:40 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [243 kB]   
Get:41 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Hit http://gb.archive.ubuntu.com precise-updates/main TranslationIndex                
Hit http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex          
Hit http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex          
Hit http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex            
Get:42 http://gb.archive.ubuntu.com precise-backports/main Sources [4,850 B]          
Get:43 http://gb.archive.ubuntu.com precise-backports/restricted Sources [14 B]     
Get:44 http://gb.archive.ubuntu.com precise-backports/universe Sources [36.4 kB]    
Get:45 http://gb.archive.ubuntu.com precise-backports/multiverse Sources [5,311 B]    
Get:46 http://gb.archive.ubuntu.com precise-backports/main amd64 Packages [6,183 B]   
Get:47 http://gb.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:48 http://gb.archive.ubuntu.com precise-backports/universe amd64 Packages [38.3 kB]
Get:49 http://gb.archive.ubuntu.com precise-backports/multiverse amd64 Packages [5,206 B]
Get:50 http://gb.archive.ubuntu.com precise-backports/main i386 Packages [6,182 B]    
Get:51 http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B] 
Get:52 http://gb.archive.ubuntu.com precise-backports/universe i386 Packages [38.0 kB]
Get:53 http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages [5,178 B]
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex              
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex      
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex      
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex        
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB                     
Hit http://gb.archive.ubuntu.com precise/main Translation-en                        
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB               
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB                 
Hit http://gb.archive.ubuntu.com precise/universe Translation-en                    
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB       
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en          
Ign http://download.virtualbox.org precise/contrib TranslationIndex                 
Ign http://download.virtualbox.org precise/non-free TranslationIndex    
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en  
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en
Ign http://download.virtualbox.org precise/contrib Translation-en_GB    
Ign http://download.virtualbox.org precise/contrib Translation-en
Ign http://download.virtualbox.org precise/non-free Translation-en_GB
Ign http://download.virtualbox.org precise/non-free Translation-en
Fetched 4,123 kB in 2s (1,424 kB/s)
Reading package lists... Done
sam@sam-pc:~$ sudo apt-get install virtualbox-4.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libqt4-opengl libsdl-ttf2.0-0
The following NEW packages will be installed:
  libqt4-opengl libsdl-ttf2.0-0 virtualbox-4.3
0 upgraded, 3 newly installed, 0 to remove and 8 not upgraded.
Need to get 69.7 MB of archives.
After this operation, 156 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ precise/universe libsdl-ttf2.0-0 amd64 2.0.9-1.1ubuntu1 [14.1 kB]
Get:2 http://ppa.launchpad.net/elementary-os/os-patches/ubuntu/ precise/main libqt4-opengl amd64 4:4.8.1-0ubuntu4.6+elementary5~ubuntu0.2.1 [351 kB]
Err http://download.virtualbox.org/virtualbox/debian/ precise/contrib virtualbox-4.3 amd64 4.3.10-92957~Ubuntu~precise
  404  Not found
Fetched 365 kB in 0s (1,090 kB/s)                                                     
Failed to fetch http://download.virtualbox.org/virtualbox/debian/pool/contrib/v/virtualbox-4.3/virtualbox-4.3_4.3.10-92957~Ubuntu~precise_amd64.deb  404  Not found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Seems this is missing now:

[http://download.virtualbox.org/virtualbox/debian/pool/contrib/v/virtualbox-4.3/virtualbox-4.3_4.3.10-92957~Ubuntu~precise_amd64.deb](http://download.virtualbox.org/virtualbox/debian/pool/contrib/v/virtualbox-4.3/virtualbox-4.3_4.3.10-92957~Ubuntu~precise_amd64.deb)

I thought this would be easier than downloading from the virtualbox site as this sets everything up ready to go. Not working though. Any suggestions?

Sam.

---

### Post by kissa2001 on 2014-03-26
I am having the same 404 error here. The file is missing from the repository.

If you are in a hurry I suggest downloading the correct DEB file directly from Oracle:
[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html)

After downloading install with:
```

sudo dpkg -i downloaded_package.deb   # Install downloaded .deb
sudo apt-get -f install               # Install and configure possible dependencies

```

---

### Post by ajgreeny on 2014-03-26
I upgraded my 4.3.8 version to 4.3.10 and the server for that VB repository was incredibly slow the first time I tried to update the package, and eventually stopped completely.  A few hours later it all worked well, so you may have hit the same problem as I had.

Try again later at a time that the server is less likely to be busy, though what time of day for you that might be I have no idea.  For me it was late evening (10 minutes before 10pm GMT.)
From my dpkg logs:-
2014-03-25 21:50:37 upgrade virtualbox-4.3 4.3.8-92456~Ubuntu~precise 4.3.10-92957~Ubuntu~precise

---

### Post by samwillc on 2014-03-26
Is it busy or is the file not there? I'm not in a hurry so will try again later. Failing that I will just download the deb package. I've got a spare drive in the pc for mucking about on but virtualbox is just so quick and easy to test out other distros! :)

---

### Post by JKyleOKC on 2014-03-26
Before you upgrade 4.3.8 to 4.3.10, be sure that all your VMs are powered off. I failed to do that and spent a scary hour recovering from the result (details in the Virtualization forum here).

---

### Post by ajgreeny on 2014-03-27
Note that there was an update yesterday (or the day before) taking VB from 4.3.8 to 4.3.10 and then another update of the 4.3.10 version today due to some problem, so maybe the first 4.3.10 version was pulled for a time whilst sorting out the second update.

---

### Post by JKyleOKC on 2014-03-27
See my "Heads Up" thread about 4.3.10 for the reason and details...

---

### Post by samwillc on 2014-03-28
> **JKyleOKC said:**
> See my "Heads Up" thread about 4.3.10 for the reason and details...

Could you post a link to the thread, I can't find it. I just wanted to install virtualbox from scratch, not an upgrade. Thanks.

---

### Post by jeffshearman on 2014-03-28
I had issues with the DEB file from ubuntu.  Flat didn't work well with USB devices.  Went to the 
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) site and without a hitch, worked just fine after a compile kernel modules.

I dl'd the 12.04.3 32 bit image yesterday and installed it to a VM with fixed disk size of 20gb.  My needs are small, and it works great!  Borrowed a hdhomerun for the tuner source and poof, less than an hour was on air (so to speak)  Great job team MythBuntu.

---

### Post by JKyleOKC on 2014-03-28
It's at [http://ubuntuforums.org/showthread.php?t=2213415](http://ubuntuforums.org/showthread.php?t=2213415) but the copy in the Oracle download area is now correct. The critical point is having a build number of r93012.

---

