---
title: "can't install anything"
date: 2007-07-17
forum: General Help
---

### Post by Talibas on 2007-07-17
I'm new to Ubuntu and I just installed Ubuntu 7.04 - the Feisty Fawn and I can't seem to install most programs, so far I've been able to install wine and tron, but when I try to install things like WoW or even rip a CD to hard drive my computer just turns off without warning

---

### Post by FunkyJack on 2007-07-17
If you can't install most packages then in terminal

```
sudo apt-get update
```

And you don't need to install WOW with wine if you have it on windows.
I tried to run my windows version and it works great.

Just in terminal

```
wine /media/*path to your wow folder*/WoW.exe
```

---

### Post by Talibas on 2007-07-17
I ran that first code and got this:

Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Translation-en_CA               
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Translation-en_CA 
Get:2 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg [191B]      
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-en_CA            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Translation-en_CA   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Translation-en_CA
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_CA        
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Translation-en_CA       
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release                      
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release                             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_CA    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_CA      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_CA
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release [50.9kB]    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Packages                     
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Sources 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages [51.4kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages [6360B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources [9259B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources [953B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages [19.7kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources [2522B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages [5412B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources [836B]
Fetched 148kB in 4s (36.5kB/s)
Reading package lists... Done

and then nothing really happened after that

and as far as copying wow from windows goes, I tried copying it to a DVD but when I put it in my disc drive I get "invalid mount option"
so I have no idea what to do

---

### Post by FunkyJack on 2007-07-17
Now you should be able to install all packages.

You don't need to copy your WOW to DVD.
If you have WOW installed on windows you can run that instalation on ubuntu :)
Did you mounted windows partitions?
Can you access them from ubuntu?

---

### Post by Talibas on 2007-07-18
No Ubuntu is the only OS on that computer, I'm fairly certain that this is some sort of hardware issue thats triggered by putting my system under a load, at first I thought maybe power supply, but I've swapped a new one in but the same thing happens, I'm starting to think it might be a motherboard problem :(

---

### Post by strabes on 2007-07-18
You need to run ```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by Talibas on 2007-07-24
yeah, this problem turned out to be an issue with my cpu heatsink, turns out that someone that shouldn't have touched my motherboard, did :S problems fixed now tho

---

