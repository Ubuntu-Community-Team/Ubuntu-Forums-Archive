---
title: "Apt-get update runs without errors but doesn't really update package list"
date: 2015-01-03
forum: General Help
---

### Post by 0-contact-7 on 2015-01-03
Hi everyone.
Since i installed 14.10 64 bits, three weeks ago, I never got any package to update. When I do apt-get update, I won't get any error, but  updating of the package list is very fast and downloaded sizes seems  very small, so i think it's not updating anything.

  When doing apt-get upgrade, it never find anything.
  Here is the output of apt-get update, in French but I guess you will figure it out.

```
vincent@vincent-LIFEBOOK-E554:~$ sudo apt-get update
[sudo] password for vincent: 
Ign http://fr.archive.ubuntu.com utopic InRelease
Ign http://dl.google.com stable InRelease                                      
Ign http://security.ubuntu.com utopic-security InRelease                       
Ign http://extras.ubuntu.com utopic InRelease                                  
Ign http://ppa.launchpad.net utopic InRelease                                  
Ign http://fr.archive.ubuntu.com utopic-updates InRelease                      
Atteint http://security.ubuntu.com utopic-security Release.gpg                 
Atteint http://dl.google.com stable Release.gpg                                
Ign http://ppa.launchpad.net utopic InRelease                                  
Atteint http://extras.ubuntu.com utopic Release.gpg                            
Ign http://fr.archive.ubuntu.com utopic-backports InRelease                    
Atteint http://security.ubuntu.com utopic-security Release                     
Atteint http://dl.google.com stable Release                                    
Ign http://ppa.launchpad.net utopic InRelease                                  
Atteint http://extras.ubuntu.com utopic Release                                
Atteint http://fr.archive.ubuntu.com utopic Release.gpg                        
Atteint http://security.ubuntu.com utopic-security/main Sources                
Ign http://ppa.launchpad.net utopic InRelease                                  
Atteint http://extras.ubuntu.com utopic/main Sources                           
Atteint http://fr.archive.ubuntu.com utopic-updates Release.gpg                
Atteint http://dl.google.com stable/main amd64 Packages                        
Atteint http://ppa.launchpad.net utopic Release.gpg                            
Atteint http://security.ubuntu.com utopic-security/restricted Sources          
Atteint http://extras.ubuntu.com utopic/main amd64 Packages                    
Réception de : 1 http://fr.archive.ubuntu.com utopic-backports Release.gpg [933 B]
Atteint http://dl.google.com stable/main i386 Packages                         
Ign http://downloads-distro.mongodb.org dist InRelease                         
Atteint http://ppa.launchpad.net utopic Release.gpg                            
Atteint http://security.ubuntu.com utopic-security/universe Sources            
Atteint http://extras.ubuntu.com utopic/main i386 Packages                     
Atteint http://fr.archive.ubuntu.com utopic Release                            
Atteint http://ppa.launchpad.net utopic Release.gpg                            
Atteint http://security.ubuntu.com utopic-security/multiverse Sources          
Atteint http://fr.archive.ubuntu.com utopic-updates Release                    
Atteint http://ppa.launchpad.net utopic Release.gpg                            
Atteint http://security.ubuntu.com utopic-security/main amd64 Packages         
Réception de : 2 http://fr.archive.ubuntu.com utopic-backports Release [62,0 kB]
Atteint http://repository.spotify.com stable InRelease                         
Atteint http://ppa.launchpad.net utopic Release                                
Atteint http://security.ubuntu.com utopic-security/restricted amd64 Packages   
Atteint http://repository.spotify.com stable/non-free amd64 Packages           
Atteint http://ppa.launchpad.net utopic Release                                
Atteint http://security.ubuntu.com utopic-security/universe amd64 Packages     
Atteint http://repository.spotify.com stable/non-free i386 Packages            
Atteint http://ppa.launchpad.net utopic Release                                
Atteint http://security.ubuntu.com utopic-security/multiverse amd64 Packages   
Atteint http://ppa.launchpad.net utopic Release                                
Atteint http://security.ubuntu.com utopic-security/main i386 Packages          
Atteint http://downloads-distro.mongodb.org dist Release.gpg                   
Atteint http://fr.archive.ubuntu.com utopic/main Sources                       
Atteint http://ppa.launchpad.net utopic/main amd64 Packages                    
Atteint http://security.ubuntu.com utopic-security/restricted i386 Packages    
Atteint http://fr.archive.ubuntu.com utopic/restricted Sources                 
Atteint http://ppa.launchpad.net utopic/main i386 Packages                     
Atteint http://security.ubuntu.com utopic-security/universe i386 Packages      
Atteint http://fr.archive.ubuntu.com utopic/universe Sources                   
Atteint http://ppa.launchpad.net utopic/main Translation-en                    
Atteint http://security.ubuntu.com utopic-security/multiverse i386 Packages    
Atteint http://fr.archive.ubuntu.com utopic/multiverse Sources                 
Atteint http://ppa.launchpad.net utopic/main amd64 Packages                    
Atteint http://security.ubuntu.com utopic-security/main Translation-en         
Atteint http://fr.archive.ubuntu.com utopic/main amd64 Packages                
Atteint http://ppa.launchpad.net utopic/main i386 Packages                     
Atteint http://security.ubuntu.com utopic-security/multiverse Translation-en   
Atteint http://fr.archive.ubuntu.com utopic/restricted amd64 Packages          
Atteint http://ppa.launchpad.net utopic/main Translation-en                    
Atteint http://fr.archive.ubuntu.com utopic/universe amd64 Packages            
Atteint http://security.ubuntu.com utopic-security/restricted Translation-en   
Ign http://extras.ubuntu.com utopic/main Translation-fr_FR                     
Atteint http://downloads-distro.mongodb.org dist Release                       
Atteint http://fr.archive.ubuntu.com utopic/multiverse amd64 Packages          
Ign http://extras.ubuntu.com utopic/main Translation-fr                        
Atteint http://ppa.launchpad.net utopic/main amd64 Packages                    
Atteint http://fr.archive.ubuntu.com utopic/main i386 Packages                 
Ign http://extras.ubuntu.com utopic/main Translation-en                        
Atteint http://ppa.launchpad.net utopic/main i386 Packages                     
Ign http://dl.google.com stable/main Translation-fr_FR                         
Atteint http://fr.archive.ubuntu.com utopic/restricted i386 Packages           
Atteint http://ppa.launchpad.net utopic/main Translation-en                    
Atteint http://security.ubuntu.com utopic-security/universe Translation-en     
Ign http://dl.google.com stable/main Translation-fr                            
Atteint http://ppa.launchpad.net utopic/main amd64 Packages                    
Ign http://dl.google.com stable/main Translation-en                            
Ign http://repository.spotify.com stable/non-free Translation-fr_FR            
Atteint http://ppa.launchpad.net utopic/main i386 Packages                     
Atteint http://fr.archive.ubuntu.com utopic/universe i386 Packages             
Ign http://repository.spotify.com stable/non-free Translation-fr               
Atteint http://downloads-distro.mongodb.org dist/10gen amd64 Packages          
Atteint http://fr.archive.ubuntu.com utopic/multiverse i386 Packages           
Ign http://repository.spotify.com stable/non-free Translation-en               
Atteint http://fr.archive.ubuntu.com utopic/main Translation-fr                
Atteint http://fr.archive.ubuntu.com utopic/main Translation-en                
Atteint http://fr.archive.ubuntu.com utopic/multiverse Translation-fr          
Atteint http://fr.archive.ubuntu.com utopic/multiverse Translation-en          
Atteint http://fr.archive.ubuntu.com utopic/restricted Translation-fr          
Atteint http://fr.archive.ubuntu.com utopic/restricted Translation-en          
Atteint http://downloads-distro.mongodb.org dist/10gen i386 Packages           
Atteint http://fr.archive.ubuntu.com utopic/universe Translation-fr            
Atteint http://fr.archive.ubuntu.com utopic/universe Translation-en            
Atteint http://fr.archive.ubuntu.com utopic-updates/main Sources               
Atteint http://fr.archive.ubuntu.com utopic-updates/restricted Sources         
Atteint http://fr.archive.ubuntu.com utopic-updates/universe Sources           
Ign http://ppa.launchpad.net utopic/main Translation-fr_FR                     
Atteint http://fr.archive.ubuntu.com utopic-updates/multiverse Sources         
Ign http://ppa.launchpad.net utopic/main Translation-fr                        
Atteint http://fr.archive.ubuntu.com utopic-updates/main amd64 Packages        
Ign http://ppa.launchpad.net utopic/main Translation-en                        
Atteint http://fr.archive.ubuntu.com utopic-updates/restricted amd64 Packages  
Atteint http://fr.archive.ubuntu.com utopic-updates/universe amd64 Packages    
Atteint http://fr.archive.ubuntu.com utopic-updates/multiverse amd64 Packages  
Atteint http://fr.archive.ubuntu.com utopic-updates/main i386 Packages         
Atteint http://fr.archive.ubuntu.com utopic-updates/restricted i386 Packages   
Atteint http://fr.archive.ubuntu.com utopic-updates/universe i386 Packages     
Atteint http://fr.archive.ubuntu.com utopic-updates/multiverse i386 Packages   
Atteint http://fr.archive.ubuntu.com utopic-updates/main Translation-en        
Atteint http://fr.archive.ubuntu.com utopic-updates/multiverse Translation-en  
Atteint http://fr.archive.ubuntu.com utopic-updates/restricted Translation-en  
Atteint http://fr.archive.ubuntu.com utopic-updates/universe Translation-en    
Réception de : 3 http://fr.archive.ubuntu.com utopic-backports/main Sources [751 B]
Réception de : 4 http://fr.archive.ubuntu.com utopic-backports/restricted Sources [14 B]
Réception de : 5 http://fr.archive.ubuntu.com utopic-backports/universe Sources [6 557 B]
Réception de : 6 http://fr.archive.ubuntu.com utopic-backports/multiverse Sources [14 B]
Réception de : 7 http://fr.archive.ubuntu.com utopic-backports/main amd64 Packages [556 B]
Réception de : 8 http://fr.archive.ubuntu.com utopic-backports/restricted amd64 Packages [14 B]
Réception de : 9 http://fr.archive.ubuntu.com utopic-backports/universe amd64 Packages [5 549 B]
Réception de : 10 http://fr.archive.ubuntu.com utopic-backports/multiverse amd64 Packages [14 B]
Réception de : 11 http://fr.archive.ubuntu.com utopic-backports/main i386 Packages [560 B]
Réception de : 12 http://fr.archive.ubuntu.com utopic-backports/restricted i386 Packages [14 B]
Réception de : 13 http://fr.archive.ubuntu.com utopic-backports/universe i386 Packages [5 546 B]
Réception de : 14 http://fr.archive.ubuntu.com utopic-backports/multiverse i386 Packages [14 B]
Atteint http://fr.archive.ubuntu.com utopic-backports/main Translation-en      
Atteint http://fr.archive.ubuntu.com utopic-backports/multiverse Translation-en
Atteint http://fr.archive.ubuntu.com utopic-backports/restricted Translation-en
Atteint http://fr.archive.ubuntu.com utopic-backports/universe Translation-en  
Ign http://downloads-distro.mongodb.org dist/10gen Translation-fr_FR           
Ign http://downloads-distro.mongodb.org dist/10gen Translation-fr
Ign http://downloads-distro.mongodb.org dist/10gen Translation-en
82,5 ko réceptionnés en 5s (14,1 ko/s)
Lecture des listes de paquets... Fait
vincent@vincent-LIFEBOOK-E554:~$ 
```

