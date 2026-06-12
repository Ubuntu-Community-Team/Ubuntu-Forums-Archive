---
title: "What is Release.gpg [191B] ?"
date: 2006-12-09
forum: General Help
---

### Post by sque on 2006-12-09
When I do apt-get update I get the following result:
```
Get:1 http://gr.archive.ubuntu.com edgy Release.gpg [191B]
Ign http://gr.archive.ubuntu.com edgy/main Translation-en_US                                                                                                                
Ign http://gr.archive.ubuntu.com edgy/restricted Translation-en_US                                                                                               
Ign http://gr.archive.ubuntu.com edgy/multiverse Translation-en_US                                                                                               
Ign http://gr.archive.ubuntu.com edgy/universe Translation-en_US                                                                                                 
Get:2 http://gr.archive.ubuntu.com edgy-updates Release.gpg [191B]                                                                                               
Ign http://gr.archive.ubuntu.com edgy-updates/main Translation-en_US                                                                                             
Ign http://gr.archive.ubuntu.com edgy-updates/restricted Translation-en_US                                                                                       
Ign http://gr.archive.ubuntu.com edgy-updates/multiverse Translation-en_US                                                                                                  
Ign http://gr.archive.ubuntu.com edgy-updates/universe Translation-en_US                                                                                                    
Ign http://wine.budgetdedicated.com edgy Release.gpg                                                                                                                        
Ign http://wine.budgetdedicated.com edgy/main Translation-en_US                                                                                                             
Hit http://gr.archive.ubuntu.com edgy Release                                                                                                                               
Hit http://gr.archive.ubuntu.com edgy-updates Release                                                                                                                       
Get:3 http://ubuntu.beryl-project.org edgy Release.gpg [189B]                                                                                      
Ign http://ubuntu.beryl-project.org edgy/main Translation-en_US                                                                                    
Hit http://wine.budgetdedicated.com edgy Release                                                                                                   
Ign http://ntfs-3g.sitesweetsite.info edgy Release.gpg                                                                                             
Ign http://ntfs-3g.sitesweetsite.info edgy/main-all Translation-en_US                                                                              
Get:4 http://security.ubuntu.com edgy-security Release.gpg [191B]                                                                                  
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US                                                                          
Ign http://security.ubuntu.com edgy-security/main Translation-en_US                                                                                
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US                                                                          
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US                                                                            
Hit http://gr.archive.ubuntu.com edgy/main Packages                                                                                                
Hit http://ubuntu.beryl-project.org edgy Release                                                                                      
Ign http://wine.budgetdedicated.com edgy/main Packages                                                          
Hit http://security.ubuntu.com edgy-security Release                                                            
Ign http://ntfs-3g.sitesweetsite.info edgy Release                                        
Hit http://wine.budgetdedicated.com edgy/main Packages                                    
Ign http://ntfs-3g.sitesweetsite.info edgy/main-all Packages                              
Hit http://gr.archive.ubuntu.com edgy/restricted Packages           
Hit http://gr.archive.ubuntu.com edgy/multiverse Packages
Hit http://gr.archive.ubuntu.com edgy/universe Packages
Hit http://gr.archive.ubuntu.com edgy/main Sources
Hit http://gr.archive.ubuntu.com edgy/restricted Sources
Hit http://gr.archive.ubuntu.com edgy/multiverse Sources
Hit http://gr.archive.ubuntu.com edgy/universe Sources
Hit http://ntfs-3g.sitesweetsite.info edgy/main-all Packages                              
Hit http://gr.archive.ubuntu.com edgy-updates/main Packages          
Hit http://gr.archive.ubuntu.com edgy-updates/restricted Packages    
Hit http://ubuntu.beryl-project.org edgy/main Packages               
Hit http://security.ubuntu.com edgy-security/restricted Packages     
Hit http://gr.archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://gr.archive.ubuntu.com edgy-updates/universe Packages
Hit http://gr.archive.ubuntu.com edgy-updates/main Sources
Hit http://gr.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://gr.archive.ubuntu.com edgy-updates/multiverse Sources
Hit http://gr.archive.ubuntu.com edgy-updates/universe Sources
Hit http://security.ubuntu.com edgy-security/main Packages
Hit http://security.ubuntu.com edgy-security/multiverse Packages
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/multiverse Sources
Hit http://security.ubuntu.com edgy-security/universe Sources
Fetched 192B in 1s (132B/s)
Reading package lists... Done

```

My question is what **Release.gpg [191B] ** means at the right of some repositories? I have the feeling that this wasn't always showing and it is something new. Is it bad? Do actually update from these repositories?

---

### Post by Azakus on 2006-12-10
Those Release.gpg files are hash-coded files that serve to verify that the source is legitimate. Here's the actual file [http://archive.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg)

---

