---
title: "sudo apt-update fails and no &quot;install&quot; option in Software Centre"
date: 2015-09-13
forum: General Help
---

### Post by swapnil10 on 2015-09-13
I have just installed Ubuntu 13.04 and now after trying the command sudo apt-get update, I get the following response. Also in Ubuntu Software Centre, it shows "get this source" instead of "install".

```
swapnil@swapnil-desktop:~$ sudo apt-get update
[sudo] password for swapnil: 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy InRelease                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security InRelease
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates InRelease
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg [72 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release.gpg                     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports InRelease
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release [9,753 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release                          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy Release.gpg 
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Sources [14 B]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates Release.gpg                 
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main i386 Packages [14 B]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports Release.gpg                   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy Release                        
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports Release             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_IN            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en               
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
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy/main Sources     
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy/restricted Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy/universe Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy/multiverse Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy/main i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy/restricted i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy/universe i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy/main Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy/multiverse Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy/restricted Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy/universe Translation-en
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates/main Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates/restricted Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates/universe Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates/multiverse Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates/main i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates/main Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates/multiverse Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates/restricted Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates/universe Translation-en
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports/main Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports/restricted Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports/universe Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports/multiverse Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports/main i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports/universe i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports/main Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports/multiverse Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports/restricted Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports/universe Translation-en
Fetched 9,853 B in 1min 11s (137 B/s)
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/saucy-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/saucy-security/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/saucy-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/saucy-security/restricted/source/Sources)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/saucy-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/saucy-security/universe/source/Sources)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/saucy-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/saucy-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/saucy-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/saucy-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/saucy-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/saucy-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/saucy-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/saucy-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/saucy-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/saucy-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/saucy/main/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/saucy/restricted/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/saucy/universe/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/saucy/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/saucy/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/saucy/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/saucy/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy-updates/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/saucy-updates/main/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy-updates/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/saucy-updates/restricted/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy-updates/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/saucy-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy-updates/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/saucy-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy-backports/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/saucy-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy-backports/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/saucy-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy-backports/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/saucy-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy-backports/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/saucy-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy-backports/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/saucy-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy-backports/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/saucy-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy-backports/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/saucy-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy-backports/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/saucy-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
swapnil@swapnil-desktop:~$
```

---

### Post by ibod on 2015-09-13
I think you will find support ended Jan 27 2014 
see [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Bucky Ball on 2015-09-13
Welcome. As above. 13.04 is no longer supported. Don't go there. [14.04 LTS is a good place]("http://www.ubuntu.com/download/desktop") to start and supported until 2019.

You are getting those errors because there are no longer updates or repositories for 13.04. Good luck.

---

### Post by swapnil10 on 2015-09-15
Thanx a lot..!! i will go for 14.04 release then..!!

---

