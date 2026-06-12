---
title: "&quot;apt-get update&quot; &quot;bad header line&quot; error every time, prevents installing via terminal"
date: 2015-01-14
forum: General Help
---

### Post by CaptainMikeRak on 2015-01-14
Pretty much what it says above in the title. I recently upgraded this PC, it appears it may have had an issue with the upgrade at some point and now I'm getting this strange issue where, whenever I use "sudo apt-get update", I get the error "bad header line" in various place throughout the text. This is preventing me from using certain programs when trying to install via the terminal. I'm thinking due to the bad upgrade I may just be better off with a clean install of Ubuntu 14.10 since I have all my data backed up on an eHDD and this was recently installed. Any thoughts on how to fix this (attempt repair or just clean install)?

---

### Post by QIII on 2015-01-14
Hello!

Could you try again and post the entire output of the terminal here between code tags?

---

### Post by CaptainMikeRak on 2015-01-14
Here's the code. This issue is preventing me from installing grub customizer (which I need to make my PC boot to the right OS). Here's the entire code including adding the repository, the "apt-get update" right through the failed install:
```
michaelprak@michaelprak-pc:~$ sudo add-apt-repository ppa:danielrichter2007/grub-customizer[sudo] password for michaelprak: 
 This PPA contains the latest release of Grub Customizer.


sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
 More info: https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keyring `/tmp/tmpta4n2__y/secring.gpg' created
