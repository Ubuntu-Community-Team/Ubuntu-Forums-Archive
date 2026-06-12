---
title: "Upgrade"
date: 2007-06-24
forum: General Help
---

### Post by shadows85 on 2007-06-24
Is it possible to upgrade my ubuntu 7.04 to ubuntu studio?

---

### Post by Silenus on 2007-06-24
```
sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'

wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update
```


That should do it.

---

### Post by shadows85 on 2007-06-24
> **Silenus said:**
> ```
sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'

wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update
```


That should do it.

Thanks, I'm trying it now.

EDIT:
```
david@davids-computer-4441:~$ sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
Password:
david@davids-computer-4441:~$ wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update
OK
Get:1 http://www.getautomatix.com feisty Release.gpg [189B]
Ign http://www.getautomatix.com feisty/main Translation-en_US                  
Hit http://www.getautomatix.com feisty Release                                 
Get:2 http://archive.ubuntustudio.org feisty Release.gpg [189B]                
Ign http://archive.ubuntustudio.org feisty/main Translation-en_US              
Get:3 http://archive.canonical.com feisty-commercial Release.gpg [191B]        
Ign http://archive.canonical.com feisty-commercial/main Translation-en_US      
Hit http://www.getautomatix.com feisty/main Packages                           
Ign http://archive.ubuntustudio.org feisty/main Translation-en_US              
Get:4 http://archive.ubuntu.com feisty-backports Release.gpg [191B]            
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_US          
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_US    
Hit http://archive.ubuntustudio.org feisty Release                             
Get:5 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/main Translation-en_US          
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US    
Get:6 http://download.tuxfamily.org feisty Release.gpg [189B]                  
Ign http://download.tuxfamily.org feisty/avant-window-navigator Translation-en_US
Hit http://archive.canonical.com feisty-commercial Release                     
Hit http://archive.ubuntustudio.org feisty/main Packages                       
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_US      
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_US    
Get:7 http://archive.ubuntu.com feisty-updates Release.gpg [191B]              
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_US        
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_US      
Get:8 http://archive.ubuntu.com feisty-security Release.gpg [191B]             
Ign http://archive.ubuntu.com feisty-security/main Translation-en_US           
Get:9 http://us.archive.ubuntu.com feisty Release.gpg [191B]                   
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                 
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US      
Hit http://security.ubuntu.com feisty-security Release                         
Hit http://download.tuxfamily.org feisty Release                               
Hit http://archive.ubuntustudio.org feisty/main Packages                       
Hit http://archive.canonical.com feisty-commercial/main Packages               
Ign http://archive.ubuntu.com feisty-security/restricted Translation-en_US     
Ign http://archive.ubuntu.com feisty-security/universe Translation-en_US
Ign http://archive.ubuntu.com feisty-security/multiverse Translation-en_US
Get:10 http://archive.ubuntu.com feisty Release.gpg [191B]                     
Ign http://archive.ubuntu.com feisty/universe Translation-en_US                
Ign http://archive.ubuntu.com feisty/multiverse Translation-en_US              
Hit http://security.ubuntu.com feisty-security/main Packages                   
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US   
Get:11 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]          
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US   
Hit http://archive.ubuntu.com feisty-backports Release                         
Hit http://archive.ubuntu.com feisty-updates Release                           
Hit http://archive.ubuntu.com feisty-security Release                          
Hit http://download.tuxfamily.org feisty/avant-window-navigator Packages       
Hit http://archive.ubuntu.com feisty Release                                   
Hit http://security.ubuntu.com feisty-security/restricted Packages             
Hit http://security.ubuntu.com feisty-security/main Sources                    
Hit http://security.ubuntu.com feisty-security/restricted Sources              
Hit http://download.tuxfamily.org feisty/avant-window-navigator Sources        
Ign http://us.archive.ubuntu.com feisty-updates/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com feisty-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release                      
Hit http://us.archive.ubuntu.com feisty-updates Release                        
Hit http://security.ubuntu.com feisty-security/multiverse Packages             
Hit http://security.ubuntu.com feisty-security/universe Packages     
Hit http://archive.ubuntu.com feisty-backports/main Packages         
Hit http://archive.ubuntu.com feisty-backports/restricted Packages   
Hit http://archive.ubuntu.com feisty-backports/universe Packages
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://archive.ubuntu.com feisty-updates/universe Packages
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://archive.ubuntu.com feisty-security/main Packages
Hit http://archive.ubuntu.com feisty-security/restricted Packages
Hit http://archive.ubuntu.com feisty-security/universe Packages
Hit http://archive.ubuntu.com feisty-security/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://archive.ubuntu.com feisty/universe Packages
Hit http://archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://us.archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-updates/universe Packages
Fetched 11B in 1s (7B/s) 
Reading package lists... Done
david@davids-computer-4441:~$ 

```

Is it suppose to end in like 5 seconds? o.o

---

### Post by Silenus on 2007-06-24
No problem, if you have any other problems just post again, and I will see if I can help.

---

### Post by shadows85 on 2007-06-24
Hmm, there was no change.

---

### Post by Silenus on 2007-06-24
did you sudo apt-get update, and sudo apt-get dist-upgrade. Then kill gdm and login again or see if there is a different session, ctrl alt backspace, and look at sessions or log in again after you sudo upgrade, etc.

Ok I saw you updated, just exit gdm and relogin or look for a new session.

---

### Post by shadows85 on 2007-06-24
> **Silenus said:**
> did you sudo apt-get update, and sudo apt-get dist-upgrade. Then kill gdm and login again or see if there is a different session, ctrl alt backspace, and look at sessions or log in again after you sudo upgrade, etc.

Ok I saw you updated, just exit gdm and relogin or look for a new session.

No, I just did it all and still no change.

---

### Post by Silenus on 2007-06-24
```
sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-desktop ubuntustudio-graphics ubuntustudio-video

sudo su -c &#8216;echo @audio - rtprio 99 >> /etc/security/limits.conf&#8217;


```

Sorry I forgot that part

---

