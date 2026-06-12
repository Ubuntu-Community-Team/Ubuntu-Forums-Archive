---
title: "I want a list of my software/apps for backup purposes"
date: 2015-10-30
forum: General Help
---

### Post by michael-piziak on 2015-10-30
When I back up, I back up everything except the software (like Gimp) that is on my system because I know I can retrieve it again - unlike photos, etc...

Is there a place, or a command in terminal, where I can get a list of all my software/apps - to help me get them again on future OS reinstalls ?

Ubuntu 12.04 lts

---

### Post by Bashing-om on 2015-10-30
michael-piziak; Hi !

Maybe something like 
```

dpkg --get-selections > ~/my-packages

```
From New install
```

sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

```
Your attention is invited to:
[http://ubuntuforums.org/showthread.php?t=1139264](http://ubuntuforums.org/showthread.php?t=1139264)
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by michael-piziak on 2015-10-30
> **Bashing-om said:**
> michael-piziak; Hi !

Maybe something like 
```

dpkg --get-selections > ~/my-packages

```
From New install
```

sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

```
Your attention is invited to:
[http://ubuntuforums.org/showthread.php?t=1139264](http://ubuntuforums.org/showthread.php?t=1139264)
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)[INDENT][INDENT]my bit to try and help
[/INDENT]
[/INDENT]


ok your 2nd set of terminal commands I *think* worked for me - but I don't really see the familiar things I've installed like Gimp, RedShift, KaZam Screencaster, OpenShot video editor, and others - unless I don't understand what I'm looking at with the results.

I typed in the first 2, then 
I typed in the 3rd command.  Another question: what is it asking me to do with the yes or no question?

I post it all here - sorry it is so long:

```
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ sudo dpkg --set-selections < my-packages
[sudo] password for michael: 
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ sudo apt-get -y update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [196 kB]            
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [54.3 kB]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [493 kB]       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [135 kB]        
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [8,723 B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [122 kB]   
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [9,730 B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [943 kB]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [4,464 B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [43.8 kB]  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [2,200 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [553 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [16.1 kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [269 kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [16.5 kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [994 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [16.1 kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [278 kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [16.7 kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [10.6 kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [7,613 B]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [11.6 kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [7,297 B]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [124 kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [8,333 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [407 kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en [9,603 B]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en [3,857 B]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en [160 kB]
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,682 B]
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [610 kB] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en  
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [11.6 kB]
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [132 kB]
Get:36 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,878 B]
Get:37 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [208 B]
Get:38 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [199 B]
Get:39 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [202 B]
Get:40 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [205 B]
Get:41 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [240 kB]
Get:42 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en [1,408 B]
Get:43 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en [2,979 B]
Get:44 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [78.1 kB]
Fetched 6,005 kB in 9s (633 kB/s)                                              
Reading package lists... Done
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ sudo apt-get dselect-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  unzip
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 194 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]?
```

---

### Post by deadflowr on 2015-10-30
I'm not sure what you did.
Seems like you ran all the commands on the same system.

So, if that was the case, you wouldn't see any updates for the packages, as those should be up-to-date already.

Case in point, the only updated package you do have listed, is a very recent package update for unzip.
That got a security update yesterday.(See: [http://www.ubuntu.com/usn/usn-2788-1/](http://www.ubuntu.com/usn/usn-2788-1/) )


edit: oh, and click Y and install the update for unzip.
That's all the y/n is asking of you.

---

### Post by michael-piziak on 2015-10-30
> **deadflowr said:**
> I'm not sure what you did.
Seems like you ran all the commands on the same system.

So, if that was the case, you wouldn't see any updates for the packages, as those should be up-to-date already.

Case in point, the only updated package you do have listed, is a very recent package update for unzip.
That got a security update yesterday.(See: [http://www.ubuntu.com/usn/usn-2788-1/](http://www.ubuntu.com/usn/usn-2788-1/) )


edit: oh, and click Y and install the update for unzip.
That's all the y/n is asking of you.

This is getting more complicated than I want it to be.

I basically would like a list of programs/apps that I added to a freshly reinstalled Ubuntu lts system - like a list of things I put on it from the Software Center.

Michael

---

### Post by Bucky Ball on 2015-10-31
```
apt-mark showmanual
```

From [here]("http://askubuntu.com/questions/159664/how-to-list-user-installed-applications-not-packages"). This might be sort of what you are after.

It really is best to [do some searching]("https://duckduckgo.com/?q=list+manually+installed+apps+ubuntu") and post here if you get stuck. Good luck. :)

---

### Post by michael-piziak on 2015-10-31
> **Bucky Ball said:**
> ```
apt-mark showmanual
```

From [here]("http://askubuntu.com/questions/159664/how-to-list-user-installed-applications-not-packages"). This might be sort of what you are after.

It really is best to [do some searching]("https://duckduckgo.com/?q=list+manually+installed+apps+ubuntu") and post here if you get stuck. Good luck. :)

That's exactly what I wanted.

Thanks!

Thread solved.

---

