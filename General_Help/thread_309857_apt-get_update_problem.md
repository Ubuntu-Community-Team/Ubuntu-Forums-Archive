---
title: "apt-get update problem"
date: 2006-11-30
forum: General Help
---

### Post by woopud on 2006-11-30
For some reason I have problems when trying to apt-get update.

```

woopud@woopud-laptop:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
woopud@woopud-laptop:~$ 

```

What to do ?
Bert

---

### Post by wieman01 on 2006-11-30
I guess a reboot should do...

---

### Post by woopud on 2006-11-30
Nope, didn't change a thing.

Bert

---

### Post by xopher on 2006-11-30
Make sure apt is the only process using the resource at the moment - close all instances of eg. synaptic, dpkg, aptitude before trying again.

---

### Post by woopud on 2006-11-30
Well, nothing else was running at the time.

```

woopud@woopud-laptop:~$ sudo apt-get update
Get:1 http://www.getautomatix.com edgy Release.gpg [189B]                      
Ign http://www.getautomatix.com edgy/main Translation-en_US                    
Get:2 http://security.ubuntu.com edgy-security Release.gpg [191B]              
Ign http://security.ubuntu.com edgy-security/main Translation-en_US            
Hit http://www.getautomatix.com edgy Release                                   
Get:3 http://archive.ubuntu.com edgy-backports Release.gpg [191B]              
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US            
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US      
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US        
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US      
Hit http://security.ubuntu.com edgy-security Release                           
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US      
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US        
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US      
Get:4 http://archive.ubuntu.com edgy-updates Release.gpg [191B]                
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_US              
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_US          
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_US        
Get:5 http://archive.ubuntu.com edgy-security Release.gpg [191B]               
Ign http://archive.ubuntu.com edgy-security/main Translation-en_US             
Hit http://www.getautomatix.com edgy/main Packages                             
Ign http://archive.ubuntu.com edgy-security/restricted Translation-en_US       
Hit http://security.ubuntu.com edgy-security/main Packages                     
Ign http://archive.ubuntu.com edgy-security/universe Translation-en_US         
Ign http://archive.ubuntu.com edgy-security/multiverse Translation-en_US 
Get:6 http://archive.ubuntu.com edgy Release.gpg [191B]                        
Ign http://archive.ubuntu.com edgy/main Translation-en_US                      
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US          
Ign http://archive.ubuntu.com edgy/universe Translation-en_US            
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US          
Hit http://security.ubuntu.com edgy-security/restricted Packages               
Get:7 http://security.ubuntu.com edgy-security/universe Packages [10.5kB]      
Hit http://archive.ubuntu.com edgy-backports Release                           
Hit http://archive.ubuntu.com edgy-updates Release                             
Hit http://archive.ubuntu.com edgy-security Release                            
Hit http://archive.ubuntu.com edgy Release                                     
Get:8 http://security.ubuntu.com edgy-security/multiverse Packages [2234B]     
Hit http://security.ubuntu.com edgy-security/main Sources                      
Hit http://security.ubuntu.com edgy-security/restricted Sources                
Get:9 http://security.ubuntu.com edgy-security/universe Sources [1297B]        
Get:10 http://security.ubuntu.com edgy-security/multiverse Sources [14B]       
Hit http://archive.ubuntu.com edgy-backports/main Packages                     
Hit http://archive.ubuntu.com edgy-backports/restricted Packages               
Hit http://archive.ubuntu.com edgy-backports/universe Packages                 
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages               
Hit http://archive.ubuntu.com edgy-updates/main Packages                       
Hit http://archive.ubuntu.com edgy-updates/restricted Packages                 
Hit http://archive.ubuntu.com edgy-updates/universe Packages                   
Hit http://archive.ubuntu.com edgy-updates/multiverse Packages                 
Hit http://archive.ubuntu.com edgy-security/main Packages                      
Hit http://archive.ubuntu.com edgy-security/restricted Packages          
Hit http://archive.ubuntu.com edgy-security/universe Packages            
Hit http://archive.ubuntu.com edgy-security/multiverse Packages          
Hit http://archive.ubuntu.com edgy/main Packages                         
Hit http://archive.ubuntu.com edgy/restricted Packages                   
Hit http://archive.ubuntu.com edgy/universe Packages                     
Hit http://archive.ubuntu.com edgy/multiverse Packages                   
Err http://us.archive.ubuntu.com edgy Release.gpg                              
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy/main Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy/restricted Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy/universe Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy/multiverse Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com edgy-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com edgy-updates/multiverse Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign http://us.archive.ubuntu.com edgy-updates Release
Ign http://us.archive.ubuntu.com edgy-updates/main Packages
Ign http://us.archive.ubuntu.com edgy-updates/restricted Packages
Ign http://us.archive.ubuntu.com edgy-updates/universe Packages
Ign http://us.archive.ubuntu.com edgy-updates/multiverse Packages
Ign http://us.archive.ubuntu.com edgy-updates/main Sources
Ign http://us.archive.ubuntu.com edgy-updates/restricted Sources
Ign http://us.archive.ubuntu.com edgy-updates/universe Sources
Ign http://us.archive.ubuntu.com edgy-updates/multiverse Sources
Err http://us.archive.ubuntu.com edgy-updates/main Packages
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com edgy-updates/restricted Packages
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com edgy-updates/universe Packages
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com edgy-updates/multiverse Packages
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com edgy-updates/main Sources
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com edgy-updates/restricted Sources
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com edgy-updates/universe Sources
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com edgy-updates/multiverse Sources
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Fetched 14.2kB in 14m30s (16B/s)                   
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-amd64/Packages.gz  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-amd64/Packages.gz  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-amd64/Packages.gz  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-amd64/Packages.gz  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
woopud@woopud-laptop:~$ 


```

---

