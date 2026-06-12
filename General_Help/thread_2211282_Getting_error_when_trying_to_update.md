---
title: "Getting error when trying to update"
date: 2014-03-15
forum: General Help
---

### Post by thekeshav on 2014-03-15
Hello,

I am using Ubuntu 12.04 (64-bit). Recently by follwing a video tutorial, I added tools of Backtrack and Kalilinux. At that time I edited the source.list file. When updating by giving ```
 sudo apt-get update 
``` it shows, some of them are ignoring and some of are errors. I am listing the code what I got, please explain me what's the problem and what I need to do ? ? ? ...... Please Help.......Thanks !!

```

[sudo] password for shivkesh: 
Get:1 http://dl.google.com stable Release.gpg [198 B]
Get:2 http://extras.ubuntu.com precise Release.gpg [72 B]                                                                                             
Hit http://in.archive.ubuntu.com precise Release.gpg                                                                                                  
Get:3 http://ppa.launchpad.net precise Release.gpg [316 B]                                                                                            
Get:4 http://dl.google.com stable Release [1,351 B]                                                                                                   
Get:5 http://security.ubuntu.com precise-security Release.gpg [198 B]                                                                                 
Hit http://deb.playonlinux.com precise Release.gpg                                                                                                  
Hit http://extras.ubuntu.com precise Release                                                                                                          
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                      
Hit http://64.repository.backtrack-linux.org revolution Release.gpg                                                                                   
Get:6 http://dl.google.com stable/main amd64 Packages [1,257 B]                                                                                       
Hit http://all.repository.backtrack-linux.org revolution Release.gpg                                                                                  
Get:7 http://in.archive.ubuntu.com precise-updates Release.gpg [198 B]                                                                                
Hit http://source.repository.backtrack-linux.org revolution Release.gpg                                                                               
Get:8 http://security.ubuntu.com precise-security Release [49.6 kB]                                                                                   
Hit http://deb.playonlinux.com precise Release                                                                                                        
Get:9 http://dl.google.com stable/main i386 Packages [1,244 B]                                                                                        
Ign http://dl.google.com stable/main TranslationIndex                                                                                                 
Hit http://64.repository.backtrack-linux.org revolution Release                                                                                       
Hit http://extras.ubuntu.com precise/main Sources                                                                                                     
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                      
Hit http://in.archive.ubuntu.com precise-backports Release.gpg                                                                                        
Hit http://deb.playonlinux.com precise/main amd64 Packages                                                                                            
Hit http://all.repository.backtrack-linux.org revolution Release                                                                                      
Hit http://source.repository.backtrack-linux.org revolution Release                                                                                   
Hit http://ppa.launchpad.net precise Release                                                                                                          
Hit http://extras.ubuntu.com precise/main amd64 Packages                                                                                              
Ign http://ppa.launchpad.net precise Release                                                                                                          
Get:10 http://security.ubuntu.com precise-security/main Sources [99.2 kB]                                                                             
Hit http://deb.playonlinux.com precise/main i386 Packages                                                                                             
Hit http://in.archive.ubuntu.com precise Release                                                                                                      
Hit http://64.repository.backtrack-linux.org revolution/main amd64 Packages                                                                           
Hit http://source.repository.backtrack-linux.org revolution/main amd64 Packages                                                                       
Hit http://all.repository.backtrack-linux.org revolution/main amd64 Packages                                                                          
Hit http://extras.ubuntu.com precise/main i386 Packages                                                                                               
Hit http://ppa.launchpad.net precise Release                                                                                                          
Ign http://deb.playonlinux.com precise/main TranslationIndex                                                                                          
Get:11 http://in.archive.ubuntu.com precise-updates Release [49.6 kB]                                                                                 
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                          
Hit http://source.repository.backtrack-linux.org revolution/microverse amd64 Packages                                                                 
Hit http://all.repository.backtrack-linux.org revolution/microverse amd64 Packages                                                                    
Hit http://64.repository.backtrack-linux.org revolution/microverse amd64 Packages                                                                     
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex                                                                                           
Ign http://dl.google.com stable/main Translation-en_IN                                                                                                
Ign http://ppa.launchpad.net precise/main amd64 Packages/DiffIndex                                                                                    
Ign http://dl.google.com stable/main Translation-en                                                                                                   
Hit http://source.repository.backtrack-linux.org revolution/non-free amd64 Packages                                                                   
Hit http://in.archive.ubuntu.com precise-backports Release                                                                                            
Hit http://all.repository.backtrack-linux.org revolution/non-free amd64 Packages                                                                      
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex                                                                                     
Hit http://64.repository.backtrack-linux.org revolution/non-free amd64 Packages                                                                       
Hit http://in.archive.ubuntu.com precise/main Sources                                                                                                 
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                            
Hit http://in.archive.ubuntu.com precise/restricted Sources                                                                                           
Hit http://ppa.launchpad.net precise/main Sources                                                                                                     
Get:12 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]                                                                       
Hit http://source.repository.backtrack-linux.org revolution/testing amd64 Packages                                                                    
Hit http://all.repository.backtrack-linux.org revolution/testing amd64 Packages                                                                       
Hit http://64.repository.backtrack-linux.org revolution/testing amd64 Packages                                                                        
Hit http://in.archive.ubuntu.com precise/universe Sources                                                                                             
Get:13 http://security.ubuntu.com precise-security/universe Sources [30.9 kB]                                                                         
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                              
Get:14 http://http.kali.org kali Release.gpg [836 B]                                                                                                  
Hit http://security.kali.org kali/updates Release.gpg                                                                                                 
Hit http://in.archive.ubuntu.com precise/multiverse Sources                                                                                           
Ign http://deb.playonlinux.com precise/main Translation-en_IN                                                                                         
Hit http://source.repository.backtrack-linux.org revolution/main i386 Packages                                                                        
Hit http://all.repository.backtrack-linux.org revolution/main i386 Packages                                                                           
Get:15 http://security.ubuntu.com precise-security/multiverse Sources [1,789 B]                                                                       
Ign http://extras.ubuntu.com precise/main Translation-en_IN                                                                                           
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                                               
Hit http://in.archive.ubuntu.com precise/main amd64 Packages                                                                                          
Ign http://deb.playonlinux.com precise/main Translation-en                                                                                            
Ign http://extras.ubuntu.com precise/main Translation-en                                                                                              
Hit http://in.archive.ubuntu.com precise/restricted amd64 Packages                                                                                    
Get:16 http://security.ubuntu.com precise-security/main amd64 Packages [370 kB]                                                                       
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                            
Get:17 http://http.kali.org kali Release [21.1 kB]                                                                                                    
Hit http://source.repository.backtrack-linux.org revolution/microverse i386 Packages                                                                  
Hit http://security.kali.org kali/updates Release                                                                                                     
Hit http://all.repository.backtrack-linux.org revolution/microverse i386 Packages                                                                     
Hit http://ppa.launchpad.net precise/main Sources                                                                                                     
Hit http://in.archive.ubuntu.com precise/universe amd64 Packages                                                                                      
Hit http://in.archive.ubuntu.com precise/multiverse amd64 Packages                                                                                    
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                              
Hit http://source.repository.backtrack-linux.org revolution/non-free i386 Packages                                                                    
Hit http://all.repository.backtrack-linux.org revolution/non-free i386 Packages                                                                       
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                                               
Hit http://source.repository.backtrack-linux.org revolution/testing i386 Packages                                                                     
Hit http://all.repository.backtrack-linux.org revolution/testing i386 Packages                                                                        
Get:18 http://http.kali.org kali/main Sources [7,527 kB]                                                                                              
Get:19 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]                                                                
Ign http://source.repository.backtrack-linux.org revolution/main TranslationIndex                                                                     
Ign http://all.repository.backtrack-linux.org revolution/main TranslationIndex                                                                        
Get:20 http://security.ubuntu.com precise-security/universe amd64 Packages [91.3 kB]                                                                  
Ign http://source.repository.backtrack-linux.org revolution/microverse TranslationIndex                                                               
Ign http://all.repository.backtrack-linux.org revolution/microverse TranslationIndex                                                                  
Ign http://source.repository.backtrack-linux.org revolution/non-free TranslationIndex                                                                 
Ign http://all.repository.backtrack-linux.org revolution/non-free TranslationIndex                                                                    
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                            
Ign http://source.repository.backtrack-linux.org revolution/testing TranslationIndex                                                                  
Hit http://ppa.launchpad.net precise/main Sources                                                                                                     
Ign http://all.repository.backtrack-linux.org revolution/testing TranslationIndex                                                                     
Hit http://in.archive.ubuntu.com precise/main i386 Packages                                                                                           
Get:21 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,446 B]                                                                
Get:22 http://security.ubuntu.com precise-security/main i386 Packages [396 kB]                                                                        
Hit http://in.archive.ubuntu.com precise/restricted i386 Packages                                                                                     
Hit http://in.archive.ubuntu.com precise/universe i386 Packages                                                                                       
Hit http://security.kali.org kali/updates/main Sources                                                                                                
Hit http://in.archive.ubuntu.com precise/multiverse i386 Packages                                                                                     
Get:23 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]                                                                 
Get:24 http://security.ubuntu.com precise-security/universe i386 Packages [96.1 kB]                                                                   
Hit http://in.archive.ubuntu.com precise/main TranslationIndex                                                                                        
Get:25 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,646 B]                                                                 
Hit http://in.archive.ubuntu.com precise/multiverse TranslationIndex                                                                                  
Hit http://security.ubuntu.com precise-security/main TranslationIndex                                                                                 
Hit http://in.archive.ubuntu.com precise/restricted TranslationIndex                                                                                  
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                                                                           
Hit http://in.archive.ubuntu.com precise/universe TranslationIndex                                                                                    
Get:26 http://in.archive.ubuntu.com precise-updates/main Sources [452 kB]                                                                             
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                                                                           
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                                                                             
Hit http://security.ubuntu.com precise-security/main Translation-en                                                                                   
Get:27 http://in.archive.ubuntu.com precise-updates/restricted Sources [8,028 B]                                                                      
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                                                                             
Get:28 http://in.archive.ubuntu.com precise-updates/universe Sources [105 kB]                                                                         
Hit http://security.ubuntu.com precise-security/restricted Translation-en                                                                             
Hit http://security.ubuntu.com precise-security/universe Translation-en                                                                               
Get:29 http://in.archive.ubuntu.com precise-updates/multiverse Sources [8,900 B]                                                                      
Get:30 http://in.archive.ubuntu.com precise-updates/main amd64 Packages [758 kB]                                                                      
Get:31 http://in.archive.ubuntu.com precise-updates/restricted amd64 Packages [12.2 kB]                                                               
Get:32 http://in.archive.ubuntu.com precise-updates/universe amd64 Packages [237 kB]                                                                  
Get:33 http://in.archive.ubuntu.com precise-updates/multiverse amd64 Packages [15.3 kB]                                                               
Ign http://source.repository.backtrack-linux.org revolution/main Translation-en_IN                                                                    
Get:34 http://in.archive.ubuntu.com precise-updates/main i386 Packages [782 kB]                                                                       
Ign http://source.repository.backtrack-linux.org revolution/main Translation-en                                                                       
Ign http://source.repository.backtrack-linux.org revolution/microverse Translation-en_IN                                                              
Ign http://source.repository.backtrack-linux.org revolution/microverse Translation-en                                                                 
Ign http://source.repository.backtrack-linux.org revolution/non-free Translation-en_IN                                                                
Ign http://source.repository.backtrack-linux.org revolution/non-free Translation-en                                                                   
Ign http://source.repository.backtrack-linux.org revolution/testing Translation-en_IN                                                                 
Ign http://source.repository.backtrack-linux.org revolution/testing Translation-en                                                                    
Get:35 http://in.archive.ubuntu.com precise-updates/restricted i386 Packages [12.2 kB]                                                                
Get:36 http://in.archive.ubuntu.com precise-updates/universe i386 Packages [242 kB]                                                                   
Get:37 http://in.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]                                                                
Get:38 http://in.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]                                                                   
Get:39 http://in.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]                                                             
Get:40 http://in.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]                                                             
Get:41 http://in.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]                                                               
Hit http://in.archive.ubuntu.com precise-backports/main Sources                                                                                       
Hit http://in.archive.ubuntu.com precise-backports/restricted Sources                                                                                 
Hit http://in.archive.ubuntu.com precise-backports/universe Sources                                                                                   
Hit http://in.archive.ubuntu.com precise-backports/multiverse Sources                                                                                 
Hit http://in.archive.ubuntu.com precise-backports/main amd64 Packages                                                                                
Hit http://in.archive.ubuntu.com precise-backports/restricted amd64 Packages                                                                          
Hit http://in.archive.ubuntu.com precise-backports/universe amd64 Packages                                                                            
Hit http://in.archive.ubuntu.com precise-backports/multiverse amd64 Packages                                                                          
Hit http://in.archive.ubuntu.com precise-backports/main i386 Packages                                                                                 
Hit http://in.archive.ubuntu.com precise-backports/restricted i386 Packages                                                                           
Hit http://in.archive.ubuntu.com precise-backports/universe i386 Packages                                                                             
Hit http://in.archive.ubuntu.com precise-backports/multiverse i386 Packages                                                                           
Hit http://in.archive.ubuntu.com precise-backports/main TranslationIndex                                                                              
Hit http://in.archive.ubuntu.com precise-backports/multiverse TranslationIndex                                                                        
Hit http://in.archive.ubuntu.com precise-backports/restricted TranslationIndex                                                                        
Hit http://in.archive.ubuntu.com precise-backports/universe TranslationIndex                                                                          
Hit http://in.archive.ubuntu.com precise/main Translation-en                                                                                          
Hit http://in.archive.ubuntu.com precise/multiverse Translation-en                                                                                    
Hit http://in.archive.ubuntu.com precise/restricted Translation-en                                                                                    
Hit http://in.archive.ubuntu.com precise/universe Translation-en                                                                                      
Hit http://in.archive.ubuntu.com precise-updates/main Translation-en                                                                                  
Hit http://in.archive.ubuntu.com precise-updates/multiverse Translation-en                                                                            
Hit http://in.archive.ubuntu.com precise-updates/restricted Translation-en                                                                            
Hit http://in.archive.ubuntu.com precise-updates/universe Translation-en                                                      
Hit http://in.archive.ubuntu.com precise-backports/main Translation-en                                                                                
Hit http://in.archive.ubuntu.com precise-backports/multiverse Translation-en                                                  
Hit http://in.archive.ubuntu.com precise-backports/restricted Translation-en                                                                          
Hit http://in.archive.ubuntu.com precise-backports/universe Translation-en                                                                            
Hit http://security.kali.org kali/updates/contrib Sources                                               
Hit http://security.kali.org kali/updates/non-free Sources                                                                                            
Ign http://all.repository.backtrack-linux.org revolution/main Translation-en_IN                                                                       
Ign http://all.repository.backtrack-linux.org revolution/main Translation-en                                                                          
Ign http://all.repository.backtrack-linux.org revolution/microverse Translation-en_IN                                                                 
Ign http://all.repository.backtrack-linux.org revolution/microverse Translation-en                                                                    
Ign http://all.repository.backtrack-linux.org revolution/non-free Translation-en_IN                                                                   
Ign http://all.repository.backtrack-linux.org revolution/non-free Translation-en                                                                      
Ign http://all.repository.backtrack-linux.org revolution/testing Translation-en_IN                                                                    
Ign http://all.repository.backtrack-linux.org revolution/testing Translation-en                                                                       
Hit http://http.kali.org kali/non-free Sources                                                                                                        
Hit http://http.kali.org kali/contrib Sources                                                                                                         
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                              
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main Translation-en_IN
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_IN
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_IN
Ign http://ppa.launchpad.net precise/main Translation-en
Fetched 11.4 MB in 2min 16s (83.6 kB/s)
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 1B22EB8D8FDFDB57 Launchpad PPA for wagung
W: Failed to fetch http://64.repository.backtrack-linux.org/dists/revolution/Release  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
shivkesh@Keshav:~$ 


```

