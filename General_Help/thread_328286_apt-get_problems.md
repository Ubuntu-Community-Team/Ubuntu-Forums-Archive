---
title: "apt-get problems"
date: 2006-12-30
forum: General Help
---

### Post by woopud on 2006-12-30
I have a lot of problems with downloading and installing updates, this is what i get:

```
woopud@woopud-desktop:~$ sudo apt-get update
Get:1 http://www.getautomatix.com edgy Release.gpg [189B]
Ign http://www.getautomatix.com edgy/main Translation-en_US                    
Get:2 http://www.getautomatix.com edgy Release [4147B]                         
Get:3 http://www.getautomatix.com edgy/main Packages [571B]                    
Ign http://security.ubuntu.com edgy-security Release.gpg                       
Ign http://security.ubuntu.com edgy-security/main Translation-en_US            
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US      
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US        
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US      
Ign http://security.ubuntu.com edgy-security Release                           
Ign http://security.ubuntu.com edgy-security/main Packages                     
Ign http://security.ubuntu.com edgy-security/restricted Packages               
Ign http://security.ubuntu.com edgy-security/universe Packages                 
Ign http://security.ubuntu.com edgy-security/multiverse Packages               
Ign http://security.ubuntu.com edgy-security/main Sources                      
Ign http://security.ubuntu.com edgy-security/restricted Sources                
Ign http://security.ubuntu.com edgy-security/universe Sources                  
Ign http://security.ubuntu.com edgy-security/multiverse Sources                
Err http://security.ubuntu.com edgy-security/main Packages                     
  404 Not Found
Err http://security.ubuntu.com edgy-security/restricted Packages               
  404 Not Found
Err http://security.ubuntu.com edgy-security/universe Packages                 
  404 Not Found
Err http://security.ubuntu.com edgy-security/multiverse Packages               
  404 Not Found
Err http://security.ubuntu.com edgy-security/main Sources                      
  404 Not Found
Err http://security.ubuntu.com edgy-security/restricted Sources                
  404 Not Found
Err http://security.ubuntu.com edgy-security/universe Sources                  
  404 Not Found
Err http://security.ubuntu.com edgy-security/multiverse Sources                
  404 Not Found
Err http://us.archive.ubuntu.com edgy Release.gpg                              
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.canonical.com dapper-commercial Release.gpg                 
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy/main Translation-en_US                   
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.canonical.com dapper-commercial/main Translation-en_US      
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy/restricted Translation-en_US             
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy/universe Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy/multiverse Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy-updates/multiverse Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy-backports Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy-backports/main Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy-backports/restricted Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy-backports/universe Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy-backports/multiverse Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy-security Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy-security/main Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy-security/restricted Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy-security/universe Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com edgy-security/multiverse Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Fetched 4907B in 36m45s (2B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/i18n/Translation-en_US.bz2  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz  404 Not Found
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
woopud@woopud-desktop:~$ 


```

Bert

---

### Post by taurus on 2006-12-30
Let's have a look at your /etc/apt/sources.list...

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by woopud on 2006-12-30
Here it is:

```
woopud@woopud-desktop:~$ sudo cat /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END
woopud@woopud-desktop:~$ 


```

Bert

---

### Post by angkor on 2006-12-30
You can try changing all the 'us' prefixes to 'nl'.

```
gksudo gedit /etc/apt/sources.list
```

Make the changes, save and close and try 'sudo apt-get update again'.

There's also one 'dapper' repository in the automatix part. I wouldn't use that.

---