gpg: keyring `/tmp/tmpta4n2__y/pubring.gpg' created
gpg: requesting key 3F055C03 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpta4n2__y/trustdb.gpg: trustdb created
gpg: key 3F055C03: public key "Launchpad PPA for Daniel Richter" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
michaelprak@michaelprak-pc:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Ign http://archive.canonical.com utopic InRelease                              
Ign http://extras.ubuntu.com utopic InRelease                                  
Hit http://repo.steampowered.com precise InRelease                             
Ign http://security.ubuntu.com utopic-security InRelease                       
Ign http://dl.google.com stable InRelease                                      
Ign http://linux.dropbox.com utopic InRelease                                  
Hit http://security.ubuntu.com utopic-security Release.gpg                     
Hit http://dl.google.com stable Release.gpg                                    
Hit http://archive.canonical.com utopic Release.gpg                            
Hit http://extras.ubuntu.com utopic Release.gpg                                
Ign http://ppa.launchpad.net utopic InRelease                                  
Ign http://us.archive.ubuntu.com utopic InRelease                              
Hit http://linux.dropbox.com utopic Release.gpg                                
Hit http://security.ubuntu.com utopic-security Release                         
Get:1 http://repo.steampowered.com precise/steam Sources [549 B]               
Hit http://dl.google.com stable Release.gpg                                    
Ign http://us.archive.ubuntu.com utopic-updates InRelease                      
Hit http://archive.canonical.com utopic Release                                
Hit http://extras.ubuntu.com utopic Release                                    
Ign http://ppa.launchpad.net utopic InRelease                                  
Hit http://linux.dropbox.com utopic Release                                    
Hit http://dl.google.com stable Release                                        
Ign http://us.archive.ubuntu.com utopic-backports InRelease                    
Get:2 http://repo.steampowered.com precise/steam amd64 Packages [604 B]        
Hit http://extras.ubuntu.com utopic/main Sources                               
Hit http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net utopic InRelease                                  
Hit http://us.archive.ubuntu.com utopic Release.gpg                            
Get:3 http://dl.google.com stable/main amd64 Packages [1,207 B]                
Hit http://extras.ubuntu.com utopic/main amd64 Packages                        
Get:4 http://repo.steampowered.com precise/steam i386 Packages [804 B]         
Hit http://us.archive.ubuntu.com utopic-updates Release.gpg                    
Hit http://ppa.launchpad.net utopic Release.gpg                                
Get:5 http://dl.google.com stable/main i386 Packages [1,216 B]                 
Hit http://extras.ubuntu.com utopic/main i386 Packages                         
Hit http://us.archive.ubuntu.com utopic-backports Release.gpg                  
Hit http://ppa.launchpad.net utopic Release.gpg                                
Hit http://us.archive.ubuntu.com utopic Release                                
Hit http://us.archive.ubuntu.com utopic-updates Release                        
Hit http://ppa.launchpad.net utopic Release.gpg                                
Hit http://archive.canonical.com utopic/partner Sources                        
Hit http://us.archive.ubuntu.com utopic-backports Release                      
Hit http://ppa.launchpad.net utopic Release                                    
Hit http://archive.canonical.com utopic/partner amd64 Packages                 
Hit http://archive.canonical.com utopic/partner i386 Packages                  
Hit http://ppa.launchpad.net utopic Release                                    
Err http://linux.dropbox.com utopic/main amd64 Packages                        
  Bad header line
Hit http://ppa.launchpad.net utopic Release                                    
Hit http://linux.dropbox.com utopic/main i386 Packages                         
Ign http://archive.canonical.com utopic/partner Translation-en                 
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://extras.ubuntu.com utopic/main Translation-en_US                     
Ign http://extras.ubuntu.com utopic/main Translation-en                        
Hit http://security.ubuntu.com utopic-security/main Sources                    
Ign http://linux.dropbox.com utopic/main Translation-en_US                     
Hit http://security.ubuntu.com utopic-security/restricted Sources              
Ign http://linux.dropbox.com utopic/main Translation-en                        
Hit http://security.ubuntu.com utopic-security/universe Sources                
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Hit http://security.ubuntu.com utopic-security/multiverse Sources              
Ign http://repo.steampowered.com precise/steam Translation-en                  
Hit http://security.ubuntu.com utopic-security/main amd64 Packages             
Hit http://security.ubuntu.com utopic-security/restricted amd64 Packages       
Hit http://security.ubuntu.com utopic-security/universe amd64 Packages         
Hit http://security.ubuntu.com utopic-security/multiverse amd64 Packages       
Hit http://security.ubuntu.com utopic-security/main i386 Packages              
Hit http://security.ubuntu.com utopic-security/restricted i386 Packages        
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://security.ubuntu.com utopic-security/universe i386 Packages          
Ign http://dl.google.com stable/main Translation-en                            
Hit http://security.ubuntu.com utopic-security/multiverse i386 Packages
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://security.ubuntu.com utopic-security/main Translation-en    
Hit http://ppa.launchpad.net utopic/main amd64 Packages                        
Ign http://dl.google.com stable/main Translation-en                            
Hit http://security.ubuntu.com utopic-security/multiverse Translation-en       
Hit http://ppa.launchpad.net utopic/main i386 Packages                         
Hit http://security.ubuntu.com utopic-security/restricted Translation-en       
Hit http://ppa.launchpad.net utopic/main Translation-en                        
Hit http://security.ubuntu.com utopic-security/universe Translation-en         
Hit http://ppa.launchpad.net utopic/main amd64 Packages                        
Hit http://ppa.launchpad.net utopic/main i386 Packages                         
Hit http://ppa.launchpad.net utopic/main Translation-en                        
Hit http://ppa.launchpad.net utopic/main amd64 Packages                        
Hit http://ppa.launchpad.net utopic/main i386 Packages                         
Hit http://ppa.launchpad.net utopic/main Translation-en                        
Hit http://us.archive.ubuntu.com utopic-backports/restricted Sources           
Hit http://us.archive.ubuntu.com utopic-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com utopic-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com utopic-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com utopic-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com utopic-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com utopic-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com utopic-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com utopic/main Sources                           
Hit http://us.archive.ubuntu.com utopic/restricted Sources                     
Hit http://us.archive.ubuntu.com utopic/universe Sources
Hit http://us.archive.ubuntu.com utopic/multiverse Sources
Hit http://us.archive.ubuntu.com utopic/main amd64 Packages
Hit http://us.archive.ubuntu.com utopic/restricted amd64 Packages
Hit http://us.archive.ubuntu.com utopic/universe amd64 Packages
Hit http://us.archive.ubuntu.com utopic/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com utopic/main i386 Packages
Hit http://us.archive.ubuntu.com utopic/restricted i386 Packages
Hit http://us.archive.ubuntu.com utopic/universe i386 Packages
Hit http://us.archive.ubuntu.com utopic/multiverse i386 Packages
Hit http://us.archive.ubuntu.com utopic/main Translation-en
Hit http://us.archive.ubuntu.com utopic/multiverse Translation-en
Hit http://us.archive.ubuntu.com utopic/restricted Translation-en
Hit http://us.archive.ubuntu.com utopic/universe Translation-en
Hit http://us.archive.ubuntu.com utopic-updates/main Sources
Hit http://us.archive.ubuntu.com utopic-updates/restricted Sources
Hit http://us.archive.ubuntu.com utopic-updates/universe Sources
Hit http://us.archive.ubuntu.com utopic-updates/multiverse Sources
Hit http://us.archive.ubuntu.com utopic-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com utopic-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com utopic-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com utopic-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com utopic-updates/main i386 Packages
Hit http://us.archive.ubuntu.com utopic-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com utopic-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com utopic-updates/multiverse i386 Packages       
Hit http://us.archive.ubuntu.com utopic-updates/main Translation-en            
Hit http://us.archive.ubuntu.com utopic-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com utopic-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com utopic-updates/universe Translation-en        
Hit http://us.archive.ubuntu.com utopic-backports/main Sources                 
Hit http://us.archive.ubuntu.com utopic-backports/universe Sources             
Hit http://us.archive.ubuntu.com utopic-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com utopic-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com utopic-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com utopic-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com utopic-backports/main Translation-en          
Hit http://us.archive.ubuntu.com utopic-backports/universe Translation-en      
Fetched 1,957 B in 27s (70 B/s)                                                
W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/utopic/main/binary-amd64/Packages  Bad header line


E: Some index files failed to download. They have been ignored, or old ones used instead.
michaelprak@michaelprak-pc:~$ sudo apt-get install grub-customizer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-customizer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 33 not upgraded.
W: Duplicate sources.list entry http://linux.dropbox.com/ubuntu/ utopic/main amd64 Packages (/var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_utopic_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://linux.dropbox.com/ubuntu/ utopic/main i386 Packages (/var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_utopic_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems



```

