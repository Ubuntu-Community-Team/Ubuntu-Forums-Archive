---
title: "False alert?"
date: 2016-03-13
forum: General Help
---

### Post by einpekkar on 2016-03-13
Hi guys!

Running 14.04 and mostly happy with that. Lately I've been getting this alert, but when i run Software Updater it says everything is honky dory. I'd like to think Software Updater is right and the alert is a bug of some sorts. Any suggestions? 

[IMG]https://dl.dropboxusercontent.com/u/87830328/Screenshot%20from%202016-03-13%2020%3A41%3A58.png[/IMG]


[IMG]https://dl.dropboxusercontent.com/u/87830328/Screenshot%20from%202016-03-13%2020%3A26%3A35.png[/IMG]

---

### Post by oldos2er on 2016-03-13
Please post the output of ```
sudo apt-get update
``` run in a terminal.

---

### Post by einpekkar on 2016-03-13
```
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty InRelease
Get:1 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates InRelease [65,9 kB]          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                             
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Get:2 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports InRelease [65,9 kB]        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty Release                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages               
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:4 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/main Sources [262 kB]        
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Get:5 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/restricted Sources [5 352 B] 
Get:6 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/universe Sources [151 kB]    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Get:7 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/multiverse Sources [5 946 B] 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Get:8 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/main amd64 Packages [713 kB] 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en               
Get:9 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [15,9 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Get:10 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/universe amd64 Packages [339 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Get:11 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [13,2 kB]
Get:12 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/main i386 Packages [692 kB] 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages             
Get:13 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/restricted i386 Packages [15,6 kB]
Get:14 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/universe i386 Packages [340 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages       
Get:15 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13,6 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages         
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages       
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/universe Translation-en        
Get:16 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/main Sources [8 661 B]    
Get:17 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/restricted Sources [28 B] 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Get:18 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/universe Sources [34,0 kB]
Get:19 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/multiverse Sources [1 898 B]
Get:20 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/main amd64 Packages [9 787 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Get:21 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/restricted amd64 Packages [28 B]
Get:22 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/universe amd64 Packages [40,9 kB]
Get:23 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages [1 571 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Get:24 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/main i386 Packages [9 814 B]
Get:25 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/restricted i386 Packages [28 B]
Get:26 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/universe i386 Packages [41,0 kB]
Get:27 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [1 552 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/universe Translation-en      
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/multiverse amd64 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en     
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/main i386 Packages                 
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/restricted i386 Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/universe i386 Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/multiverse i386 Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/main Translation-en
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/multiverse Translation-en
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/restricted Translation-en
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/universe Translation-en
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/universe Translation-en_US
Fetched 2 849 kB in 7s (375 kB/s)                                              
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by howefield on 2016-03-13
If you don't use Chrome browser any more you can remove the repository information for it, if you do still use Chrome have a read at [this thread]("http://ubuntuforums.org/showthread.php?t=2315941")..

---

### Post by MibunoOokami on 2016-03-14
Are your settings set to automatic download/install? My wife used to get the same message on her machine after we set it for manual checking for updates.

---

### Post by Bucky Ball on 2016-03-14
Have added code tags to your output. Please see the link in my signature below for how to use them in future. :)

---

### Post by einpekkar on 2016-03-14
Still using Chrome. Did what was suggested in the thread you linked to. And, lo and behold! It seems to work.

Thanks! :D

---

### Post by howefield on 2016-03-14
> **einpekkar said:**
> Still using Chrome. Did what was suggested in the thread you linked to. And, lo and behold! It seems to work.

Thanks! :D

You're welcome, thanks for the update and glad you sorted it.

---

### Post by einpekkar on 2016-03-14
:? Guess what? After a few minutes the annoying warning triangle was back. A repeat of the procedure, including a restart, made no difference.

---

### Post by einpekkar on 2016-03-19
The mystery deepens. After the alert reappeared all by itself. Or whatever. I decided to just ignore it. And now, after a few ordinary automatic updates. It's gone again. Maybe it didn't like being ignored? :D

---