### Post by taurus on 2006-12-30
Maybe the [http://security.ubuntu.com/](http://security.ubuntu.com/) site is currently down!  Try to run it again tomorrow and see what happens...

---

### Post by angkor on 2006-12-30
> **taurus said:**
> Maybe the [http://security.ubuntu.com/](http://security.ubuntu.com/) site is currently down!  Try to run it again tomorrow and see what happens...

Strange, it works fine for me.

---

### Post by woopud on 2006-12-30
This is what I get then:

```
woopud@woopud-desktop:~$ gksudo gedit /etc/apt/sources.list
(gedit:15971): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
woopud@woopud-desktop:~$ sudo apt-get update
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]              
Ign http://security.ubuntu.com edgy-security/main Translation-en_US            
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US      
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US        
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US      
Hit http://security.ubuntu.com edgy-security Release                           
Hit http://security.ubuntu.com edgy-security/main Packages                     
Hit http://security.ubuntu.com edgy-security/restricted Packages               
Hit http://security.ubuntu.com edgy-security/universe Packages                 
Hit http://security.ubuntu.com edgy-security/multiverse Packages               
Hit http://security.ubuntu.com edgy-security/main Sources                      
Hit http://security.ubuntu.com edgy-security/restricted Sources                
Hit http://security.ubuntu.com edgy-security/universe Sources                  
Hit http://security.ubuntu.com edgy-security/multiverse Sources                
Err http://us.archive.ubuntu.com edgy-backports Release.gpg                    
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://nl.archive.ubuntu.com edgy Release.gpg                              
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://archive.canonical.com edgy-commercial Release.gpg                   
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err http://www.getautomatix.com edgy Release.gpg                               
  Could not connect to www.getautomatix.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy-backports/main Translation-en_US         
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://nl.archive.ubuntu.com edgy/main Translation-en_US                   
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://archive.canonical.com edgy-commercial/main Translation-en_US        
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err http://www.getautomatix.com edgy/main Translation-en_US                    
  Could not connect to www.getautomatix.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com edgy-backports/restricted Translation-en_US   
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://nl.archive.ubuntu.com edgy/restricted Translation-en_US             
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://us.archive.ubuntu.com edgy-backports/universe Translation-en_US     
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://nl.archive.ubuntu.com edgy/universe Translation-en_US               
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://us.archive.ubuntu.com edgy-backports/multiverse Translation-en_US   
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://nl.archive.ubuntu.com edgy/multiverse Translation-en_US             
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://us.archive.ubuntu.com edgy-security Release.gpg                     
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://nl.archive.ubuntu.com edgy-updates Release.gpg                      
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://us.archive.ubuntu.com edgy-security/main Translation-en_US          
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://nl.archive.ubuntu.com edgy-updates/main Translation-en_US           
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://us.archive.ubuntu.com edgy-security/restricted Translation-en_US    
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://nl.archive.ubuntu.com edgy-updates/restricted Translation-en_US     
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://us.archive.ubuntu.com edgy-security/universe Translation-en_US      
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://nl.archive.ubuntu.com edgy-updates/universe Translation-en_US       
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://us.archive.ubuntu.com edgy-security/multiverse Translation-en_US    
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://nl.archive.ubuntu.com edgy-updates/multiverse Translation-en_US     
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Ign http://nl.archive.ubuntu.com edgy Release         
Ign http://nl.archive.ubuntu.com edgy-updates Release 
Ign http://nl.archive.ubuntu.com edgy/main Packages   
Ign http://nl.archive.ubuntu.com edgy/restricted Packages
Ign http://nl.archive.ubuntu.com edgy/universe Packages
Ign http://nl.archive.ubuntu.com edgy/multiverse Packages
Ign http://nl.archive.ubuntu.com edgy/main Sources    
Ign http://nl.archive.ubuntu.com edgy/restricted Sources
Ign http://nl.archive.ubuntu.com edgy/universe Sources
Ign http://nl.archive.ubuntu.com edgy/multiverse Sources
Ign http://nl.archive.ubuntu.com edgy-updates/main Packages
Ign http://nl.archive.ubuntu.com edgy-updates/restricted Packages
Ign http://nl.archive.ubuntu.com edgy-updates/universe Packages
Ign http://nl.archive.ubuntu.com edgy-updates/multiverse Packages
Ign http://nl.archive.ubuntu.com edgy-updates/main Sources
Ign http://nl.archive.ubuntu.com edgy-updates/restricted Sources
Ign http://nl.archive.ubuntu.com edgy-updates/universe Sources
Ign http://nl.archive.ubuntu.com edgy-updates/multiverse Sources
Err http://nl.archive.ubuntu.com edgy/main Packages   
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://nl.archive.ubuntu.com edgy/restricted Packages
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://nl.archive.ubuntu.com edgy/universe Packages
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://nl.archive.ubuntu.com edgy/multiverse Packages
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://nl.archive.ubuntu.com edgy/main Sources    
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://nl.archive.ubuntu.com edgy/restricted Sources
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://nl.archive.ubuntu.com edgy/universe Sources
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://nl.archive.ubuntu.com edgy/multiverse Sources
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://nl.archive.ubuntu.com edgy-updates/main Packages
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://nl.archive.ubuntu.com edgy-updates/restricted Packages
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://nl.archive.ubuntu.com edgy-updates/universe Packages
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://nl.archive.ubuntu.com edgy-updates/multiverse Packages
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://nl.archive.ubuntu.com edgy-updates/main Sources
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://nl.archive.ubuntu.com edgy-updates/restricted Sources
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://nl.archive.ubuntu.com edgy-updates/universe Sources
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Err http://nl.archive.ubuntu.com edgy-updates/multiverse Sources
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Fetched 191B in 1h28m0s (0B/s)                        
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://www.getautomatix.com/apt/dists/edgy/Release.gpg  Could not connect to www.getautomatix.com:80 (1.0.0.0), connection timed out
Failed to fetch http://www.getautomatix.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2  Could not connect to www.getautomatix.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.canonical.com/ubuntu/dists/edgy-commercial/Release.gpg  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/i18n/Translation-en_US.bz2  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
woopud@woopud-desktop:~$ 


```

---

### Post by angkor on 2006-12-31
Maybe you're having the same problem as this thread starter:

[http://www.ubuntuforums.org/showthread.php?t=327980](http://www.ubuntuforums.org/showthread.php?t=327980)

---