Any idea ?

---

### Post by plucky on 2015-01-03
Can you try a different repository? Perhaps the Main Repository.

You can select one in "Software Sources".

Good Luck

---

### Post by Bucky Ball on 2015-01-03
```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... but I don't see any obvious issue with your output although you do seem to have a few PPA repos that you have probably manually installed being ignored. Are they old or the server is down?

Maybe there just hasn't been a big update lately for 14.10. Have you got Software Updater set to inform you and update regularly? That will tell you exactly what it wants to update. Try running that in a week or so.

---

### Post by 0-contact-7 on 2015-01-03
Thank you for you suggestion Plucky, but i still get same result.

```
vincent@vincent-LIFEBOOK-E554:~/dev/Cadendar$ sudo apt-get update[sudo] password for vincent: 
Atteint http://repo.steampowered.com precise InRelease
Ign http://dl.google.com stable InRelease                                      
Ign http://extras.ubuntu.com utopic InRelease                                  
Ign http://ppa.launchpad.net utopic InRelease                                  
Ign http://archive.ubuntu.com utopic InRelease                                 
Atteint http://dl.google.com stable Release.gpg                                
Atteint http://extras.ubuntu.com utopic Release.gpg                            
Atteint http://repository.spotify.com stable InRelease                         
Ign http://ppa.launchpad.net utopic InRelease                                  
Atteint http://dl.google.com stable Release                                    
Atteint http://extras.ubuntu.com utopic Release                                
Ign http://ppa.launchpad.net utopic InRelease                                  
Ign http://archive.ubuntu.com utopic-updates InRelease                         
Ign http://downloads-distro.mongodb.org dist InRelease                         
Atteint http://dl.google.com stable/main amd64 Packages                        
Atteint http://extras.ubuntu.com utopic/main Sources                           
Ign http://ppa.launchpad.net utopic InRelease                                  
Atteint http://dl.google.com stable/main i386 Packages                         
Atteint http://extras.ubuntu.com utopic/main amd64 Packages                    
Atteint http://ppa.launchpad.net utopic Release.gpg                            
Ign http://archive.ubuntu.com utopic-backports InRelease                       
Atteint http://extras.ubuntu.com utopic/main i386 Packages                     
Atteint http://ppa.launchpad.net utopic Release.gpg                            
Atteint http://ppa.launchpad.net utopic Release.gpg                            
Atteint http://repository.spotify.com stable/non-free amd64 Packages           
Ign http://archive.ubuntu.com utopic-security InRelease                        
Atteint http://repo.steampowered.com precise/steam Sources                     
Atteint http://ppa.launchpad.net utopic Release.gpg                            
Atteint http://downloads-distro.mongodb.org dist Release.gpg                   
Atteint http://repository.spotify.com stable/non-free i386 Packages            
Atteint http://ppa.launchpad.net utopic Release                                
Atteint http://archive.ubuntu.com utopic Release.gpg                           
Atteint http://ppa.launchpad.net utopic Release                                
Atteint http://archive.ubuntu.com utopic-updates Release.gpg                   
Atteint http://ppa.launchpad.net utopic Release                                
Atteint http://downloads-distro.mongodb.org dist Release                       
Atteint http://ppa.launchpad.net utopic Release                                
Réception de : 1 http://archive.ubuntu.com utopic-backports Release.gpg [933 B]
Atteint http://repo.steampowered.com precise/steam amd64 Packages              
Atteint http://ppa.launchpad.net utopic/main amd64 Packages                    
Atteint http://archive.ubuntu.com utopic-security Release.gpg                  
Atteint http://ppa.launchpad.net utopic/main i386 Packages                     
Atteint http://ppa.launchpad.net utopic/main Translation-en                    
Atteint http://archive.ubuntu.com utopic Release                               
Atteint http://ppa.launchpad.net utopic/main amd64 Packages                    
Atteint http://downloads-distro.mongodb.org dist/10gen amd64 Packages          
Atteint http://ppa.launchpad.net utopic/main i386 Packages                     
Ign http://dl.google.com stable/main Translation-fr_FR                         
Atteint http://archive.ubuntu.com utopic-updates Release                       
Atteint http://ppa.launchpad.net utopic/main Translation-en                    
Atteint http://repo.steampowered.com precise/steam i386 Packages               
Ign http://extras.ubuntu.com utopic/main Translation-fr_FR                     
Ign http://dl.google.com stable/main Translation-fr                            
Ign http://extras.ubuntu.com utopic/main Translation-fr                        
Réception de : 2 http://archive.ubuntu.com utopic-backports Release [62,0 kB]  
Ign http://dl.google.com stable/main Translation-en                            
Atteint http://ppa.launchpad.net utopic/main amd64 Packages                    
Atteint http://downloads-distro.mongodb.org dist/10gen i386 Packages           
Ign http://extras.ubuntu.com utopic/main Translation-en                        
Atteint https://deb.nodesource.com utopic InRelease                            
Atteint http://ppa.launchpad.net utopic/main i386 Packages                     
Atteint http://ppa.launchpad.net utopic/main Translation-en                    
Atteint http://ppa.launchpad.net utopic/main amd64 Packages                    
Atteint https://deb.nodesource.com utopic/main Sources                         
Atteint http://ppa.launchpad.net utopic/main i386 Packages                     
Ign http://repository.spotify.com stable/non-free Translation-fr_FR            
Atteint http://archive.ubuntu.com utopic-security Release                      
Ign http://repository.spotify.com stable/non-free Translation-fr               
Atteint https://deb.nodesource.com utopic/main amd64 Packages                  
Atteint http://archive.ubuntu.com utopic/main Sources                          
Atteint http://archive.ubuntu.com utopic/restricted Sources                    
Atteint https://deb.nodesource.com utopic/main i386 Packages                   
Atteint http://archive.ubuntu.com utopic/universe Sources                      
Atteint http://archive.ubuntu.com utopic/multiverse Sources                    
Réception de : 3 https://deb.nodesource.com utopic/main Translation-fr_FR      
Atteint http://archive.ubuntu.com utopic/main amd64 Packages                   
Atteint http://archive.ubuntu.com utopic/restricted amd64 Packages             
Ign http://repository.spotify.com stable/non-free Translation-en               
Atteint http://archive.ubuntu.com utopic/universe amd64 Packages               
Atteint http://archive.ubuntu.com utopic/multiverse amd64 Packages             
Atteint http://archive.ubuntu.com utopic/main i386 Packages                    
Atteint http://archive.ubuntu.com utopic/restricted i386 Packages              
Ign http://ppa.launchpad.net utopic/main Translation-fr_FR                     
Atteint http://archive.ubuntu.com utopic/universe i386 Packages                
Ign http://ppa.launchpad.net utopic/main Translation-fr                        
Ign http://ppa.launchpad.net utopic/main Translation-en                        
Atteint http://archive.ubuntu.com utopic/multiverse i386 Packages              
Atteint http://archive.ubuntu.com utopic/main Translation-fr                   
Atteint http://archive.ubuntu.com utopic/main Translation-en                   
Atteint http://archive.ubuntu.com utopic/multiverse Translation-fr             
Atteint http://archive.ubuntu.com utopic/multiverse Translation-en             
Atteint http://archive.ubuntu.com utopic/restricted Translation-fr             
Atteint http://archive.ubuntu.com utopic/restricted Translation-en             
Atteint http://archive.ubuntu.com utopic/universe Translation-fr               
Atteint http://archive.ubuntu.com utopic/universe Translation-en               
Atteint http://archive.ubuntu.com utopic-updates/main Sources                  
Atteint http://archive.ubuntu.com utopic-updates/restricted Sources            
Atteint http://archive.ubuntu.com utopic-updates/universe Sources              
Atteint http://archive.ubuntu.com utopic-updates/multiverse Sources            
Atteint http://archive.ubuntu.com utopic-updates/main amd64 Packages           
Ign https://deb.nodesource.com utopic/main Translation-fr_FR                   
Atteint http://archive.ubuntu.com utopic-updates/restricted amd64 Packages     
Ign http://downloads-distro.mongodb.org dist/10gen Translation-fr_FR           
Ign https://deb.nodesource.com utopic/main Translation-fr                      
Atteint http://archive.ubuntu.com utopic-updates/universe amd64 Packages       
Ign http://downloads-distro.mongodb.org dist/10gen Translation-fr              
Ign https://deb.nodesource.com utopic/main Translation-en                      
Atteint http://archive.ubuntu.com utopic-updates/multiverse amd64 Packages     
Atteint http://archive.ubuntu.com utopic-updates/main i386 Packages            
Ign http://downloads-distro.mongodb.org dist/10gen Translation-en              
Atteint http://archive.ubuntu.com utopic-updates/restricted i386 Packages      
Atteint http://archive.ubuntu.com utopic-updates/universe i386 Packages        
Ign http://repo.steampowered.com precise/steam Translation-fr_FR               
Atteint http://archive.ubuntu.com utopic-updates/multiverse i386 Packages      
Atteint http://archive.ubuntu.com utopic-updates/main Translation-en           
Ign http://repo.steampowered.com precise/steam Translation-fr                  
Atteint http://archive.ubuntu.com utopic-updates/multiverse Translation-en     
Atteint http://archive.ubuntu.com utopic-updates/restricted Translation-en     
Ign http://repo.steampowered.com precise/steam Translation-en                  
Atteint http://archive.ubuntu.com utopic-updates/universe Translation-en       
Réception de : 4 http://archive.ubuntu.com utopic-backports/main Sources [751 B]
Réception de : 5 http://archive.ubuntu.com utopic-backports/restricted Sources [14 B]
Réception de : 6 http://archive.ubuntu.com utopic-backports/universe Sources [7 264 B]
Réception de : 7 http://archive.ubuntu.com utopic-backports/multiverse Sources [14 B]
Réception de : 8 http://archive.ubuntu.com utopic-backports/main amd64 Packages [556 B]
Réception de : 9 http://archive.ubuntu.com utopic-backports/restricted amd64 Packages [14 B]
Réception de : 10 http://archive.ubuntu.com utopic-backports/universe amd64 Packages [9 514 B]
Réception de : 11 http://archive.ubuntu.com utopic-backports/multiverse amd64 Packages [14 B]
Réception de : 12 http://archive.ubuntu.com utopic-backports/main i386 Packages [560 B]
Réception de : 13 http://archive.ubuntu.com utopic-backports/restricted i386 Packages [14 B]
Réception de : 14 http://archive.ubuntu.com utopic-backports/universe i386 Packages [9 505 B]
Réception de : 15 http://archive.ubuntu.com utopic-backports/multiverse i386 Packages [14 B]
Atteint http://archive.ubuntu.com utopic-backports/main Translation-en         
Atteint http://archive.ubuntu.com utopic-backports/multiverse Translation-en   
Atteint http://archive.ubuntu.com utopic-backports/restricted Translation-en   
Atteint http://archive.ubuntu.com utopic-backports/universe Translation-en     
Atteint http://archive.ubuntu.com utopic-security/main Sources                 
Atteint http://archive.ubuntu.com utopic-security/restricted Sources           
Atteint http://archive.ubuntu.com utopic-security/universe Sources             
Atteint http://archive.ubuntu.com utopic-security/multiverse Sources           
Atteint http://archive.ubuntu.com utopic-security/main amd64 Packages          
Atteint http://archive.ubuntu.com utopic-security/restricted amd64 Packages    
Atteint http://archive.ubuntu.com utopic-security/universe amd64 Packages      
Atteint http://archive.ubuntu.com utopic-security/multiverse amd64 Packages    
Atteint http://archive.ubuntu.com utopic-security/main i386 Packages           
Atteint http://archive.ubuntu.com utopic-security/restricted i386 Packages     
Atteint http://archive.ubuntu.com utopic-security/universe i386 Packages       
Atteint http://archive.ubuntu.com utopic-security/multiverse i386 Packages     
Atteint http://archive.ubuntu.com utopic-security/main Translation-en          
Atteint http://archive.ubuntu.com utopic-security/multiverse Translation-en    
Atteint http://archive.ubuntu.com utopic-security/restricted Translation-en    
Atteint http://archive.ubuntu.com utopic-security/universe Translation-en      
91,2 ko réceptionnés en 14s (6 323 o/s)                                        
Lecture des listes de paquets... Fait
vincent@vincent-LIFEBOOK-E554:~/dev/Cadendar$ sudo apt-get upgrade
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Calcul de la mise à jour... Fait
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.
vincent@vincent-LIFEBOOK-E554:~/dev/Cadendar$

