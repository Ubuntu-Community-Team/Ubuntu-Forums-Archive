---
title: "package manager doesn't work"
date: 2006-12-21
forum: General Help
---

### Post by MikeReiner on 2006-12-21
Update:
Well, i'm at my friend's house with my PC.. and the package manager works fine now... we have the same ISP (and same model of modem for that matter)

I wonder if my router is the problem.. hm.

---

### Post by bruenig on 2006-12-22
Paste your /etc/apt/sources.list

---

### Post by MikeReiner on 2006-12-22
## comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
                                   
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

# AMAROK 1.4.4
deb [http://kubuntu.org/packages/amarok-144](http://kubuntu.org/packages/amarok-144) edgy main


For the record, I had this issue at first with LinuxMint, I thought that OS I might be causing it so I switched to real ubuntu (6.10), but then for some reason I couldn't get the nvidia drivers to work and the package manager still didn't work..

so I switched BACK to linuxmint, got my drivers working, and other than the package manager, all is smoothe.

Also, it is worth noting, that when it states that it fails to fetch a file, I am able to copy and paste the address to the file into firefox and download then manually run the .deb... meaning I can reach the destination just fine.. but the package manager can't...

---

### Post by MikeReiner on 2006-12-23
Update:

Well, i'm at my friend's house with my PC.. and the package manager works fine now... we have the same ISP (and same model of modem for that matter)

I wonder if my router is the problem.. hm.

---

### Post by NeoLithium on 2006-12-23
What type of errors, if any are you getting?

---

### Post by MikeReiner on 2006-12-23
Failed to fetch, basically a timeout when attempting to download the .deb package.

---

### Post by hanzomon4 on 2006-12-23
Sometimes this happens with my dsl connection. It usually goes away after awhile

---

