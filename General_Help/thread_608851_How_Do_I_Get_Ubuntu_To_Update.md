---
title: "How Do I Get Ubuntu To Update?"
date: 2007-11-10
forum: General Help
---

### Post by Joesplace on 2007-11-10
I downloaded Ubuntu three weeks ago and loaded on my laptop and desktop. My laptop shows the needed updates via Update Manager and works great. I get updates every fiew days.

My desktop always says everything is up-to-date. It has never updated anything. It connects to the internet fine - so I know something must not be working here. How do I get update manager to work? It downloads 43 packages, checks for updates and says everything is up-to-date.

On the Software sources, the Update tab is set to notify for updates . . .

Thanks
Joe

---

### Post by taurus on 2007-11-10
What happens when you run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Joesplace on 2007-11-10
Heres' the readout:

joe@joes-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US        
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US 
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release               
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Fetched 4B in 1s (3B/s)  
Reading package lists... Done

joe@joes-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joe@joes-desktop:~$

---

### Post by taurus on 2007-11-10
Looks like your system is up-to-day.

---

### Post by Joesplace on 2007-11-10
Well, I guess I'm going to believe it even though it's never downloaded any updates . . . thanks for the help!

---

### Post by 1337455 10534 on 2007-11-10
Heres a nice little script that I wrote and use.
Download it, and go to its properties. Under permission; allow executing text file.
Run it in the terminal..
You like it?

---

### Post by shad0w_walker on 2007-11-10
Depending on different packages you have installed it might just be that something updated on the laptops software that wasn't installed on the desktop.

Also, it may just be that the updates were security updates and you have the auto download enabled on security updates.

---

### Post by 1337455 10534 on 2007-11-10
Ya, I tick everything available in teh Software Sources..
Anybody try the script yet? I'm planning to implement something similar in another project of mine.

---

### Post by Joesplace on 2007-11-10
just tried your script - runs really good, didn't bomb either:) Nice little program . . .

---

### Post by taurus on 2007-11-10
> **1337455 10534 said:**
> Heres a nice little script that I wrote and use.
Download it, and go to its properties. Under permission; allow executing text file.
Run it in the terminal..
You like it?

Any reason you have "sudo **aptitude** update" and then use apt-get after that. "sudo **apt-get** upgrade"?

---

### Post by 1337455 10534 on 2007-11-10
None at all. I felt goofy. Should I change this? Is there really a difference?
Oh, and thx for noticing! :)

---