---

### Post by QIII on 2015-01-14
OK.  Looks like the maintainer of the dropbox PPA may have some maintenance to do.  There might not be a Utopic package.

For now, you can disable that PPA in your sources to avoid the messages about it.  You don't need to reinstall.

But if you look near the bottom, you'll see that grub-customizer is already the latest version, which would indicate it was installed.  You just didn't get anything from the dropbox PPA.

---

### Post by CaptainMikeRak on 2015-01-14
Oh, whoops. Sorry about the overlook on my part (had to dual-boot MS Windows [which actually gave me a headache] again for some programs). Thanks for the help! Just one last question, how do I disable the dropbox PPA? That's not something I've ever had to deal with yet.

---

### Post by Bashing-om on 2015-01-14
CaptainMikeRak; Hello;

From 'Software Sources' -> other sources . Uncheck them .

[INDENT]ain't nothing but a thing
[/INDENT]

---

### Post by CaptainMikeRak on 2015-01-14
Thanks mate! I completely forgot about that section, it's been awhile since I actually used Ubuntu as my primary OS (12.04 was the last one I used just to give you an idea), so now I'm refamiliarizing myself with the OS.  Thanks to both of you for the help!

---

### Post by Bashing-om on 2015-01-14
Captain; Great !

> **CaptainMikeRak said:**
> Thanks mate! I completely forgot about that section, it's been awhile since I actually used Ubuntu as my primary OS (12.04 was the last one I used just to give you an idea), so now I'm refamiliarizing myself with the OS.  Thanks to both of you for the help!

Pleased that I was able to be of some small help.
We try and make you the more comfortable with this

[INDENT][INDENT][INDENT]our operating system by choice
[/INDENT][/INDENT][/INDENT]

---

