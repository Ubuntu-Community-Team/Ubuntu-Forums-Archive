---
title: "Update error in Ubuntu 14.04"
date: 2016-11-12
forum: General Help
---

### Post by mongoose970 on 2016-11-12
I'm getting an error marked with a no-entry sign on the top right of my Ubuntu 14.04 (I've been meaning to upgrade it for a while now but hadn't got round to it) desktop. It states 'Error: BrokenCount > 0. This usually means that your installed packages have unmet dependencies.' Now whenever I try to update my computer, I get another error and it refuses to update.

Could somebody help explain to me what this means? And how do I upgrade to the latest version of Ubuntu? Sorry, I'm not the best with technology.

Thanks for helping!

---

### Post by ventrical on 2016-11-12
> **mongoose970 said:**
> I'm getting an error marked with a no-entry sign on the top right of my Ubuntu 14.04 (I've been meaning to upgrade it for a while now but hadn't got round to it) desktop. It states 'Error: BrokenCount > 0. This usually means that your installed packages have unmet dependencies.' Now whenever I try to update my computer, I get another error and it refuses to update.

Could somebody help explain to me what this means? And how do I upgrade to the latest version of Ubuntu? Sorry, I'm not the best with technology.

Thanks for helping!

Try:

In the terminal:
 
```

sudo dpkg --configure -a

```

Sometimes if there is a package interruption it will not fully install some packages or depends.

You can then try to update your current 14.04 which is good until 2019 I believe. 

Regards..

---

### Post by mongoose970 on 2016-11-13
Thanks for your help,

I tried it, and it came up with an error and wouldn't proceed. It claims that the version of linux-image-generic and linux-headers-generic on my system do not match what is required for the process - which as I see it is the technical way of saying they need to be updated. So I'm assuming I need to update them manually? How do I do that?

---

### Post by howefield on 2016-11-13
You need to post the exact errors.. eg the output of 

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

Post the full terminal input and output to assist someone else who knows how to advise you.

---

### Post by mongoose970 on 2016-11-13
Output of apt-get update:

```
   	 	 	 	   Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [65.9 kB] 
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                   
 Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty InRelease                               
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                   
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                   
 Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates InRelease [65.9 kB]           
 Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                        
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                     
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release.gpg                             
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release                                 
 Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                               
 Get:4 [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg [933 B]                   
 Get:5 [http://archive.canonical.com](http://archive.canonical.com) trusty Release [9,359 B]                     
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                         
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                          
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                         
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                         
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                          
 Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [4,613 B]   
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                         
 Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [120 kB]          
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                                
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                         
 Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [45.1 kB]     
 Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted Sources [5,888 B]  
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                          
 Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [3,207 B]  
 Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main Sources [384 kB]        
 Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [13.3 kB] 
 Get:13 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources [10.0 kB]            
 Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [547 kB]  
 Get:15 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages [5,611 B]     
 Get:16 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages [6,295 B]      
 Get:17 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en [4,593 B]     
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_GB                      
 Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe Sources [169 kB]    
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                         
 Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 InRelease                              
 Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [142 kB] 
 Get:20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse Sources [7,522 B] 
 Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [4,138 B] 
 Get:22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [16.4 kB] 
 Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [13.1 kB] 
 Get:24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main amd64 Packages [918 kB] 
 Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [507 kB]   
 Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 Release.gpg                            
 Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [142 kB] 
 Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [4,289 B] 
 Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [301 kB]  
 Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en [2,201 B] 
 Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en [3,349 B] 
 Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [84.5 kB] 
 Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 Release                                
 Get:32 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe amd64 Packages [388 kB] 
 Get:33 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [14.0 kB] 
 Get:34 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted i386 Packages [16.2 kB] 
 Get:35 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main i386 Packages [877 kB]  
 Get:36 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe i386 Packages [389 kB] 
 Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main amd64 Packages                    
 Get:37 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [14.5 kB] 
 Get:38 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main Translation-en [445 kB] 
 Get:39 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse Translation-en [7,340 B] 
 Get:40 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted Translation-en [3,842 B] 
 Get:41 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe Translation-en [205 kB] 
 Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main i386 Packages                     
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Sources                      
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Sources                            
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Sources                        
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Sources                      
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted amd64 Packages     
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main amd64 Packages           
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe amd64 Packages                 
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse amd64 Packages               
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted i386 Packages                
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main i386 Packages                      
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe i386 Packages                  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse i386 Packages                
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Translation-en_GB                  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Translation-en                     
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Translation-en_GB  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Translation-en     
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Translation-en_GB            
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Translation-en               
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Translation-en_GB   
 Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main Translation-en_GB                 
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Translation-en                 
 Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main Translation-en                    
 Fetched 5,965 kB in 5s (1,066 kB/s)                                  
 Reading package lists... Done 
  
```

Output of apt-get upgrade:

```
   	 	 	 	   Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 You might want to run &#8216;apt-get -f install&#8217; to correct these. 
 The following packages have unmet dependencies. 
  linux-generic : Depends: linux-image-generic (= 3.13.0.87.93) but 3.13.0.86.92 is installed 
                  Depends: linux-headers-generic (= 3.13.0.87.93) but 3.13.0.86.92 is installed 
 E: Unmet dependencies. Try using -f. 
  
```

---

### Post by Bashing-om on 2016-11-13
mongoose970; Hello;

And as another poke at this, if ya follow the package manager's advise:
```

sudo apt -f install

```

What results ?

By the way, you should be up on the latest kernel:
> 
sysop@1404mini:~$ uname -r
3.13.0-101-generic
sysop@1404mini:~$


[INDENT][INDENT]what does it take to keep
[INDENT][INDENT][INDENT]your package manager satisfied
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

