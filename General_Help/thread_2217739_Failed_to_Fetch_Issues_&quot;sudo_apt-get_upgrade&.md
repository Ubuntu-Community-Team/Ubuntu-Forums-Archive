---
title: "Failed to Fetch Issues &quot;sudo apt-get upgrade&quot;"
date: 2014-04-18
forum: General Help
---

### Post by Petro Dawg on 2014-04-18
Using Ubuntu14.04 (since beta testing)

When I run...

```
sudo apt-get upgrade
```

I get the following errors...

```
W: Failed to fetch http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

I figured ppa paths may have changed during beta to final release (or I did something unintentionally while installing programs at some point), but I'm not sure what exactly is going on.  Can I just delete these these paths, or do I need to correct the paths, or something else entirely?  I'll also need a little help in figuring out how to delete the paths if deleting is the proper course of action. 

The full output is given below just in case...

```

Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://extras.ubuntu.com trusty InRelease                       
Ign http://ppa.launchpad.net trusty InRelease                        
Ign http://us.archive.ubuntu.com trusty-updates InRelease            
Hit http://extras.ubuntu.com trusty Release.gpg                                
Ign http://us.archive.ubuntu.com trusty-backports InRelease                    
Ign http://ppa.launchpad.net trusty InRelease                        
Hit http://archive.getdeb.net trusty-getdeb InRelease                
Ign http://us.archive.ubuntu.com trusty-security InRelease                     
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://ppa.launchpad.net trusty Release.gpg                       
Get:1 http://us.archive.ubuntu.com trusty Release.gpg [933 B]        
Hit http://extras.ubuntu.com trusty/main Sources                               
Get:2 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]          
Ign http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                  
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://archive.getdeb.net trusty-getdeb/apps amd64 Packages                
Hit http://us.archive.ubuntu.com trusty-security Release.gpg                   
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://archive.getdeb.net trusty-getdeb/apps i386 Packages                 
Get:3 http://us.archive.ubuntu.com trusty Release [58.5 kB]                    
Ign http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:4 http://us.archive.ubuntu.com trusty-updates Release [58.5 kB]            
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Hit http://us.archive.ubuntu.com trusty-security Release                       
Get:5 http://us.archive.ubuntu.com trusty/main Sources [1,064 kB]              
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en_US             
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en                
Get:6 http://us.archive.ubuntu.com trusty/restricted Sources [5,433 B]
Get:7 http://us.archive.ubuntu.com trusty/universe Sources [6,399 kB]          
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Err http://ppa.launchpad.net trusty/main amd64 Packages                        
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages                         
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Get:8 http://us.archive.ubuntu.com trusty/multiverse Sources [174 kB]          
Get:9 http://us.archive.ubuntu.com trusty/main amd64 Packages [1,350 kB]       
Get:10 http://us.archive.ubuntu.com trusty/restricted amd64 Packages [13.0 kB] 
Get:11 http://us.archive.ubuntu.com trusty/universe amd64 Packages [5,859 kB]  
Get:12 http://us.archive.ubuntu.com trusty/multiverse amd64 Packages [132 kB]  
Get:13 http://us.archive.ubuntu.com trusty/main i386 Packages [1,348 kB]       
Get:14 http://us.archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB]  
Get:15 http://us.archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]   
Get:16 http://us.archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]   
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Get:17 http://us.archive.ubuntu.com trusty-updates/main Sources [1,712 B]      
Get:18 http://us.archive.ubuntu.com trusty-updates/restricted Sources [14 B]   
Get:19 http://us.archive.ubuntu.com trusty-updates/universe Sources [648 B]    
Get:20 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [1,790 B]
Get:21 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [3,014 B]
Get:22 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [14 B]
Get:23 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [1,633 B]
Get:24 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [6,437 B]
Get:25 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [3,050 B]
Get:26 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [14 B]
Get:27 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [1,631 B]
Get:28 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [6,422 B]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://us.archive.ubuntu.com trusty-security/main Sources                  
Hit http://us.archive.ubuntu.com trusty-security/restricted Sources            
Hit http://us.archive.ubuntu.com trusty-security/universe Sources              
Hit http://us.archive.ubuntu.com trusty-security/multiverse Sources            
Hit http://us.archive.ubuntu.com trusty-security/main amd64 Packages           
Hit http://us.archive.ubuntu.com trusty-security/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com trusty-security/universe amd64 Packages       
Hit http://us.archive.ubuntu.com trusty-security/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com trusty-security/main i386 Packages            
Hit http://us.archive.ubuntu.com trusty-security/restricted i386 Packages      
Hit http://us.archive.ubuntu.com trusty-security/universe i386 Packages        
Hit http://us.archive.ubuntu.com trusty-security/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com trusty-security/main Translation-en           
Hit http://us.archive.ubuntu.com trusty-security/multiverse Translation-en     
Hit http://us.archive.ubuntu.com trusty-security/restricted Translation-en     
Hit http://us.archive.ubuntu.com trusty-security/universe Translation-en       
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com trusty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com trusty-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com trusty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com trusty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty-security/universe Translation-en_US
Fetched 22.5 MB in 1min 26s (260 kB/s)
W: Failed to fetch http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by buzzingrobot on 2014-04-18
Check that PPA's page on launchpad. They don't seem to have updated to Trusty.

---

### Post by Petro Dawg on 2014-04-18
So do you expect those paths were included with the expectation that they will be updated at some future date?  Should I just wait a while for those PPAs to be updated and expect the errors to resolve themselves or do I need change my PPA list to get all the updates I need.

---

### Post by ibjsb4 on 2014-04-18
Just disable (uncheck) the ppa in software sources for now and wait for the upgrade to come out.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)


It will be posted here when released


[http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/)

---

### Post by Petro Dawg on 2014-04-18
Actually, I think I now remember installing that PPA back when I was trying to fix my HDMI sound output, but I could have swore I did a complete OS reinstall since adding it (I guess I didn't).  Anyway, thanks for showing me where to turn that PPA off.

---

