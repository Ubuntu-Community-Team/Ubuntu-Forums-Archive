---
title: "Need help to fix Sources List"
date: 2012-11-19
forum: General Help
---

### Post by lumaja on 2012-11-19
Seems to me I have problems with “Sources List”  
 During installation of some applications which are known  to don’t give any problems, my doesn’t
 install with some errors which don’t understand.
 Did sudo gedit /etc/apt/sources.list.
 

 # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted 
  
 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
 # newer versions of the distribution. 
  
 ## Major bug fix updates produced after the final release of the 
 ## distribution. 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
 ## team. Also, please note that software in universe WILL NOT receive any 
 ## review or updates from the Ubuntu security team. 
 deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise universe 
 deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise universe 
 deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-updates universe 
 deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-updates universe 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 ## team, and may not be under a free licence. Please satisfy yourself as to  
 ## your rights to use the software. Also, please note that software in  
 ## multiverse WILL NOT receive any review or updates from the Ubuntu 
 ## security team. 
  
 ## N.B. software from this repository may not have been tested as 
 ## extensively as that contained in the main release, although it includes 
 ## newer versions of some applications which may provide useful features. 
 ## Also, please note that software in backports WILL NOT receive any review 
 ## or updates from the Ubuntu security team. 
  
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe 
  
 ## Uncomment the following two lines to add software from Canonical's 
 ## 'partner' repository. 
 ## This software is not part of Ubuntu, but is offered by Canonical and the 
 ## respective vendors as a service to Ubuntu users. 
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner 
 # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner 
  
 ## This software is not part of Ubuntu, but is offered by third-party 
 ## developers who want to ship their latest software. 
 deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main 
 deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main 
 deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib
 

 Again as I don't understand I am asking for help to correct this.  
 Thank you

---

### Post by SlugSlug on 2012-11-19
unless you need the source files you can hash out all the deb-src lines
Make 
```
deb-src
```look like
```
# deb-src
```
please post output of 

```
sudo apt-get update
```

---

