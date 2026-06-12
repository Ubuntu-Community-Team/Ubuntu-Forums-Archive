---
title: "Servers dead or problem with my computer?"
date: 2008-05-31
forum: General Help
---

### Post by DexterLB on 2008-05-31
the result of sudo apt-get update:
```

Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_US
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]                          
Ign http://ppa.launchpad.net hardy/main Packages                           
Hit http://ppa.launchpad.net hardy/main Packages                           
Hit http://archive.canonical.com hardy Release                             
Hit http://archive.canonical.com hardy/partner Packages                    
Hit http://archive.canonical.com hardy/partner Sources
Hit http://archive.ubuntu.com hardy Release.gpg                                
Ign http://archive.ubuntu.com hardy/main Translation-en_US
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy/universe Translation-en_US
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy-updates Release.gpg
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy-security Release.gpg
Ign http://archive.ubuntu.com hardy-security/main Translation-en_US
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy-proposed Release.gpg
Ign http://archive.ubuntu.com hardy-proposed/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-proposed/main Translation-en_US
Ign http://archive.ubuntu.com hardy-proposed/multiverse Translation-en_US
Ign http://archive.ubuntu.com hardy-proposed/universe Translation-en_US
Hit http://archive.ubuntu.com hardy Release
Hit http://archive.ubuntu.com hardy-updates Release
Hit http://archive.ubuntu.com hardy-security Release
Hit http://archive.ubuntu.com hardy-proposed Release
Hit http://archive.ubuntu.com hardy/main Packages
Hit http://archive.ubuntu.com hardy/restricted Packages
Hit http://archive.ubuntu.com hardy/restricted Sources
Hit http://archive.ubuntu.com hardy/main Sources
Hit http://archive.ubuntu.com hardy/multiverse Sources
Hit http://archive.ubuntu.com hardy/universe Sources
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://archive.ubuntu.com hardy/multiverse Packages
Hit http://archive.ubuntu.com hardy-updates/main Packages
Hit http://archive.ubuntu.com hardy-updates/restricted Packages
Hit http://archive.ubuntu.com hardy-updates/restricted Sources
Hit http://archive.ubuntu.com hardy-updates/main Sources
Hit http://archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://archive.ubuntu.com hardy-updates/universe Sources
Hit http://archive.ubuntu.com hardy-updates/universe Packages
Hit http://archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://archive.ubuntu.com hardy-security/main Packages
Hit http://archive.ubuntu.com hardy-security/restricted Packages
Hit http://archive.ubuntu.com hardy-security/restricted Sources
Hit http://archive.ubuntu.com hardy-security/main Sources
Hit http://archive.ubuntu.com hardy-security/multiverse Sources
Hit http://archive.ubuntu.com hardy-security/universe Sources
Hit http://archive.ubuntu.com hardy-security/universe Packages
Hit http://archive.ubuntu.com hardy-security/multiverse Packages
Hit http://archive.ubuntu.com hardy-proposed/restricted Packages
Hit http://archive.ubuntu.com hardy-proposed/main Packages
Hit http://archive.ubuntu.com hardy-proposed/multiverse Packages
Hit http://archive.ubuntu.com hardy-proposed/universe Packages
Hit http://archive.ubuntu.com hardy-proposed/restricted Sources
Hit http://archive.ubuntu.com hardy-proposed/main Sources
Hit http://archive.ubuntu.com hardy-proposed/multiverse Sources
Hit http://archive.ubuntu.com hardy-proposed/universe Sources
Fetched 1B in 1min36s (0B/s)
Reading package lists... Done

```

When you look at it carefully, you see it couldn't get any information. Pings to the servers work, 0% packet loss, so, what could it be?

---

### Post by quelx on 2008-05-31
**Hit** means no update **Ign** is ignored, I don't see any problems with the servers nor apt.  Your package lists at least are up to date.

---

