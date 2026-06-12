---
title: "Problem with software center and updates."
date: 2013-09-02
forum: General Help
---

### Post by jesus-freak on 2013-09-02
I've recently started having a couple of problems. When I go to software center and select something to download, it never shows the reviews, it's just like it's endlessly loading. It doesn't seem to effect downloading and installing software but I like to read the reviews sometimes. The second problem is that Ubuntu seemed to regularly update until a couple of weeks ago, it seemed to just stop. So I ran the updater and after waiting for about 10 min a box came up that said "Failed to download repository Information. Please check your internet connection" My connection is fine. Any ideas on either of these problems?

---

### Post by rai_shu2 on 2013-09-02
Might want to double-check the repos.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by jesus-freak on 2013-09-02
I'm not sure what I'm looking for in the repos. I went through it and everything looks in order. I changed the server to the main one instead of the one I had selected earlier. Then I tried to run update and was able to do so although it was quite slow. But I'm still having the problem with the reviews never loading in software center. If someone could give me a bit more detail as to what to look for in the repos that would be great! Thanks for the help!!

---

### Post by jesus-freak on 2013-09-02
Anyone have any ideas why the software center isn't working correctly? Just so you know, I'm pretty new to linux, maybe 8 months or so.

---

### Post by ibjsb4 on 2013-09-02
Do an update in terminal and look for errors.

```
sudo apt-get update
```

---

### Post by jesus-freak on 2013-09-02
I just did what you said and this is what I got. Does anyone see anything in this that would tell us what is wrong?

Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg [72 B]                       
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                                    
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages                        
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                         
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release.gpg                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release.gpg                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Sources                               
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release.gpg                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release.gpg                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Sources                               
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release                           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_PH                     
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Sources                               
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main amd64 Packages               
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main i386 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release.gpg                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages               
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_PH               
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release                      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release.gpg             
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports Release.gpg           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_PH               
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                  
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner amd64 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security Release.gpg            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_PH               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main amd64 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted amd64 Packages                 
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main amd64 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe amd64 Packages                   
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main i386 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse amd64 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe i386 Packages                    
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_PH              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse i386 Packages                  
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Translation-en                 
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main amd64 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en                 
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_PH                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Translation-en                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main amd64 Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_PH                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted amd64 Packages         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_PH
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse i386 Packages
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main amd64 Packages
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe amd64 Packages
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse amd64 Packages
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse Translation-en
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted Translation-en
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Fetched 72 B in 1min 16s (0 B/s)

---

### Post by ibjsb4 on 2013-09-02
Nope, looks good.  Try your software center again.  Sometimes all it needs is a kick start.  Also ..

```
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg [72 B]                       
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                                    
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages                        
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                         
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release.gpg                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release.gpg                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Sources                               
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release.gpg                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release.gpg                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Sources                               
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release                           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_PH                     
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Sources                               
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main amd64 Packages               
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main i386 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release.gpg                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages               
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_PH               
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release                      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release.gpg             
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports Release.gpg           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_PH               
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                  
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner amd64 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security Release.gpg            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_PH               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main amd64 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted amd64 Packages                 
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main amd64 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe amd64 Packages                   
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main i386 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse amd64 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe i386 Packages                    
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_PH              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse i386 Packages                  
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Translation-en                 
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main amd64 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en                 
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_PH                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Translation-en                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main amd64 Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_PH                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted amd64 Packages         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_PH
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse i386 Packages
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main amd64 Packages
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe amd64 Packages
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse amd64 Packages
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse Translation-en
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted Translation-en
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Fetched 72 B in 1min 16s (0 B/s) 		
```

Using code tags is a good idea :)

[ATTACH=CONFIG]245922[/ATTACH]

---

### Post by jesus-freak on 2013-09-02
Nope, still won't load the reviews or recommendations. It just does this endless loading thing.

---

### Post by ibjsb4 on 2013-09-02
Try another package manager, see if it will work.

```
sudo apt-get install synaptic
```

And for the moment you can see reviews/comments at [Ubuntu Apps Directory]("https://apps.ubuntu.com/cat/")

---