### Post by lumaja on 2012-11-19
Terminal output
 

 luis@luis-G41M-Combo:~$ deb-src 
 deb-src: command not found 
 

 luis@luis-G41M-Combo:~$ # deb-src 
 

 luis@luis-G41M-Combo:~$ sudo apt-get update 
 [sudo] password for luis:  
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                              
 Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise InRelease                              
 Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates InRelease                      
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                  
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise Release.gpg                            
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates Release.gpg                    
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                       
 Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise InRelease                            
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                            
 Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                       
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise Release                                
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates Release                        
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                     
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                    
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe Sources                       
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe i386 Packages                 
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe TranslationIndex              
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib i386 Packages                
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe Sources               
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe i386 Packages         
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe TranslationIndex      
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                         
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                  
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe Translation-en                
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                               
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe Translation-en        
 Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib TranslationIndex             
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex               
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources                
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                         
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                      
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages          
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex       
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en         
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex            
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex            
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                     
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages               
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex            
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                     
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages               
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex            
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                     
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages               
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex            
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                     
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages               
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex            
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                     
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages               
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex            
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                     
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages               
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex            
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_ZA              
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_ZA                     
 Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib Translation-en_ZA  
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en       
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en              
 Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib Translation-en               
 Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
   404  Not Found 
 Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
   404  Not Found 
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Fetched 72 B in 9s (7 B/s)                                                      
 W: Failed to fetch [http://ppa.launchpad.net/atarero/atareo/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/atarero/atareo/ubuntu/dists/precise/main/source/Sources)  404  Not Found 
  
 W: Failed to fetch [http://ppa.launchpad.net/atarero/atareo/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/atarero/atareo/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found 
  
 E: Some index files failed to download. They have been ignored, or old ones used instead. 
 luis@luis-G41M-Combo:~$

---

### Post by wojox on 2012-11-19
[Disable the PPA's]("http://askubuntu.com/a/143206/2973")

---

### Post by lumaja on 2012-11-20
Following  your last post it shows there still duplicate sources I cant find them in Repositories
 How to correct this?
 

 luis@luis-G41M-Combo:~$ sudo apt-get update 
 [sudo] password for luis:  
 Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise InRelease 
 Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates InRelease                      
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise Release.gpg                            
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates Release.gpg                    
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise Release                                
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                              
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                       
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates Release                        
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                  
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe Sources                       
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe i386 Packages                 
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe TranslationIndex              
 Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise InRelease                            
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                            
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe Sources               
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe i386 Packages         
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe TranslationIndex      
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                     
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe Translation-en                
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe Translation-en        
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                         
 Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib i386 Packages                
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                          
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                  
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources      
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages               
 Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib TranslationIndex             
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex               
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                      
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages          
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en 
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_ZA    
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en       
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_ZA 
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en 
 Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib Translation-en_ZA 
 Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib Translation-en 
 Reading package lists... Done 
 W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages) 
 W: You may want to run apt-get update to correct these problems 
 luis@luis-G41M-Combo:~$

---

### Post by lisati on 2012-11-21
What happens when you try the suggestion given?
```
sudo apt-get update
```

---

### Post by lumaja on 2012-11-21
Results of your request.

luis@luis-G41M-Combo:~$ sudo apt-get update
[sudo] password for luis: 
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise InRelease                             
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise Release.gpg                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates Release.gpg                   
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise Release                               
Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise InRelease                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe Sources                      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe TranslationIndex             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe Sources              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe i386 Packages        
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages       
Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib TranslationIndex  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex           
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_ZA   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_ZA          
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib Translation-en_ZA
Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib Translation-en
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
luis@luis-G41M-Combo:~$

---

### Post by cwsnyder on 2012-11-21
If you have Synaptic package manager installed, you can manage your sources from a GUI instead of just the command line by going to Settings >> Repositories and check for duplicates in the Other software.

On the command line it would be:```
sudo nano /etc/apt/sources.list
``` or whatever your preferred editor, and look for lines which are exact duplicates.

---

### Post by lumaja on 2012-11-21
Enter in the Terminal “sudo nano /etc/apt/sources.list”.
 There is a  ENTIRELY UNSUPPORTED and a reference to ”ZA” this mighty be South Africa where reside.
 

 # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ pr$ 
  
 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
 # newer versions of the distribution. 
  
 ## Major bug fix updates produced after the final release of the 
 ## distribution. 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
 ## team. Also, please note that software in universe WILL NOT receive any 
 ## review or updates from the Ubuntu security team. 
 deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise universe 
 deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise universe 
 deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-updates universe 
 deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-updates universe 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 ## team, and may not be under a free licence. Please satisfy yourself as to  
 ## your rights to use the software. Also, please note that software in  
 ## multiverse WILL NOT receive any review or updates from the Ubuntu 
 ## security team. 
  
 ## N.B. software from this repository may not have been tested as 
 ## extensively as that contained in the main release, although it includes 
 ## newer versions of some applications which may provide useful features. 
 ## Also, please note that software in backports WILL NOT receive any review 
 ## or updates from the Ubuntu security team. 
  
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe 
  
 ## Uncomment the following two lines to add software from Canonical's 
 ## 'partner' repository. 
 ## This software is not part of Ubuntu, but is offered by Canonical and the 
 ## respective vendors as a service to Ubuntu users. 
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner 
 # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner 
  
 ## This software is not part of Ubuntu, but is offered by third-party 
 ## developers who want to ship their latest software. 
 deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main 
 # deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main 
 deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib

---

### Post by cwsnyder on 2012-11-21
I don't see anything in your /etc/apt/sources.list which should be causing your problems with updating your file list for an upgrade.  Ubuntu Universe may duplicate some files in extras.ubuntu.com, but should not cause your errors with [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner.

One last try, could you list your /etc/apt/preferences file to check for any pinning?

---

### Post by lumaja on 2012-11-21
/etc/apt/preferences file
 The preferences name is “preferences.d” there’s nothing on the page and on the bottom is “ 0 items, Free space: 195.GB
 

 Refer to my previous reply the entry ENTIRELY UNSUPPORTED and a reference to ”ZA” should I carry on update from the same Software Sources or should I change.
 

  This started from when I was Installing “Sweet Home 3D” with Synaptic there was a error “ could not apply changes! Fix broken packages first” I contact they support was informed to contact Ubuntu and after all this exercise just been in Synaptic again to install the some application the result was the same about “fix broken packages first” and I don’t know what I should do next.     
  Thank you for your great support.

---

### Post by cwsnyder on 2012-11-21
In Synaptic, choose from the menu, Edit >> Fix Broken Packages ,then choose the Apply check-mark button.

---

### Post by lumaja on 2012-11-24
I tried your suggestion, nothing happens and the Apply  check-mark  doesn’t change to green.
 I tried various times with same result. I want do install another application and on Apply
 to install an warning window opens.
 

         “Could not apply changes! Fix broken package first”.
 

 Unmark the package and then Fix Broken Packages again, an warning window opens.
 

         E: Unable to correct problems, you have held broken packages. 
         E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held             packages. 
         E: Unable to correct dependencies.
 Seems there is serious problems with Synaptic.
 Should I open another Thread about this subject.

---

### Post by cwsnyder on 2012-11-24
See if you have the same problems with the parent package **apt-get**.  **apt-get** is used by aptitude, synaptic, & update-manager.  The terminal commands to fix broken packages are:```
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by monkeybrain2012 on 2012-11-24
Well the ppa entries may be in the directory /etc/apt/sources.list.d instead of on the file /etc/apt/sources.list

You can fix this by opening the Software Centre, go to Edit > Repositories and Other Software to look at what ppa you have activated. If you have double entries just remove one. Then reload SC and that should fix it.

---

### Post by monkeybrain2012 on 2012-11-24
> **lumaja said:**
> I tried your suggestion, nothing happens and the Apply  check-mark  doesn’t change to green.
 I tried various times with same result. I want do install another application and on Apply
 to install an warning window opens.
 

         “Could not apply changes! Fix broken package first”.
 

 Unmark the package and then Fix Broken Packages again, an warning window opens.
 

         E: Unable to correct problems, you have held broken packages. 
         E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held             packages. 
         E: Unable to correct dependencies.
 Seems there is serious problems with Synaptic.
 Should I open another Thread about this subject.

You may need to reload synaptic after fixing broken package.

---

### Post by lumaja on 2012-11-25
Your request output:
 

 luis@luis-G41M-Combo:~$ sudo apt-get -f install  
 [sudo] password for luis:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following packages were automatically installed and are no longer required:  
   janino python-pywapi libdirectfb-extra libhal1 libjava3d-jni libitext-java  
   python-bittorrent java3ds-fileloader libjava3d-java libsunflow-java  
   libvecmath-java  
 Use 'apt-get autoremove' to remove them.  
 0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.  
 luis@luis-G41M-Combo:~$ sudo apt-get update  
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                              
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                                 
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                        
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                  
 Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise InRelease                  
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                               
 Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [71 B]                       
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                   
 Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib i386 Packages                
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                          
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                  
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages          
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex     
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages               
 Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib TranslationIndex   
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex       
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex            
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en         
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_ZA    
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en       
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_ZA  
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en  
 Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib Translation-en_ZA  
 Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib Translation-en  
 Fetched 71 B in 5s (13 B/s)  
 Reading package lists... Done  
 luis@luis-G41M-Combo:~$ sudo apt-get dist-upgrade  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 Calculating upgrade... Done  
 The following NEW packages will be installed:  
   skype-bin  
 The following packages will be upgraded:  
   skype  
 1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.  
 Need to get 30,7 MB of archives.  
 After this operation, 1 415 kB of additional disk space will be used.  
 Do you want to continue [Y/n]? Y  
 Get:1 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner skype i386 4.1.0.20.0-0ubuntu0.12.04.1 [15,3 kB]  
 Get:2 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner skype-bin i386 4.1.0.20.0-0ubuntu0.12.04.1 [30,6 MB]  
 Fetched 30,7 MB in 4min 52s (105 kB/s)                                          
 (Reading database ... 338436 files and directories currently installed.)  
 Preparing to replace skype 4.0.0.8-1 (using .../skype_4.1.0.20.0-0ubuntu0.12.04.1_i386.deb) ...  
 Unpacking replacement skype ...  
 Selecting previously unselected package skype-bin.  
 Unpacking skype-bin (from .../skype-bin_4.1.0.20.0-0ubuntu0.12.04.1_i386.deb) ...  
 Processing triggers for bamfdaemon ...  
 Rebuilding /usr/share/applications/bamf.index...  
 Processing triggers for desktop-file-utils ...  
 Processing triggers for gnome-menus ... 
 Setting up skype-bin (4.1.0.20.0-0ubuntu0.12.04.1) ...  
 Setting up skype (4.1.0.20.0-0ubuntu0.12.04.1) ...  
 luis@luis-G41M-Combo:~$  
 

 After this I shut down and restart went to Synaptic tried install the previous package the result was the same as before.
 

 

 Answer to **monkeybrain2012,**
 Before I do anything let me show my Other Software.
 

 **Other Software **contains the following
 **Canonical Parterners **           (Disable)
 Software package by Canonical for their partners
 **Canonical Partners** (Source Code)          (Disable)
 Software packaged by Canonical for their partners
 **Idependent**              (Enable)  
 Provide by third-party software developers        
 **Idependent** (Source Code)         (Disable)
 Provided by third- party software developers
 h[ttp://download.virtualbox.org/virtualbox/debian]("http://download.virtualbox.org/virtualbox/debian") precise contrib       (Enable)
 **Canonical Partners **Added by Software-center         (Enable)
 Software packaged by Canonical for their partners
 

 Then there is 19 ppa that I disable.

---

### Post by dino99 on 2012-11-25
is it done ?

[HTML]The following packages were automatically installed and are no longer required: 
janino python-pywapi libdirectfb-extra libhal1 libjava3d-jni libitext-java 
python-bittorrent java3ds-fileloader libjava3d-java libsunflow-java 
libvecmath-java 
Use 'apt-get autoremove' to remove them.[/HTML]

sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean

sudo apt-get update
sudo apt-get install -f

---

### Post by lumaja on 2012-11-26
I tried your idea with sudo apt-get autoremove, result follows.
 

 luis@luis-G41M-Combo:~$ sudo apt-get autoremove  
 [sudo] password for luis:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following packages will be REMOVED: 
   janino java3ds-fileloader libdirectfb-extra libhal1 libitext-java  
   libjava3d-java libjava3d-jni libsunflow-java libvecmath-java  
   python-bittorrent python-pywapi  
 0 upgraded, 0 newly installed, 11 to remove and 0 not upgraded.  
 After this operation, 8 062 kB disk space will be freed.  
 Do you want to continue [Y/n]? Y  
 (Reading database ... 338436 files and directories currently installed.)  
 Removing libsunflow-java ...  
 Removing janino ...  
 Removing java3ds-fileloader ...  
 Removing libdirectfb-extra ...  
 Removing libhal1 ...  
 Removing libitext-java ...  
 Removing libjava3d-java ...  
 Removing libjava3d-jni ...  
 Removing libvecmath-java ...  
 Removing python-bittorrent ...  
 Removing python-pywapi ...  
 Processing triggers for man-db ...  
 Processing triggers for libc-bin ...  
 ldconfig deferred processing now taking place  
 Processing triggers for python-support ...  
 luis@luis-G41M-Combo:~$ sudo apt-get autoclean  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 Del lsb-invalid-mta 4.0-0ubuntu20.2 [4 576 B]  
 Del ubuntu-tweak 0.8.3-0~bzr1936+20121105~precise1 [908 kB]  
 Del psensor-common 0.6.2.16-1ubuntu4.1 [7 058 B]  
 Del libqt4-webkit 4:4.8.1-0ubuntu4.3 [7 802 B]  
 Del gnome-shell-extension-weather 0.2-0+20121109~precise1 [43,5 kB]  
 Del ubuntu-tweak 0.8.3-0~bzr1939+20121116~precise1 [907 kB]  
 Del psensor 0.6.2.16-1ubuntu4.1 [53,7 kB]  
 luis@luis-G41M-Combo:~$ sudo apt-get clean  
 luis@luis-G41M-Combo:~$ sudo apt-get update  
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                              
 Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise InRelease                            
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                       
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                  
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                            
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                     
 Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]             
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                
 Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib i386 Packages                
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                         
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                    
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                  
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages          
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages               
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex     
 Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib TranslationIndex   
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex       
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex            
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en         
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_ZA    
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en       
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_ZA  
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en  
 Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib Translation-en_ZA  
 Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib Translation-en  
 Fetched 72 B in 5s (12 B/s)  
 Reading package lists... Done  
 luis@luis-G41M-Combo:~$ sudo apt-get install -f  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.  
 luis@luis-G41M-Combo:~$  
 

 I don’t know what all this is, went to Synaptic trying again to install the application and same
 warning as before come up.
 Then as I want to install other application on the future I tried to do so, and the result follows .
 

 Sweet Home 3D  -  (this is the application that gave the warning first time)  **Warning**.
 Skrooge  -  **Warning**.
 Grisbi  -  can be installed no warning.
 Osmo  -  can be installed no warning.

---

### Post by lumaja on 2012-11-30
I post a reply a few days ago, as dint had no answer yet, I would like to know if the problem is fixed or what?.
 Thank you

---

### Post by ibjsb4 on 2012-11-30
Did you follow wojox's suggestion (post#4)?  Third party software?

---

### Post by rayd5 on 2012-11-30
I have been trapped in the same problem for more than a couple of days. But I found
that it is not only the sources file that prevents one from accessing the software 
repositories.  After setting up the sources file, there is an APT configuration file that
needs to be edited. In this file , /etc/apt/apt.conf, add the following lines (for 
two protocols in this case, http & ftp):
Acquire::http::proxy "http://<username>:<password>@<proxy address>:<port>/"; Acquire::ftp::proxy "ftp://<username>:<password>@<proxy address>:<port>/"; (with the appropriate values for username,passwords, proxy address &
port). This is if you want to access the respositories through the
proxy.

The link here explains this much clearly:
 [http://askubuntu.com/questions/89437/how-to-install-packages-with-apt-get-on-a-system-connected-via-proxy](http://askubuntu.com/questions/89437/how-to-install-packages-with-apt-get-on-a-system-connected-via-proxy)

I hope this will be useful to someone.

---

### Post by lumaja on 2012-12-01
To ibjsb4,
 

 I follow wojox's suggestion just after I receive it.
 

 My Repository:
 Ubuntu Software: -  Community-maintained free and open-source software (universe). the only enable one.
 Other Software:
 Independent
 [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib
 Canonical Partners Added by software-center Software packaged by Canonical for their partners
 [SIZE=3]The only enable ones, the others which are all ppa are disable.[/SIZE]

---

### Post by geodome on 2012-12-01
Hi, 

The software updater constantly tries to download from [https://sg.archive.ubuntu.com](https://sg.archive.ubuntu.com) which I believe to be an invalid address. How do I change the software updater settings such that it will download updates from another address? As a result, I can't get the latest update for LibreOffice.

LATEST UPDATE: I have figured out how to change the server settings for the Ubuntu software update.

---

