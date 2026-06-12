---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2013-11-03
forum: General Help
---

### Post by viktor-hubinette on 2013-11-03
Hi when i try to download stuff and also do sudo apt-get upgrade this shows up E: Sub-process /usr/bin/dpkg returned an error code (1) please can someone help me to fix this? tell me what commands i gonna use so you can see my problem

---

### Post by Bashing-om on 2013-11-03
viktor-hubinette; Hi ! Welcome to the forum !

We need to see the entire error and in context.
Post pack the outputs of terminal codes:
```

sudo apt-get update
sudo apt-get upgrade

```
so, a tale is told.

[INDENT][INDENT]where there are solutions there are no poroblems
[/INDENT][/INDENT]

---

### Post by viktor-hubinette on 2013-11-03
this happen @**Bashing-om**

update : [http://shortText.com/Ye42G](http://shortText.com/Ye42G)

Upgrade : [http://shortText.com/k5BWg](http://shortText.com/k5BWg)

btw i did just installed ubuntu 13.04 and i cant acces to wireless internet (im now using my mobile internet to the computer) and i cant download things or update in update manager and so on :/

---

### Post by Bashing-om on 2013-11-03
viktor-hubinette; Hey;

Your links do not load for me. Post the info back to this thread:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

The wireless issue may or may  not be related. Will know more after your system is stable and updated.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by viktor-hubinette on 2013-11-03
[COLOR=Black]viktor@Viktor-Dator:~$ sudo apt-get update
[sudo] password for viktor: 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg                     
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg                            
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release                                
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Sources                    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring Release.gpg                            
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner Sources                        
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                                    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates Release.gpg                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Sources              
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner amd64 Packages                 
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports Release.gpg                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Sources                
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages                  
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Sources              
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates Release                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                         
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main amd64 Packages             
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted amd64 Packages       
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/restricted Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe amd64 Packages         
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/universe Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse amd64 Packages       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_US                     
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/multiverse Sources                     
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/main amd64 Packages                    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/restricted amd64 Packages              
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/universe amd64 Packages      
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/multiverse amd64 Packages    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/main i386 Packages           
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/restricted i386 Packages     
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/universe i386 Packages       
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/multiverse i386 Packages     
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/main Translation-en          
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/multiverse Translation-en    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/restricted Translation-en    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/universe Translation-en      
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/main Sources         
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/restricted Sources   
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/universe Sources     
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_US    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/multiverse Sources   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/main amd64 Packages            
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en                 
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/restricted amd64 Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/universe amd64 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/main i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/universe i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/main Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/restricted Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/universe Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/main Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/universe Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/multiverse Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/main amd64 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/restricted amd64 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/universe amd64 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/multiverse amd64 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/main i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/restricted i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/universe i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_US
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_US
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_US
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/restricted Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/universe Translation-en
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/multiverse Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/restricted Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/universe Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/multiverse Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/restricted Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/universe Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/multiverse Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/restricted Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/universe Translation-en_US
Reading package lists... Done
viktor@Viktor-Dator:~$ 
 Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/main i386 Packages           
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/restricted i386 Packages     
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/universe i386 Packages       
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/multiverse i386 Packages     
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/main Translation-en          
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/multiverse Translation-en    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/restricted Translation-en    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/universe Translation-en      
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/main Sources         
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/restricted Sources   
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/universe Sources     
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_US    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/multiverse Sources   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/main amd64 Packages            
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en                 
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/restricted amd64 Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/universe amd64 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/main i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/universe i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/main Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/restricted Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/universe Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/main Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/universe Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/multiverse Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/main amd64 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/restricted amd64 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/universe amd64 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/multiverse amd64 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/main i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/restricted i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/universe i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_US
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_US
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_US
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/restricted Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/universe Translation-en
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/multiverse Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/restricted Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring/universe Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/multiverse Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/restricted Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-updates/universe Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/multiverse Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/restricted Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) raring-backports/universe Translation-en_US
Reading package lists... Done
viktor@Viktor-Dator:~$ 
[/COLOR]
			
		 		 	 			[CENTER] 				 				 			[/CENTER]

---

### Post by viktor-hubinette on 2013-11-03
[COLOR=Black]viktor@Viktor-Dator:~$ sudo apt-upgrade
[sudo] password for viktor: 
sudo: apt-upgrade: command not found
viktor@Viktor-Dator:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xserver-common-lts-raring
The following packages have been kept back:
  libboost-dev libboost-filesystem-dev libboost-regex-dev libboost-system-dev
  libboost-thread-dev
0 upgraded, 0 newly installed, 1 to remove and 5 not upgraded.
1 not fully installed or removed.
After this operation, 1,646 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 264726 files and directories currently installed.)
Removing xserver-common-lts-raring ...
Removing 'diversion of /usr/lib/xorg/protocol.txt to /usr/lib/xorg/protocol-precise.txt by xserver-common-lts-raring'
dpkg-divert: error: rename involves overwriting `/usr/lib/xorg/protocol.txt' with
  different file `/usr/lib/xorg/protocol-precise.txt', not allowed
