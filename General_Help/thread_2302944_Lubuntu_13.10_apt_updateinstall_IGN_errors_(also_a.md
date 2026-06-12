---
title: "Lubuntu 13.10 apt update/install IGN errors (also affects Mint machines)"
date: 2015-11-14
forum: General Help
---

### Post by clarenimbus on 2015-11-14
Can't install anything, run apt-get update, or basically do anything useful with the repositories.  and the mint machines I run behave the same!  is this a conspiracy? Do I just have to stay with the latest release?  that seems like a pain.

I feel like I've done my due diligence checking if this issue is already resolved, but I apologize if this is something obvious or whatever.   Thanks in advance.

This is the output of apt-get update
 
```
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy InReleaseIgn [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security InRelease             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates InRelease           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release.gpg            
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy InRelease                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports InRelease                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release                
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources/DiffIndex 
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy/partner i386 Packages         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg                       
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates Release.gpg           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports Release.gpg         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources/DiffIndex
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release                                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates Release               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Sources                      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports Release             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources/DiffIndex
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main i386 Packages                
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/main Sources/DiffIndex                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages/DiffIndex     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/restricted Sources/DiffIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/universe Sources/DiffIndex    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/multiverse Sources/DiffIndex  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/main i386 Packages/DiffIndex  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/restricted i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/universe i386 Packages/DiffIndex        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/multiverse i386 Packages/DiffIndex      
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-en_CA     
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-en        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_CA            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/main Sources/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/restricted Sources/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/universe Sources/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/multiverse Sources/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/main i386 Packages/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/restricted i386 Packages/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/universe i386 Packages/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/multiverse i386 Packages/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/main Sources/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/restricted Sources/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/universe Sources/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/multiverse Sources/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/main i386 Packages/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/restricted i386 Packages/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/universe i386 Packages/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/multiverse i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/main Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/multiverse Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/restricted Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/universe Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/main Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/multiverse Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/restricted Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/universe Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/main Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/multiverse Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/restricted Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/universe Translation-en
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/main Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/restricted Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/universe Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/multiverse Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/main i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/restricted i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/universe i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/main Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/restricted Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/universe Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/multiverse Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/main i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/main Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/restricted Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/universe Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/multiverse Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/main i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/universe i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/saucy-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/saucy-security/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/saucy-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/saucy-security/restricted/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/saucy-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/saucy-security/universe/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/saucy-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/saucy-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy/main/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/saucy/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/saucy-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/saucy-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy/restricted/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/saucy/restricted/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/saucy-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/saucy-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy/universe/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/saucy/universe/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/saucy-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/saucy-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy/multiverse/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/saucy/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy/main/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy/restricted/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/saucy/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/saucy-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/saucy-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy/universe/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/saucy/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy/multiverse/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/saucy/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy-updates/main/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/saucy-updates/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy-updates/restricted/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/saucy-updates/restricted/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy-updates/main/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/saucy-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy-updates/restricted/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/saucy-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy-backports/main/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/saucy-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy-backports/restricted/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/saucy-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy-backports/universe/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/saucy-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy-backports/multiverse/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/saucy-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy-backports/main/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/saucy-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy-backports/restricted/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/saucy-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy-backports/universe/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/saucy-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/saucy-backports/multiverse/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/saucy-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]
```

---

### Post by howefield on 2015-11-14
Your Lubuntu release is well past End of Life and is now unsupported with the repositories having been moved into old-releases. The answer is to move to a supported release.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by clarenimbus on 2015-11-14
Software Updater gives "Failed to download repository information;  Check your internet connection."

Oh.  Okay.  Thank you!  Now to figure out how to mark this as resolved.

---

### Post by howefield on 2015-11-15
> **clarenimbus said:**
> Software Updater gives "Failed to download repository information;  Check your internet connection."

Yep, your sources.list is pointing to a non existent source because they are moved after a period of time, once the version goes end of life,  You could point your sources.list to the old-releases repositories but there are no security updates to saucy any more, so the best bet is to clean install to a supported version eg 14.04 or upgrade from 13.10 to Trusty.

Lubuntu Long Term Support releases (current one is 14.04) get 3 years of updates and interim releases 9 months, so is supported till April 2017. The next LTS will come out in April 2016. Unless you specifically want the latest and greatest, and it seems you don't ;)  it probably makes sense to stay on the LTS releases upgrading every 2 years or so. 

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

