---
title: "major failure of your software management system"
date: 2006-11-23
forum: General Help
---

### Post by ChristopherL on 2006-11-23
When I go to applications menu add/remove I get the following error message:

Failed to check for installed and available applications


This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

Everything was fine before I tried to install Automatix2.

---

### Post by h2gofast on 2006-11-23
I've run Automatix2 on 4 different machines without a hitch.  Anecdotal evidence I know, but I suspect Automatix2 isn't the problem.  
In a console window try
sudo aptitude update      (or sudo apt-get update   if you don't have aptitude installed)

then if their are no errors 
 
sudo aptitude upgrade

post any errors back here and someone should be able to help you.
also post your /etc/apt/sources.list file as well.
automatix2 does rewrite your /etc/apt/sources.list file so it's possible it borked something.  
happy thanksgiving 
h2.

---

### Post by Adrenal on 2006-11-23
> **ChristopherL said:**
> When I go to applications menu add/remove I get the following error message:

Failed to check for installed and available applications


This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

Everything was fine before I tried to install Automatix2.
Hehe, whoa, dude. Ok, here's what you do.
Firstly, it seems like your sources.list is borked. This is the file that ubuntu reads to see if your software is the latest version etc. Firstly, I'll get you to open up your terminal and type in
```
sudo rm /etc/apt/sources.list
```
That'll delete it. It will ask you for a password, type in the one you use to log in.

Then, type in
```
sudo gedit /etc/apt/sources.list
```(this assumes your own gnome. If KDE, replace "gedit" with "kedit")

In the new file, paste the following
```
deb http://au.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

##Added by Adross
deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
#AUTOMATIX REPOS END

#Added for Beryl
deb http://www.beerorkid.com/compiz edgy main-edgy
deb http://media.blutkind.org/xgl/ edgy main-edgy
deb http://compiz-mirror.lupine.me.uk/ edgy main-edgy
deb http://ubuntu.compiz.net/ edgy main-edgy
deb http://amaranth.selfip.com edgy lrm
deb http://ubuntu2.beryl-project.org edgy main

```

This should give you a working sources.list. Next type in 
```
sudo apt-get update
```
This will reload everything, similar to when you refresh a webpage
then, just for kicks
```
sudo apt-get update
```

And that should do it

---

### Post by ChristopherL on 2006-11-23
I did what you wrote Adrenal, it´s working 
now.

But when I updated i saw this in the last lines in the terminal:W: GPG error: [http://ubuntu.compiz.net](http://ubuntu.compiz.net) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: GPG error: [http://compiz-mirror.lupine.me.uk](http://compiz-mirror.lupine.me.uk) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: GPG error: [http://ubuntu2.beryl-project.org](http://ubuntu2.beryl-project.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A947CF51609B551
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C
W: GPG error: [http://media.blutkind.org](http://media.blutkind.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: GPG error: [http://www.beerorkid.com](http://www.beerorkid.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: You may want to run apt-get update to correct these problems
christopherl@christopherl:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
christopherl@christopherl:~$ 

Should I worry about this?

---

### Post by ChristopherL on 2006-11-23
Adrenal is this source.list for Australia?
How can I make it for Sweden?

---

### Post by Adrenal on 2006-11-23
Ok, first things first.
The Beryl thing seems to be a problem. So find the text
> #Added for Beryl
and delete that and everything below that line.

Secondly, what's wrong with Australia? I like Australia. But fine, if you want your fancy swedish data open your sources list with
> sudo gedit /etc/apt/sources.list
Click "replace" with gedit and replace "au." with "se."

Any problems, let me know

---

### Post by ChristopherL on 2006-11-24
Ok, less error linese but still little left
check this out:

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Get:3 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US      
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [189B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US        
Get:5 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                      
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US        
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US        
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release [27.3kB]                
Get:8 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release [4886B]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US       
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US                
Get:10 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release [4147B]                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release [23.3kB]               
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release [19.6kB]                 
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                   
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release [27.3kB]                
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release [34.7kB]                         
Get:16 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages [1889B]    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages [634B]           
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages [14B]      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US     
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release.gpg [191B]      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages [20.7kB]     
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages [1432B]      
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages [14B]      
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages [14B]              
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages [14B]        
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages [14B]          
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages [14B]        
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages [20.7kB]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages [3514B]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages [6757B]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages [2223B]     
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                   
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages [940kB]                    
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release [34.7kB]                      
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages [3514B]    
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources [4218B]           
Get:36 [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages [571B]                   
Get:37 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources [925B]      
Get:38 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages [6757B]      
Get:39 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources [433B]        
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release [19.6kB]              
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages [5974B]
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages [3559kB]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release [23.3kB]            
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages [940kB]                 
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages [126kB]              
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages [5974B]           
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources [274kB]                  
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources [1436B]            
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages [3559kB]            
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources [1068kB]             
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages [14B]           
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages [14B]     
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources [14B]            
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources [14B]      
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages [634B]        
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages [14B]   
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages [1432B]   
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages [14B]   
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources [409B]         
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources [14B]    
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources [980B]     
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources [14B]    
Fetched 10.8MB in 47s (227kB/s)                                                
Reading package lists... Done
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C
W: You may want to run apt-get update to correct these problems
christopherl@christopherl:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Get:2 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US      
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US      
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [189B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US        
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                     
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Get:6 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                      
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US       
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                      
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                     
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US         
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages          
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                       
  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US     
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [189B]   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages         
Get:11 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release [4147B]              
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                         
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources
Fetched 4345B in 2s (1991B/s)
Reading package lists... Done
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C
W: You may want to run apt-get update to correct these problems

---

### Post by Adrenal on 2006-11-24
Ok, most of those lines are meant to be there, that's just ubuntu keeping you posted and which sources it's updated. There is one error and to get rid of that delete 
##Added by Adross
and everything below it. That will give you a stock sources.list file with backports, multiverse and universe enabled.

---

### Post by ChristopherL on 2006-11-25
Thanks Adrenal

---

### Post by Adrenal on 2006-11-25
No worries mate

---

