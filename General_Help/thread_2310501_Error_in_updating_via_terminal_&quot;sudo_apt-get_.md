---
title: "Error in updating via terminal? &quot;sudo apt-get update&quot;"
date: 2016-01-19
forum: General Help
---

### Post by karthik31 on 2016-01-19
I visited all the forums still ain't getting any solutions for this
when i try to update using : ```
sudo apt-get update
```
It shows error like
```
sudo apt-get update
Get:1 http://ppa.launchpad.net trusty InRelease [15.5 kB]                      
Get:2 http://ppa.launchpad.net trusty InRelease [15.5 kB]                      
Get:3 http://ppa.launchpad.net trusty/main Sources [1,567 B]                   
Get:4 http://ppa.launchpad.net trusty/main amd64 Packages [3,376 B]            
Get:5 http://ppa.launchpad.net trusty/main i386 Packages [3,376 B]             
Get:6 http://ppa.launchpad.net trusty/main Translation-en [1,556 B]            
Get:7 http://ppa.launchpad.net trusty/main amd64 Packages [1,075 B]            
Get:8 http://ppa.launchpad.net trusty/main i386 Packages [1,077 B]             
Get:9 http://ppa.launchpad.net trusty/main Translation-en [868 B]              
Ign http://in.archive.ubuntu.com trusty InRelease                              
Ign http://archive.canonical.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:10 http://in.archive.ubuntu.com trusty-updates InRelease [64.4 kB]         
Get:11 http://archive.canonical.com trusty Release.gpg [933 B]                 
Get:12 http://extras.ubuntu.com trusty Release.gpg [72 B]                      
Get:13 http://archive.canonical.com trusty Release [9,359 B]                   
Get:14 http://extras.ubuntu.com trusty Release [11.9 kB]                       
Get:15 http://archive.canonical.com trusty/partner Sources [10.1 kB]           
Get:16 http://extras.ubuntu.com trusty/main Sources [14 B]                     
Get:17 http://in.archive.ubuntu.com trusty-backports InRelease [64.5 kB]       
Get:18 http://archive.canonical.com trusty/partner amd64 Packages [5,608 B]    
Get:19 http://extras.ubuntu.com trusty/main amd64 Packages [14 B]              
Get:20 http://archive.canonical.com trusty/partner i386 Packages [6,305 B]     
Get:21 http://extras.ubuntu.com trusty/main i386 Packages [14 B]               
Get:22 http://in.archive.ubuntu.com trusty-security InRelease [64.4 kB]        
Get:23 http://archive.canonical.com trusty/partner Translation-en [4,588 B]    
Get:24 http://in.archive.ubuntu.com trusty Release.gpg [933 B]                 
Get:25 http://in.archive.ubuntu.com trusty-updates/main Sources [248 kB]       
Get:26 http://in.archive.ubuntu.com trusty-updates/restricted Sources [5,359 B]
Get:27 http://in.archive.ubuntu.com trusty-updates/universe Sources [147 kB]   
Ign http://extras.ubuntu.com trusty/main Translation-en_IN                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:28 http://in.archive.ubuntu.com trusty-updates/multiverse Sources [5,161 B]
Get:29 http://in.archive.ubuntu.com trusty-updates/main amd64 Packages [689 kB]
Get:30 http://oss.oracle.com unstable InRelease                                
Ign http://oss.oracle.com unstable InRelease                                   
Get:31 http://oss.oracle.com unstable Release                                  
Get:32 http://in.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Ign http://oss.oracle.com unstable Release                                     
Get:33 http://in.archive.ubuntu.com trusty-updates/universe amd64 Packages [334 kB]
Get:34 http://oss.oracle.com unstable/main Sources                             
Get:35 http://oss.oracle.com unstable/non-free Sources                         
Get:36 http://in.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.0 kB]
Get:37 http://in.archive.ubuntu.com trusty-updates/main i386 Packages [663 kB] 
Get:38 http://oss.oracle.com unstable/non-free i386 Packages                   
Get:39 http://in.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:40 http://oss.oracle.com unstable/main Translation-en_IN                   
Get:41 http://in.archive.ubuntu.com trusty-updates/universe i386 Packages [335 kB]
Get:42 http://in.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.1 kB]
Get:43 http://in.archive.ubuntu.com trusty-updates/main Translation-en [348 kB]
Get:44 http://in.archive.ubuntu.com trusty-updates/multiverse Translation-en [6,832 B]
Get:45 http://in.archive.ubuntu.com trusty-updates/restricted Translation-en [3,699 B]
Get:46 http://in.archive.ubuntu.com trusty-updates/universe Translation-en [175 kB]
Get:47 http://in.archive.ubuntu.com trusty-backports/main Sources [8,221 B]    
Get:48 http://in.archive.ubuntu.com trusty-backports/restricted Sources [28 B] 
Get:49 http://in.archive.ubuntu.com trusty-backports/universe Sources [33.2 kB]
Get:50 http://in.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:51 http://in.archive.ubuntu.com trusty-backports/main amd64 Packages [9,402 B]
Get:52 http://in.archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:53 http://in.archive.ubuntu.com trusty-backports/universe amd64 Packages [39.8 kB]
Get:54 http://in.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,571 B]
Get:55 http://in.archive.ubuntu.com trusty-backports/main i386 Packages [9,411 B]
Get:56 http://in.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:57 http://in.archive.ubuntu.com trusty-backports/universe i386 Packages [39.8 kB]
Get:58 http://in.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Err http://oss.oracle.com unstable/non-free Sources                            
  HttpError404
Get:59 http://in.archive.ubuntu.com trusty-backports/main Translation-en [5,549 B]
Err http://oss.oracle.com unstable/main amd64 Packages                         
  HttpError404
Get:60 http://in.archive.ubuntu.com trusty-backports/multiverse Translation-en [1,215 B]
Err http://oss.oracle.com unstable/non-free amd64 Packages                     
  HttpError404
Get:61 http://in.archive.ubuntu.com trusty-backports/restricted Translation-en [14 B]
Ign http://oss.oracle.com unstable/main Translation-en_IN                      
Get:62 http://in.archive.ubuntu.com trusty-backports/universe Translation-en [34.6 kB]
Ign http://oss.oracle.com unstable/main Translation-en                         
Ign http://oss.oracle.com unstable/non-free Translation-en_IN                  
Ign http://oss.oracle.com unstable/non-free Translation-en                     
Get:63 http://in.archive.ubuntu.com trusty-security/main Sources [103 kB]      
Get:64 http://in.archive.ubuntu.com trusty-security/restricted Sources [4,035 B]
Get:65 http://in.archive.ubuntu.com trusty-security/universe Sources [32.7 kB] 
Get:66 http://in.archive.ubuntu.com trusty-security/multiverse Sources [2,357 B]
Get:67 http://in.archive.ubuntu.com trusty-security/main amd64 Packages [410 kB]
Get:68 http://in.archive.ubuntu.com trusty-security/restricted amd64 Packages [13.0 kB]
Get:69 http://in.archive.ubuntu.com trusty-security/universe amd64 Packages [123 kB]
Get:70 http://in.archive.ubuntu.com trusty-security/multiverse amd64 Packages [4,798 B]
Get:71 http://in.archive.ubuntu.com trusty-security/main i386 Packages [384 kB]
Get:72 http://in.archive.ubuntu.com trusty-security/restricted i386 Packages [12.7 kB]
Get:73 http://in.archive.ubuntu.com trusty-security/universe i386 Packages [123 kB]
Get:74 http://in.archive.ubuntu.com trusty-security/multiverse i386 Packages [4,955 B]
Get:75 http://in.archive.ubuntu.com trusty-security/main Translation-en [225 kB]
Get:76 http://in.archive.ubuntu.com trusty-security/multiverse Translation-en [2,437 B]
Get:77 http://in.archive.ubuntu.com trusty-security/restricted Translation-en [3,206 B]
Get:78 http://in.archive.ubuntu.com trusty-security/universe Translation-en [71.9 kB]
Get:79 http://in.archive.ubuntu.com trusty Release [58.5 kB]                   
Get:80 http://in.archive.ubuntu.com trusty/main Sources [1,064 kB]             
Get:81 http://in.archive.ubuntu.com trusty/restricted Sources [5,433 B]        
Get:82 http://in.archive.ubuntu.com trusty/universe Sources [6,399 kB]         
Get:83 http://in.archive.ubuntu.com trusty/multiverse Sources [174 kB]         
Get:84 http://in.archive.ubuntu.com trusty/main amd64 Packages [1,350 kB]      
Get:85 http://in.archive.ubuntu.com trusty/restricted amd64 Packages [13.0 kB] 
Get:86 http://in.archive.ubuntu.com trusty/universe amd64 Packages [5,859 kB]  
Get:87 http://in.archive.ubuntu.com trusty/multiverse amd64 Packages [132 kB]  
Get:88 http://in.archive.ubuntu.com trusty/main i386 Packages [1,348 kB]       
Get:89 http://in.archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB]  
Get:90 http://in.archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]   
Get:91 http://in.archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]   
Get:92 http://in.archive.ubuntu.com trusty/main Translation-en [762 kB]        
Get:93 http://in.archive.ubuntu.com trusty/multiverse Translation-en [102 kB]  
Get:94 http://in.archive.ubuntu.com trusty/restricted Translation-en [3,457 B] 
Get:95 http://in.archive.ubuntu.com trusty/universe Translation-en [4,089 kB]  
Ign http://in.archive.ubuntu.com trusty/main Translation-en_IN                 
Ign http://in.archive.ubuntu.com trusty/multiverse Translation-en_IN           
Ign http://in.archive.ubuntu.com trusty/restricted Translation-en_IN           
Ign http://in.archive.ubuntu.com trusty/universe Translation-en_IN             
Fetched 32.4 MB in 2min 3s (263 kB/s)                                          
W: GPG error: http://oss.oracle.com unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2E2BCDBCB38A8516
W: Failed to fetch http://oss.oracle.com/debian/dists/unstable/non-free/source/Sources  HttpError404

W: Failed to fetch http://oss.oracle.com/debian/dists/unstable/main/binary-amd64/Packages  HttpError404

W: Failed to fetch http://oss.oracle.com/debian/dists/unstable/non-free/binary-amd64/Packages  HttpError404

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Still this error occurs how to solve it?

---

### Post by sammiev on 2016-01-19
Disable oss.oracle.com from your source list and try again.

Read [here]("https://help.ubuntu.com/community/Repositories/Ubuntu").

---

### Post by Bucky Ball on 2016-01-19
Open Software & Updates> Other Software tab> untick or remove the oss.oracle PPA that has been manually installed. It is either down or broken.

* Ninja-ed by sammiev! ;)

---

### Post by karthik31 on 2016-01-20
I followed your instructions. btw am getting this list entry error.
CODE:
```
W: Duplicate sources.list entry http://in.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://in.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-i386_Packages)


```
How to solve it?
And my compact sources.list is
```
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://in.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ trusty universe
deb http://in.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://in.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://in.archive.ubuntu.com/ubuntu/ trusty-security main restricted
deb http://in.archive.ubuntu.com/ubuntu/ trusty-security universe
deb http://in.archive.ubuntu.com/ubuntu/ trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb http://in.archive.ubuntu.com/ubuntu/ trusty universe
# deb-src http://archive.ubuntu.com/ubuntu trusty main universe
deb-src http://extras.ubuntu.com/ubuntu trusty main
```

---

### Post by Bashing-om on 2016-01-20
karthik31; Hello"

Yep one duplication of " deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty multiverse" at the top of the list is at the end of the list:
```

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
[color=blue]deb http://in.archive.ubuntu.com/ubuntu/ trusty universe[/color]
# deb-src http://archive.ubuntu.com/ubuntu trusty main universe
deb-src http://extras.ubuntu.com/ubuntu trusty main

```

If it were me, I would remove the 2nd instance to keep the list consistent with default .
( make a backup of the file before making any edits to any file )

[INDENT][INDENT]ducks, all in a row
[/INDENT][/INDENT]

---

