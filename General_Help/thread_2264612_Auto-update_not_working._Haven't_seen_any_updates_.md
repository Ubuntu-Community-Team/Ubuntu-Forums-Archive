---
title: "Auto-update not working. Haven't seen any updates since 12/13/14."
date: 2015-02-08
forum: General Help
---

### Post by ericajade on 2015-02-08
Hi Friends in the Ubuntu community,

I haven't seen an auto-update message since the last update I made on 12/13/14 and can't seem to find an option anywhere to download any new updates. Since then though I see a ton of scripts everytime I select Ubuntu on my dual-boot system installed on my Sony VAIO laptop, and Windows start-up has been finicky as well; restarts the computer before even getting to the Windows log-in screen. However, once I get either Ubuntu or Windows up and running all else seems fine.

I'm not super familiar with how to make changes in Ubuntu so appreciate any help you can offer in laymen's terms. 

Thanks so much,
Erica

---

### Post by sandyd on 2015-02-08
Hi, can you run the following commands in the terminal and post the output?

```

cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d
sudo apt-get update
```
Thanks!

---

### Post by ericajade on 2015-02-09
cat/etc/apt/sources.list
bash: cat/etc/apt/sources.list: No such file or directory
erica@erica-laptop:~$ cat etc/apt/sources.list
cat: etc/apt/sources.list: No such file or directory
erica@erica-laptop:~$ ls - /etc/apt/sources.list/d
ls: cannot access -: No such file or directory
ls: cannot access /etc/apt/sources.list/d: Not a directory
erica@erica-laptop:~$ sudo apt-get update
[sudo] password for erica: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]           
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [62.0 kB]             
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed InRelease                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed Release.gpg [933 B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [191 kB]   
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [62.0 kB]            
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                      
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed Release [209 kB]            
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [15.1 kB]                        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [8,846 B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [3,624 B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [85.4 kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [101 kB] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [1,970 B]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [46.9 kB]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [2,123 B]           
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en    
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [177 kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en            
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [2,061 B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [102 kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [4,463 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [427 kB] 
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [8,846 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [250 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [11.3 kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en [207 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en [128 kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/main i386 Packages [157 kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/restricted i386 Packages [681 B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/multiverse i386 Packages [28 B]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/universe i386 Packages [23.3 kB]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/main Translation-en [65.5 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/restricted Translation-en
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/universe Translation-en [15.5 kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US        
Fetched 2,373 kB in 7s (326 kB/s)                                              
Reading package lists... Done

---

### Post by ericajade on 2015-02-09
I think it may have worked because my Auto-updater re-appeared. I'm downloading 250 updates now. I'll let you know if something goes awry. Thanks so much!!

---

### Post by plucky on 2015-02-10
> **ericajade said:**
> I think it may have worked because my Auto-updater re-appeared. I'm downloading 250 updates now. I'll let you know if something goes awry. Thanks so much!!

Have you disabled checking for updates in Software Sources?

Seems suspicious that just running ```
sudo apt-get update
``` has found updates to install and the Update Manager has not notified you before.

Good Luck

---

### Post by ericajade on 2015-02-10
If I'm looking at the right thing then Sofrware Sources auto-update is disabled. 

I do however continue to see a ton of code in the background on start up; before the log-in screen pops up. Then I still get this "System Program Problem detected" and when I select "Report Problem" the details say "Action: com.ubuntu.apport.apport-gtk-root, Vendor: Apport"

---

### Post by plucky on 2015-02-10
> If I'm looking at the right thing then Software Sources auto-update is disabled. 

Does it look like attached except precise in place of Lucid?

---

### Post by ericajade on 2015-02-10
Yes, except the "pre-released updates" box was checked. I un-checked it. See attached.
[ATTACH=CONFIG]259893[/ATTACH]

---

### Post by oldos2er on 2015-02-10
> **ericajade said:**
> cat/etc/apt/sources.list
bash: cat/etc/apt/sources.list: No such file or directory
erica@erica-laptop:~$ cat etc/apt/sources.list
cat: etc/apt/sources.list: No such file or directory
erica@erica-laptop:~$ ls - /etc/apt/sources.list/d
ls: cannot access -: No such file or directory
ls: cannot access /etc/apt/sources.list/d: Not a directory


It helps to copy and paste commands from the code box. There should be a space between "cat" and "/etc/apt/sources.list", and "/etc/apt/sources.list/d" should be "/etc/apt/sources.list.d/"

---