dpkg: error processing xserver-common-lts-raring (--remove):
 subprocess installed post-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 xserver-common-lts-raring
E: Sub-process /usr/bin/dpkg returned an error code (1)
viktor@Viktor-Dator:~$ 

@Bashing-om
[/COLOR]

---

### Post by viktor-hubinette on 2013-11-03
@bashing-om i have pasted my output of the commands there you told me

---

### Post by Bashing-om on 2013-11-03
viktor-hubinette; Hey,

What I require of you at this time is to copy and paste the outputs of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```
following the instructions in this tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

I will do all that is within my power to help.

---

### Post by viktor-hubinette on 2013-11-03
but i allready posted to outputs of that on the link you send me it are in the comments on last page

---

### Post by viktor-hubinette on 2013-11-03
the output of sudo apt-get upgrade [COLOR=Black]root@Viktor-Dator:/home/viktor# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xserver-common-lts-raring
The following packages have been kept back:
  libboost-dev libboost-filesystem-dev libboost-regex-dev libboost-system-dev
  libboost-thread-dev
0 upgraded, 0 newly installed, 1 to remove and 5 not upgraded.
1 not fully installed or removed.
After this operation, 1,646 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 264683 files and directories currently installed.)
Removing xserver-common-lts-raring ...
Removing 'diversion of /usr/lib/xorg/protocol.txt to /usr/lib/xorg/protocol-precise.txt by xserver-common-lts-raring'
dpkg-divert: error: rename involves overwriting `/usr/lib/xorg/protocol.txt' with
  different file `/usr/lib/xorg/protocol-precise.txt', not allowed
dpkg: error processing xserver-common-lts-raring (--remove):
 subprocess installed post-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 xserver-common-lts-raring
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Viktor-Dator:/home/viktor# 
[/COLOR]

---

### Post by bapoumba on 2013-11-03
> **Bashing-om said:**
> viktor-hubinette; Hey;

Your links do not load for me. Post the info back to this thread:


The update goes fine, all raring repos. Upgrade :
```
viktor@Viktor-Dator:~$ sudo apt-upgrade
[sudo] password for viktor: 
sudo: apt-upgrade: command not found
viktor@Viktor-Dator:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree 
Reading state information... Done
The following packages will be REMOVED:
xserver-common-lts-raring
The following packages have been kept back:
libboost-dev libboost-filesystem-dev libboost-regex-dev libboost-system-dev
libboost-thread-dev
0 upgraded, 0 newly installed, 1 to remove and 5 not upgraded.
1 not fully installed or removed.
After this operation, 1,646 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 264726 files and directories currently installed.)
Removing xserver-common-lts-raring ...
Removing 'diversion of /usr/lib/xorg/protocol.txt to /usr/lib/xorg/protocol-precise.txt by xserver-common-lts-raring'
dpkg-divert: error: rename involves overwriting `/usr/lib/xorg/protocol.txt' with
different file `/usr/lib/xorg/protocol-precise.txt', not allowed
dpkg: error processing xserver-common-lts-raring (--remove):
subprocess installed post-removal script returned error exit status 2
No apport report written because MaxReports is reached already
Errors were encountered while processing:
xserver-common-lts-raring
E: Sub-process /usr/bin/dpkg returned an error code (1)
viktor@Viktor-Dator:~$ 
```
Not sure why a precise conf file is in the way. I have a /usr/lib/xorg/protocol.txt

[http://ubuntuforums.org/showthread.php?t=2172620](http://ubuntuforums.org/showthread.php?t=2172620)
[http://ubuntuforums.org/showthread.php?t=2177053](http://ubuntuforums.org/showthread.php?t=2177053)
I would not change the file permission though..

---

### Post by bapoumba on 2013-11-03
2 posts moved from another thread in here, thanks overdrank :)

---

### Post by Bashing-om on 2013-11-03
@bapoumba;
Me too, It is scratching my curiosity bump. What process can and will generate that "/usr/lib/xorg/protocol-precise.txt" ?
I can not follow ""/var/usr/dpkg/info/xserver-common-lts-raring.postrm" ' In the link you found as that file does not exist in my stable install ([http://ubuntuforums.org/showthread.php?t=2172620](http://ubuntuforums.org/showthread.php?t=2172620)). A typo from that original poster as to the proper path ?

@viktor-hubinette; I am in the process of further research.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-11-03
@viktor-hubinette;

I maybe making a bit of progress, post back to this thread - between code tags (#) - the output of terminal command:
```

ls -la /var/lib/dpkg/info/xserver-common-lts-raring.postrm

```

And will see what can be done.

[INDENT][INDENT]inquiring minds 
[/INDENT][/INDENT]

---

