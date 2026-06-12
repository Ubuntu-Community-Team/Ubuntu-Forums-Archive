---
title: "Cant seem to enable universe repositories?"
date: 2007-04-09
forum: General Help
---

### Post by darkenemy on 2007-04-09
at the very least, i am under the impression that when i type the "sudo apt-get update" command into the terminal, there should be no errors anywhere.

i have some, and would like to fix it.  i believe there is some problem enabling the universe repositories, but i could be wrong.

heres what i get when i type "sudo apt-get update"

> Ign [http://flomertens.free.fr](http://flomertens.free.fr) edgy Release.gpg                                                                                                              
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy Release.gpg                                                                                                               
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Translation-en_US                                                                                                    
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]                                                                                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US                                                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US                                                                                   
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release.gpg [191B]                                                                                            
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy Release.gpg                                                                                                      
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Translation-en_US                                                                                           
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Translation-en_US                                                                                       
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                                                                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                                                                                                
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Translation-en_US                                                                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US                                                                                          
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy Release                                                                                                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Translation-en_US                                                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US                                                                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US                                                                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                                                                                                        
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy Release                                                                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US                                                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US                                                                                            
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]                                                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US                                                                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US                                                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US                                                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US                                                                                    
Ign [http://flomertens.free.fr](http://flomertens.free.fr) edgy/main Translation-en_US                                                                                                   
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Packages                                                                                                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Translation-en_US                                                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                                                                                                  
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Packages                                                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                                                                                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Translation-en_US                                                                                      
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Packages                                                                                                         
Get:5 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release.gpg [189B]                                                                                                  
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Packages                                                                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                                                                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources                                                                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                                                                                            
Ign [http://flomertens.free.fr](http://flomertens.free.fr) edgy/main-all Translation-en_US                                                                                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Translation-en_US                                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                                                                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages                                                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources                                                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                                                                                                          
Hit [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Packages                                                                                                             
Hit [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Packages                                                                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                                                                                              
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]                                                                                           
Get:7 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]                                                                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US                                                                                   
Get:8 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]                                                                                       
Hit [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Packages                                                                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages                                                                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                                                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages                                                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages                                                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Sources                                                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US                                                                                         
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US                                                                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                                                                                                  
Hit [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Packages                                                                                                
Ign [http://flomertens.free.fr](http://flomertens.free.fr) edgy Release                                                                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Sources                                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources                                                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages                                                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages                                                                                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US                                                                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                                                                                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US                                                                                     
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Translation-en_US                                                                                                
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages                                                                                            
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages [4655kB]                                                                                          
99% [9 Packages gzip 0] [Waiting for headers] [Waiting for headers] [Waiting for headers]                                                         8404B/s 0s
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                                                                                                     
  Sub-process gzip returned an error code (1)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US                                                                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                                                                                              
Ign [http://flomertens.free.fr](http://flomertens.free.fr) edgy/main Packages                                                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release                                                                                                         
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Translation-en_US                                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                                                                                                        
Ign [http://flomertens.free.fr](http://flomertens.free.fr) edgy/main-all Packages                                                                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Packages                                                                                                   
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release                                                                                                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Packages                                                                                             
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Packages                                                                                                         
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Packages                                                                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Packages                                                                                               
Hit [http://flomertens.free.fr](http://flomertens.free.fr) edgy/main Packages                                                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Packages                                                                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                                                                                                  
Hit [http://flomertens.free.fr](http://flomertens.free.fr) edgy/main-all Packages                                                                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages                                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                                                                                              
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources
Fetched 9B in 28s (0B/s) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


can anyone help?

---

### Post by aysiu on 2007-04-09
Maybe try a different mirror?
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