---

### Post by grahammechanical on 2014-03-15
Personal Package Archives (PPA) are useful for installing software that is not in the standard Ubuntu repositories but they should be disabled after the installation of the software. Then error messages like this will not appear. It could also be the case that some of the repositories listed are no longer in existence and that is why the index files are not being downloaded and the repositories are being ignored.

Regards.

---

### Post by raja.genupula on 2014-03-15
Open your terminal and paste these commands one after one

> [INDENT]  sudo -i

   apt-get clean

  cd /var/lib/apt

  mv lists lists.old

  mkdir -p lists/partial

  apt-get clean

  apt-get update


[/INDENT]

Let us know what you got.

---

### Post by deadflowr on 2014-03-15
> **grahammechanical said:**
> Personal Package Archives (PPA) are useful for installing software that is not in the standard Ubuntu repositories but they should be disabled after the installation of the software. Then error messages like this will not appear. It could also be the case that some of the repositories listed are no longer in existence and that is why the index files are not being downloaded and the repositories are being ignored.

Regards.

That depends on the package being installed from the ppa.
While most packages installed will be one and done, a few will need continuous updates.
Like google-chrome, or other browsers.

Disabling the ppa for those could leave the user without updated security fixes.

But, I do agree that for a lot of ppas, you can simply disable them for the fact that the ppa is as updated as installing the package from a deb file.

