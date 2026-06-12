---
title: "SLOW Updates"
date: 2008-04-25
forum: General Help
---

### Post by edthefox on 2008-04-25
I was just trying to install some packages and it just took over 20 minutes just to do an update. Is someone ddosing the repositories. My network seems fine. Is anyone else having this issue?

```
eddie@IT2-ubuntu804b:~$ time sudo apt-get update
Hit http://archive.canonical.com hardy Release.gpg
Hit http://security.ubuntu.com hardy-security Release.gpg           
Ign http://archive.canonical.com hardy/partner Translation-en_US    
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Hit http://archive.canonical.com hardy Release                       
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release                          
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://security.ubuntu.com hardy-security/main Packages          
Hit http://archive.canonical.com hardy/partner Sources               
Hit http://security.ubuntu.com hardy-security/restricted Packages    
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Get:1 http://archive.ubuntu.com hardy Release.gpg [191B]
Hit http://archive.ubuntu.com hardy Release    
Hit http://archive.ubuntu.com hardy/main Sources                               
Get:2 http://us.archive.ubuntu.com hardy Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Hit http://archive.ubuntu.com hardy/restricted Sources                        
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com hardy-backports Release.gpg [191B]
Ign http://us.archive.ubuntu.com hardy-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com hardy-proposed Release.gpg [191B]
Ign http://us.archive.ubuntu.com hardy-proposed/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-proposed/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-proposed/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com hardy-proposed/universe Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Ign http://us.archive.ubuntu.com hardy-updates Release                         
Ign http://us.archive.ubuntu.com hardy-backports Release
Ign http://us.archive.ubuntu.com hardy-proposed Release
Hit http://us.archive.ubuntu.com hardy/main Packages    
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/main Sources     
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-backports/main Packages
Hit http://us.archive.ubuntu.com hardy-backports/restricted Packages
Hit http://us.archive.ubuntu.com hardy-backports/universe Packages
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-proposed/restricted Packages
Hit http://us.archive.ubuntu.com hardy-proposed/main Packages
Hit http://us.archive.ubuntu.com hardy-proposed/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-proposed/universe Packages
Fetched 764B in 21min52s (1B/s)
Reading package lists... Done

real	21m52.405s
user	0m0.096s
sys	0m0.040s
eddie@IT2-ubuntu804b:~$ 

```

---

### Post by uopjohnson on 2008-04-25
I think we (as in the community) as ddosing the repos.  I'm getting a really slow connection in San Francisco, since yesterday, bout when I downloaded hardy. Probably lots of folks doing dist-upgrades.

---

### Post by jbysmith on 2008-04-25
> **uopjohnson said:**
> I think we (as in the community) as ddosing the repos.  I'm getting a really slow connection in San Francisco, since yesterday, bout when I downloaded hardy. Probably lots of folks doing dist-upgrades.

That's pretty much it.  Got a bajillion people hammering the repositories.. Took me near an hour to get Wine installed; usually takes me under 30 seconds.

Think I'm going to have to start taking vacations every six months and avoid using my computer for a few days during dist-upgrade season :D

---

### Post by dnzz on 2008-04-25
While downloading French repos are fast enough but it takes some time to set up a connection with server.

---

### Post by romis on 2008-04-25
This time around it wasn't as slow for me as last time around, when my download speeds were mostly measured in bytes per second. This time around I got between 30 and sometimes even 80 kilobytes per second.

Yeah, we as a community have "clogged" their "tubes", maybe time to shoot a power ball through?

---

### Post by natrixgli on 2008-04-25
Hehe... Just goes to show you how much we take package management for granted! 


-n8

---

