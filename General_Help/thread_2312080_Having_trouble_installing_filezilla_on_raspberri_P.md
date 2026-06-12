---
title: "Having trouble installing filezilla on raspberri Pi"
date: 2016-02-01
forum: General Help
---

### Post by nzdreamer55 on 2016-02-01
Hello everyone,


I have Pi 2 and wanted to install FileZilla on it.  However it says that I have broken packages.  What does that mean and how do I correct it?

```
pi@raspberry:~$ sudo apt-get install filezilla
[sudo] password for pi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 filezilla : Depends: filezilla-common (= 3.12.0.2-1ubuntu2.1) but 3.14.1-1u1~ppa1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by TheFu on 2016-02-03
Start by updating the system.

1) sudo apt-get update
2) sudo apt-get upgrade
3) sudo apt-get install filezilla

DO NOT CONTINUE if any of those steps has ANY failure.  Post the **relevant** output back here, using "code tags", so things line up clearly.
R U running Ubuntu on the pi?

---

### Post by nzdreamer55 on 2016-02-03
```
pi@raspberry:~$ sudo apt-get update
[sudo] password for pi: 
Sorry, try again.
[sudo] password for pi: 
Hit http://ppa.launchpad.net wily InRelease
Hit http://ppa.launchpad.net wily InRelease                                    
Hit http://ppa.launchpad.net wily InRelease                                    
Ign http://ppa.launchpad.net wily InRelease                                    
Ign http://ppa.launchpad.net wily Release.gpg                                  
Hit http://ppa.launchpad.net wily/main armhf Packages                          
Hit http://ppa.launchpad.net wily/main Translation-en                          
Hit http://ppa.launchpad.net wily/main armhf Packages                          
Hit http://ppa.launchpad.net wily/main Translation-en                          
Hit http://ppa.launchpad.net wily/main armhf Packages                          
Hit http://ppa.launchpad.net wily/main Translation-en                          
Ign http://ppa.launchpad.net wily Release                                      
Err http://ppa.launchpad.net wily/main armhf Packages                          
  404  Not Found
