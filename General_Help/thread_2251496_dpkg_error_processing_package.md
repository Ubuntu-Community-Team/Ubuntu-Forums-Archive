---
title: "dpkg: error processing package"
date: 2014-11-04
forum: General Help
---

### Post by pactaman on 2014-11-04
Lost connection to server while i was installing packages and  now I seem to getting the following error around libglib2.0-dev  package.
  > sudo apt-get -f install                                            
Reading package lists... Done                                                   
Building dependency tree                                                        
Reading state information... Done                                               
0 upgraded, 0 newly installed, 0 to remove and 102 not upgraded.                
1 not fully installed or removed.                                               
After this operation, 0 B of additional disk space will be used.                
Setting up libglib2.0-dev (2.40.2-0ubuntu1) ...                                 
Segmentation fault (core dumped)                                                
dpkg: error processing package libglib2.0-dev (--configure):                    
 subprocess installed post-installation script returned error exit status 139   
Errors were encountered while processing:                                       
 libglib2.0-dev                                                                 
E: Sub-process /usr/bin/dpkg returned an error code (1)
  I tried removing, dpkg purge, autoremove - nothing seems to work.
  Any clue how I can fix this package?

---

### Post by tgalati4 on 2014-11-04
There are log files in /var/log, specifically dpkg.log.  Look through there and post any helpful messages, not the entire log file.

What is the output of:

```
sudo apt-get check
```

Understand that the error could be because another package is missing, so treat all error messages as suggestions.  Try to determine which package was being downloaded or installed during the outage.  Note the exact time that the outage occured. Check syslog.  Then reinstall the 3 or 4 packages before that point, based on the time stamp.  They should all be listed in the log files.

Because of the multi-threading, it's possible that a few packages were broken during this outage, not just one.

---

### Post by pactaman on 2014-11-04
Here is what I am getting

> Reading package lists... Done                                                    
Building dependency tree                                                         
Reading state information... Done 

Also

> Errors were encountered while processing:^M                                       
libglib2.0-dev^M                                                                 
libpulse-dev:amd64^M                                                             
libsdl1.2-dev^M                                                                 
Log ended: 2014-11-04  10:11:05

> dpkg: dependency problems prevent configuration of libpulse-dev:amd64:^M          
libpulse-dev:amd64 depends on libglib2.0-dev; however:^M                          
Package libglib2.0-dev is not configured yet.^M                                ^M                                                                               dpkg: error processing package libpulse-dev:amd64 (--configure):^M                
dependency problems - leaving unconfigured^M                                    
dpkg: dependency problems prevent configuration of libsdl1.2-dev:^M              
 libsdl1.2-dev depends on libpulse-dev; however:^M                                 
Package libpulse-dev:amd64 is not configured yet.^M                            ^M                                                                               dpkg: error processing package libsdl1.2-dev (--configure):^M                     
dependency problems - leaving unconfigured^M         

---

