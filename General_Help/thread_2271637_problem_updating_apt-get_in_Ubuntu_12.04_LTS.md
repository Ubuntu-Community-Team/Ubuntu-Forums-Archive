---
title: "problem updating apt-get in Ubuntu 12.04 LTS"
date: 2015-03-31
forum: General Help
---

### Post by harshal4 on 2015-03-31
Dear Ubuntu expert,

I am new to Ubuntu and I am trying to update apt-get but I get following error message. 
Can someone please help me? I would be really grateful to you.


Best,
Harshal 


sudo apt-get update
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg
  Could not connect to extras.ubuntu.com:80 (91.189.92.152). - connect (111: Connection refused)
Err [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise Release.gpg                          
  Could not connect to de.archive.ubuntu.com:80 (141.30.13.10). - connect (111: Connection refused) [IP: 141.30.13.10 80]
Err [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates Release.gpg                  
  Unable to connect to de.archive.ubuntu.com:http: [IP: 141.30.13.10 80]
Err [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                          
  Could not connect to archive.canonical.com:80 (91.189.92.150). - connect (111: Connection refused) [IP: 91.189.92.150 80]
Err [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports Release.gpg                
  Unable to connect to de.archive.ubuntu.com:http: [IP: 141.30.13.10 80]
Err [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-security Release.gpg
  Unable to connect to de.archive.ubuntu.com:http: [IP: 141.30.13.10 80]
Err [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-proposed Release.gpg
  Unable to connect to de.archive.ubuntu.com:http: [IP: 141.30.13.10 80]
Reading package lists... Done
W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://de.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Could not connect to de.archive.ubuntu.com:80 (141.30.13.10). - connect (111: Connection refused) [IP: 141.30.13.10 80]

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://de.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Unable to connect to de.archive.ubuntu.com:http: [IP: 141.30.13.10 80]

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://de.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Unable to connect to de.archive.ubuntu.com:http: [IP: 141.30.13.10 80]

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://de.archive.ubuntu.com/ubuntu/dists/precise-security/Release.gpg)  Unable to connect to de.archive.ubuntu.com:http: [IP: 141.30.13.10 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/Release.gpg](http://archive.canonical.com/ubuntu/dists/precise/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.92.150). - connect (111: Connection refused) [IP: 91.189.92.150 80]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Could not connect to extras.ubuntu.com:80 (91.189.92.152). - connect (111: Connection refused)

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/precise-proposed/Release.gpg](http://de.archive.ubuntu.com/ubuntu/dists/precise-proposed/Release.gpg)  Unable to connect to de.archive.ubuntu.com:http: [IP: 141.30.13.10 80]

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by kc1di on 2015-03-31
Hello harshal4  and Welcome to Ubuntu,

Looks like the server your using may be down. 
you could try a different one or wait a day or so and see if it comes back up. 

You can try a different one by going to System Settings >Software & Updates in the screen that comes up there is a dialogue box about 2/3rds the way down, click on that and select a different server close to you.

---

### Post by slickymaster on 2015-03-31
*Moved to the ***General Help*** sub-forum*

---