```

---

### Post by Jonathan Precise on 2015-01-03
Hello 0-contact-7, welcome to the forums!

Sorry, my French isn't that good, but from what I'm understanding, [FONT=Courier New]sudo apt-get update[/FONT] returns a "Done" at the end. Please correct me if I'm wrong.

Note that  [FONT=Courier New]sudo apt-get update[/FONT] might be misleading for some users. To check for updates, you need to run that command, but to actually update the system, you need [FONT=Courier New]sudo apt-get **upgrade**[/FONT]. Both are normally used in conjunction so to check for any new updates first, and then install them.

Also, [FONT=Courier New]sudo apt-get upgrade[/FONT] that Bucky Ball told you to run said that your system is up to date. What package are you trying to update?

-Jonathan

---

### Post by 0-contact-7 on 2015-01-03
Bucky, perhaps you are right, and there has been no update for the past weeks.

---

### Post by Jonathan Precise on 2015-01-03
> **plucky said:**
> Can you try a different repository? Perhaps the Main Repository.

You can select one in "Software Sources".

Good Luck

+1. I've experienced issues in the past from other mirrors than archive.ubuntu.com, so try to stick to that one (also called Main Server in the program "Software and Updates")

---

### Post by 0-contact-7 on 2015-01-03
> **Jonathan Precise said:**
> Hello 0-contact-7, welcome to the forums!

Also, [FONT=Courier New]sudo apt-get upgrade[/FONT] that Bucky Ball told you to run said that your system is up to date. What package are you trying to update?

-Jonathan

The thing is with Trusty i had updates quite every day, and since i'm on Utopic since i got my new laptop three weeks ago, i don't remember having to update at all.

---

### Post by bapoumba on 2015-01-03
Some of the French mirrors are not up-to-date : [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)
My last auto update/upgrade was on Dec 23rd.

What is your configuration in Software Sources in the Update tab ? (on lubuntu the utility is names Software & Updates).

---

### Post by 0-contact-7 on 2015-01-03
Ok, thank you for your help, i will watch future upgrades to see if they happen or not, perhaps i'm trying to fix a non existing problem !

---

