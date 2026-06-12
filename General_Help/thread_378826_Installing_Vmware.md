---
title: "Installing Vmware"
date: 2007-03-07
forum: General Help
---

### Post by darkenemy on 2007-03-07
im having a problem installing vmware on my ubuntu 6.10
 
when i type > sudo '/home/darkenemy/Desktop/vmware-player-distrib/vmware-install.pl' 

into the therminal,
i get

> 
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

Unable to copy the source file ./installer/services.sh to the destination file 
/etc/init.d/vmware.

Execution aborted.


for the life of me i cant get this to work.  can anyone help?

---

### Post by tronica on 2007-03-07
cd into vmware-distrib and run vmware-install.pl while in the vmware-distrib directory

---

### Post by darkenemy on 2007-03-07
how?

---

### Post by tronica on 2007-03-07
Nevermind on that, that won't work.  Heres the easy solution, Its in the repos, just do

> sudo apt-get install vmware-player

if it says it can't find it, you need to add extra repos, follow this guide here

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

---

### Post by darkenemy on 2007-03-07
this is what i got 

>  sudo apt-get install vmware-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vmware-player: Depends: libssl0.9.7 but it is not installable
E: Broken packages


i have already downloaded the file and everything, its just installing it that wont work.

---

### Post by tronica on 2007-03-07
if you follow that link and add those repos, it will give you libssl

---

### Post by darkenemy on 2007-03-07
id didnt work this is what i got

> sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]                                                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US                                                             
Get:2 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]                                          
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release.gpg [191B]                                                 
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                                                           
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US                                        
Get:5 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release.gpg [191B]                                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Translation-en_US                                               
Get:6 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Translation-en_US                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US                                               
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Translation-en_US                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US                                               
Get:7 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release [4874B]                                              
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Translation-en_US                                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Translation-en_US                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US                                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                                                            
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]                                                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                                                 
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]                                               
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages                                                 
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Translation-en_US                                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US                                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US                                             
Get:10 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages [1050B]                                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US                                       
Get:11 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release [4421B]                                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US                       
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release [38.4kB]      
Get:13 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Packages [2279B]             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                                    
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release [38.4kB]                                                     
Get:15 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Packages [1677B]                
Get:16 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Sources [879B]                                             
Get:17 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Sources [1077B]                                                                                          
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release [38.4kB]                                                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                                                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages                                                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources                                                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                                                                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages                                                                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                                                                                                    
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages [64.2kB]                                                                                    
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Packages [79.5kB]                                                                                      
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages [14B]                                                                                 
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Sources [14B]                                                                                  
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Sources [1074B]                                                                                  
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources [19.9kB]                                                                                     
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages [14B]                                                                                 
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages [11.0kB]                                                                                
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages [4655kB]                                                                                        
99% [20 Packages 61012/79.5kB 76%]                                                                                                               9704B/s 1s
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                                                                                                    
  Sub-process gzip returned an error code (1)
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Packages [14B]                                                                                   
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Packages [25.8kB]                                                                                  
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Packages [3084B]                                                                                 
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages [7779B]                                                                                      
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages [14B]                                                                                  
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages [16.0kB]                                                                                 
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages [4824B]                                                                                
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources [2710B]                                                                                       
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources [14B]                                                                                   
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources [6712B]                                                                                   
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources [1466B]                                                                                 
Fetched 377kB in 1m8s (5472B/s)                                                                                                                            
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.





sudo '/home/darkenemy/Desktop/vmware-player-distrib/vmware-install.pl' 
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

Unable to copy the source file ./installer/services.sh to the destination file 
/etc/init.d/vmware.

Execution aborted.


sorry im new with linux.  could you be more specific about how to add the repositories... i may have screwed it up somehow.  i just coppied it from the page into my /etc sources.list thing.

---

### Post by tronica on 2007-03-07
ok, assuming you did add that list of repos to /etc/apt/sources.list, then where it says GPG error, you forgot to add the gpg key

paste this in the terminal

> wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

then do a 

sudo apt-get update

then 

sudo apt-get install vmware-player

---

### Post by darkenemy on 2007-03-07
ok this is what i got

>  sudo wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
OK
darkenemy@darkenemy-desktop:~$ sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]                                                                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US                                                                                  
Get:2 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release.gpg [191B]                                                                                                 
Get:3 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]                                                                                      
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US                                                                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                                                                                                 
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]                                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US                        
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release.gpg [191B]                                                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Translation-en_US                                                                   
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                                                                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                                                                         
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                                                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Translation-en_US                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Translation-en_US                   
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US                           
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US                 
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages                                                
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Translation-en_US                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                                     
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Translation-en_US                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Packages                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Packages                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Sources       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources      
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Packages
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages [4655kB]
99% [9 Packages gzip 0] [Waiting for headers]            
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
  Sub-process gzip returned an error code (1)
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Sources
Fetched 199B in 4s (49B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.



sudo apt-get install vmware-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vmware-player: Depends: libssl0.9.7 but it is not installable
E: Broken packages


i must really suck at this whole linux thing.  how do i just make it better?

(btw. i noticed your buddy rich picture, that video from that performance is one of the things that got me started on drums, amazing)

---

### Post by tronica on 2007-03-07
you could try installing libssl manuly.

[http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8a-7ubuntu0.3_i386.deb]("http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8a-7ubuntu0.3_i386.deb")

download that to your desktop

the cd to the desktop

> cd Desktop

then  do a>  sudo dpkg -i libssl0.9.8_0.9.8a-7ubuntu0.3_i386.deb

then try installing vmware-player.

I'm not a drumer sadly, but a huge fan of buddy.

---

### Post by darkenemy on 2007-03-07
when i do that i get this

> :~/Desktop$ sudo dpkg -i libssl0.9.8_0.9.8a-7ubuntu0.3_i386.deb
dpkg: error processing libssl0.9.8_0.9.8a-7ubuntu0.3_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libssl0.9.8_0.9.8a-7ubuntu0.3_i386.deb


am i just destined not to run vmware?

---

