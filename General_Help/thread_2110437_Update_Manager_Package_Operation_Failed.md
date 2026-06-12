---
title: "Update Manager Package Operation Failed"
date: 2013-01-30
forum: General Help
---

### Post by vchapman on 2013-01-30
The update process no longer works. Here is what I get:

```


nstallArchives() failed:  Extracting templates from packages: 93%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 93%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 93%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 93%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
dpkg: error: parsing file '/var/lib/dpkg/available' near line 0: 
 newline in field name `../../../../../share/pyshared/gnome_sudoku/gtk_goodies/dialog_extras.py' 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2) 


```Please help to fix this. Thank you.

---

### Post by raja.genupula on 2013-01-30
try with 
```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get update
```
then try again.

---

### Post by vchapman on 2013-01-30
> **raja.genupula said:**
> try with 
```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get update
```
then try again.
I ran the code  that you suggest (twice in fact) and I still get the same error when I try to apply the updates.

---

### Post by vchapman on 2013-01-31
> **raja.genupula said:**
> try with 
```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get update
```then try again.

I did this:

```


victor@ubuntu-laptop:~$ sudo apt-get autoremove
[sudo] password for victor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 33 not upgraded.
victor@ubuntu-laptop:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
victor@ubuntu-laptop:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Ign http://extras.ubuntu.com precise InRelease                                 
Hit http://dl.google.com stable Release.gpg                                    
Ign http://archive.canonical.com precise InRelease                   
Ign http://archive.canonical.com precise InRelease                   
Ign http://ca.archive.ubuntu.com precise InRelease                   
Ign http://ca.archive.ubuntu.com precise-updates InRelease           
Ign http://ca.archive.ubuntu.com precise-security InRelease          
Hit http://dl.google.com stable Release                              
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://dl.google.com stable/main amd64 Packages                  
Hit http://archive.canonical.com precise Release.gpg                 
Hit http://ca.archive.ubuntu.com precise Release.gpg                 
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://extras.ubuntu.com precise Release                                   
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://archive.canonical.com precise Release.gpg                 
Get:1 http://ca.archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Get:2 http://ca.archive.ubuntu.com precise-security Release.gpg [198 B]        
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://ca.archive.ubuntu.com precise Release                               
Hit http://archive.canonical.com precise Release                               
Get:3 http://ca.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Ign http://dl.google.com stable/main Translation-en_CA                         
Get:4 http://ca.archive.ubuntu.com precise-security Release [49.6 kB]          
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ca.archive.ubuntu.com precise/main Sources                          
Hit http://ca.archive.ubuntu.com precise/restricted Sources
Hit http://ca.archive.ubuntu.com precise/universe Sources
Hit http://ca.archive.ubuntu.com precise/multiverse Sources           
Hit http://ca.archive.ubuntu.com precise/main amd64 Packages          
Hit http://ca.archive.ubuntu.com precise/restricted amd64 Packages    
Hit http://ca.archive.ubuntu.com precise/universe amd64 Packages      
Hit http://ca.archive.ubuntu.com precise/multiverse amd64 Packages    
Hit http://ca.archive.ubuntu.com precise/main i386 Packages           
Hit http://ca.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://ca.archive.ubuntu.com precise/universe i386 Packages       
Hit http://ca.archive.ubuntu.com precise/multiverse i386 Packages     
Hit http://ca.archive.ubuntu.com precise/main TranslationIndex        
Hit http://ca.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://ca.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://ca.archive.ubuntu.com precise/universe TranslationIndex
Get:5 http://ca.archive.ubuntu.com precise-updates/main Sources [218 kB]
Ign http://extras.ubuntu.com precise/main Translation-en_CA                  
Ign http://extras.ubuntu.com precise/main Translation-en                     
Ign http://archive.canonical.com precise/partner Translation-en_CA
Ign http://archive.canonical.com precise/partner Translation-en
Ign http://archive.canonical.com precise/partner Translation-en_CA
Ign http://archive.canonical.com precise/partner Translation-en
Get:6 http://ca.archive.ubuntu.com precise-updates/restricted Sources [5,118 B]
Get:7 http://ca.archive.ubuntu.com precise-updates/universe Sources [76.4 kB]
Get:8 http://ca.archive.ubuntu.com precise-updates/multiverse Sources [4,737 B]
Get:9 http://ca.archive.ubuntu.com precise-updates/main amd64 Packages [480 kB]
Get:10 http://ca.archive.ubuntu.com precise-updates/restricted amd64 Packages [9,531 B]
Get:11 http://ca.archive.ubuntu.com precise-updates/universe amd64 Packages [174 kB]
Get:12 http://ca.archive.ubuntu.com precise-updates/multiverse amd64 Packages [9,425 B]
Get:13 http://ca.archive.ubuntu.com precise-updates/main i386 Packages [489 kB]
Get:14 http://ca.archive.ubuntu.com precise-updates/restricted i386 Packages [9,483 B]
Get:15 http://ca.archive.ubuntu.com precise-updates/universe i386 Packages [176 kB]
Get:16 http://ca.archive.ubuntu.com precise-updates/multiverse i386 Packages [10.4 kB]
Hit http://ca.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://ca.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://ca.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://ca.archive.ubuntu.com precise-updates/universe TranslationIndex     
Get:17 http://ca.archive.ubuntu.com precise-security/main Sources [62.8 kB]    
Get:18 http://ca.archive.ubuntu.com precise-security/restricted Sources [1,950 B]
Get:19 http://ca.archive.ubuntu.com precise-security/universe Sources [20.0 kB]
Get:20 http://ca.archive.ubuntu.com precise-security/multiverse Sources [1,379 B]
Get:21 http://ca.archive.ubuntu.com precise-security/main amd64 Packages [222 kB]
Get:22 http://ca.archive.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:23 http://ca.archive.ubuntu.com precise-security/universe amd64 Packages [62.4 kB]
Get:24 http://ca.archive.ubuntu.com precise-security/multiverse amd64 Packages [2,184 B]
Get:25 http://ca.archive.ubuntu.com precise-security/main i386 Packages [229 kB]
Get:26 http://ca.archive.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:27 http://ca.archive.ubuntu.com precise-security/universe i386 Packages [63.7 kB]
Get:28 http://ca.archive.ubuntu.com precise-security/multiverse i386 Packages [2,366 B]
Hit http://ca.archive.ubuntu.com precise-security/main TranslationIndex        
Hit http://ca.archive.ubuntu.com precise-security/multiverse TranslationIndex  
Hit http://ca.archive.ubuntu.com precise-security/restricted TranslationIndex  
Hit http://ca.archive.ubuntu.com precise-security/universe TranslationIndex    
Hit http://ca.archive.ubuntu.com precise/main Translation-en_CA                
Hit http://ca.archive.ubuntu.com precise/main Translation-en                   
Hit http://ca.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://ca.archive.ubuntu.com precise/restricted Translation-en             
Hit http://ca.archive.ubuntu.com precise/universe Translation-en_CA            
Hit http://ca.archive.ubuntu.com precise/universe Translation-en               
Hit http://ca.archive.ubuntu.com precise-updates/main Translation-en_CA        
Hit http://ca.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://ca.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://ca.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://ca.archive.ubuntu.com precise-updates/universe Translation-en_CA    
Hit http://ca.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://ca.archive.ubuntu.com precise-security/main Translation-en          
Hit http://ca.archive.ubuntu.com precise-security/multiverse Translation-en    
Hit http://ca.archive.ubuntu.com precise-security/restricted Translation-en    
Hit http://ca.archive.ubuntu.com precise-security/universe Translation-en      
Fetched 2,438 kB in 14s (165 kB/s)                                             
Reading package lists... Done