### Post by jesus-freak on 2013-09-02
Here is some more info.
[IMG][[IMG]http://i47.photobucket.com/albums/f167/hendrix4000/Screenshotfrom2013-09-02222519.png[/IMG]](http://s47.photobucket.com/user/hendrix4000/media/Screenshotfrom2013-09-02222519.png.html)[/IMG]
[IMG][[IMG]http://i47.photobucket.com/albums/f167/hendrix4000/Screenshotfrom2013-09-02222539.png[/IMG]](http://s47.photobucket.com/user/hendrix4000/media/Screenshotfrom2013-09-02222539.png.html)[/IMG]
[[IMG]http://i47.photobucket.com/albums/f167/hendrix4000/Screenshotfrom2013-09-02222546.png[/IMG]](http://s47.photobucket.com/user/hendrix4000/media/Screenshotfrom2013-09-02222546.png.html)
[IMG][[IMG]http://i47.photobucket.com/albums/f167/hendrix4000/Screenshotfrom2013-09-02222552.png[/IMG]](http://s47.photobucket.com/user/hendrix4000/media/Screenshotfrom2013-09-02222552.png.html)[/IMG]
[IMG][[IMG]http://i47.photobucket.com/albums/f167/hendrix4000/Screenshotfrom2013-09-02222559.png[/IMG]](http://s47.photobucket.com/user/hendrix4000/media/Screenshotfrom2013-09-02222559.png.html)[/IMG]

And then when I use the software center this is what I am seeing.
[IMG][[IMG]http://i47.photobucket.com/albums/f167/hendrix4000/Screenshotfrom2013-09-01222620.png[/IMG]](http://s47.photobucket.com/user/hendrix4000/media/Screenshotfrom2013-09-01222620.png.html)[/IMG]

---

### Post by jesus-freak on 2013-09-02
Thanks for that link, it is useful to me at the moment with my software center not working correctly! As far as synaptic, I already have that but I'm not a fan of it. I know many people like it better but I don't even know how to use it so I prefer the more simple software center for now. Anyway, there is obviously a problem that is making it not work right. I would rather find and fix the problem rather than find something else to work around the problem.



> **ibjsb4 said:**
> Try another package manager, see if it will work.

```
sudo apt-get install synaptic
```

And for the moment you can see reviews/comments at [Ubuntu Apps Directory]("https://apps.ubuntu.com/cat/")

---

### Post by ibjsb4 on 2013-09-02
Ok, try this

```
gksudo software-center
```

See if will spit out any errors by opening it in terminal.

You can also try a reinstall:

```
sudo apt-get remove --purge software-center && sudo apt-get install software center
```

I am stepping out for a while, check back later.

---

### Post by jesus-freak on 2013-09-02
Okay, when I opened software center in terminal it worked! I could view the reviews. But then I tried to open it normally and I got the same old problem. Here is what it said when I opened it in terminal.

2013-09-03 11:17:07,757 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has no usable Address providers'
2013-09-03 11:17:08,111 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-09-03 11:17:08,123 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-09-03 11:17:08,139 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-09-03 11:17:08,139 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-09-03 11:17:08,240 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2013-09-03 11:17:17,957 - softwarecenter.ui.gtk3.views.lobbyview - WARNING - skipping exhibit for: 'u'spindl'' not available
2013-09-03 11:17:17,957 - softwarecenter.ui.gtk3.views.lobbyview - WARNING - skipping exhibit for: 'u'wakfu'' not available
2013-09-03 11:17:17,963 - softwarecenter.ui.gtk3.widgets.exhibits - WARNING - download failed: '<class 'gi._glib.GError'>', 'Operation not supported'
2013-09-03 11:17:23,971 - softwarecenter.db.utils - INFO - software-center-agent finished with status 0
2013-09-03 11:17:29,277 - softwarecenter.ui.gtk3.widgets.exhibits - WARNING - download failed: '<class 'gi._glib.GError'>', 'Operation not supported'

Should I go ahead and try to re-install the software center?

---

### Post by jesus-freak on 2013-09-02
Okay, I went ahead and tried to re-install software center. It uninstalled fine but when I tried to install it, I get these errors.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package software
E: Unable to locate package center

So Then I went to synaptic and located the software center and tried to install it and I got these errors.

E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to lock the download directory


My second attempt to install software center through synaptic was successful BUT now I'm back to were I was before. Software center works, just still the annoying endless loading of the reviews and recommendations.

Opening software center through terminal with "gksudo software-center" allows everything to work correctly and the reviews and recommendations load up fine, it's just when I try to open it normally it messes up.

---

### Post by jesus-freak on 2013-09-03
With this latest info does anyone have any ideas?

---

### Post by Bashing-om on 2013-09-03
jesus-freak; Hi !
Looks like you attempted to install "software center" as two different packages (??)
> 
Reading state information... Done
E: Unable to locate package software
E: Unable to locate package center

Do not know what damage might have been done. But, try as:
```

sudo apt-get install software-center

```
note the "-" between the terms makes it the one application you are dealing with(proper name).

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by jesus-freak on 2013-09-03
Okay, just so you know, I never did anything to the software center, it just started acting up on it's own about 2 months ago. Secondly, I only did what the other person suggested. They said I should try to remove the software center and re install it. They gave me these codes to do it with sudo apt-get remove --purge software-center to remove it and sudo apt-get install software center to re install it. I successfully uninstalled it using that code, it was completely gone. Then I tried to run the install code and got a error message and it was not installed, it was still 100% gone at this point. So then I tried to install it using synaptic and I also got a error message and it didn't let me install it at all, it was still 100% gone. Then I tried to install it again using synaptic and this time it installed okay BUT I'm still left with the exact same problem I started out with, the reviews and suggestions won't load. So in short I did absolutely nothing to get this problem in the first place, it just popped out of no where and after all I've tried I'm left with the same problem I started with. Now, after running the code you just suggested here are the results.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
software-center is already the newest version.
The following packages were automatically installed and are no longer required:
  bve-route-cross-city-south bve-train-br-class-323
  bve-train-br-class-323-3dcab firefox-globalmenu libboost-signals1.49.0
  libloudmouth1-0 libopal3.10.10 python-cssselect
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
justdrea@justdrea-Satellite-A665:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Thanks for your help!

---

### Post by Bashing-om on 2013-09-03
jesus-freak; Hi !

Hey .. calm down .. We are all human and can make mistakes. Look at what all you are learning in the process of learning to live with your operating system of choice. May I offer that is is an example to always be aware of what/how you are telling your system what to do ...you are the one ultimately responsible - we all get tired and can make an error.
Ok .. things with the OS look in good shape ..
The last error message just indicates that you are attempting to alter the system without providing the authority to do so: 
> 
justdrea@justdrea-Satellite-A665:~$ apt-get autoremove

Give the authority with "sudo"
```

sudo apt-get autoremove

```

OK ??

now back to the situation at hand .. update the status to us by once more providing the errors generated when software-center is started from the CLI:
```

gksudo software-center

```
And let's see where we stand now.

[INDENT][INDENT]open source, we are all in this together 
[/INDENT][/INDENT]

---

### Post by jesus-freak on 2013-09-03
I'm calm, I was just making sure that you knew that I wasn't here because I'm trying to fix something that I did wrong because as far as I know I did nothing. I go online, I use skype,I use office, I listen to music, I play videos, that is about the extent of my computer usage. I'm not an advanced user and so I don't do things unless I'm sure of what I'm doing. Of course sometimes we can do something totally normal or innocent and the result can do damage. But as far as I know I never did anything to damage it. One day it worked, the next day it didn't. I had not installed any new software or removed any software in between it working and it not working. No hardware changes, nothing. To me it's a mystery. Anyway, when I use the command gksudo software-center The software center opens and everything seems to work correctly. Here are the results of that.

 2013-09-03 23:34:05,043 - softwarecenter.db.utils - INFO - software-center-agent finished with status 0
2013-09-03 23:34:07,319 - softwarecenter.ui.gtk3.widgets.exhibits - WARNING - download failed: '<class 'gi._glib.GError'>', 'Operation not supported'

But still when I open software center normally I have the same problem.
Thanks so much for your help.

---

### Post by Bashing-om on 2013-09-03
jesus-freak; Well...
To be upfront, the GUI is not an area of interest to me and I am deficient in knowledge. As the application functions when started from the CLI, must be a "failure to communicate" at the GUI layer. In looking about I ran across this intriguing bit of info:
> 
Michael Vogt (mvo) wrote on 2012-04-13:	 #2
Thanks for your bugreport, I don't quite understand.

software-center does not need to run as root for a start, what exactly is the error in question?

let us try this and see what is reported:
```

software-center &

```
[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by jesus-freak on 2013-09-03
That command opens software center with the original problem. Here is what it says

2013-09-04 00:38:05,035 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'http://97.83.206.36:65535/'
2013-09-04 00:38:06,096 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-09-04 00:38:06,104 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-09-04 00:38:06,104 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-09-04 00:38:06,197 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()

---

### Post by Bashing-om on 2013-09-03
jesus-freak;

That sorta sets me back .. not at all what I expected ... gonna have to take a bit of time to think about it and do some research ..
this: certainly makes me pause:
> 
2013-09-04 00:38:05,035 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'http://97.83.206.36:65535/'

Are you at work - behind a LAN ? Going through a proxy router at some point ?

[INDENT][INDENT]sometimes I wonder, other times I just do not know
[/INDENT][/INDENT]

---

### Post by jesus-freak on 2013-09-03
Nope, not at work, not behind a LAN, not going through  a proxy router

---

### Post by Bashing-om on 2013-09-03
jesus-freak; Hummm .. real odd.
That URL is being called from somewhere..obvious places to look is in the sources.list files:
```

cat /etc/apt/sources.list
ls -la /etc/apt/sources.list.d

```
maybe a possibility that an added PPA is in conflict ?

[INDENT][INDENT]gots to be a reason.
[/INDENT][/INDENT]

---

### Post by jesus-freak on 2013-09-03
Result of cat /etc/apt/sources.list

cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main


Result of ls -la /etc/apt/sources.list.d

drwxr-xr-x 2 root root 4096 Sep  2 14:27 .
drwxr-xr-x 6 root root 4096 Aug 30 21:05 ..
-rw-r--r-- 1 root root  130 Sep  2 22:22 atareao-lenses-raring.list
-rw-r--r-- 1 root root  130 Sep  2 22:22 atareao-lenses-raring.list.save
-rw-r--r-- 1 root root  176 Sep  2 22:22 google-chrome.list
-rw-r--r-- 1 root root  176 Sep  2 22:22 google-chrome.list.save
-rw-r--r-- 1 root root  175 Sep  2 22:22 google-earth.list
-rw-r--r-- 1 root root  175 Sep  2 22:22 google-earth.list.save
-rw-r--r-- 1 root root  180 Sep  2 22:22 google-talkplugin.list
-rw-r--r-- 1 root root  180 Sep  2 22:22 google-talkplugin.list.save
-rw-r--r-- 1 root root  160 Sep  2 22:22 private-ppa.launchpad.net_commercial-ppa-uploaders_cloudware_ubuntu.list
-rw-r--r-- 1 root root  160 Sep  2 22:22 private-ppa.launchpad.net_commercial-ppa-uploaders_cloudware_ubuntu.list.save
-rw-r--r-- 1 root root  166 Sep  2 22:22 private-ppa.launchpad.net_commercial-ppa-uploaders_crossover-trial_ubuntu.list
-rw-r--r-- 1 root root  166 Sep  2 22:22 private-ppa.launchpad.net_commercial-ppa-uploaders_crossover-trial_ubuntu.list.save
-rw-r--r-- 1 root root  166 Sep  2 22:22 private-ppa.launchpad.net_commercial-ppa-uploaders_minitube-ubuntu_ubuntu.list
-rw-r--r-- 1 root root  166 Sep  2 22:22 private-ppa.launchpad.net_commercial-ppa-uploaders_minitube-ubuntu_ubuntu.list.save
-rw-r--r-- 1 root root  161 Sep  2 22:22 private-ppa.launchpad.net_commercial-ppa-uploaders_pct-listen_ubuntu.list
-rw-r--r-- 1 root root  161 Sep  2 22:22 private-ppa.launchpad.net_commercial-ppa-uploaders_pct-listen_ubuntu.list.save
-rw-r--r-- 1 root root  157 Sep  2 22:22 private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list
-rw-r--r-- 1 root root  157 Sep  2 22:22 private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.save
-rw-r--r-- 1 root root  166 Sep  2 22:22 private-ppa.launchpad.net_commercial-ppa-uploaders_youtube-to-mp3_ubuntu.list
-rw-r--r-- 1 root root  166 Sep  2 22:22 private-ppa.launchpad.net_commercial-ppa-uploaders_youtube-to-mp3_ubuntu.list.save
-rw-r--r-- 1 root root  124 Sep  2 22:22 roggan87-nr-raring.list
-rw-r--r-- 1 root root  124 Sep  2 22:22 roggan87-nr-raring.list.save
-rw-r--r-- 1 root root  142 Sep  2 22:22 scopes-packagers-ppa-raring.list
-rw-r--r-- 1 root root  142 Sep  2 22:22 scopes-packagers-ppa-raring.list.save
-rw-r--r-- 1 root root    0 Sep  2 22:22 steam.list
-rw-r--r-- 1 root root    0 Sep  2 22:22 steam.list.save
-rw-r--r-- 1 root root    0 Sep  2 22:22 unity-2d-team-unity-2d-daily-raring.list
-rw-r--r-- 1 root root    0 Sep  2 22:22 unity-2d-team-unity-2d-daily-raring.list.save

---

### Post by Bashing-om on 2013-09-03
jesus-freak; Hey ...
what is Net responsibility ? - from PPA " roggan87-nr-raring.list" - 
Looks like a good possibility of the source of conflict.

[INDENT][INDENT]hey it is a thought
[/INDENT][/INDENT]

---

### Post by jesus-freak on 2013-09-03
I really have no idea of what it is. If that is the problem then how to I fix it? Any idea?

Actually I do remember this. About 8 months ago when I started using Ubuntu a friend recommended this accountability software. It was supposed to work with Ubuntu but it didn't seem to do anything. After only a few days I removed it. The software center worked fine after removing it, that was like 8 months ago and the software center started having problems about 2 months ago. But if some part of that software is still in my computer then I need to get rid of it because I already removed it.

---

### Post by jesus-freak on 2013-09-04
Any ideas?

---

### Post by Bashing-om on 2013-09-04
jesus-freak; Hey,

If that software is no longer installed, then yes, for sure need to remove that source .. and look about and see if all has been removed.
We can get the name of the PPA:
```

cat /etc/apt/sources.list.d/roggan87-nr-raring.list

``` 
A good possibility is in an attempt to "update" this ppa, it has broken the package management system.
Did you upgrade your system to "raring" ???
Any other - no longer used applications -  you have installed we need to address also ?
Also need to look from the prior error indicator what is in the files:
First, let us see what they are before poking into them.
```

ls -la /usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc
ls -la /usr/lib/python2.7/dist-packages/gi/importer.py/

```
I will need a bit of looking at these directories before getting down to it.
Strange files I have never encountered before.
----------
Shortly I will again be away from the keyboard ... I will be able to return later in my PM.

[INDENT][INDENT]just poke'n about
[/INDENT][/INDENT]

---

### Post by jesus-freak on 2013-09-04
Here is what it says when I enter that command

deb [http://ppa.launchpad.net/roggan87/nr/ubuntu](http://ppa.launchpad.net/roggan87/nr/ubuntu) raring main
deb-src [http://ppa.launchpad.net/roggan87/nr/ubuntu](http://ppa.launchpad.net/roggan87/nr/ubuntu) raring main

No, I didn't upgrade, I installed 13.04 and didn't upgrade from an older version.

---

### Post by Bashing-om on 2013-09-05
jesus-freak;

This
> 
deb [http://ppa.launchpad.net/roggan87/nr/ubuntu](http://ppa.launchpad.net/roggan87/nr/ubuntu) raring main
deb-src [http://ppa.launchpad.net/roggan87/nr/ubuntu](http://ppa.launchpad.net/roggan87/nr/ubuntu) raring main

though correct, is not at all what I had expected to see for a ppa's name...

How bout the output of:
```

ls -la /usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc
ls -la /usr/lib/python2.7/dist-packages/gi/importer.py/

```
At this point I am uncertain of a procedure.

[INDENT][INDENT]think'n on it and look'n[/INDENT][/INDENT]

---

### Post by jesus-freak on 2013-09-05
Here is the results of the other two codes

-rw-r--r-- 1 root root 2068 Sep  3 11:35 /usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc


ls: cannot access /usr/lib/python2.7/dist-packages/gi/importer.py/: Not a directory

---

### Post by Bashing-om on 2013-09-05
jesus-freak; Well, well
net-responsibility - not properly un-installed - seems more likely to be the root cause.


In for a penny in for a pound ...I find that Net-Responsibility is well supported, before relaying to you what I may have in mind .. let's look at what is.
Post back the outputs:
```

ls -la /usr/bin/net-responsibility
ls -la /usr/share/net-responsibility
ls -la /usr/lib/libNetResponsibility.*
ls -la /usr/lib/net-responsibility/report.*

```
source:
[http://netresponsibility.com/index.php](http://netresponsibility.com/index.php)

[INDENT][INDENT]a little look'n goes a long way
[/INDENT][/INDENT]

---

### Post by jesus-freak on 2013-09-06
All of these codes you send only produce the following.

cannot access: No such file or directory

---

### Post by Bashing-om on 2013-09-06
jesus-freak;Outstanding !

We can safely "assume" that 'net-responsibility' no longer exist on your system and that the requirement for :
> 
deb [http://ppa.launchpad.net/roggan87/nr/ubuntu](http://ppa.launchpad.net/roggan87/nr/ubuntu) raring main
deb-src [http://ppa.launchpad.net/roggan87/nr/ubuntu](http://ppa.launchpad.net/roggan87/nr/ubuntu) raring main

no longer exist also. Get rid of that source "get".
```

sudo rm  /etc/apt/sources.list.d/roggan87-nr-raring.list
sudo rm  /etc/apt/sources.list.d/roggan87-nr-raring.list.save

```
Because we have made changes to the operating system .. update the database.
```

sudo apt-get update
sudo apt-get upgrade

```
Post back with any reported errors. if all is good at this point try Software-center and advise of the results.

[INDENT][INDENT]workie great last long time ?
[/INDENT][/INDENT]

---

### Post by jesus-freak on 2013-09-06
I did all of what you said and still the software center won't work correctly. Here is the result of the latest codes that you gave me.

justdrea@justdrea-Satellite-A665:~$ sudo rm  /etc/apt/sources.list.d/roggan87-nr-raring.list
[sudo] password for justdrea: 
justdrea@justdrea-Satellite-A665:~$ sudo rm  /etc/apt/sources.list.d/roggan87-nr-raring.list.save
justdrea@justdrea-Satellite-A665:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg                            
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg [72 B]                       
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release.gpg [933 B]             
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports Release.gpg                     
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security Release.gpg [933 B]            
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner Sources                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner amd64 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages                        
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release [40.8 kB]               
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release.gpg                       
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                         
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release.gpg                       
Get:5 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release.gpg [316 B]             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports Release                         
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release.gpg                       
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security Release [40.8 kB]              
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main amd64 Packages                       
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted amd64 Packages                 
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe amd64 Packages                   
Get:7 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release [9,767 B]               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse amd64 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted i386 Packages                  
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release                           
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_PH              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_PH                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe i386 Packages                    
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse i386 Packages                  
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                       
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main amd64 Packages
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                       
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main i386 Packages
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Translation-en                 
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Sources                               
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Translation-en                   
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main amd64 Packages [164 kB]    
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main amd64 Packages               
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main i386 Packages                
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted amd64 Packages [14 B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe amd64 Packages [143 kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse amd64 Packages [3,702 B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main i386 Packages [163 kB]    
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted i386 Packages [14 B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe i386 Packages [144 kB]
Get:15 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main amd64 Packages [1,304 B]  
Get:16 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main i386 Packages [1,313 B]   
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse i386 Packages [3,871 B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en [77.7 kB]  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_PH                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Translation-en         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_PH                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_PH                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_PH                         
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main amd64 Packages               
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Translation-en [74.9 kB]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main i386 Packages                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_PH                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main amd64 Packages             
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted amd64 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe amd64 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse amd64 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main i386 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main Translation-en             
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages              
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe Translation-en         
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main amd64 Packages [97.8 kB] 
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted amd64 Packages [14 B]
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages              
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe amd64 Packages [33.7 kB]
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages               
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse amd64 Packages [3,702 B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main i386 Packages [97.0 kB]  
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted i386 Packages [14 B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe i386 Packages [34.3 kB]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse i386 Packages [3,871 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe Translation-en          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en_PH                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted Translation-en_PH
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_PH
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Fetched 1,142 kB in 1min 17s (14.8 kB/s)
Reading package lists... Done
justdrea@justdrea-Satellite-A665:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  minitube-ubuntu
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 869 kB of archives.
After this operation, 21.5 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [https://private-ppa.launchpad.net/commercial-ppa-uploaders/minitube-ubuntu/ubuntu/](https://private-ppa.launchpad.net/commercial-ppa-uploaders/minitube-ubuntu/ubuntu/) raring/main minitube-ubuntu amd64 2.1.3-0ubuntu1 [869 kB]
Fetched 869 kB in 5s (157 kB/s)          
(Reading database ... 415370 files and directories currently installed.)
Preparing to replace minitube-ubuntu 2.1.2-0ubuntu1 (using .../minitube-ubuntu_2.1.3-0ubuntu1_amd64.deb) ...
Unpacking replacement minitube-ubuntu ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up minitube-ubuntu (2.1.3-0ubuntu1) ...

---

### Post by Bashing-om on 2013-09-06
jesus-freak; Then;

As there is no direct problem with the package management system the problem must reside within USC ...
Try this:
```
rm -r ~/.cache/software-center
```
reboot and see:

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by jesus-freak on 2013-09-06
That didn't seem to do anything. Ran the code and rebooted and same problem.

---

### Post by Bashing-om on 2013-09-06
jesus-freak; Yuk,

Back to square one .. from terminal, start software-center and relay the errors.
See what we can cypher out once more.

[INDENT][INDENT]try try again
[/INDENT][/INDENT]

---

### Post by jesus-freak on 2013-09-06
justdrea@justdrea-Satellite-A665:~$ gksudo software-center
2013-09-07 11:20:05,849 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has no usable Address providers'
2013-09-07 11:20:06,193 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-09-07 11:20:06,195 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-09-07 11:20:06,202 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-09-07 11:20:06,202 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-09-07 11:20:06,274 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2013-09-07 11:20:09,757 - softwarecenter.ui.gtk3.widgets.exhibits - WARNING - download failed: '<class 'gi._glib.GError'>', 'Operation not supported'
2013-09-07 11:20:18,477 - softwarecenter.db.utils - INFO - software-center-agent finished with status 0
2013-09-07 11:20:20,886 - softwarecenter.ui.gtk3.widgets.exhibits - WARNING - download failed: '<class 'gi._glib.GError'>', 'Operation not supported'
justdrea@justdrea-Satellite-A665:~$

---

### Post by Bashing-om on 2013-09-06
jesus-freak; 
Presently stuck .. let me have a lot of time, and I will boot into something that has USC on it and do some poking about.

[INDENT][INDENT]be back soonest[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-09-07
jesus-freak;  Not much wiser now.

Still pondering,, for reference, here is the errors from a working USC.
> 
sysop1@1204-a:~$ software-center &
[1] 2099
sysop1@1204-a:~$ 2013-09-07 15:18:02,644 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-09-07 15:18:02,650 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-09-07 15:18:03,150 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-09-07 15:18:03,316 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-09-07 15:18:03,325 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2013-09-07 15:18:09,160 - softwarecenter.db.update - INFO - skipping region restricted app: 'Flaggame' (not whitelisted)
2013-09-07 15:18:09,321 - softwarecenter.db.update - INFO - skipping region restricted app: 'reEarCandy' (not whitelisted)
2013-09-07 15:18:10,758 - softwarecenter.db.update - INFO - skipping region restricted app: 'Comentarios Web' (not whitelisted)
2013-09-07 15:18:10,957 - softwarecenter.db.update - INFO - skipping region restricted app: 'Bulleti d'esquerra de Calonge i Sant Antoni ' (not whitelisted)
2013-09-07 15:18:12,551 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0
2013-09-07 15:18:12,552 - softwarecenter.db.database - INFO - reopen() database
2013-09-07 15:18:12,553 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True

This prior to clearing the "update" -pending- cache.

[INDENT][INDENT]back to look'n
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-09-07
jesus-freak; A bit of digging

This one is the biggy:
> 
 root - ERROR - Could not find any typelib for LaunchpadIntegration

lesser import is the geoclue.
Show the status of the following:
```

dpkg -l geoclue
dpkg -l geoclue-ubuntu-geoip
dpkg -l libgeoclue0
dpkg -l geoclue-hostip
###
dpkg -l launchpad-integration
dpkg -l gir1.2-launchpad-integration-*
dpkg -l python-gi-cairo

```
Expect this to give us indicators of where to look/why to look.

[INDENT][INDENT]hey we be look'n
[/INDENT][/INDENT]

---

### Post by jesus-freak on 2013-09-08
Alright, thanks for all the help

---

### Post by vasa1 on 2013-09-08
I can't help with your basic issue but I want to ask about the output of sudo apt-get update.

I see you have 
raring-backports 
amd64 Packages
i386 Packages
Translation-en_PH and 
[https://private-ppa.launchpad.net](https://private-ppa.launchpad.net)

Do you really need raring-backports? I think that that is enabled by default but I turned it off. 
Then why both amd64 and i386? 
And you have both "Translation-en" and "Translation-en_PH". I guess Translation-en_PH is a flavor of Translation-en but what does "PH" stand for?
And what is "private-ppa.launchpad.net"?

Hope you don't mind my asking more questions instead of helping!

---

### Post by jesus-freak on 2013-09-08
First of all let me tell you that I have only been using Linux for about 8 months so I'm a beginner. I have no idea what "Raring-backports" are or how to turn them off. I have no idea about the AMD64 and i386 either. I have an Intel 64 bit processor and I downloaded and installed the correct version of Ubuntu for my system. It runs really great other than this one issue. As for the Translation-en_PH, I would guess the PH stands for Philippines since that is where I live. I'm an American but I live here now. I would guess that since it says en_PH that it might be a simplified English because English is the second language here. But I've never seen any difference in the English on here. I have no idea what private-ppa.launchpad.net is. Maybe someone else can answer these questions better than I can. Thanks.

---

### Post by jesus-freak on 2013-09-08
justdrea@justdrea-Satellite-A665:~$ dpkg -l geoclue
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  geoclue        0.12.99-0ubu amd64        Geographic information framework
justdrea@justdrea-Satellite-A665:~$ dpkg -l geoclue-ubuntu-geoip
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  geoclue-ubuntu 1.0.1-0ubunt amd64        Provide positioning for GeoClue v
justdrea@justdrea-Satellite-A665:~$ dpkg -l libgeoclue0
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  libgeoclue0    0.12.99-0ubu amd64        C API for GeoClue
justdrea@justdrea-Satellite-A665:~$ dpkg -l geoclue-hostip
dpkg-query: no packages found matching geoclue-hostip




justdrea@justdrea-Satellite-A665:~$ dpkg -l launchpad-integration
dpkg-query: no packages found matching launchpad-integration
justdrea@justdrea-Satellite-A665:~$ dpkg -l gir1.2-launchpad-integration-*
dpkg-query: no packages found matching gir1.2-launchpad-integration-*
justdrea@justdrea-Satellite-A665:~$ dpkg -l python-gi-cairo
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  python-gi-cair 3.8.0-2ubunt amd64        Python Cairo bindings for the GOb

---

### Post by Bashing-om on 2013-09-08
jesus-freak; Arranging my thinking ->

8 months huh .. You have come a long way .. and done a lot. Let's see what we can do to get you even more comfortable with this - our operating system of choice.
1. We do need to clean up your sources; KISS always applies. Why do you need the 32 bit (i386) - as Vasa1 inquires ? ... all valid questions.

2. geoclue looks to be in order, but will require (re-)visiting when all else settles out.

3. The biggy in my eyes:
[quote]
justdrea@justdrea-Satellite-A665:~$ dpkg -l gir1.2-launchpad-integration-*
XX -> think this is OK .. will verify ---> Update: should have version 0.1.56.1 installed

dpkg-query: no packages found matching gir1.2-launchpad-integration-*
XX -> think this is OK .. will verify ---> Update: should have version 0.1.56.1 installed


justdrea@justdrea-Satellite-A665:~$ dpkg -l python-gi-cairo
UNKNOWN I show s/b 3.2.2-1~precis ,OP 3.8.0-2ubuntu -- How can you have a later version than I do ? As I am running this on version 12.04 fully updated.

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name Version Architecture Description
+++-==============-============-============-=================================
ii libgeoclue0 0.12.99-0ubu amd64 C API for GeoClue
XX -> looks good --> update I have 0.12.0-1ubu , How can you be behind if others are ahead in versions

justdrea@justdrea-Satellite-A665:~$ dpkg -l geoclue-hostip
dpkg-query: no packages found matching geoclue-hostip
XX -> this I do need to verify.

-------------------
How comfortable are you in editing system files ? need to look and maybe do some editing.

I will presently reboot into an install with USC and do some comparisons....

My Edit on updated info from me .. let's make sure we are on the same page:
my system kernel/info:
[quote]
Linux 1204-a 3.2.0-52-generic #78-Ubuntu SMP Fri Jul 26 16:21:44 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
[quote]
please post your output:
```

uname -a

```

See if we can get things straight.

[INDENT][INDENT]I will be back
[/INDENT][/INDENT]

---

### Post by jesus-freak on 2013-09-08
justdrea@justdrea-Satellite-A665:~$ uname -a
Linux justdrea-Satellite-A665 3.8.0-30-generic #44-Ubuntu SMP Thu Aug 22 20:52:24 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

As far as editing system files, I can do it as long as someone tells me what to do.

---

### Post by Bashing-om on 2013-09-08
jesus-freak;  good deal.

It is GMT-6 time here now .. and I am not think'n as clear as I need to be .. we will continue this in my AM.. starting with getting the needed files installed and then looking at a couple of files to make sure they are as needed.
Then I think .. think about cleaning up your system ( when USC is up and running)...

Will meet ya when I can boot into my 12.04 install ..

[INDENT][INDENT]all things work to the good ........
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-09-09
jesus-freak; Regret the delay in getting back at ya .. took a bit longer to get my chores done and back to the keyboard.

Anyway .. procedure,
Have the package manager do an audit on it's condition prior to installing the required assets for USC.
```

dpkg -C

```
that is with an upper case "c".
No return is a good thing .. if no return from that command proceed with:
```

sudo apt-get install launchpad-integration
sudo apt-get install gir1.2-launchpad-integration
sudo apt-get install python-gi-cairo

```
I want to "install" all of them due to my concern over versions in the packages. Any response "latest version installed" is acceptable, move on to next command. Any errors that is reported; we want to examine that content.

Reboot at this time and I hope that the software-center is functional. If still with a serious problem .. we will then next look at a couple of files ..and possibly make a correction. One of which has been corrected as of version  5.2.3 of software-center. - But we will look anyway to make sure.

And still remaining is geoclue's warnings.

[INDENT][INDENT]all things are possible
[/INDENT][/INDENT]

---

### Post by jesus-freak on 2013-09-09
Okay, the dpkg -C command didn't bring up anything so I preceeded to the next step. The first of the sudo apt codes installed fine. The second one returned this error

justdrea@justdrea-Satellite-A665:~$ sudo apt-get install gir1.2-launchpad-integration
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gir1.2-launchpad-integration
E: Couldn't find any package by regex 'gir1.2-launchpad-integration'


And the third one said it was already installed and up to date.

---

### Post by Bashing-om on 2013-09-09
jesus-freak;

I don't know what to think presently .. I will now boot back into 12.04 and see what the older kernel (3.2) version relates.

Back in a bit.

---

### Post by Bashing-om on 2013-09-09
jesus-freak; Hey, 
From a quick looksee in my version 12.04 .. that files is a gotta have ! -unless there is a big change in the 3.8 kernel that this interface is no longer in use ????
So let's see if we can find it.
```

apt-cache search gir1.2-launchpad-integration*

```

who said nothing changes but that all things remain the same

---

### Post by jesus-freak on 2013-09-09
No result at all with that command

---

### Post by Bashing-om on 2013-09-10
jesus-freak; Good and Bad !

My results:
> 
sysop1@1204-a:~$ apt-cache search gir1.2-launchpad-integration*
gir1.2-launchpad-integration-3.0 - library for launchpad integration (gir files)
sysop1@1204-a:~$ 

and reason why:
> 
sysop1@1204-a:~$ apt-cache show gir1.2-launchpad-integration-3.0
<snip>
Description-en: library for launchpad integration (gir files)
 The launchpad-integration tools provide an easy way to set menu items,
 for an application using GtkUIManager, pointing to the launchpad pages
 about a package. Users can get information about the used application here,
 translate it, ...
 .
 This package contains the gobject introspection information for the GTK+ 3.0
 version of the library.
<snip>



-------------
This proves conclusively that the kernel has changed... and I have not been troubleshooting your issue correctly.
No damage done .. but I am back to square 3 in resolving this issue.

[INDENT][INDENT]drop back 3 yards and punt
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-09-10
jesus-freak;

Starting again, show the output of:
```

software-center -V

```
I will see what I can correlate with the 3.8 series kernel.

[INDENT][INDENT]keep'n on keep'n on
[/INDENT][/INDENT]

---

### Post by jesus-freak on 2013-09-10
justdrea@justdrea-Satellite-A665:~$ software-center -V
Usage: software-center [options] [package-name | apturl | deb-file]

software-center: error: no such option: -V

---

### Post by Bashing-om on 2013-09-10
jesus-freak; well !

I had expected the -V option to return the version of software-center that you have installed.
Lemme think up another approach to get a handle on this.

I will be back
[INDENT][INDENT]but not shortly
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-09-10
jesus-freak; My morning to ya.

Back on this... here is a way to identify the version of software-center you have installed: 
Mine for comparison:
> 
software-center: error: no such option: -V
sysop1@1204-a:~$ dpkg -l software-center
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  software-cente 5.2.9          Utility for browsing, installing, and removi
sysop1@1204-a:~$

Your version ? show the output of:
```

dpkg -l software-center

```

I have an idea as to how to proceed !

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by jesus-freak on 2013-09-10
Here you go

justdrea@justdrea-Satellite-A665:~$ dpkg -l software-center
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  software-cente 5.6.0-0ubunt all          Utility for browsing, installing,

---

### Post by Bashing-om on 2013-09-10
jesus-freak; Thanks,

Here I go too ! Workin' onner
[INDENT][INDENT]I'll be back whenever[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-09-10
jesus-freak; Hey !

Let's do this, edit a particular file, as I understand in some circumstances a race condition is present.
The line of interest is 164, take a look and see if this expression exist:
> 
self.exhibit_banner.set_exhibits([FeaturedExhibit()])

with terminal code:
```

cat -n /usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py

```
If that line does exist in that file at line number 164, do: - copy and paste into terminal -
```

sudo cp /usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py /usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py-orig
gksudo gedit /usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py

```
Comment the line in the file lobbyview.py that contains that expression :
(to comment you've to put the character "#" in the begin of the line)
Save the file in gedit and closer all out.
Reboot with terminal code:
```

sudo shutdown -r now

```

Is the software-center now fully functional ?

[INDENT][INDENT]shortcut is worth the shot
[/INDENT][/INDENT]

---

### Post by jesus-freak on 2013-09-11
Okay, so this line is there self.exhibit_banner.set_exhibits([FeaturedExhibit()])

>   Comment the line in the file lobbyview.py that contains that expression :
(to comment you've to put the character "#" in the begin of the line)
Save the file in gedit and closer all out.
Reboot with terminal code:  

That contains what expression? I just want to be sure before I do anything stupid

---

### Post by mörgæs on 2013-09-11
Now the thread is a week long, and the problem persisted for two months before. Due to PPA's being added and removed the system might be in an unstable state, not only with regards to Software Centre. 

While I appreciate Bashing-om's effort I would just point to the option of a fresh install. Half an hour, problem solved.

---

### Post by jesus-freak on 2013-09-11
Okay, closed. I thought this was a place to get help and to learn but I guess the moderator is only interested in the quick or easy fix. I'm not going to bother with this forum anymore then.

---

### Post by mörgæs on 2013-09-11
It was written with my nerd-hat (not the moderator-hat) on and it was only an option to consider, not an order. I am afraid that you are on a looong journey, and other options might be more efficient. Yes, I promote solutions that are quick and easy.

Anyway, your decision.

---

### Post by VMC on 2013-09-11
The reason I came here was the amount of posts I saw. I noticed someone pointed to the fact you have both i386 and amd64 in your list. I think you replied you have a 64bit cpu, which is using the amd64. Don't know what your using the i386 stuff for.

Also the correct input of the software message is ```
software-center --version
```. We might look into what programs are installed on you system:
```
apt-cache pkgnames
```. It will be long so save it using redirection would help. Also, since the topic of software center error has come up. What's the output of : ```
apt-cache pkgnames|grep software*
```. Here's min, but I'm on Precise and not Raring:```
libsoftware-release-perlopendrim-lmp-softwareupdate
ti-omap4-software-channel
python-software-properties
software-properties-common
software-center
libsoftware-license-perl
software-properties-gtk
software-properties-kde
opendrim-lmp-softwareinventory
software-center-aptdaemon-plugins
lubuntu-software-center
```.

---

### Post by Bashing-om on 2013-09-11
jesus-freak; see all the above post .. I am here for the duration, whatever it takes to find the solution.

I am confident that VMC has greater experience/knowledge than my own and that mörgæs has our better interest at heart.
My own advise .. was that complete line that contains the  expression "self.exhibit_banner.set_exhibits([FeaturedExhibit()])" is to be commented out . Thus that line will not be parsed in the execution of that file. As that file is backed up a method exist to "undo" any harm. In this instance to revert back is simply remove the '#' character that was placed at the start of the line, save the file and you are back where you started from.

With the edit in the file, does USC function and what errors are now generated when starting USC from terminal ?

[INDENT][INDENT]and I am still learning, even after all these years
[/INDENT][/INDENT]

---

### Post by jesus-freak on 2013-09-11
I think I'm going to throw in the towel on this one. I really appreciate all your time!! I've learned a lot about how things work and that was really the point of all this. I have too many significant problems to deal with in my wife's computer and trying to work on both at the same time is way to much. Thanks again.

---

### Post by Bashing-om on 2013-09-11
jesus-freak; Understand !

Not at all a problem. The quick fix is to (re-)install.

[INDENT][INDENT]most learned is fighting a problem to resolution.[/INDENT][/INDENT]

---