---

### Post by thekeshav on 2014-03-21
Thanks for your kind reply ! Here What I got !!!!!!!!!
```

shivkesh@Keshav:~$ sudo -i
root@Keshav:~# apt-get clean
root@Keshav:~# cd /var/lib/apt
root@Keshav:/var/lib/apt# mv lists lists.old
root@Keshav:/var/lib/apt# mkdir -p lists/partial
root@Keshav:/var/lib/apt# apt-get clean
root@Keshav:/var/lib/apt# apt-get update
Get:1 http://dl.google.com stable Release.gpg [198 B]
Get:2 http://dl.google.com stable Release [1,351 B]                                                                                                   
Get:3 http://extras.ubuntu.com precise Release.gpg [72 B]                                                                                             
Get:4 http://ppa.launchpad.net precise Release.gpg [316 B]                                                                                            
Get:5 http://in.archive.ubuntu.com precise Release.gpg [198 B]                                                                                        
Get:6 http://deb.playonlinux.com precise Release.gpg [198 B]                                                                                          
Get:7 http://security.ubuntu.com precise-security Release.gpg [198 B]                                                                                 
Get:8 http://dl.google.com stable/main amd64 Packages [1,256 B]                                                                                       
Get:9 http://extras.ubuntu.com precise Release [11.9 kB]                                                                                              
Get:10 http://deb.playonlinux.com precise Release [1,724 B]                                                                                           
Get:11 http://ppa.launchpad.net precise Release.gpg [316 B]                                                                                           
Get:12 http://dl.google.com stable/main i386 Packages [1,243 B]                                                                                       
Get:13 http://ppa.launchpad.net precise Release.gpg [316 B]                                                                                           
Get:14 http://extras.ubuntu.com precise/main Sources [8,130 B]                                                                                        
Get:15 http://deb.playonlinux.com precise/main amd64 Packages [542 B]                                                                                 
Ign http://dl.google.com stable/main TranslationIndex                                                                                                 
Get:16 http://source.repository.backtrack-linux.org revolution Release.gpg [198 B]                                                                    
Get:17 http://all.repository.backtrack-linux.org revolution Release.gpg [198 B]                                                                       
Get:18 http://ppa.launchpad.net precise Release [11.9 kB]                                                                                             
Get:19 http://extras.ubuntu.com precise/main amd64 Packages [10.8 kB]                                                                                 
Get:20 http://in.archive.ubuntu.com precise-updates Release.gpg [198 B]                                                                               
Get:21 http://security.ubuntu.com precise-security Release [49.6 kB]                                                                                  
Get:22 http://64.repository.backtrack-linux.org revolution Release.gpg [198 B]                                                                        
Get:23 http://ppa.launchpad.net precise Release [11.9 kB]                                                                                             
Get:24 http://extras.ubuntu.com precise/main i386 Packages [10.8 kB]                                                                                  
Get:25 http://deb.playonlinux.com precise/main i386 Packages [542 B]                                                                                  
Ign http://deb.playonlinux.com precise/main TranslationIndex                                                                                          
Get:26 http://http.kali.org kali Release.gpg [836 B]                                                                                                  
Get:27 http://ppa.launchpad.net precise Release [11.9 kB]                                                                                             
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                                                            
Get:28 http://source.repository.backtrack-linux.org revolution Release [13.5 kB]                                                                      
Get:29 http://ppa.launchpad.net precise/main Sources [51.8 kB]                                                                                        
Get:30 http://all.repository.backtrack-linux.org revolution Release [13.5 kB]                                                                         
Get:31 http://in.archive.ubuntu.com precise-backports Release.gpg [198 B]                                                                             
Get:32 http://64.repository.backtrack-linux.org revolution Release [4,840 B]                                                                          
Get:33 http://security.ubuntu.com precise-security/main Sources [100 kB]                                                                              
Get:34 http://ppa.launchpad.net precise/main amd64 Packages [45.8 kB]                                                                                 
Get:35 http://in.archive.ubuntu.com precise Release [49.6 kB]                                                                                         
Ign http://dl.google.com stable/main Translation-en_IN                                                                                                
Get:36 http://ppa.launchpad.net precise/main i386 Packages [45.7 kB]                                                                                  
Get:37 http://source.repository.backtrack-linux.org revolution/main amd64 Packages [14 B]                                                             
Get:38 http://64.repository.backtrack-linux.org revolution/main amd64 Packages [4,463 kB]                                                             
Get:39 http://all.repository.backtrack-linux.org revolution/main amd64 Packages [3,256 kB]                                                            
Get:40 http://in.archive.ubuntu.com precise-updates Release [49.6 kB]                                                                                 
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                            
Get:41 http://ppa.launchpad.net precise/main Sources [7,317 B]                                                                                        
Get:42 http://source.repository.backtrack-linux.org revolution/microverse amd64 Packages [14 B]                                                       
Ign http://deb.playonlinux.com precise/main Translation-en_IN                                                                                         
Get:43 http://ppa.launchpad.net precise/main amd64 Packages [7,167 B]                                                                                 
Get:44 http://security.kali.org kali/updates Release.gpg [836 B]                                                                                      
Ign http://deb.playonlinux.com precise/main Translation-en                                                                                            
Get:45 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]                                                                       
Get:46 http://http.kali.org kali Release [21.1 kB]                                                                                                    
Get:47 http://ppa.launchpad.net precise/main i386 Packages [7,004 B]                                                                                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                            
Get:48 http://ppa.launchpad.net precise/main Sources [6,403 B]                                                                                        
Get:49 http://security.ubuntu.com precise-security/universe Sources [30.9 kB]                                                                         
Get:50 http://source.repository.backtrack-linux.org revolution/non-free amd64 Packages [14 B]                                                         
Get:51 http://ppa.launchpad.net precise/main amd64 Packages [7,498 B]                                                                                 
Get:52 http://security.kali.org kali/updates Release [11.0 kB]                                                                                        
Get:53 http://ppa.launchpad.net precise/main i386 Packages [7,486 B]                                                                                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                            
Get:54 http://source.repository.backtrack-linux.org revolution/testing amd64 Packages [84.6 kB]                                                       
Get:55 http://security.ubuntu.com precise-security/multiverse Sources [1,789 B]                                                                       
Get:56 http://security.ubuntu.com precise-security/main amd64 Packages [373 kB]                                                                       
Ign http://extras.ubuntu.com precise/main Translation-en_IN                                                                                           
Ign http://extras.ubuntu.com precise/main Translation-en                                                                                              
Get:57 http://in.archive.ubuntu.com precise-backports Release [49.6 kB]                                                                               
Get:58 http://source.repository.backtrack-linux.org revolution/main i386 Packages [14 B]                                                              
Get:59 http://source.repository.backtrack-linux.org revolution/microverse i386 Packages [14 B]                                                        
Get:60 http://source.repository.backtrack-linux.org revolution/non-free i386 Packages [14 B]                                                          
Get:61 http://source.repository.backtrack-linux.org revolution/testing i386 Packages [84.6 kB]                                                        
Get:62 http://in.archive.ubuntu.com precise/main Sources [934 kB]                                                                                     
Get:63 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]                                                                
Get:64 http://security.ubuntu.com precise-security/universe amd64 Packages [91.6 kB]                                                                  
Ign http://ppa.launchpad.net precise/main Translation-en_IN                                                                                           
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                              
Ign http://ppa.launchpad.net precise/main Translation-en_IN                                                                                           
Ign http://source.repository.backtrack-linux.org revolution/main TranslationIndex                                                                     
Get:65 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,446 B]                                                                
Get:66 http://security.ubuntu.com precise-security/main i386 Packages [399 kB]                                                                        
Ign http://source.repository.backtrack-linux.org revolution/microverse TranslationIndex                                                               
Ign http://source.repository.backtrack-linux.org revolution/non-free TranslationIndex                                                                 
Ign http://source.repository.backtrack-linux.org revolution/testing TranslationIndex                                                                  
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                              
Ign http://ppa.launchpad.net precise/main Translation-en_IN                                                                                           
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                              
Get:67 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]                                                                 
Get:68 http://http.kali.org kali/main Sources [7,528 kB]                                                                                              
Get:69 http://in.archive.ubuntu.com precise/restricted Sources [5,470 B]                                                                              
Get:70 http://in.archive.ubuntu.com precise/universe Sources [5,019 kB]                                                                               
Ign http://source.repository.backtrack-linux.org revolution/main Translation-en_IN                                                                    
Ign http://source.repository.backtrack-linux.org revolution/main Translation-en                                                                       
Ign http://source.repository.backtrack-linux.org revolution/microverse Translation-en_IN                                                              
Ign http://source.repository.backtrack-linux.org revolution/microverse Translation-en                                                                 
Ign http://source.repository.backtrack-linux.org revolution/non-free Translation-en_IN                                                                
Ign http://source.repository.backtrack-linux.org revolution/non-free Translation-en                                                                   
Get:71 http://security.ubuntu.com precise-security/universe i386 Packages [96.4 kB]                                                                   
Ign http://source.repository.backtrack-linux.org revolution/testing Translation-en_IN                                                                 
Get:72 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,646 B]                                                                 
Get:73 http://all.repository.backtrack-linux.org revolution/microverse amd64 Packages [2,589 B]                                                       
Get:74 http://all.repository.backtrack-linux.org revolution/non-free amd64 Packages [14 B]                                                            
Get:75 http://all.repository.backtrack-linux.org revolution/testing amd64 Packages [77.0 kB]                                                          
Ign http://dl.google.com stable/main Translation-en                                                                                                   
Get:76 http://all.repository.backtrack-linux.org revolution/main i386 Packages [3,256 kB]                                                             
Ign http://source.repository.backtrack-linux.org revolution/testing Translation-en                                                                    
Get:77 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]                                                                       
Get:78 http://security.ubuntu.com precise-security/multiverse TranslationIndex [72 B]                                                                 
Get:79 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]                                                                 
Get:80 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]                                                                   
Get:81 http://security.kali.org kali/updates/main Sources [93.2 kB]                                                                                   
Get:82 http://security.ubuntu.com precise-security/main Translation-en [174 kB]                                                                       
Get:83 http://security.ubuntu.com precise-security/multiverse Translation-en [1,299 B]                                                                
Get:84 http://security.ubuntu.com precise-security/restricted Translation-en [1,253 B]                                                                
Get:85 http://security.ubuntu.com precise-security/universe Translation-en [56.6 kB]                                                                  
Get:86 http://64.repository.backtrack-linux.org revolution/microverse amd64 Packages [2,766 B]                                                        
Get:87 http://64.repository.backtrack-linux.org revolution/non-free amd64 Packages [14 B]                                                             
Get:88 http://64.repository.backtrack-linux.org revolution/testing amd64 Packages [65.2 kB]                                                           
Get:89 http://http.kali.org kali/non-free Sources [117 kB]                                                                                            
Get:90 http://security.kali.org kali/updates/contrib Sources [20 B]                                                                                   
Get:91 http://in.archive.ubuntu.com precise/multiverse Sources [155 kB]                                                                               
Get:92 http://http.kali.org kali/contrib Sources [55.5 kB]                                                                                            
Get:93 http://security.kali.org kali/updates/non-free Sources [20 B]                                                                                  
Get:94 http://in.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]                                                                            
Get:95 http://all.repository.backtrack-linux.org revolution/microverse i386 Packages [2,589 B]                                                        
Get:96 http://all.repository.backtrack-linux.org revolution/non-free i386 Packages [14 B]                                                             
Get:97 http://all.repository.backtrack-linux.org revolution/testing i386 Packages [87.9 kB]                                                           
Ign http://all.repository.backtrack-linux.org revolution/main TranslationIndex                                                                        
Ign http://all.repository.backtrack-linux.org revolution/microverse TranslationIndex                                                                  
Ign http://all.repository.backtrack-linux.org revolution/non-free TranslationIndex                                                                    
Ign http://all.repository.backtrack-linux.org revolution/testing TranslationIndex                                                                     
Get:98 http://in.archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]                                                                       
Get:99 http://in.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB]                                                                        
Ign http://all.repository.backtrack-linux.org revolution/main Translation-en_IN                                                                       
Ign http://all.repository.backtrack-linux.org revolution/main Translation-en                                                                          
Ign http://all.repository.backtrack-linux.org revolution/microverse Translation-en_IN                                                                 
Ign http://all.repository.backtrack-linux.org revolution/microverse Translation-en                                                                    
Ign http://all.repository.backtrack-linux.org revolution/non-free Translation-en_IN                                                                   
Ign http://all.repository.backtrack-linux.org revolution/non-free Translation-en                                                                      
Get:100 http://in.archive.ubuntu.com precise/multiverse amd64 Packages [119 kB]                                                                       
Ign http://all.repository.backtrack-linux.org revolution/testing Translation-en_IN                                                                    
Ign http://all.repository.backtrack-linux.org revolution/testing Translation-en                                                                       
Get:101 http://in.archive.ubuntu.com precise/main i386 Packages [1,274 kB]                                                                            
Get:102 http://in.archive.ubuntu.com precise/restricted i386 Packages [8,431 B]                                                                       
Get:103 http://in.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]                                                                        
Get:104 http://in.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]                                                                        
Get:105 http://in.archive.ubuntu.com precise/main TranslationIndex [3,706 B]                                                                          
Get:106 http://in.archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B]                                                                    
Get:107 http://in.archive.ubuntu.com precise/restricted TranslationIndex [2,596 B]                                                                    
Get:108 http://in.archive.ubuntu.com precise/universe TranslationIndex [2,922 B]                                                                      
Get:109 http://in.archive.ubuntu.com precise-updates/main Sources [452 kB]                                                                            
Get:110 http://in.archive.ubuntu.com precise-updates/restricted Sources [8,028 B]                                                                     
Get:111 http://in.archive.ubuntu.com precise-updates/universe Sources [105 kB]                                                                        
Get:112 http://in.archive.ubuntu.com precise-updates/multiverse Sources [8,900 B]                                                                     
Get:113 http://in.archive.ubuntu.com precise-updates/main amd64 Packages [759 kB]                                                                     
Get:114 http://in.archive.ubuntu.com precise-updates/restricted amd64 Packages [12.2 kB]                                                              
Get:115 http://in.archive.ubuntu.com precise-updates/universe amd64 Packages [237 kB]                                                                 
Get:116 http://in.archive.ubuntu.com precise-updates/multiverse amd64 Packages [15.3 kB]                                                              
Get:117 http://in.archive.ubuntu.com precise-updates/main i386 Packages [783 kB]                                                                      
Get:118 http://in.archive.ubuntu.com precise-updates/restricted i386 Packages [12.2 kB]                                                               
Get:119 http://in.archive.ubuntu.com precise-updates/universe i386 Packages [242 kB]                                                                  
Get:120 http://in.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]                                                               
Get:121 http://in.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]                                                                  
Get:122 http://in.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]                                                            
Get:123 http://in.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]                                                            
Get:124 http://in.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]                                                              
Get:125 http://in.archive.ubuntu.com precise-backports/main Sources [4,850 B]                                                                         
Get:126 http://in.archive.ubuntu.com precise-backports/restricted Sources [14 B]                                                                      
Get:127 http://in.archive.ubuntu.com precise-backports/universe Sources [36.4 kB]                                                                     
Get:128 http://in.archive.ubuntu.com precise-backports/multiverse Sources [5,311 B]                                                                   
Get:129 http://in.archive.ubuntu.com precise-backports/main amd64 Packages [6,183 B]                                                                  
Get:130 http://in.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]                                                               
Get:131 http://in.archive.ubuntu.com precise-backports/universe amd64 Packages [38.2 kB]                                                              
Get:132 http://in.archive.ubuntu.com precise-backports/multiverse amd64 Packages [5,206 B]                                                            
Get:133 http://in.archive.ubuntu.com precise-backports/main i386 Packages [6,182 B]                                                                   
Get:134 http://in.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]                                                                
Get:135 http://in.archive.ubuntu.com precise-backports/universe i386 Packages [38.0 kB]                                                               
Get:136 http://in.archive.ubuntu.com precise-backports/multiverse i386 Packages [5,178 B]                                                             
Get:137 http://in.archive.ubuntu.com precise-backports/main TranslationIndex [72 B]                                                                   
Get:138 http://in.archive.ubuntu.com precise-backports/multiverse TranslationIndex [72 B]                                                             
Get:139 http://in.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]                                                             
Get:140 http://in.archive.ubuntu.com precise-backports/universe TranslationIndex [73 B]                                                               
Get:141 http://in.archive.ubuntu.com precise/main Translation-en [726 kB]                                                                             
Get:142 http://in.archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]                                                                      
Get:143 http://in.archive.ubuntu.com precise/restricted Translation-en [2,395 B]                                                                      
Get:144 http://in.archive.ubuntu.com precise/universe Translation-en [3,341 kB]                                                                       
Get:145 http://in.archive.ubuntu.com precise-updates/main Translation-en [339 kB]                                                                     
Get:146 http://in.archive.ubuntu.com precise-updates/multiverse Translation-en [9,010 B]                                                              
Get:147 http://in.archive.ubuntu.com precise-updates/restricted Translation-en [2,988 B]                                                              
Get:148 http://in.archive.ubuntu.com precise-updates/universe Translation-en [138 kB]                                                                 
Get:149 http://in.archive.ubuntu.com precise-backports/main Translation-en [5,562 B]                                                                  
Get:150 http://in.archive.ubuntu.com precise-backports/multiverse Translation-en [4,610 B]                                                            
Get:151 http://in.archive.ubuntu.com precise-backports/restricted Translation-en [14 B]                                                               
Get:152 http://in.archive.ubuntu.com precise-backports/universe Translation-en [28.0 kB]                                                              
Fetched 47.1 MB in 3min 17s (239 kB/s)                                                                                                                
W: Failed to fetch http://64.repository.backtrack-linux.org/dists/revolution/Release  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

root@Keshav:/var/lib/apt# 

```


Some of them are still appearing !

---

### Post by thekeshav on 2014-03-21
Thanks for letting me to know !

---

### Post by ernie4chan on 2014-03-21
I was encountering the same problem! Thanks for the help!

---