Ign http://ppa.launchpad.net wily/main Translation-en_US                       
Ign http://ppa.launchpad.net wily/main Translation-en                          
Ign http://ppa.launchpad.net wily/main Translation-en_GB                       
Hit http://ports.ubuntu.com wily InRelease                                     
Get:1 http://ports.ubuntu.com wily-updates InRelease [64.4 kB]
Hit http://ports.ubuntu.com wily-security InRelease                            
Hit http://ports.ubuntu.com wily-backports InRelease                           
Hit http://ports.ubuntu.com wily InRelease                                     
Get:2 http://ports.ubuntu.com wily-updates InRelease [64.4 kB]                 
Hit http://ports.ubuntu.com wily-security InRelease                            
Get:3 http://ports.ubuntu.com wily-updates/main Sources [45.5 kB]              
Get:4 http://ports.ubuntu.com wily-updates/restricted Sources [3,741 B]        
Get:5 http://ports.ubuntu.com wily-updates/universe Sources [12.5 kB]          
Get:6 http://ports.ubuntu.com wily-updates/multiverse Sources [1,923 B]        
Get:7 http://ports.ubuntu.com wily-updates/main armhf Packages [114 kB]        
Get:8 http://ports.ubuntu.com wily-updates/restricted armhf Packages [7,632 B] 
Get:9 http://ports.ubuntu.com wily-updates/universe armhf Packages [53.3 kB]   
Get:10 http://ports.ubuntu.com wily-updates/multiverse armhf Packages [2,528 B]
Get:11 http://ports.ubuntu.com wily-updates/main Translation-en [60.4 kB]      
Get:12 http://ports.ubuntu.com wily-updates/multiverse Translation-en [2,536 B]
Get:13 http://ports.ubuntu.com wily-updates/restricted Translation-en [3,024 B]
Get:14 http://ports.ubuntu.com wily-updates/universe Translation-en [33.9 kB]  
Hit http://ports.ubuntu.com wily-backports/restricted Sources                  
Hit http://ports.ubuntu.com wily-backports/multiverse Sources                  
Hit http://ports.ubuntu.com wily-backports/restricted armhf Packages           
Hit http://ports.ubuntu.com wily-backports/multiverse armhf Packages           
Hit http://ports.ubuntu.com wily-backports/multiverse Translation-en           
Hit http://ports.ubuntu.com wily-backports/restricted Translation-en           
Get:15 http://ports.ubuntu.com wily-updates/main armhf Packages [114 kB]       
Get:16 http://ports.ubuntu.com wily-updates/restricted armhf Packages [7,632 B]
Get:17 http://ports.ubuntu.com wily-updates/universe armhf Packages [53.3 kB]  
Get:18 http://ports.ubuntu.com wily-updates/multiverse armhf Packages [2,528 B]
Get:19 http://ports.ubuntu.com wily-updates/main Translation-en [60.4 kB]      
Get:20 http://ports.ubuntu.com wily-updates/multiverse Translation-en [2,536 B]
Get:21 http://ports.ubuntu.com wily-updates/restricted Translation-en [3,024 B]
Get:22 http://ports.ubuntu.com wily-updates/universe Translation-en [33.9 kB]  
Hit http://ports.ubuntu.com wily/main Sources                                  
Hit http://ports.ubuntu.com wily/restricted Sources                            
Hit http://ports.ubuntu.com wily/universe Sources                              
Hit http://ports.ubuntu.com wily/multiverse Sources                            
Hit http://ports.ubuntu.com wily/main armhf Packages                           
Hit http://ports.ubuntu.com wily/restricted armhf Packages                     
Hit http://ports.ubuntu.com wily/universe armhf Packages                       
Hit http://ports.ubuntu.com wily/multiverse armhf Packages                     
Hit http://ports.ubuntu.com wily/main Translation-en                           
Hit http://ports.ubuntu.com wily/main Translation-en_GB                        
Hit http://ports.ubuntu.com wily/multiverse Translation-en                     
Hit http://ports.ubuntu.com wily/multiverse Translation-en_GB                  
Hit http://ports.ubuntu.com wily/restricted Translation-en                     
Hit http://ports.ubuntu.com wily/restricted Translation-en_GB                  
Hit http://ports.ubuntu.com wily/universe Translation-en                       
Hit http://ports.ubuntu.com wily/universe Translation-en_GB                    
Hit http://ports.ubuntu.com wily-security/main Sources                         
Hit http://ports.ubuntu.com wily-security/restricted Sources                   
Hit http://ports.ubuntu.com wily-security/universe Sources                     
Hit http://ports.ubuntu.com wily-security/multiverse Sources                   
Hit http://ports.ubuntu.com wily-security/main armhf Packages                  
Hit http://ports.ubuntu.com wily-security/restricted armhf Packages            
Hit http://ports.ubuntu.com wily-security/universe armhf Packages              
Hit http://ports.ubuntu.com wily-security/multiverse armhf Packages            
Hit http://ports.ubuntu.com wily-security/main Translation-en                  
Hit http://ports.ubuntu.com wily-security/multiverse Translation-en            
Hit http://ports.ubuntu.com wily-security/restricted Translation-en            
Hit http://ports.ubuntu.com wily-security/universe Translation-en              
Hit http://ports.ubuntu.com wily-backports/main Sources                        
Hit http://ports.ubuntu.com wily-backports/universe Sources                    
Hit http://ports.ubuntu.com wily-backports/main armhf Packages                 
Hit http://ports.ubuntu.com wily-backports/universe armhf Packages             
Hit http://ports.ubuntu.com wily-backports/main Translation-en                 
Hit http://ports.ubuntu.com wily-backports/universe Translation-en             
Hit http://ports.ubuntu.com wily/main armhf Packages                           
Hit http://ports.ubuntu.com wily/universe armhf Packages                       
Hit http://ports.ubuntu.com wily/restricted armhf Packages                     
Hit http://ports.ubuntu.com wily/multiverse armhf Packages                     
Hit http://ports.ubuntu.com wily/main Translation-en                           
Hit http://ports.ubuntu.com wily/main Translation-en_GB                        
Hit http://ports.ubuntu.com wily/multiverse Translation-en                     
Hit http://ports.ubuntu.com wily/multiverse Translation-en_GB                  
Hit http://ports.ubuntu.com wily/restricted Translation-en                     
Hit http://ports.ubuntu.com wily/restricted Translation-en_GB                  
Hit http://ports.ubuntu.com wily/universe Translation-en                       
Hit http://ports.ubuntu.com wily/universe Translation-en_GB                    
Hit http://ports.ubuntu.com wily-security/main armhf Packages                  
Hit http://ports.ubuntu.com wily-security/restricted armhf Packages            
Hit http://ports.ubuntu.com wily-security/universe armhf Packages              
Hit http://ports.ubuntu.com wily-security/multiverse armhf Packages            
Hit http://ports.ubuntu.com wily-security/main Translation-en                  
Hit http://ports.ubuntu.com wily-security/multiverse Translation-en            
Hit http://ports.ubuntu.com wily-security/restricted Translation-en            
Hit http://ports.ubuntu.com wily-security/universe Translation-en              
Fetched 747 kB in 3min 23s (3,664 B/s)                                         
W: Failed to fetch http://ppa.launchpad.net/run-one/ppa/ubuntu/dists/wily/main/binary-armhf/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Thanks when I tried the first thing I got this.  I didn't go any further.

