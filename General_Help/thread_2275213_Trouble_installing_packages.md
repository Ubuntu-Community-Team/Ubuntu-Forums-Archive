---
title: "Trouble installing packages"
date: 2015-04-24
forum: General Help
---

### Post by michael277 on 2015-04-24
Whenever I try to install something I get a "requires istallation of untrusted packages" error. When I click repair, the error still comes up. Besides some "get", "hit", and "ign" stuff, sudo apt-get update gives the message  "W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
"

---

### Post by ian-weisser on 2015-04-24
Easily fixed. See [http://askubuntu.com/questions/198371/apt-encounters-errors-with-bad-gpg-keys](http://askubuntu.com/questions/198371/apt-encounters-errors-with-bad-gpg-keys)

---

### Post by michael277 on 2015-04-25
fixed

---

### Post by Bashing-om on 2015-04-25
michael277; Good deal !

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT][INDENT]up up and Away
[/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-05-19
I have tried the "fix" and keep getting the message that the public keys are unchanged.  Yet, I still get hte same error message that the untrusted packages won't install.  It's become an endless loop of updating keys that are unchaged yet non-working.  Help.

---

### Post by StephenG on 2015-05-19
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports InRelease                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security InRelease                        
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg [933 B]                     
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release.gpg [933 B]             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports Release.gpg [933 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security Release.gpg [933 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                                   
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release [63.5 kB]               
Get:6 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                     
Get:7 [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg [933 B]                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release              
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty Release             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports Release                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports Release                         
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security Release [63.5 kB]              
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources/DiffIndex              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources/DiffIndex                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security Release                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources/DiffIndex              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Sources/DiffIndex     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Sources/DiffIndex     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Sources/DiffIndex       
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages/DiffIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages/DiffIndex      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages/DiffIndex     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages/DiffIndex 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages/DiffIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en                 
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Sources/DiffIndex            
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Sources/DiffIndex      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Sources/DiffIndex      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Sources/DiffIndex        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages/DiffIndex      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages/DiffIndex  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse i386 Packages/DiffIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main Sources/DiffIndex          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted Sources/DiffIndex    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe Sources/DiffIndex      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse Sources/DiffIndex    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main i386 Packages/DiffIndex    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse i386 Packages/DiffIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en_US              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse Translation-en 
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted Translation-en 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse i386 Packages/DiffIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Sources [202 kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Sources [5,161 B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Sources [2,564 B] 
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Sources [117 kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages [505 kB]  
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages [9,256 B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages [280 kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse i386 Packages [12.1 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main i386 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse i386 Packages        
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Sources [80.6 kB]        
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Sources [2,335 B]  
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Sources [2,061 B]  
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Sources [24.9 kB]    
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main i386 Packages [256 kB]   
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted i386 Packages [8,846 B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe i386 Packages [104 kB]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse i386 Packages [3,828 B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Translation-en_US       
Fetched 1,747 kB in 9s (190 kB/s)                                              
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32

---

### Post by StephenG on 2015-05-19
This is the follow-up:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.oe3w6QxH1s --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d/fuzebox.gpg --keyring /etc/apt/trusted.gpg.d/pipelight-stable.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

---

