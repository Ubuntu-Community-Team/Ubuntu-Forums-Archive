---
title: "Packages not installing/uninstalling"
date: 2007-01-27
forum: General Help
---

### Post by Goodfox on 2007-01-27
I can't get any packages to install or uninstall through Synaptic or the Add/Remove Applications screen, no matter how many times I try.

This morning and last night it all seemed to be working fine, but since then, I've been following a few different tutorials to speed up Ubuntu, and I don't know if any of those have had an effect.

Does anyone know how to reverse the changes I've made or fix the package installation? Thanks in advance for any help.

---

### Post by taurus on 2007-01-27
Run these two commands from a terminal and see if there's any error message?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Goodfox on 2007-01-27
Thanks, I tried both, and it came up with this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]               
Ign http://security.ubuntu.com edgy-security/main Translation-en_US             
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US       
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US       
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US         
Get:2 http://gb.archive.ubuntu.com edgy Release.gpg [191B]                      
Ign http://gb.archive.ubuntu.com edgy/main Translation-en_US                    
Ign http://gb.archive.ubuntu.com edgy/restricted Translation-en_US              
Ign http://gb.archive.ubuntu.com edgy/multiverse Translation-en_US              
Ign http://gb.archive.ubuntu.com edgy/universe Translation-en_US                
Get:3 http://gb.archive.ubuntu.com edgy-updates Release.gpg [191B]              
Ign http://gb.archive.ubuntu.com edgy-updates/main Translation-en_US            
Ign http://gb.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Hit http://security.ubuntu.com edgy-security Release                            
Ign http://gb.archive.ubuntu.com edgy-updates/multiverse Translation-en_US      
Ign http://gb.archive.ubuntu.com edgy-updates/universe Translation-en_US
Hit http://gb.archive.ubuntu.com edgy Release                     
Hit http://gb.archive.ubuntu.com edgy-updates Release             
Hit http://security.ubuntu.com edgy-security/main Packages                      
Hit http://gb.archive.ubuntu.com edgy/main Packages                             
Hit http://security.ubuntu.com edgy-security/restricted Packages  
Hit http://security.ubuntu.com edgy-security/multiverse Packages                
Hit http://security.ubuntu.com edgy-security/main Sources                       
Hit http://gb.archive.ubuntu.com edgy/restricted Packages                       
Hit http://gb.archive.ubuntu.com edgy/multiverse Packages                       
Hit http://gb.archive.ubuntu.com edgy/main Sources                              
Hit http://security.ubuntu.com edgy-security/restricted Sources                 
Hit http://security.ubuntu.com edgy-security/universe Packages                  
Hit http://gb.archive.ubuntu.com edgy/restricted Sources                        
Hit http://gb.archive.ubuntu.com edgy/universe Packages           
Hit http://gb.archive.ubuntu.com edgy-updates/main Packages       
Hit http://gb.archive.ubuntu.com edgy-updates/restricted Packages 
Hit http://gb.archive.ubuntu.com edgy-updates/multiverse Packages 
Hit http://gb.archive.ubuntu.com edgy-updates/main Sources        
Hit http://gb.archive.ubuntu.com edgy-updates/restricted Sources  
Hit http://gb.archive.ubuntu.com edgy-updates/universe Packages   
Get:4 http://wine.budgetdedicated.com edgy Release.gpg [191B]     
Ign http://wine.budgetdedicated.com edgy/main Translation-en_US
Hit http://wine.budgetdedicated.com edgy Release
Ign http://wine.budgetdedicated.com edgy/main Packages
Ign http://wine.budgetdedicated.com edgy/main Sources                           
Hit http://wine.budgetdedicated.com edgy/main Packages                          
Hit http://wine.budgetdedicated.com edgy/main Sources                           
Fetched 4B in 12s (0B/s)                                                        
Reading package lists... Done

``````
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Running prelink, please wait...

```
I'm really new to linux though, so I'm not sure to make of it.

It it helps, one of the changes I made was for prelink, so could that have something to do with it?

---

### Post by taurus on 2007-01-27
Did you wait for this process to finish, **Running prelink, please wait...**?

---

### Post by Goodfox on 2007-01-27
Yeah, but as soon as it said that, it came up with the line "daniel@steven:~$", without me doing anything.

---

### Post by taurus on 2007-01-27
As long as there is no error message, that's good.  Now, what would you like to install?  See if you can with 

```
sudo aptitude install **package_name**
```

---

### Post by Goodfox on 2007-01-27
Hm, I've tried installing / removing a few different things now, and every time it says towards the end of the installation:

"dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `d' must be followed by colon
Running prelink, please wait...
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `d' must be followed by colon"

---

