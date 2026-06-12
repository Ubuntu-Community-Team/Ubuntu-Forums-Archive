---
title: "repositories and understanding them"
date: 2015-01-18
forum: General Help
---

### Post by matt18 on 2015-01-18
Ello all. I have a question.

I am running 12.04 and i am curious to know if this version uses the same repositories as the 14.xx LTS version? 

As in, will ubuntu software manger and update manager update older versions of software to new current ones found in newer LTS versions? For example, can i update my libre office from version 3 to version 4.x in ubuntu 12.04 with out adding any new repos or ppas? or is the only way to get newest software without using command line or adding additional repos, to update to the newest LTS?

Reason i ask. I am a network engineer and i love cli, but i have had some friends and neighbors want to use ubuntu for home use but are extremely intimidated by the CLI. They just want to have update manager or software center to update the libreoffice or gimp to the newest current version regardless of what LTS distro they are on. haha So i am testing it out as a standard user who never ever wants to use the command line. I did a poll once and asked about a hundred computer users (mac and windows) if they have ever opened up the command line interface.. 97% said nope. haha. So i am trying to spread the word of ubuntu but i know how people operate haha. They want the newest version of applications with out using the cli. haha.

Does the update manger keep all software up to date to the newest version that the current LTS uses regardless of the LTS version they are running?



thanks.

---

### Post by deadflowr on 2015-01-18
No
The repos for 12.04 are for 12.04, and the repos for 14.04 are for 14.04 and never the twain shall meet.

edit: To add, some packages are in continuous updating, such as firefox, which will have a new version in both.
But most packages are frozen to a specific version at the time the version is released.

LTS releases are unique in that the also have the ability to upgrade the kernel and graphic stack to versions used in newer releases.
Which why you might notice packages in 12.04 marked with lts-trusty  for linux-images and xserver-xorg packages.

But overall newer versions of programs and packages will not be upgraded to the newer versions found in other repos.
 If you see any packages get newer versions it is more likely because of security updates over feature updates.
(Or you cannot get those security updates without also installing the newer feature updates.)

if that makes any sense to you...

---

### Post by matt18 on 2015-01-18
thank you

ok, so how would i update libreoffice from version 3 to 4.3 in ubuntu 12.04 cuz i just tried using the apt-get-repository command and adding the repo for it and it still loads the old version?

so basically, in order to get the new software, they would have to do a distro upgrade then?

---

### Post by matt18 on 2015-01-18
sudo add-apt-repository ppa:libreoffice/libreoffice-4-3

sudo apt-get update and then a upgrade

---

### Post by matt18 on 2015-01-18
yeah it makes sense and thats what i thought was going on. So i will let them know that. Now on to my questions for me. haha

I want to get libreoffice 4.3 on my 12.04 because i hear the new features are better than version 3 haha. But when i try following the method above or outlined by ask ubuntu, it will always load version 3 and then every time i open update manager, it says i need to do a partial upgrade. so it doesnt like th eppas for some reason. Is 4.3 stable in 12.04?

Oh an d i performed a ppa purge to revert back to my old version of libre. and i removed the ppa and now update manager says it cant update becuase it doesnt trust the repos. so ill fix that later i just want libre office 4.3 to work nicly on my 12.04

thanks Or would it be easier to just hit the dang upgrade to 14.xx? haha. i have always had bad luck upgrading distros in vmplyer thats why i hesitate haha

---

### Post by deadflowr on 2015-01-18
```
sudo add-apt-repository ppa:libreoffice/libreoffice-4-3
```
click enter to accept the new keys
then update your package list
```
sudo apt-get update
```
then update your system
```
sudo apt-get upgrade
```
when you run the last command look at the output and you will see "the following packages will be upgraded and a list of the libreoffice packages among any other packages that would also already be up-datable.
then click y to proceed.

So there is no need to upgrade to a newer release...

I have no idea what apt-get repository does, as that is not a real command.

The ppa I put up is for the 4.3 version, because it is stable, where if you used the ppa for libreoffice/ppa it is full of packages for the release candidate which is not as stable. 
Again, if that makes any sense...

**Edit**:Seems you figured somethings out while my rather slow fingers jumbled words I typed left and right...

---

### Post by matt18 on 2015-01-18
yeah, see. i did exactly that but it still opens up libreoffice 3 from the applications menu. haha. i will try one more time and see what happens. thanks

tried it again 

with
sudo add-apt-repository ppa:libreoffice/libreoffice-4-3
sudo apt-get update
sudo apt-get install libreoffice

installs fine with no errors but still opens version 3. This is driving me crazy haha

---

### Post by deadflowr on 2015-01-18
Post the output for the apt-get update command.

---

### Post by matt18 on 2015-01-18
```
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Get:1 [http://debian.scribus.net](http://debian.scribus.net) precise Release.gpg [190 B]                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://debian.scribus.net](http://debian.scribus.net) precise Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://debian.scribus.net](http://debian.scribus.net) precise Release                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
Ign [http://debian.scribus.net](http://debian.scribus.net) precise/main Sources/DiffIndex                   
Ign [http://debian.scribus.net](http://debian.scribus.net) precise/main i386 Packages/DiffIndex             
Ign [http://debian.scribus.net](http://debian.scribus.net) precise/main TranslationIndex                    
Ign [http://debian.scribus.net](http://debian.scribus.net) precise/non-free TranslationIndex                
Hit [http://debian.scribus.net](http://debian.scribus.net) precise/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Hit [http://debian.scribus.net](http://debian.scribus.net) precise/main i386 Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Err [http://debian.scribus.net](http://debian.scribus.net) precise/non-free Sources                   
  404  Not Found
Err [http://debian.scribus.net](http://debian.scribus.net) precise/non-free i386 Packages
  404  Not Found
Ign [http://debian.scribus.net](http://debian.scribus.net) precise/main Translation-en_US
Ign [http://debian.scribus.net](http://debian.scribus.net) precise/main Translation-en
Ign [http://debian.scribus.net](http://debian.scribus.net) precise/non-free Translation-en_US
Ign [http://debian.scribus.net](http://debian.scribus.net) precise/non-free Translation-en
Fetched 190 B in 8s (22 B/s)                                                   
W: GPG error: [http://debian.scribus.net](http://debian.scribus.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5BC4CFB8EEF818CF
W: Failed to fetch [http://debian.scribus.net/debian/dists/precise/non-free/source/Sources](http://debian.scribus.net/debian/dists/precise/non-free/source/Sources)  404  Not Found

W: Failed to fetch [http://debian.scribus.net/debian/dists/precise/non-free/binary-i386/Packages](http://debian.scribus.net/debian/dists/precise/non-free/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
lt72884@ubuntu:~$
```

im not seeing the newly added ppa haha

---

### Post by matt18 on 2015-01-18
I just looked at update manager and it shows two of the ppas unchecked from launchpad that have libreoffice 4.3 in the path. However, those are the ones i unchecked because it was causing update manager to want to do a partial upgrade.

---

### Post by matt18 on 2015-01-18
I just redid everything and made sure those two were checked and now it opens the correct one. Now i just need to fix the update manager. This thread can be set to solved now thanks

I will open new thread for new issue.

---

### Post by matt18 on 2015-01-18
All right. i redid everything and made sure in update manager that they were checked. it now opens 4.3 so now its time to see if it works haha.  solved  i will open new thread for fixing update manager issues

---

### Post by deadflowr on 2015-01-18
The update manager seems to have a problem with the debian-scribus repository.
fer what it's worth.

You can mark this thread as solved by going up to the top thread area where it says thread tools and selecting mark this the as solved.

---

