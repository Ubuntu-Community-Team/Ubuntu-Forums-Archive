---
title: "help installing nautilus bug fix"
date: 2007-02-12
forum: General Help
---

### Post by warri0r on 2007-02-12
does anyone know how to install a bug fix for nautilus.it started using high cpu :(

today this nautilus started using 100% cpu. i searched the forum and got two links tat are shown below.

[https://launchpad.net/ubuntu/+source/nautilus/+bug/54684](https://launchpad.net/ubuntu/+source/nautilus/+bug/54684)

[http://people.ubuntu.com/~seb128/debug/54684/](http://people.ubuntu.com/~seb128/debug/54684/)

so some one tell me how to install this fix,which of those listed and am i on the right way(is this the right fix)


plz someone help me :(

screenshot:

[IMG]http://img377.imageshack.us/img377/9034/untitledmx7.jpg[/IMG]

---

### Post by bapoumba on 2007-02-12
Hello,
_quickly_ reading through the bug, looks like it made it to edgy-updates.
Do you have this repo in your sources.list ?

---

### Post by warri0r on 2007-02-12
sorry dude i m really a dumb newbie to linux as well as ubuntu. i didnt get wat u mean by source.list

i know abt repositories where we can download software packages for ubuntu and some basic shell commands tat i learnt from school. tats all i know :(

plz help me to fix that bug :(

**~Edit**
if you are talking abt those automatic updates tat pop up near the clock, then sorry plz give me an alternate way coz when i use tat to update anything then it ll ask me to restart and when i make a reboot THATS IT, i ll get either a black or blue screen and i need to reinstall again :( plz kindly throw some light .

---

### Post by bapoumba on 2007-02-12
Please open a terminal (> Accessories > Terminal), run:
```
cat /etc/apt/sources.list
```
and paste the complete output in here.

---

### Post by warri0r on 2007-02-12
here the output tat i got 


> deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END


---

### Post by bapoumba on 2007-02-12
Your repositories list looks okay to me. What is the output to **sudo aptitude update** ?

---

### Post by warri0r on 2007-02-12
**got this output:**


> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                       
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                     
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US             
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                    
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy Release.gpg [191B]                      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/main Translation-en_US                    
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Get:5 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]           
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US       
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US         
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/restricted Translation-en_US              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/universe Translation-en_US                
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy-updates Release.gpg [191B]              
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy-updates/main Translation-en_US            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy-updates/restricted Translation-en_US  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release [50.9kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy Release                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US        
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy-updates Release [38.4kB]               
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                  
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                 
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release [38.4kB]                
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release [38.4kB]                  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages [62.1kB]          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/main Packages                             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/restricted Packages                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/main Sources                              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/restricted Sources                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/universe Packages                         
Get:15 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy-updates/main Packages [64.0kB]         
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release [50.9kB]                 
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages [5689B]     
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources [12.3kB]           
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources [923B]       
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages [31.9kB]      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                      
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages [7779B]           
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages [14B]       
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages [16.0kB]      
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages [4824B]     
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages [10.7kB]        
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages [14B]         
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages [62.1kB]        
Get:28 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy-updates/restricted Packages [14B]      
Get:29 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy-updates/main Sources [19.7kB]          
Get:30 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy-updates/restricted Sources [14B]       
Get:31 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy-updates/universe Packages [10.7kB]     
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages [5689B]      
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages [31.9kB]       
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages [3785B]      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                          
Fetched 568kB in 28s (20.0kB/s)                                                 
Reading package lists... Done

---

### Post by bapoumba on 2007-02-12
If they are any updates showing up in your panel, please run ```
sudo aptitude update
```. If not, your system is up to date, and your bug may not be related to the one you've linked.
Do you have another user on your computer ? You can add a new one, named temp for example (**sudo adduser temp**) and see if this new user has the same problem.

If the new user is okay, the problem may be with your user configuration files. We'll see which one afterwards.

---

### Post by warri0r on 2007-02-12
s theres an update icon popping near the clock. but plz guide me to download using commandline or automatix or anyother thing

whenever i update anything with tat update notifier, i cant boot my computer again. it ll go into a blue screen or a black screen showing a message "[some code] : bug : cpu, soft, lockup  (sorry i remember the key words only). even i tried deselecting those kernel update while updating :(


now i never update with tat notifier and i m running ubuntu successfully for the past 2 days after some 16 installations.

plz kindly help me :(

---