---

### Post by TheFu on 2016-02-04
I don't run non-LTS releases, so I'm not certain, but this doesn't look evil. Try the 2nd command. If there are any errors, stop.

---

### Post by nzdreamer55 on 2016-02-04
Thanks for the help.  Went on and still got the same error

```
pi@raspberry:~$ sudo apt-get upgrade
[sudo] password for pi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following packages were automatically installed and are no longer required:
  apt-clone archdetect-deb dpkg-repack gir1.2-json-1.0 gir1.2-timezonemap-1.0
  gir1.2-xkl-1.0 libdebian-installer4 libtimezonemap-data libtimezonemap1
  os-prober python3-icu python3-pam rdate
Use 'apt-get autoremove' to remove them.
Done
The following packages will be upgraded:
  ifupdown
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 46.4 kB of archives.
After this operation, 66.6 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://ports.ubuntu.com/ wily-updates/main ifupdown armhf 0.7.54ubuntu1.2 [46.4 kB]
Fetched 46.4 kB in 2min 0s (384 B/s)               
(Reading database ... 165703 files and directories currently installed.)
Preparing to unpack .../ifupdown_0.7.54ubuntu1.2_armhf.deb ...
Unpacking ifupdown (0.7.54ubuntu1.2) over (0.7.54ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (225-1ubuntu9) ...
Processing triggers for man-db (2.7.4-1) ...
Setting up ifupdown (0.7.54ubuntu1.2) ...
pi@raspberry:~$ sudo apt-get install filezilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 filezilla : Depends: filezilla-common (= 3.12.0.2-1ubuntu2.1) but 3.14.1-1u1~ppa1 is to be installed
E: Unable to correct problems, you have held broken packages.
pi@raspberry:~$ 


```

Sorry I cannot help more, but is there a way to uninstall the broken packages?

---

### Post by TheFu on 2016-02-04
If you have added any PPAs or installed any packages directly with *.deb files, those are likely the issue. Remove those PPAs and rerun all the commands I provided above, in order. Remove any manually installed .deb packages too (if you use dpkg directly, that's one issue.)

Another thing you can try is **aptitude** instead of apt-get. Both tools read/write to the same backend DBs, but aptitude tends to be a little smarter in resolving dependencies. Could be that aptitude isn't installed, so you're sorta stuck.

It's a r-pi - why not start with a fresh OS install?  Honestly, that is what I'd do on my pi.

---

