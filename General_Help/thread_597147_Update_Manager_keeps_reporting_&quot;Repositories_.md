---
title: "Update Manager keeps reporting &quot;Repositories changed&quot;"
date: 2007-10-30
forum: General Help
---

### Post by Roobert on 2007-10-30
HI,

Every time I try to check for updates with update manager, I get this message in a pop-up box: ```
Repositories Changed
The repository information has changed.
You have to click on the "Reload" button for your changes to take effect.
```

However, if I click reload as it instructs, nothing changes; update manager keeps reporting "Repositories changed". What is the cause of this message, and is it a problem? Do I have to edit something in my sources.list?

Thanks,

~ Eric.

---

### Post by taurus on 2007-10-30
What happens when you run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Roobert on 2007-10-30
Here's the output from apt-get-update:

```
$ sudo apt-get update
[sudo] password for epatton:
Get:1 http://ca.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://ca.archive.ubuntu.com gutsy/main Translation-en_CA                                           
Ign http://ca.archive.ubuntu.com gutsy/restricted Translation-en_CA        
Ign http://ca.archive.ubuntu.com gutsy/universe Translation-en_CA          
Ign http://ca.archive.ubuntu.com gutsy/multiverse Translation-en_CA        
Get:2 http://ca.archive.ubuntu.com gutsy-updates Release.gpg [191B]        
Ign http://ca.archive.ubuntu.com gutsy-updates/main Translation-en_CA       
Ign http://ca.archive.ubuntu.com gutsy-updates/restricted Translation-en_CA
Get:3 http://ca.archive.ubuntu.com gutsy-backports Release.gpg [191B]
Ign http://ca.archive.ubuntu.com gutsy-backports/main Translation-en_CA     
Ign http://ca.archive.ubuntu.com gutsy-backports/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-backports/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-backports/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com gutsy Release                       
Hit http://ca.archive.ubuntu.com gutsy-updates Release               
Hit http://ca.archive.ubuntu.com gutsy-backports Release             
Get:4 http://security.ubuntu.com gutsy-security Release.gpg [191B]   
Get:5 http://archive.ubuntu.com gutsy Release.gpg [191B]            
Ign http://security.ubuntu.com gutsy-security/main Translation-en_CA
Get:6 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]    
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_CA 
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_CA
Hit http://ca.archive.ubuntu.com gutsy/main Packages                                      
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_CA   
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com gutsy/restricted Packages           
Hit http://ca.archive.ubuntu.com gutsy/restricted Sources            
Hit http://ca.archive.ubuntu.com gutsy/main Sources                  
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com gutsy/multiverse Sources            
Hit http://ca.archive.ubuntu.com gutsy/universe Sources              
Hit http://ca.archive.ubuntu.com gutsy/universe Packages             
Hit http://ca.archive.ubuntu.com gutsy/multiverse Packages           
Hit http://ca.archive.ubuntu.com gutsy-updates/main Packages         
Hit http://ca.archive.ubuntu.com gutsy-updates/restricted Packages   
Hit http://ca.archive.ubuntu.com gutsy-updates/main Sources          
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com gutsy-updates/restricted Sources    
Hit http://ca.archive.ubuntu.com gutsy-backports/main Packages       
Hit http://ca.archive.ubuntu.com gutsy-backports/restricted Packages 
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com gutsy-backports/universe Packages   
Hit http://ca.archive.ubuntu.com gutsy-backports/multiverse Packages 
Hit http://ca.archive.ubuntu.com gutsy-backports/main Sources        
Hit http://ca.archive.ubuntu.com gutsy-backports/restricted Sources  
Hit http://ca.archive.ubuntu.com gutsy-backports/universe Sources    
Hit http://ca.archive.ubuntu.com gutsy-backports/multiverse Sources  
Hit http://security.ubuntu.com gutsy-security Release                
Hit http://archive.ubuntu.com gutsy Release    
Hit http://archive.ubuntu.com gutsy-updates Release                 
Hit http://security.ubuntu.com gutsy-security/main Packages         
Hit http://security.ubuntu.com gutsy-security/restricted Packages   
Hit http://security.ubuntu.com gutsy-security/restricted Sources    
Hit http://archive.ubuntu.com gutsy/main Sources
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://archive.ubuntu.com gutsy/restricted Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Hit http://archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://archive.ubuntu.com gutsy-updates/main Packages
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://archive.ubuntu.com gutsy-updates/universe Packages
Hit http://archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://archive.ubuntu.com gutsy-updates/main Sources
Hit http://archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://archive.ubuntu.com gutsy-updates/universe Sources
Fetched 6B in 2s (2B/s)  
Reading package lists... Done
```

And output from apt-get upgrade:

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

~ Eric.

---

### Post by taurus on 2007-10-30
Looks like there is nothing to upgrade since everything is the latest.

---

### Post by Roobert on 2007-10-30
But even if that is the case, it doesn't explain why I'm getting this "repositories changed" message. I notice that some of the repos in my sources.list point to "ca.archive.ubuntu.com", and others just to "archive.ubuntu.com". Is that normal, or should they all point to either the Canadian server or the master Ubuntu server?

~ Eric.

---

### Post by Roobert on 2007-11-01
I did a find and replace on all of my repository sites, replacing "ca.archive.com" with "archive.com", and it seemed to work. Update manager immediately showed that I had 92 new updates! It looks like it hasn't been working for a while. 

Anyway, hopefully this will be useful for someone else who is having the same problem.

~ Eric.

---

