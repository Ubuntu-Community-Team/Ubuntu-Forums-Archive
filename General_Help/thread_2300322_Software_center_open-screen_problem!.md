---
title: "Software center open-screen problem!"
date: 2015-10-25
forum: General Help
---

### Post by dachuu25 on 2015-10-25
my software-center have this problem and I don't know how to solve out. Please help!

[ATTACH=CONFIG]265151[/ATTACH]

---

### Post by Bucky Ball on 2015-10-25
Welcome. Can you open a terminal and run these commands one at a time thanks:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

Report any and all errors you get between code tags (see last link in my signature).

---

### Post by dachuu25 on 2015-10-25
Sorry but I have tried like you said and... nothing happens :(

---

### Post by Bucky Ball on 2015-10-25
Please tell us exactly what happens when you hit return after inputting this command:

```
sudo apt-get update
```

... in a terminal. You will get output of some kind when the machine updates. Might be an error at the end, might be just the machine updating normally, but there will be something.

When you say nothing happens, do you mean you get no error messages, or literally nothing happens?

---

### Post by dachuu25 on 2015-10-25
Here they are: > Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily InRelease
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-updates InRelease                          
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-backports InRelease                        
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-security InRelease                         
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily/main Sources                               
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily/restricted Sources                         
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily/universe Sources                           
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily/multiverse Sources                         
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily/main amd64 Packages                        
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily/restricted amd64 Packages                  
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily/universe amd64 Packages                    
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily/multiverse amd64 Packages                  
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily/main i386 Packages                         
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily/restricted i386 Packages      
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily/universe i386 Packages        
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily/multiverse i386 Packages      
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily/main Translation-en                        
Hit [http://archive.canonical.com](http://archive.canonical.com) wily InRelease                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease                                    
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily/multiverse Translation-en                  
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily/restricted Translation-en                  
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily/universe Translation-en       
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-updates/main Sources          
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-updates/restricted Sources                 
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-updates/universe Sources                   
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-updates/multiverse Sources                 
Hit [http://archive.canonical.com](http://archive.canonical.com) vivid InRelease                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease                                    
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-updates/main amd64 Packages                
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-updates/restricted amd64 Packages          
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-updates/universe amd64 Packages
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-updates/multiverse amd64 Packages
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-updates/main i386 Packages    
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-updates/restricted i386 Packages           
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-updates/universe i386 Packages             
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-updates/multiverse i386 Packages           
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-updates/main Translation-en                
Hit [http://archive.canonical.com](http://archive.canonical.com) wily/partner amd64 Packages                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease                                    
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-updates/multiverse Translation-en
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-updates/restricted Translation-en
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-updates/universe Translation-en            
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-backports/main Sources                     
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-backports/restricted Sources               
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-backports/universe Sources     
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-backports/multiverse Sources               
Hit [http://archive.canonical.com](http://archive.canonical.com) wily/partner i386 Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease                                    
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-backports/main amd64 Packages              
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-backports/restricted amd64 Packages        
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-backports/universe amd64 Packages          
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-backports/multiverse amd64 Packages        
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-backports/main i386 Packages               
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-backports/restricted i386 Packages
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-backports/universe i386 Packages
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-backports/multiverse i386 Packages
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-backports/main Translation-en  
Hit [http://archive.canonical.com](http://archive.canonical.com) wily/partner Translation-en       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease                                    
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-backports/multiverse Translation-en        
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-backports/restricted Translation-en        
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-backports/universe Translation-en
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-security/main Sources                      
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-security/restricted Sources                
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-security/universe Sources                  
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-security/multiverse Sources                
Hit [http://archive.canonical.com](http://archive.canonical.com) vivid/partner Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease                        
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-security/main amd64 Packages               
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-security/restricted amd64 Packages
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-security/universe amd64 Packages
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-security/multiverse amd64 Packages
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-security/main i386 Packages    
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-security/restricted i386 Packages
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-security/universe i386 Packages
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-security/multiverse i386 Packages
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-security/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease   
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-security/multiverse Translation-en         
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-security/restricted Translation-en
Hit [http://opensource.xtdv.net](http://opensource.xtdv.net) wily-security/universe Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Sources                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Sources 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily Release.gpg  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Sources                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily Release                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Sources                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en                          
Reading package lists... Done                       

---

### Post by Bucky Ball on 2015-10-25
Ok. Now the other two:

```

sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

Only post the errors, if there are any. If you are asked to choose yes or no for upgrades, choose yes.

These commands will not upgrade your release to a newer one, only the software in your current install, if it needs it.

I've seen a few other threads with problems in SCentre in the newly released Wily so you don't seem to be alone. You might have a sniff about to see if someone else has solved this.

---

### Post by dachuu25 on 2015-10-25
Both of them printed out this: > Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by dachuu25 on 2015-10-25
Although they are disappear in the main page, they're still appear in search page.[ATTACH=CONFIG]265155[/ATTACH]

---

