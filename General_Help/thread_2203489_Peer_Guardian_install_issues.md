---
title: "Peer Guardian install issues"
date: 2014-02-03
forum: General Help
---

### Post by hebrewofyhwh on 2014-02-03
I am a new user of Ubunto and I amy trying to  install peer guardian and I used this site: [http://linuxg.net/how-to-install-peerguardian-on-ubuntu-linux-mint-and-elementary-os/#comment-169937](http://linuxg.net/how-to-install-peerguardian-on-ubuntu-linux-mint-and-elementary-os/#comment-169937)  to install but I had a problem at the very last command.    Any help will be appreiciated.       Here is the terminal command  page cut and paste :
```
 mycomputer:~$ sudo add-apt-repository ppa:jre-phoenix/ppa 
[sudo] password formycomputer:  
You are about to add the following PPA to your system:  This PPA provides offical packages of PeerGuardian Linux (pgl) for all supported Ubuntu series. This archive enhances [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net), where I offer Debian packages for the current Debian series.  PeerGuardian Linux (pgl) is a privacy oriented firewall application. It blocks connections to and from hosts specified in huge blocklists (thousands or millions of IP ranges). Its origin seeds in targeting aggressive IPs while you use P2P. PeerGuardian Linux is actively developed. However the team is very small and with few spare time. Contributors are welcome! Check out [http://peerguardian.sourceforge.net](http://peerguardian.sourceforge.net).  For Ubuntu hardy you will find the precessors of pgl here: nfblock/moblock, blockcontrol and mobloquer. They aren't developed any more.  More info: [https://launchpad.net/~jre-phoenix/+archive/ppa](https://launchpad.net/~jre-phoenix/+archive/ppa) 
Press [ENTER] to continue or ctrl-c to cancel adding it  gpg: keyring `/tmp/tmpzANIin/secring.gpg' created gpg: keyring `/tmp/tmpzANIin/pubring.gpg' created gpg: requesting key 9C0042C8 from hkp server keyserver.ubuntu.com gpg: /tmp/tmpzANIin/trustdb.gpg: trustdb created gpg: key 9C0042C8: public key "Launchpad PPA for jre-phoenix" imported gpg: Total number processed: 1 gpg:               imported: 1  (RSA: 1) OK
mycomputer:~$ sudo apt-get update 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg 
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                     
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]            
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                      
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                          
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                       
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [927 B]                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex            
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [3,106 B]             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex              
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [451 kB]        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en 
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [8,028 B] 
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [103 kB] 
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,486 B] 
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [768 kB] 
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [12.2 kB] 
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [239 kB] 
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.7 kB] 
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B] 
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B] 
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B] 
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex  
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
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en      
Fetched 1,683 kB in 12s (133 kB/s)                                              
Reading package lists... Done 
mycomputer:~$ sudo apt-get install pgl 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
E: Unable to locate package pgl
```

---

### Post by jre on 2014-02-03
1.)
Please don't hijack other threads. You have a new question, so start a new thread.

2.)
Please see my signature: use CODE tags. I see you already unsuccessfully tried that in your edit at 10:41 PM: "Reason: It is not formatted right". Unfortunately you failed there.

3.)
See the official documentation: [https://sourceforge.net/p/peerguardian/wiki/pgl-Install-DebianUbuntu/](https://sourceforge.net/p/peerguardian/wiki/pgl-Install-DebianUbuntu/)

4.)
```
sudo apt-get install pgld pglcmd pglgui
```
instead of
```
sudo apt-get install pgl
```

Greets
jre

---

### Post by Iowan on 2014-02-03
Moved to new thread.  I've added code tags, and *tried* to add some formatting.

---

### Post by jre on 2014-02-03
Thanks, seeing the code now confirms I as right. Use advice 4

---

### Post by hebrewofyhwh on 2014-02-04
Thank you for your responses.  I am really not that familiar with these things and codes and such. I am used to using the Windows computer and these options I have never learned.   I am certain that people "Hijack" things deliberatly, but I did not do any such thing delibertatly;  it requires fore thought to commit sin because sin is a decision that men make.     I will certainly make an effort to learn what I need to communicate with you folks so that I can get fully comfortable with this new type of Operating system.      I have just tried the command that you gave Jre for the Terminal command screen  i.e.  ```
sudo apt-get install pgld pglcmd pglgui
```  and it worked , and I thank you.   thank you again for your responses here. I really appreiciate the help.

---

### Post by jre on 2014-02-04
You're welcome :)

What I told you in 1) and 2) are just normal forum rules. They are not special for this forum. Just try to adhere to them in the future.

btw, thx Iowan

---

### Post by hebrewofyhwh on 2014-02-04
I got a question now on the Peer Guardian issue.  The GUI has disappeared. I right click on the blue dot and I don't see where to get the GUI open again so I can whitelist some sites. Thank you again .,

---

### Post by hebrewofyhwh on 2014-02-04
Removed to start new thread...

---

### Post by jre on 2014-05-22
> **hebrewofyhwh said:**
> I got a question now on the Peer Guardian issue.  The GUI has disappeared. I right click on the blue dot and I don't see where to get the GUI open again so I can whitelist some sites. Thank you again .,

Sorry I've been quite busy. Do you still have the problem?

Generally this should be quite easy:
Left click on the blue dot (pglgui icon in the tray, I assume you also have that on Ubuntu with Unity), and the window should pop up again/come to focus.
Or do the same as to start a new pglgui instance (click its icon, I'm not sure how this is called in Ubuntu) . That should change focus to the pgl window.

---

