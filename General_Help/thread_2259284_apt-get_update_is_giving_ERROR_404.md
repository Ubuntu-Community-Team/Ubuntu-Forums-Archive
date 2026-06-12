---
title: "apt-get update is giving ERROR 404"
date: 2015-01-03
forum: General Help
---

### Post by snitz2 on 2015-01-03
I'm trying to add Kali Tools on my Ubuntu 13.04 following this tutorial
[http://exploiterz.blogspot.com/2013/08/how-to-integrate-kali-linux-tools-in.html](http://exploiterz.blogspot.com/2013/08/how-to-integrate-kali-linux-tools-in.html)

I've added the new repositories to /etc/apt/sources.list
```
[I]deb http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu [COLOR=red]raring[/COLOR] main
deb-src http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu [COLOR=red]raring[/COLOR] main
deb http://ppa.launchpad.net/wagungs/kali-linux/ubuntu [COLOR=red]raring[/COLOR] main
deb-src http://ppa.launchpad.net/wagungs/kali-linux/ubuntu [COLOR=red]raring[/COLOR] main[/I]
```

But when I run sudo apt-get update, I get this following:

```
halnex@Node:~$ sudo apt-get update
Ign http://security.ubuntu.com raring-security Release.gpg
Ign http://lb.archive.ubuntu.com raring Release.gpg                            
Ign http://lb.archive.ubuntu.com raring-updates Release.gpg                    
Ign http://security.ubuntu.com raring-security Release                         
Ign http://lb.archive.ubuntu.com raring-backports Release.gpg                  
Get:1 http://ppa.launchpad.net raring Release.gpg [316 B]                      
Ign http://lb.archive.ubuntu.com raring Release                                
Get:2 http://ppa.launchpad.net raring Release.gpg [316 B]                      
Ign http://lb.archive.ubuntu.com raring-updates Release                        
Ign http://lb.archive.ubuntu.com raring-backports Release                      
Get:3 http://ppa.launchpad.net raring Release [9,753 B]                        
Get:4 http://ppa.launchpad.net raring Release [9,752 B]                        
Get:5 http://ppa.launchpad.net raring/main Sources [7,324 B]                   
Get:6 http://ppa.launchpad.net raring/main i386 Packages [6,970 B]             
Get:7 http://ppa.launchpad.net raring/main Sources [49.7 kB]                   
Get:8 http://ppa.launchpad.net raring/main i386 Packages [43.1 kB]             
Ign http://extras.ubuntu.com raring Release.gpg                                
Ign http://extras.ubuntu.com raring Release                                    
Ign http://ppa.launchpad.net raring/main Translation-en_US                     
Ign http://ppa.launchpad.net raring/main Translation-en                        
Ign http://ppa.launchpad.net raring/main Translation-en_US            
Ign http://ppa.launchpad.net raring/main Translation-en               
Err http://extras.ubuntu.com raring/main Sources                      
  404  Not Found
Err http://extras.ubuntu.com raring/main i386 Packages                         
  404  Not Found
Ign http://extras.ubuntu.com raring/main Translation-en_US                     
Ign http://extras.ubuntu.com raring/main Translation-en                        
Err http://security.ubuntu.com raring-security/main Sources                    
  404  Not Found [IP: 91.189.92.201 80]
Err http://security.ubuntu.com raring-security/restricted Sources
  404  Not Found [IP: 91.189.92.201 80]
Err http://security.ubuntu.com raring-security/universe Sources
  404  Not Found [IP: 91.189.92.201 80]
Err http://security.ubuntu.com raring-security/multiverse Sources
  404  Not Found [IP: 91.189.92.201 80]
Err http://security.ubuntu.com raring-security/main i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err http://security.ubuntu.com raring-security/restricted i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err http://security.ubuntu.com raring-security/universe i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err http://security.ubuntu.com raring-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Ign http://security.ubuntu.com raring-security/main Translation-en_US
Ign http://security.ubuntu.com raring-security/main Translation-en
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_US
Ign http://security.ubuntu.com raring-security/multiverse Translation-en
Ign http://security.ubuntu.com raring-security/restricted Translation-en_US
Ign http://security.ubuntu.com raring-security/restricted Translation-en
Ign http://security.ubuntu.com raring-security/universe Translation-en_US
Ign http://security.ubuntu.com raring-security/universe Translation-en
Err http://lb.archive.ubuntu.com raring/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign http://lb.archive.ubuntu.com raring/main Translation-en_US
Ign http://lb.archive.ubuntu.com raring/main Translation-en
Ign http://lb.archive.ubuntu.com raring/multiverse Translation-en_US
Ign http://lb.archive.ubuntu.com raring/multiverse Translation-en
Ign http://lb.archive.ubuntu.com raring/restricted Translation-en_US
Ign http://lb.archive.ubuntu.com raring/restricted Translation-en
Ign http://lb.archive.ubuntu.com raring/universe Translation-en_US
Ign http://lb.archive.ubuntu.com raring/universe Translation-en
Err http://lb.archive.ubuntu.com raring-updates/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring-updates/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring-updates/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring-updates/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring-updates/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign http://lb.archive.ubuntu.com raring-updates/main Translation-en_US
Ign http://lb.archive.ubuntu.com raring-updates/main Translation-en
Ign http://lb.archive.ubuntu.com raring-updates/multiverse Translation-en_US
Ign http://lb.archive.ubuntu.com raring-updates/multiverse Translation-en
Ign http://lb.archive.ubuntu.com raring-updates/restricted Translation-en_US
Ign http://lb.archive.ubuntu.com raring-updates/restricted Translation-en
Ign http://lb.archive.ubuntu.com raring-updates/universe Translation-en_US
Ign http://lb.archive.ubuntu.com raring-updates/universe Translation-en
Err http://lb.archive.ubuntu.com raring-backports/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring-backports/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring-backports/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring-backports/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring-backports/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring-backports/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://lb.archive.ubuntu.com raring-backports/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign http://lb.archive.ubuntu.com raring-backports/main Translation-en_US
Ign http://lb.archive.ubuntu.com raring-backports/main Translation-en
Ign http://lb.archive.ubuntu.com raring-backports/multiverse Translation-en_US
Ign http://lb.archive.ubuntu.com raring-backports/multiverse Translation-en
Ign http://lb.archive.ubuntu.com raring-backports/restricted Translation-en_US
Ign http://lb.archive.ubuntu.com raring-backports/restricted Translation-en
Ign http://lb.archive.ubuntu.com raring-backports/universe Translation-en_US
Ign http://lb.archive.ubuntu.com raring-backports/universe Translation-en
Fetched 127 kB in 1min 12s (1,754 B/s)
W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/raring-security/main/source/Sources   404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/source/Sources   404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/raring-security/universe/source/Sources   404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/source/Sources   404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages   404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages   404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages   404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-i386/Packages   404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://lb.archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring/universe/source/Sources   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch  http://lb.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages   404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by bapoumba on 2015-01-03
Raring, 13.04, has been EOL since January 27, 2014. Please use/install a supported release.

---

### Post by Bucky Ball on 2015-01-03
> **bapoumba said:**
> Raring, 13.04, has been EOL since January 27, 2014. Please use/install a supported release.

+1. I have changed your [html] tags to [code] tags in your last post to save some space.

---

