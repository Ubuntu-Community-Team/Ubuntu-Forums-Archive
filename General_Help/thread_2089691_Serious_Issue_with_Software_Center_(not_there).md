---
title: "Serious Issue with Software Center (not there?)"
date: 2012-11-30
forum: General Help
---

### Post by romber on 2012-11-30
Hi Everyone,

To start, I have Ubuntu 12.10 x64.

So I have googled this problem many times, and I honestly don't think there is a solution to this. Anyways, I got this error:

"An error occurred, Please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 

'Error: Opening the cache (E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_quantal_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.)'. This usually means that your installed packages have unmet dependencies

So I can't click the Package Manager (actually, I'm not sure what right-click menu means and if Package Manager is the same as Software Center). When I do click on the Package Manager, it opens for a second and then closes and normally shows me a 'Send Error' box. When I click update through the error icon (white minus sign on red background at the top near the date), software updater fails.

I have tried many of the terminal commands, with no success. Actually, as far as I can tell is anything using "apt-get" won't work properly.

Here I did "sudo apt-get update" and this is what I got```
Ign http://dl.google.com stable InRelease
Ign http://extras.ubuntu.com quantal InRelease                                 
Ign http://us.archive.ubuntu.com quantal InRelease                             
Ign http://dl.google.com stable InRelease                                      
Hit http://extras.ubuntu.com quantal Release.gpg                     
Ign http://security.ubuntu.com quantal-security InRelease            
Hit http://dl.google.com stable Release.gpg                                    
Ign http://us.archive.ubuntu.com quantal-updates InRelease                     
Hit http://extras.ubuntu.com quantal Release                                   
Hit http://dl.google.com stable Release.gpg                                    
Ign http://us.archive.ubuntu.com quantal-backports InRelease                   
Hit http://dl.google.com stable Release        
Hit http://us.archive.ubuntu.com quantal Release.gpg                           
Hit http://dl.google.com stable Release                                        
Get:1 http://extras.ubuntu.com quantal/main Sources [1,702 B]                  
Get:2 http://us.archive.ubuntu.com quantal-updates Release.gpg [933 B]         
Get:3 http://dl.google.com stable/main amd64 Packages [1,225 B]                
Get:4 http://dl.google.com stable/main i386 Packages [1,242 B]                 
Get:5 http://extras.ubuntu.com quantal/main amd64 Packages [2,279 B]           
Hit http://us.archive.ubuntu.com quantal-backports Release.gpg                 
Get:6 http://security.ubuntu.com quantal-security Release.gpg [933 B]          
Hit http://us.archive.ubuntu.com quantal Release                               
Get:7 http://us.archive.ubuntu.com quantal-updates Release [49.6 kB]           
Get:8 http://extras.ubuntu.com quantal/main i386 Packages [2,261 B]            
Get:9 http://dl.google.com stable/main amd64 Packages [663 B]                  
Get:10 http://dl.google.com stable/main i386 Packages [643 B]                  
Get:11 http://security.ubuntu.com quantal-security Release [49.6 kB]           
Hit http://us.archive.ubuntu.com quantal-backports Release                     
Get:12 http://us.archive.ubuntu.com quantal/main Sources [872 kB]              
Ign http://extras.ubuntu.com quantal/main Translation-en_US                    
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                
Get:13 http://security.ubuntu.com quantal-security/main Sources [14.4 kB]      
Get:14 http://security.ubuntu.com quantal-security/restricted Sources [14 B]   
Get:15 http://security.ubuntu.com quantal-security/universe Sources [5,417 B]  
Get:16 http://security.ubuntu.com quantal-security/multiverse Sources [695 B]  
Get:17 http://security.ubuntu.com quantal-security/main amd64 Packages [44.9 kB]
Get:18 http://us.archive.ubuntu.com quantal/restricted Sources [5,646 B]       
Get:19 http://us.archive.ubuntu.com quantal/universe Sources [5,522 kB]        
Get:20 http://security.ubuntu.com quantal-security/restricted amd64 Packages [14 B]
Get:21 http://security.ubuntu.com quantal-security/universe amd64 Packages [14.9 kB]
Get:22 http://security.ubuntu.com quantal-security/multiverse amd64 Packages [1,151 B]
Get:23 http://security.ubuntu.com quantal-security/main i386 Packages [44.9 kB]
Get:24 http://security.ubuntu.com quantal-security/restricted i386 Packages [14 B]
Get:25 http://security.ubuntu.com quantal-security/universe i386 Packages [14.9 kB]
Get:26 http://security.ubuntu.com quantal-security/multiverse i386 Packages [1,394 B]
Hit http://security.ubuntu.com quantal-security/main Translation-en            
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en      
Hit http://security.ubuntu.com quantal-security/restricted Translation-en      
Hit http://security.ubuntu.com quantal-security/universe Translation-en        
Ign http://security.ubuntu.com quantal-security/main Translation-en_US         
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US   
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US   
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US     
Get:27 http://us.archive.ubuntu.com quantal/multiverse Sources [166 kB]        
Get:28 http://us.archive.ubuntu.com quantal/main amd64 Packages [1,137 kB]     
Get:29 http://us.archive.ubuntu.com quantal/restricted amd64 Packages [8,369 B]
Get:30 http://us.archive.ubuntu.com quantal/universe amd64 Packages [5,274 kB] 
Get:31 http://us.archive.ubuntu.com quantal/multiverse amd64 Packages [131 kB] 
Get:32 http://us.archive.ubuntu.com quantal/main i386 Packages [1,136 kB]      
Get:33 http://us.archive.ubuntu.com quantal/restricted i386 Packages [8,387 B] 
Get:34 http://us.archive.ubuntu.com quantal/universe i386 Packages [5,285 kB]  
Get:35 http://us.archive.ubuntu.com quantal/multiverse i386 Packages [133 kB]  
Hit http://us.archive.ubuntu.com quantal/main Translation-en                   
Hit http://us.archive.ubuntu.com quantal/multiverse Translation-en             
Hit http://us.archive.ubuntu.com quantal/restricted Translation-en             
Hit http://us.archive.ubuntu.com quantal/universe Translation-en               
Get:36 http://us.archive.ubuntu.com quantal-updates/main Sources [46.1 kB]     
Get:37 http://us.archive.ubuntu.com quantal-updates/restricted Sources [889 B] 
Get:38 http://us.archive.ubuntu.com quantal-updates/universe Sources [20.3 kB] 
Get:39 http://us.archive.ubuntu.com quantal-updates/multiverse Sources [2,940 B]
Get:40 http://us.archive.ubuntu.com quantal-updates/main amd64 Packages [117 kB]
Get:41 http://us.archive.ubuntu.com quantal-updates/restricted amd64 Packages [1,970 B]
Get:42 http://us.archive.ubuntu.com quantal-updates/universe amd64 Packages [63.0 kB]
Get:43 http://us.archive.ubuntu.com quantal-updates/multiverse amd64 Packages [7,956 B]
Get:44 http://us.archive.ubuntu.com quantal-updates/main i386 Packages [117 kB]
Get:45 http://us.archive.ubuntu.com quantal-updates/restricted i386 Packages [1,979 B]
Get:46 http://us.archive.ubuntu.com quantal-updates/universe i386 Packages [63.3 kB]
Get:47 http://us.archive.ubuntu.com quantal-updates/multiverse i386 Packages [8,121 B]
Hit http://us.archive.ubuntu.com quantal-updates/main Translation-en           
Hit http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com quantal-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com quantal-updates/universe Translation-en       
Get:48 http://us.archive.ubuntu.com quantal-backports/main Sources [14 B]      
Get:49 http://us.archive.ubuntu.com quantal-backports/restricted Sources [14 B]
Get:50 http://us.archive.ubuntu.com quantal-backports/universe Sources [2,241 B]
Get:51 http://us.archive.ubuntu.com quantal-backports/multiverse Sources [14 B]
Get:52 http://us.archive.ubuntu.com quantal-backports/main amd64 Packages [14 B]
Get:53 http://us.archive.ubuntu.com quantal-backports/restricted amd64 Packages [14 B]
Get:54 http://us.archive.ubuntu.com quantal-backports/universe amd64 Packages [1,066 B]
Get:55 http://us.archive.ubuntu.com quantal-backports/multiverse amd64 Packages [14 B]
Get:56 http://us.archive.ubuntu.com quantal-backports/main i386 Packages [14 B]
Get:57 http://us.archive.ubuntu.com quantal-backports/restricted i386 Packages [14 B]
Get:58 http://us.archive.ubuntu.com quantal-backports/universe i386 Packages [2,005 B]
Get:59 http://us.archive.ubuntu.com quantal-backports/multiverse i386 Packages [14 B]
Hit http://us.archive.ubuntu.com quantal-backports/main Translation-en         
Hit http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com quantal-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com quantal-backports/universe Translation-en     
Ign http://us.archive.ubuntu.com quantal/main Translation-en_US                
Ign http://us.archive.ubuntu.com quantal/multiverse Translation-en_US          
Ign http://us.archive.ubuntu.com quantal/restricted Translation-en_US          
Ign http://us.archive.ubuntu.com quantal/universe Translation-en_US            
Ign http://us.archive.ubuntu.com quantal-updates/main Translation-en_US        
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com quantal-updates/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com quantal-updates/universe Translation-en_US    
Ign http://us.archive.ubuntu.com quantal-backports/main Translation-en_US      
Ign http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/universe Translation-en_US  
Fetched 20.4 MB in 2min 11s (155 kB/s)                                         
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_quantal_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

```

Then after I did this, I got a message that Ubuntu 12.10 has had an internal error.

So yea, I hope I provided enough info. to get a headstart on this. Sorry if I'm too literal with the description...I'm still fairly new to all of this.

Thanks for any help!

---

### Post by dino99 on 2012-11-30
software center /update-manager are not as strong as synaptic; so do your choice. Such kind of issue is disturbing but harmless.

---

### Post by ibjsb4 on 2012-11-30
In terminal:

sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update

That should fix it.

---

### Post by romber on 2012-11-30
> **ibjsb4 said:**
> In terminal:

sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update

That should fix it.

Thanks! That worked. My problem before was I had dansguardian installed, so when I ran that command I would get similar errors as before. I uninstalled it and now it works!

Thanks again

---

### Post by utkjamie on 2012-12-01
> **ibjsb4 said:**
> In terminal:

sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update

That should fix it.

Thanks! Same problem occurred to me this morning on Ubuntu 12.10 x64. Your solution worked perfectly.

---

### Post by shishpt on 2013-02-01
Thank you, this worked for me as well. 

-Shishpt

---

