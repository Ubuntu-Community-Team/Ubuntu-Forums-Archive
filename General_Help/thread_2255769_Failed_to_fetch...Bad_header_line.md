---
title: "Failed to fetch...Bad header line"
date: 2014-12-07
forum: General Help
---

### Post by sccjono on 2014-12-07
Hello all,

I wonder if anyone can help with a minor but nonetheless annoying issue. Just recently (about four days now) I have been getting an error when running 'sudo apt-get update'. See below. You can see that the update it fails on is that of Dropbox but I don't think it is an issue their end as it works fine on another machine. Several posts I have found where a user has the same problem but no definitive fix. Is it some kind of cache problem perhaps?

```
jono@HP-Pav-g6:~$ sudo apt-get update[sudo] password for jono: 
Ign http://extras.ubuntu.com utopic InRelease
Hit http://extras.ubuntu.com utopic Release.gpg                                                                                                                          
Ign http://ppa.launchpad.net utopic InRelease                                                                                                                            
Ign http://gb.archive.ubuntu.com utopic InRelease                                                                                                                        
Hit http://extras.ubuntu.com utopic Release                                                                                                                              
Ign http://gb.archive.ubuntu.com utopic-updates InRelease                                                                                                                
Ign http://dl.google.com stable InRelease                                                                                                                                
Ign http://gb.archive.ubuntu.com utopic-backports InRelease                                                                                                              
Hit http://gb.archive.ubuntu.com utopic Release.gpg                                                                                                                   
Get:1 http://gb.archive.ubuntu.com utopic-updates Release.gpg [933 B]                                                                                                 
Ign http://dl.google.com stable InRelease                                                                                                                             
Hit http://gb.archive.ubuntu.com utopic-backports Release.gpg                                                                                                         
Hit http://gb.archive.ubuntu.com utopic Release                                                                                         
Hit http://dl.google.com stable Release.gpg                                                                                             
Get:2 http://gb.archive.ubuntu.com utopic-updates Release [62.0 kB]                                                                     
Ign http://security.ubuntu.com utopic-security InRelease                                   
Ign http://ppa.launchpad.net utopic InRelease                                              
Hit http://dl.google.com stable Release.gpg                                                                                                      
Ign http://ppa.launchpad.net utopic InRelease                                                                                                    
Hit http://extras.ubuntu.com utopic/main Sources                                                                                                                       
Hit http://ppa.launchpad.net utopic Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net utopic Release.gpg                                                                                                    
Hit http://dl.google.com stable Release                                                                                                            
Hit http://gb.archive.ubuntu.com utopic-backports Release                                                                                                        
Ign http://linux.dropbox.com utopic InRelease                                                                                                                    
Hit http://extras.ubuntu.com utopic/main amd64 Packages                                                                                                          
Hit http://ppa.launchpad.net utopic Release.gpg                                                                                         
Hit http://security.ubuntu.com utopic-security Release.gpg                                                                                                     
Hit http://extras.ubuntu.com utopic/main i386 Packages                                                                                                         
Hit http://ppa.launchpad.net utopic Release                                                                                                                    
Hit http://dl.google.com stable Release                                                                                                                        
Hit http://ppa.launchpad.net utopic Release                                                                                                                    
Hit http://ppa.launchpad.net utopic Release                                                                                                                    
Get:3 http://dl.google.com stable/main amd64 Packages [1,209 B]                                                                                                
Hit http://security.ubuntu.com utopic-security Release                                                                                   
Hit http://linux.dropbox.com utopic Release.gpg                                                                                           
Ign http://extras.ubuntu.com utopic/main Translation-en_GB                                                                               
Hit http://ppa.launchpad.net utopic/main amd64 Packages                                                            
Ign http://extras.ubuntu.com utopic/main Translation-en                                                                                  
Hit http://ppa.launchpad.net utopic/main i386 Packages                                                                                   
Hit http://linux.dropbox.com utopic Release                                                                        
Get:4 http://dl.google.com stable/main i386 Packages [1,201 B]                                                     
Hit http://security.ubuntu.com utopic-security/restricted Sources                                                 
Get:5 http://dl.google.com stable/main amd64 Packages [469 B]                                                     
Get:6 http://dl.google.com stable/main i386 Packages [464 B]                                                                               
Get:7 http://gb.archive.ubuntu.com utopic-updates/main Sources [30.9 kB]                                             
Hit http://ppa.launchpad.net utopic/main amd64 Packages                                                                                 
Get:8 http://gb.archive.ubuntu.com utopic-updates/restricted Sources [14 B]                                                             
Hit http://ppa.launchpad.net utopic/main i386 Packages                                                                                  
Get:9 http://gb.archive.ubuntu.com utopic-updates/universe Sources [9,320 B]                                                               
Hit http://ppa.launchpad.net utopic/main Translation-en                                                                                 
Get:10 http://gb.archive.ubuntu.com utopic-updates/multiverse Sources [703 B]                                                           
Get:11 http://gb.archive.ubuntu.com utopic-updates/main amd64 Packages [90.0 kB]                                                         
Hit http://ppa.launchpad.net utopic/main amd64 Packages                                                                      
Hit http://ppa.launchpad.net utopic/main i386 Packages                                                                       
Get:12 http://gb.archive.ubuntu.com utopic-updates/restricted amd64 Packages [14 B]                                          
Get:13 http://gb.archive.ubuntu.com utopic-updates/universe amd64 Packages [37.9 kB]                                                          
Ign http://ppa.launchpad.net utopic/main Translation-en_GB                                                                                
Get:14 http://gb.archive.ubuntu.com utopic-updates/multiverse amd64 Packages [1,143 B]                                                    
Ign http://ppa.launchpad.net utopic/main Translation-en                                                                                          
Get:15 http://gb.archive.ubuntu.com utopic-updates/main i386 Packages [89.1 kB]                                                           
Hit http://security.ubuntu.com utopic-security/restricted amd64 Packages                                                                             
Get:16 http://gb.archive.ubuntu.com utopic-updates/restricted i386 Packages [14 B]                                                          
Get:17 http://gb.archive.ubuntu.com utopic-updates/universe i386 Packages [37.8 kB]                                                           
Get:18 http://gb.archive.ubuntu.com utopic-updates/multiverse i386 Packages [1,394 B]                                                                
Ign http://ppa.launchpad.net utopic/main Translation-en_GB                                                                                
Ign http://ppa.launchpad.net utopic/main Translation-en                                                                                   
Hit http://gb.archive.ubuntu.com utopic-updates/restricted Translation-en                                                                 
Hit http://gb.archive.ubuntu.com utopic/main Sources                                        
Hit http://gb.archive.ubuntu.com utopic/restricted Sources                                                
Hit http://gb.archive.ubuntu.com utopic/universe Sources                                                  
Hit http://gb.archive.ubuntu.com utopic-backports/main Sources                      
Hit http://gb.archive.ubuntu.com utopic-backports/restricted Sources                                           
Hit http://gb.archive.ubuntu.com utopic-backports/multiverse Sources                                           
Hit http://security.ubuntu.com utopic-security/restricted i386 Packages                                        
Hit http://gb.archive.ubuntu.com utopic-backports/main amd64 Packages                                          
Hit http://gb.archive.ubuntu.com utopic-backports/restricted amd64 Packages                                    
Ign http://dl.google.com stable/main Translation-en_GB                                                         
Hit http://gb.archive.ubuntu.com utopic-backports/multiverse amd64 Packages                                    
Ign http://dl.google.com stable/main Translation-en                                                            
Hit http://gb.archive.ubuntu.com utopic-backports/main i386 Packages                                           
Hit http://gb.archive.ubuntu.com utopic-backports/restricted i386 Packages                                
Ign http://dl.google.com stable/main Translation-en_GB                              
Hit http://gb.archive.ubuntu.com utopic-backports/multiverse i386 Packages                                
Ign http://dl.google.com stable/main Translation-en                                                       
Hit http://gb.archive.ubuntu.com utopic-backports/main Translation-en               
Hit http://gb.archive.ubuntu.com utopic-backports/multiverse Translation-en         
Hit http://gb.archive.ubuntu.com utopic-backports/restricted Translation-en         
Hit http://gb.archive.ubuntu.com utopic/multiverse Sources                          
Hit http://gb.archive.ubuntu.com utopic/main amd64 Packages                         
Hit http://gb.archive.ubuntu.com utopic/restricted amd64 Packages                   
Hit http://gb.archive.ubuntu.com utopic/universe amd64 Packages                     
Hit http://gb.archive.ubuntu.com utopic/multiverse amd64 Packages                   
Hit http://gb.archive.ubuntu.com utopic/main i386 Packages                          
Err http://linux.dropbox.com utopic/main amd64 Packages                             
  Bad header line
Hit http://gb.archive.ubuntu.com utopic/restricted i386 Packages
Hit http://gb.archive.ubuntu.com utopic/universe i386 Packages                          
Hit http://gb.archive.ubuntu.com utopic/multiverse i386 Packages                        
Hit http://gb.archive.ubuntu.com utopic/main Translation-en_GB    
Hit http://gb.archive.ubuntu.com utopic/main Translation-en                             
Hit http://gb.archive.ubuntu.com utopic/multiverse Translation-en_GB                    
Hit http://linux.dropbox.com utopic/main i386 Packages                                  
Hit http://gb.archive.ubuntu.com utopic/multiverse Translation-en                       
Hit http://security.ubuntu.com utopic-security/restricted Translation-en                
Hit http://gb.archive.ubuntu.com utopic/restricted Translation-en_GB                    
Hit http://gb.archive.ubuntu.com utopic/restricted Translation-en                       
Hit http://gb.archive.ubuntu.com utopic/universe Translation-en_GB                      
Hit http://gb.archive.ubuntu.com utopic/universe Translation-en                         
Hit http://gb.archive.ubuntu.com utopic-updates/main Translation-en                     
Hit http://gb.archive.ubuntu.com utopic-updates/multiverse Translation-en               
Hit http://gb.archive.ubuntu.com utopic-updates/universe Translation-en                 
Hit http://gb.archive.ubuntu.com utopic-backports/universe Sources
Hit http://security.ubuntu.com utopic-security/main Sources       
Hit http://gb.archive.ubuntu.com utopic-backports/universe amd64 Packages               
Hit http://gb.archive.ubuntu.com utopic-backports/universe i386 Packages                
Hit http://gb.archive.ubuntu.com utopic-backports/universe Translation-en               
Hit http://security.ubuntu.com utopic-security/universe Sources                         
Hit http://security.ubuntu.com utopic-security/multiverse Sources 
Hit http://security.ubuntu.com utopic-security/main amd64 Packages
Hit http://security.ubuntu.com utopic-security/universe amd64 Packages
Hit http://security.ubuntu.com utopic-security/multiverse amd64 Packages
Ign http://linux.dropbox.com utopic/main Translation-en_GB
Hit http://security.ubuntu.com utopic-security/main i386 Packages
Hit http://security.ubuntu.com utopic-security/universe i386 Packages
Ign http://linux.dropbox.com utopic/main Translation-en           
Hit http://security.ubuntu.com utopic-security/multiverse i386 Packages
Hit http://security.ubuntu.com utopic-security/main Translation-en
Hit http://security.ubuntu.com utopic-security/multiverse Translation-en
Hit http://security.ubuntu.com utopic-security/universe Translation-en
Fetched 365 kB in 9s (37.2 kB/s)                                                                                                                                         
W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/utopic/main/binary-amd64/Packages  Bad header line


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by llamabr on 2014-12-07
Have you tried commenting out the dropbox line?

---

### Post by sccjono on 2014-12-08
I have just commented out the line in /etc/apt/sources.list.d/dropbox.list and ran the update and yes it worked. But I was going to say that surely that would just stop my system checking for Dropbox updates? So I uncommented the line and it still works. I'm confused but happy, thank you. Any ideas on what causes this or how doing this fixed it?

Jon

---

### Post by llamabr on 2014-12-08
You can leave it commented.  It won't mess with installed software -- it just won't update it.

No idea what happened.  Maybe leave it commented for a few weeks, and then uncomment it.  Sometimes these things fix themselves, if it's just a connection issue.

---