```Then I ran the update manager and got:

```


installArchives() failed:  Extracting templates from packages: 90%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 90%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 90%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 90%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
dpkg: error: parsing file '/var/lib/dpkg/available' near line 0: 
 newline in field name `../../../../../share/pyshared/gnome_sudoku/gtk_goodies/dialog_extras.py' 
Error in function:  



```So the proposed solution does not appear to have worked. What should I try next. Thanks.

---

### Post by ibjsb4 on 2013-01-31
Some possible solutions here.

[http://www.google.com/search?client=ubuntu&channel=fs&q=error%3A+parsing+file+%27%2Fvar%2Flib%2Fdpkg&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=error%3A+parsing+file+%27%2Fvar%2Flib%2Fdpkg&ie=utf-8&oe=utf-8)

---

### Post by vchapman on 2013-01-31
> **ibjsb4 said:**
> Some possible solutions here.

[http://www.google.com/search?client=ubuntu&channel=fs&q=error%3A+parsing+file+%27%2Fvar%2Flib%2Fdpkg&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=error%3A+parsing+file+%27%2Fvar%2Flib%2Fdpkg&ie=utf-8&oe=utf-8)
Thank you. This worked for me:

[http://askubuntu.com/questions/55099/dpkg-error-parsing-file-var-lib-dpkg-available-near-line-0](http://askubuntu.com/questions/55099/dpkg-error-parsing-file-var-lib-dpkg-available-near-line-0)

---

### Post by ibjsb4 on 2013-01-31
Nice :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

