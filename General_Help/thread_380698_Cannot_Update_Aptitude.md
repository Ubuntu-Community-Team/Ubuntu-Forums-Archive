---
title: "Cannot Update Aptitude"
date: 2007-03-09
forum: General Help
---

### Post by ndube on 2007-03-09
Whenever I sudo apt-get update, the following is the result

ndube@JPTI-NETTECH-LTU:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg          
  Error reading from server - read (104 Connection reset by peer)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg 
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.6 80]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources [3620B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.6 80]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources [3593B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.6 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
47% [Working]            
gzip: stdin: not in gzip format
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
  Sub-process gzip returned an error code (1)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.6 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Sources
Fetched 2B in 1s (2B/s)                                
Reading package lists... Done


I am assuming that because I only retrieved 2B, I am not connecting to the repos. I can surf the internet fine. Does anyone have any ideas?

---

### Post by leogibson on 2007-03-12
> **ndube said:**
> * 				Last edited by ndube : 2 Days Ago at 12:38 PM. 				Reason: Resolved*

im having this same problem especially with the following:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
  Sub-process gzip returned an error code (1)

how did you resolve this?

---

### Post by ndube on 2007-03-13
My clark connect firewall ([www.clarkconnect.com](www.clarkconnect.com)) was blocking aptitude from connecting to ubuntu.com. I whitelisted ubuntu.com, canonical.com, and a few third party repos for automatix, wine, etc.

Hope this helps.

---

