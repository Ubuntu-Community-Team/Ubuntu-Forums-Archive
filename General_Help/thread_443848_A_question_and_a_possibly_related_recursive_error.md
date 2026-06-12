---
title: "A question and a possibly related recursive error"
date: 2007-05-14
forum: General Help
---

### Post by Tucci on 2007-05-14
I'm a new Ubuntu user, and I accidentally messed up my sources.list, so I couldn't get any applications. I was seemingly able to fix that, however, the instructions I followed claimed I had to run 'sudo apt-get update' in the Terminal after fixing the sources.list. I did and now I get an error message that tells me to run 'sudo apt-get update' to fix the error! The original problem appears to be fixed and I can download software normally, so why does this error message appear? And why would an error message suggest I take the same action that caused the error in the first place?

On a possibly related note, I used Celtx (a screenwriting program) on my Mac and Windows. I know it is Linux-compatible, but it isn't anywhere in the software list. Did I remove a repository or something in fixing my sources.list?

Here's my sources,list:

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

Here's the error message that comes up in Terminal after running sudo apt-get update:

Err [http://medibuntu.sos-sts](http://medibuntu.sos-sts) feisty Release.gpg
  Could not resolve 'medibuntu.sos-sts'
Err [http://medibuntu.sos-sts](http://medibuntu.sos-sts) feisty/free Translation-en_US                     
  Could not resolve 'medibuntu.sos-sts'
Err [http://medibuntu.sos-sts](http://medibuntu.sos-sts) feisty/non-free Translation-en_US                 
  Could not resolve 'medibuntu.sos-sts'
Ign [http://medibuntu.sos-sts](http://medibuntu.sos-sts) feisty Release                                    
Ign [http://medibuntu.sos-sts](http://medibuntu.sos-sts) feisty/free Packages                              
Ign [http://medibuntu.sos-sts](http://medibuntu.sos-sts) feisty/non-free Packages                          
Err [http://medibuntu.sos-sts](http://medibuntu.sos-sts) feisty/free Packages                              
  Could not resolve 'medibuntu.sos-sts'
Err [http://medibuntu.sos-sts](http://medibuntu.sos-sts) feisty/non-free Packages                          
  Could not resolve 'medibuntu.sos-sts'
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US   
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release [32.4kB]             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Packages            
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages [11.3kB]        
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages [14B]     
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages [1715B]     
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages [14B]    
Get:9 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]                  
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release
  
Get:10 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release [7232B]
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
Fetched 53.1kB in 4s (10.7kB/s)
Failed to fetch [http://medibuntu.sos-sts/repo/dists/feisty/Release.gpg](http://medibuntu.sos-sts/repo/dists/feisty/Release.gpg)  Could not resolve 'medibuntu.sos-sts'
Failed to fetch [http://medibuntu.sos-sts/repo/dists/feisty/free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts/repo/dists/feisty/free/i18n/Translation-en_US.bz2)  Could not resolve 'medibuntu.sos-sts'
Failed to fetch [http://medibuntu.sos-sts/repo/dists/feisty/non-free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts/repo/dists/feisty/non-free/i18n/Translation-en_US.bz2)  Could not resolve 'medibuntu.sos-sts'
Failed to fetch [http://medibuntu.sos-sts/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts/repo/dists/feisty/free/binary-i386/Packages.gz)  Could not resolve 'medibuntu.sos-sts'
Failed to fetch [http://medibuntu.sos-sts/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts/repo/dists/feisty/non-free/binary-i386/Packages.gz)  Could not resolve 'medibuntu.sos-sts'
Reading package lists... Done
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by raja on 2007-05-14
Looks like you have the medibuntu repository added somewhere. Go to Synaptic and remove this if you dont want it anymore. If you want to use it, you have to add the gpg keys to your list of trusted keys. That is what the warning is all about. See [this thread]("http://ubuntuforums.org/showthread.php?p=2572506") to learn how to add the key.

---

### Post by Tucci on 2007-05-14
Okay, I did that in the terminal and it asked for my password, then nothing seemed to occur. I ran 'sudo apt-get update' again and got what appears to be the same message:

Get:1 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                 
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Packages            
Err [http://medibuntu.sos-sts](http://medibuntu.sos-sts) feisty Release.gpg                                
  Could not resolve 'medibuntu.sos-sts'
Err [http://medibuntu.sos-sts](http://medibuntu.sos-sts) feisty/free Translation-en_US               
  Could not resolve 'medibuntu.sos-sts'
Err [http://medibuntu.sos-sts](http://medibuntu.sos-sts) feisty/non-free Translation-en_US
  Could not resolve 'medibuntu.sos-sts'
Ign [http://medibuntu.sos-sts](http://medibuntu.sos-sts) feisty Release            
Ign [http://medibuntu.sos-sts](http://medibuntu.sos-sts) feisty/free Packages      
Ign [http://medibuntu.sos-sts](http://medibuntu.sos-sts) feisty/non-free Packages  
Err [http://medibuntu.sos-sts](http://medibuntu.sos-sts) feisty/free Packages      
  Could not resolve 'medibuntu.sos-sts'
Err [http://medibuntu.sos-sts](http://medibuntu.sos-sts) feisty/non-free Packages  
  Could not resolve 'medibuntu.sos-sts'
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Fetched 192B in 4s (43B/s)
Failed to fetch [http://medibuntu.sos-sts/repo/dists/feisty/Release.gpg](http://medibuntu.sos-sts/repo/dists/feisty/Release.gpg)  Could not resolve 'medibuntu.sos-sts'
Failed to fetch [http://medibuntu.sos-sts/repo/dists/feisty/free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts/repo/dists/feisty/free/i18n/Translation-en_US.bz2)  Could not resolve 'medibuntu.sos-sts'
Failed to fetch [http://medibuntu.sos-sts/repo/dists/feisty/non-free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts/repo/dists/feisty/non-free/i18n/Translation-en_US.bz2)  Could not resolve 'medibuntu.sos-sts'
Failed to fetch [http://medibuntu.sos-sts/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts/repo/dists/feisty/free/binary-i386/Packages.gz)  Could not resolve 'medibuntu.sos-sts'
Failed to fetch [http://medibuntu.sos-sts/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts/repo/dists/feisty/non-free/binary-i386/Packages.gz)  Could not resolve 'medibuntu.sos-sts'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

