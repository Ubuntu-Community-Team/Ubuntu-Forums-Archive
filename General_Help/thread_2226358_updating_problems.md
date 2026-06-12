---
title: "updating problems"
date: 2014-05-26
forum: General Help
---

### Post by ankit10 on 2014-05-26
when i type sudo apt-get update it show like this

```
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg     
  Unable to connect to ppa.launchpad.net:http:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease      
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports InRelease      
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security InRelease       
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-proposed InRelease       
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg    
  Cannot initiate the connection to archive.ubuntu.com:80 (2001:67c:1360:8c01::18). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8c01::18 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release.gpg
  Cannot initiate the connection to archive.ubuntu.com:80 (2001:67c:1360:8c01::18). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8c01::18 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports Release.gpg
  Cannot initiate the connection to archive.ubuntu.com:80 (2001:67c:1360:8c01::18). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8c01::18 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security Release.gpg
  Cannot initiate the connection to archive.ubuntu.com:80 (2001:67c:1360:8c01::18). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8c01::18 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-proposed Release.gpg
  Cannot initiate the connection to archive.ubuntu.com:80 (2001:67c:1360:8c01::18). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8c01::18 80]
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/InRelease](http://archive.ubuntu.com/ubuntu/dists/trusty/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease](http://archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-security/InRelease](http://archive.ubuntu.com/ubuntu/dists/trusty-security/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-proposed/InRelease](http://archive.ubuntu.com/ubuntu/dists/trusty-proposed/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/trusty/InRelease](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/trusty/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/trusty/Release.gpg](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/trusty/Release.gpg)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg)  Cannot initiate the connection to archive.ubuntu.com:80 (2001:67c:1360:8c01::18). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8c01::18 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg)  Cannot initiate the connection to archive.ubuntu.com:80 (2001:67c:1360:8c01::18). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8c01::18 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg)  Cannot initiate the connection to archive.ubuntu.com:80 (2001:67c:1360:8c01::18). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8c01::18 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg)  Cannot initiate the connection to archive.ubuntu.com:80 (2001:67c:1360:8c01::18). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8c01::18 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-proposed/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/trusty-proposed/Release.gpg)  Cannot initiate the connection to archive.ubuntu.com:80 (2001:67c:1360:8c01::18). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8c01::18 80]

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by deadflowr on 2014-05-26
I merged your posts, added code tags, and move it into it's own thread.

---

### Post by prmurthy on 2014-05-27
> Network is unreachable
I think that's a pretty broad hint that you dont have net access? You need to fix your internet connectivity first. Once "ping www.yahoo.com" is successful, or you can browse the web, you can run the update.

---

