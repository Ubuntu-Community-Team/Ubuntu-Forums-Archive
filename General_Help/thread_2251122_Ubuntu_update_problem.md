---
title: "Ubuntu update problem"
date: 2014-11-02
forum: General Help
---

### Post by snowflake2 on 2014-11-02
Hi, I have Ubuntu 14.04.01 LTS dualboot with win8. Am total linux newbie and have some issues with updating, could you please give me some pointers?

Thanks a lot

When I run apt-get update I get the following 

```


roland@roland-Lenovo-IdeaPad-S500:~$ sudo apt-get update
[sudo] password for roland: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty InRelease                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-updates InRelease                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-updates Release.gpg                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease             
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-backports Release.gpg        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease                       
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty Release                      
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]           
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-updates Release                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-backports Release                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty/universe Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources 
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty/multiverse Sources        
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty/main amd64 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources 
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty/universe amd64 Packages   
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty/multiverse amd64 Packages 
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [151 kB]
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty/main Translation-en                
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty/multiverse Translation-en          
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty/restricted Translation-en          
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty/universe Translation-en            
Get:4 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-updates/main Sources [134 kB]        
Get:5 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-updates/restricted Sources [1'408 B] 
Get:6 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-updates/universe Sources [89.3 kB]   
Get:7 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-updates/multiverse Sources [3'517 B] 
Get:8 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-updates/main amd64 Packages [352 kB] 
Get:9 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [5'820 B]
Get:10 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-updates/universe amd64 Packages [216 kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease                         
Get:11 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [9'365 B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg [933 B]                    
Get:13 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-updates/main i386 Packages [346 kB] 
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release.gpg [933 B]            
Get:15 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-updates/restricted i386 Packages [5'820 B]
Get:16 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-updates/universe i386 Packages [216 kB]
Get:17 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [9'546 B]
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                                   
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-backports/main amd64 Packages          
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release [59.7 kB]              
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-backports/restricted amd64 Packages    
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-backports/universe amd64 Packages      
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages    
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages       
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages         
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty-backports/universe Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) trusty/universe Translation-en_US             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main amd64 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted amd64 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en                 
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main amd64 Packages [352 kB]   
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted amd64 Packages [5'820 B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages [346 kB]    
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages [5'820 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_US              
Fetched 2'311 kB in 35s (65.9 kB/s)                                            
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)  trusty-security/main amd64 Packages  (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)  trusty-security/restricted amd64 Packages  (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)  trusty-security/main i386 Packages  (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)  trusty-security/restricted i386 Packages  (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems



```

---

### Post by Bucky Ball on 2014-11-02
Open your Software Sources (not using Ubuntu so not sure if you can get there directly, but Software Updater>Settings in the bottom left will).

Go to 'Other Software' tab. Check for duplicates of the repositories in the error messages. Disable one of them so it leaves one still active. Update again and see what happens. If that doesn't fix, we'll dig deeper and check the sources file directly.

---

### Post by flaymond on 2014-11-02
Hello mate! I'm a newbie too...but I think i can fix your problems. Try alternative..using GUI....go to app search top left of your ubuntu...type Software Updater..and click it...Ubuntu update just for the software...because Linux is a kernel....Linux not an OS (but it will be one and much better than windows if you set up your Linux with appropriate softwares)...Maybe my information is not incorrect (sorry if i make a mistake)...but you can still try it..who knows?

---

### Post by Bucky Ball on 2014-11-02
You're advising the OP to do an update, which is what they are already doing when they encounter the problem they posted about. Please read all posts carefully prior to posting and try and be clear and concise. Your post is hard to follow (particularly for a newcomer) and not sure how the information contained in it is relevant as it is advising them to replicate their issue by updating. :-k

;)

---

### Post by snowflake2 on 2014-11-02
yep found the duplicate, disabled, works perfect now.  Much obliged, thanks! 

Interprog, thanks too mate.

---

### Post by Bucky Ball on 2014-11-02
Excellent. Please follow the second link in my signature to mark the thread as solved and help future travellers. Good luck. ;)

---

### Post by flaymond on 2014-11-02
Im not saying that my answer is 100% percent accurate...and for a newbie...I need to learn a lot....and that dont mean i cannot help anyone, with my little experience....and like i said in previous reply.....you can try it..who knows? (sorry...if im rude...dont ban me please!)

---

### Post by Bucky Ball on 2014-11-02
> **InterProg said:**
>  (sorry...if im rude...dont ban me please!)

Not at all. Enjoy the forums and good luck. ;)

---

