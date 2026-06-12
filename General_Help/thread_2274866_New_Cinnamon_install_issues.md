---
title: "New Cinnamon install issues"
date: 2015-04-22
forum: General Help
---

### Post by Thrackerzod on 2015-04-22
Hello! I'm not That new to Linux, I ran Slackware a bit for some time a couple years back and at some point in the late 2000s ran Ubuntu Karmic Koala for several months, and decided to give Ubuntu another whirl.

I installed 14.04, and rather than use Unity (which I am not a fan of) I wanted to check out Cinnamon, so I got that installed with apt-get...but I'm not sure if I did something incorrectly or the Cinnamon install is a little borked. Completely unsure of how to fix this. I did attempt reinstalling Cinnamon with "sudo apt-get remove cinnamon && sudo apt-get install cinnamon", but that didn't solve anything. Image of what I'm talking about. I don't think its supposed to look like that. :P [http://i.imgur.com/rY7DRkv.png](http://i.imgur.com/rY7DRkv.png)

---

### Post by flaymond on 2015-04-22
Do you installed from ppa? I once installed cinnamon on ubuntu-14.04 using ppa (dev one is the latest).

```

sudo add-apt-repository ppa:lestcape/cinnamon
sudo apt-get update
sudo apt-get install cinnamon

```

* This is lester ppa, but there's more maintaining Cinnamon DE.

For Cinnamon (3rd party DE from Mint), I just wanna say it's better to install from the ppa.

---

### Post by Thrackerzod on 2015-04-22
I did sudo apt-get update after adding that repo and it spat out this o.O ```
W: Failed to fetch http://ppa.launchpad.net/lestcape/cinnamon/ubuntu/dists/utopic/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/lestcape/cinnamon/ubuntu/dists/utopic/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.



```

I'm assuming that means it didn't work.

Update: Come to find out the Cinnamon devs got rid of the stable repo and only left the nightly repo up. Only way to get the stable releases of Cinnamon is with Linux Mint. Ain't that some crap?

---

### Post by flaymond on 2015-04-23
Mine does this - ```


inter@mate:~$ sudo apt-add-repository ppa:lestcape/cinnamon

To avoid problems please:
- Use mdm as a display manager:
  sudo apt-get install mdm
  sudo dpkg-reconfigure mdm 
- Remove overlay-scrollbars:
  gsettings set org.gnome.desktop.interface ubuntu-overlay-scrollbars false
 More info: https://launchpad.net/~lestcape/+archive/ubuntu/cinnamon
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpzr1nuzjt/secring.gpg' created
gpg: keyring `/tmp/tmpzr1nuzjt/pubring.gpg' created
gpg: requesting key FA2AF90A from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpzr1nuzjt/trustdb.gpg: trustdb created
gpg: key FA2AF90A: public key "Launchpad PPA for Lester Carballo Pérez" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK

apt get update :
[CODE]
inter@mate:~$ sudo apt-get update
[sudo] password for inter: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Reading package lists... Done  

```



The repository is right, the update is run smoothly. So, ya, I think maybe something happened with your installation.

* It's just a guess though, do you really installing it from ubuntu repos before adding this ppa? Anyway, there's a couple more unofficial ppa, maintaining Cinnamon DE for Ubuntu. Well, hope you find the right one and got a good installation of Cinnamon. Good luck! :D

---

### Post by deadflowr on 2015-04-23
The output from the error shows you are on 14.10, not 14.04.
The output shows utopic which is 14.10. 14.04 would show trusty.

Unfortunately, there is no version from that ppa for 14.10.
run the add-apt command again and add -r to remove it.
```
sudo add-apt-repository -r ppa:lestcape/cinnamon
```
the -r means remove.

Beyond that, is a version of cinnamon available in the normal repos (Universe repository) in 14.10?
I thought it was removed in 14.04 but returned in 14.10.
I maybe wrong...

---

### Post by flaymond on 2015-04-23
[QUOTE=deadflowr]The output from the error shows you are on 14.10, not 14.04.
The output shows utopic which is 14.10. 14.04 would show trusty.
[/QUOTE]

That's right, that's why I'm giving him 14.04 lestcape ppa for Cinnamon.

[QUOTE=Thrackerzod]I installed 14.04,[/QUOTE]

I believe zod did some typos there. Sorry, I just know 14.04 ppa, since it's LTS.

Thanks.

---

