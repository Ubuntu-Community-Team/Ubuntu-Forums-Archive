---
title: "apt-get update ignored notices?"
date: 2006-11-27
forum: General Help
---

### Post by kvonb on 2006-11-27
Should I be concerned about these "Ignored" notices?

> kev@kev:~$ sudo apt-get update
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                      
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                    
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Get:3 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release.gpg [189B]                    
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn Translation-en_US             
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US      
Get:5 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/main Translation-en_US                   
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/restricted Translation-en_US             
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US 

Thanks, Kev :)

---

### Post by mssever on 2006-11-28
As far as I know, they're nothing to be concerned about.

---

### Post by adam.tropics on 2006-11-28
As far as I am aware they just indicate nothing has changed in a given repo since the last time you updated. So no, perfectly normal.

---

